---
title: "Installing Ubuntu 10.10 64-bit"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by lsuengineer on 2010-10-10
Hello,
I recently bought a new computer with Windows 7 64-bit installed. I would like to format the drive and install Ubuntu 64-bit - no dual boot. Normally the installer gave me the option to format and install Ubuntu, however, the only screen I get after "Preparing to install Ubuntu" looks like the attached screenshot. As you can see it is completely blank. I shouldent have to use something like GParted if I don't want to dual boot. What is the problem?

Thanks

---

### Post by GatoViejo on 2010-10-10
Are there any other devices in the boot loader menu? (besides /dev/sdf)
If so, what happens when you pick one?

---

### Post by nlsthzn on 2010-10-10
Which version of Ubuntu are you trying to install?

---

### Post by lsuengineer on 2010-10-10
There are no other options and it gives me the error "No root file system is defined" after selecting Install Now. This is release 10.10 64-bit Desktop. At first I thought it didn't support my hard drive, but my windows partition can be mounted in the live cd, so it recognises the other partitions.

---

### Post by GatoViejo on 2010-10-10
> **lsuengineer said:**
> "No root file system is defined"

means that you did not (or had no opportunity to) tell it what partition to use for root (/). If the disk is full of a windows install, then it has no free space to work with. If you are serious about removing windows forever (as I would be) then launch gparted and delete all existing partitions. Then the installer should have something to use.

---

### Post by lsuengineer on 2010-10-10
Ok, I deleted all of the partitions in GParted and restarted. I got the same error. Should I create a new partition (ext4) on the unallocated space? Will that give it a root?

---

### Post by konungursvia on 2010-10-10
> **lsuengineer said:**
> Ok, I deleted all of the partitions in GParted and restarted. I got the same error. Should I create a new partition (ext4) on the unallocated space? Will that give it a root?

Yes but you need an additional step. Choose "Edit partition" for the whole partition and set the mount point to /

That, in addition to choosing ext4 or whatever fs you prefer.

Then proceed.

---

### Post by lsuengineer on 2010-10-10
I do not see the option to set the mount point. I set the partition as primary. Why does the installation not give the the option to "erase and use entire disk"?

---

### Post by nlsthzn on 2010-10-10
> **lsuengineer said:**
> I do not see the option to set the mount point. I set the partition as primary. Why does the installation not give the the option to "erase and use entire disk"?

Thats the problem with the new installer in 10.10... I have no idea how it looks, what it is supposed to do (gotten used to the standard installation process over the last couple of years) :(

---

### Post by konungursvia on 2010-10-10
You should be able to format the partition using Gparted, then when you install from the Ubuntu disk you can select the partition, right click it and choose "edit partition" which will have a mount point drop down menu. It has in all other iterations of ubuntu.

---

### Post by lsuengineer on 2010-10-10
Please see the attached image. There is no place to set the mount point. I selected "boot" under flags, but I still get the same blank install screen. I tried an old 9.10 disk and got the same problem.

---

### Post by nlsthzn on 2010-10-10
> **lsuengineer said:**
> Please see the attached image. There is no place to set the mount point. I selected "boot" under flags, but I still get the same blank install screen. I tried an old 9.10 disk and got the same problem.

As far as I can recall you don't specify the mount points in GParted, only create the partitions you want and after this step in the installation you are supposed to select the partitions you want to install too and then select them to be mounted as /, /home and swap etc. (Will be installing 10.10 in a virtual machine when I get home because there are way to many people struggling with installation IMO and I can't figure it out).

---

### Post by allxk on 2010-10-13
This is a bug!
Please see attached image:
The disk partitioned with gparted.
Ubuntu 10.10 x64 Installation window will not show any partitions, and edit partition option.
Same thing with Ubuntu 10.10 x32.
Will somebody report it to developers?

---

### Post by nlsthzn on 2010-10-13
> **allxk said:**
> This is a bug!
Please see attached image:
The disk partitioned with gparted.
Ubuntu 10.10 x64 Installation window will not show any partitions, and edit partition option.
Same thing with Ubuntu 10.10 x32.
Will somebody report it to developers?

Well, I am very skeptical to just call any problem I am having a bug without many others experiencing the same problems as I am... however, if you feel certain you can check out [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=1011078") and report it as a bug... Not only might you get your problem solved you may solve the problem for others...

(As a final thought on your problem, have you tried installing 10.04 and seeing if the same thing happens?  If it does there may be another underlying cause perhaps...)

---

