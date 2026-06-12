---
title: "Installing and choosing the right Ubuntu"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by NoSuchDevice on 2010-11-02
Hello All,

Recently I install ubuntu using wubi 10.4, and then from there I upgraded it to 10.10, and yes it all went south, but luckily I managed to fix the whole dam computer. 

Now I was just wondering I want a very very easy way to install ubuntu I was looking at ubuntu 9, and was wondering is there any program like wubi which can install it, cause I will probably kill my computer if I try another way. Also my main purpose will be programming so is ubuntu 9 good for that?

Thanks
NoSuchDevice

---

### Post by pizza-is-good on 2010-11-02
Welcome to Ubuntu!

Sorry to hear that you had a bad experience with the upgrade, but I'm glad you got it working.

There are currently two 'live' versions of Ubuntu, Ubuntu 10.04LTS and Ubuntu 10.10. There are also a number of versions that are still being supported, Ubuntu 8.04LTS and 9.10 are both being supported until next April.
While you can install an older version, there really is no reason to do so.
The version number of Ubuntu is as follows: Year.Month (So 10.10 is October 2010, 10.04 is April 2010, 8.04 is April 2008, etc..). LTS means Long Term Support.
There really isn't a Ubuntu 9... You have 9.04 and 9.10. Both are good, in fact, 9.10 was my favorite Ubuntu, but it doesn't have the latest features and will not be supported for much longer.
It is recommended you choose either the 10.10 or 10.04LTS, as they are the most up to date and will be supported for the most time.

Any Ubuntu is good for programming.

As for ease of installation, there are 2 main ways to install Ubuntu: directly onto your Hard Drive, or through Wubi. Both are really simple, and if you are a programmer, you should have no difficulty installing it onto your hard drive. If you do install it to your hard drive, you can install it side by side with windows, so when you turn on your computer you can choose which operating system to use. This is called a dual boot system, and is what most of us use.

If you follow the steps provided by canonical or outlined in many places in these forums, you will not kill your computer. If you still need more help, just ask away!

~pizza

---

### Post by NoSuchDevice on 2010-11-02
Well I am a beginner programmer so still at the early age, as for installing I really don't want to mess up the boot loader like I did before meaning I could not boot in to windows. So is there a programme which will install ubuntu 10.10? (and yes dual boot is the main thing I need to do as well)

Thanks

---

### Post by pizza-is-good on 2010-11-02
Wubi is available for Ubuntu 10.10. It should work in the same way as it did when you installed it before.

You have to note, however, that using wubi installs Ubuntu as a program in Windows, which does not allow Ubuntu to run as well and as fast as it would if it is installed alongside.

When you do a dual-boot installation, Ubuntu automatically installs a boot-loader called GRUB 2. Other than in some rare cases, GRUB will recognize all of the OSs installed in a hard drive. If for some reason an OS doesn't show up, it _can_ be added. Just because it doesn't show up doesn't mean its not there.

I have not yet installed 10.10, but I have heard that the installation and dual-boot set up process is much easier to do than in 10.04, where it already was really easy. Again, if this is the way you want to go, we can guide you along.

So, do you want to dual boot or use wubi?

~pizza

---

### Post by NoSuchDevice on 2010-11-02
Will wubi be safe for long run? If not I will go the other way.

btw I have already made a 20GB partition


Thanks

---

### Post by pizza-is-good on 2010-11-02
Wubi is definitely safe in the long run. If you mean safety as in security.
Is it practical? Well, no, not really. Wubi's main purpose is to allow new users to test and play around in ubuntu before deciding to rearrange their HDD to install it. It gives users the ability to save their changes in the system, without loosing them all as with a LiveCD. While it is possible to permanently use Wubi, it prevents you from unleashing the full potential of ubuntu. Also, keep in mind, that since in Wubi ubuntu is installed in windows, if anything corrupts your windows installation, your ubuntu one will probably be compromised as well. It is always nice to have a backup.
I'm not against the idea of Wubi, but it really doesn't make much sense to use it if you plan on using ubuntu in the long run.

~pizza

---

### Post by NoSuchDevice on 2010-11-03
OK I won't use Wubi to install however I got two questions.

1. One will ubuntu installation automatically configure the bootloader so I can boot in windows or ubunu?

2. I have made a partion of 20GB and assigned drive letter L for ubuntu, now when installing ubuntu how do I select the L drive?

Thanks
NoSuchDevice.

---

### Post by pizza-is-good on 2010-11-03
In answer to your first question, yes, the installation will automatically configure the bootloader. You might have to uninstall wubi before you install ubuntu. It seems to me as if leaving it installed might give some problems, but I have no experience with wubi, so don't take my word for it.

