---
title: "Serious Problem With Ubuntu 15.04"
date: 2015-12-22
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2015-12-22
I got a new Dell Ispirion 5558on and it had Windows 10 on it with a 1 TB HDD.   I wanted to install Ubuntu on it so I changed to Legacy in the boot options in BIOS.  My Ubuntu disc is the 15.04 version and after installing I was going to upgrade to 15.10,  However, after installing the damn thing ate the Windows installation which I really didn't have a problem with.  The problem is I'm not able to get the wifi working.  So no upgrade is possible.  I have no idea why this is happening and it's actually the second time.  I took the laptop back to Best Buy and told them the wifi adapter wasn't working and they replaced it.  Now I'm worried it something with Dell because I used the same disc to install the system on my desktop!  If you have any suggestions please help because I only have wifi at home and will have to find a wired network if you can't help.  :(:confused:

Oh yeah, the wifi did work on Windows before it was overwritten!

---

### Post by Vladlenin5000 on 2015-12-22
A couple of things you're doing wrong or harder than they should be (and a few additional comments):

1. There's no need to change to Legacy. Actually you shouldn't have changed it if you intended to dual boot and the first OS had been installed in UEFI mode, the default since (factory installed) Windows 8.
2. It didn't "ate" your Windows, it merely did what you asked it to (or let it) do. A basic knowledge of partitioning is required for installing/managing operating systems.
3. Installing 15.04 which will be out of support in a matter of days just to upgrade online? Please don't. Obtain installation media for the current release and simply install it. An online update is slow (hours), cumbersome and prone to errors. An installation from scratch of the same version you would end up with takes only a few minutes.
4. The WiFi was most likely fine. Replacing it was a waste of time and materials. Please go to the section Networking and Wireless and read the sticky [Before posting in Network & Wireless ]("http://ubuntuforums.org/showthread.php?t=370108")and follow instructions to start troubleshooting. If an alternative internet connection - Ethernet cable, phone tethering, etc. isn't a option the same sticky has also instructions for those scenarios. To keep in mind: Ubuntu, as well as almost all mainstream distros, natively support a lot more hardware than Windows but not all. Some WiFi devices can be problematic in Ubuntu but for most there are solutions. The problematic ones are those not detected like yours.
5. You can use the same installation media for as many machine you like.

---

### Post by shane_faulkinbury2 on 2015-12-22
Thanks [[IMG]http://ubuntuforums.org/customavatars/avatar1468732_3.gif[/IMG]]("http://ubuntuforums.org/member.php?u=1468732")[COLOR=#000000][COLOR=#DD4814][COLOR=#000000][Vladlenin5000]("http://ubuntuforums.org/member.php?u=1468732"), I read up on all of that![/COLOR][/COLOR]
[/COLOR]

---

### Post by Vladlenin5000 on 2015-12-22
You're welcome. 
Good luck. We're here to help so don't hesitate in asking whenever you need or have doubts.

---

### Post by shane_faulkinbury2 on 2015-12-23
Well luckily I was able to  download a good copy of 15.10 and everything installed and wifi is working great!  :D:p:D

---

### Post by Vladlenin5000 on 2015-12-23
As expected, newer releases provide newly added support for newer hardware.

---

