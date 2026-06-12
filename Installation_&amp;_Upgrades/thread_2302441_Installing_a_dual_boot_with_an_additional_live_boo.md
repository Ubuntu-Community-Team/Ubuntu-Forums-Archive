---
title: "Installing a dual boot with an additional live boot system"
date: 2015-11-10
forum: Installation &amp; Upgrades
---

### Post by Jahidul_Hamid on 2015-11-10
I am thinking of installing a dual boot with win10 & xubuntu/LM and a live boot of Xubuntu/LM in my 2TB portable HDD. I know that a dual boot is possible, but not sure about the third one.

My boot options should be like this:

1. (partition#1) Xubuntu/LM
2. (partition#2) Windows
3. (partition#3) Xubuntu/LM live


And also If I install a full system on the Portable HDD, will there be a problem running it on different PCs which have different hardwares?

---

### Post by Dennis N on 2015-11-10
Could you clarify what LM means in Xubuntu/LM? What exactly are you installing on partition #3? Adding 'live' to it makes me wonder what you have in mind there.

---

### Post by oldfred on 2015-11-10
Is system newer UEFI or older BIOS? And are other systems UEFI or BIOS?

If you do not install proprietary drivers, it should work on other systems, but then may not work as well on all systems. Depends mostly on Video & Wireless drivers.

If you have a full install, you then can use grub to directly boot ISO. I have many ISOs on my sdb (internal) and several flash drives that I boot with grub2's loopmount.

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by yancek on 2015-11-10
You will need to answer the questions above before you actually get any help, to many unknowns.  If you want an Xubuntu install, a windows install and also a Live read-only install of Xubuntu, yes you can do that.  No one will be able to do more than guess until you post more info.

---

### Post by Jahidul_Hamid on 2015-11-12
> **yancek said:**
> If you want an Xubuntu install, a windows install and also a Live read-only install of Xubuntu, yes you can do that.
You got it...That's what I want...

---

### Post by Jahidul_Hamid on 2015-11-12
> **Dennis N said:**
> Could you clarify what LM means in Xubuntu/LM? What exactly are you installing on partition #3? Adding 'live' to it makes me wonder what you have in mind there.
It's either Xubuntu or Linux Mint, I haven't decided on the OS yet. And on partition #3 it will be a live system like a live usb/cd/dvd.

---

### Post by Jahidul_Hamid on 2015-11-12
> **oldfred said:**
> Is system newer UEFI or older BIOS? And are other systems UEFI or BIOS?

If you do not install proprietary drivers, it should work on other systems, but then may not work as well on all systems. Depends mostly on Video & Wireless drivers.



My system supports UEFI, but I always use Legacy boot.

No proprietary drivers...

---

### Post by oldfred on 2015-11-12
You cannot have Windows on the external drive. Windows does not allow that.

But otherwise you can install multiple Linux and boot live ISO directly without too much difficulty.

---

### Post by yancek on 2015-11-12
Trying to install windows 10 on an external disk will result in the below message as you need to pay microsoft a licensing fee for each computer you use it on.

> "windows setup does 
not support configuration or installation to a disk connected through usb or IEEE 1394 ports"

---

### Post by Jahidul_Hamid on 2015-11-14
> **yancek said:**
> Trying to install windows 10 on an external disk will result in the below message as you need to pay microsoft a licensing fee for each computer you use it on.

I see, thanks for the info...
It will save my time...

I am going to use these two tutorials to make a multiboot partition of live and actual systems:

[http://community.linuxmint.com/tutorial/view/1849](http://community.linuxmint.com/tutorial/view/1849)
[http://community.linuxmint.com/tutorial/view/1846](http://community.linuxmint.com/tutorial/view/1846)

---

### Post by oldfred on 2015-11-14
Examples show 32 bit.

Even if just using legacy boot, do not use anything but the 64 bit versions. No reason anymore for 32 bit unless a very old system or some major application that you have that only runs on 32s bit. Almost everything is 64 bit.

---

