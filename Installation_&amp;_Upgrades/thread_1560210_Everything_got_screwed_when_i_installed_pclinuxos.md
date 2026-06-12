---
title: "Everything got screwed when i installed pclinuxos"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by Zireth ZH on 2010-08-24
Hey guys.. i had 3 OS installed before i decided to install pclinuxos... 

I had ubuntu, mint and win 7... now i cant boot non of em having pclinuxos installed in a newly created partition... grub only shows pclinuxos and nothing else... please help.. i cant even see my other partitions .. installed pclinuxos as root ... sorry im a nub.. 

please help

---

### Post by wojox on 2010-08-24
Try [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Zireth ZH on 2010-08-24
> **wojox said:**
> Try [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

i only got pclinuxos live usb .. will this work ? im lost lol

---

### Post by ajgreeny on 2010-08-24
No, I don't think that will help as PCLinuxOS has legacy grub, as far as I can make out.  You really need a live CD with grub2 on it, so Mint or Ubuntu would be fine.  However if you can find all the details of the partitions of ubuntu and mint using PCLinuxOS, it should be possible to add the entries for them into the PCLinuxOS menu.lst file.

In PCLinuxOS run ```
fdisk -l
``` as root, and also ```
blkid
```again as root.  I know very little about that distro, so will have to leave you to deal with running commands as root, but I suspect it needs "su" to get root privileges, then run the commands, and report back here the output of those.

You can change the OS that supplies grub once you have booted to either Mint or Ubuntu by running ```
sudo grub-install /dev/sda
``` assuming that grub is on the MBR of your first disk.

---

### Post by Zireth ZH on 2010-08-24
> **ajgreeny said:**
> No, I don't think that will help as PCLinuxOS has legacy grub, as far as I can make out.  You really need a live CD with grub2 on it, so Mint or Ubuntu would be fine.  However if you can find all the details of the partitions of ubuntu and mint using PCLinuxOS, it should be possible to add the entries for them into the PCLinuxOS menu.lst file.

In PCLinuxOS run ```
fdisk -l
``` as root, and also ```
blkid
```again as root.  I know very little about that distro, so will have to leave you to deal with running commands as root, but I suspect it needs "su" to get root privileges, then run the commands, and report back here the output of those.

You can change the OS that supplies grub once you have booted to either Mint or Ubuntu by running ```
sudo grub-install /dev/sda
``` assuming that grub is on the MBR of your first disk.

heres the output .. what now? thx :D

[root@localhost /]# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7987739d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15200   122092544   83  Linux
/dev/sda2           15200       30400   122093568    7  HPFS/NTFS
/dev/sda3   *       30402       60802   244190527+   5  Extended
/dev/sda5           30402       40759    83200603+   7  HPFS/NTFS
/dev/sda6           45635       60180   116837376   83  Linux
/dev/sda7           60180       60802     4993024   82  Linux swap / Solaris
/dev/sda8           40760       45634    39158406   83  Linux

Partition table entries are not in disk order
[root@localhost /]# blkid
/dev/sda1: UUID="21b3c1e2-b521-43d8-9756-649e0bb32f5b" TYPE="ext4" 
/dev/sda5: UUID="6CDCBAE2DCBAA5AC" LABEL="Backup Disk" TYPE="ntfs" 
/dev/sda6: LABEL="Xfce" UUID="5990120b-ca88-43f7-9cf5-4ec61982606e" TYPE="ext4" 
/dev/sda8: UUID="620cc8ea-6d1b-4968-8c14-00e103c79214" TYPE="ext4" 
/dev/sda7: UUID="691e8fba-6934-4b8b-a971-674e217d2bdb" TYPE="swap" 
/dev/sda2: UUID="8E2090CC2090BD21" LABEL="Windows 7" TYPE="ntfs"

---

### Post by Zireth ZH on 2010-08-24
> **ajgreeny said:**
> You can change the OS that supplies grub once you have booted to either Mint or Ubuntu by running ```
sudo grub-install /dev/sda
``` assuming that grub is on the MBR of your first disk.

im not sure about that MBR thing.. only thing i know is.. that i installed win 7 first.. then ubuntu .. then mint... does this helps?

---

### Post by ajgreeny on 2010-08-24
I have had a bit of a re-think, and now I suspect the easiest way to proceed is to use PCLinuxOS to download supergrub, burn it to a CD as an image as you would an iso of ubuntu or mint.  When you boot from that CD it should allow you to boot from any OS on your machine, so try out what it finds, and when you get to ubuntu or mint run 
```
sudo grub-install /dev/sda
sudo update grub
```
and grub should then run from ubuntu or mint, and should include PCLinuxOS in the menu.
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by Zireth ZH on 2010-08-24
> **ajgreeny said:**
> I have had a bit of a re-think, and now I suspect the easiest way to proceed is to use PCLinuxOS to download supergrub, burn it to a CD as an image as you would an iso of ubuntu or mint.  When you boot from that CD it should allow you to boot from any OS on your machine, so try out what it finds, and when you get to ubuntu or mint run 
```
sudo grub-install /dev/sda
sudo update grub
```
and grub should then run from ubuntu or mint, and should include PCLinuxOS in the menu.
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

first ... thanks alot for ur help! 

Before u replied i posted the same topic in pclinuxos forums.. they told me to boot pclinuxos livecd .. then go to restore MRB, RMB i dun remember what it was.. it worked.. it seems that it replaced grub 2 for previous version of grub maybe? i can now see both ubuntu and mint in the grub menu.. except win 7 .. got any ideas on how to fix this? 



i can go try what u suggested if that fixes my prob.. 

the last thing is.. i can see my drives in both ubuntu and mint but not in the case of pclinuxos.. what went wrong ?

thanks thanks alot

---

### Post by Zireth ZH on 2010-08-24
OK i solved the problem by using PCC (pc linux control center) `Setup boot system` 

Wow so easy... well the grub thing looks awful but at least i can boot all my OS ... ubuntu should get a control center like that and specially that feature in next release, if they dun have a feature lika this... it is good for newbies.. 

thanks for the help guys

---

### Post by ajgreeny on 2010-08-25
I'm glad you got there in the end.

I know so little about PCLinuxOS that I had no way to know that you could do what you have managed.  It seems PCLinuxOS is a good distro to look at again; I last looked about 4 or 5 years ago.

In spite of the many complaints about grub2 in this forum, I find it extremely good, and it has the advantage of finding all OSs after it has been re-installed, simply by running ```
sudo update-grub
```Legacy grub does not, or did not do that for you and needed manual edits to add any non detected OSs after installation or re-installation.

---

