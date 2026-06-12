---
title: "Installing LAMP"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by hcimis on 2012-04-03
Hello All,

This may be an easy fix for you to identify.  I have a VM of Ubuntu 11 on Vsphere.  I am trying to install LAMP so I can begin developing our new website on top of WordPress, but I have run into a snag.  I am unable to get the  Apache, MySQL and PHP installed.  I am using ```
sudo apt-get install
``` to install each item.

I get the following message:

Package [package name]is not available.....

E: Package [package name] has no installation canidate

I have also done ```
sudo apt-get update
``` and this runs but several of the websites come back with 404

---

### Post by codemaniac on 2012-04-03
Hello hcimis ,

Welcome to the UbuntuForums.
you are missing the package name .
```
sudo apt-get install ***package_name ***
```
have this fired in your terminal .

```
sudo apt-get install lamp-server^
```

---

### Post by hcimis on 2012-04-03
I did include the package name when running.  I just omitted it in the post.

---

### Post by mastablasta on 2012-04-03
have you tried using tasksel for instaling the stack?:
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

note this is install only tool and is not ment for unnistall.

---

### Post by hcimis on 2012-04-03
mastablasta

I get a 404 error when accessing this page.

---

### Post by hcimis on 2012-04-03
Just checked it again and it worked.

---

### Post by hcimis on 2012-04-03
I get the same message when trying to install tasksel.

---

### Post by hcimis on 2012-04-03
I was able to figure it out.  Our proxy was blocking.

---

