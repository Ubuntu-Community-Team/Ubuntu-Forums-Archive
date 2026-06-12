---
title: "Error: No Such Partition?"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by sfps9 on 2011-01-02
I recently tried to uninstall Ubuntu myself using my Windows Vista Drive Manager and just deleting the entire partition and merging it with my Vista partition. All I wanted to do was rid myself of Ubuntu because I couldn't understand it. Unfortunately, now when I try to boot into Vista, all I get is "error: no such partition grub recover>" or something like that. I have no idea how to fix this since I can't get past the error into an OS. I have gotten all of my important data off the computer but I don't have a recovery disc! PLEASE HELP I don't know what to do!

---

### Post by sfps9 on 2011-01-02
BTW, all I did to get the data off was to boot Ubuntu from my flash drive and copy the data from the hard drive to another flash drive. The only solution I can think of is reinstalling Ubuntu on a new partition but I wasn't sure if that would allow the grub to boot and I don't know how to create another partition while not in Windows. When I tried to use GParted when I was running Ubuntu off my flash drive it wouldn't let me shrink the existing partition.

---

### Post by wilee-nilee on 2011-01-02
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

boot to the repair command line then run
bootrec.exe /fixmbr

There is also a Linux bootloader you can use if you still have a cd or thumb loaded.

---

### Post by sfps9 on 2011-01-02
So you're saying I should download that ISO and burn to a DVD. Then stick that in my laptop and boot to that. I assume I can pull up a command prompt and type in what you said. What will that do exactly. From my understanding my hard drive is messed up, I can't even boot into Windows!

---

### Post by sfps9 on 2011-01-02
The other thing I just thought of: if I reinstalled my BIOS, which I don't know how to do, would it work around the GRUB?

---

### Post by wilee-nilee on 2011-01-02
> **sfps9 said:**
> The other thing I just thought of: if I reinstalled my BIOS, which I don't know how to do, would it work around the GRUB?

Grub is in the mbr, but the files that made it work on booting vista were in Ubuntu if you just want Vista follow the instructions, it puts the MS bootloader in the mbr=master boot record. If you just want to load a Linux boot loader we would need to have you boot a live Ubuntu cd and run this command, post it and I will give you the command to install that bootloader.
```
sudo fdisk -lu
```

The download is like 138 mib use a cd it is just a small program to get you to the recovery.

Here is a W7 forums visual to getting to the command in repair and some instructions.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following command
**BootRec.exe /fixmbr** 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by sfps9 on 2011-01-03
WORKED LIKE A CHARM! I can't thank you enough! Really, thanks for taking the time to help me, and most likely others, who have this problem!

---

### Post by carver29 on 2011-01-17
I hope someone can help me. I have spent 4 hours today trying to delete ubuntu from my laptop. The uninstall seemed to work, but there apears to be a partition left of about 12 gb on Hard drive. My big problem is the option to boot win7  ( 64 bit) or ubuntu comes up everytime I start the  Acer Aspire 5810-T. I have tried this  [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)   along with all the other things I could search out, none seem to remove the dual option. I think I can put the ubuntu disk in to recover the Hd space, just not sure it is not a windows space, it is labled PQSERVICE and is 11.72 GB, fat32.  I read I need to get rid of the double boot option first. How do I do that? I did look at bcdedit but I am not sure what to do, I am not very computer literate.  It is a shame ubuntu does not warn of how hard it willl be to uninstall completely the OS, I would have just used it off the Cd drive.. I do not want it becuase it does not run software I need and honsetly it was dificult to d/l and add software.
Thank you for any clues.
Peter

---

