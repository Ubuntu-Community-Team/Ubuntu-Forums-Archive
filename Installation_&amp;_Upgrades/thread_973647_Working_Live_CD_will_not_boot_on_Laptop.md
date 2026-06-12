---
title: "Working Live CD will not boot on Laptop"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by joe2949 on 2008-11-06
I have A problem; when I try to boot my laptop with a Ubuntu 8.04 live CD (tested on my desktop and verified to work) it a)doesn't boot past the loading screen with the 32-bit version or b)shows a screen that is pixillated and not readable in the 64-bit version. 

I can verify that ubuntu will work on this laptop as I can run it using wubi, however I want to be able to dual-boot without sharing a partition with windows vista

Laptop is new and I have checked and made sure my bios (insyde v. 1.2) and chipset drivers are up to date 

I am using a Toshiba Satellite L305, hopefully I am just overlooking something very simple

---

### Post by Partyboi2 on 2008-11-07
Have you tried to install using safe graphics mode? Press F4 at the main menu for the option.

---

### Post by Mark Phelps on 2008-11-07
Getting laptops to work under Ubuntu is especially difficult due to the degree of BIOS and driver customization that laptop vendors do under Windows.  If you can't get decent video with the LiveCD, you're facing an uphill struggle getting decent video after you install.

I don't know why video would be fine under Wubi, but since that's running as an application inside Windows, it might just be using the windows video driver somehow.  You could post questions to the Wubi subforum to get more info.

Also, unless you have a Vista DVD or Vista Recovery CD, do NOT shrink your Vista partition using either the LiveCD or GParted.  While that works most of the time, when it fails, you MUST then boot into Vista (using the afore mentioned DVD or CD) and do a Startup Repair, or your Vista OS will then be permanently unusable.

---

### Post by joe2949 on 2008-11-07
I have tried the method of safe graphics mentioned above and it again will boot, make the Ubuntu startup sound then the screen is riddled with vertical lines every color of the rainbow. 

I have an Intel 4500mhd integrated chip and as far as i can see I will just have to wait for the newest drivers to come out. It's odd, however, that when I use Wubi it allows me to run Ubuntu like a charm

---

### Post by Partyboi2 on 2008-11-07
If you are able to successfully install using wubi then you can move the install to its own partition. See [[COLOR=Blue]here[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") I would suggest shrinking down your vista partition with the resize function in vista then use gparted to create the partitions needed then following the steps to migrate.

Another option you could try is to use the [[COLOR=Blue]alternate cd[/COLOR]]("http://releases.ubuntu.com/intrepid/") , which is a text base installer to install ubuntu.

---

