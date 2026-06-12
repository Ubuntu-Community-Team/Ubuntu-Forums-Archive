---
title: "Install multiple flavors linux - best way"
date: 2014-12-14
forum: Installation &amp; Upgrades
---

### Post by Edho on 2014-12-14
Hello,

Best way to install Ubuntu 14.04 LTS ?

Situation now :

Hardware :
AMD Athlon X2 - 2.2 Ghz , 3.7 Gb ram , 500 Gb harddisk.
According Gparted...
- sda1 - ext4 - 450 GIB (boot)
- sda2 - extended 14.65 GiB
     sda5 linux-swap 14.65 GiB

Operation System :
Ubuntu 10.10 Maverick ... (updates ended)
-------------------------------
I want install 14.04 LTS BUT keep (for now) 10.10 as choice.
(for safety in case things go wrong)
Later i want install other linux flavors to play with.
For example ..before booting i get a choice beween 4 OS.

What is the best way to install?
- Harddisk partitioning before install?
- Or the partitioning can also during install?

How do i start?
Any tips?

Thank You.

---

### Post by tdmeskimo on 2014-12-14
Another choice that I did was to use the AHCI feature on my motherboard ( [http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface) ) to pick a HDD with one OS on it.  So like the system I am on now I have a Win7 HDD, Ubuntu Unity HDD, and a Xubuntu HDD, before I turn my system on I pick the OS I want slide the HDD in and turn on.  With some hardware HDD tray I don't have to open the case up, just slide in and lock the tray and boot.  That is the upside, the down side of this is trying to rember what is on each HDD, now I started to us perment markers, :-)  as well by my choice a HDD for each OS to play with. :p  What I like about using the AHCI feature is I can "hot" swap data (not the OS) HDD while the system is on and running.

So you could check out your motherboard to see if it supports AHCI feature, and if so have fun.

---

### Post by oldfred on 2014-12-14
I have many installs of Ubuntu. For a while I had every install from 10.10 thru 13.xx, but ran out of room and started overwriting. I use 20 or 25G for / (root) for every system and have data in a large data partition that I mount in every install. I also moved Firefox & Thunderbird profiles (and some other larger hidden folders in /home that may have lots of data, not not system settings) into my shared data partition. 

Some may suggest using virtualbox, but that needs newer hardware and enough RAM that you can share between installs. 

How much room do you have in current / , can you shrink it and can you create a data partition to move data into, then shrink / even more so you can create more partitions for other / (root)?

Post this:
df -h

---

### Post by grahammechanical on 2014-12-14
I have several installs of Ubuntu and its flavours on my two hard disks. I always use the Something Else option. I use Gparted from a live session to create the partitions. Gparted will let us queue up actions but I always run one action at a time because a queue of actions will take a long time to complete.

I have one very large partition where I keep my data. I then have 15 - 20 GB partitions into which I install Ubuntu. I do not have a separate /home partition or a separate /boot partition. I can access my data from any install of Ubuntu. Keep in mind that the last Linux to be installed will take control of the Grub boot menu.

I select one installation to be the main daily driver. Then whenever a new install takes over control of the boot menu (a kernel update of existing installs will do the same thing), I load my daily driver Ubuntu and run

```
sudo update-grub
sudo grub-install /dev/sda
```

In this way my daily driver OS is at the top of the boot menu and will automatically load after the time out of 10 seconds. In fact, my daily driver Ubuntu is on my second hard disk so I use /dev/sdb instead of /dev/sda. Just so you know how it works.

Regards

---

### Post by Dennis N on 2014-12-14
> According Gparted...
- sda1 - ext4 - 450 GIB (boot)
- sda2 - extended 14.65 GiB
sda5 linux-swap 14.65 GiB

Faced with this, this is how I would proceed:

I assume "boot" partition that you indicate should be root partition. Assuming sda2 only contains the swap partition, I would delete sda5 and sda2 first (they will be replaced). Then shrink sda1 down to reflect the current and future expected use by the existing Ubuntu OS. The remaining disk space is now unallocated. Create an extended partiton out of the entire unallocated space. Inside that extended partiton, add a swap partition (size equal to amt. of RAM), then one or more logical partitions for new OS installs. All OSes on the disk will share the same swap.

To maintain multiple OSes, you should consider (eventually) using a custom grub menu:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by Edho on 2014-12-14
Thanks all for the tips.

df -h command give this 

Filesystem            Size    Used  Avail  Use% Mounted on
/dev/sda1             445G   42G  380G  10%        /

As i understand...
- download 14.04 LTS image and burn on a DVD.
- boot live/install DVD
- With the program Gparted :
1 - shrink sda1 to 50 GiB
2 - Make a data partition 250 GiB
3 - Make several partitions 10 GiB (one on a time)
4 - Install 14.04 on one of the new partitions
5 - Later i can install other flavours on the remaining new partitions
6 - Grub menu is updated automaticaly by the install procedure at every new install ???
7- Later i can put a new flavour over the current 10.10 Maverick

Is this right ?

---

### Post by oldfred on 2014-12-14
I think 10GB is a little small unless you want to install and test for just a bit  and then erase. I use 11GB but 2GB  of that 11 is .wine for Picasa. My / partition is usually 25GB.

I like to keep extra room, so if moving some of the 42GB into your data partition the 50GB should be ok, otherwise that is a bit tight.

You have to keep track of Which grub is in charge and last installed version will normally be the one you use to boot. But better to have one main working install and keep it as the grub you use to boot with.

---

### Post by mastablasta on 2014-12-15
it would be better to just jump in install 14.04. of you need 10.10 you can install in virtualbox.

otherwise create home partition and then install 10.10 into new root partition.

---

### Post by Dennis N on 2014-12-15
> **Edho said:**
> Thanks all for the tips.

df -h command give this 

Filesystem            Size    Used  Avail  Use% Mounted on
/dev/sda1             445G   42G  380G  10%        /

As i understand...
- download 14.04 LTS image and burn on a DVD.
- boot live/install DVD
- With the program Gparted :
1 - shrink sda1 to 50 GiB
2 - Make a data partition 250 GiB
3 - Make several partitions 10 GiB (one on a time)
4 - Install 14.04 on one of the new partitions
5 - Later i can install other flavours on the remaining new partitions
6 - Grub menu is updated automaticaly by the install procedure at every new install ???
7- Later i can put a new flavour over the current 10.10 Maverick

Is this right ?

In the plan you need to create the extended partition which will be used to contain an indefinite number of logical partitions. Remember that you can have at most 4 primary partitions, one of which will be used as that extended partition. You can create more logical partitions out of the exended partition's unallocated space as needed.  Need a swap partition - can be in the extended partition.

One of those logical partitons (or it could be one of your available primary partitions) can be for data shared by all the OSes you have installed (a good idea - a shared music library, for example). The other logical partitions would be for other OS installs.

Installing each additional OS installs grub and you end up booting into grub menu created the last one (but that can be avoided by using a custom menu which you can get into at some future time, or use gm's method. I like custom menus.)

Maverick can be replaced later.

---

### Post by Edho on 2014-12-16
I failed in installing Linux Mint and Ubuntu 14.04.
Crashed in Live CD boot or Live Cd install.

Looks like Ubuntu Mate works (live cd)
Tomorow i will try an install.

For testing other flavours it's maybe better using of live USB sticks.

Thanks all for the advice.

Thread closing please.

---

