---
title: "USB boot for fresh install - no install option ?"
date: 2020-04-09
forum: Installation &amp; Upgrades
---

### Post by oygle on 2020-04-09
HP 4330S - The boot usb is from **mkusb** and I have used this procedure before and been able to do a fresh installtion of Kubuntu. However, this time, with trying 19.10 and **mkusb**, there is a splash screen after booting from usb, but nothing on the desktop. No icons, nothing ? The mouse pointer can be seen , but left or right button does nothing.

I have tried the **mkusb** with live boot, with persistant live and with clone, but same problem. Have checked the BIOS settings and they seem okay. No UEFI checked which I think is 'secure boot'.

Can I do a usb boot with any of the **mkusb** options, and have NO splash screen, so that I can see what is going on.

---

### Post by mastablasta on 2020-04-09
yes, various boot options are available - more here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

i would say you have a corrupted "install" or maybe you just need nomodeset and install correct drivers later on. what is the PC configuration? GPU in particular?

---

### Post by oygle on 2020-04-09
> **mastablasta said:**
> yes, various boot options are available - more here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Yes I have been reading through some docs. I even tried 'Startup Disk Creator' to make the boot usb, but that had the same problems. So that may indicate it is not necessarily the tool used for making the boot usb. 

> **mastablasta said:**
> i would say you have a corrupted "install" or maybe you just need nomodeset and install correct drivers later on. what is the PC configuration? GPU in particular?

Thinking that it may be the usb, I have tried another usb several times with mkusb, but same problem. Bt back to your suggestion of a corrupt. I'm trying to do this as the laptop has 19.10 currently but the whole plasma and menus is a mess, it won't work so as there is no data there yet, thought to wipe with a fresh install. Did read some docs where if there is something corrupt it can possibly stop a fresh install from a usb boot ??

I'll have to read up on 'nomodereset', thanks. Here is a pic of the specs

---

### Post by ajgreeny on 2020-04-09
Did you check the hashes of the iso file you downloaded?

It could be a bad download.

---

### Post by oygle on 2020-04-09
> **ajgreeny said:**
> Did you check the hashes of the iso file you downloaded?

It could be a bad download.

Yes, the MD5sum is okay. There have been far too many weird things going on with that laptop. It won't even let me drop down to Konsole, plus there are processes still there from before I last shutdown ?  Can't navigate on the desktop, or swap between tasks. So at present running a secure erase on the hard drive, it will take 2 hours. I did have DBAN on a usb, booted to usb but the laptop went and booted to the HDD. Virus in the MBR ??  Myth Busters would say it is plausible...lol

---

### Post by oygle on 2020-04-09
So, after the HDD was reformatted, tried the usb again, same problem. When powering down the laptop there was a very quick message, something like "no caching mode page found"

---

### Post by oygle on 2020-04-10
Finally used a DVD and "Startup Disk Creator" to burn the ISO, and the install option appeared. It is installing now.  :D

For some reason the HP 4330S laptop was unable to use a usb to boot, despite the fact it had been used a number of times in the past to boot from a usb. As I thought the initial source of the problem may possibly be **mkusb** I added a post at [https://ubuntuforums.org/showthread.php?t=1958073&p=13945255#post13945255](https://ubuntuforums.org/showthread.php?t=1958073&p=13945255#post13945255) . However have now released it wasn't **mkusb** or 'Startup Disk Creator --> usb at all. Possibly memory or motherboard, etc ?  

I do feel that the troubleshooting for this would have been substantially reduced if the boot from usb enabled a terminal view of what was happening, instead of the splash screen. That said, was the troubleshooting compounded because the laptop has a broken screen ? I have a large VGA connected to it. This frustrates the booting process as I have to power on, press F9 3 or 4 times, quickly close the lid and then the VGA monitor displays ...lol

---

### Post by sudodus on 2020-04-10
After a dialogue starting [at this post](https://ubuntuforums.org/showthread.php?t=1958073&page=46&p=13945255#post13945255) I am joining you here.

It seems the computer does not want to boot from USB, but it boots from DVD.

We think there are some hardware issues, maybe not only with booting from USB, and need your help to debug it :-P

---

