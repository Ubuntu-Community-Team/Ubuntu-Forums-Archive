---
title: "Slow fresh install"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by exsheeple on 2016-10-11
I am installing a fresh copy of Ubuntu 16.04 via CDROM on a PC:

Processor - AMD Phenom(tm) II X4 965 Processor, MMX, 3DNow (4 CPUs) 3.4GHz 
Memory:	 12GB 
Hard Drive:	 1TB.  

It is installing extremely slow.  I have installed Ubuntu on other PC's that were considerably lower specs.  What could be causing this issue?  Thanks!!!!

---

### Post by RobGoss on 2016-10-11
Hello and welcome, You might try installing Ubuntu from a USB drive sometimes a CD installations may take a bit longer depending on the CD drive and condition. I have a laptop that takes twice as long to install any OS but if I us a USB it's much faster

---

### Post by howefield on 2016-10-12
> **exsheeple said:**
> I am installing a fresh copy of Ubuntu 16.04 via CDROM on a PC:

Processor - AMD Phenom(tm) II X4 965 Processor, MMX, 3DNow (4 CPUs) 3.4GHz 
Memory:	 12GB 
Hard Drive:	 1TB.  

It is installing extremely slow.  I have installed Ubuntu on other PC's that were considerably lower specs.  What could be causing this issue?  Thanks!!!!

Can you give some context to "extremely slowly", what does it mean ?

In my experience 16.04 seems to take longer to install than previous releases on the same hardware but not to the point of thinking it an exceptional issue.

---

### Post by exsheeple on 2016-10-12
The total installation took maybe about 4 hours or so. Could it be the actual hard drive that's slowing down the installation process?

---

### Post by RobGoss on 2016-10-12
4- hours is extremely long it shouldn't take that long most of my installations take about 5 minutes or so. On one of my older laptops the installations take much longer so I would say yes on older machines it may take longer then expected depending on the hardware and on that machine

---

### Post by exsheeple on 2016-10-12
I agree. It never took that long when I used the computer to dual boot with Windows. This is a hard drive that I have taken out of another computer,  formatted it,  and install Ubuntu only. Could it be the hard drive causing this issue?

---

### Post by howefield on 2016-10-12
> **exsheeple said:**
> The total installation took maybe about 4 hours or so. Could it be the actual hard drive that's slowing down the installation process?

If you mean 4 hours from booting the Live media to having a default install then that is way excessive, when I said 16.04 seemed slower to install I (for me) I meant roughly taking 20 minutes where it was 10 minutes previously, although I never timed it, just a feeling :)

If by "total" you mean including configuring and installing extra software on top of the actual install of Ubuntu then that's a different thing. Did you opt to download updates and proprietary software during the installation process, perhaps you had network issues ?

---

### Post by exsheeple on 2016-10-12
It usually does take about 20 or 30 minutes normally. I did not choose to download the necessary drivers during installation. It was pretty quick to come up to the live CD screen. I don't think there are any issues with the CD ROM but I will try the installation via USB and see if I experienced the same problem. I did not notice the CD-ROM light flashing during the installation,  side note

---

### Post by howefield on 2016-10-12
Might be worth running the Disk utility tests and benchmarks on the disk then.

---

### Post by exsheeple on 2016-10-12
Do you know any software that I can use to test the disks? Is there something on the live CD?

---

### Post by RobGoss on 2016-10-12
Hello I came across this post it may help you with testing the disk and other problems [https://apps.ubuntu.com/cat/applications/testdisk/](https://apps.ubuntu.com/cat/applications/testdisk/)

You can also find the post here
 [http://askubuntu.com/questions/398335/how-to-install-testdisk-in-ubuntu-13-10](http://askubuntu.com/questions/398335/how-to-install-testdisk-in-ubuntu-13-10)

---

### Post by howefield on 2016-10-13
> **exsheeple said:**
> Do you know any software that I can use to test the disks? Is there something on the live CD?

As I mentioned, load up the Disks utilities and run the benchmarks and tests from there.

---

### Post by exsheeple on 2016-10-13
I installed testdisk but found no how-to on using the app for test disk health, only recovering data.  I used pendrivelinux to create a bootable disk but the PC didnt see the usb as being a bootable media even after accessing the BIOS and choosing the boot the the removable device strangely.  This is madness!

---

### Post by RobGoss on 2016-10-13
> **exsheeple said:**
> I installed testdisk but found no how-to on using the app for test disk health, only recovering data.  I used pendrivelinux to create a bootable disk but the PC didnt see the usb as being a bootable media even after accessing the BIOS and choosing the boot the the removable device strangely.  This is madness!

Try using a different USB port maybe the one you are using is not working correctly

---

### Post by exsheeple on 2016-10-13
This is crazy... Different hard drive.... Installed like a dream! I checked original hard drive and it seems healthy. I guess not. Any who, thanks for your help

---

