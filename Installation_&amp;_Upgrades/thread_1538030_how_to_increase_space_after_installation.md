---
title: "how to increase space after installation"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by harpinder on 2010-07-24
hi
i have installed ubuntu 10.04 inside windows 7.my window is on c drive and ubuntu is on d drive.on installation i have only give 5gb space to ubuntu.but now i want to increase this space for ubuntu as a full drive i.e the whole drive for ubuntu.
is this possible without uninstall? or i have to reinstall ubuntu.
i dont want to losse my data on ubuntu like upgrades and other softwares that i have installed.now i have only 1 gb free space.
please help
thanks

---

### Post by Rubi1200 on 2010-07-24
> **harpinder said:**
> hi
i have installed ubuntu 10.04 inside windows 7.my window is on c drive and ubuntu is on d drive.on installation i have only give 5gb space to ubuntu.but now i want to increase this space for ubuntu as a full drive i.e the whole drive for ubuntu.
is this possible without uninstall? or i have to reinstall ubuntu.
i dont want to losse my data on ubuntu like upgrades and other softwares that i have installed.now i have only 1 gb free space.
please help
thanks

> i have installed ubuntu 10.04 inside windows 7

Did you install using Wubi or with the Ubuntu CD?

From within Ubuntu, go to the terminal and post the output of this:

```
sudo fdisk -l
```

---

### Post by ServerStorm on 2010-07-24
Hi harpinder,

You need to make sure that your Master Boot Record is on your Ubuntu installation. To do this:

