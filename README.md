
# journey-java-business-sdk
**Java SDK** to integrate with Urbanbuz Platform (Journey)

**Run Sample code**
Here is the minimal code needed to submit a transaction to Urbanbuz. If your app and build environments are set up correctly, this code should compile and run without error. You can verify the created transation in journey platform.

    package com.urbanbuz.integration.app;
    import java.util.Map;
    import com.urbanbuz.integration.api.UrbanbuzAPI;
    import com.urbanbuz.integration.dto.txn.TransactionDTO;
    import com.urbanbuz.integration.util.JSON;

    public class QuickStartExample {

	public static final String BASE_URL = "https://stage-api.urbanbuz.com"; // This will be different for production.

	public static final String API_KEY = "Your API Key";

	private static final String API_SECRET = "Your API Secret";

	public static void main(String[] args) {

		UrbanbuzAPI urbanbuzAPI = new UrbanbuzAPI(BASE_URL, API_KEY, API_SECRET);

		TransactionDTO transactionDTO = JSON.getGson().fromJson("{\"customer\":{\"customer_id\":\"77703999878907\","
				+ "\"phone\":\"971551467246\"}," + "\"receipt\":\"14336570004\","
				+ "\"openTime\":\"2018-02-24 15:24:45\"," + "\"billed\":500,\"paid\":500," + "\"itemDiscountTotal\":0,"
				+ "\"itemTaxTotal\":0,\"operatorId\":\"89541\"," + "\"operatorName\":\"Shefin\","
				+ "\"items\":[{\"sku\":\"014810037379\",\"type\":\"ITEM\",\"qty\":1,\"unitPrice\":100},"
				+ "{\"sku\":\"014810078968\"," + "\"type\":\"ITEM\",\"qty\":2,\"unitPrice\":200}],"
				+ "\"payments\":[{\"name\":\"MASTER\",\"typeName\":\"CARD\",\"amount\":500,\"referenceId\":\"Payment-20180224\"}]}",
				TransactionDTO.class);

		Map<Integer, String> submitTransaction = urbanbuzAPI.submitTransaction("1234", transactionDTO);
		System.out.println(submitTransaction);
	}
    }
