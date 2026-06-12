---
title: "Dualboot Vista (on RevoDrive) + Ubuntu (on SSD)"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by XSaenen on 2011-11-24
Hi all. 
 
First post here. I'm familiar with forums, but not with Ubuntu. I tried to search for an answer, but found nothing that applied to my situation.
 
I have been playing with Ubuntu in Virtualbox, but would like to test it outside of VB's limited environment. Hence my intention to dualboot it.
The PC is currently running Vista Ultimate 64 (I'm not a fan of Win7) on an OCZ RevoDrive X2. I plan on putting Ubuntu on a separate 64GB SSD.
 
However I have some major concerns : 
1 ) my search revealed that a Windows install in RAID 0 can get into problems when you try to dualboot Linux, even on a separate HDD. Seeing as the RevoDrive is basically a PCI HDD that consists of 4 SSDs in an internal RAID 0, I'm slightly worried. It's bad enough to go through an entire wipe + reinstall if it goes wrong, but because the drive uses an internal RAID arrangement, I'm slightly worried about messing that up and basically killing the drive. These things don't come cheap, so I don't want to take any unneccessary risks. 
2 ) Before installing Vista, I had to download drivers from the OCZ site to enable the Revodrive as a boot drive. These drivers are only available for Windows because the drive won't appear during the installer's HDD selection, so I'm worried that it might not work with a bootloader. I couldn't care less if the Revodrive is accessible in Ubuntu or not, just as long as it works when I want to run Vista. My job requires me to run Windows on my PC, otherwise I would have pulled out the Windows drive for a week and gone for an all-out Ubuntu install
3 ) I tried to dualboot my last PC (XP + Vista), and found many of the guides to contradict eachother. I made several attempts using the different guides, and the results varied between not finding any disks and bluescreening. I'm already finding contradictions in some Ubuntu dualboot guides (all with Vista installed first), so I'm getting nervous already.
 
I'm pretty good at setting up XP, Vista and Win7 and am usually the one that gets to solve everyone else's mess, but I'm not comfortable with command line stuff and am certainly not familiar with coding. 
As a result I don't think I can call myself an experienced user. I'm more of a regular user who understands windows' UI better than the average person does. Put me out of that Windows environment and I know very little.
 
So ... Has anyone got any experience with setting up dualboot on PCs with a RevoDrive? If so, a detailed guide for complete noobs would be appreciated. 
 
-----
 
Full PC specs, for those interested or in case it makes a difference :
 
MoBo : Gigabyte GA P67A-UD3P B3
CPU : Intel Core i5 2500 (@ stock 3.3 GHz)
RAM : 16GB GEiL DDR3-1333 CL7 (4 x 4GB)
GFX card : AI Radeon HD4870x2 (@ stock speed)
 
Vista system HDD : OCZ Revodrive X2 240GB
Unused HDD (intended for Ubuntu) : OCZ Vertex 2 60GB
Data HDD : Seagate Barracuda 1TB 7200RPM
Media HDD : Samsung HD204UI 2TB 5400RPM
DVD 1 : Sony Optiarc AD-5260S
DVD 2 : Sony Optiarc AD-7261S Lightscribe
 
