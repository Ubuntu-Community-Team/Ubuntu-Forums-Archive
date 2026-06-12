---
title: "Is it possible to edit my Windows NTFS partition with GParted"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by chumchum on 2008-03-22
Hello all
I've been using Wubi for a while, and loved it! To such an extent that I've decided to install a proper WindowsXP/Ubuntu dual boot, here I am booted with a gutsy live disc, but I'm having difficulty installing, my HDD is 146.05 GB, here are the partitions, as seen in GParted (I'll include jargon I'm clueless with)
N.B: In the place of the asterisk(*) there is a locked padlock.

==========================
Partition           Filesystem     mountpoint    label      size         used        unused       flags
/dev/sda1         fat32                                           6.00GiB    3.65Gib    2.35 GiB     hidden
/dev/sda2 *      ntfs              /media/HDD    HDD   143.04GiB  122.09Gib 20.95GiB    boot
unallocated      unallocated                                   7.84Mib

==========================
I want take 16GiB from /dev/sda2 (the Windows XP partition) to create a partition for linux and another GB(not sure how much I should use, recommendations will be appreciated) from there for the swap. However GParted just won't let me edit it (I think that's why there's a padlock :P) but why is it doing this? And how can I force it to allow me to edit it?
Also, being a windows user and relatively new to Linux, I'm still confused on the concept of the "Swap" partition, how big should it be? How do I get around making it?

Many, Many thanks in advance

---

### Post by tvtech on 2008-03-22
yes but I"ll make a couple recommendations.  go into windows disable system restore and virtual memory page file then reboot.  
Then defrag the crap out of that *******.
then you can change the size of your disk.
this isn't an issue with windows xp, some problems have been noted on vista

swap: there are lots of philosophies if you've got more than 2gig of ram then a gig or so for swap should be way more than enough.  


get the gparted livecd instead of using it through ubuntu
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

your going to probably want a minimum of 10 gig of space for the whole install.  some say to set up a seperate partition for /home  but I never do  "this is for ease of use when upgrading"  I just fresh install every six months I hate upgrades

---

### Post by Pumalite on 2008-03-22
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP. Choose 'resize from the menu.

---

### Post by Pumalite on 2008-03-22
If it's a laptop and you want hibernation; then: /swap=RAM

---

### Post by chumchum on 2008-03-22
Thank you very much for your quick reply =D
But one last question if I may,
If I don't want to perform a "fresh install" every six months, but rather upgrade within the OS (don't know the correct term for that is :$) will a single 16GB partition suffice?

---

### Post by Pumalite on 2008-03-22
You can do that. But is better to have a separate /home partition and do a clean install saving your /home for the new installation.

---

