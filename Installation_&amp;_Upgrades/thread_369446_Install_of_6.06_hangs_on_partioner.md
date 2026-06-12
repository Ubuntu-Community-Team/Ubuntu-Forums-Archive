---
title: "Install of 6.06 hangs on partioner"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by beaversqueezer on 2007-02-24
Everything is fine from the mailed version of 6.06 until it starts the partioner and it hangs at 50% and won't go any farther. I erased the HD before starting so it was clean.I got 5.10 to install OK before this. Any suggestions?

---

### Post by gerrit on 2007-03-22
Hi,

Want to tell I´m having just the same problem installing Xubuntu 6.06 from the live CD on a IBM600e laptop (~350MHz P-II with 130MB ram).  The system is verrrry slow, *and each time it hangs when starting the partinioner* just as with you. 

I tried with a complete blank HDD (so removed all partitions with dos fdisk), also with one partition with DOS-6 installed (1GB), and also with two partitions (one Suse 10.0 and the other DOS-6), ...

But each time it takes a very long time to get to the start of the partitioner (step 5 in the installation process) and when it starts it hangs. Like with you most, of the time at 50%, but I also saw 64 %. I waited 1 hour and then aborted by unplugging the batteries. (nothing else helps, that good it hangs!)

I ran the check on the live-CD and all checksums are OK. The PC works, it worked under Suse and good old DOS (though the network adapter did not). 

If you have a fix for this, please let me know, I really would like to try Xubuntu on this somewhat older machine!

regards
Gerrit

---

### Post by wpshooter on 2007-03-22
IF you do not have anything on the machine that you need to keep then consider WIPING the drive competely clean with this program and then try the install again.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by gerrit on 2007-03-24
Thanks for the tip, it could very well be that something was left on the HDD.  I ran killdisk under dos, and then removed all partitions. Ran life install 6.06 LTS again, but did not work. Than created a few partitions with fdisk 2GB each (largest possible with dos-fdisk)  and tried once more. Again the instalation stuck at the partitioner, but now somewhat further. 

Is there a way to install from the command line? It looks like the installer in the grafic environment "eats" all the resources on my little ("only" 130MB ram) PC.  If there is, how do I perform such an installation?

regards, Gerrit

---

### Post by bulldog on 2007-03-24
Try the 'alternate cd ' it's less resources consuming.

To partition your drive before you install,you can use the GParted live cd,it's only 30MB download.
Boot from the GParted live cd and you'll have a graphical partitioner like PM.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by gerrit on 2007-03-24
Yesyesyes! Thanks for the tip. The alternative download works perfect. Textmode..., love it ! (I know, I´m an old pre-DOS fossile from when 16kB core was really top of the bill)

In text-mode the install is really fast. Did not need to run the separate partition tool you mentioned, the Xubuntu partitioner worked well. But still I´ll write the URL down for future reference.

The system has been is installed, and now I´m going to struggle with the network- and sound-system, which seem to be nasty on my thinkpad 600e. Also the video is slow, perhaps installing a better driver will help. Still work to do!  I´ll go and read what people write about these items on the fora.

I wonder why the Live-CD-Install did not work on my system, but I´m afraid I would not understand the explanation.

thanks again for the alternate CD tip!
Gerrit

---

### Post by bulldog on 2007-03-24
The live cd is a nice item to try an OS the easy way.

I always use the alternate cd to install,you know why :) 

I'm sure you'll get all your hardware to work.

Welcome to Ubuntu and enjoy.

---

### Post by beaversqueezer on 2007-04-08
Where do you find the alternate cd? I'm guessing it's an ISO image but I'm not good with command lines as started into pc's with Windows 95. I don't even know how to use dos. Would I be able to install this version? Even the upgrade to 5.10 that puts edgy hangs at 386 image I believe it is. I thank you all for your patience and help for this linux newbie.

---

### Post by bulldog on 2007-04-08
> **beaversqueezer said:**
> Where do you find the alternate cd? I'm guessing it's an ISO image but I'm not good with command lines as started into pc's with Windows 95. I don't even know how to use dos. Would I be able to install this version? Even the upgrade to 5.10 that puts edgy hangs at 386 image I believe it is. I thank you all for your patience and help for this linux newbie.

The alternate cd is very easy to install,just answer a few simple questions and continue.
You don't need any command line language to install.
Type in a google search box 'Ubuntu alternate cd' and you'll find a location near you.
You have to make a choice which release you want to install.
If you're totally new to ubuntu,I suggest the Dapper Drake 6.06,or the Edgy Eft 6.10.
Don't go for the Feisty Fawn7.04 cause it's still Beta.
The safest choice would be 6.06.

---

### Post by Unclown on 2007-04-08
> **beaversqueezer said:**
> Everything is fine from the mailed version of 6.06 until it starts the partioner and it hangs at 50% and won't go any farther. I erased the HD before starting so it was clean.I got 5.10 to install OK before this. Any suggestions?


I understand (corrections appreciated) that there are several known issues with the Ubuntu Dapper (6.06) Live CD Install:

1) Apparently there are issues (crash?/install fails?)if you try to do the install, and you have less than 256MB RAM.

Ways to fix this:

Not the easiest, basically you need to sort out your partitions, and end up with a mounted and working 'SWAP' partition.

I.e. as root:

Cfdisk ==> make a swap partition; 'cfdisk /dev/xxx' (Don't forget to make sure the partition table lists it as type 'Linux Swap/82?'
Format Swap partition; 'mkswap /dev/sda3' etc.
Use swap partion; 'swapon /dev/xxx(x)' (e.g. 'swapon /dev/sda3')


2) I believe that there is/was a bug? in GParted, that if you used one of the 'Back' buttons anywhere in the process, this would bomb out the install.

Ways around this:

Once booted into the Live CD, open GParted (Or, Terminal==> Root User==>cfdisk) and manually configure your drive(s)/partition(s).

THEN run the install, and when GParted starts, choose to manually do your partition table.

Specify which partitions are linked to which mount point/etc (SWAP, '/', '/home', '/boot', etc.).


HTH.

---

### Post by bulldog on 2007-04-08
> **Unclown said:**
> I understand (corrections appreciated) that there are several known issues with the Ubuntu Dapper (6.06) Live CD Install:

1) Apparently there are issues (crash?/install fails?)if you try to do the install, and you have less than 256MB RAM.

Ways to fix this:

Not the easiest, basically you need to sort out your partitions, and end up with a mounted and working 'SWAP' partition.

I.e. as root:

Cfdisk ==> make a swap partition; 'cfdisk /dev/xxx' (Don't forget to make sure the partition table lists it as type 'Linux Swap/82?'
Format Swap partition; 'mkswap /dev/sda3' etc.
Use swap partion; 'swapon /dev/xxx(x)' (e.g. 'swapon /dev/sda3')



2) I believe that there is/was a bug? in GParted, that if you used one of the 'Back' buttons anywhere in the process, this would bomb out the install.

Ways around this:

Once booted into the Live CD, open GParted (Or, Terminal==> Root User==>cfdisk) and manually configure your drive(s)/partition(s).

THEN run the install, and when GParted starts, choose to manually do your partition table.

Specify which partitions are linked to which mount point/etc (SWAP, '/', '/home', '/boot', etc.).


HTH.

Thanks for the input,but we're talking about the alternate cd and not the live cd anymore.
You're replying on a 6 weeks old issue.:)

---

### Post by beaversqueezer on 2008-01-12
Got it bulldog and thank you for the help.I appologize for taking so long to say that but you're right about the alternate cd.Thank you again,beaversqueezer

---

