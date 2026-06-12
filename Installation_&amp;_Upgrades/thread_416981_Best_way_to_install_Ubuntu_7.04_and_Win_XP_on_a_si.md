---
title: "Best way to install Ubuntu 7.04 and Win XP on a single HDD (Dual Boot)?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by RamenBooko on 2007-04-21
I'm starting clean, so I would be starting XP from scratch, as well as Ubuntu. What's the best way to do this? Which goes first, what partitions do I need, etc...

---

### Post by volksolwagen57 on 2007-04-21
you would need to install windows first, since they're bastards and don't see out of any of their windows. then you would need to install ubuntu which allows you to partition your harddrive to whatever size you want to use or to another hard disk, i don't know what you've got. you would have to partition your ubuntu hard drive space to ext3, whereas your xp part will be ntfs.
hope this helps.

edit: oops! haha i didn't see the whole title to your thread, just disregard the bit where i make reference to another hard disk. good luck!

---

### Post by codingmaster on 2007-04-21
Hello!

With Windows XP it does not matter, where you install Windows.

Just feel free and comfortable to use the way you prefer.

I guess, you will have at least 2 Windows drives.

It depends whether you will use primary or extended partions.
But you have to know, that you can only use up to 4 primary partions.
Extended partions are part of primary partions.

You can use for example the following structure:

primary partion 1: Big C drive
primary partion 2: extended
                           extended partion: D drive

primary partion 3: extended
                           extended partion with Ubuntu

Then you will still have a primary partition left, when you will want to resize
some partitions and make changes.

It depends, how you will setup your linux partitions.

I prefer to have:
/boot
/
/usr
/usr/local
/tmp
/var
/home

Each in one extended partion.

You will also need a swap partition for swap space.

I think as Linux beginner, it is a good way to have:
/boot - 300 MB will be enough
/
/home

This depends on the space you will have, you can also put everything in one partition.
To have /home in an own partition is a good way, when you will delete your system, you will not need to delete /home and can boot it using an other installation.

Good luck and enjoy Ubuntu!

Best regards, Georgy Berdyshev

---

### Post by bulldog on 2007-04-21
Windows must be installed first,definitely :) 
And install it on the first primary partition as well.

Your partitions are depending on how large your hdd is and what you want to do with it.

Can only give the average details for ubuntu.
Create a partition for windows as large as you want format it NTFS
Create a 10GB partition for the / [root] system format it as ext3
Create a 1GB partition for the swap and format it as swap.
Create a /home partition as big as you like for the personal data and settings,and format it ext3

If I may make a suggestion,download the GParted live cd ,it's only aproc. 50MB and burn it on a cd-r.
Boot from this cd and follow the on screen steps.
This aloud you to create all your partitions with a nice graphical interface.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If you want to have more partitions,you should create an extended partition and create logicals within.

---

### Post by codingmaster on 2007-04-21
Hmm, one thing in addition!

It will not matter for you so much, what you will use: ext3 or reiserfs.
I prefer myself reiserfs.

But ext3 is always a good choice for beginners.

There is pretty much magic and tuning you can do to a file system, the main advantage is on huge server systems - which I actually manage ;)  - where you see the performance increase because of a fs :)

So, ext3 to your partitions and the swap space is swap.

Regards, Georgy Berdyshev

---

### Post by RamenBooko on 2007-04-21
Ok, so I have an 80 GB HDD on my laptop. I'm going to use 35GB for XP, 35GB for Ubuntu and 1GB for the Swap.

Now, for the 35GB Ubuntu partition, why does some of it need to be for the /root and some for the /home ?

---

### Post by Stelakis1 on 2007-04-21
It doesn't have to be a different partition to mount "/home" it's just a matter of free space administration...
For example I use 10Gb for Win 10Gb for Ubuntu and for exerything else I have a third parition that is visible from both OSs. The proper order of installation is: 1) WinXP etc... 2) Ubuntu... because things here are easier...

---

