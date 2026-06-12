---
title: "GNU GRUB version 1.99~rc1-13 ubuntu3"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by Brooksy_FC on 2011-09-28
Hey Guys, I've recently got some new updates and installed them. I restarted my machine and now this comes up...

> Minimal BASH-like line editing is supported.
For the first word, TAB lists possible command completions. Anywhere else TAB list possible device or file completions.

grub>

I've never had this come up before and I'm not sure what it is. 

Can anyone help?

---

### Post by FerroPower on 2011-09-28
you might need to install grub in your boot partition, if you have LiveCD it will work. 
  try this 
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

This link below is complete reference kind

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by YesWeCan on 2011-09-28
Hi. The grub> prompt might indicate a missing grub.cfg file. That means you need to boot into ubuntu and run [COLOR="DarkSlateBlue"]sudo update-grub[/COLOR].

The Ubuntu Grub2 page that FerroPower gave a link to has a section on booting from the grub prompt. It's very easy.

[COLOR="DarkSlateBlue"]set root=(hdX,Y)
linux /vmlinuz root=/dev/sdZY ro
initrd /initrd.img
boot[/COLOR]

Where X =0 for sda, X=1 for sdb, etc.
Y = 1 for sdX1, Y=2 for sdX2, etc.
Z = a for sda, Z=b for sdb, etc.

If your drive is sda and Ubuntu's root partition is sda1
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

---

### Post by Brooksy_FC on 2011-09-28
Thanks for your responses,

How do I get into Ubuntu to update the grub, if I can't get in?

---

### Post by dino99 on 2011-09-28
sudo dpkg-reconfigure grub-pc

---

### Post by drs305 on 2011-09-28
Did you try to use *YesWeCan's* method of booting from the grub prompt?

If you can't into Ubuntu at all, you can boot a LiveCD and use the 'chroot' method of updating grub. The process involves mounting your Ubuntu partition and installing certain system files. You then 'chroot' and the commands you run affect the real installation rather than the LiveCD.

You can click on the "Chroot" link in my signature line to see how to chroot if you need to use this process. The thread describes how to completely purge/reinstall grub, but if you only need to update grub you wouldn't purge/reinstall - once you chroot you would only run "update-grub". You could also run *dino99's* command if necessary.

---

### Post by Brooksy_FC on 2011-09-29
The only CD I have is the installation CD, just had the software on it. I've tried typing boot, no kernal. I've tried holding shift and nothing works. 

I don't even know what GRUB is haha. This has never come up before

---

### Post by drs305 on 2011-09-30
The installation CD is the LiveCD. You can select "Try Ubuntu" to boot to the Ubuntu desktop, where you can access the Internet, explore your drive, and run scripts.

It might be best to run the Boot Info Script and post the contents of RESULTS.txt  It will show us the status of your boot files. You can download the script from the "BIS" link in my signature line.

Otherwise, the "Chroot" link will detail how to completely remove and reinstall Grub from the LiveCD (installation CD). I've also written a "Grub Rescue" megathread which helps to boot the system from the Grub command prompt. 
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by FerroPower on 2011-10-01
Something should be done about this grub errors everyone gets them(every user gets the similar error)

Why cannot grub search for bootable disks and show them in list for selection [COLOR="Red"]even if[/COLOR] some config file is missing ? 

I know a beginner like me would love to explore and configure the grub everytime such error boots up, but its time grub developers do something about it so that new users don't get scared to death everytime such screen pops up.(grub error are very similar to Blue Screen of Death in windows OS)

instead of showing some stupid grub> prompt it should automatically ask if the user want to update-grub or select the default OS from the list.

---

### Post by Brooksy_FC on 2011-10-03
I tried running sudo update-ubuntu and I get "/usr/sbin/grub-probe: error: cannot stat 'aufa'

I've ran the Boot Info Script and this is what I got...

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       240,974       240,912  de Dell Utility
/dev/sda2    *        240,975   234,436,544   234,195,570   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07D8-0405                              vfat       DellUtility
/dev/sda2        643C40263C3FF222                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------


---

### Post by drs305 on 2011-10-03
Your best bet may be to post in the Wubi Megathread. Explain your situation and post the RESULTS.txt

The people who monitor that thread are very experienced with Wubi issues.

---

### Post by Brooksy_FC on 2011-10-04
Ok will do, Thanks for your help :)

---