### Post by chumchum on 2008-03-22
OK, Thanks, so if I have 6GB for ubuntu itself and 10GB for my home, will that work?
(forgive my stupid questions, I'm not very bright with such things)
EDIT: the wiki how to doesn't give any info on how to do that, would you happen to know a good guide, if so please send a link.
EDIT 2: Out of curiosity, why does this work when I boot GParted on it's own and not using a gutsy live disc?

---

### Post by Pumalite on 2008-03-22
How to do what?

---

### Post by chumchum on 2008-03-22
Sorry for not being clear, how do I speciffically tell the installer that I want partition x to be  
for ubuntu and partition y to be the home folder, is it a flag (I don't even know what those are:S) or is it during install?

---

### Post by Pumalite on 2008-03-22
I assume you know the name of the partition you just created. Using Ubuntu Live CD, go 'Manual'. Free the space you just created, then make 'new' partition of 6000 MB, mount point '/', another new partition for /swap, mount point 'swap', the rest for /home.

---

### Post by chumchum on 2008-03-22
Thank you, I'll try this tomorrow, as it's getting late here and will come crawling back for help if I get lost (most likely scenario).
Just a few questions (you're being very patient with me, and it's very nice of you =P) what kind of file system does the ubuntu partition have to be? And can the names be totally arbitrary?

---

### Post by Pumalite on 2008-03-22
There are several. I prefer good old ext3. Swap has it's own format. Names are not arbitrary.

---

### Post by erginemr on 2008-03-22
I have also been following your thread for some time. While I agree with Pumalite's postings mostly, I believe 6 GB is too little for the root (/) partition. You should carve out more from partition Windows while you can (by emptying it a little bit more and defragging the rest of course) and spare at least 10 GB for /.

---

### Post by chumchum on 2008-03-23
OK thanks for the advice.
I'm defragging as I'm writing this (it's taking for bloody ever) and I want to be sure about some things before starting.
What makes a fresh install on a different partition better than a mere update?I would rather have a single partition, what will I lose by doing this?
will the following work out?
N.B: PC's a desktop with 1200MB RAM 
==========================
Partition      |Filesystem                  mountpoint          label        size           flags
/dev/sda1   | *see first post for info on this*
/dev/sda2   | *see first post for info on this* 
ubuntu root|  ext3                               /                       ?           10GB            ?
swap           | swap                          swap                     ?           1.5GB          ? 
home           |ext3                          /home(?)                ?           10GB            ?
==========================
You mentionned naes not being arbitrary, but I have no idea what to call them (when i say "name" I refer to the "partition" column, or though it may be label). I'm also unsure about what label is :(
What flags should I use for each partition? (I'm in windows atm so the awnser may be blatantly obvious, but I can't see the possible choices.)
Does my hoice of label matter?




EDIT: I wanted to make a neat chart, but the forum doesn't display multiple spaces alas, so it may seem messy.

---

### Post by Pumalite on 2008-03-23
Your scheme looks fine to me.

---

### Post by unutbu on 2008-03-23
> What makes a fresh install on a different partition better than a mere update?

Sometimes there are bugs that creep in when a system distribution is upgraded. Updating packages is usually just fine, but upgrading from say Gutsy to Heron will for some be a journey with some surprises. 

Doing a fresh install cuts down on ugly surprises because the developers get a chance to lay down your system from scratch. (No old config file problems, for example.) If you reserve a partition for the fresh install, you have the added benefit of not having to abandon your old system before trying out the new one. 

This is definitely a smart way to operate if you have the space and the intention of upgrading.

---

### Post by Pumalite on 2008-03-23
+1
(forgot that question)

---

### Post by chumchum on 2008-03-24
Well it seems theres absolutely no way to resize the Windows partition as long as it's "locked", it seems to be denying all forms of editing, there doesn't seem to be any way to allow resizing with Windows' disk manager, would anyone know how to resize a partition from within XP?

---

### Post by erginemr on 2008-03-24
You can resize it by downloading and booting from GParted Live CD:
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

but you need to defrag your NTFS drive from within Windows first.

---

### Post by rosegarden78 on 2008-03-24
> **chumchum said:**
> Hello all
I've been using Wubi for a while, and loved it! To such an extent that I've decided to install a proper WindowsXP/Ubuntu dual boot, here I am booted with a gutsy live disc, but I'm having difficulty installing, my HDD is 146.05 GB, here are the partitions, as seen in GParted (I'll include jargon I'm clueless with)
N.B: In the place of the asterisk(*) there is a locked padlock.

==========================
Partition           Filesystem     mountpoint    label      size         used        unused       flags
/dev/sda1         fat32                                           6.00GiB    3.65Gib    2.35 GiB     hidden
/dev/sda2 *      ntfs              /media/HDD    HDD   143.04GiB  122.09Gib 20.95GiB    boot
unallocated      unallocated                                   7.84Mib

==========================
I want take 16GiB from /dev/sda2 (the Windows XP partition) to create a partition for linux and another GB(not sure how much I should use, recommendations will be appreciated) from there for the swap. However GParted just won't let me edit it (I think that's why there's a padlock :P) but why is it doing this? And how can I force it to allow me to edit it?
Also, being a windows user and relatively new to Linux, I'm still confused on the concept of the "Swap" partition, how big should it be? How do I get around making it?

Many, Many thanks in advance


You can disable swap in Ubuntu with this command: sudo swapoff /dev/sda5.  I wouldn't use gparted, cfdisk or mkdosfs on a Windows compatible disk.  Furthermore, I don't think you should use partitions.  VirtualBox virtual machines are much better.  If you format in Linux you will destroy your Microsoft boot record.

Use the internal disk for the host OS (Ubuntu Studio and VirtualBox) and use the second disk for storing large files.  A virtual machine can be copied as one file whereas a partition is not so easily restored.

Related articles:
[http://ubuntuforums.org/showthread.php?p=4578974#post4578974](http://ubuntuforums.org/showthread.php?p=4578974#post4578974)
[http://ubuntuforums.org/showthread.php?t=277684&page=2](http://ubuntuforums.org/showthread.php?t=277684&page=2)
[http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format](http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format)

---

### Post by Pumalite on 2008-03-24
Nonsense. Use Gparted Live CD. Boot from it. Right click on XP, choose 'resize' from the menu. Then install Ubuntu, let Grub install to MBR (it will not destroy anything) and you'll have dual boot. If you change your mind later, you can restore your Windows MBR easily with your Installation Disk or Super Grub.
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by rosegarden78 on 2008-03-24
I never said automatic option didn't work, only IF use entire disk it's possible to erase.  The automatic option always worked for me.  However, in today's experience with VirtualBox and USB hard disk drives I have found the following to be true:

---Windows XP running in VirtualBox with USB support requires a Microsoft-formatted disk or else it won't be accessable in the virtual machine.

---Using a Linux formatter or partitioner will make a boot sector that is not compatible with Microsoft and Windows XP - specifically when running in VirtualBox with USB support.

The related articles explain the situation I solved more clearly.  I'm sorry if this is slightly off topic but I use Gestalt reasoning, so the rest of the articles will bring this one into context.  I remember my first time with the installer I didn't know what / or swap meant!

Related articles:
[http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format](http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format)
[http://ubuntuforums.org/showthread.php?p=4578974#post4578974](http://ubuntuforums.org/showthread.php?p=4578974#post4578974)
[http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361](http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361)

But I meant what I said about not using multiple partitions and boot because you can backup and restore a virtual machine as one .vdi file whereas restoring a workable XP installation from a disk partition is not so easy.

---

### Post by chumchum on 2008-03-24
OK, thanks
I'll listen to  Pumalite as he seems like he knows more about Linux ;)
Will try that tomorrow (tried it before, but got scared off by it's apparent "complicatedness").
But if something somewhere is denying GParted and Ubuntu Installer's auto partitioner the right to edit the NTFS partition, why would this live CD (which by my understanding, is nearly the same GParted as the one I open in the Ubuntu live CD) have editing rights?

---

### Post by Pumalite on 2008-03-24
It works with unmounted drives/partitions.

---

### Post by rosegarden78 on 2008-03-24
Sun Microsystems acquired VirtualBox from Innotek for millions of dollars - it's worth downloading and works on Windows or Linux as the host.  Knowledge of Linux has really nothing to do with using a partitioner.  Just launch sudo gparted or sudo cfdisk if that's what you really want to do.  GParted is a little more user friendly.  But I don't have to explain myself to anyone.  When you install a XP virtual machine and attempt to connect a Linux formatted drive you'll see what happens.  :)

Of course Gparted can resize a partition in NTFS and Ubuntu can read NTFS!  Didn't Pumalite say use the Guided Resize Disk option when installing Ubuntu?  The installer uses Gparted so you can do it automatically, by hand, or use entire disk but I'm saying VirtualBox is great because the VDI machine works independent of the host.  IE: A virtual machine you make in Linux will work in VirtualBox for Windows.  You are welcome to try your hand at dual-booting and that's great.

Sun Microsystems acquired Innotek VirtualBox for millions of dollars...but the download is free.

Related articles:
[http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format](http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format)
[http://ubuntuforums.org/showthread.php?p=4578974#post4578974](http://ubuntuforums.org/showthread.php?p=4578974#post4578974)
[http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361](http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361)

---

### Post by Pumalite on 2008-03-24
> **chumchum said:**
> OK, thanks
I'll listen to  Pumalite as he seems like he knows more about Linux ;)
Will try that tomorrow (tried it before, but got scared off by it's apparent "complicatedness").
But if something somewhere is denying GParted and Ubuntu Installer's auto partitioner the right to edit the NTFS partition, why would this live CD (which by my understanding, is nearly the same GParted as the one I open in the Ubuntu live CD) have editing rights?

I'd recommend you to leave at least 20 GB for Ubuntu. In that new space; make 3 new partitions:
10 GB for '/'
1 GB for /swap
The rest for /home
Install and go 'Manual', choose already prepared partitions and press 'Forward'

---

### Post by erginemr on 2008-03-25
> **chumchum said:**
> OK, thanks
I'll listen to  Pumalite as he seems like he knows more about Linux ;)
Will try that tomorrow (tried it before, but got scared off by it's apparent "complicatedness").
But if something somewhere is denying GParted and Ubuntu Installer's auto partitioner the right to edit the NTFS partition, why would this live CD (which by my understanding, is nearly the same GParted as the one I open in the Ubuntu live CD) have editing rights?

> **Pumalite said:**
> It works with unmounted drives/partitions.

The GParted from Ubuntu Live CD works too, if you enter "Gnome Main Menu -> Places -> Computer" and right-click on the Windows partitions and unmount them  if they are already mounted. 

But GParted from Ubuntu Live CD is somewhat crippled in that it needs an extra package. For it to be able to partition NTFS drives, you will need an active internet connection to install the **ntfsprogs** package from Synaptic.

CORRECTION: It seems ntfsprogs is installed by default. I will boot a Live CD, play with it for a while and post back.

---

### Post by erginemr on 2008-03-25
OK. Here is what I have found. Ubuntu Live CD has that package already installed and GParted (ver. 0.3.3) can indeed create and resize NTFS partitions. But it crashes often during this process so is unreliable. 

The GParted Live CD however packs the most recent version (ver. 0.3.4x), via which I had successfully resized my windows partition several times in the past. The bottom line is; you should go for GParted Live CD.

---