As for your second question. It is good that you created the partition, although it wasn't nevessary, it will save you a little time during the installation. Ubuntu doesn't work with drive letters, so you'll never see the 'L'. There are other ways to tell. Boot into a live CD of ubuntu, open up a terminal window (the command prompt in ubuntu), and type:```
sudo fdisk -l
```(just copy it from the text box in my post, that way you don't have spelling errors. The last letter is a lowercase L)
Then post the output here so I can tell you how to select your partition during installation.

The first thing you'll have to decide is which version to use, if 10.04 or 10.10. Get a live CD of both, and play around with them, to see which one you like better and which one works better with your hardware. Let me know if you need help creating the live CD.


~pizza

---

### Post by ctbear on 2010-11-03
I'm new to ubuntu and I'm a little confused about wubi and dual boot. What are the disadvantages of wubi against a native dual boot option?

---

### Post by NoSuchDevice on 2010-11-03
> **pizza-is-good said:**
> In answer to your first question, yes, the installation will automatically configure the bootloader. You might have to uninstall wubi before you install ubuntu. It seems to me as if leaving it installed might give some problems, but I have no experience with wubi, so don't take my word for it.

As for your second question. It is good that you created the partition, although it wasn't nevessary, it will save you a little time during the installation. Ubuntu doesn't work with drive letters, so you'll never see the 'L'. There are other ways to tell. Boot into a live CD of ubuntu, open up a terminal window (the command prompt in ubuntu), and type:```
sudo fdisk -l
```(just copy it from the text box in my post, that way you don't have spelling errors. The last letter is a lowercase L)
Then post the output here so I can tell you how to select your partition during installation.

The first thing you'll have to decide is which version to use, if 10.04 or 10.10. Get a live CD of both, and play around with them, to see which one you like better and which one works better with your hardware. Let me know if you need help creating the live CD.


~pizza


Thanks for your help, much appreciated. OK here is the info from the terminal code:

```
Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       39516   317406684    7  HPFS/NTFS
/dev/sda2           39516       42427    23387136    7  HPFS/NTFS
/dev/sda3           42428       43777    10843875    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
1 heads, 63 sectors/track, 15504336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06b70da3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2    15504256   488384028    7  HPFS/NTFS

```

OK I will stick with UBUNTU 10.4 LTS for now, then later update to 10.10. Also I am guessing it's the sda2 (but you can confirm that), just need to know what to select upon install. 

Cheers
NoSuchDevice.

---

### Post by TBABill on 2010-11-03
ctbear, it's normally good to start a new thread if your question is a bit different than the original poster's questions or comments, but easy enough to answer.
 
Basically a Wubi install is inside of Windows. When you boot up Windows you can then go into your Ubuntu Wubi install. When you dual boot, both operating systems reside on the same or different drives (different partitions if they share one drive) and you select which operating system you want the computer to use for that session. The only way to get to the other operating system in that configuration is to restart and select the other one at the Grub2 menu. It's very simple to do but it does keep your systems completely separate from each other. 
 
The reason you have a Grub2 menu is because Windows' native boot loader does not care about or expect other operating systems. Ubuntu uses Grub2 so that it can see any other operating system and allow you to use whichever you choose. Basically you have Windows installed, then install Ubuntu...and on every restart you see the Grub2 menu and select Ubuntu or Windows. 
 
I hope that clears it up a bit. If you have further questions please post a new thread and you'll get lots of assistance with anything you may need.

---

### Post by pizza-is-good on 2010-11-03
> **NoSuchDevice said:**
> Thanks for your help, much appreciated. OK here is the info from the terminal code:

```
Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       39516   317406684    7  HPFS/NTFS
/dev/sda2           39516       42427    23387136    7  HPFS/NTFS
/dev/sda3           42428       43777    10843875    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
1 heads, 63 sectors/track, 15504336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06b70da3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2    15504256   488384028    7  HPFS/NTFS

