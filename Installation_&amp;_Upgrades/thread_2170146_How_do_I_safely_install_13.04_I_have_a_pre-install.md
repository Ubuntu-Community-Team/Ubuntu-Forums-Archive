---
title: "How do I safely install 13.04? I have a pre-installed copy of Win8."
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by Chaivalla on 2013-08-25
I have a Lenovo Y500 which came pre-installed with Windows 8. How do I safely install Ubuntu 13.04? I can’t afford to mess up my current installation as I rely on it for work.[br]br[/br][br]br[/br]Please help. A step-by-step guide would be nice. I already have the USB installer prepared via UNetbootin.[br]br[/br][br]br[/br]I have two drives, a 16 GB SSD and a 1 TB HDD:[br]br[/br][br]br[/br]Disk 0 (16 GB SSD)          
[list]        
[*]14.91 GB // Primary Partition           
[/list]
        Disk 1 (1 TB HDD)       
[list]        
[*]1000 MB // Recovery Partition        
[*]260 MB // EFI System Partition        
[*]1000 MB // OEM Partition        
[*]884.18 GB // Boot, Page File, Crash Dump,&#65279; Primary Partition // NTFS (C:)        
[*]25 GB // Primary Partition // NTFS (D:)        
[*]20 GB // Recovery Partition        
[/list]

---

### Post by mikewhatever on 2013-08-25
No one can ever guarantee that you won't ever make a mistake. If you can't efford to mess up W8, and there is no recovery option (DVD/USB), then install Ubuntu in VirtualBox.

---

### Post by Chaivalla on 2013-08-25
:( *sighs* Things used to be easier a few years ago.

---

### Post by Quackers on 2013-08-25
You would be dealing with partitioning on a bootable hard drive. There is always (and always has been) risk involved with such actions.
Most of the time things will go without a problem. Sometimes there will be a problem and it is vital to be able to get a) your system back and b) your data back.
You have to decide whether it's worth the risk or not.

---

### Post by Boab1993 on 2013-08-25
Hi there Chaivalla,

If your just wanting ubuntu without going anywhere near your windows 8 partition, you can install it onto your usb drive(it will be fully functioning and have all features unlike the Live CD image you have on it currently)

First things first, with windows 8, read this page : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

Its very friendly and easy to do.

If your comfortable with Unetbootin, dont let me put you off, its a good bit of kit.

Ive had trouble with Unetbootin in the past is use the Universal Usb Installer : [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

You should be good to go from this point.

Boot from your USB stick, if you dont know how to do this during your 'Lenovo' screen at the very begining of startup there should be a few commands at the bottom of the screen like 'f10 for BIOS' etc

There should be one reading '[a key] for BootLoader' -in some cases this doesnt exist and is just in the 'BIOS' menu so be sure to check there if unsure- or similar, hit that key and edit the order so that usb is at the top and continue.

You should then have the ubuntu splash screen appear, from here you can try it out or install and other things.

After pressing enter at 'Install Ubuntu' you should be given 3 options of how to install ubuntu.

Choose the 'alongside windows 8' option.

Run through the install, and your done.

---

### Post by Chaivalla on 2013-08-25
If I choose "alongside windows 8" I don't need to install on or resize a partition??

---

### Post by Boab1993 on 2013-08-25
Whoops.

Just saw two partitions, didnt see one was your recovery. However, this is not a problem, theres a windows tool for 'shrinking' your partition.

If you dont know how to do this look here: [http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/](http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/)

Its a step by step guide with screen shots and arrows pointing directly to what you need to do.

The tool will not allow you to shrink onto space where data is stored, so you will not loose any data on your disk; if you cant shrink your partition properly, you need to defragment your disk and then it should be possible.

---

### Post by Chaivalla on 2013-08-25
My post got deleted, and I want to apologize if I offended anyone. It wasn't aimed at anyone really. I was just expressing my frustration at this whole complicated installation process. My frustration still stands. I just want to be able to install and use Ubuntu without any complications. Thanks.

---

### Post by Boab1993 on 2013-08-26
Haha thats alright i can understand, however it is best not to do things like that on the forum or moderators can have your thread closed.

The reason this is far more complicated than normal install is because of the new UEFI firmware windows 8 has, ubuntu just wasn't made for it, but i imagine in later updates it will be taken into account.

If you don't like the methods above, if you want to install it to a usb stick, all you need is a small partition and large partiton on your usb. intsall the live cd to the small one, install the actual OS to the big one. You will need to install ubuntu if EFI mode and disable secure boot/fast boot, but thats a few flicks of a switch.

---

### Post by oldfred on 2013-08-26
Some other threads with Lenovo systems. So be somewhat similar, if not identical.
 Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

Best to use Windows tools to shrink Windows and reboot Windows a couple of times so it can run chkdsk and make its repairs to recognize new size. 
Does your Windows boot ok with secure boot off?

Lots of links to install procedures many with screen shots in link in my signature.

---

### Post by sharathkumar on 2013-09-07
This is the first time I am writing an installation guide, am afraid it might not be that good. But I've successfully tried this on my Lenovo U310 with 32GB SSD and 500GB HDD.

Get Ubuntu 64bit 13.04 and using [unetbootin]("http://unetbootin.sourceforge.net/"), create a bootable flash drive.

Since your storage is in a RAID configuration, I'd advise you to take a backup before proceeding. It goes without saying though.

[COLOR=#000000]Disk 0 (16 GB SSD) [/COLOR]

[LIST]
[*]14.91 GB // Primary Partition
[/LIST]

[COLOR=#000000]Disk 1 (1 TB HDD) [/COLOR]

[LIST]
[*]1000 MB // Recovery Partition
[*]260 MB // EFI System Partition
[*]1000 MB // OEM Partition
[*]884.18 GB // Boot, Page File, Crash Dump,&#65279; Primary Partition // NTFS (C)
[*]25 GB // Primary Partition // NTFS (D)
[*]20 GB // Recovery Partition
[/LIST]

As the EFI Partition's location and the SSD's usage as a cache drive, it is a bit complex. But it gives Windows a boost whilst booting up and running applications.
Installing on the 25GB Primary Partition would be best. So transfer it's content.

Installation:
1) Booting probably requires pressing the Novo button (previously known as One Key Recovery button) on the side to get to boot menu.
From previous posts it's clear that you got to the installation point.

2) In the type of installation, select "Something Else" and select the 25GB partition, format it and assign the mount point of "/", the root folder. 
3) Make the 25GB partition the boot device and proceed with the installation.
4) With UEFI in place, the Windows Boot Device is the option you must be getting in boot order, but the above step adds "Ubuntu" to the boot menu.
5) Rebooting might end up in two ways.

a) Into GRUB with Ubuntu and Windows EFI booting option in the GRUB menu, Ubuntu will boot fine. But Windows won't.
For this, you simply have to goto UEFI menu by pressing the NOVO key and changing the boot order to "Windows" first and Ubuntu next. Ubuntu's position here is irrelevant. This will make Windows boot first but the only way to boot into Ubuntu will be by pressing the Novo key and selecting Ubuntu in the Boot Menu. Once inside Ubuntu, you can later delete the Windows EFI option from GRUB 

b) Into Windows; in which case, as above, you'll have to press the Novo key and get to Ubuntu via the Boot Menu.

This work-around is working fine for me.

---

