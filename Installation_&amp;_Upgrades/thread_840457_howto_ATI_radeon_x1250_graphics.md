---
title: "howto ATI radeon x1250 graphics"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by beN..87 on 2008-06-25
**_How to install the proprietary drivers for ATI Radeon x1250 integrated graphics._**

*If youve got a different ATI chip - just substitute in the approprate driver and you should be able to do it the same way.*
[B][U]
Before you get started[/U][/B]

1. Get the proprietry drivers from ATI at this link here

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

 if it does not take you directly to the file, it is under the menu 
>linux>x86>integrated motherboard>x1250

the file is nearly 60mb, be sure to keep this file uncorrupted, and use a healthy USB drive to put it on, in a folder called /ati on the memory stick.

2. Get the Alternate Install CD, you must use the alternate install CD so that your screen can display your installation menus. 

**_Installation_**
[U]
Step 1 - Installation of Ubuntu
[/U]
Insert your install CD and boot up, check the CD for defects.

Press F6

enter the following code:

noapic

(this should add the boot paramater --noapic to prevent a screen I/O error)

<press return key>

Install your system to your liking.

select continue to now reboot without the CD in the drive

[U]
Step 2 - Installation of drivers[/U]

your computer will boot into your installed ubuntu system - without your graphics installed , you will be met by some code and a screen that will flash for 10 seconds or so, when its stopped flashing

press Alt and F2

login prompt: enter your username and password

enter the following code:

sudo bash
(enter pasword)

now mount up your USB drive and transfer your ATI driver onto your system in /ati

enter the following code:

cd /ati

enter the following code:

ls

(this shoudl return the name of your ATI installer ' ati-driver-installer-8-5-x86.x86_64.run ' so you can easily look up and check you are spelling it correctly in the next step)

enter the following code:

sh ati-driver-installer-8-5-x86.x86_64.run

(your ati driver installer will now run an installation menu - mostly unless you are experienced accept all default settings - literally just hit enter each time to accept the defaults)

now that it has finished - wait 2 minutes - just let it do its thing while the system updates - be patient - better to wait 2 minutes then have to reinstall your entire system

enter the following code:

reboot

you should now have a graphical login screen in pretty pretty brown, and a full graphical desktop after login!

enjoy! :guitar:

[U]
Troubleshooting[/U]

Whitescreen of Death:

Have you made sure to use a healthy USB drive not full of clutter to keep the ATI file uncorrupted? this file is VERY sensitive!

Have you used the correct driver for your chip? are you sure of what your chip is?

---

### Post by archer2000 on 2008-07-13
I reinstalled Hardy two times on **P200-Pro T8100 Bordoso**, also the proprietary driver.

The first install worked fine.

After the second install, I got a whitescreen after the login.
This bug is discussed here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/196900](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/196900)

So, I disabled compiz: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/196900/comments/13](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/196900/comments/13)

Have fun!

---

