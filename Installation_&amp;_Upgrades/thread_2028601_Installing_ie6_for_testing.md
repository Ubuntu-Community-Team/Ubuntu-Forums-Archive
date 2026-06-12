---
title: "Installing ie6 for testing"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by proggrammer on 2012-07-18
Hi,

I am using ubuntu 12.04 LTS 64-bit, kindly suggest me a pointer/instruction to install ie6 on my machine.

---

### Post by na5h on 2012-07-18
These instructions should work for IE9, 8 and 7...but not for IE6, I'm afraid:
[http://www.webupd8.org/2011/09/test-websites-in-internet-explorer-9-8.html](http://www.webupd8.org/2011/09/test-websites-in-internet-explorer-9-8.html)

According to the Wine Application Database, it's not going to work in Ubuntu 12.04 through Wine either (although it did work back in Ubuntu 10.04 with Wine 1.2-rc1):
[http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)

I suppose the only way to get IE6 working under Ubuntu would be to run Windows on a virtual machine...

---

### Post by Mark Phelps on 2012-07-18
> **proggrammer said:**
> Hi,

I am using ubuntu 12.04 LTS 64-bit, kindly suggest me a pointer/instruction to install ie6 on my machine.

That is a complete waste of time!  MS has been actively pushing a compaign for over six months to kill off usage of IE6.

Why test with something that is now obsolete?

---

### Post by QIII on 2012-07-18
> **Mark Phelps said:**
> That is a complete waste of time!  MS has been actively pushing a compaign for over six months to kill off usage of IE6.

Why test with something that is now obsolete?

This.

---

### Post by na5h on 2012-07-19
> **Mark Phelps said:**
> That is a complete waste of time!  MS has been actively pushing a compaign for over six months to kill off usage of IE6.

Why test with something that is now obsolete?

I agree! If you want to, you could use something like
```
<!--[if IE 6]>
CONTENT ONLY VIEWABLE TO IE 6.0
<![endif]-->
```
in your HTML to tell people using IE 6 to upgrade their browser...

---

