---
title: "Lost Windows XP Cause Of Linux"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by gccradioscience on 2010-11-16
I wish the installation process wouldn't mess up my Windows XP when installing Ubuntu 9.10  

 Back on a Sunday of November 14, 2010, I was trying to install linux Ubuntu 9.10 on my C Drive, but I wanted to install it on my Slave Drive, but the software did not want to give me an option to install on the slave drive.   The way the partitioning happenned it was not giving me any choice, but to install on my C Drive.  After I rebooted, the installation software gave me the option to install on the slave drive and I got it working. 

 Still I wish that the software would have the user pick out where to do the partition or if Windows XP is installed that it would take the free disk space to install the partiton for linux ubuntu 9.10 or any other upgrade.  If there is no hard disk space then it would not let it happen.  I would let it install it on the slave drive or flash drive, or external HDD.  

Now I have to call HP up and get some recovery CD's ordered to get Windows XP back cause of this big mistake.  Still I am able to get online with Ubuntu 9.10, but still I need Windows XP for my CD-ROM's and bought software.

---

### Post by Rubi1200 on 2010-11-16
Hi,
sorry to hear you are having troubles.

However, if you can boot into Ubuntu, please click on the link at the bottom of my post and follow the instructions there.

Post the results of the boot info script and we will see if there is a way to help you get back into your Windows installation.

Thanks.

---

### Post by pricetech on 2010-11-16
Unfortunately, computers do exactly what you tell them to, though not necessarily what you want them to.

Just guessing, but more than likely if it went the way you describe you haven't lost your XP.  Grub just missed it when you installed Ubuntu on your other drive.  As such, we should be able to help you get access to it.

If on the other hand, you wiped your primary master, XP is gone.

Let us know what the above mentioned script gives you and we'll go from there.

---

### Post by TNT1 on 2010-11-16
Sounds like an opportunity to bin windows and go full linux. Welcome.

---

### Post by cyberphrog on 2010-11-16
If/when you get your WinXP restore disks, consider reloading windows as a VM.  I've done this on several boxes for various family members (with Ubuntu as the host OS) and it seems to work well...

---

### Post by pricetech on 2010-11-16
May not work so well with a restore disk since it will have a lot of other junk spun into the OS.

Otherwise I agree with using the VM.

---

### Post by kansasnoob on 2010-11-16
> **gccradioscience said:**
> I wish the installation process wouldn't mess up my Windows XP when installing Ubuntu 9.10  

 Back on a Sunday of November 14, 2010, I was trying to install linux Ubuntu 9.10 on my C Drive, but I wanted to install it on my Slave Drive, but the software did not want to give me an option to install on the slave drive.   The way the partitioning happenned it was not giving me any choice, but to install on my C Drive.  After I rebooted, the installation software gave me the option to install on the slave drive and I got it working. 

 Still I wish that the software would have the user pick out where to do the partition or if Windows XP is installed that it would take the free disk space to install the partiton for linux ubuntu 9.10 or any other upgrade.  If there is no hard disk space then it would not let it happen.  I would let it install it on the slave drive or flash drive, or external HDD.  

Now I have to call HP up and get some recovery CD's ordered to get Windows XP back cause of this big mistake.  Still I am able to get online with Ubuntu 9.10, but still I need Windows XP for my CD-ROM's and bought software.

Are you certain it was 9.10 and not 10.10?

I always found the old ubiquity quite clear.

Since you seem to be running Ubuntu please post the output of:

```
lsb_release -a
```

---

### Post by gccradioscience on 2010-11-17
> **kansasnoob said:**
> Are you certain it was 9.10 and not 10.10?

I always found the old ubiquity quite clear.

Since you seem to be running Ubuntu please post the output of:

```
lsb_release -a
```

It was Ubuntu 9.10 not 10.10.

---

### Post by gccradioscience on 2010-11-17
> **cyberphrog said:**
> If/when you get your WinXP restore disks, consider reloading windows as a VM.  I've done this on several boxes for various family members (with Ubuntu as the host OS) and it seems to work well...

How do I do that?   Using Virtual Machine?   I have to look into that.  Thanks for the suggestion.

---

### Post by cyberphrog on 2010-11-19
> **gccradioscience said:**
> How do I do that?   Using Virtual Machine?   I have to look into that.  Thanks for the suggestion.
For a virtual machine, download/install VirtualBox.  From there, you can create a VM and load an OS into it (you'll need a Windows OS disk if you want windows).  You can create multiple VMs for multiple purposes.

---

