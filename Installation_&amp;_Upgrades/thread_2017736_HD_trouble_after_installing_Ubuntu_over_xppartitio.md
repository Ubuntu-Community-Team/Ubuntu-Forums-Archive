---
title: "HD trouble after installing Ubuntu over xp/partitioning/format"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by sayen on 2012-07-05
I had xp home edition  with sbs2003 on a  laptop I received ( acer aspire 1642WLMi ) but I wanted ubuntu on it... 
So I installed Ubuntu "over" windows , it asked me to erase some partitions and from that moment on : error, error, error.
Like : hard disk failure ( odd as my harddisk was **totally FINE before installing**)
Like : no folders in /sys ( df -l shows missing folders) 
( error during installation : SYSTEM could not be installed)
/home did not show anything / all programs did not work etc
so reinstalled ubuntu second time - nothing better
reinstalled windows xp home - formatting c:\  got even worse
back to ubunto : got better ( /home works fine, system configuration shows up.. so some hope right?!)

I did :
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade

error during upgrade:
cups  
printer-driver-gutenprint
grub-pc
E: Subprocess  /usr/bin/dpkg returned error code (1)
(dependency problems)
warnings during installation( upgrade) 
couldn find pid (is /proc mounted?)
could not write log, openpty() failed (/dev/pts not mounted?)
etc


df -l  gives me:
df: /sys/fs/fuse/connections No such file or directory
same with /sys/kernel/debug , /sys/kernel/security, /run shm

So......... long story short

HELP ?!
I did not dare to do a fsck.. as a huge warning popped up
and.....well pretty lost now

Is there something I can do ( clean my hd, format again or new partition or something else?  just getting a new hd is not my option as it worked before installing ubuntu perfectly!)

Thanks in advance!
a lady in trouble

---

### Post by sayen on 2012-07-05
ps looked in partions through disk Utility
seems I have 3 partitions:
dev/sda1 ( EXT4)
dev/sda2 (Extended)
dev/sda5 Swap Space

dont know if it matters......to tell

---

### Post by oldfred on 2012-07-05
What did fsck on sda1 show?

Can your boot the install and updates are not working or can you only boot liveCD?

First a full filecheck:
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

Also Disk Utility can show info on hard drive status. Windows often does not show that a hard drive is failing. All I know is in Disk Utility green is good. When you click on the drive it should show a heading with Smart Data. You can also run some drive tests and it gives lots of detail which I do not understand.

---

### Post by Bucky Ball on 2012-07-06
> **sayen said:**
>  ... clean my hd, format again or new partition or ***something else***?

Exactly. When you get to the partitioning section of the install choose, 'Something Else' and partition manually.

B best to remove all partitions then start fresh (with just free space). Boot from your install media, get to the desktop, open Gparted (partition editor) and remove any partitions (you may need to right click/unmount them). Run any disk checks you need to.

Once you have that scenario, continue with the install by clicking the icon on the desktop. When you get to partition: Something Else. Good luck. ;)

---

### Post by sayen on 2012-07-07
first of all thank you for your replies

in the meantime I managed to get several things working 
Maybe I can contribute a little to the forum by telling what I did

I checked the update file and found out the main problem was 
[B]
Read error -read (5 input/output error)[/B]

so I checked the forums and found a solution:
sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm -rf /var/lib/apt/listst/*

[I]this gave me the error : list directory/var/lib/list/partial is missing
solved it with:
sudo mkdir /var/lib/lists/partial
[/I]
sudo dpkg --configure -a
sudo aptitude update

[I]error: aptitude not found
solved it with
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install aptitude
[/I]
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install -f

Since then : applications work, Sys folder is **not empty **, firefox works, I can download programs using ubuntu software center ( could not even open that one before) and I get into Disk Utility......... so perfect!!!!!!!!!!

Now only dealing with libreoffice which is telling me:
Bus error (core dumped)
I removed and reinstalled libreoffice but sadly not the solution to that.

As I was able to get into **Disk Utility** it gave me the next errors:
Reallocating sector count : failed
Current pending sector count : warning

As I understood the reallocating is not that bad ( well.. uhm..  not good but it is fixable)
the second one is not fixable
Am I right?

Would it still be a good idea to do the fsck and " something else" as you both suggested or would you both say.. let it be, back up and when it's dead you will find out soon enough as there is nothing that can be fixed?

And any suggestions on getting libreoffice working? (bus error) cant find any solutions on the forum for that........

Thank you so much for your efforts!

---

