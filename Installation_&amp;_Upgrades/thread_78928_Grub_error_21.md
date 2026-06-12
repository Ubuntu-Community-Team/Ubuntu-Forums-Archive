---
title: "Grub error 21"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by Chris Chan on 2005-10-19
I have installed Hoary on my dell dimension 8300 (14x200 Northwood, 512MB DDR, GeForce FX5200). I installed it on the 160GB WD drive I have as primary slave. My WinXP Home install is on the 40GB Seagate primary master. Both drives (IIRC) are set to cable-select. I chose to install GRUB to the primary master's MBR. Now, it just gives me error 21 upon boot and I can't boot into XP nor Hoary. No idea how to solve this as I am a linux newbie. Help?

---

### Post by sirtux42 on 2005-10-21
I get the same  thing. Though I installed it with suse93 along with 2000 pro
  my suse93 disk as  a mbr  repair tool  It  repairs the problem..But not ubuntu issue..

  U may need to  repair the MRB  from your with your fdisk under dos.

---

### Post by Chris Chan on 2005-10-22
Is that running from a DOS floppy 'fdisk /fixmbr'? I am rather a newbie to multi-booting. Specifics to fix the MBR?

---

### Post by Herman on 2005-10-22
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Chris, above is a link for the GRUB manual, so you can read it if you want and look up your error code.
Restoring your MBR with FDISK will get Windows booting again, and that's enough to calm most people down for a while and stop them panicking. You need a Windows boot disk such as 'boot98c_seoem.exe, which you can download for free somewhere on the internet.
But to fix your problem properly, (get Ubuntu booting too), you should maybe try to restore GRUB. Read what it says in the link under here, there are a couple of ways suggested.
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

I am  experimenting with GAG boot loader too, you need to install LILO on your new Ubuntu partition for that. That would mean re-installing. You might like to keep an eye on this thread, (below) to see how things develop with GAG, and may want to give that a try, but it's too early to actually recommend it to anyone yet. It might turn out to be one answer to some of the boot loader problems people are having though.
[http://www.ubuntuforums.org/showthread.php?t=79286](http://www.ubuntuforums.org/showthread.php?t=79286) 
                          That's all, from Herman

---

### Post by bluck on 2005-10-22
[QUOTE=Chris Chan]I have installed Hoary on my dell dimension 8300 (14x200 Northwood, 512MB DDR, GeForce FX5200). I installed it on the 160GB WD drive I have as primary slave. My WinXP Home install is on the 40GB Seagate primary master. Both drives (IIRC) are set to cable-select. I chose to install GRUB to the primary master's MBR. Now, it just gives me error 21 upon boot and I can't boot into XP nor Hoary. No idea how to solve this as I am a linux newbie. Help?[/QUOTE]

i found that when dual booting with windows and linux, its a good idea for your linux install to have a /boot partition, which doesnt need to be large (50MB is enough).

this way, windows doesnt do nasty things to your boot loader  trying to "fix" the MBR.

---

### Post by sirtux42 on 2005-10-23
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

------
 Thats the  error I get.. I repaird my grub through suse.
  seems linux lists  external  IDE harddrives as    sda's
  my bios isnt set up to notice if it has scsi drives..
 I might just  say heck with it.. and  install the  external HD internally .
 And  try it that way.. see if  any grub issues pop up..
 
 my  grub list things as..
    suse  hd0,5    /dev/hda6, root=/dev/had6
  windoez  hda0,0  /dev/hda1
  Ubuntu  hda2,0  /dev/sda1

---

### Post by Chris Chan on 2005-10-26
Thanks all, will try stuff once I get home at 15.30 (am at school now -- my only internet ATM) and to me the error 21 does not make sense as bios recognises both hd's. (both internal) My only theory is that GRUB might be doing this b/c the volume label on my windoze XP partition was ~33chars long and grub might not support such long labels. (the label was not my decision)

---

### Post by Chris Chan on 2005-10-28
tried using a rescue floppy. did not even recognise c: drive.

---

### Post by javiert30 on 2005-11-02
I had the same situation like you, all i did was, I put my windows xp pro cd on the cd rom, press f8 when the pc is booting, choose to boot from cd rom, follow instructions, let windows xp start windows hardware verification, then wait until it ends, and a new window appears telling  you if you want to install win xp or press r to repair, then press r, choose wich file to rapair, it must be windows so you have to press 1 then enter, it going to ask you for your administrator password, if you do not have a password press enter, a dos command prompt appears like this c:windows/ after that type help, then you going to see a list menu with commands that you can execute, look for something that says fixmrb then wrinte it in c:windows/fixmrb then enter, a  question and warning appears but dont worry press enter and it fix the mrb on your hard disk, when it finish, type exit, then your pc going to start without the grub error 21, CLEAN AGAIN.  If it works for you please send email.

---

### Post by Chris Chan on 2005-11-03
Thanks Javier, will try today and post back tomorrow. Will this keep my documents/settings?

---

### Post by Chris Chan on 2005-11-08
I have NO idea what my administrator password is. Will try the Ultimate Boot CD once I go over to my friend's house to dl and burn it.. ([http://ultimatebootcd.com](http://ultimatebootcd.com))

---

### Post by patrick295767 on 2005-11-09
With vmware i got the grub 21 error msg tooo...
  
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)
  
I hope u'll find the reason why such error 

good luck!

pat'

---

### Post by mirna on 2005-11-13
Hi,

I have the same problem.
I got a separate hard drive SCSI1 on USB port and tried to install Ubuntu on it without changing anything on my original hard drive that has Windows XP running on it. 
At the end of the installation Grub was installed and now when I try to boot the system I get the following error message:
Grub loading
Please wait ...
Error 21

I have tried to fix the problem by following the instructions on the forum, but it seems that I cannot access "grub" at all - the system says it doesn't exist. I have tried both the installation CD and the Gnoppix Live CD, and for both grub doesn't exist. Also, my win XP is not accessible. I have 2 questions:
1. How do I boot into win XP again? I do not have the win XP booting disk.
2. How do I correct the grub problem?

My drives are partitioned in the following way:
IDE1 master(hda)-40.0GB
#1 primary  38.2GB  ntfs  (set to be bootable)
#2 primary  1.8GB  fat32  (not set to bootable)

SCSI1 (0,0,0)(sda)-40.0GB
#1 primary 16.4MB  ext2  (this is the partition for \boot and is set to bootable, yet /boot is not showing)
#2 primary 1GB  swap  swap
#3 primary 39GB  ext3  (this is the partition for \ and is not bootable, and again / is not showing)

Please help!!!

Mirna

---