[LIST=1]
[*]Download and create a Live CD of Ubuntu
[*]Reboot into the Live CD
[*]Open the console
[LIST]
[*]# sudo grub
[/LIST]
[*]Find your Linux drive:
[LIST]
[*]grub# find /boot/grub/stage1
[*]for example this might return (hd2, 0)
[/LIST]
[*]Install GRUB into the Master Boot Record (MBR) of the Linux drive:
[LIST]
[*]grub# root(hd2, 0)
grub# setup(hd2)
[/LIST]
[*]Open System -> Administration -> gParted (Use synaptic package manager to install it if you don't see it). Select the drive where you put the MBR and add the 'boot' flag to it.
[*]Your  Windows boot entries will be in menu.lst, you can safely delete them.
[*]You can again use gParted and delete the volume(s) where window files are installed. You can recreate the raw space as a data drive for your Linux or resize your existing Linux (data) drives.
[/LIST]
Hope this helps,
Steve

---

### Post by bcbc on 2010-07-24
> **harpinder said:**
> hi
i have installed ubuntu 10.04 inside windows 7.my window is on c drive and ubuntu is on d drive.on installation i have only give 5gb space to ubuntu.but now i want to increase this space for ubuntu as a full drive i.e the whole drive for ubuntu.
is this possible without uninstall? or i have to reinstall ubuntu.
i dont want to losse my data on ubuntu like upgrades and other softwares that i have installed.now i have only 1 gb free space.
please help
thanks
You can migrate the wubi install: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

@severstorm: you're referring to grub-legacy, not grub2 which comes with 10.04. And installing grub to the MBR from a wubi install will make the computer unbootable. Either way - strange advice since the issue is one of space, not booting.

---

### Post by arpanaut on 2010-07-24
What in this post has anything to do with the OP question about gaining more space on his **WUBI** installation, on top of that 10.4 uses Grub2 and these instructions are for legacy grub.

I don't understand what you are trying to accomplish by this post.
@harpinder, this has nothing to do with your question, please ignore.

> **ServerStorm said:**
> Hi harpinder,

You need to make sure that your Master Boot Record is on your Ubuntu installation. To do this:

[LIST=1]
[*]Download and create a Live CD of Ubuntu
[*]Reboot into the Live CD
[*]Open the console
[LIST]
[*]# sudo grub
[/LIST]
[*]Find your Linux drive:
[LIST]
[*]grub# find /boot/grub/stage1
[*]for example this might return (hd2, 0)
[/LIST]
[*]Install GRUB into the Master Boot Record (MBR) of the Linux drive:
[LIST]
[*]grub# root(hd2, 0)
grub# setup(hd2)
[/LIST]
[*]Open System -> Administration -> gParted (Use synaptic package manager to install it if you don't see it). Select the drive where you put the MBR and add the 'boot' flag to it.
[*]Your  Windows boot entries will be in menu.lst, you can safely delete them.
[*]You can again use gParted and delete the volume(s) where window files are installed. You can recreate the raw space as a data drive for your Linux or resize your existing Linux (data) drives.
[/LIST]
Hope this helps,
Steve

---

### Post by bcbc on 2010-07-24
> **bcbc said:**
> You can migrate the wubi install: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

...

Just to elaborate - if you want to use up the whole 'drive d:' for ubuntu and your wubi is currently installed on d:,  the migrate script I linked to above will not allow you to migrate to the same partition.

I recommend shrinking your D: drive so you get a new partition, then migrating straight to that. Creating a swap partition is also a good idea. (Since you can only have 4 primary partitions, creating an extended partition gives you the most flexibility).

---

### Post by ServerStorm on 2010-07-25
Sorry I should have read the post, question and version more closely. After re-reading your situation my advice does stink :( Sorry Harpinder... hopefully the others helped :oops:

Regards,
Steve

---

### Post by harpinder on 2010-07-25
> **Rubi1200 said:**
> Did you install using Wubi or with the Ubuntu CD?

From within Ubuntu, go to the terminal and post the output of this:

```
sudo fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe442e442



i have installed using ubuntu cd
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       19456   135307462+   f  W95 Ext'd (LBA)
/dev/sda5            2612        5875    26218048+   7  HPFS/NTFS
/dev/sda6            5876       12402    52428096    7  HPFS/NTFS
/dev/sda7           12403       19456    56661223+   7  HPFS/NTFS

---

### Post by harpinder on 2010-07-25
> **ServerStorm said:**
> Sorry I should have read the post, question and version more closely. After re-reading your situation my advice does stink :( Sorry Harpinder... hopefully the others helped :oops:

Regards,
Steve

no problem brother,your are always welcome

---

### Post by harpinder on 2010-07-25
> **bcbc said:**
> Just to elaborate - if you want to use up the whole 'drive d:' for ubuntu and your wubi is currently installed on d:,  the migrate script I linked to above will not allow you to migrate to the same partition.

I recommend shrinking your D: drive so you get a new partition, then migrating straight to that. Creating a swap partition is also a good idea. (Since you can only have 4 primary partitions, creating an extended partition gives you the most flexibility).

i have 4 drives c,d,e,f. can i use e or f drive to migrate wubi as their is enough free space available.

---

### Post by harpinder on 2010-07-25
> **arpanaut said:**
> What in this post has anything to do with the OP question about gaining more space on his **WUBI** installation, on top of that 10.4 uses Grub2 and these instructions are for legacy grub.

I don't understand what you are trying to accomplish by this post.
@harpinder, this has nothing to do with your question, please ignore.
thanks man

---

### Post by bcbc on 2010-07-26
> **harpinder said:**
> i have 4 drives c,d,e,f. can i use e or f drive to migrate wubi as their is enough free space available.

yes you can use any partition that is big enough and empty.

---

### Post by harpinder on 2010-07-26
> **bcbc said:**
> yes you can use any partition that is big enough and empty.

i have moved the wubi to f drive.i think so ;).as there are same files and folders on the d and f drive.so i think it is successful.
now,can i uninstall it from inside window?

---

### Post by bcbc on 2010-07-26
> **harpinder said:**
> i have moved the wubi to f drive.i think so ;).as there are same files and folders on the d and f drive.so i think it is successful.
now,can i uninstall it from inside window?

Yes, if you
1. chose to install the grub bootloader 
2. have booted into your new install and used it and everything looks good.

Also, if you didn't set up a [swap]("https://help.ubuntu.com/community/SwapFaq") partition, then I recommend creating one (or use a swap file). The swap file won't allow hibernation, but it will work the same as a swap partition to improve performance if you do memory intensive tasks.

If you're still not sure you can post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and I can have a look at what you've got.

---

### Post by harpinder on 2010-07-26
after installing grub bootloader i am not able to boot into ubuntu from the windows boot loader.whats going wrong.as i am a normal user i do not understand what is swap and how to make work it.
thanks for your help

---

### Post by bcbc on 2010-07-26
> **harpinder said:**
> after installing grub bootloader i am not able to boot into ubuntu from the windows boot loader.
Can you boot windows? When you select it from the grub menu, do you still get the windows boot manager offering Windows or Ubuntu? What error do you get when you select Ubuntu from the windows boot manager?


> **harpinder said:**
> whats going wrong.as i am a normal user i do not understand what is swap and how to make work it.
thanks for your help
That link I gave you in the last post explains what swap is and how to set it up. If there is any part of it that is unclear I can try and clarify.

---

### Post by harpinder on 2010-07-26
[QUOTE=bcbc;9638594]Can you boot windows? When you select it from the grub menu, do you still get the windows boot manager offering Windows or Ubuntu? What error do you get when you select Ubuntu from the windows boot manager

yes i am using window now, it boots successfully.but when i use ubuntu in window boot manger it restarts my laptop.thats the problem.i have not uninstalled the wubi inside windows.after updating grub it shows the ubuntu two times i.e indide window and on disk f.i think so.what u think.

---

### Post by bcbc on 2010-07-26
> **harpinder said:**
> yes i am using window now, it boots successfully.but when i use ubuntu in window boot manger it restarts my laptop.thats the problem.i have not uninstalled the wubi inside windows.after updating grub it shows the ubuntu two times i.e indide window and on disk f.i think so.what u think.

No the 'two times' is simply the number of kernels you have (or normal and rescue mode). Grub won't automatically pick up a wubi install inside windows and list it - you have to select windows and then select Ubuntu.

But run the bootinfoscript (I added a link to the howto in a previous post). That should show what has happened.

---

### Post by harpinder on 2010-07-26
as i am not able to boot into ubuntu then how can i use bootinfoscript.

---

### Post by bcbc on 2010-07-26
> **harpinder said:**
> i have moved the wubi to f drive.i think so ;).as there are same files and folders on the d and f drive.so i think it is successful.
now,can i uninstall it from inside window?

How exactly did you migrate your wubi? Did you use the instructions on this link ([http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)) I provided?

What is the first menu you see when you boot your computer (after the bios loads)?

---

### Post by harpinder on 2010-07-27
first menu is windows boot loader.in this windows7 and ubuntu are present.but when i select ubuntu it restarts my laptop.

---

### Post by seba505 on 2011-07-08
Hello,

I am having the same problem with allocating space after installing Ubuntu 10.04 LTS using wubi.
Windows is installed on C and Ubuntu is installed on D from within Windows. I left the default 17GB setting when I installed it.
I just want to have one computer in the network where everybody can share files. The D drive has ~60GB of space.

In home/user there are only 12.6 GB of free space and would like to expand this to the remaining free space.

Any thoughts on how to achieve this? Thanks


**sudo fdisk -l** says the following:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa5dfa5df

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/sda5            1276        9728    67898691    7  HPFS/NTFS

---

