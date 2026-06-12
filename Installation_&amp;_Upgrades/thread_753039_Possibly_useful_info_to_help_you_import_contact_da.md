---
title: "Possibly useful info to help you import contact data into Evolution"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by alliterationArtiste on 2008-04-12
I managed to solve my Evolution CONTACT import issue by 'spoofing' a csv import file from my particular data source.

The evolution import will only import csv files in a known format (you probably know this by now!) so i had to work out what that format was. I ran an import from a vritual machine configured with outlook, found out what the format was and then created a sql script to import.

If you are importing from Microsoft CRM then this script will be of huge interest. Otherwise what it shows you is the structure of the csv file needed to import into Evolution as an outlook csv import file.

I've only done contacts which was all I needed but I'm sure mail could be done in the same way if needed.

For those not familiar with sql, the field names are the bits after the 'as' keyword.

mysourceSystemFieldName as [Target CSV File Field Name]

If there is no 'as' keyword then the source field and target fields have the same name. Hope this is of benefit to someone.

select

	c.salutation as Title,

	c.firstName as [First Name],

	c.middleName as [Middle Name],

	c.lastName as [Last Name],

	c.suffix,

	a.name as Company,

	Department,

	c.jobTitle as [Job Title],

	addr.Line1 as [Business Street],

	addr.Line2 as [Business Street 2],

	addr.Line3 as [Business Street 3],

	addr.city as [Business City],

	addr.county as [Business State],

	addr.postalCode as [Business Postal Code],

	addr.country as [Business Country/Region],

	caddr.Line1 as [Home Street],

	caddr.Line2 as [Home Street 2],

	caddr.Line3 as [Home Street 3],

	caddr.city as [Home City],

	caddr.county as [Home State],

	caddr.postalCode as [Home Postal Code],

	caddr.country as [Home Country/Region],

	null as [Other Street],

	null as [Other Street 2],

	null as [Other Street 3],

	null as [Other City],

	null as [Other State],

	null as [Other Postal Code],

	null as [Other Country/Region],

	null as [Assistant's Phone],

	a.fax as [Business Fax],

	a.telephone1 as [Business Phone],

	a.telephone2 as [Buiness Phone 2],

	null as Callback,

	null as [Car Phone],

	a.telephone1 as [Company Main Phone],

	null as [Home Fax],

	c.telephone1 as [Home Phone],

	c.telephone2 as [Home Phone 2],

	null as ISDN,

	c.mobilePhone as [Mobile Phone],

	null as [Other Fax],

	null as [Other Phone],

	null as Pager,

	null as [Primary Phone],

	null as [Radio Phone],

	null as [TTY/TDD Phone],

	null as Telex,

	null as Account,

	null as Anniversary,

	null as [Assistant's Name],

	null as [Billing Information],

	null as Birthday,

	null as [Business Address PO Box],

	null as [Categories],

	null as Children,

	null as [Directory Server],

	c.emailAddress1 as [E-mail Address],

	null as [E-mail Type],

	null as [E-mail Display Name],

	c.emailAddress2 as [E-mail 2 Address],

	null as [E-mail 2 Type],

	null as [E-mail 2 Display Name],

	null as [E-mail 3 Address],

	null as [E-mail 3 Type],

	null as [E-mail 3 Display Name],

	null as Gender,

	null as [Government ID Number],

	null as Hobby,

	null as [Home Address PO Box],

	null as Initials,

	null as [Internet Free Busy],

	null as Keywords,

	null as [Language],

	null as Location,

	null as [Manager's Name],

	null as Mileage,

	null as Notes,

	null as [Office Location],

	null as [Organizational ID Number],

	null as [Other Address PO Box],

	null as Priority,

	null as [Private],

	null as [Profession],

	null as [Referred By],

	null as [Sensitivity],

	null as Spouse,

	null as [User 1],

	null as [User 2],

	null as [User 3],

	null as [User 4],

	c.webSiteUrl as [Web Page]



	

	







from contactBase c

left join accountBase a on a.accountId=c.accountId

left join customerAddressBase addr on a.accountId=addr.parentId and addr.addressNumber=1

left join customerAddressBase caddr on c.contactId=caddr.parentId and caddr.addressNumber=1

---

