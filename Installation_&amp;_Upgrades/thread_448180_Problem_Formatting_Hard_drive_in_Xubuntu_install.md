---
title: "Problem Formatting Hard drive in Xubuntu install"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by FlyingCheese on 2007-05-18
I'm trying to install Xubuntu on an old Dell laptop (Inspiron 7000: PII with 384MB of RAM). The LiveCD Boots up perfectly, I go through the install process until I get to the "Ready to Install" screen and I notice it wants to install the ext3 partition on #1 and swap on #5. Odd, but whatever. I click Forward, and it starts up the partitioner and installs the OS, but then it fails at creating the file system:

"The ext3 file system creation partition #1 if IDE1 master (hda) failed."

It does this every time, even when I manually set up the partitions.

So I load up my Windows XP CD to see if it has any problems formatting the drive, and it does it perfectly, but Xubuntu has problems.

And the CD is fine, I checked it for errors.

---

### Post by SoloSalsa on 2007-05-18
Sorry to hear that.  Since I first used Ubuntu, I noticed that **every** installer goes berserkers with certain partition layouts.  Both graphical and alternate disks, from 6.06 to 7.04, and both Xubuntu and Ubuntu.
I found that, if you want a custom partition table, it is best to: make only swap and root partitions (and home, if it suits you), and leave the rest unformatted; install; and when you have a working desktop, then go for your desired layout, made of the unformatted space.
If you are not so picky about the disk layout, then let the installer **completely** erase and format the drive automatically.

---

### Post by FlyingCheese on 2007-05-18
> **SoloSalsa said:**
> If you are not so picky about the disk layout, then let the installer **completely** erase and format the drive automatically.

I tried this, among other things. No matter how I try to format it, it fails at the same place. The only format that actually worked right was Windows XP, but I don't want XP on this machine, it's way too slow.:(

---

### Post by jerrylamos on 2007-05-18
Feisty Xubuntu install has a bug in the partitioner.  It won't delete or new or resize partitions.

Fix is to bring up CD Live, use System, Admin, Gparted to set the partitions to what you want.

Then boot Xubuntu for install, 
select manual partitioning, 
edit the partition you want Xubuntu on.
I forget if you unmount or not, but I think so.
Set the file system to ext3
Set the mount point to /
select Format
continue with the install.
I and others have succeeded with this.  There's some more info in my post "Workarounds" on forum "Installation & Upgrades"

Cheers, Jerry

---

### Post by DUNC4N on 2007-05-23
Thanks Jerry, 

Lets just say for example that I have a 40gig hd in my laptop. 

If its not too much trouble could you elaborate on what I need to do to install xubuntu.

I.E.

Create a partition named this, and give it say 36 gb.

create a partition named this, and give it 2gb.


I'm trying to pick this stuff up as quickly as I can, but I'm paranoid about size alotment, what exactly I should name the partition, and when I'm done partitioning I should have this this and this.

Thanks so much.

---

### Post by DUNC4N on 2007-05-25
Well I installed ubuntu, while I was waiting for a reply. Could I change it to xubuntu post install?

Either way I'm more than willing to reinstall. Standing fast...

---

### Post by DUNC4N on 2007-05-25
xubuntu seems pretty cool, installed the 606 version. Still waiting for the feisty help.

---

### Post by jerrylamos on 2007-05-25
I've never tried it, but you could give a go at doing System, Administration, Synaptic Package Manager, and Upgrade from Dapper 6.06 to Edgy 6.10.  If that boots O.K., usual postings say yes, then try to Upgrade from Edgy 6.10 to Feisty 7.04.  From the postings, sometimes this works better than a new install because no new partitioning is required.

Now people vary.  I like to have a Ubuntu that works, and then a new one I'm trying out.  I do that with a 40 GB drive by partitioning 19.5 GB partiton for one Linux, partition two a 1 GB swap, then partition 3 a 19.5 GB partition for another Linux.  Whichever Linux is booted uses the same swap.  That way I can always have a running Linux like 6.06 or 6.10, and a test partition for 7.04 Feisty.  If/when the Feisty became solid, then that would free up the other  partition for trying out Gutsy or whatever other Linux is interesting.  It's easy to copy files back and forth between the two Linux partitions.  Some people have multiple partitions for one Linux which always seems to me like deliberately fragmenting.  Cheers, Jerry

---

### Post by nicefinger on 2007-05-25
Same problem .. 
As far as I remember I did like this .
Select "check disk and use free space", make only 1 partition and mount it on /.

It was when I choosed  "use the whole disk" that my problem appeared (my disk was empty ...)

---

### Post by koz-man on 2007-05-25
Nice to see people elsewhere in the world having the same fun as i on a Friday evening.  I am using an empty drive as well.  On my third time trying to install, this time i will choose the free space as you mentioned above.  I have successfully installed over a windows pc but this time it's a fresh install on a pc with no os.  

I notice an error in this process "Gnome Daemon" cannot load -- or something like that...  Any idea what that is?

I will post if selecting the free space rather than the entire drive option fixes my problem.

---

### Post by DUNC4N on 2007-06-05
Lets just say for example that I have a 40gig hd in my laptop. 

If its not too much trouble could you elaborate on what I need to do to install xubuntu.

I.E.

Create a partition named this, and give it say 36 gb.

create a partition named this, and give it 2gb.


I'm trying to pick this stuff up as quickly as I can, but I'm paranoid about size alotment, what exactly I should name the partition, and when I'm done partitioning I should have this this and this.

---

### Post by DUNC4N on 2007-06-06
Wow, I figured out that I could install it right over my kubuntu install, then remove the kubuntu.

Thanks for those that tried to help.

I'm such a nub. 


To jump on the steep learning curve, I've downloaded slackware, gentoo, freebsd, and a couple others, only way I'm really going to learn...

Currently trying SAM linux, which is pretty amazing, however I really didn't have to do anything, and thats part of the fun. ;)

---

