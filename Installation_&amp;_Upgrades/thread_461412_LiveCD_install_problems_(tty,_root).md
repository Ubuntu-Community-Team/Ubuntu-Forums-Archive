---
title: "LiveCD install problems (tty, root)"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by vuroth on 2007-06-01
First experience with ubuntu.  I'm trying to install overtop of my existing WinXP, single HD system.  Taking the plunge, as it were.

I get this error, which seems to be quite common, based on google searches:

/bin/sh: can't access tty: job control turned off.

Based on [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864/comments/13"),, I try adding break-top to the live CD init, do **modprobe piix**, then **exit**.   Oh, I also removed **splash** from the kernel/livecd init.  Now, I see this:

/bin/sh: can't access tty; job control turned off
(initramfs) modprobe piix
(initramfs) exit
[ ##.#####] Buffer I/O error on device hde, logical block #  (x8)
cp: unable to open '/root/var/log/': no such file or directory
mount: Mounting /root/dev on /dev/xstatic/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-3ubunu3) Builtin shell (ash)
Enter 'help'...

/bin/sh: can't access tty: job control turned off.

I ran the checksum thing on the .iso before I burned it, so I'm inclined to think the CD is ok.

What's my next step forward?

V

---

### Post by r3g on 2007-06-01
Hi,

I had the same problem a few days ago.

Googling told me that there were issues with installing from the live cd for some systems. So I donwloaded the "alternate" desktop cd witch boots to a menu where you choose the text based installer. This worked fine for me and everything worked perfectly after that (even my RT2500 wifi card which I had spent weeks trying to configure under Fedora Core 6 previously).

To get the alternate CD just go to the Ubuntu download page - [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
Then check the box just under the "Start Download" button before downloading.

Hope all goes well,

Richard.

---

### Post by vuroth on 2007-06-01
Thanks.  The alternate CD gets me further.  Now, the partitioner is complaining about hde errors....  :(

EDIT:

The attempt to mount a file system with type ext3 in IDE3 master, partition #1 (hde1) at / failed.

With guided partitioning, I get abort/retry/ignore errors on hde3.

Bleh.

V

---

### Post by vuroth on 2007-06-01
Some more info, based on my reading:

[ ##.#####] Buffer I/O error on device hde, logical block # (x8 )  is still occurring
Single 30.8GB Quantum Fireball IDE HD, as primary/master.  Asus A7V mobo.  HD is AUTO.  CD/RW is Secondary/Master, I believe.

The Buffer I/O and abort/ignore/retry errors to HDE are worrisome.

V

---

### Post by vuroth on 2007-06-01
I found the ctrl-alt-f4 page.  Lots of hde1 errors here.

partman:  Reading all physical volumes.  This may take a while...
partman:  /dev/hde:  read failed after 0 of 2048 at 0:  Input/output error
partman:  /dev/hde: read failed after 0 of 2048 at 30839472128 Input/output error
partman:  /dev/hde: read failed after 0 of 2048 at 0: Input/output error
partman:  /dev/hde1: read failed after 0 of 1024 at xxxxxx
partman:  /dev/hde1: read failed after 0 of 2048 at 0
partman:  /dev/hde5: read failed after 0 of 512 at xxxx
partman:  /dev/hde5: read failed after 0 of 2048 at 0: Input/output error
partman:  No volume groups found
kernel:  end_request: I/O error, dev hde, sector 0
kernel:  end_request: I/O error, dev hde, sector 63
kernel:  end_request: I/O error, dev hde, sector xxxxxxxx

I may try to find some other way to partition or unpartition the drive  :(

---

### Post by vuroth on 2007-06-01
I was able to use another distro (Mandrake 8.0 CD I had lying around) to partition and format.  partman still gave retry/ignore/abort errors, so I suspect that partman's guided partition selection didn't take, but we'll see.

I do find it puzzling that a 5 year old distro would have an easier time repartitioning my drive than a new one.  Still, whatever works....

V

---

### Post by vuroth on 2007-06-01
got as far as grub.  Simply could not install grub or lilo to the mbr.  I sense a recurring theme here, but can't quite figure out what it is.  ubuntu insall doesn't like something with my hard drive setup...somehow.

Ended up selecting no bootloader, so now I have a nice install of ubuntu which won't boot.  I'd use the live CD but, of course, I can't boot the live CD either....

I'm getting close to being stumped.

V

---

### Post by vuroth on 2007-06-01
Apologies if I'm spamming, but I'm hoping that as I gain more info, someone will be able to help me.  Alternately, maybe this info will help the next person.

I went back to the live CD.  The Boot from library disk, then keep pressing ENTER trick worked, to a point.  I got to do the normal install.  No errors popped up until GRUB, which is of course fatal.

I suspect that the same errors occurred, but were masked, but maybe not.

V

---

### Post by vuroth on 2007-06-02
gparted won't apply a disklabel - gets an error

sudo fdisk -l /dev/hde
Buffer I/O error on device hde, logical block 0
Buffer I/O error on device hde, logical block 1

At this point, I have 2 guesses:
1. Some BIOS HD setting is something ubuntu and friends do not like
2. My HD is corrupt, but in a way that Windows and Mandrake tolerate, and ubuntu doesn't.

Crossing my fingers for 1.....

---

### Post by r3g on 2007-06-02
Wow Vuroth, you've been busy since I logged on yesterday!

This is beyond my knowledge of Ubuntu, but if you look at some of the post titles in this forum, there seems to be an awful lot of poeple having trouble getting 7.04 to boot after install. I'm thinking that it's more likely to be something that Ubuntu doesn't like about the current drive configurations rather than an epidemic of bad sectors affecting a large proportion of people installing Ubuntu.

I'm not sure whether this would help or not, but have you considered using a drive wiping utility to clean the drive before re-partitioning. I use D-Ban - [http://dban.sourceforge.net/]("http://dban.sourceforge.net/")

Then, try using the manual partitioning to set up Ubuntu.

Richard.

---

### Post by wpshooter on 2007-06-02
Might want to try **KILLDISK** program to** WIPE** the drive completely clean and then might want to consider using a WIN98 boot diskette to use **FDISK** and **FORMAT** to prep the drive before attempting to install Ubuntu again.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by vuroth on 2007-06-02
Thanks.  Giving it (DBAN) a try now.

---

### Post by Topsiho on 2007-06-02
1. I am puzzled about hde, which would indeed be the master on IDE3. What puzzles me is that as far as I know (which is not véry far) most computers or all computers have only two IDE connectors. So that only hda, hdb, hdc and hdd are possible. Forgive me if I am wrong. Then I also discovered that Feisty treats them as SCSI drives, which would mean sda, sdb etc. I think that then sde is possible, just as sdf etc.

2. I am (was) interested in this same problem as I experienced this too on one of three computers, ONLY with Feisty Fawn (the older distro's of Ubuntu all installed without any hitch). I read somewhere that the installer of the Live CD was optimizing the boot process by doing things in parallel, which I guess on some hardware causes timing problems, things not being ready when expected by some process. Which sounds credible to me as the booting process of Feisty really is fast, when it works.

3. I have also read somewhere that the problem occurs when more than one hard disk is present. The solution, if this is true, is to remove temporarily all disks except the one on which you install, and adding the removed disks later. Add them in /etc/fstab.

4. What I did and this worked without any hitch was using the alternate disk. This one has another installer, a text one, which is just as easy to work with as the graphical installer of the Live CD (only less fun, as with the Live CD the installer lets you do anything with your computer in the mean time, just as surfing, mailing, playing a game).

Well, I hope this information can help you straighten out your difficulties, I almost forgot:

5. You could try install the previous version, which is Edgy Eft (6.10). After doing all the updates (which will be many) you can then try and upgrade to Feisty Fawn, just using the upgrade possibility in th Update program. You will need much diskspace if you do that, for the download may amount to that of two CDroms (in my case over 1000 MiB, 1331 packets), which will be stored in in some cache in /var, and you will need much time and patience, as in fact this is a tremendous large update of the program.
(I did this on an other computer just to give it a try)

ah,

6. It is a good idea, I found, to do the partitioning before the installing, using the GParted Live CD, which you can download as an .iso (Google for it) and burn it, just as you maybe did for the Ubuntu .iso(s). When installing Ubuntu, it's little bed is there, ready for it.

Good luck,

Topsiho

---

### Post by Topsiho on 2007-06-02
I discovered the reason for your hde, in another post in this forum:

p://ubuntuforums.org/showthread.php?t=456662&page=46: 

"The problem is, that the updated kernel apparently attempts to address my SATA disk as hde (which, conceptually, would be "the third IDE interface master"). In fact, this is exactly the same behaviour that I saw under earlier Slackware releases that didn't yet support SATA: They simply assumed that the SATA interface was an extra IDE interface--which won't work."

It appears that you have at least one SATA disk that is not recognized as such.

Topsiho

---

### Post by vuroth on 2007-06-02
What a difference!

I ran D-BAN, cleaned up the HD completely, and then reran the alternate install CD.  No Retry/Ignore/Abort errors, partition ran smoothly, and grub installed no problem.

Not really clear why ubuntu instlal couldn handle what was there, but nonetheless, thanks for the excellent advice!

V

---

### Post by r3g on 2007-06-02
Glad to hear that you're up and running now.

Just out of curiosity, I tried putting a spare 40gb Segate ATA drive into my machine and installed 7.04 onto there and it refuses to boot ( "can't access tty: job control turned off" ). I tried both a live cd install and the alternate cd install and both give the same error. Yet my Excel Store 80Gb ATA drive works fine.

There's an official bug listed along the same lines as this;
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084")

It makes references to the way that 7.04 sees different types of drives in different ways.

So it would seem that a successful install is pretty much a lottery of the right combination of hardware.

Maybe later versions of Ubuntu will make the process somewhat easier for us all !

Richard.

---

