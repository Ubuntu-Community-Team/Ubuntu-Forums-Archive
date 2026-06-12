---
title: "installing 11.10 on HD with windows 7"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by thegutterpoet on 2011-10-22
I have been running windows 7 for the last year, and now wish to install Ubuntu on the same hard drive. When I did this a few years back with an earlier ubuntu and win xp, the ubuntu installation process automatically created an option which allowed me to choose between windows xp and ubuntu whenever i switched the pc ON.

Does Ubuntu 11.10 also have a safe and easy to navigate application within its install routine, to do the same making damn sure that windows 7 is not damaged?

Do i need to repartition the HD before installing ubuntu?
if so, any reccomended partition sizes???

i have a 297gb HD...with an external 1tb HD.

I am intending to use the 64-bit ubuntu 11.10 as i have a 64 bit OS...

my main fear is simply...******* up somehow and killing Windows. 

any advice is appreciated.

---

### Post by kurt18947 on 2011-10-22
It should but here's what you can do to have a recovery plan.  Before doing anything, create an image of your existing setup.  Actually you could create two images in case one image set decides it doesn't want to restore properly.  Then you could install 11.10 choosing to install alongside Windows (or whatever the terminology).  If this doesn't work for whatever reason, you can  nuke the partition using a Live session or standalone Gparted and restore the image. You should be exactly where you were when you created the image. An imaging program that many use is clonezilla (clonezilla.org). I don't have any experience with clonezilla, I use something else but others have used it successfully.

How many partitions do you have now?  You could use the disk utility in a live session to check.  Hard drives can only have 4 primary partitions.  Some manufacturers use them all for various restore utilities.  If this is your case,  your life just got more complicated.  You'd need to delete at least one of the manufacturer created partitions and possibly resize others in order to create space for an Ubuntu installation.

---

### Post by lovinglinux on 2011-10-22
If you just want to try Ubuntu, you install Wubi, which creates a virtual disk on Windows and add the option to boot from either one of them. If you don't like, you can easily remove Ubuntu, just like you do with any other Windows application. There is no need to partition your HD with this method. However, is not recommended for long term usage.

Download: [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Documentation: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Discussion: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by jessiebrownjr on 2011-10-22
I just did this, I selected the option to install alongside. Popped the Ubuntu CD out, rebooted...
 
Then for some reason I had windows telling me it wanted to check my disk for errors, which I did.
 
No bootload for Linux seems to have installed, what now?
 
I am using 32 bit win 7 as well as 32 bit 11.10 Ubuntu

---

### Post by raja.genupula on 2011-10-22
You mean your Ubuntu not booting from Boot loader or anything else ? Please provide us more information .

---

### Post by jessiebrownjr on 2011-10-22
> **raja.genupula said:**
> You mean your Ubuntu not booting from Boot loader or anything else ? Please provide us more information .
 
No bootloader is showing up, like it didn't install properly possibly:(

---

### Post by kurt18947 on 2011-10-22
> **jessiebrownjr said:**
> No bootloader is showing up, like it didn't install properly possibly:(

You installed Ubuntu after Windows?  You used default settings when installing Ubuntu? The reason I ask is that Ubuntu uses something called GRUB to control boot behavior.  Installing Windows after Ubuntu would overwrite GRUB.  My second thought is if you change GRUB's destination via one of the install screens, GRUB will be written to the Ubuntu partition instead of to the hard drive's MBR (I think that's the location, not sure). You might be able to reinstall GRUB from a Live session but I'm not sure how to do that.  A little searching will supply the answer I'm sure.  I use a boot manager so I'm not familiar with editing GRUB.

---

### Post by jessiebrownjr on 2011-10-22
Yeah I didnt change anything but the size of the partition. Yeah I am sure grub didnt isntall properly (not sure why yet) because the mbr is still only windows 7. I think you can install grub from live, I havent done it in a while though--coming back to Ubuntu after a year break!

---

### Post by raja.genupula on 2011-10-22
K in my signature there a link for Grub recovery ,I am sure that gonna help you.

All The best.

---

### Post by jessiebrownjr on 2011-10-22
> **raja.genupula said:**
> K in my signature there a link for Grub recovery ,I am sure that gonna help you.
 
All The best.
 Epic, will do this later after I finish my homework :-):KS

---

