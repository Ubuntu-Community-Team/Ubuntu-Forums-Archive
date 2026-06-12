---
title: "Preserving list of installed software on upgrade"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by rlp1938 on 2010-03-23
I prefer to do a clean install of each new version of Ubuntu.
I do have a separate /home partition which I preserve during each new install. I also have many additional packages installed.
My question is:
How do I preserve the list of installed additional software so that I may readily reinstall all of it after each upgrade?

Thanks,
Bob Parker

---

### Post by patchwork on 2010-03-23
From the dpkg man page:

>  To make a local copy of the package selection states:
            dpkg --get-selections >myselections

       You might transfer this file to another computer, and install it
       there with:
            dpkg --clear-selections
            dpkg --set-selections <myselections

       Note that this will not actually install or remove anything, but
       just set the selection state on the requested packages. You will
       need some other application to actually download and install the
       requested packages. For example, run apt-get dselect-upgrade.

       Ordinarily, you will find that dselect(1) provides a more conve&#8208;
       nient way to modify the package selection states.


```
man dpkg
```

---

### Post by Rasa1111 on 2010-03-23
what about APTonCD? 

would that work for what you need?

---

### Post by rlp1938 on 2010-03-23
> **patchwork said:**
> From the dpkg man page:



```
man dpkg
```

Thanks for the information:
I also intend to preserve and restore after upgrade, /var/cache/apt/
What I hope to achieve by that is to minimise the actual download afterward.

Thanks again,
Bob Parker

---

### Post by patchwork on 2010-03-23
Keep in mind that when you upgrade, the packages you are restoring may not be the same version as is included with the new release...the first update may require updating each of the packages anyway.  Shouldn't be a deal-breaker, but it might catch you off guard if you weren't expecting it.

---

### Post by rlp1938 on 2010-03-23
> **patchwork said:**
> Keep in mind that when you upgrade, the packages you are restoring may not be the same version as is included with the new release...the first update may require updating each of the packages anyway.  Shouldn't be a deal-breaker, but it might catch you off guard if you weren't expecting it.

Sure. I'm just trying to minimise the required download, not avoid it altogether.

Thanks,
Bob Parker

---

### Post by tfultz33 on 2010-07-18
you mean to tell me that after each upgrade you have to re-download every program you installed before the upgrade? What's the point? Why shove out releases every 6 months when you lose the software you spent 6 months installing??
Linux simply hates dialup users.

---

### Post by Copernicus1234 on 2010-07-18
> **tfultz33 said:**
> you mean to tell me that after each upgrade you have to re-download every program you installed before the upgrade? What's the point? Why shove out releases every 6 months when you lose the software you spent 6 months installing??
Linux simply hates dialup users.

If you want to do a clean install, you have to reinstall all programs. Thats what a clean install means - to start from scratch.

If you dont want that, just do a ordinary system update instead.

In Windows, you cant even preserve a list of your installed software when you do a clean install. You have to remember everything you had installed and then find it on the web, download and install it again.  Which is particularly bad in Windows since Windows systems becomes slower and slower with time, meaning you want to do a clean install quite often. :)

---

### Post by rlp1938 on 2010-07-18
> **tfultz33 said:**
> you mean to tell me that after each upgrade you have to re-download every program you installed before the upgrade? What's the point? Why shove out releases every 6 months when you lose the software you spent 6 months installing??
Linux simply hates dialup users.

Not so! apt-get install aptoncd
Then check out the manual page for it.

---

### Post by tfultz33 on 2010-07-18
If i used an alternative cd and upgraded from 9.10 to 10.4 would it remove all my movie editing software and firefox addons etc?

---

### Post by tfultz33 on 2010-07-18
Thanks. I'll check out aptoncd

---

### Post by rlp1938 on 2010-07-25
> **tfultz33 said:**
> If i used an alternative cd and upgraded from 9.10 to 10.4 would it remove all my movie editing software and firefox addons etc?

AFAIK there should be no problem. I go the other way; I have have 2 partitions for all Ubuntu except /home and do a new clean install on those partitions alternating with each new release, I make sure that I DO NOT format /home at installation time.

---