Case : Cooler Master HAF X (with all optional case fans installed)
CPU cooler : Cooler Master V8
Fan controller : Laptron FC5 v2
PSU : BeQuiet! Dark Power Pro 850W
Keyboard : Logitech DiNovo Edge + Logitech N305 numerical pad
Mouse : Logitech M570 Trackman
Cam : Logitech LifeCam HD-6000
Monitors : 2x Samsung Syncmaster 2333sw (23"), for a total 3840x1080 resolution

---

### Post by WasMeHere on 2011-11-24
Welcome to the Ubuntu Forums, XSaenen

I run three dual boots Ubuntu + XP and I have set up Linux Mint + Vista for my daughter. But I have no experience of RevoDrive (or any RAID).

1. **Boot from a persistent live drive**

This system is normally meant for booting several computers from the same USB drive. The persistence is obtained with a special casper read-write file with a file-system inside where to write settings and personal files. It is like carrying your computer environment from one computer to another. This could be done using your SSD, and it should not interfere with your other system. You should test it with a USB stick before installing it to the SSD.

2. **Regular dual-boot**

I think it could be safe to disconnect the RevoDrive and install Ubuntu to your SSD. ***But I give neither promise nor guarantee***. Make sure to take notes of any changes to the BIOS setting, so that you can restore them afterwards!

Then connect your RevoDrive again and see what happens! Try to set the bios to boot from Ubuntu if it doesn't already do that. And then run ```
sudo update-grub
``` from a terminal window. After reboot you might have a dual-boot system.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by oldfred on 2011-11-24
I think Olle Wiklund's suggestion of disconnecting drive is the best in your case. You do want to be extremely careful where grub2's boot loader gets installed. It likes to default to sda which may be the RevoDrive and create issues. 

I prefer to manually format in advance and then use manual install. With manual install you do get a choice (combo box) on which drive (and it really should not give partitions) to install the grub2 boot loader into. I have clicked thru to fast and installed grub to the wrong drive but for me it was no big deal, I just reinstalled to the correct drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

If only using Linux on the SSD, you may want to consider the new gpt partitioning scheme.

[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)

Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)


I recently purchased a 60GB Microcenter SSD and just installed two versions of Ubuntu into two / partitions. I used gpt and created a bios_grub partition. Does you  new system use UEFI?

---

### Post by XSaenen on 2011-11-24
Fred,
 
I just looked it up, and it seems Gigabyte still uses their Legacy BIOS.  So no UEFI.
 
It looks like the best option would be to unplug every HDD except the SSD then.  That way Ubuntu and GRUB can only go there.  
I'm doing a full backup of everything that's on my HDDs, and once it's done I'll open this thread on my laptop and give it a go.  
 
Thanks in advance

---

### Post by darkod on 2011-11-24
You are correct to search for information in advance, not when problems show up. But don't get too spooked up. Don't forget, forums are for the "problems", and not for hearing about the millions of success stories. :)

You can disconnect the Revo to be on the safe side, but since you already said there are no drivers for linux and it seems it will not even be detected by the ubuntu installer, that's the same as not being there right?
On the other hand the installer might detect it even without special drivers, just because windows needs them it doesn't mean linux does too.

In any case, linux is very good in situations with multiple drives and as long as you pay attention and know partitioning your disks, you should be OK. Linux also offers you to choose where to install the bootloader which helps a lot with multiple disks, and is not something you get with windows which only tries to guess where to put the bootloader according to the system setup.

---

### Post by XSaenen on 2011-11-24
Well ...
 
I installed Ubuntu 11.10 without any problem, but haven't tried the multiboot yet. I might have to revert to an older version before I'll attempt that.
 
11.10 keeps failing to install the drivers for my GFX card. As a result it'll only allow a 1920x1920 resolution at max, whereas I want my usual 3840x1080
 
There also seems to be a bug with the keyboard. If I use a generic corded keyboard in my usual layout (we use azerty here in Belgium) , there are no problems. However my DiNovo appears to work as azerty when typing in LibreOffice, but when trying to log in or when using the search box, Ubuntu somehow thinks it's a qwerty. 
The control panel only shows the "Belgian" layout.
 
I still have that 10.04 .iso which I used in my Virtualbox, and that seems to have neither of these issues. So I'll give that a go instead. I prefer to have a stable platform before I start messing around with dualboot.

---

### Post by XSaenen on 2011-11-24
Right ... exactly what I feared.
 
I got 10.04 running just fine after a bit of tweaking, then re-installed the HDDs and the Revodrive. 
Upon boot, all drives were shown in the BIOS, including the Revo.
 
Booted to linux and ran the sudo update-grub in terminal. It showed :
 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
done
 
Upon reboot it still showed all the drives in BIOS ... and went straight into Ubuntu again. It looks to me as if GRUB2 is unable to identify the RevoDrive as a HDD that contains an OS, and therefore boots straight into the only one it sees. The Revo isn't shown in Ubuntu either, unlike the other HDDs.
 
Sorry for double-posting, by the way.
 
-----
 
EDIT : The good news is that I can use F12 to boot to Vista. Seeing as that'll still be my primary OS, I'll probably edit the BIOS options to default to Vista. 
Vista doesn't see the disc that contains Ubuntu and vice versa, but both of them see my other disks. Whilst not being exactly what I wanted, it's a good start and does result in me running 2 OS'ses (or whatever the plural of an OS is) on one PC.
 
If anyone has any suggestions on how to acquire proper dualboot anyway, feel free to tell me. 
I'm thinking along the lines of putting a bootloader on the Revodrive, but I'm worried that that'll cause it to default to the SSD every single time.

---

### Post by darkod on 2011-11-24
Since you didn't install with the alternate cd activating the fakeraid in the process, I wonder if the dmraid package is loaded at all or if the array is activated as far as ubuntu can see.

I found this link with a quick search on google:
[http://en.gentoo-wiki.com/wiki/RAID/NVRAID_with_dmraid](http://en.gentoo-wiki.com/wiki/RAID/NVRAID_with_dmraid)

If you ignore the fact that it's for gentoo, and focus only on the dmraid commands, in the part Loading dmraid with LiveCD says that you can activate existing array with:

sudo dmraid -a y

On another page I noticed that the command to delete an array seems to be:

sudo dmraid -x

so make sure you DO NOT run anything like that. :)

dmraid man page:
[http://linux.die.net/man/8/dmraid](http://linux.die.net/man/8/dmraid)

---

### Post by XSaenen on 2011-11-24
Hehe, I'm going to stay clear of such dangerous commands.  I already went way out of my comfort zone to get this far.  
I'll need to do a lot of googleing and studying before I'm ready to mess with raid arrays.
 
Well, at least I have Ubuntu running properly on the PC itself and can boot to it whenever I want.  Putting it on my laptop should be easy now, and on that one the dualboot should work just fine.

---

### Post by darkod on 2011-11-24
I can't say I blame you. :)

Although I'm pretty sure this is just a case of the array not being made active, I can't tell for sure.

One idea though, just to see if the Revo is recognized, which is the first step ubuntu to be able to work with the array at all. If I'm not mistaken, the Revo should be considered as PCI or PCI-X device. So, running the command to list all pci devices should show it (or it's controller):

lspci

I'm curious if it shows up.

---

### Post by XSaenen on 2011-11-25
Ubuntu sees a RAID controller, but I'm not sure if it's the Revo.  

```
xavier@Red-Queen:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Device 1c46 (rev 05)
00:1f.2 IDE interface: Intel Corporation Cougar Point 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation Cougar Point 2 port SATA IDE Controller (rev 05)
01:00.0 PCI bridge: PLX Technology, Inc. PEX 8647 48-Lane, 3-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ab)
02:04.0 PCI bridge: PLX Technology, Inc. PEX 8647 48-Lane, 3-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ab)
02:08.0 PCI bridge: PLX Technology, Inc. PEX 8647 48-Lane, 3-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ab)
03:00.0 VGA compatible controller: ATI Technologies Inc R700 [Radeon HD 4870 X2]
03:00.1 Audio device: ATI Technologies Inc HD48x0 audio
04:00.0 Display controller: ATI Technologies Inc R700 [Radeon HD 4870 X2]
05:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
06:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
08:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
0a:00.0 PCI bridge: Pericom Semiconductor PCI Express to PCI-XPI7C9X130 PCI-X Bridge (rev 04)
0b:00.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)
xavier@Red-Queen:~$ 
```I must add that I put Ubuntu on my laptop and my netbook, and the dualboot there works flawlessly.  
The laptop ( HP pavilion dv6-3000 ) is having a few touchpad issues because the buttons are part of the actual touchpad surface, which makes click & drag a bit difficult.  It just goes berserk if I click and then touch another place on the touchpad with another finger.  It also won't recognize the right click button.  But that's probably a matter of adjusting some lines in some files.  I'll leave that for another topic.
On the netbook it's running perfectly fine.  I just might ditch Windows completely on that one.
Not too sure about touchscreen functionality, so I'll leave my HP Slate alone for now.

---

### Post by darkod on 2011-11-25
Being detected as PCI-X Silicon Image I would say that's it.
Probably just activating the array is what's missing to show up in ubuntu.

---

### Post by dabl on 2011-11-25
I run aptosid on a 120GB Revodrive.  My Asus motherboard can not boot the Revodrive, so /boot is on a small 15GB SATA SSD (the rest of that one -- 14.5GB -- is swap).  I don't dual boot, but I don't see why I couldn't if I wanted to.  I have a Win 7 VM for necessary Windows work.

I disabled the Revodrive's default RAID, and use it as 2 60-GB partitions.  It's fast enough that way -- the RAID is not necessary for any of my purposes.  The Win 7 VM and a couple other VMs are also on the Revodrive.  I have a pair of WD1002 6GB/s SATA drives in a BTRFS filesystem for general data storage.  It all works great.  Post back if you need any details about it.

---

