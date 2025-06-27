
# Discovery


Pelo que eu percebi o código para as imagens - um svg, deverá ser injectado no datacontract-editor/templates/render.js


```
export function renderDataContract(dataContract) {
	const local_date = new Date().toLocaleDateString();

    const mermaidCode = generateMermaid(dataContract);

    const svg = renderSvg(mermaidCode);

    return nunjucks.render("datacontract.html", { datacontract: dataContract, mermaid_diagram: svg, formatted_date: local_date, datacontract_cli_version: version });
}
```

A variavel "mermaid_diagram" existe no datacontract.html que é um template que está no datacontract-cli (datacontract-cli\datacontract\templates\datacontract.html). Ou seja, outro repositório. No GIT Hub eles dizem que para o caso de se mudarem os templates é preciso compilalos novamente.

Experimentei gerar um svg dummy, para testar mas aparentemente esta a precisar de um modulo de JS que é o puppeteer para renderizar a imagem. No entanto, esse módulo parece estar a entrar em conflit com a framework que está a ser também usada que é o vite. Com isto não consegui testar nada.

No Data Contract Manager CE eles parecem estar a usar React Flow para fazer os diagramas. Mas pelo que percebi é um major refactor do que eles têm no datacontract-editor porque o react e o vite não são compatíveis.



# Testing


**Build Docker Image**

```
docker build -t datacontract/editor .
```

**Run Docker**

```
docker run -p 8173:80 datacontract/editor
```


```
docker run -v "C:\Users\DATASRM\Documents\REPOS\work-azuredevops\data.data-catalog.metadata-management\data-products\prod-vNext:/usr/local/apache2/htdocs/datacontracts" -p 8173:80 datacontract/editor
```


# React Flow Sample JSON


```
{
    "nodes": [
        {
            "id": "SalesOrderUpdated",
            "type": "model",
            "data": {
                "name": "SalesOrderUpdated",
                "fields": [
                    {
                        "name": "SalesOrder",
                        "type": "record",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 0
                    },
                    {
                        "name": "OmsNumber",
                        "description": "The OMS number of the sales order. The structure of the OMS number is described on https://dev.azure.com/STARK-IT/Athene%20Program/_wiki/wikis/Athene-Program.wiki/553/Number-Series",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "CompanyCode",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "OrderNumber",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "RequisitionNumber",
                        "type": "long",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "BuildingSite",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "CustomerReference",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "SalesHandlerId",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "StoreId",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "DeductionPercentage",
                        "type": "double",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "DeliveryNotes",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "PickUpStoreId",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "DeliveryCode",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "DeliveryDate",
                        "description": "Represents a point in time, typically expressed as a date and time of day, relative to Coordinated Universal Time (UTC).",
                        "type": "timestamp_tz",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "CreditNote",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "OrderDate",
                        "description": "Represents a point in time, typically expressed as a date and time of day, relative to Coordinated Universal Time (UTC).",
                        "type": "timestamp_tz",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "CountryCode",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "PaymentType",
                        "description": "Enum Description: [Payment Type](#payment-type)",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "TotalPriceInclVat",
                        "type": "double",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "InvoiceNumber",
                        "type": "long",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "CustomerNumber",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "MdmCustomerNumber",
                        "description": "Mdm data",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "IsInternalTrade",
                        "description": "Inferred from MDM Customer data. If the matched customer to the order is of type \"InternalCustomer\", this field is set to true.",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "OrderStatus",
                        "description": "Enum Description: [Order Status](#order-status)",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "IsDiscountApplied",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "OrderNote",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "DeliveryContactInfo",
                        "description": "Object Mapping: [Delivery Contact Info](#delivery-contact-info)",
                        "type": "record",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "ContactPhoneNumber",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 2
                    },
                    {
                        "name": "EmailAddress",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 2
                    },
                    {
                        "name": "DeliveryAddress",
                        "description": "Object Mapping: [Delivery Address](#delivery-address)",
                        "type": "record",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "RouteId",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 2
                    },
                    {
                        "name": "CustomerName",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 2
                    },
                    {
                        "name": "StreetAndNumber",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 2
                    },
                    {
                        "name": "PostalCodeAndCity",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 2
                    },
                    {
                        "name": "Address4",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 2
                    },
                    {
                        "name": "TermsOfPayment",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "ShippingCondition",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "CashPayment",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "SalesPersonNumber",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "ManualCaseNumber",
                        "type": "long",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "EditCode",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "OrderLockId",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "PointOfSaleMarking",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "NoDeliveryFee",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "NoPackagingFee",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "NoDispatchFee",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "IsDeleted",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "PickingInstruction",
                        "description": "Only populated if MKTYP2 == 'X'",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "MarkingInstruction",
                        "description": "Only populated if MKTYP4 == 'X'",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "DeliveryInstruction",
                        "description": "Only populated if MKTYP3 == 'X'",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "ReturnReasonCode",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "IsReadyForPicking",
                        "description": "True -> if message in topic",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "DeliveryMethod",
                        "description": "21st position of GDATAL string then mapped into Enum. Enum Description: [Delivery Method](#delivery-method)",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "OriginCode",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "IsRental",
                        "description": "true if OriginCode is 'NH'",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "WebOrderId",
                        "type": "long",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "CashRegisterId",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "BatchNumber",
                        "type": "long",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "InvoiceDate",
                        "description": "Represents a point in time, typically expressed as a date and time of day, relative to Coordinated Universal Time (UTC).",
                        "type": "timestamp_tz",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "ProjectSalesNumber",
                        "description": "Inferred through building site",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "ReservationStatus",
                        "description": "Enum Description: [Reservation Status](#reservation-status)",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "DeliveryWeek",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "IsSpecialOrder",
                        "description": "Is calculated in OMS. If OMS Movement Type is not Order, or all Order Lines are return.",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "OrderLines",
                        "description": "Object Mapping: [Sales Order Line](#sales-order-line)",
                        "type": "array",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "FikNumber",
                        "type": "string",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "DocumentReferences",
                        "description": "Object Mapping: [Document Reference](#document-reference)",
                        "type": "array",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "IsUnknownCustomer",
                        "description": "Inferred in OMS with data received from Aspect4. If GIDENT is \"7120\" in messages received on this topic, the message represents an unknown customer. This is applied to Sales Orders in OMS when customer number matches one of the unknown customers from Aspect 4.",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "ValueDate",
                        "description": "Represents a point in time, typically expressed as a date and time of day, relative to Coordinated Universal Time (UTC).",
                        "type": "timestamp_tz",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "ClosedBeforeSnapshot",
                        "description": "OMS managed field. We mark property to true when we run the snapshot and the order is in status PaidInCashOrDebited",
                        "type": "boolean",
                        "primary": false,
                        "unique": false,
                        "required": true,
                        "indent": 1
                    },
                    {
                        "name": "RouteId",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    },
                    {
                        "name": "SequenceNumber",
                        "type": "int",
                        "primary": false,
                        "unique": false,
                        "required": false,
                        "indent": 1
                    }
                ]
            }
        }
    ],
    "edges": []
}
```


