---
title: "New to 16.04 and I noticed its really hard to remove &quot;online accounts&quot;"
date: 2016-06-07
forum: Installation &amp; Upgrades
---

### Post by Karl_Hungus on 2016-06-07
Ok so new to 16.04 and I noticed its really hard to remove "online accounts" even if you never logged in via Ubuntu "Online Accounts" service.

Does anybody have any insight into where these files are stored.

I really don't like the idea of Ubuntu automatically logging me into facebook.

this shows up under SystemSettings/OnlineAccounts in the GUI



Any help would be greatly appreciated,

thank you in advance.

---

### Post by X-RED_Tech on 2016-06-08
Ubuntu won't log you automatically anywhere unless you explicitly add such accounts to the "online accounts" so you can leave that alone and just don't use it.

---

### Post by grahammechanical on 2016-06-08
For Online Accounts to do anything we have to set up those services by registering with the service and then entering our usernames and passwords in the Online Accounts utility. Then when we want to access one of those services Online Accounts will login for us.

This is the official documentation for Online Accounts.

[https://help.ubuntu.com/16.04/ubuntu-help/accounts.html](https://help.ubuntu.com/16.04/ubuntu-help/accounts.html)

If you do not have accounts with any of those services or if you have not set up those services in Online Accounts then Ubuntu will not log you in to those accounts. It cannot log you in to those services and anyway Online Accounts will only do its stuff if we open Online Accounts and instruct it to make a connection to a particular service.

The fact is that Online Accounts is installed but deactivated until we set it up to do something and then instruct it to do what we want.

Regards.

---

### Post by Karl_Hungus on 2016-06-08
Thank you both for the responses, I feel its no issue, I just won't use the service as of now.

---

