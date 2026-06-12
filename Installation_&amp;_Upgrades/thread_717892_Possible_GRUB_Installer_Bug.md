---
title: "Possible GRUB Installer Bug"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by mohamedafattah on 2008-03-07
A couple of weeks ago, I was helping a friend to install Ubuntu 7.10 on his PC.
His PC had 2 hard disks: One of them was IDE (hda). The other one is SCSI (sda). Windows was installed on the SCSI one, and therefore I decided to install Ubuntu on it as the Motherboard starts from it.
The Live CD, Installation went very normal. After finishing the installation, the GRUB Loader did not show up and windows loaded.  However, After reinstalling GRUB from the alternate CD, GRUB loaded and none of the options (Ubuntu / Windows) worked correctly. The three Ubuntu options (Normal - Recovery - Memtest) reported that device not found. Windows reported that NTLDR was not found.

Well, long story short, I searched a lot on the live CD, found a couple of posts here and there, and tried a lot of different grub options and nothing worked correctly. At last, I followed a very wild guess and it worked, although I don't know the GRUB options well.

First of all, the Ubuntu load options were:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=88575a1c-30c9-42c1-abd0-0fc416e27922 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```I deleted the root option totally, and then Ubuntu loaded perfectly. My wild guess was that Ubuntu and the GRUB was on the same partition.

Secondly, the Windows load options were:
```
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```The two map options seemed to me either conflicting or useless as both Ubuntu and Windows were living on (hd0). So I commented them. Not telling you how glad I was resolving the problem and not leaving his PC with no operating system :) , I wonder what caused the problem and I hope the bug is correctly reported, but I don't know what are the necessary information required to really identify the bug in my friend's system.

The menu.lst_old represents the one installed by the alternate CD, and the menu.lst_new is the one I modified and working perfectly right now.

---

### Post by mikewhatever on 2008-03-07
You should provide more info, such as <sudo fdisk -l> and <cat /boot/grub/device.map>. Generally speaking, GRUB often gets confused when more then one HDD is in place. I've looked at the new menu.lst, and the root part for Ubuntu is missing there, so it's hard to tell if it is really on hd0, but Windows is on hd1 according to that file.

---

