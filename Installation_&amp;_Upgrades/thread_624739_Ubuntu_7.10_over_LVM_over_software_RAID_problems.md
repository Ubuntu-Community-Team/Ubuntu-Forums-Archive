---
title: "Ubuntu 7.10 over LVM over software RAID problems"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by RoboJ1M on 2007-11-27
Hi,

I'm making a media server with three 500GB SATA disks in it.
Using Ubuntu 7.10 Alternate x86 CD, it fails when installing the LILO bootloader at the end of the installation. I can skip the LILO installation after it fails but I just end up with GRUB Error 15 (?)

Here is what I'm doing:

Physical drives:

/dev/sda
/dev/sdb
/dev/sdc

Partitioned:

/dev/sda1 - 50MB Bootable RAID (primary, beginning)
/dev/sdb1 - 50MB Bootable RAID (primary, beginning)
/dev/sdc1 - 50MB Bootable RAID (primary, beginning)
/dev/sda2 - ~500GB RAID (primary)
/dev/sdb2 - ~500GB RAID (primary)
/dev/sdc2 - ~500GB RAID (primary)

RAID config:

/dev/md0 - RAID1 (/dev/sda1, /dev/sdb1, /dev/sdc1) - ext2, mount as '/boot'
/dev/md1 - RAID5 (/dev/sda2, /dev/sdb2, /dev/sdc2) - LVM

LVM Config:

/dev/vg0 - LVM VG (/dev/md1)

/dev/vg0/root - 5GB XFS, mount as '/'
/dev/vg0/home - 20GB XFS, mount as '/home'
/dev/vg0/media - ~1TB XFS, mount as '/media'
/dev/vg0/swap - 4GB swap, mount as swap

Everything goes smoothly until just after all the packages have been installed.
It pops up a window asking where to install LILO (because GRUB can't do this, yes?).
This windows has two options:

/dev/md1
Manual

I select Manual and choose:

/dev/md0 (The bootable 50MB RAID1 array containing /boot)

This fails, and the installation is snafu.

After doing my homework, I'm sure this is *meant* to be possible.

1) The BIOS boots one of it's bootable drives (3) and as they are RAID1 parts, it's just a normal partition.
2) This loads the kernel, which then mounts up all the other advanced stuff and up comes the system.

Or have I got something very, very wrong?

TIA,

J1M.

---

### Post by siouzi on 2007-11-27
I'm setting up raid as well, but as raid1. I have heard of this "installer swap bug" and when I tried to set up swap using the installer, it did not work. The installer complained that the swap cannot be activated. However, there was one time when I encountered a similar situation because I remember thinking "wtf LILO this n that error, I want GRUB!"... So my advice is, try without swap, just set it to "do not use" and ignore the warning. If that doesn't help, start from scratch. Clear the raid superblocks and erase all data as a last measure.

Ironically, now I'm trying lvm on top of _encrypted_ software raid1 and it seems everything goes smoothly using the installer: setting up root, home **and swap** partitions on lvm! (Smoothly except the manual crypttab editing and initramfs building at the end...). So what can I say, except that the installer is very, very buggy with raid setups!

---

### Post by 1st-Laffer on 2007-11-27
Only registered to post my dismay at the general condition of this os..........

//Rant Start

Last time I had a play with Linux was about 8 years ago - and soon put it back down again.  Very immature product.

Have a need to setup a 1.5TB software array - Win Server 2003 - no probs, infact a doddle.  Long setup (re-sync) time though and awful write performance.

"I know" I thought.... i'll slap ubuntu on and see what that does.  Been 'playing' with the last two versions on and off for a couple of months.

Now, after around 15 hours of trying to get a software raid 5 to work I can tell you that :

A) Server (gutsy) is a shock being presented with just a command line.  Hey I'm from the pre DOS days but sheez this is 2007.  I binned that immediately... I have the need now - not in three weeks time when I have learned the CLI basics..............

