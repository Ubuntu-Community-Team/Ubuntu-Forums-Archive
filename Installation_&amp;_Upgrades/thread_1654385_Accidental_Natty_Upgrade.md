---
title: "Accidental Natty Upgrade?"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by zami on 2010-12-28
I set a computer that has been out of commission for over a year, to upgrading last night.

I *thought* I was going to 10.10, but when I checked my repositories when all was said and done, everything "Maverick" related was "disabled on upgrade to Maverick".  

Then to see "well what the heck *did* I upgrade to?",

System > About Ubuntu tells me
You are using Ubuntu 11.04
                - the Natty Narwhal - released in April 2011 and supported until October 2012.
	

Wha?

Am I really at 11.04?  Could I have upgraded to Natty by accident?

I don't think I'm really in Natty  - Unity isn't even an option, and it's the default choice in 11+, right?

I'v re-enabled all my needed repos.  Is this mis-identification going to cause me any problems down the road?  

-zami

edit:
I upgraded via the Update Manager, not the command line to get developer releases.  The Update Manager is set to "Normal releases".  I do have all update options checked - maverick-security, maverick-updates, maverick-proposed, and maverick-backports.

---

### Post by howefield on 2010-12-28
It is most likely this bug...

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

What is the output of the following terminal command ?

```
lsb_release -a
```

---

### Post by zami on 2010-12-28
> **howefield said:**
> It is most likely this bug...

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

What is the output of the following terminal command ?

```
lsb_release -a
```
Thank you!  I was just googling for "command line to tell Ubuntu version".

Looks like Maverick.

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

Off to read the bug link...

-zami

---

### Post by zami on 2010-12-28
Excellent.  So long as it's just the docs with the wrong info, and not antying actually in-charge of updates/upgrades, it's all good.

Thanks for the bug link.  :)

-zami

---

### Post by howefield on 2010-12-28
> **zami said:**
> Excellent.  So long as it's just the docs with the wrong info, and not antying actually in-charge of updates/upgrades, it's all good.

Yep, you have Maverick. I'm sure the documentation will be fixed shortly.

> Thanks for the bug link.  :)

You're welcome.

---

