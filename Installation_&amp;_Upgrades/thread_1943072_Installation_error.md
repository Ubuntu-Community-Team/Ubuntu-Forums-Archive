---
title: "Installation error"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by jbw31697 on 2012-03-18
I am running Windows7 Ultimate

I have been trying to install Ubuntu 11.10 into my Windows7 installation. I am using the link on the main page where it says to install alongside Windows. It extracts and goes for about 8 minutes of installation then gives me an error message;
```
An error occurred
Permission Denied
For more information see log file 

```Logfile (this is the last few entries of the logfile where this error is repeated several times)
```
[Errno 13] Permission denied: 'J:\\wubildr'
```

Can someone please help me?

---

### Post by aoidenyx on 2012-03-20
I have a similar issue but a different error. Wish there was a fix.

---

### Post by Bucky Ball on 2012-03-21
You say you're trying to install Ubuntu *inside* Windows. This is not side-by-side or a dual-boot install. You are attempting to do a Wubi install or install Ubuntu as a virtual machine, both installed inside Windows?

What you are describing is neither. You are describing a dual-boot (where you have Windows on one partition and Ubuntu on another (or others). 

Which exactly are you going for? A Wubi or VM install or a dual-boot? You need to download the Wubi installer for that and the desktop (or alternate) ISO for the other two. ;)

Ah, just re-read your post. You are going for a Wubi install, not dual-boot/side-by-side. Check [+Permission+denied%3A+%27J%3A%5C%5Cwubildr%27&pf=p&output=search&sclient=psy-ab&oq=[Errno+13]+Permission+denied:+%27J:%5C%5Cwubildr%27&aq=f&aqi=&aql=&gs_sm=&gs_upl=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=91ab9ffd81bcd339&biw=1024&bih=597"]THIS]("http://www.google.com.au/#hl=en&sugexp=frgbld&gs_nf=1&cp=43&gs_id=6&xhr=t&q=[Errno+13) to see if you can get any clues. If you are wanting to dual-boot you need to download the desktop ISO.

---

### Post by bcbc on 2012-03-21
> **jbw31697 said:**
> I am running Windows7 Ultimate

I have been trying to install Ubuntu 11.10 into my Windows7 installation. I am using the link on the main page where it says to install alongside Windows. It extracts and goes for about 8 minutes of installation then gives me an error message;
```
An error occurred
Permission Denied
For more information see log file 

```Logfile (this is the last few entries of the logfile where this error is repeated several times)
```
[Errno 13] Permission denied: 'J:\\wubildr'
```

Can someone please help me?

This problem is bug [lpbug]862003[/lpbug]. The install is successful... reboot to complete.

---

