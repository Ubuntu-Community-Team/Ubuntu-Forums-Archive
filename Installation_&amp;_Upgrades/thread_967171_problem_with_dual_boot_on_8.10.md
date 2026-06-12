---
title: "problem with dual boot on 8.10"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by jackgu1988 on 2008-11-01
I tried to install ubuntu 8.10 on my windows vista hdd (x64) and when i restarted to login for first time there was no ubuntu selection on the boot screen. What should i do?

---

### Post by taurus on 2008-11-01
Did you remember to install GRUB to your Master Boot Record--MBR--when you installed Ubuntu?

---

### Post by jackgu1988 on 2008-11-01
no... how can i do that?

---

### Post by tvtech on 2008-11-01
usually when you do a manual install and select your partition it does it automatically.  in fact unless your using the alternative install disk where you select where grub will be installed it will automatically install on the master MBR of your primary boot drive.

---

### Post by jackgu1988 on 2008-11-01
oh ok! i think i know what i've done wrong now... but is there any way i can install grub on the hard drive that i have installed ubuntu? thank you!

---

### Post by caljohnsmith on 2008-11-01
Yes, it's definitely possible to install Grub to Ubuntu if you omitted it during the install, but it is usually not worth the hassle if you can just simply reinstall with Grub. You shouldn't need to do anything special to install Grub during the installation process as long as you only have one HDD. But if you have specific questions about the installation process, let us know.

---

### Post by jackgu1988 on 2008-11-01
I have 3 HDD's on at the moment, 2 of them having 2 different versions of windows. I have windows vista x64 on hd1 and windows xp x32 on hd2. I installed windows xp fist on hd2 and then i installed windows vista on the main one. Now i would like to install linux on either one, preferably to the second one (the one with windows xp on it). What should i do?

---

### Post by caljohnsmith on 2008-11-01
OK, begin by booting your Live CD, choose the first option that says something like "try Ubuntu without making any changes", and once you get the Ubuntu desktop, go to System > Admin > Partition Editor, and use the partition editor to resize the Windows XP partition on your second HDD to make room for Ubuntu. Once XP is resized, create two partitions, one for the main Ubuntu install, and one for a swap partition. Format the Ubuntu partition to ext3 and the swap partition should be formatted as swap. 

Once the partitions are set up, double-click the installer icon in the upper left corner of the desktop. As you go through the first few steps of the installer, select the Win XP drive, select "manual" for partitioning, and then select the partition for the main Ubuntu install and set its mount point as "/". Then select the swap partition and set its mount point as swap. Once you get to the very end of the installer just before it will install, press the "advanced" button and tell Grub to be installed to "/dev/sdb" or whichever is the Windows XP drive that you are installing Ubuntu to. 

Give that a shot and let me know how it goes, or if you have further questions. :)

---

### Post by jackgu1988 on 2008-11-01
Thanks for the reply. I have 3 partitions under sdb:
-/dev/sdb1 which is the windows xp left over partition
-/dev/sdb2 which is the partition i created for ubuntu
-/dev/sdb3 for the swap
Which one should i use in the final "Advanced" step you are refering to?

---

### Post by caljohnsmith on 2008-11-01
> **jackgu1988 said:**
> 
Which one should i use in the final "Advanced" step you are refering to?
You don't need to do that until the very last screen of the installation, where it gives you a list of everything the installer is planning on doing. There you will see the "advanced" button, press it, and simply specify "/dev/sdb" as the drive to install Grub to (don't use a partition such as /dev/sdb1). Sounds like you are making good progress though, so let me know how it goes. :)

---

### Post by jackgu1988 on 2008-11-01
Okay, everything seems to work fine, many thanks! Just one problem. Every timee i boot the computer i get an error like this:
"[ 32.39292392] usb 8-2: device descriptor read/64, error -110 a bunch of times in a row and then hub 8-0:1.0: unable to enumerate USB device on port 2 and then the same error as the first one again, but with a "5-2" instead of an  8-2, again a bunch of times. After that i get usb 8-2: device not accepting address 5 and device not accepting address 6. Weird part is that after spending 5 mins on those errors, the system runs normally and i get to the ubuntu login screen. Any suggestions?

---

### Post by caljohnsmith on 2008-11-02
> **jackgu1988 said:**
> Okay, everything seems to work fine, many thanks! Just one problem. Every timee i boot the computer i get an error like this:
"[ 32.39292392] usb 8-2: device descriptor read/64, error -110 a bunch of times in a row and then hub 8-0:1.0: unable to enumerate USB device on port 2 and then the same error as the first one again, but with a "5-2" instead of an  8-2, again a bunch of times. After that i get usb 8-2: device not accepting address 5 and device not accepting address 6. Weird part is that after spending 5 mins on those errors, the system runs normally and i get to the ubuntu login screen. Any suggestions?
I can't be sure, but it sure sounds like a BIOS issue to me; you might want to check the manufacturers website of your motherboard for a BIOS upgrade. Or if your lucky, maybe all you need to do is tweak some setting in your BIOS related to your USB drive and/or USB settings. That's about all I can suggest at this point. Good luck and let me know how it goes. :)

---

### Post by ^[H3ad-Tr1p]^ on 2008-11-02
I have the same problem on my new laptop asus m50

hardy didn't have this problem,intrepid instead it has

with intrepid I had install with alternate cd of intrepid 8.10 rc...if I try to install with a cd live I can't install and I can't install with alternate 8.10 .I must install only with 8.10 rc

then ,often when I power up my laptop ,it doesn't boot normally

I can see a kernel message after a grub,that tell me :

unable to enumerate usb device on port 1 

or something like it

then I must to power off my laptop with the power button and retry to boot again

when it doesn't boot,I can hear the irritating buzzar of the sistem thet doesn't stop until I don't power off with the power button

---