### Post by pepsi_max2k on 2007-04-21
FWIW, I learnt all my partitioning tips from tweakhound, [http://www.tweakhound.com/xp/installxp/installXP1.htm](http://www.tweakhound.com/xp/installxp/installXP1.htm) , [http://www.tweakhound.com/xp/installxp/installxp_myway.htm](http://www.tweakhound.com/xp/installxp/installxp_myway.htm) and [http://www.tweakhound.com/xp/xptweaks/supertweaks5.htm](http://www.tweakhound.com/xp/xptweaks/supertweaks5.htm)

If it was me, I'd do like so...

During Windows install, partition 

Ram * 2, Primary, NTFS, Pagefile partition for windows (any drive letter you like other than what's already used. I'd use E: here).
Ram * 1, Primary, anything, swap file for linux.
33% of what's left, Primary / Active (bootable),  NTFS, Windows C: drive for programs.
Extended partition containing:
33%, Logical,  anything, Ubuntu.
33%, Logical, NTFS or FAT32, D: drive from data.

Then when installing ubuntu, the seconds parition (will show as something like hda2) format and mount as swap, and the fouth (hda4) format with a linux fs (i'm using jfs as it's faster with large files, you may want ext3 or reiser4) and mount as /.

Depending on whether you use windows or ubuntu most, you may or may not want the ubuntu partition before windows. Given that you likely use windows for gaming, you'll prolly want windows on an earlier partition anyway. Depending on how many programs you're gonna install, sizes for both OS partitions may vary. As I have much less programs on linux than windows (namely, less games) I actually have my windows paritition much (much) bigger than linux's one.

Don't forget to change windows' pagefile to use the pagefile partition instead of C. (I keep ram/2 on C, and ram*2 on dedicated pagefile part.). That said, the seperate pagefile partition is possibly a waste of space. the pagefile won't give much of a speed increase unless it's on a seperate drive (i think...). keeping it as part of the windows partition, although not ensuring the pagefile is at start of disk (and therefore speeding things up a tiny bit), will save any extra space in the pagefile partition to be used with the windows partition.

And as for the data partition, if you don't wanna share stuff between windows and linux (at least... not accessible from windows, you can read ntfs from ubuntu...) you could just use ntfs, but if you wanna share data you may wanna use FAT32, or create another (probably smaller) partition as FAT32 for shared data, and an NTFS one just for windows data.

Preferably you'll have another drive for backups / partition images, but if not you may wanna think about that (though frankly, there's not much point backing up stuff to a seperate parition on the same disk).

Annndd... Obviously all of ubuntu has been stored in a single parition, mounted as / . If you know what you're doing and want seperate partitions for /home, /boot, /var, etc see above. I just know that if I ever uninstall ubuntu, whatever replaces it is gonna have so many differences that saving the contents of /home is next to pointless anyway. All my useful data is on my data / shared data partition anyways :)

---

### Post by antar on 2007-04-21
My system, which has worked well on three 80GB (really 75GB) HD laptops is this.

Install Windows first.
Use GParted (get the LiveCD) to re-partition hard drive:
-resize Windows partition down to 25GB. I'd reccomend even smaller if you don't mind installing your Program Files to another partition
-make a 10GB partition for Ubunut (ext3). You won't need any more than that.
-have a 0.5-1GB swap
-have the rest (~40GB) be one FAT32 partition

In Windows, change My Documents to point to a folder on your FAT32 partition. Then, just remember to save most of your stuff to the FAT32 partition--a good idea, so it'll be accessible in both Windows and Ubuntu.

I know I'm not saying much new, just was hoping to throw in my two bits.

---

### Post by RichTJ99 on 2007-04-21
Hi,

I am in a similar boat.  I have a 80 gig drive & the current formatting is 38 gigs WinXP, 38 gigs Win Vista, Vista has the "boot" manager on it.

I would like to shave either Vista or XP down 10 gigs & take that 10 gigs to play with Ubuntu (if I can get my exchange email working & office, I may just give up on Windows completely).  I think I can use some sort of windows emulation to get office working as well.

Anyway, with Redhat, there was a formatting utility that would help you resize your partitions & go from there.  

Does the Ubuntu setup offer similar options?

Is there some particular way I should  do this with 10 gigs of space on a multi dual boot system?
Thanks,
Rich

---

### Post by RichTJ99 on 2007-04-23
Just checking if anyone knows about a dual boot XP system with Vista & Ubuntu, is that possible?

---

### Post by bulldog on 2007-04-23
Yes that is possible.
I should decrease XP rather than Vista.

To partition or resize I should recommend the GParted live cd [50MB]


[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it on a disk and boot from it.
You can partition with a GUI like Partition magic.

---

### Post by RichTJ99 on 2007-04-23
Hrmm, I know that in the past when I installed Redhat, it had an "expert" partitioning utility.  It would allow you to resize NTFS, then set the linux partitions.  I am  guessing that Ubuntu does not have that option?

As far as the boot menus, is the choice  Ubuntu or Windows, once you choose windows, its  Vista or XP?

---

### Post by mijj on 2007-04-23
I have two XP partitions (one hidden minimum systools and one main bloat).

I installed Ubuntu and the multiboot completeley messes up booting into either of the XP partitions.

I dont know if this is Grub that's messing it up, or the installation of Ubuntu that's messing it up.

Is there an alternative way to install Ubuntu that will allow me to use a different boot manager?

I'm only familiar with the dlaoded Ubuntu install CD.

---

