---
title: "installing ubuntu 14.04 LTS in a disk partition."
date: 2014-07-31
forum: Installation &amp; Upgrades
---

### Post by abhi90 on 2014-07-31
Hello.
I have my old 500GB hdd and I decided to use it for ubuntu.
My disk partition is **C:50GB, D:150GB, E:100GB, F:200GB.**
I formatted **C drive** and I want to install ubuntu in it.
_**Can anyone tell me the exact procedure to install it.**_
My friend told me that there is difficulty in setting the **mounting point(\ or \home)** or something like that **(Don't know exactly) **and he also told me that he was trying to install it and end up in formatting the whole hard drive.
That's why I still not installed it.
I downloaded ubuntu 14.04 LTS(ISO) and **already create a bootable pendrive.**

---

### Post by The Cog on 2014-07-31
First, back up anything of importance from the entire drive. Hardware problems, software bugs and users errors can all trash the whole disk. User error is more likely if you are not familiar with the installer.

Second, you cannot install Linux onto any partition that has been formatted by windows - cannot install on NTFS. The easiest thing to do is to delete the partition and tell the installer that you want to use the free disk space. It will then create and format the required partition itself (probably create two partitions, the other one being swap space). Beware that the default action by the installer is to erase the entire disk.

Also be aware that the bootloader it installs relies on files placed on the Linux install partition. Never delete the Linux partition without replacing the linux bootloader (called GRUB) first.

---

### Post by abhi90 on 2014-07-31
How to delete the partition? Is there any option given while installation?
And what is the type of format i should choose? swap, ext3, ext4?
And what about mounting point?

---

### Post by Bashing-om on 2014-07-31
abhi90; Hi !

Admittedly a 1st time install can be confusing; Please show us what there is to work with.
Post back the outputs - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

``` with advisory of what you know is installed where, and with the info from those outputs, where you intend to install ubuntu.

[INDENT][INDENT]knowledge is power to advise
[/INDENT][/INDENT]

---

### Post by abhi90 on 2014-08-03
Which partition type i have to select ?
And which mount point should I use?

---

### Post by Mark Phelps on 2014-08-03
Instead of asking more questions, you would do better entering the commands you were told in post #4. We can't help you if you won't provide information.

---

