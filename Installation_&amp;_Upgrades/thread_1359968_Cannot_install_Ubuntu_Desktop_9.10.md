---
title: "Cannot install Ubuntu Desktop 9.10"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by George1 on 2009-12-20
Hi,

I've always been a Windows user but want to install and learn Ubuntu.

I have followed the instructions to download and burn the ISO file on a disk.  After trying unsuccessfully 4 times to install it I am asking for some help.

I start the installation process from a bootable disk and all seems to be normal. Couple of times I will reach 70% installation and twice about 90% when the laptop will just shut down with no error messages.

I have about 100gb allocated for Ubuntu in a logical partition. 

My laptop:
Acer Aspire 7720-6208
Intel Core 2 Duo processor T5450 (1.66 GHz)
3gb DDR2
320gb HDD
DVD-Super Multi DL

Any help will be very much appreciated.

Thanks,
George

---

### Post by darkod on 2009-12-20
First of all, you need to have unallocated space so Ubuntu can create the necessary partitions inside. In your case, this doesn't seem to be the problem because the installation is starting, but just to mention, don't create partition in advance, leave the space as unallocated. During step 4 of the installer you can create partitions manually if you want to or just use guided option when you're new to ubuntu and linux.
Did you try to run the Try Ubuntu option from the cd? That will run ubuntu from the cd so you can see how it runs on your particular hardware.
Another thing to try is creating a bootable usb stick from the ISO and try with that.

---

### Post by George1 on 2009-12-20
Thank you Darko!
Indeed, I did not create the partition but left it as unallocated space. During the installation process, Ubuntu's partition program will create the partition from the unallocated space.

I can run Ubuntu from the CD and use most of the programs on the cd. 

The installation runs ok, I would set up my location, then the partition is created then it will start coping the files. At some point I will see that it is installing drivers for USB and CD-rom etc. There are no warning messages at all - it just shuts down. I am used to the buggy Windows and the 'normal' crashing. Nothing like that, the laptop just turns off.

Thanks again,
George

---

### Post by cpplinux on 2009-12-20
You should use a primary partition instead of a logical partition. At least,  the **/boot** directory must be mounted in a primary partition.

---

### Post by darkod on 2009-12-20
I'm not sure to be honest. I would go with the usb stick idea. It saves a CD too. :)
More details for creating it (if you need help with that) in post #7 here:
[http://ubuntuforums.org/showthread.php?t=1359446](http://ubuntuforums.org/showthread.php?t=1359446)

---

### Post by darkod on 2009-12-20
> **cpplinux said:**
> You should use a primary partition instead of a logical partition. 

Not true, at least not for Ubuntu. Usually in the guided install it sets itself up in extended partition and works just fine. That's not the issue.

---

### Post by Cheesemill on 2009-12-20
You may have a bad CD.

Did you check the md5sum of the .iso before you burnt it and run the 'Test this disk for errors' when booting the CD?

---

### Post by George1 on 2009-12-20
Thank you. 
Yes, I did check the md5sum of the .iso before burning and later 'Test this disk for errors'. I did, however, burnt the .iso file on a dvd. I am not sure if it would make any difference but will burn the image file on a CD. I also downloaded the [PC (Intel x86) alternate install CD]("http://releases.ubuntu.com/releases/9.10/ubuntu-9.10-alternate-i386.iso") and try again. Ar the end I will try usb stick.
I will give you an update regarless of the outcome. 
Thanks,
George

---

### Post by George1 on 2009-12-23
Thank you All for helping.

I finally managed to install Ubuntu 9.10 from a CD. I don't think my installation problems were not coming from a faulty disk or ISO file. Several times while running ubuntu the laptop will simply shut down unexpectedly. 

Anyway, I have it going and now my Ubunu experience begins... it is so different from Windows, especially installing programs.

Thank you all,
George

---

### Post by SecretCode on 2009-12-23
When it simply shuts down, is it very hot? I haven't seen this happen with Ubuntu installations, but some laptops do get hot enough to trigger the BIOS thermal shutdown, when running CPU intensive tasks - and a thermal shutdown is instantaneous, no warning.

---

### Post by George1 on 2009-12-23
Overheating was one of the reasons I suspected for the shutdowns. It happens just the way you are describing it. On couple of occasions during installation I noticed that the laptop go too hot. After one of the unexpected shutdowns I did start Ubuntu in recovery mode and noticed in too many lines the word overheating.

Is this normal?

George

---

### Post by SecretCode on 2009-12-23
Normal as in good, no. Normal as in quite likely to happen on an under-cooled laptop, sadly yes.

---

### Post by George1 on 2009-12-24
Thank you!

---