```OK I will stick with UBUNTU 10.4 LTS for now, then later update to 10.10. Also I am guessing it's the sda2 (but you can confirm that), just need to know what to select upon install. 

Cheers
NoSuchDevice.

Thank you for the output. Yes, it looks like /dev/sda2 is your 20 GB partition. What is in sda3 (the 10GB partition)?

OK, here is what to do now. Download and burn to a CD the Ubuntu 10.04LTS CD (you may already have done that).
Backup all your data! It is often overlooked, as the installation is very reliable nowadays, but it is always a good idea to backup.
Unplug your external. There is no need for it to be plugged in during the installation.

sda2 is formatted as NTFS. It is not recommended that you install a linux OS in a windows partition. You can either format it to ext4 from the live cd, or do that during the installation.
Also, are you planning on using the hibernate mode in ubuntu once you install it? If so you will need to create swap space.

After that, put in the ubuntu CD, and go through the installation. Make sure you select sda2 as the install partition.
A recommendation from personal experience with my 10.04 install: When you put in the live CD, select 'try ubuntu without installing'. Then get into the desktop. Enable all your hardware drivers (System>>Administration>>Hardware Drivers). Have an Internet connection. Make sure everything works. Now use the 'install ubuntu' icon on the desktop. You will still be able to use ubuntu while it is installing, so if you run into any problems or have any questions, just open up firefox and ask. Don't do anything you are not sure of.

Good luck!

~pizza

---

### Post by janpol on 2010-11-03
Another alternative, is to install Ubuntu inside a Virtual Machine in Windows using Virtual Box if you are not shure about installing it in the HDD, or if you just want to play with it for a while. 

I thought it was worth mentioning ;)

---

### Post by ctbear on 2010-11-03
> **TBABill said:**
> ctbear, it's normally good to start a new thread if your question is a bit different than the original poster's questions or comments, but easy enough to answer.
 
Basically a Wubi install is inside of Windows. When you boot up Windows you can then go into your Ubuntu Wubi install. When you dual boot, both operating systems reside on the same or different drives (different partitions if they share one drive) and you select which operating system you want the computer to use for that session. The only way to get to the other operating system in that configuration is to restart and select the other one at the Grub2 menu. It's very simple to do but it does keep your systems completely separate from each other. 
 
The reason you have a Grub2 menu is because Windows' native boot loader does not care about or expect other operating systems. Ubuntu uses Grub2 so that it can see any other operating system and allow you to use whichever you choose. Basically you have Windows installed, then install Ubuntu...and on every restart you see the Grub2 menu and select Ubuntu or Windows. 
 
I hope that clears it up a bit. If you have further questions please post a new thread and you'll get lots of assistance with anything you may need.

I apologize. I figured my question was similar to the OP's so I might as well ask here.
I will go make a separate thread :)

---

### Post by NoSuchDevice on 2010-11-03
> **pizza-is-good said:**
> Thank you for the output. Yes, it looks like /dev/sda2 is your 20 GB partition. What is in sda3 (the 10GB partition)?

OK, here is what to do now. Download and burn to a CD the Ubuntu 10.04LTS CD (you may already have done that).
Backup all your data! It is often overlooked, as the installation is very reliable nowadays, but it is always a good idea to backup.
Unplug your external. There is no need for it to be plugged in during the installation.

sda2 is formatted as NTFS. It is not recommended that you install a linux OS in a windows partition. You can either format it to ext4 from the live cd, or do that during the installation.
Also, are you planning on using the hibernate mode in ubuntu once you install it? If so you will need to create swap space.

After that, put in the ubuntu CD, and go through the installation. Make sure you select sda2 as the install partition.
A recommendation from personal experience with my 10.04 install: When you put in the live CD, select 'try ubuntu without installing'. Then get into the desktop. Enable all your hardware drivers (System>>Administration>>Hardware Drivers). Have an Internet connection. Make sure everything works. Now use the 'install ubuntu' icon on the desktop. You will still be able to use ubuntu while it is installing, so if you run into any problems or have any questions, just open up firefox and ask. Don't do anything you are not sure of.

Good luck!

~pizza

Thanks for the reply. The 10GB is a windows vista recovery partition. If it is not recommended to install on a windows partition then what shall I do stick with it? or not?

Also

OK i got this  problem when I get to the screen "prepare disk space" what do I select?

Specify Partion manually? Then select the sad2 ?

---

### Post by pizza-is-good on 2010-11-03
> **NoSuchDevice said:**
> Thanks for the reply. The 10GB is a windows vista recovery partition. If it is not recommended to install on a windows partition then what shall I do stick with it? or not?

Yes, definitely stick with it. It is not at all a big deal. All that happens during installation is that said NTFS partition (sda2) will be formatted to ext4.

---

### Post by pizza-is-good on 2010-11-03
> **NoSuchDevice said:**
> 
OK i got this  problem when I get to the screen "prepare disk space" what do I select?

Specify Partion manually? Then select the sad2 ?

Yes, but if you can post a screenshot, that would help. Applications>>Accessories>>Take Screenshot.

~pizza

---

### Post by NoSuchDevice on 2010-11-03
OK here it is:

---

### Post by NoSuchDevice on 2010-11-03
oh here is another one just to speed things up, this is if I select the option "Specify partions manually"

---

### Post by pizza-is-good on 2010-11-03
> **NoSuchDevice said:**
> oh here is another one just to speed things up, this is if I select the option "Specify partions manually"

OK, select sda2 and then check the 'format' box.

---

### Post by NoSuchDevice on 2010-11-03
OK I can't check the "format" but  I doubled clicked it and anther screen came up. 

It said "Use As" and you can see my selection via the image, however what is the "Mount Point"?

Cheers
NoSuchDevice

---

### Post by pizza-is-good on 2010-11-03
what options does it give you under 'Mount Point'?

---

### Post by NoSuchDevice on 2010-11-03
OK It gigves these ones:

/

/Home

/Boot

OK there are a few more But I am not on Ubuntu now, I could not leave it on, sorry, someone would have come a long and mess things up. :( and the "/" is there as well.

---

### Post by pizza-is-good on 2010-11-03
OK, I'm pretty sure that it is 
```
/
```That would be 'root'.

If you want to be sure, I would recommend you use GParted (System>>Administration>>GParted) from the Ubuntu liveCD to format sda2 to ext4. That should do it for you.

The mount point is where you want that partition mounted (kind of like drive letters in windows). / or root, would be like your C drive, that is where all the system files are stored. /home is like 'my documents', that is where user files are stored. If you don't specify one, it will be placed inside root. /boot is where the boot files are stored. If you don't specify anything, boot will be placed in the Master Boot Record.

I'm gonna run now for today, but post again if you have any questions.

~pizza

---