B) Client - not much better.  For a completely bog standard user (docs, mail, spreadsheet maybes internet) you can get away with it.  Other than that forget it.  Heres why:

Still have to use the command line for ANYTHING important.  and even then most 'things' do not appear to work (have given up on linux SW raid 5 - it's a joke)

Package installer a joke - slick at the outset but where oh where does it install stuff so that it is easily accessible?  If your installing a GUI with an associated service/kernel patch why oh why does it not appear in something akin to 'User Installed Apps' or something similar?  After failing miserably at a command line raid 5 I decided to install LVM2 and an associated GUI - not that I ever got to use either  - couldn't find them anywhere.

Ubuntu (linux in general?) still presents the user with lots of low level crap that is not easy to understand (or for that matter get any clarification out of google) What is that directory structure all about?  Why can you even see it as it takes the sudo bastardisation to do anything with anyway.  I DONT WANT TO SEE ALL THAT CRAP - stick it in one DIR named UBUNTU or even Linux!  the vast majority out here in user land understand drives and folders - why is linux still trying to do something different?  Mount points?! Still editing the fstab (or whatever) in this day and age for basic use is a joke.

I could go on and on.  The crux is that if you want to be taken seriously (or dare I say it as valid competition to MS) you really have to make this damn thing more easily usable and by that I mean ALL the more powerful features need to be fully gui'd or at the very least - easy to follow howto's/tutorials that come with it rather than the current pisspoor crap that for example does not even mention raid.  It really does not tell you anything you need to know.  By all means keep all the techno crap that 'very' techy (or linux affiliated) users can still mess with if they want.  You really need a shell over the rest of it hiding all the 'crap' and presenting a simplified view.

To put this into perspective - on Win Server 2003 (ommitting the re-sync wait) I had a software raid 5 setup in around 15 minutes.  In Ubuntu, after 15 hours I appear to be nowhere near getting it working.  On both I had never setup software raid before.

//Rant over

About to flatten server box and look for the cheapest HW raid 5 I can lay my hands on and run it with windows.

1st Laffer.

Footnote : looks like another 8 years before I have another serious look at linux.

---

### Post by RoboJ1M on 2007-11-28
Well, I don't remember it mentioning anything about swap but I'll try it.
If you leave the swap partition as 'do not use', how do you then use it as swap once the OS is up and running?
As far as I could tell it was just along the lines of DANGER TO TEH LILO.
I'll have another go this lunch time, I'll take a photo of the screen if it errors again.
So frustrating, I really want this up and running, I'm so excited about having this machine running!

So, where are all the ubuntu uber-experts? Hello?? INSTALLER BUG?!?

Thanks,

J1M.

---

### Post by siouzi on 2007-11-28
I just tried a similar but simpler raid 5 setup with ext3 fs and lvm with just root, home and swap (should that even matter...). Swap is not an issue when put on LVM. (But bugs out if you put it on encrypted raid). I did not get any warnings about LILO and boot works fine using grub.

- created md0 raid1, sda + sdb, sdc as spare
- created md1 raid5, sda + sdb + sdc
- use md1 device for lvm
- set up lvm and it's volumes
- set md0 to /boot, ext3 format

Sorry I can't be of any help - I've only seen the LILO bug(?) once. Just try again (and ignore the swap thing).

---

### Post by RoboJ1M on 2007-11-28
That's of enourmous help actually, because it's almost *exactly* the same as what I'm going.

Which is RAID1 (bootable) + RAID5 with LVM over the RAID5.
But yours WORKED! :D

Which means that there is nothing fundamentally wrong with what I'm trying. Which is good, 'cos this stuff is EXPENSIVE.

I notice you have 2 active + 1 spare for your RAID1 and I have 3 active and 0 spare. I wonder if that makes a difference...

Thanks,

J1M.

---

### Post by siouzi on 2007-11-28
> **RoboJ1M said:**
> 
I notice you have 2 active + 1 spare for your RAID1 and I have 3 active and 0 spare. I wonder if that makes a difference...


I'm glad to hear it worked! I didn't know the installer let you activate 3 devices for raid1?! With raid1, only two devices should be used (or maybe an even number, I don't know).

Unfortunately your troubles may not be over yet, remember to test how it works when one drive fails. Before that though, remember to install the grub to sdb and sdc as well (I think the installer just installs it to sda). I found that after a drive failure, the thing just sits there doing nothing for a few minutes. Then a busybox prompt appears with a warning about /dev/mapper/<lvm name>-root. I have to enter this and hit CTRL+D to continue to boot.

```

(initramfs) mdadm -A -s

```

This is because the array becomes deactivated and you have to start it again. I have no idea how to get rid of the delay and this manual boot, i.e. to automatically activate the array after failure :(

---

### Post by RoboJ1M on 2007-11-28
Oops, no, I mean YOURS worked, mine still doesn't work.
But our two setups are very similar and therefore mine works in theory.
Which is better that not knowing whether mine will work at all.

I know I'll have MANY more problems to overcome, but hey, this is linux. If I wanted easy I'd buy a Mac and let corporate suits tell me what I should be doing.

So, I need to re-attempt the install with 2 active + 1 spare for the bootable RAID1, not 3 active. It defaulted to 2 active, but I told it to use 3.

Right, I'll retry that when I get a chance.

But I'm very glad that what I'm trying SHOULD work!! :D:D

Thanks,

J1M.

---

### Post by RoboJ1M on 2007-11-30
OK,

It's nothing to do with trying to create two primary partitions per drive.
I tried creating 1 primary and 1 logical:

/dev/sd<a, b, c>1: primary beginning 50MB RAID
/dev/sd<a, b, c>5: 500.1GB RAID

I still get the lilo error at the end of the install.

Remembered to get a shot of it this time, photo attached.

I'll try creating the RAID1 device (/dev/md0) with 2 active devices and 1 spare this time.
/dev/sdc1, which is going to be the spare. Do I set this to be bootable??

Another question:

How can I quickly blank the HDDs? It's murder getting it to forget md0 and md1. I have to re-partition the HDDs and reset several times before the damn thing forgets about the old /dev/md0 and 1. 

Thanks,

J1M.

---

### Post by siouzi on 2007-11-30
I wonder why the installer chooses LILO over grub? What happens if you go back and then manually choose to install grub? In my raid5 test setup I made all the drives identical: all had a partition set to bootable and were used for md0 /boot.

The installer won't let you delete/recreate the md devices because the array is active. To stop it hit ALT+F2 and in the console type
```

mdadm --stop --scan

```

It should stop all md devices. Or mdadm --stop /dev/md0 etc. Im not sure if the next step is necessary, but this should delete the raid information from all partitions you choose:
```

# to see all the raid devices sd1 sdb5 etc
cat /proc/mdstat

# then clear them
mdadm --zero-superblock /dev/sd1
...

```

With ALT+F1 you can get back to the installer. HTH!

---

### Post by RoboJ1M on 2007-12-03
Oooh, now THAT is going to make testing a S**T load easier :):):)

