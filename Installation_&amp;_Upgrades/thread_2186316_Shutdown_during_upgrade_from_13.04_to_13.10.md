---
title: "Shutdown during upgrade from 13.04 to 13.10"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by zach832 on 2013-11-06
So yesterday I tried upgrading to 13.10 and lost power to my computer. At first I was getting file system errors and could not boot to the login screen. I searched around and have tried several solutions, all of which have failed. I did try startx after logging in without gui and that showed my desktop, but no gnome toolbar at the top. I have practically no experience when it comes to advanced ubuntu commands so I'll need help with those. 

The machine works fine, the only problem is the software. I've tried apt-get update and apt-get upgrade, however upgrade gives me an error while installing shimmer themes. 

Please pardon my lack of experience but I desperately need my computer fixed. 
Thanks.

---

### Post by ian-weisser on 2013-11-06
The text warning at the beginning of the upgrade specifically warned you that an interruption during the upgrade process could irreparably break your system.

It's difficult to tell from your description how bad the damage is, or which of the several thousand updated packages was corrupted by the shutdown, or which packages were or were not installed.

Generally in this (very rare) case, I recommend backing up your personal data and reinstalling from scratch.

---

### Post by zach832 on 2013-11-06
I know, but I couldn't prevent a power outage. I guess reinstalling will by my only option. Thanks anyway

---

### Post by ian-weisser on 2013-11-06
Sorry, wish I had a less-intrusive answer that would reliably get your system up and working again.

---

### Post by krinda32 on 2013-11-07
Hi there,  
I've got a similar problem. Whilst upgrading from 13.04 to 13.10 the process got stuck updating CUPS and didn't progress. 
The point is that I shut down the PC (soft shut down) but UBUNTU doesn't enter back in graphic mode. I've got root access though. 
The question is how do I restart upgrade process from command line

Thank you

---

### Post by ian-weisser on 2013-11-07
Well, you don't "restart" the process. Your system is now broken, not restored to the pre-updated state. You have two options:

1) You learn a *lot* about how to diagnose and repair a broken system. Might take a day or two, might take weeks.

or

2) You backup your data and reinstall afresh.

---

### Post by philinux on 2013-11-07
> **krinda32 said:**
> Hi there,  
I've got a similar problem. Whilst upgrading from 13.04 to 13.10 the process got stuck updating CUPS and didn't progress. 
The point is that I shut down the PC (soft shut down) but UBUNTU doesn't enter back in graphic mode. I've got root access though. 
The question is how do I restart upgrade process from command line

Thank you

If you've got a root prompt with net access then try this.

```
dpkg --configure -a
```

It's worth a shot.

---

### Post by craig10x on 2013-11-07
Also, in the future (I am assuming here you aren't running multiple ubuntus...just one) then do an upgrade using the option to Upgrade that should be offered you when you by the installer on a live session iso of ubuntu...it doesn't need to go to the internet as it has all the files to install right on the iso itself...even looks like a clean install when you do it (with the slide show and everything)....works VERY WELL (although any PPAs installed should be unchecked prior to using it)....it's fast, doesn't use the internet and you don't have to worry about interrupted installations...

---

### Post by krinda32 on 2013-11-07
In giving this a try. Thanks a lot

---

