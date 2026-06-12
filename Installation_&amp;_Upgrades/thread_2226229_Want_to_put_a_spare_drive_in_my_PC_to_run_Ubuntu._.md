---
title: "Want to put a spare drive in my PC to run Ubuntu. Best way?"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by warren3 on 2014-05-26
Hi.


I have recently been drawn to the world of Ubuntu after putting Lubuntu on my uncles XP laptop. 


After thinking about buying a little netbook just to use for an Ubuntu mess about I have decided to put a spare lappy HD into my PC. 


My PC has these drives:
120GB 840 Evo with Win7 and programs on it.
500GB mechanical drive with flac files on it.


So I would like to add a lappy HD on another SATA controller. Now I have terrible memories of using partition magic from years ago and corrupting my OS drive. I just don't want to mess up my Win7 SSD drive and have to re-install.


Is it as simple as disconnecting my two drives and connecting my lappy hd and installing Ubuntu. Once this is installed, reconnecting my Evo and 500GB drive and using F12 to choose my boot drive or do I need to do something else as well?  I just don't want to boot into Ubuntu and have it do something to my other drives without me knowing.


Do I need a bootmanager?


Thanks.

---

### Post by mastablasta on 2014-05-26
> **warren3 said:**
> 
Is it as simple as disconnecting my two drives and connecting my lappy hd and installing Ubuntu. Once this is installed, reconnecting my Evo and 500GB drive and using F12 to choose my boot drive or do I need to do something else as well? I just don't want to boot into Ubuntu and have it do something to my other drives without me knowing.

yes, that is the safest way for someone that doesn't know exactly what they are doing :p

BTW, if you select the correct drive for instalation of OS and boot loader other drives remain untouched.

> 
Do I need a bootmanager?

sure, all OS need one. it's installed by default. windows uses it's own that can boot only windows OS. Ubuntu uses GRUB that can boot Ubuntu or Windows or FreeBSD or... .

---

### Post by oldfred on 2014-05-26
If you have unplugged drives and just install to empty drive it will default to / (root) and swap on entire drive. For a smaller drive and a new user that is fine. Auto install always installs grub2 boot loader to sda. Which if only drive will also be ok.

But if you want more control over partition sizes, additional partitions, a separate /home or anything other than auto install's install of grub to drive that is sda then you have to use Something Else. I think gparted is a bit easier to use for partitioning, but you can use the built in practitioner to manually create, format and choose mount points.
Only with Something else do you get the combo box at bottom of partition screen to change location of grub2 boot loader.

---

### Post by warren3 on 2014-06-01
Hello.

Thanks for your advice.

I am still unsure on the best method.  So the hard drive is only a small laptop drive and that is the one I want to put Ubuntu on.  So should I disconnect my main Windows SSD and my 500gb data drive while I install Ubuntu onto the laptop drive?  Or should I just leave everything connected and then make the whole laptop drive into unallocated space and choose to install 'Ubuntu alongside Windows' option during installation?

Cheers.

---

### Post by LastDino on 2014-06-01
Like already mentioned, disconnecting is the safest way and you wont face booting problems either as WIndows boot-loader wont be touched and Grub will be installed on the only connected drive during installation. That's a win-win situation.  Like Oldfred has suggested, If drive is small (250GB or approx), you wont even need to mess with partitions much and will be fine with just SWAP and /root. These will be created automatically when you install the Ubuntu without you actually needing to defining any partition at all. Just let it be default, given **all other drives are disconnected**.

---

### Post by sudodus on 2014-06-01
> **LastDino said:**
> Like already mentioned, disconnecting is the safest way and you wont face booting problems either as WIndows boot-loader wont be touched and Grub will be installed on the only connected drive during installation. That's a win-win situation.  Like Oldfred has suggested, If drive is small (250GB or approx), you wont even need to mess with partitions much and will be fine with just SWAP and /root. These will be created automatically when you install the Ubuntu without you actually needing to defining any partition at all. Just let it be default, given **all other drives are disconnected**.

+1 ... assuming that it is easy to use a hotkey (F12, or whichever key it is in your computer) to select boot device.

Otherwise, if you have to enter the BIOS/UEFI menus, change the boot order, and reboot, it is better to keep the default boot device connected and put the bootloader into the that device, **/dev/sda**

---

