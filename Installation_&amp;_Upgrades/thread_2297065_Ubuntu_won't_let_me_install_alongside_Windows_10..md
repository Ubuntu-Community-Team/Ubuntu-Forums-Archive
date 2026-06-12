---
title: "Ubuntu won't let me install alongside Windows 10."
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by Thetri on 2015-09-30
Whenever I try to install Ubuntu 14.04 or 12.04 it only gives me the option to install over windows and not along side it. I have installed Linux mint 17.1 on the system previously and it worked I then removed it to install the regular Ubuntu and no option to install along side. I tried kubuntu and Linux mint kde after and they worked so it's only a Ubuntu issue. 

It happens on both computers I own. Every other Ubuntu variant I try works except the main version. It used to work before and the only change made to these PC's is they have windows 10. 

Is there a way to fix this? I can just install Ubuntu-desktop in xubuntu to get it but this usually results in an annoying error message at every boot. I would like to just install the Ubuntu main release if I can.

---

### Post by Bucky Ball on 2015-09-30
Boot into Windows. Switch off hibernate and fastboot (I think it is called).

---

### Post by Bucky Ball on 2015-09-30
Boot into Windows. Switch off hibernate and fastboot (I think it is called).

---

### Post by Bucky Ball on 2015-09-30
Boot into Windows. Switch off hibernate and fastboot (I think it is called).

---

### Post by Bucky Ball on 2015-09-30
Boot into Windows. Switch off hibernate and fastboot (I think it is called).

---

### Post by yancek on 2015-09-30
Do you have any free space, unallocated on the drive?  Otherwise you will need to use the Something Else option to select a specific partition or partitions to install to.  You haven't posted any drive/partition info so only guessing here.

---

### Post by Bucky Ball on 2015-09-30
Use 'Something Else' at the partitioning section of the install regardless. Safest way. And yes, create free space when booted into Windows in the first instance to install Ubuntu in to.

---

### Post by Thetri on 2015-10-01
I don't have any unallocated partitions because i never had to do that before. Kubuntu, Linux mint and others all allow me to install it a lot side windows so I don't see why this partitioning thing should matter. I just got one drive that is 930 gb and about 700 gb free. I installed Linux mint and gave that 30 gb of space. I don't get why it works with others and not Ubuntu. I'll try that hibernate thing. If the something else unallocated method works I may just that but it's odd how the option isn't there. Normally it's mint that gives me issues where it tries to make me install it to the USB it is being run from.

---

### Post by Bucky Ball on 2015-10-01
? If you don't have free space, where you going to install Ubuntu?

Sounds like you have been doing Wubi installs, Ubuntu inside Windows. These are not supported any longer by Canonical and haven't been for awhile. You're unlikely to get much help with a Wubi install as there are few, if any, members who are familiar with it or using it anymore.

Suggest you do some research on a real dual-boot. Windows on one partition, Ubuntu on the other. For that you need some free space. Easy. Boot to Windows and shrink a partition or two to leave free space.

---

### Post by Thetri on 2015-10-01
I haven't used WUBI since 11.10. i didn't know it was still around. I was using the option on the live usb that says "Install alongside Windows 7" before. This allowed me to use my windows partition. I just move the slider to set how much space linux gets. I usually give it half my hdd something you should know isn't possible in WUBI. Doing it like this creates a partition from the space provided. screenshot of the option i'm trying to use: [http://pad3.whstatic.com/images/thumb/e/ec/Install-Ubuntu-Linux-Step-7Bullet1.jpg/670px-Install-Ubuntu-Linux-Step-7Bullet1.jpg](http://pad3.whstatic.com/images/thumb/e/ec/Install-Ubuntu-Linux-Step-7Bullet1.jpg/670px-Install-Ubuntu-Linux-Step-7Bullet1.jpg)

This method works on everything else except Ubuntu. I was wondering why its gone. I tried the install to unallocated partiton before and i got a grub2 rescue error so i avoid linux distro that don't let me do this.

---

### Post by Bucky Ball on 2015-10-01
Boot into Windows and switch off hibernation? And right first time: Wubi isn't around any more. It doesn't work on newer versions of Win, and as I say, not supported.

---

### Post by Thetri on 2015-10-06
I managed to get it to work by making a unallocated partition and then using gpart on the live USB. Odd how with kubuntu and Linux mint kde I didn't need to do that but it's no big deal it works. I shyed away from the something else option due to it looking complex and my fear of messing up my main windows install with all my gaming data. Thanks for the help.

---

### Post by Bucky Ball on 2015-10-06
Good news. Please see the first link in my signature. Thanks.

---

