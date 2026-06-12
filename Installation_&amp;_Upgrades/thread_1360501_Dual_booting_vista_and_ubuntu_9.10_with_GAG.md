---
title: "Dual booting vista and ubuntu 9.10 with GAG"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by overflowing on 2009-12-21
Not so much asking for advice just logging my experience maybe it will help someone.  My scenario I have a single 500GB hard drive.

Installed Windows Vista on first 80GB
Installed Ubuntu 9.10 (Karmic Koala) on next 25GB
4GB Swap
Remainder as NTFS storage

Installed GAG as boot loader (love this program).  Vista started fine.  However when I chose Ubuntu from the GAG boot menu I would get a message "sector boot not found or invalid".  Hmmm I had done this before with a previous version of Ubuntu.  I figured it was something with GRUB not being configured correctly.

I booted using the Ubuntu LiveCD and tried to reinstall grub.  I guess 9.10 uses grub2 which I kept getting error messages and could find no one online doing what I was trying to do.  grub2 was frustrating me.  So I uninstalled grub2 and reinstalled grub as follows (this is from memory):

Boot Ubuntu LiveCD
Open Terminal
In terminal:
sudo -i
fdisk -l (to find out which partition ubuntu was installed)
mount /dev/sda5 /media/root
mount --bind /dev /media/root/dev
mount --bind /proc /media/root/proc
chroot /media/root su
apt-get purge grub2 grub-pc
apt-get update
apt-get install grub
grub

At grub prompt:
find /boot/grub/stage1
root (hd0,4)
setup (hd0,4)
quit

Rebooted.  All is well. Vista and Ubuntu can now start from GAG.  Key points:
-I couldn't get apt-get install grub to work.  It would complain something about no installation candidate and I discovered I had to do apt-get update
-For grub, most instructions tell you to do "setup (hd0)" but for using GAG you need to do "setup (hd0,4)" replacing 4 with your partition number, because you want GAG in the MBR not grub

Had to post because I wish I had this post when I was trying to get this to work for hours.

---

### Post by John_Reflex on 2009-12-21
LUV U MAN!

**U ROCK**
:guitar: :KS

---

### Post by itziar on 2010-01-31
Hello,

I was actually desperated with GAG and GRUB2 when I found your post. I've tried everything you say, but I get an error at this point: find /boot/grub/stage1.

