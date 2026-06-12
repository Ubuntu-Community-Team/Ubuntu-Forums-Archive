---
title: "Change current dual boot partitions or fresh reinstall Lubuntu with Windows VM?"
date: 2023-06-22
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2023-06-22
[SIZE=2]Hello all,[/SIZE][SIZE=2] 

My old laptop PC is functional, but in need of repair (2 keys on the keyboard no longer work & it has only 4GB of RAM). Fortunately I was given a "new" (for me) 5 year old PC by a relative.  I am presently dual booting Windows 10 and Lubuntu 22.04 LTS on the "new" (for me) PC. I installed the Lubuntu during a USB Lubuntu liveboot next to the "native" Windows 10. And I sized the respective partitions (using the Lubuntu installer at the beginning of the installation process). I have about a 150GB partition for Windows 10 and about 330 GB partition for Lubuntu. The hard drive is 500GB total capacity. **See the attached screenshot below showing the partitions in the KDE Partition Manager **[/SIZE]**[SIZE=2](that c[/SIZE]****[SIZE=2]ame[/SIZE]****[SIZE=2] with Lubuntu)[/SIZE]**[SIZE=2]. I have 8GB of RAM; I hope to add another 8GB of RAM (for a total of 16GB of RAM) in the next few weeks. 

It's been about 7-10 days since I installed the Lubuntu and I pretty much have gotten it the point where I want to use the "new" (for me) PC instead of the old PC laptop (that needs repair). I want to [/SIZE][SIZE=2]experiment [/SIZE][SIZE=2]for a period of time [/SIZE][SIZE=2]by [/SIZE][SIZE=2]add[/SIZE][SIZE=2]ing[/SIZE][SIZE=2] Windows 10 as a Virtual Machine with Lubuntu as the host. [/SIZE][SIZE=2]I may also increase the size of the Lubuntu partition and decrease the size of the Windows partition by a corresponding amount. A[/SIZE][SIZE=2]nd if th[/SIZE][SIZE=2]e experimentation[/SIZE][SIZE=2] seems to work well, I will likely [/SIZE][SIZE=2]pursue one of two courses of action. [/SIZE][SIZE=2]_**First course:**_[/SIZE][SIZE=2] increase the Lubuntu partition to it's maximum size and delete the Windows partition. [/SIZE]**[SIZE=2]I tentatively plan to resize partitions using the Lubuntu KDE Partition Manager. [/SIZE]****[SIZE=2]_Second course:_[/SIZE]**[SIZE=2] do a fresh install of Lubuntu and eliminate Windows 10 (either before or during the Lubuntu install).

I am not sure [/SIZE][SIZE=2]which of these two courses is the best/wisest -- I am concerned that resizing or deleting partitions could be problematic. Perhaps there also is another approach I should consider.[/SIZE][SIZE=2] 

**QUESTION(S):** [/SIZE][SIZE=2]Should I [/SIZE][SIZE=2]eventually: [/SIZE][SIZE=2]**1)**[/SIZE][SIZE=2] do the first course: change current dual boot partitions or [/SIZE][SIZE=2]**2) **[/SIZE][SIZE=2]do the second course: do a [/SIZE][SIZE=2]fresh reinstall Lubuntu with elimination of  Windows on the hard drive with the addition of Windows as a VM?[/SIZE]

 [SIZE=2]Or is there another course of action I should consider?[/SIZE]
 
 [SIZE=2]As always, thank you,[/SIZE]
 
 [SIZE=2]A.[/SIZE]
  
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292410&stc=1[/IMG]

---

### Post by yancek on 2023-06-22
If you intend to keep windows, it is best to shrink the windows partition from the windows Disk Management tool and after that reboot and run chkdsk.
To resize Lubuntu, you need the install usb as you cannot resize a Linux partition while it is mounted.
As far as which method to use, deleting windows or not is a personal choice.  I still have windows on the laptop I use although I boot it maybe twice a year.

---

### Post by TheFu on 2023-06-22
Can't answer, since what you intend to do with each OS isn't laid out nor is the hardware listed.  Use **inxi -bz** to provide an overview of the hardware on the system.  If the passmarks are over 4000, I wouldn't worry about running a VM for Win10 using 3GB of RAM for it.  I'd probably allocate 40-65G of storage for Windows, if it is used for just a few things, like taxes and accounting.  

