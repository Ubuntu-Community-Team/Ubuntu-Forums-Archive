---
title: "How to add Windows to GRUB (moved Wind. partition to another disk)?"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by tmp72 on 2013-08-22
I had 2 hard drive:

1) Windows 7 (*NTFS*)
2) Ubuntu (*ext*), linux-swap (*swap*)

I bought new hard drive what is 3x more faster than my older. So i decided to move my operations systems to new HDD.
Ofc i didn't installed them as fresh but used some software to copy all three (Windows, linux, linux-swap) partitions to new HDD.
It finished successfull. I marked new Windows partition as *active.* After this opertaion, i unplagged both older HDD from PC. Now i used lubuntu LiveCD to change */etc/fstab* file and rewrite GRUB 2. Ok, done. Now i'm able to launch "new" linux from "new" partition on new HDD. (I got a problem with linux-swap but doesn't matter right now) 

Ok cool story bro, but now i got some !#$^% problem [B]how to add Windows entry to GRUB menu?
[/B]I tried with:

adding lines to */etc/grub.d/40_custom*
```
#!/bin/shexec tail -n +3 $0


menuentry "Windows 7 (loader) (on /dev/sda1)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
chainloader +1
}

```

then
```

grub-mkconfig -o /boot/grub/grub.cfg

```

Right now inside grub.cfg there are no lines about Windows entry. So i tried:
```

update-grub

```
or
```

update-grub2

```

Not working all, still no Windows entry on *grub.cfg* and GRUB list after restart. 
What should i do?

---

### Post by deadflowr on 2013-08-22
Not knowing exactly what you've done, my guess is that you'll need to rebuild the Windows boot manager.

It's hard to tell what you did, whether or not you were ever successful in loading/running Windows from the new drive or not.

[EasyBCD]("http://neosmart.net/EasyBCD/") might help.

---

### Post by tmp72 on 2013-08-22
> **deadflowr said:**
> Not knowing exactly what you've done, my guess is that you'll need to rebuild the Windows boot manager.

It's hard to tell what you did, whether or not you were ever successful in loading/running Windows from the new drive or not.

[EasyBCD]("http://neosmart.net/EasyBCD/") might help.


Well, right now i added this *Windows* entry so i got it on GRUB list after restart. I fixed my UUID problem with linux and linux-swap partition so its working good. But the problem is with booting Windows partition. I used Windows Recovery mode from Windows 7 instalation DVD and after the "revocery" (hehe) process now Windows is trying to start. In the end it will fail with BSOD with code (dont remember for sure what it was, i will verify it in few minutes) "0x0c00000e" or "0x0c00000c". 

Im not sure I need to fix this problem issue - I mean... this Windows system I installed long time ago and it is runing slowly. So maybe faster way is to reinstall @#$% than repair it. The more I still got this Windows instalation on another disk/partition and its working there.


**Update:**
The blue screen is:
> STOP: c000021a {Fatal System Error}
The Session Manager Initialization system process terminated unexcpecly with a status of 0x000003a (0x00000000 0x00000000). 
The system has been shut down.


---

### Post by orasisd on 2013-08-22
I am not sure, I believe your problem is windows related after using a new disk, maybe some MBR stuff is missing. Were they images of the partitions you copied to the new disk ? In my experience all those programs like acronis etc, **do** mess things.
On Ubuntu you may wanna give a try to 'Boot Repair'

---

### Post by oldfred on 2013-08-22
Boot-Repair primarily is for Linux systems, and only makes minor fixes to Windows like MBR or turn on chkdsk flag.

Windows has all sorts of details and best to use Windows tools to move a Windows install. The MBR may have serial number info (bytes between boot code and partition table). The sectors after the MBR may contain serial numbers for DRM software (we had big conflicts with grub2 and flexnet trying to both use sector 32). And all NTFS PBR or partition boot sectors need to have the correct boot signature. Usually chkdsk fixes that. 

Best to run a full set of Windows 7 repairs.

---

