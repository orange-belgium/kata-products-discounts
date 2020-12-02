# Kata Products Promotions
### User story
As a user I want to able to see all the promotions I have, based on the products I own, so that I can check if the products I own give me good advantages.

### Acceptance criterias
The mobile team requires an API allowing the application to display the list of promotions a customer have. The endpoint will be a **POST** on **/promotions** with the following payload as an example:

```json
{
    "clientType":"retail",
    "products":[
        {
            "id":"A"
        },
        {
            "id":"B"
        },
        {
            "id":"C"
        },
        {
            "id":"C"
        },
        {
            "id":"E"
        }
    ]
}
```

There are 2 possible types of client: 
* **retail**
* **business**

Regarding the products, the company is owning five products identified by:
* **A**
* **B**
* **C**
* **D**
* **E**

> **Important note:** a client can only have maximum **one** product A and maximum **one** product B but can have **multiple** products C, D and E.

The company has currently two discounts available: 
* a first discount identified by **X**
* a second discount identified by **Y**.

Business has given the following rules:
* For **retail** clients:

Has product A | Number of product C and D | Number of product E | Number of discount X | Number of discount Z
------------ | ------------- | ------------- | ------------- | -------------
false |	0	|0	|0	|0
false	|0|	1|	0	|0
false|	0|	n>1|	0	|0
false|	1	|0|	0	|0
false	|1|	1|	0	|0
false	|1	|n>1	|0|	0
false	|m>1|	0|	m	|0
false|	m>1|	1	|m|	0
false|	m>1	|n>1	|m	|0
true|	0	|0	|0	|0
true|	0	|1	|0	|1
true|	0	|n>1	|0|	n
true	|1	|0	|1|	0
true|	1	|1	|1	|1
true|	1	|n>1	|1|	n
true|	m>1|	0	|m	|0
true	|m>1|	1	|m|	1
true|	m>1	|n>1	|m	|n

* For **business** clients: the same rules as above are applied **EXCEPT** that he needs to have **product A and product B**. If the business client doesn't have product B he is **not eligible to any promotion**.

Mobile team is expecting to receive as a response a list of promotions being given to the customer as well as their **quantity (number of the same promotion being given to the customer)**.

The response API contract interface given to the mobile team is the following:

```json
[
    {
        "id":"X",
        "quantity":2
    },
    {
        "id":"Y",
        "quantity":0
    }
]
```

### To do
* Create a public repository on GitHub so you can share the link later on. You'll be able to push your code as long as you're progressing on this exercise
* Create an API in **SpringBoot** or **Node.js** answering the needs above

> Keep in mind that this API need to be scalable in case other promotions come into the picture.

### Contact
In case of questions, feel free to contact:  [Kevin BEAULIEU](mailto:kevin.beaulieu@orange.com?subject=Kata%20Products%20Promotions)

License
----

MIT