16GB is fine, but so is 8GB. RAM is the easiest thing to change in a VM. No reinstall needed.

If the system doesn't have an SSD for the boot, I'd look at replacing that before adding more RAM. It will likely matter more for speed. I saw a 1TB Samsung 980 NVMe SSD for US$45 and a 1TB Samsung 870 2.5in SATA SSD for $50 yesterday.  Both had free shipping.  Don't know the conversion to AUD or availability there.  Quality SSDs are getting cheap.  I paid $70 for a 980 a month ago, so I'm a little unhappy.

Use the current HDD for backups, if you don't already have a backup solution.

If you don't plan on video editing in MS-Windows, then I'd definitely move to a VM.  You'll need to deal with the license key. I don't know how to handle that, since my newest MS-Windows is win7 still and they used keys, not something embedded into the laptop BIOS.

I'd also use LVM for disk management, not straight partitions.  Regardless, I'd never allocate the / partition to be over 35G in size. I'd setup /home, /var to be separate. Doesn't matter if this is partitions or LVM LVs.  Keeping the OS and data separate is an important idea worth following, unless this entire system is just a toy/play system. Then do whatever you like.

Of course, only you know your situation.

---

### Post by MAFoElffen on 2023-06-22
+1 -- (To TheFu's recommendation)

The question is very open ended and wide-scoped. I do Multi-Boot and have for a decade and a half. Though I wonder lately why. About the only reason I boot Windows anymore, is to apply updates.

I used to keep Windows there so I could support my Windows Customers and for Gaming on native hardware. I don't have time to Game much these days. (Dang.)

My daily driver is still Ubuntu Linux, or Ubuntu Linux based.

---

### Post by AbleTassie on 2023-06-22
> **yancek said:**
>   ... To resize Lubuntu, you need the install usb as you cannot resize a Linux partition while it is mounted.

Thanks Yancek, just to clarify: to resize the Lubuntu partition on the hard drive, I would need to do a liveboot using a usb and then use a tool like the Lubuntu KDE partition manager on the liveboot usb to resize the Lubuntu hard drive partition, correct?

> **TheFu said:**
> Can't answer, since what you intend to do with each OS isn't laid out nor is the hardware listed.  Use **inxi -bz** to provide an overview of the hardware on the system.  If the passmarks are over 4000, I wouldn't worry about running a VM for Win10 using 3GB of RAM for it.  I'd probably allocate 40-65G of storage for Windows, if it is used for just a few things, like taxes and accounting.   Thanks Fu, the 500 GB hard drive is an SSD; here is hardware info: **Output from inxi - bz terminal command:**
System:
   Kernel: 5.19.0-45-generic x86_64 bits: 64 Desktop: LXQt 0.17.1
     Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
 Machine:
   Type: Laptop System: ASUSTeK product: X556UQ v: 1.0
     serial: <superuser required>
   Mobo: ASUSTeK model: X556UQ v: 1.0 serial: <superuser required>
     UEFI: American Megatrends v: X556UQ.316 date: 04/16/2019
 Battery:
   ID-1: BAT0 charge: 19.9 Wh (98.5%) condition: 20.2/38.0 Wh (53.1%)
     volts: 7.6 min: 7.6
CPU:
Info: dual core Intel Core i7-6500U [MT MCP] speed (MHz): avg: 2466
min/max: 400/3100
Graphics:
Device-1: Intel Skylake GT2 [HD Graphics 520] driver: i915 v: kernel
Device-2: NVIDIA GM108M [GeForce 940MX] driver: nouveau v: kernel
Device-3: Chicony USB2.0 VGA UVC WebCam type: USB driver: uvcvideo
Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080~60Hz
OpenGL: renderer: Mesa Intel HD Graphics 520 (SKL GT2)
v: 4.6 Mesa 22.2.5-0ubuntu0.1~22.04.3
Network:
Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
driver: r8169
Device-2: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
driver: ath10k_pci
Drives:
Local Storage: total: 476.94 GiB used: 20.1 GiB (4.2%)
Info:
   Processes: 204 Uptime: 16m Memory: 7.62 GiB used: 2.36 GiB (30.9%)
   Shell: Bash inxi: 3.3.13

As always, thanks for the advice Fu, MAFoElfeen and Yancek.[B] 

Any more comments or advice from the three of you (Yancek, Fu or MAFoElfeen) or anybody else will be welcomed. [/B]                               

Thanks,

A.

---

### Post by grahammechanical on 2023-06-22
Using a partition manger can be scary. Especially when you first see the warnings about loss of data. I have resized/moved/deleted/created partitions many time over the years. No failures so far. When resizing partitions it is good not to be too confident. Double check your decisions.

The partition manager will let you queue several actions to be run one after the other. This will often take many minutes. Which can be nerve racking. I prefer to complete one action at a time. I am less nervous doing that.

As stated above, use Windows tools to alter Windows partitions and defrag before and after.

Regards

---

### Post by guiverc on 2023-06-22
My *primary* PC died late last year (a 2009 dell) & I finally got a new box to replace it earlier this year (*a second hand/refurbished 2017 dell*). Whilst at the *swap meet* I also purchased a number of other *newer* (*second hand*) boxes too.

My *new *primary PC came with windows 11, the other 4 came with w10, all were resized using Lubuntu installs (*they each now have a non-LTS & LTS installed in dual boot now along with original windows; resizing being done by `calamares` installer but it's the equivalent of booting a 'live' system & using KDE Partition Manager to resize what I assume was NTFS windows partitions*), with 4 of the 5 booting windows exactly as expected afterwards..  Alas one doesn't boot windows anymore :o, which was no loss for me (*except I couldn't PASS the QA-test!*) thus maybe emphasizing the warning already provided that its best to use windows tools to resize windows partitions already mentioned by @yancek & others...  FYI:   No data on the partition was lost; the few files I added for validation purposes were all there untouched, but windows failed to boot on 1 of the 5 boxes & needed fixing.


Myself, if I needed to resize a partition, I may actually boot a non-Lubuntu/Kubuntu/Ubuntu-Studio ISO (ie. Ubuntu Desktop, Xubuntu, Ubuntu-MATE etc) & use `gparted`.  The main reason I'll do that is I'm more familiar with `gparted` then KDE Partition Manager and thus have a *higher confidence* I'll not make a *mess* with it (I QA-test with KDE Partition Manager for sure, but I've had a higher failure rate with it on some older boxes than `gparted` too).  If I only had a Lubuntu thumb-drive handy; I'd just use that; but may `apt install gparted` & use that on Lubuntu over KDE Partition Manager. In 99% of cases KDE Partition Manager & Gparted are equal; but for maybe 1% I've had more success with gparted.

---

### Post by AbleTassie on 2023-06-24
> **TheFu said:**
> 
I'd also use LVM for disk management, not straight partitions.  Regardless, I'd never allocate the / partition to be over 35G in size. I'd setup /home, /var to be separate. Doesn't matter if this is partitions or LVM LVs.  Keeping the OS and data separate is an important idea worth following, unless this entire system is just a toy/play system. Then do whatever you like. Of course, only you know your situation.

Hi Fu and others,

Thanks for bringing LVM disk management to my attention. I was not aware of it. And I have spent some time studying it and it certainly appears to be a very powerful tool compared to storing data on partitions that are limited to a physical device. Here are some of the things I have studied on LVM disk management: [U]
An Introduction to LVM Concepts, Terminology, and Operations[/U] at [URL="https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations"]
https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations[/URL]  and 
[U]
How To Use LVM To Manage Storage Devices on Ubuntu 18.04[/U] at 
[https://www.digitalocean.com/community/tutorials/how-to-use-lvm-to-manage-storage-devices-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-use-lvm-to-manage-storage-devices-on-ubuntu-18-04) and
 
_Lvm (Ubuntu Wiki)_ at [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)  

There are also youtube videos. _**Any other suggestions of sources of instruction for a beginner (**__**who just wants to use LVM on a simple laptop, not a server**_[U][B]) would be appreciated.

[/B][/U]QUESTION: I am thinking that since LVM can be modified on the fly, I may be able to set up my LVM with my current Lubuntu/Windows 10 dual boot, rather than wipe out the Lubuntu and Windows >  then set up my LVM >  then install Lubuntu and Windows. Is this correct?

If this is correct, do you (or others) have any suggestions as to how to do this without screwing up my present dual boot?

Thanks again,

A.

---

### Post by TheFu on 2023-06-24
> **AbleTassie said:**
>  
[/B][/U]QUESTION: I am thinking that since LVM can be modified on the fly, I may be able to set up my LVM with my current Lubuntu/Windows 10 dual boot, rather than wipe out the Lubuntu and Windows >  then set up my LVM >  then install Lubuntu and Windows. Is this correct?

If this is correct, do you (or others) have any suggestions as to how to do this without screwing up my present dual boot?
 

I don't dual boot and haven't in over a decade.  I put MS-Windows into a VM.

I think laptops need to be encrypted. All portable devices do and doing encryption for multiple booting OSes is just too much hassle for me.  So, on a laptop, I simply check the "Encrypt + LVM" checkbox and let the installer do its thing (wiping the storage completely is step 1).  

Post-install, I boot from the live-boot-installer, mount the LUKS partition, then **lvreduce** the "root" LV, add a "home" LV, add a "var" LV and mount those where needed, carefully moving over any files that were placed on /var and /home during the install.  I'll delete the "swap" LV and create a new "swap01" LV of the size I want (always 4.1GB for non-servers), and finally, I'll fix the fstab for the installed area to mount these LVs using /dev/{vgname}/{lvname} links.

Here's the last **df -Th** output from the last time I booted the laptop with all the junk removed (loop and fake storage items). It has been over a year now.
```
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root       25G   19G  4.3G  82% /
/dev/sda2                              721M  261M  424M  39% /boot
/dev/sda1                              511M  4.5M  507M   1% /boot/efi
/dev/mapper/ubuntu--vg-stuff      99G   65G   30G  69% /stuff
/dev/mapper/ubuntu--vg-home--lv   74G   23G   48G  33% /home 

```
That storage on the laptop was setup in 2018, so I've changed how I do it. As part of my backups, I capture some storage information. Back then, I'd dump **lvdisplay** to a file. The **egrep 'LV Path|LV Size' lvdisplay.txt** important things:
```
  LV Path                /dev/ubuntu-vg/root
  LV Size                25.00 GiB
  LV Path                /dev/ubuntu-vg/swap_1
  LV Size                <4.46 GiB
  LV Path                /dev/ubuntu-vg/home-lv
  LV Size                75.00 GiB
  LV Path                /dev/ubuntu-vg/stuff
  LV Size                100.00 GiB
```
The storage in that system is a 500G SATA SSD. As you can see, I've allocated less than 50% and I'm using about 50% of that.  "stuff" is an area that doesn't get backed up. It is for temporary workspace.  For me, a laptop is never a trusted system. It can be wiped without any real data loss expected.  Important data is kept elsewhere, unless it is being actively worked.

**lvreduce** is a hassle and dangerous, so it is best handled immediately after install when the risks for data loss are smallest.  I think I have a diagram showing this ... see attached.
Hope this helps.

As for MS-Windows, run that in a virtual machine. I run it on a VM on a Ryzen system not on a laptop.  Remote access using SPICE into the Windows VM is easy to setup.  SPICE makes remote access nearly as fast as local access and only works for KVM-based VMs.  Most of the time, I'll use an LV for the storage of each VM, but I don't do that with MS-Windows.  My Windows VM is from 2008-ish, so migrating it from file-based storage has some risks.  OTOH, I've migrated it from system to system 3+ times and not needed to 'reactivate' it thanks to KVM virtualization.  

With Linux, the migration between systems is nearly risk free, assuming you have good backups. No license validation needed or license tracking for paid software.  That is very freeing.

Anyway, I don't have the best advice for someone who feels dual booting is a good idea.

---

### Post by TheFu on 2023-06-24
The good news is that LVM is LVM regardless of distro.  The core commands used are the same to create, resize, move, change across all distros for at least the last 20 yrs. A few options have been added, like for LVM-RAID, but most people wouldn't use that.

In a single disk setup, LVM is pretty simple.

---

### Post by Dennis N on 2023-06-24
> QUESTION: I am thinking that since LVM can be modified on the fly, I may be able to set up my LVM with my current Lubuntu/Windows 10 dual boot, rather than wipe out the Lubuntu and Windows > then set up my LVM > then install Lubuntu and Windows. Is this correct?

If this is correct, do you (or others) have any suggestions as to how to do this without screwing up my present dual boot?

I don't think you can convert your existing Lubuntu with standard install on a partition to an LVM installation, if that's what you are thinking. (If so, I would be interested in learning that process).

You can add a partition for LVM use to your existing disk, space permitting. That's how I began learning LVM - just one partition for experimenting with an LVM installation and the LVM commands. The existing installs are not disturbed, and all can be in a multiboot setup.

---

### Post by TheFu on 2023-06-24
There is no migration of already installed OS on partitions to LVM method.  A fresh install is needed.  However, many backup/restore processes are storage agnostic, so if your backup/restore process isn't tied to the actual storage used, then switching should be possible in less than 1 hour.

For unencrypted OS installs, I prefer to setup my LVM layouts using a script between the ISO boot and storage "Do Something Else" options. Basically, I switch to a different tty and use scp to pull the script to the machine being installed and manually use CLI tools to partition, create a PV, VG, then the LVs that I want, add some labels to help keep the purpose known in my mind, and finally toggle back to the installer and "Do Something Else" ... where I connect each partition and LV to the specific storage for the system. Then the installer goes and finishes.  [Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144) is a reference. Just forget the LUKS encryption aspects.  I find the 20 lines in my script that I manually tweak are easier than all the nasty point-n-click the installer requires to do anything with LVM.  Just connecting pre-existing LVs is a hassle, but only needed once as part of the install process.  It is nice to have these things setup and used by the installer, so I don't need to go back, resize LVs, create some others, and mount them as I really desire.  Finally, having to move data from the installed locations (/var and /home) in to the new LVs is a bit of a hassle.  By setting up the LVs before installation, I avoid that.

Also, if you have existing UEFI partitions, then you don't need to create or touch those. They should be recognized by the installer. However, they may need to be resized/moved.  YMMV.  Ubuntu seems to think we need 500MB for UEFI.  I don't know why.  
On a 22.04 system default ZFS install, they allocated 512MB, but it is only using **17MB**.
On a 20.04 system where I controlled everything, I allocated 50MB, but it is only using **6.1MB**.  Across all my UEFI using systems, I've never needed even 50MB for that partition.

---

### Post by AbleTassie on 2023-06-29
> **TheFu said:**
> The good news is that LVM is LVM regardless of distro.  The core commands used are the same to create, resize, move, change across all distros for at least the last 20 yrs. A few options have been added, like for LVM-RAID, but most people wouldn't use that.

In a single disk setup, LVM is pretty simple.

Thank you for your comments as always Fu. I hope to eventually start using LVM after some study so I know what I am doing. Just one more question for you or others. It seems to me that a GUI for LVM would be helpful for beginners. I have found a December 2020 article on GUIs for LVM that can be used for the Linux OSs, _How To Use GUI LVM Tools_ by Ares Lee in the Linux Journal see [link]("https://www.linuxjournal.com/content/review-gui-lvm-tools"). I have copied & pasted a table from the article that compares and contrasts such GUIs for LVM. It is underneath my username below.

QUESTION: Can you recommend a GUI program for LVM that can be used with Ubuntu that is free? 

Thanks again,

Able

Table from article _How To Use GUI LVM Tools_ :


[TABLE]
[TR]
[TD]**Features**[/TD]
[TD]             **LVM GUI**[/TD]
[TD]             **Blivet-gui**[/TD]
[TD]             **GParted**[/TD]
[TD]             **YaST Partitioner**[/TD]
[TD]             **KVPM**[/TD]
[TD]             **Visual LVM**[/TD]
[/TR]
[TR]
[TD]             **Platform**[/TD]
[TD]             rhel/centos *[/TD]
[TD]             centos 7+ *[/TD]
[TD]             *****[/TD]
[TD]             opensuse[/TD]
[TD]             *****[/TD]
[TD]             *****[/TD]
[/TR]
[TR]
[TD]             **Disk Operations**[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[/TR]
[TR]
[TD]             **Create PV**[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Resize PV**[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Delete PV**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Modify PV Settings**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Migrate PV**[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[/TR]
[TR]
[TD]             **Create VG**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Delete VG**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Append/Reduce PV**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Config w/ create VG**[/TD]
[TD]             yes[/TD]
[TD]             PE Size only[/TD]
[TD]             no[/TD]
[TD]             PE Size only[/TD]
[TD]             PE Size only[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Rename VG**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Modify VG Settings**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Backup/Restore VG**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Create LV****[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Resize LV**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Delete LV**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Rename LV**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Modify LV Settings**[/TD]
[TD]             no[/TD]
[TD]             no but has menuitem[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             Some[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Format LV**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[/TR]
[TR]
[TD][/TD]
[/TR]
[TR]
[TD]             * means support multiple platforms[/TD]
[/TR]
[TR]
[TD]             ** the supported logical volume type :[/TD]
[/TR]
[/TABLE]

[B]Supported Volume Type
[/B]
[TABLE]
[TR]
[TD][/TD]
[TD]             **LVM GUI**[/TD]
[TD]             **Blivet-gui**[/TD]
[TD]             **GParted**[/TD]
[TD]             **YaST Partitioner**[/TD]
[TD]             **KVPM**[/TD]
[TD]             **Visual LVM**[/TD]
[/TR]
[TR]
[TD]             **Simple/Linear**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Stripe/RAID0**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Mirror/RAID1**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **StripeMirror/RAID10**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **RAID4**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **RAID5**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **RAID6**[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[/TR]
[TR]
[TD]             **Snapshot**[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[/TR]
[TR]
[TD]             **Pool**[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[TD]             yes[/TD]
[TD]             yes[/TD]
[TD]             no[/TD]
[/TR]
[TR]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by TheFu on 2023-06-29
I've never used any GUI with LVM.  Most of my systems don't have any GUI at all.  
LVM on Linux works the same as LVM on Unix. The big ideas are all the same.  So, if you've ever used VeritasVM/FS, then their isn't much of a learning curve.

The real key to understanding LVM is that everything pivots around the VG, Volume Group.  PVs  can be added to a VG.  LVs are pulled from an LV and depending on the number of PVs and the amount of free storage in each will determine whether you can have striped, RAIDx or concatenated LVs.  Basically, with 3 different types of objects, LVM is extremely flexible.  OTOH, just because something CAN be done, that doesn't make it a good idea.  For example, I don't have LVs that cross multiple disks unless they are RAID1. That's because I was burned doing that about 20 yrs ago. I'd merged 3 disks (PVs) into a single VG and kept expanding the LV.  Then 1 of those disks failed and all the data on all three disks became unavailable. I probably have those 3 disks on a shelf somewhere. Maybe the data can be restored with 20 yrs more knowledge, but at the time I didn't have that ability.

---

### Post by AbleTassie on 2023-06-30
I have a basic understanding of LVM and it certainly seems pretty simple and like a powerful tool and approach as opposed to the: "conventional" approach of physical volumes (devices) with essentially physical partitions within the physical devices, and (I think) what amounts to logical volumes within separate partitions. And I appreciate Fu's caution about being careful about (or not) using LVs across multiple physical volumes or disks.

For a beginner, I think that use of a GUI with LVM might be helpful and prevent mistakes early on. I think it will take a while longer, playing around and experimenting for me to get comfortable with LVM. 

The responses here have helped me think about the best approach the situation prompting my original query: **Change current dual boot partitions or fresh reinstall Lubuntu with Windows VM? **I am starting to think more about Backup of my Home folder and some of the other suggestions early on in the thread as important to do.

So thanks to everybody for their posts, answers and replies: I think you have informed me further about my situation. I am going to mark this thread as SOLVED.

Thank you,

Able

---

### Post by TheFu on 2023-06-30
LVM can do so many things that are nearly impossible for any GUI to capture in a useful way.  A GUI would just handle the most trivial 20% LVM setups, which hardly makes having the GUI useful.

As you learn more about LVM, you'll come to understand better.

---

