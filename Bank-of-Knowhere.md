**Event** : Space Heroes CTF 2023

**Challenge** : Bank-of-Knowhere

**Description** : Groot is in dire need of some crucial intel about the Bank of Knowhere, but they only
share such classified information with their inner circle. To become a member of their inner circle,
one must have at least 2000₳ - Units in their bank account. Can you lend a hand to Groot in acquiring
this information?

**Vulnerability** : HTTP Parameter Pollution

We are presented with our current balance and a table of the balance of other members. We are
seemingly able to send currency to other members.

![image](https://user-images.githubusercontent.com/95172913/233913148-88fb71f6-3685-4993-b164-a1c5bfa5f4d9.png)


The request from clicking the ‘Submit’ button was captured in BurpSuite

![image](https://user-images.githubusercontent.com/95172913/233913203-d160b696-e4d7-423f-9cc3-61b4115b353b.png)


We can see the request contains URL/HTTP parameters to pass the information along to the server
for processing.


Can we change the parameters to send currency between accounts not owned by Groot?

![image](https://user-images.githubusercontent.com/95172913/233913226-0b49f1b2-d786-4fe7-b86e-558dffcfe99b.png)


Yes! 450 has transferred from Rocket to Gamora

![image](https://user-images.githubusercontent.com/95172913/233913238-2521d98e-642a-472c-822d-86add1a13039.png)


Can we change the sender and receiver parameters to try and give ourselves currency from another
account?

![image](https://user-images.githubusercontent.com/95172913/233913263-e907c521-e2e1-4737-8033-15d0999a84f5.png)
**Unsuccessful**


What happens if we add a second **receiver** parameter, maybe the server only checks the first
instance of a receiver parameter?...
![image](https://user-images.githubusercontent.com/95172913/233913297-957d564d-db6a-4798-9451-c9b0d93184ea.png)
**No Error, Looking Good!**

Success! We have been able to increase Groot’s balance!

![image](https://user-images.githubusercontent.com/95172913/233913322-767871db-4cca-44c8-8570-e65eed0b8874.png)


This method was repeated once more with the amount parameter increased to bring Groot’s balance
to over 2000.

This then let us access the **/admin** page, which gave us the flag.

![image](https://user-images.githubusercontent.com/95172913/233913337-fd308961-e272-44fd-9b2c-87af87626fde.png)
