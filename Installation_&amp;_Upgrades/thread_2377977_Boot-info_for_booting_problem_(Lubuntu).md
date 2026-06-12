---
title: "Boot-info for booting problem (Lubuntu)"
date: 2017-11-18
forum: Installation &amp; Upgrades
---

### Post by minefox on 2017-11-18
[http://paste.ubuntu.com/25989660/](http://paste.ubuntu.com/25989660/)

I've tried to install Lubuntu onto a USB flash drive, and then onto another USB drive.
The one with the installer on it is 16GB, and the one I'm trying to install to is 32GB. I was also going to add a swap of 16GB with a third usb drive but that's irrelevant.

So, when I tried to install onto the 32GB drive, all was going well until it said that the grub boot loader (I don't quite remember what it was exactly) but then the installer crashed and I couldn't do anything else. I've tried it 3 times, and I don't know what the problem is.

I'm installing Lubuntu 17.04.
I know the newest version is 17.10 but I thought maybe I could just select the install updates button in the installer.

If that's the problem, I'll just download the 17.10 update and use unetbootin again. It just takes a while to install so I figured if I can do something and maybe learn something in the process then I might as well just fix it rather than install it again.

Thanks in advance!

---

### Post by minefox on 2017-11-18
I forgot to say that I got lubuntu onto the 16GB USB with unetbootin, but I'm sure that was figured out by the end.

---

### Post by oldfred on 2017-11-18
Do not run Boot-Repair's auto fix. That just installs one grub to the MBR of all drives. You do want to use Boot-Repair's advanced mode, choose install in sdd5 and install boot loader to MBR of sdd.
Do pay attention to drive order. When you reboot the 32GB drive may not be sdd, depending on whether you have other flash drives plugged in or not. 

I do prefer to install current LTS version or now 16.04 as main working install and have it on several flash drives.  
And only install the in between versions to test or experiment with settings. Note 17.04 expires in Jan 2018.
If you have 4GB of RAM, you may not need swap at all. On my 4GB system I (almost) never used swap. But I only loaded a few apps or tabs in Firefox at one time. My old laptop only had 1.5GB and I learned not to open more than one larger app and a couple of smaller apps, or else it would go to swap and get real slow. So that became mainly how I use system. 
Also with 17.04 or later, it uses a swap file by default, but will use a swap partition if found. So best not to use swap partition, use the space for larger / (root) or more data.

With multiple drive installs, you must partition in advance and use Something Else or partition during install. I find it slightly easier to use gparted to partition, but that is more my choice. And then you must choose in the combo box at the bottom to install boot loader (grub) into MBR of same drive you are installing into.
And with a somewhat smaller flash drive of 32GB, best to only use / (and maybe swap). Most desktops do not need /boot, only the full drive LVM with encryption uses a /boot partition by default. And you do not need the other partitions. Issue when on smaller drive is managing use of each partition and amount of remaining space. If all system folders are in one larger partition remaining space is shared.

You have Windows in BIOS boot mode, so that drive can only be MBR(msdos). Bit more advanced is the newer gpt partitioning. That is the standard partitioning used with all new UEFI based systems. Mac since converted to Intel chips & Windows since Windows 8 about 5 years ago.
Ubuntu has been able to boot in BIOS or UEFI mode from gpt since at least 2010 as I converted one drive to gpt back then to boot my BIOS only system. And about 5 years ago I started partitioning all drives including my flash drives with gpt and both the required extra partitions required for UEFI and/or BIOS boot.

My full install (is UEFI & gpt, but has bios_grub in case I want to easily convert back to BIOS boot).
```
Disk /dev/sdc: 31.6GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  536MB   535MB   fat32        USB_ESP    boot, esp
 4      536MB   538MB   2097kB               bios_grub  bios_grub
 2      538MB   15.2GB  14.7GB  ext4         root
 3      15.2GB  31.6GB  16.4GB  ext4         usb_data

```

---

### Post by minefox on 2017-11-18
Thanks for all the info!

The reason I wanted to add a lot of swap is because I would like to use Blender (3d modeling software). But, the more RAM you have the smoother and faster it goes. And it'll be able to load files and do processes faster.
I'm going to try to use the 17.10 in case the problem was just the iso was corrupted or something. 

But still, thanks for all the help. This computer is currently windows 7 for all kinds of programs, but I would like to have a USB I can plug in to any 64-bit PC and use my own stuff without interrupting the original hard drive. I've done it before with I think 16.04 or 15.10 and it worked flawlessly. :D I don't know if you know or not, but there's a distro called Tails that I used once but it's super super high security. That's pretty much what I was going for, but with persistence. just plug in, boot, use, shutdown & unplug.

---

