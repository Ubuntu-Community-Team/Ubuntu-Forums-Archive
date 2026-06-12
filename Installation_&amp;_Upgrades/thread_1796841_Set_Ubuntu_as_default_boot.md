---
title: "Set Ubuntu as default boot"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by reddylast on 2011-07-04
Hi,

I have installed Ubuntu 11.04 alongside of win-7 (in separate drive). Whenever I start/reboot my computer it takes me to a booting menu with "Win-7" & "Ubuntu" as options and here the problem is that Win-7 is set a default boot option. But I want to make Ubuntu as default boot option.

As of now I don't want to eliminate windows completely from my computer bcoz I'm a new for Ubuntu. I did lots of Google search to find out right solution for this but unable.

Does anyone have any idea how to get rid off this problem ?

Regards,
Reddy

---

### Post by coffeecat on 2011-07-04
> **reddylast said:**
> Hi,

I have installed Ubuntu 11.04 alongside of win-7 (in separate drive).

Are you sure about that? If you install Ubuntu to its own partition, then Ubuntu will be the default OS to boot, whereas Wubi uses the Windows boot menu with Windows as the default. It sounds as though you may have a wubi install, which is inside your Windows partition. It would be wise to clarify this point before deciding what to do, because the answer will be different.

---

### Post by JRV on 2011-07-04
Any of the three methods mentioned in this thread will work **IF** this is not a Wubi installation.

[http://ubuntuforums.org/showthread.php?t=1795241](http://ubuntuforums.org/showthread.php?t=1795241)

---

### Post by reddylast on 2011-07-04
Sorry for not clarifying my question properly. Yeah ! you are right, I installed it with Wubi.

Regards,
Reddy

---

### Post by Mark Phelps on 2011-07-04
Since this appears to be a Wubi install ... you set the boot default inside Windows. Don't let anyone tell you to install GRUB -- that will only make matters worse.

In Win7, enter MSCONFIG in the start area.  When the popup appears, select the Boot tab.  That should provide you an option to set the default boot selection.

---

### Post by reddylast on 2011-07-04
> **Mark Phelps said:**
> Since this appears to be a Wubi install ... you set the boot default inside Windows. Don't let anyone tell you to install GRUB -- that will only make matters worse.

In Win7, enter MSCONFIG in the start area.  When the popup appears, select the Boot tab.  That should provide you an option to set the default boot selection.


Thanks for your quick response. I tried above trick to set Ubuntu as default boot but I did't find any option to change default boot. Is there any other way to do this ?

---

### Post by bcbc on 2011-07-04
My recommendation is that if you want Ubuntu as the default you should install Ubuntu direct to partition (or [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") your Wubi install). Wubi is intended to try out Ubuntu - so if you're planning to use it more often than Windows, now might be a good time to think about a regular install.

But this is how to do it... Right click on "Computer", Properties, Advanced System Settings, Startup & recovery settings. Select default OS from drop down box.

Make sure that "the time to display list of operating systems" is not reduced below 15 seconds (to be safe**) or windows won't boot. 

**I've seen cases of setting it to zero or 1 causes windows boot manager to boot straight to Ubuntu. Maybe 2 or 3 will work, but I'm not planning to test this. That's why I say don't set below 15 to be safe.

---

