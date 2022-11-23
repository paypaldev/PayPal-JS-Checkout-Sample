![PayPal Developer Cover](https://github.com/paypaldev/.github/blob/main/pp-cover.png)
<a href="https://twitter.com/paypaldev" target="_blank">
   <img alt="Twitter: PayPal Developer" src="https://img.shields.io/twitter/follow/paypaldev?style=social" />
</a>
# PayPal-JS Standard-Checkout-Sample

This code sample shows how to set up standard payments on your checkout page so your buyers can pay with PayPal, debit and credit cards, Pay Later options, Venmo, and alternative payment methods.This code sample uses the [JavaScript SDK](https://developer.paypal.com/sdk/js/reference). The client-side sample code adds payment buttons to your website that capture the payment immediately. If you need to store the resulting transaction details in a database or want to fulfill orders automatically, use the included full-stack example code instead.

If you want to create this app from scratch, follow the [standard checkout integrartion](https://developer.paypal.com/docs/checkout/standard/integrate/) guide from the [PayPal Developer](https://developer.paypal.com/home) docs.

## Styling PayPal Buttons

In this code sample, you can find the following code. The PayPal SDK allows you to do some [customization](https://developer.paypal.com/sdk/js/reference/#link-buttons) to the PayPal buttons. You can change the layout, colors, size, label, and more.

```javascript
    style: {
        color: "gold",
        shape: "rect",
        layout: "vertical"
    }
```

## Create Order
The `createOrder()` callback allows you to create the request of your order with the following properties from the [V2 orders create call](https://developer.paypal.com/api/orders/v2/#orders-create-request-body): item_total, purchase_units, and more.

```javascript
createOrder: (data, actions) => {
    const createOrderPayload = {
        purchase_units: [
            {
                amount: {
                    value: "1.00"
                }
            }
        ]
    };

    return actions.order.create(createOrderPayload);
},
```

## Approve Order
The `onApprove()` allows doing something with the order details after the order has been created. You can learn more about the [onApprove()](https://developer.paypal.com/sdk/js/reference/#link-onapprove) callback in your docs.

```javascript
onApprove: (data, actions) => {
    const captureOrderHandler = (details) => {
        const payerName = details.payer.name.given_name;
        console.log('Transaction completed');
    };

    return actions.order.capture().then(captureOrderHandler);
},
```

## Run this App
Replace **YOUR-CLIENT-ID-CREDENTIALS** in the SDK <script src> with your own sandbox client ID from one of your [REST apps](https://www.paypal.com/signin?returnUri=https%3A%2F%2Fdeveloper.paypal.com%2Fdeveloper%2Fapplications%2F&_ga=1.84996752.841672670.1664266268). This ensures the payments will be sent to the correct account. Note which sandbox Business account corresponds to the REST app you are using.

Just open the `index.html` file and you should see the following buttons.

![paypal buttons](SC-paypal-buttons.png)

## PayPal Developer Community
The PayPal Developer community helps you build your career, while also improving PayPal products and the developer experience. You’ll be able to contribute code and documentation, meet new people and learn from the open-source community.
 
* Website: [developer.paypal.com](https://developer.paypal.com)
* Twitter: [@paypaldev](https://twitter.com/paypaldev)
* GitHub:  [@paypal](https://github.com/paypal)
