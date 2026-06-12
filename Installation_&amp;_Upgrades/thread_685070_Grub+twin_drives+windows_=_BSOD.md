---
title: "Grub+twin drives+windows = BSOD"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by dfarce on 2008-02-01
First thing's first. I know that there are a ton of help me forums on the internet, but I haven't found one which actually relates to the same problem I am having. Correct me if I'm wrong and link me, but I think I've hit a dead end on this. 

My setup is as follows:
SATA1:
   250Gb drive, windows on first partition. 
   mounted under /dev/sda
   Referenced under Grub as hd1
   Normal windows boot loader installed and *FUNCTIONING CORRECTLY*

SATA2:
   250Gb drive, data only
   mounted under /dev/sdb
   Referenced under grub as hd2

SATA3:
   30Gb drive, loaded with Ubuntu Hardy Heron
   Mounted under /dev/sdc
   Referenced under grub as hd0
   Grub installed and also *FUNCTIONING CORRECTLY*

Menu.lst
   
#Hardy Developement Branch
title		Ubuntu Hardy
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-4-generic root=UUID=49d6d09c-3c40-4373-9469-ca8fbe2ed5f4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-4-generic
quiet

#Windows XP
title				XP Pro
rootnoverify 			(hd1,0)
savedefault
makeactive
map 				(hd0,0) (hd1,0)
map 				(hd1,0) (hd0,0)
chainloader			+1

What happens is this, if I set the boot order in the bios so that grub boots, then grub will load properly. If I select Hardy then it will load and Ubuntu will boot, no problem there. Likewise, because I never touched my windows MBR, if I select the windows drive to boot first in the bios, windows boots, no problem. But, when I select windows from grub, then that's when things get interesting. For a while, selecting windows would seem to work at first, but I never actually got to a full boot. I would see the loading screen, then *bam*! BSOD with the following error code on it:

STOP: 0x0000007B(etc., etc., etc., etc)

After some research, I noted that that kind of stop error was resultant from windows not being able to find certain drivers, most notably, HARD DRIVE DRIVERS! So, I downloaded the latest drivers for windows XP for my motherboard and installed them. After playing with some other options, including chainloader (hd1,0)+1, I noticed that the error message had changed. It now reads:

STOP: 0x0000007E(etc.,etc.,etc.,etc.)
AND
GoBack2k.sys - Adress BA66CABB base at BA66A000 DateStamp 434177fd

The numbers seem to change every time I do it. 

I am really lost now, it seems to be a windows problem, but I am not sure if its just a parameter I am missing in grub thats not passing the proper info to windows. Anyone have any idea how to make windows load properly out of grub? I don't really desire to overwrite the MBR unless I am sure that that is what it will take to fix the problem. I would like to keep it windows relatively independent because, as is shown here, if grub has troubles then I can flip the boot order and boot back into windows, skipping grub altogether. 

Thanks in advance and sorry for the long post!

---

### Post by dfarce on 2008-02-02
A quick update, for whatever reason, my errors have reverted to being STOP: 0x0000007B errors again. No idea what caused the other ones.

---