Thanks!!

J.

---

### Post by RoboJ1M on 2007-12-04
OK, I've found an Ubuntu guide on how to manually install the GRUB bootloader on sda/b/c1 using a live CD.
I'm going to try this and I've reinstalled 7.10 from scratch, including skipping the bootloader install.
One thing concerns me though, the warning message about having no bootloader says something about using /vmlinuz with the bootloader. Which is on /dev/vg0/root.

I was under the impression that the kernel lived in /boot, not '/'? If the kernel lives inside root, which is in LVM inside RAID5 then this is all a bit chicken and egg as I need the kernel to read that location?

Anyway, I'm going to try the manual GRUB install at lunchtime.

Does anybody know what the minimum set of files is and where they are located to boot the system?

Thanks,

J1M.

---

### Post by RoboJ1M on 2007-12-04
The guide didn't work, I just get Error 15 file not found for either:

/boot/grub/stage1
or
/grub/stage1

This is really annoying. I really like Ubuntu and I want it to work!!

(the guide is this: [https://help.ubuntu.com/community/Installation/FileServerWithRAID#head-b7f1ec96d06eb6d2abc4f0696b8bcf4795371467](https://help.ubuntu.com/community/Installation/FileServerWithRAID#head-b7f1ec96d06eb6d2abc4f0696b8bcf4795371467))

---

### Post by RoboJ1M on 2007-12-05
Hi,

Which release of Ubuntu did you get your bootable RAID1 working with?

J1M.

---

### Post by siouzi on 2007-12-06
I don't know if it makes a difference, but in that guide I'd use hd0 instead of hd1. If the boot partition is the first (= 0) partition on each drive, then
```

grub> device (hd0) /dev/sda
grub> root (hd0,0)
grub> setup (hd0)

grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)

grub> device (hd0) /dev/sdc
grub> root (hd0,0)
grub> setup (hd0)

```

This way when one drive fails, it becomes automagically the next hd0. With an LVM group named "lvm" and root volume named "root" the /boot/grub/menu.lst should have entries like this:
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            **(hd0,0)**
kernel          /vmlinuz-2.6.22-14-generic **root=/dev/mapper/lvm-root** ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

```

---

### Post by RoboJ1M on 2007-12-07
Yeah, unfortunately all of those commands just complain that there is no /grub/stage1 found.
and sudo grub-install doesn't work either.

As much as I don't want to, looks like this isn't going to work with Ubuntu. I'm going to try Debian Etch next week, see how I get on with that.

However, please continue to post any ideas and thanks for you help siouzi!

J.

---

### Post by RoboJ1M on 2007-12-14
Hi,

Fixed it.

Followed this guide:

[http://dev.jerryweb.org/raid/](http://dev.jerryweb.org/raid/)

4 things were different to what I tried:

1) /dev/sda,b,c1 *not* set to bootable
2) /dev/sda,b,c1 512MB
3) didn't label any of the partitions
4) left 2% of the HDDs as free space (10GB per drive!! 8@)

If I had to guess, I'd say it was 1) that made the difference.
I shall experiment and post the solution.

Thanks for all your help siouzi!

J1M.

---

### Post by breaking on 2008-01-12
I am trying to install the same thing as J1M.  I have 3 brand new 500GB PATA drives that I am using (well, trying to use) to build a new Ubuntu server.

I have the drives installed and everything goes spectacular until the boot loader.  I fail with the lilo install problem.  After reading J1M's last post, I tried reconfiguring each drive with a 50MB primary partition and a ~500GB logical partition.

I then set the 50M partitions up as a RAID1 array using sda1 & sdb1 with sdc1 as a spare.

I setup the remaining space as a RAID5 array with sda2, sdb2, sdc2 as the members.

I put LVM on top of the /dev/md1 raid array.  I created two volume groups, xyzzyVG-root and xyzzyVG-swap.

I made the swap group the swap partition (2GB) and the root partition as root (/).

So, what am I doing wrong?

I've tried to install grub w/o success (it says I don't have a partition table in /dev/mapper/xyzzyVG-root or in /dev/md0).

I've also tried to install lilo manually w/o success.  I can't edit the /etc/lilo.conf with vi because of the TERM=bterm problem.  When I set TERM=vt100, I still can't use the editing commands to change the file (arrow keys do not work, hjkl work to navigate cursor but d, and backspace in insert mode do nothing).

HELP!  Please!  I'm just trying to setup a simple home fileserver.  This shouldn't be this hard should it?

Thanks,

- James

---

### Post by RoboJ1M on 2008-01-14
Did you try this guide?

[http://dev.jerryweb.org/raid/](http://dev.jerryweb.org/raid/)

That's how I got it working. I've not yet managed to find out exactly what it was in that guide that makes it work though. I *think* it's that you mustn't set the RAID1 partitions to bootable.

Regards,

J1M.

---

