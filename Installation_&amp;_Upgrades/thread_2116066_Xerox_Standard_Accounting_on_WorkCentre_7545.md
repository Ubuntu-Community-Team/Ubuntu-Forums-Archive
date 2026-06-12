---
title: "Xerox Standard Accounting on WorkCentre 7545"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by fabfisc on 2013-02-14
Hi,
i'm facing some problem with XSA.

I posted in an old thread [here]("http://ubuntuforums.org/showthread.php?t=1081388&highlight=Xerox+Standard+Accounting"), so i opened one new.

In my WorkCentre 7545 configuration i've the following config (see attachments).

I have added the suggested lines in ppd:

[I]*%                Generic Accounting
*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: **XSAGroup**
*JCLAccounting XSADisabled/Disabled: ""
*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;"
*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GENERALACCT,MyGenAcctID<22>;<0A>"
*JCLAccounting **XSAGroup**/XSA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,**user_bn**<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GROUPACCT,**2**<22>;<0A>"
*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,MyAcctID<22>;<0A>"
*JCLCloseUI: *JCLAccounting
[/I]

But, still now, cannot print using the "user_bn" account and "2" as groupID or "3" (new added for test), and i'm getting "*_The job was deleted due to invalid accounting IDs._*".

Can you help me to solve that?

---

### Post by fabfisc on 2013-02-18
Partially solved in this way:

```
*%                Generic Accounting
*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: **XSAGroup**
*JCLAccounting XSADisabled/Disabled: ""
*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,**user_bn**<22>;"
*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,**user_bn**<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GENERALACCT,**2**<22>;<0A>"
*JCLAccounting XSAGroup/XSA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,**user_bn**<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GROUPACCT,**2**<22>;<0A>"
*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,**user_bn**<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,**2**<22>;<0A>"
*JCLCloseUI: *JCLAccounting
```

Now i want to use color user, i defined a user for color print's, but even i substitute it instead of "user_bn" i get b/w prints!

Any suggestion?

---

### Post by Bucky Ball on 2013-02-18
Which Ubuntu release are you using?

---

### Post by fabfisc on 2013-02-18
I've tested on:

Ubuntu 10.10
Ubuntu 11.10
Ubuntu 12.04.1 LTS (even 64bit)
Mint 14 Nadia.

---