It says the file can't be found, and I can´t continue. I'm using GRUB2 meanwhile (I've reinstalled it), but do you have any idea why this happens and how can I solve it? I'm totally newby to Ubuntu :s

Thank you very much!

---

### Post by overflowing on 2010-01-31
Well one thing is, where it says "/dev/sda5", that is particular to my setup.  It probably will be something different for you.

Also this will probably be different for you:
root (hd0,4)

You have to use the output of fdisk -l to figure out which partition ubuntu is on.

---

### Post by itziar on 2010-02-01
> **overflowing said:**
> Well one thing is, where it says "/dev/sda5", that is particular to my setup.  It probably will be something different for you.

Also this will probably be different for you:
root (hd0,4)

You have to use the output of fdisk -l to figure out which partition ubuntu is on.

Yes, I know. My Ubuntu is on sda7 and I used /dev/sda7, but Grub can't find /boot/grub/stage1.

Any ideas?

Thanks!

---

### Post by overflowing on 2010-02-01
> **itziar said:**
> Yes, I know. My Ubuntu is on sda7 and I used /dev/sda7, but Grub can't find /boot/grub/stage1.

Any ideas?

Thanks!

Yeah I think I forgot a step.  Before you chroot you also have to mount dev and proc like:

mount /dev/sda7 /media/root
mount --bind /dev /media/root/dev
mount --bind /proc /media/root/proc
chroot /media/root su

Try that and then the remaining steps.  If that doesn't work, you might also need to do install grub after the chroot like:

grub-install /dev/sda7

---

### Post by itziar on 2010-02-04
Thanks, I'll try that ;)

---

### Post by manorbarndavid on 2010-02-05
I found that the cleanest way, which has given me no problem with either Vista or Ubuntu was to install a second clean hard disk, and while installing Ubuntu on that, I had the Vista disk disconnected.  After installation and checking Ubuntu, I reconnected the Vista disk and now select which OS using the BIOS Boot menu at start up.

---

### Post by eihcet04 on 2010-12-01
Had to change a few steps to get this working for me (in red):

Boot Ubuntu LiveCD
Open Terminal
In terminal:
sudo -i
fdisk -l (to find out which partition ubuntu was installed)
mount /dev/sda5 /media/root
mount --bind /dev /media/root/dev
mount --bind /proc /media/root/proc
[COLOR=Red]cp /etc/resolv.conf /media/root/etc/[/COLOR]  (This is needed to enable networking for the apt-get update below)
chroot /media/root su
apt-get purge grub2 grub-pc
apt-get update
apt-get install grub
[COLOR=Red]grub-install /dev/sda5[/COLOR] (This was previously noted in a later post)
grub

At grub prompt:
find /boot/grub/stage1
root (hd0,4)
setup (hd0,4)
quit

#I was getting errors:   "embed /boot/grub/e2fs_stage1_5 (hd0,5)" ...failed (this is not fatal)   at the >setup (hd0,4) in grub
#so had to also run:
[COLOR=Red]update-grub [COLOR=Black](to update the menu.lst)[/COLOR][/COLOR]

#Comments / Notes: 
#1) Upon completion of the update-grub, the menu.lst file was finally generated.  I was then able to reboot only to find GAG was no longer in the MBR and GRUB had replaced it.  Fortunately it DID boot into ubuntu just fine.  I rebooted off the GAG CD and tested the Windows partitions which worked fine as well, so I reinstalled GAG from the CD and now all 3 partitions are bootable.  
#2) The resolv.conf command was key for the apt-get update to work.  For some reason that copy isn't always needed but I lost DNS resolution a few times without it. 
#3) The GAG Wiki notes a grub2 incompatibility and offers an alternative sudo grub-install /dev/sda5 command.  I tried this and would get errors about blocklists, requiring the --force option.  Using that grub2 would install into the partition and be bootable from GAG for exactly 1 reboot.  Then it would fail again.  
#4) When I had the problems with resolv.conf I booted off an 8.0.4 ubuntu live cd hoping to use the grub1 from there.  However, the chroot /media/root su doesn't work nor did /bin/bash in place of su.  Not sure why, but, it's not required that I solve that.  Might be a 32bit live cd vs 64bit install.

#Hopefully I didn't forget anything else, I think that was all of it.  I may have binded a few other directories at one point following a 'how to chroot, simple and fast' guide but I don't think that was needed just the cp resolv.conf part of that post.  

[FONT=Fixedsys]My Fdisk -l output:
[/FONT] [FONT=Fixedsys]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5104    40997848+  17  Hidden HPFS/NTFS
/dev/sda2            7170       38913   254983618    5  Extended
/dev/sda3   *        5105        7169    16587112+   7  HPFS/NTFS
/dev/sda5            9998       10994     8008402+  82  Linux swap / Solaris
/dev/sda6            7170        9997    22715847   83  Linux
/dev/sda7           10995       38913   224259336    7  HPFS/NTFS[/FONT]

[FONT=Fixedsys]#My install is on DEV/SDA6 so I adjusted the numbering accordingly.  

[/FONT]#Grub1 numbers partitions starting from 0.  So, first hard disk is 0 and first partition is 0, hd(0,0).  

#Grub2 (I read) starts at 1 for the partitions instead of 0.  Unfortunately even in the MBR, Grub2 would not detect the hidden primary install, or at least only detected one of the two Windows Primary partitions.  I wasn't sure how to modify the scripts to get it to detect all 3 and hide the non-booted windows partition when I went that route.  GAG is much simpler in this regards.

---

### Post by soyouth on 2011-01-14
Hey guys, 

I installed ubuntu10 for the first time and wanted to use gag and then couldn't understand what was happening ! Overflowing definitely saved my day by sharing this ! Still I was not able to get the apt update to work so I manually downloaded grub package from another system and I could boot from gag but still I was left with an empty grub prompt. Following every single step of  eihcet04 got me out of trouble ! 

This is very useful ! The incompatibility between gag and grub2 is often silenced.

Best

Soyouth
[URL="http://ubuntuforums.org/member.php?u=1197594"]
[/URL]

---

### Post by Airidh on 2011-07-01
Thank you, thank you, thank you so much!!!! :D.  This has been bothering me for weeks - thought I had messed up the partitioning and was preparing to wipe all 15 (XP) partitions and start again.  

I'll write to the GAG folk if I can find an address.

---

### Post by overflowing on 2013-01-28
Just confirming this still works with Ubuntu 12.10.  Recently re-installed Ubuntu over my old installation using a new ISO.  Had the same "boot sector" issue again in GAG after installing.

Thanks to eihcet04 for detailing some of the missing steps.  There were some very minor differences but you should still be able to follow them.  By default I don't believe grub2 was installed so didn't need to uninstall but I did apt-get purge grub-pc.  When installing grub it said it needed to uninstall some other grub related package first to which I just agreed.  I didn't really dig into what's changed since the last time I've done this.  I'm not even sure what version of grub is installed by default in 12.10 but I did find a reference that what every one had previously referred to as "grub2" was actually version 1.99 ([http://www.iloveubuntu.net/grub-2-20-landed-ubuntu-1210-default](http://www.iloveubuntu.net/grub-2-20-landed-ubuntu-1210-default)).  Not sure what that's about but the steps still worked for me.

Just to clarify for future readers you run fdisk -l to find out what partition your ubuntu install is on.  How do you know which one? Under the "System" column there should be one that says "Linux", use that one.  You don't want "Linux swap / Solaris" or "HPFS/NTFS/exFAT".

For me it was /dev/sda5 the first time around.  This second time it was /dev/sda6 (I think the first time I had to do partition configuration and picking with the old ubuntu installer, the new one in 12.10 auto detected my old install and handled the partition picking automatically)

---

