## LendfMe API Document

### Introduction

Welcome to LenfMe's API Documentation!

We provide some API interfaces to query infomation about Lendf.Me Money Market, you can get information about

- market(Asset information)
- accounts(Details about all users who have borrowed)
- liquidation(All liquidation transactions)

If you have any questions or feedback, you can open an issue at [our github repo](https://github.com/Lendfme/docs/issues) or come chat with us on our [Telegram](https://t.me/dforcenet).

## Public Rest API

### Get List Markets

> get market information

**Url**

> [https://api.lendf.me/v2/info?data=markets](https://api.lendf.me/v2/info?data=markets)(Recommended)

> [https://api.lendf.me/v1/info?data=markets ](https://api.lendf.me/v1/info?data=markets) (Deprecated)

**Request Method**

```
GET
```

**Request Parameters**

```
none
```

**Response Result**

| field                       | type   | description                                      |
| --------------------------- | ------ | ------------------------------------------------ |
| markets                     | object | List all assets information                      |
| totalSupplyBalance          | string | Total supply balance of all asset markets in ETH |
| totalSupplyBalanceUSD       | string | Total supply balance of all asset markets in USD |
| totalBorrowBalance          | string | Total borrow balance of all asset markets in ETH |
| totalBorrowBalanceUSD       | string | Total borrow balance of all asset markets in USD |
| totalCollateralizationRatio | string | Collateral ratio of all asset markets            |
| userCount                   | int    | Total current users                              |
| collateralRatio             | string | Asset collateral ratio                           |
| originationFee              | string | Borrowing fee                                    |
| liquidationDiscount         | string | Liquidation discount                             |

**_markets details_**

| name            | type   | description                                               |
| --------------- | ------ | --------------------------------------------------------- |
| asset           | string | The address of the asset                                  |
| name            | string | The name of the asset                                     |
| symbol          | string | The symbol of the asset                                   |
| decimal         | int    | The number of decimals used for the asset                 |
| balance         | string | The number of supplying for the asset                     |
| blockNumber     | int    | The block number of last time updating for market details |
| totalSupplyRaw  | string | Total amount of this asset supplied in Wei                |
| totalSupply     | string | Total amount of this asset supplied in ETH                |
| totalSupplyUSD  | string | Total amount of this asset supplied in USD                |
| supplyAPR       | string | Supply annualized interest rate                           |
| grossSupplyRaw  | string | Gross supply balance in Wei                               |
| grossSupplyUSD  | string | Gross supply balance in USD.                              |
| utilizationRate | string | Utilization rate(totalBorrowRaw / grossSupplyRaw)         |
| totalBorrowRaw  | string | Total amount of this asset borrowed in Wei                |
| totalBorrow     | string | Total amount of this asset borrowed in ETH                |
| totalBorrowUSD  | string | Total amount of this asset borrowed in USD                |
| borrowAPR       | string | Borrow annualized interest rate                           |
| oraclePrice     | string | The price of the asset relative to Wei                    |
| price           | string | The price of the asset relative to USD                    |

**Example:**

**Request url**

> [https://api.lendf.me/v2/info?data=markets](https://api.lendf.me/v2/info?data=markets)(Recommended)

**Response:**

```
{
  "markets": {
    "0xeb269732ab75A6fD61Ea60b06fE994cD32a83549": {
      "asset": "0xeb269732ab75A6fD61Ea60b06fE994cD32a83549",
      "name": "dForce",
      "symbol": "USDx",
      "decimal": 18,
      "balance": "454038488256182756875394",
      "blockNumber": 9771237,
      "totalSupplyRaw": "1239644669859264971432835",
      "totalSupply": "1239644.669859264971432835",
      "totalSupplyUSD": "1239644.669859264971432835",
      "supplyAPR": "0.0362099931188832",
      "grossSupplyRaw": "1219762214821004714561308",
      "grossSupplyUSD": "1219762.214821004714561308",
      "utilizationRate": "62.77",
      "totalBorrowRaw": "765723726564821957685914",
      "totalBorrow": "765723.726564821957685914",
      "totalBorrowUSD": "765723.726564821957685914",
      "borrowAPR": "0.0588579915363552",
      "oraclePrice": "7574609907589759",
      "price": "1.00"
    }
  },
  "totalSupplyBalance": "203339.523557695601301218345913711472473966",
  "totalSupplyBalanceUSD": "26844883.900086973735317793",
  "totalBorrowBalance": "57740.096148362377614354396158410512052086",
  "totalBorrowBalanceUSD": "7622847.493506801220863362",
  "totalCollateralizationRatio": "3.521634654629211403",
  "userCount": 1248,
  "collateralRatio": "1250000000000000000",
  "liquidationDiscount": "100000000000000000",
  "originationFee": "100000000000000"
}
```

**Error message**

> none

**Attention!**

We will release a new version soon, and in the new verison, the returning data of querying market information will be changed slightly, so if possible, please use the latest version, V2!
In the V2 version, the type of `markets` is `object`,
In the V1 version, the type of `markets` is `array`, and the returning data like following:

```
{
  "markets": [
    {
      "asset": "0xeb269732ab75A6fD61Ea60b06fE994cD32a83549",
      "name": "dForce",
      "symbol": "USDx",
      "decimal": 18,
      "balance": "300756278713149900416366",
      "blockNumber": 9247588,
      "totalSupplyRaw": "1505215058620996270431627",
      "totalSupply": "1505215.058620996270431627",
      "totalSupplyUSD": "1505215.058620996270431627",
      "supplyAPR": "0.0722734140263904",
      "grossSupplyRaw": "1495809221075834220226050",
      "grossSupplyUSD": "1495809.22107583422022605",
      "utilizationRate": "79.89",
      "totalBorrowRaw": "1195052942362684319809684",
      "totalBorrow": "1195052.942362684319809684",
      "totalBorrowUSD": "1195052.942362684319809684",
      "borrowAPR": "0.0923084705432736",
      "oraclePrice": "7369196757553426",
      "price": "1.00"
    }
  ],
  "totalSupplyBalance": "62235.093754153167704753550999113532604102",
  "totalSupplyBalanceUSD": "8445302.2224385856328138",
  "totalBorrowBalance": "20293.927067620951553618110326809782177384",
  "totalBorrowBalanceUSD": "2753885.903076163378632703",
  "totalCollateralizationRatio": "3.066685592531251828",
  "userCount": 291,
  "collateralRatio": "1250000000000000000",
  "originationFee": "500000000000000",
  "liquidationDiscount": "100000000000000000"
}
```

### Liquidation history

> Returns all liquidation history.

**Url**

> [https://api.lendf.me/v1/info?data=liquidateBorrow](https://api.lendf.me/v1/info?data=liquidateBorrow)

**Request Method**

```
GET
```

**Request Parameters**

| Parameter  | value                                | description                                                                                                      |
| ---------- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| address    | User account address(default is all) | The acount you want to get liquidation history(case-insensitive letters)                                         |
| pageNumber | Page number(default is 1)            | The number of page to get                                                                                        |
| pageSize   | Page size (default is 50)            | The total number of accounts list at the current page(the parameter cannot be zero and less than or equal to 50) |

**Return Result**

| field   | type   | description                |
| ------- | ------ | -------------------------- |
| data    | array  | Liquidate information list |
| request | object | The size of liquidate data |

**_data_**

| name            | type   | description                                   |
| --------------- | ------ | --------------------------------------------- |
| transactionHash | string | Transaction hash                              |
| blockNumber     | int    | When the transaction was confirmed            |
| targetAccount   | string | Liquidated address                            |
| liquidator      | string | Liquidator address                            |
| assetBorrow     | object | Asset information borrowed by liquidated user |
| assetCollateral | object | Asset information supplied by liquidated user |

**_assetBorrow_**

| name                     | type   | description                                                           |
| ------------------------ | ------ | --------------------------------------------------------------------- |
| asset                    | string | Asset address borrowed by liquidated user                             |
| name                     | string | The name of the asset                                                 |
| symbol                   | string | The symbol of the asset                                               |
| decimal                  | int    | The number of decimals used for the asset                             |
| borrowBalanceBefore      | string | Borrowing amount before liquidation                                   |
| borrowBalanceAccumulated | string | Total amount of principal and interest of the loan before liquidation |
| amountRepaid             | string | The number of asset was repaid                                        |
| borrowBalanceAfter       | string | Borrowing amount after liquidation                                    |

**_assetCollateral_**

| name                         | type   | description                                                             |
| ---------------------------- | ------ | ----------------------------------------------------------------------- |
| asset                        | string | Asset address supplied by liquidated user                               |
| name                         | string | The name of the asset                                                   |
| symbol                       | string | The symbol of the asset                                                 |
| decimal                      | int    | The number of decimals used for the asset                               |
| collateralBalanceBefore      | string | Supply amount before liquidation                                        |
| collateralBalanceAccumulated | string | Total amount of principal and interest of the supply before liquidation |
| amountSeized                 | string | The number of collateral seized by liquidator                           |
| collateralBalanceAfter       | string | Supply amount after liquidation                                         |

**_request_**

| field           | type | description                               |
| --------------- | ---- | ----------------------------------------- |
| pageSize        | int  | Current page size                         |
| pageNumber      | int  | Current page number                       |
| totalSize       | int  | Total number of liquidation history lists |
| totalPageNumber | int  | Total number of pages by page size        |

**Example**

**Request url**

> [https://api.lendf.me/v1/info?data=liquidateBorrow&address=all](https://api.lendf.me/v1/info?data=liquidateBorrow&address=all)

**Response:**

```
{
  "data": [
    {
      "transactionHash": "0xc2a1b0d2cacbd02a120c7959985d553679868d1821dadb97fe8b209df614e95e",
      "blockNumber": 9236926,
      "targetAccount": "0xdA1d0C7f174effBA98Ea1E31424418DC9aeaEa22",
      "liquidator": "0x932906251479106D96904184aA4985C1a291B35d",
      "assetBorrow": {
        "asset": "0x3212b29E33587A00FB1C83346f5dBFA69A458923",
        "name": "The Tokenized Bitcoin",
        "symbol": "imBTC",
        "decimal": 8,
        "borrowBalanceBefore": "0.09779123",
        "borrowBalanceAccumulated": "0.09779127",
        "amountRepaid": "0.01897006",
        "borrowBalanceAfter": "0.07882121"
      },
      "assetCollateral": {
        "asset": "0xdAC17F958D2ee523a2206206994597C13D831ec7",
        "name": "Tether USD",
        "symbol": "USDT",
        "decimal": 6,
        "collateralBalanceBefore": "1009.133987",
        "collateralBalanceAccumulated": "1009.137477",
        "amountSeized": "176.372465",
        "collateralBalanceAfter": "832.765012"
      }
    }
  ],
  "request": {
    "pageSize": 1,
    "pageNumber": 1,
    "totalSize": 1,
    "totalPageNumber": 1
  }
}
```

**Error message**

```
Returns error message
```

| Error name | Error message                     | Error parameter | description                                    |
| ---------- | --------------------------------- | --------------- | ---------------------------------------------- |
| Error      | targetAccount Parameter error!!   | targetAccount   | The input parameter is not an Ethereum address |
| Error      | assetBorrow Parameter error!!     | assetBorrow     | The input parameter is not an Ethereum address |
| Error      | assetCollateral Parameter error!! | assetCollateral | The input parameter is not an Ethereum address |

### List borrowed accounts

> Get accounts list have borrowed asset.

**Url**

> [https://api.lendf.me/v1/account](https://api.lendf.me/v1/account)

**Request Method**

```
GET
```

**Request Parameters**

| Parameters | value       | description                                                                                                      |
| ---------- | ----------- | ---------------------------------------------------------------------------------------------------------------- |
| pageNumber | Page number | The number of page to get                                                                                        |
| pageSize   | Page size   | The total number of accounts list at the current page(the parameter cannot be zero and less than or equal to 50) |

**Return Result**

| field    | type   | description                                 |
| -------- | ------ | ------------------------------------------- |
| accounts | array  | List of borrowed account information        |
| request  | object | Information about page number and page size |

**_accounts_**

| name            | type   | description                          |
| --------------- | ------ | ------------------------------------ |
| address         | string | Borrowing account address            |
| totalSupplyWeth | string | Total Supply in ETH                  |
| totalSupplyUSD  | string | Total supply value in US dollars     |
| totalBorrowWeth | string | Total borrow in ETH                  |
| totalBorrowUSD  | string | Total borrow value in US dollars     |
| shortfallWeth   | string | shortfall in ETH.                    |
| collateralRate  | double | Divide total supply and total borrow |
| borrow          | array  | Borrowing assets information         |
| supply          | array  | Suppling assets information          |

**_borrow_**

| name        | type   | description                               |
| ----------- | ------ | ----------------------------------------- |
| asset       | string | Borrowing asset address                   |
| name        | string | The name of the asset                     |
| symbol      | string | The symbol of the asset                   |
| decimal     | int    | The number of decimals used for the asset |
| oraclePrice | string | The asset price got from contract         |
| amount      | string | The amount of borrowed asset              |
| USDValue    | string | The USD value of borrowed asset           |
| price       | string | The price of borrowed asset in USD        |

**_supply_**

| name        | type   | description                               |
| ----------- | ------ | ----------------------------------------- |
| asset       | string | Suppling asset address                    |
| name        | string | The name of the asset                     |
| symbol      | string | The symbol of the asset                   |
| decimal     | int    | The number of decimals used for the asset |
| oraclePrice | string | The asset price got from contract         |
| amount      | string | The amount of supplied asset              |
| USDValue    | string | The USD value of supplied asset           |
| price       | string | The price of supplied asset in USD        |

**_request_**

| name            | type | description                        |
| --------------- | ---- | ---------------------------------- |
| blockNumber     | int  | Number of current blocks           |
| pageSize        | int  | Current page size                  |
| pageNumber      | int  | Current page number                |
| totalSize       | int  | Total number of account lists      |
| totalPageNumber | int  | Total number of pages by page size |

**Example**

**Request Url**

> [https://api.lendf.me/v1/account](https://api.lendf.me/v1/account)

**Response:**

```
{
  "accounts": [
    {
      "address": "0x2f04a067bedcC3a8fce349cB1bb234c17c4a83e2",
      "totalSupplyWeth": "0.004664242210516262133056",
      "totalSupplyUSD": "0.632937667967056829",
      "totalBorrowWeth": "0.003744252050767163967257764908328922",
      "totalBorrowUSD": "0.508095003289104197",
      "shortfallWeth": "0.000016072852942692826016206135411152",
      "collateralRate": 1.245707326129554,
      "borrow": [
        {
          "asset": "0xeb269732ab75A6fD61Ea60b06fE994cD32a83549",
          "name": "dForce",
          "symbol": "USDx",
          "decimal": 18,
          "oraclePrice": "0.007369196757553426",
          "amount": "0.508095003289104197",
          "USDValue": "0.508095003289104197",
          "price": "1.00"
        }
      ],
      "supply": [
        {
          "asset": "0xdAC17F958D2ee523a2206206994597C13D831ec7",
          "name": "Tether USD",
          "symbol": "USDT",
          "decimal": 6,
          "oraclePrice": "0.007346836819407404",
          "amount": "0.634864",
          "USDValue": "0.632937667967056829",
          "price": "0.996965756393584814321456436931"
        }
      ]
    }
  ],
  "request": {
    "blockNumber": 9251631,
    "pageSize": 1,
    "pageNumber": 1,
    "totalSize": 33,
    "totalPageNumber": 33
  }
}
```

**Error message**

> Returns error message

| Error name | Error message                            | description                                             |
| ---------- | ---------------------------------------- | ------------------------------------------------------- |
| Error      | You should provide a non-zero parameter! | Input parameter is zero or page size is greater than 50 |

### Get max liquidation amount

> Returns max liquidation amount by **_targetAccount_**, **_assetBorrow_**, **_assetCollateral_**

**Url**

> [https://api.lendf.me/v1/liquidate?targetAccount=0x0eEe3E3828A45f7601D5F54bF49bB01d1A9dF5ea&assetBorrow=0xeb269732ab75A6fD61Ea60b06fE994cD32a83549&assetCollateral=0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2](https://api.lendf.me/v1/liquidate?targetAccount=0x0eEe3E3828A45f7601D5F54bF49bB01d1A9dF5ea&assetBorrow=0xeb269732ab75A6fD61Ea60b06fE994cD32a83549&assetCollateral=0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2)

**Request Method**

```
GET
```

**Request Parameters**

| Parameters      | value                                           | description                                     |
| --------------- | ----------------------------------------------- | ----------------------------------------------- |
| targetAccount   | Liquidated address                              | Target account to be liquidated                 |
| assetBorrow     | Asset address borrowed by Liquidated users      | Target account borrowed asset address           |
| assetCollateral | Asset address collateralizedby Liquidated users | Target account supplyied asset contract address |

**Return result**

| name            | type   | description                                     |
| --------------- | ------ | ----------------------------------------------- |
| targetAccount   | string | Target account to be liquidated                 |
| assetBorrow     | string | Target account borrowed asset address           |
| assetCollateral | string | Target account supplyied asset contract address |
| maxClose        | object | The number of liquidation requested             |
| amountSeize     | object | The number of collateral seized by liquidator   |

**_maxClose_**

| name        | type   | description                               |
| ----------- | ------ | ----------------------------------------- |
| name        | string | The name of the asset                     |
| symbol      | string | The symbol of the asset                   |
| decimal     | int    | The number of decimals used for the asset |
| oraclePrice | string | The asset price got from contract         |
| amountRaw   | string | Original amount of borrowed asset         |
| amount      | string | The number of borrowed asset in ETH       |
| USDValue    | string | The USD value of borrowed asset           |
| price       | string | The price of borrowed asset in USD        |

**_amountSeize_**

| name        | type   | description                               |
| ----------- | ------ | ----------------------------------------- |
| name        | string | The name of the asset                     |
| symbol      | string | The symbol of the asset                   |
| decimal     | int    | The number of decimals used for the asset |
| oraclePrice | string | The asset price got from contract         |
| amountRaw   | string | Original amount of mortgaged asset        |
| amount      | string | The number of mortgaged asset in ETH      |
| USDValue    | string | The USD value of mortgaged asset          |
| price       | string | The price of mortgaged asset in USD       |

**Example**

**Request Url**

> [https://api.lendf.me/v1/liquidate?targetAccount=0x0eEe3E3828A45f7601D5F54bF49bB01d1A9dF5ea&assetBorrow=0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2&assetCollateral=0xeb269732ab75A6fD61Ea60b06fE994cD32a83549](https://api.lendf.me/v1/liquidate?targetAccount=0x0eEe3E3828A45f7601D5F54bF49bB01d1A9dF5ea&assetBorrow=0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2&assetCollateral=0xeb269732ab75A6fD61Ea60b06fE994cD32a83549)

**Response:**

```
{
  "targetAccount": "0x0eEe3E3828A45f7601D5F54bF49bB01d1A9dF5ea",
  "assetBorrow": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2",
  "assetCollateral": "0xeb269732ab75A6fD61Ea60b06fE994cD32a83549",
  "maxClose": {
    "name": "Wrapped Ether",
    "symbol": "WETH",
    "decimal": 18,
    "oraclePrice": "1000000000000000000",
    "amountRaw": "0",
    "amount": "0.00",
    "USDValue": "0.00",
    "price": "135.700000000000012457"
  },
  "amountSeize": {
    "name": "dForce",
    "symbol": "USDx",
    "decimal": 18,
    "oraclePrice": "7369196757553426",
    "amountRaw": "0",
    "amount": "0.00",
    "USDValue": "0.00",
    "price": "1.00"
  }
}
```

**Error message**

> Returns error message

| Error name | Error message                     | Error parameter | description                                    |
| ---------- | --------------------------------- | --------------- | ---------------------------------------------- |
| Error      | targetAccount Parameter error!!   | targetAccount   | The input parameter is not an Ethereum address |
| Error      | assetBorrow Parameter error!!     | assetBorrow     | The input parameter is not an Ethereum address |
| Error      | assetCollateral Parameter error!! | assetCollateral | The input parameter is not an Ethereum address |
