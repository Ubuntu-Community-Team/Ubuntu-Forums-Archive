---
title: "Can't boot into XP after installing Ubuntu"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Hans Fastolfe on 2008-06-06
My PC won't boot at all after installing Ubuntu. I get a "disk read error" message, followed by "Press ctrl+alt+delete" to continue. At first, I could boot into Ubuntu, but not XP. Shortly thereafter, I could not boot into either.

I had tried to install Ubuntu 8 on a Compaq PC as dual boot with the existing XP Home Edition. I used the CD I just received in the mail. I ran Checkdisk and Disk Defragmenter on the PC first. The hard drive had plenty of free space, and I assigned 20 GB to Ubuntu. The first installation was not entirely successful; Firefox would not work, and I could not figure out how to reinstall. I can do this in Windows and Max OS X, but I was utterly baffled by Ubuntu (I don't claim to be a computer whiz; I hadn't studied computers since I took COBOL in college--with punch cards--and have never used Linux before).

So I started over and reinstalled Ubuntu. When the PC rebooted, I saw the expected boot menu, but with twice as many Ubuntu options; they seemed duplicated. Ubuntu booted properly, but not XP. On trying to boot into XP I received the "disk read error" message. After that, Ubuntu would not boot.

The PC recovery tools do not work. When I try to run the Windows System Recovery utility, I receive the same "disk read error" message. I did not try the Destructive Recovery utility, as that would seem to erase the entire hard drive and restore it to the original out-of-the-box settings. I wish to avoid that, if possible. Unfortunately, I need Windows on the PC.

I do not think the Ubuntu installation disk is corrupted. I used the same disk the preceding day to successfully install Ubuntu on an XP PC as a dual-boot system. That works properly, both XP and Ubuntu. The Live CD function works properly, as I ran Ubuntu from it on the now-unbootable PC. I seemed to see the files on what should be the Windows partition.

A friend suggested I might have corrupted the Windows boot.ini file on the second Ubuntu installation.

Am I frakked?

---

### Post by meindian523 on 2008-06-06
Please post ```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.lst
``` and the link to the mythbuntu thread.

---

### Post by Hans Fastolfe on 2008-06-06
Here's the link to mythbuntu thread:

[http://ubuntuforums.org/showthread.php?t=820480](http://ubuntuforums.org/showthread.php?t=820480)

---

### Post by Hans Fastolfe on 2008-06-06
I ran ```
sudo fdisk -l
``` and this is what came up:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6993    56171241    7  HPFS/NTFS
/dev/sda2           13638       14593     7673400    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            6994       13637    53367930    5  Extended
/dev/sda5            9613       13474    31021483+  83  Linux
/dev/sda6           13475       13637     1309266   82  Linux swap / Solaris
/dev/sda7            6994        9497    20113317   83  Linux
/dev/sda8            9498        9612      923706   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
```

The XP boot.ini file reads as follows:

```
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcon
```

---

### Post by Hans Fastolfe on 2008-06-06
Just spoke with my local PC repairman, who's done very good work for my family and friends.  He says the most likely cause is a corrupt boot loader.  If so, I'll have to reinstall Windows XP and then install Ubuntu.

---

### Post by Herman on 2008-06-06
Wait a minute.

I don't think that's a boot loader error message, I think that's a message from your BIOS.
In other words, your computer does not seem to be booting as far as the boot loader every time.
You may be able to fix that by taking a look in your BIOS and checking that your hard disk is properly detected and set up in there.
The fact that this is occurring intermittently seems to imply some kind of hardware trouble, such as a loose connection or a faulty hard drive cable possibly, (if this is a desktop PC), or, (I hate to say it), even a flakey hard drive. 
Check to make sure your hard drive is plugged in securely, and if it's an IDE (PATA) type of hard drive, also recheck your jumpers, including the jumpers on your CD/DVD drive too.

A good test too try to see if it's a hardware problem or a MBR problem or a boot loader problem or what, it to try booting up from a CD such as [Super Grub Disk]("http://www.supergrubdisk.org/")
 and see what happens. 
Super Grub Disk will boot Windows from the boot sector, so you will be bypassing the MBR, so that may help determine if it's an MBR or a GRUB problem for sure. (I think not).

Another good CD you can use for testing purposes if you have Windows XP, is the NTLDR CD that you can download from Miles Comer's website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm").
That CD contains the Windows XP boot loader NTLDR, and also ntdetect.com and a generic boot.ini file, so you will be able to boot your Windows XP even if the MBR, boot sector, anf your Windows boot loader are sll corrupted or even missing.

You might also try running CHKDSK /R from a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"). That should fix a corrupted file system in Windows XP in case that's the problem. 

It would probably be worth spending some time testing to try to locate the cause of the trouble rather than just re-installing, although you can try that if you want. 

Here are a few other links on this error message, and re-installing didn't help these other people, 
[Getting rid of "A Disk Read Error Occured. Press CTRL+ALT+DEL to ...]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.hardwareanalysis.com%2Fcontent%2Ftopic%2F19004%2F&ei=oKBJSODhGpyuoQTg0oDBBA&usg=AFQjCNEL_oZnXZ3AI0k1kZSfDSHJROg_XQ&sig2=dsDGNNWc_gf0EQltByPeGQ")
and 
[Disk Read Error]("http://www.google.com.au/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fwww.hardwareanalysis.com%2Fcontent%2Ftopic%2F11890%2F&ei=oKBJSODhGpyuoQTg0oDBBA&usg=AFQjCNE9u_WVIMXCoZdZTlzJPlxOtszYZw&sig2=0f_4TvF_0HgGO1ngfuSITg")
and
[HELP! A disk read error occurred. Press CTRL+ALT+Delete to restart ...]("http://www.google.com.au/url?sa=t&ct=res&cd=4&url=http%3A%2F%2Fwww.raymond.cc%2Fblog%2Farchives%2F2005%2F10%2F21%2Fhelp-a-disk-read-error-occurred-press-ctrlaltdelete-to-restart%2F&ei=oKBJSODhGpyuoQTg0oDBBA&usg=AFQjCNH2aoAX-DLocE0V8MwLvWYPSzFO7A&sig2=aPFQ9RZqluwqAL3_etFnSA")
There are lots more in google.

Regards, Herman :)

---

