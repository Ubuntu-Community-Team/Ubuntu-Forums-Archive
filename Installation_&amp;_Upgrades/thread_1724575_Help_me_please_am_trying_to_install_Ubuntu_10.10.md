---
title: "Help me please am trying to install Ubuntu 10.10"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by n3oom on 2011-04-08
Hi all am new in all the ubuntu thing .. so I wanna try it.. so I download the iso file .. I put it in a usb flash .. using Universal-USB-Installer-1.8.3.9 
everything went fine .. but after i choose the install ubuntu option from the boot menu .. it loaded with the ubuntu logo . and after that I wait like 40 minz nothing appear .. just a blank screen with mouse I can move .. [IMG]http://www.10people.co.uk/wp-content/uploads/2010/10/warty-final-ubuntu.jpg[/IMG]

this is the screen 

please help 

this is my laptop

OS Name	Microsoft Windows 7 Ultimate
Version	6.1.7600 Build 7600
Other OS Description 	Not Available
OS Manufacturer	Microsoft Corporation
System Manufacturer	FUJITSU SIEMENS
System Model	ESPRIMO Mobile V6555
System Type	X86-based PC
Processor	Intel(R) Core(TM)2 Duo CPU     T5870  @ 2.00GHz, 2001 Mhz, 2 Core(s), 2 Logical Processor(s)
BIOS Version/Date	Phoenix Technologies Ltd. V1.19, 9/9/2009
SMBIOS Version	2.5
Windows Directory	C:\Windows
System Directory	C:\Windows\system32
Boot Device	\Device\HarddiskVolume1
Hardware Abstraction Layer	Version = "6.1.7600.16385"
Installed Physical Memory (RAM)	3.00 GB
Total Physical Memory	2.50 GB
Available Physical Memory	1.21 GB
Total Virtual Memory	5.00 GB
Available Virtual Memory	3.14 GB
Page File Space	2.50 GB

---

### Post by masterJanky on 2011-04-08
Perhaps you did not get get the ISO on the flash drive cleanly?  I would try to recreate the USB drive with the ISO and see where that lands you.

---

### Post by Enigmapond on 2011-04-08
Did you verify the MD5sum on the image you downloaded?

---

### Post by n3oom on 2011-04-08
> **masterJanky said:**
> Perhaps you did not get get the ISO on the flash drive cleanly?  I would try to recreate the USB drive with the ISO and see where that lands you.

I did it more than once man

---

### Post by n3oom on 2011-04-08
> **Enigmapond said:**
> Did you verify the MD5sum on the image you downloaded?

whats the MID5sum .. do u mean 32bit or 64bit
I choose the 32bit coz my windows 7 is 32bit

---

### Post by Quackers on 2011-04-08
It seems that your pc has a Nvidia 8200 graphics card. It may possilby need a boot option to boot properly.
When booting from the usb, as soon as you see the first purple screen (with the little man icon at the bottom) press any key. Then choose your language and on the next screen press F6. You should see some options appear bottom right. Select the "nomodeset" option. 
I would recommen that you use "try ubuntu" option first, to check that everything works ok, before installing.

Also see here
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by n3oom on 2011-04-08
> **Quackers said:**
> It seems that your pc has a Nvidia 8200 graphics card. It may possilby need a boot option to boot properly.
When booting from the usb, as soon as you see the first purple screen (with the little man icon at the bottom) press any key. Then choose your language and on the next screen press F6. You should see some options appear bottom right. Select the "nomodeset" option. 
I would recommen that you use "try ubuntu" option first, to check that everything works ok, before installing.

Also see here
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

man there is no options appears .. just the  balck menu .that has  1)run ubuntu .. 
2) install ubuntu 
and other options 
this one : 
[IMG]http://www.geekinside.org/drupal/sites/default/files/ubuntu8-boot-menu.jpg[/IMG]

---

### Post by Quackers on 2011-04-08
For a start you could select the "check cd for defects". At least that will confirm that the cd is ok - or not.

---

### Post by n3oom on 2011-04-08
> **n3oom said:**
> whats the MID5sum .. do u mean 32bit or 64bit
I choose the 32bit coz my windows 7 is 32bit

ok man i download winMD5Sum, and I compare everything is fine A message box said "MD5 Check Sums are the same" :D

---

### Post by n3oom on 2011-04-08
> **Quackers said:**
> For a start you could select the "check cd for defects". At least that will confirm that the cd is ok - or not.

ok man am gonna do it now .. :)

---

### Post by n3oom on 2011-04-08
> **n3oom said:**
> ok man am gonna do it now .. :)

ok man nth happen .. I still have the same problem .. and btw i tried this usb on other laptops and it worked fine .. so its n my laptop

---

### Post by Quackers on 2011-04-08
Nothing happens? It's supposed to check the cd, giving details of what it's checking as it goes along. 
When you boot from the usb are you getting to the first purple screen with the little man icon at the bottom?
If yes, press any key before that screen disappears. You should then get asked for your choice of language. Choose language and on the next screen press F6 key.
This should bring up some boot options in the bottom right hand side of the screen. Select the nomodeset option then continue.

---

### Post by n3oom on 2011-04-08
> **Quackers said:**
> Nothing happens? It's supposed to check the cd, giving details of what it's checking as it goes along. 
When you boot from the usb are you getting to the first purple screen with the little man icon at the bottom?
If yes, press any key before that screen disappears. You should then get asked for your choice of language. Choose language and on the next screen press F6 key.
This should bring up some boot options in the bottom right hand side of the screen. Select the nomodeset option then continue.
thnx man everything went ok... the installation went fine .. and after restarting , I choose ubuntu from the grub  menu which also include :
the recovery mode for ubuntu 
2 test option 
and the windows 7 loader 
but the loading of ubuntu freeze at the ubuntu logo .. wt should I do ??

---

### Post by Dutch70 on 2011-04-08
Try choosing nomodeset...
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by Quackers on 2011-04-08
Yes, if you used nomodeset for booting the usb, you will need it for the first boot of Ubuntu (until graphics drivers are installed).

---

