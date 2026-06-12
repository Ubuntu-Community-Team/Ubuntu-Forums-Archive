---
title: "/bin/sh: Can't access tty; Job control turned off"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by Styan on 2006-11-04
I've searched and tried many methods that are already listed on these boards to no avail. Any help appreciated!  Thanks in advance!

So tonight I decided to update my 6.06 box to 6.10. Boy was that a mistake!

Using the foolproof updater (gksu "update-manager -c") command I waited 3 hours for all of the actions to complete, and I'm told to restart. Ok no problem, ... dapper shuts down, and up comes the new splash screen. The progress bar makes it about 1/8th of an inch across the screen and wham! I get this:

```

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

My commands at this interface are very limited and theres not much I can do. (That I know anything about.)

If I press CTRL+ALT+F1, I see the following:
```

  Booting 'Ubuntu, kernel 2.6.17-10-386'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmliniz-2.6.17-10-386 root=uuid=9c4db707-6051-46b2-8dd6-3f7c7ae0fb95 ro quiet splash
  [Linux-bxImage, setup=0x1c00, size=0x17e851]
initrd /boot/initrd.img-2.6.17-10-386
  [Linux-initrd @ 0x1f976000, 0x6791c0 bytes]
savedefault
boot
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```

There are no other CTRL+ALT+F# combos other than F1 and F8 (F8 returns me to the (initramfs) prompt.

Any insight on to what I can do to get this box back up and running would be great! (Hopefully without having to re-install.)

Thanks,
Styan

---

### Post by K.Mandla on 2006-11-04
Hmm. I had thought this problem was confined to live CD installs. This is the first time I've ever heard of it after an upgrade.

I don't know if you've seen this thread already, but supposedly someone fixed this problem there.

[http://www.ubuntuforums.org/showthread.php?t=279884](http://www.ubuntuforums.org/showthread.php?t=279884)

Edit: It might just be that Grub is pointing at the wrong partition, but I still suspect is the changeover in tty handling that happened between Dapper and Edgy. Just thinking out loud, I guess. ... :-k

---

### Post by Styan on 2006-11-04
I'll have a go again at that thread when I get home. 

My issue is when I'm at the (initramfs) prompt, an 'ls' doesn't show any files from my hard drive's file system. So maybe grub is pointing to the wrong place... Which then (perhaps a stupid question) where do I go to check to see where it's pointing? is that in the inittab file?? 

The other thing I've read about is for some the i386 kernel works and others it doesn't and the same for the generic kernel.  If I look where I think the kernels are... I only see the i386 one.  

Very confused! Like I said, I'll take a stab at the options in that thread when I get home and post my results.

Styan

---

### Post by Matthewb57 on 2006-11-04
I'm not very technical with linux yet, but I can get things to work sometimes.  I had this same issue except mine came about in a different way.  The only thing I noticed was mine just happened one time after I rebooted my computer after I "resumed" it from sleeping and things were screwed up (I have a laptop).

After the reboot I had those above issues.  I was playing around, trying some things like others stated in other posts.  What I found was that everything was intact on my partition.  I could mount it, search all files, and they were all there.  Booting from a live CD I checked again, and yes, everything looked good.

Anyways, I tried manually booting though grub (using commands) which showed successful, except when the kernel was booted.  So I figured maybe the kernel was screwed up somehow.  After verifying I could mount the drive successfully  all the time I decided to just copy the kernel off the live cd and then proceeded to boot from that kernel (which would be the older one in my grub).

**And here I am now posting this post.  So this worked**...  I do have to now get the latest kernel working again that my system has which is:
2.6.15-27-386

The one I copied was 2.6.15-26-386 off the live CD.  Maybe the corruption happened with an upgrade to that kernel somewhere... I don't know.  All I know is both 2.6.15-27-386 and 2.6.15-26-386 residing on my hd were somehow corrupt or something.  Selecting regular or "recovery" proved unsuccessful

What I'm going to do now is restart and try loading the new kernel again (without deleting and modifying yet) and see if I have the same issue.  If I do, I'll look at removing it and getting the update again.

Hope this helps someone...and I'll post my results shortly

-Matt
Ubuntu 6.06

---

### Post by Matthewb57 on 2006-11-04
Okay...so now my other kernel (2.6.15-27-386) is working fine too (just booted and I'm posting this post right after).  Weird... could something have been corrupted based on a crash of my system and then restored after one successful boot using that live cd copied kernel?

Anybody have any ideas about this?

Well, everything is okay now.  Don't know whether the solution above can really help, but the only thing I did was the above and it worked right after. No harm in trying...

Good luck!

---

### Post by K.Mandla on 2006-11-04
Strange stuff. I wish I could reproduce this error so I could tinker with it. :-k

If you can describe what you did to work around this issue, the folks who find a bug report for it might thank you.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/59792](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/59792)

Cheers and thanks.

---

### Post by Styan on 2006-11-04
Alright! It was the same issue as in one of the previous threads, where the GRUB was pointing here: root=/by-uid/[whole bunch of hex code] rather than: root=/dev/hda1 just edited the line to show /dev/hda1

Prior to my post here, I had no idea how to get into the Grub ... so I started randomly hitting keys (like you do F8 for getting into the windows "grub" lol)  btw, for ubuntu its 'esc' :p

Thanks for all your help guys! Hopefully this will help anyone else with the problem.

---

### Post by redmarshall on 2006-11-04
"Styan" You are very much apreciated.  I searched for hours trying to get edgy to boot right and you have one of the most simple ideas.  it worked!  THANK YOU!

---

### Post by Styan on 2006-11-04
Glad I could be of assistance. I too was bewildered as to what I had to do to get it to work.  Make sure once you get it booting correctly you re-write the commands in the menu.lst file.

---

### Post by Shamlou on 2006-11-09
I had installed ubuntu and was using it normally. One day I was installing Frozen bubble (the game) and I left it to download and install packages, because it was going to take 40+ minutes. We were going out that night and I had forgotten that I was installing something and just turned it off (pressed the power button which does the logout and shutdown automatically). It was the moment I pressed the power button that I realized I had something going on, but it was too late.

The next morning when I turned the computer on. ubunutu wouldn't start. It said: "/bin/sh: can't access tty; job control turned off" Then it would give me "#" on the next line where I can't type anything.

I've been searching forums for some suggestions to people who have had the same problem. Unfortunately, I haven't ran across anything that has helped.

My friend said that I should just reinstall the whole thing. I would, but I don't want to. I don't have any important files that I would lose by reinstalling. But I will feel sorry for losing all my hours spent on customizing my ubuntu (desktop, programmes, etc.). So, I figured that there must be some way to avoid total reinstallation.

I thought maybe I could see what's going on in the system by using the ubuntu live CD and access my hard drive from it, but I don't know how to mount my hard drive. And when/if I get access to my HD with the ubuntu live CD what exactly should I check/change/edit ?

I've used linux for many years, I know the basics, but I'm nowhere near as good as I would like to be. So, I would appreciate the help. Helps me learn at the same time.

I have two HDs in use right now. One is a Master (Ubuntu) and the other a slave (Windows). I don't know if this helps/complicates the situation.

Thanks for your help in advance.

---

### Post by Styan on 2006-11-09
First thing to check is if your Grub is pointing to the right place.

Use escape when booting to access the Grub.

If that doesn't do it repost here.

---

### Post by Hollunder on 2006-11-09
Hi,
I'm in the same initial situation as Styan (upgrade from 6.06 to 6.10) and I get the same error: /bin/sh: can't access tty; job control turned off

What I did: 
I checked menu.lst and it pointed to the wrong place (0,2 instead of 0,1)
I already corrected this, so it's not the problem.

I checked /bin and I found:
sh [pointing to] dash
as well as
sh.distrib [pointing to] bash

I'm rather new to ubuntu, so I don't exactly know what's going on. I guess it could be some bash/dash-problem.

Any help is appreciated.

---

### Post by captgadget on 2006-11-09
I just encountered this same problem and I had a USB Flash Drive in at the same time. I removed the flash drive and it booted right up. So I guess you might check for that.

---

### Post by Shamlou on 2006-11-10
This is what a part of my menu.lst says:

```
title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot
```

Does this help?

---

### Post by Hollunder on 2006-11-10
Shamlou, it looks good [to me at least]

I just solved my problem.

menu.lst pointed to 0,2 instead of 0,1
and
menu.lst has a line called: boot by uuid, and the following number pointed to the uuid of mz swap partition. I simply had to change that number to the one of the boot patition.

Thanks, until next time ;)

---

### Post by Shamlou on 2006-11-10
My menu.lst doesn't seem to have that line : **boot by uuid**
Where should it be? Should I add it somewhere?

Thanks.

---

### Post by raja on 2006-11-11
Hello,
I have the same error while booting, except that this is in a client machine which is PXE booting off a LTSP server running on a host with Edubuntu edgy. Cant believe it is not related. Any ideas on what I could do?
Thanks ina dvance

---

### Post by mld4165 on 2006-11-11
hi all

This machine is a dual boot. Windows XP and Kubuntu. 6.06 ran fine since it first came out.

I upgraded from LTS 6.06 to 6.10 by using the following instructions:
Upgrading from 6.06 LTS

Users of Kubuntu 6.06 LTS can upgrade to 6.10 over the internet by following these instructions:

    * NOTE: This procedure upgrades your system over the Internet, which requires a large download of several hundred megabytes.
    * In Konqueror go to /etc/apt, right click on sources.list and choose Actions -> Edit as Root
    * Change all instances of dapper to edgy
    * Launch a console with KMenu -> System -> Konsole
    * In the console run: sudo apt-get update
    * In the console run: sudo apt-get dist-upgrade and follow the prompts to upgrade
    * In the console run: sudo apt-get install kubuntu-desktop python-qt3 python-kde3 ubuntu-minimal and follow the prompts to install
    * Reboot your computer


I now get this error when I now boot:

busybox
/bin/sh: can't access tty; job control turned off

I can mount the drive with usb pen drive running dsl linux. I checked the fstab and the entires appear to be correct.

output of fdisk -l

Disk /dev/sda: 1024 MB, 1024966656 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/sda1   *           1         125     1000912+   e  Win95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(123, 254, 63) logical=(124, 155, 63)

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        9541    35680365   83  Linux
/dev/hda3            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap

output of fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

output of menu.lst:
title      Ubuntu, kernel 2.6.17-10-386
root      (hd0,1)
kernel      /boot/vmlinuz-2.6.17-10-386 root=UUID=b15b73d2-1df8-4404-a73c-278e4975d678 ro splash
initrd      /boot/initrd.img-2.6.17-10-386
savedefault
boot

title      Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root      (hd0,1)
kernel      /boot/vmlinuz-2.6.17-10-386 root=UUID=b15b73d2-1df8-4404-a73c-278e4975d678 ro single
initrd      /boot/initrd.img-2.6.17-10-386
boot

I have changed the kernel line to read root=/dev/hda2 but I have had no luck.

CD rom is broken in my laptop so I need help to fix.

thanks
Matt

---

### Post by macogw on 2006-11-11
I'm getting this error now.  I upgraded as soon as Edgy was released, had a fiasco, but got it working.  I've been booting from an external hard drive which I used dd to copy my regular hard drive to for a backup while my computer was getting fixed (they claim it's drivers....BULLSHIT! it worked fine until September then started overheating and going nuts).  Now I'm trying to boot from it with my own computer again (I was booting it with library computers).  It says all that crap, but I tried the recovery version of the Edgy kernel.  Where it starts going nuts, it says:

EXT3-fs error (device sdb1) ext3_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
Ext3-fs group descriptors corrupted !
mount: Mounting /dev/disk/by-uuid/fcb5f5a3-604a-49ba-a2dd-7f8fd7d60134 on /root faild: Invalid argument
Begin: Running /scripts/local-bottom...
Done.
Done.
Begin: Running /scripts/init-bottom...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Now, could this have anything to do with Ubuntu being on sdb while Grub (when I clicked 'e' for edit on the kernel) says hd0 (hda is my optical drive...)?  What do I change to get it to boot, and then how do I change the menu.lst to match?  I'm going to be copying the drive back onto the internal hard drive soon, but I want it to be working before I do that (and I want to show Windows Vista--which is on the internal--to the guys at work).

Thanks for any help.



EDIT:  I Googled the first line and came up with someone saying they couldn't boot after using Windows.  Sounded like my problem.  Since it also said something about the blocks and there's had to do with renumbering the blocks, it seemed like it would work.  Freaked out for a bit thinking I had given away my last Ubuntu cd, then remembered I bought the Official Ubuntu Book a couple weeks ago, and used that cd to boot from.  Killed X and ran fsck on that partition.  Yay!  It works again!

---

### Post by mld4165 on 2006-11-13
> Killed X and ran fsck on that partition. Yay! It works again!

i tried this before posting but it did not work for me.

anyone have any ideas?

thanks
mld4165

---

### Post by Smuve on 2006-11-14
If you have multiple drives, try rearranging them on your mobo.

I'm not sure if this will help, but I had received the same error after I attached my sata data drive.  Rearranging the drives on the mobo fixed the problem for me.

Background if your interested:
I have three sata hard drives in my computer now, one for windows, one for linux, and one for shared data.  The two OS drives used to be attached to SATA 3 & 4 for a raid array (required by mobo) with the data drive attached SATA 1.

To install an OS, I disconnect all drives except the one I am installing on.  An older distro used to install GRUB on my IDE drive no matter what.  It was a pain in the arse, so that's why I disconnect everything now.  It allows me to use the bios to select the boot drive instead of messing with GRUB.

Anyhow, last night Edgy installed fine and the computer restarted perfectly when it was the only drive attached.  However, as soon as I attached the data drive, I received the same error as in the original post when rebooting.

After a couple futile attempts at other installation methods, I simply reordered my drives and put windows and linux on SATA 1 & 2 and put the data drive on SATA 3.  Now everything works fine.

Therefore, as mentioned above, I'm sure the problem is with GRUB but this worked for me and I'm more comfortable having my OS drives listed first anyhow.

---

### Post by Shamlou on 2006-11-15
I think the problem might be a simple one. Someone had mentioned it before, too. I think the problem is that it's not reading my HD from the right place. A little before it tells me that it can't access tty and so on, it also says something like "/dev/hda1: can't find hda1" or something of that sort. I haven't ran my ubuntu for a while now, so I don't remember exactly what it said. I'll check later on today and post it here if I have time.
I checked my menu.lst and it seemed to be ok there. But maybe it wasn't...

---

### Post by Shamlou on 2006-11-15
As I mentioned before, I have two hard drives. One with Windows on it (slave) and onw with Ubuntu on it (master). I usually change the first boot from BIOS. It's worked fine before until I was installing Frozen Bubbles (on ubuntu) and I accidentally shut the computer off without letting it finish.

It was the next morning when I turned it on and it gave me the following things, as it still does today:

```
Mounting root filesystem
Booting 'Ubuntu, kernel 2.6.15-27-386'

root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
  [Linux-bzImage, setup=0x1c00, size=0x157856]
initrd /boot/initrd.img-2.6.15-27-286
  [Linux-initrd @ 0x1f979000, 0x676242 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
mount: Mounting /dev/hda1 on root failes: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mouting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

```
And after this it's totally stuck. Nothing will work but rebooting (not that that will work properrly either). At least typing won't work. ESC won't work, the Fx buttons won't work, not even with CTRL, ALT or/and SHIFT.

I miss my Ubuntu. I got so used to using it. I had jsut cusomized my desktop and everything just the way I love it. *sniff*

If anyone can help, I'd really appreciate it. It can't be that complicated. It seems as though a few changes in a few files will do the trick. I just don't know what to do and where.

Thanks in advance for your help.

---

### Post by Styan on 2006-11-17
Sounds like /dev/hda1 doesn't exist to me... check that first.

---

### Post by pbi on 2006-12-01
Shamlou,

I am running into the same error with my machine, using K7 kernel - 2.6.15-27-386.

I am using two SATA drives, 1 XP (sda1) and 1 Ubuntu (sdb1).

I traced this error to bug-21759
[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/21759](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/21759)

This bug relates to initramfs-tools, and the answer is obscure to me (found in a reply by tarski)

*from tarski*
> 
I found something nasty in file "/usr/share/initramfs-tools/scripts/functions", and a way to correct it.

1. At the end, in function "parse_numeric", replace :

    *)
        minor=$((0x${1#??}))
        major=$((0x${1%??}))

by :

    *)
        value=$((0x${1}))
        minor=$(( ${value} % 256 ))
        major=$(( ${value} / 256 ))

2. Enter commands :

  cd /boot
  sudo mkinitramfs -o initrd.new `uname -r`

3. Modify configuration file for your preferred bootloader, then let it run to install your new boot configuration.

N.B. : In rescue mode from Live CD or another Linux system still booting, steps 2 and 3 must be run after mounting the partition containing your Ubuntu system and performing a "chroot" command.



I have tried the following:

1) Redo grub, but I end up with the same error as Shamlou, again.  

2) I have checked my SATA drives with SeagateTools, and it found no errors with either drive.  The BIOS finds the drives without problems.  Even LiveCD finds the XP and Ubuntu drives but can not access the Ubuntu one.

I am at a loss, and too chicken to start coding.  I have spent so much time setting up my Ubuntu drive only to have it disappear.  ](*,)

Any help will be appreciated.

---

### Post by pbi on 2006-12-03
I am at the end of my rope with this.  I am fairly new to linux, and this is very daunting.  My LiveCD recognizes the Ubuntu drive, but there is no way to mount it.

The BusyBox prompt is very spartan and not very helpful.

I have tried every command that I am familar, and I am unable to mount my Ubuntu drive (permission denied or directory no found).  Even changing the directory is almost impossible at the BusyBox prompt.  The commands that are listed are very limited. I can't find the su command in the list, nor can BusyBox recognize the su command.

I can't use regular su command to get permissions.  Is there any way to access this drive without reformatting?

---

### Post by Shamlou on 2006-12-03
Hi pbi.

How did you mount your linux partition? I mounted mine and it was fine, though I didn't manage to actually change much to affect the failure of the boot, but I did have basically full read/write access.

My problem had prolonged for many weeks already and the only reason I didn't want to reinstall was that I didn't want to lose all my configuration. But I figured that it would take less time to reconfigure everything than to fight with it.

Nasim

---

### Post by faswad on 2006-12-05
I've had the same problem for a few months now, ever since I upgraded to 6.10. I cannot find anyway to fix it. I've tried:

1. shuffling drive connections around
2. updating menu.lst to reflect shuffling of drives (hda1, hdc1, sda1, etc)
3. booting from livecd (unable to mount the drive, even though its visible)

I dont want to re-install everything. This problem could just happen again and i'd be in the same boat once more. Until there is an official announcement of this bug, I'll stay away from Ubuntu.

What I'm doing now is is using Ext2Fsd to load my Ubuntu parition in Windows XP... pretty sad, but I still need the data on the partition.

---

### Post by styfer on 2006-12-06
hi
i have the exact same problem

can't access tty; job control turned off

follow by a command prompt
strange but true when i type 'exit' (without qoutes) i can boot to ubuntu

can you guys with the problem try that?

---

### Post by amh on 2006-12-10
I am having the same problem.  I tried the "exit" idea but alas I get exactly the same result:

/bin/sh: can't access tty; job control turned off
(initramfs)

I am running a Pentium D processor 820 with 1GB and two SATA drives -- one I use to boot XP and the other ubuntu.  Ubuntu worked the first few times I booted it and I was (and still am hopefully) looking forward to using it.  I have noticed that this problem has been kicking around for a while (I found references dating back to 2004).
I would re-install but I fear that it will simply re-occur.
I hope that the ubuntu "guru's" are paying attention and will fix the problem.

---

### Post by Bobtheknight on 2006-12-12
I have the same problem as well, except with me I'm trying to get it to install to a external hard drive.  I checked my menu.lst and that seemed to work right.  (The sda(0,0) points to right direction and everything)

My /bin/sh points to dash and my /bin/sh.distrib points to bash.

I'm going to try the type exit idea.  But if anyone know of why this might happen to external drives give me a shout please.

Ok I'm back, exit doesn't work, but when I press ctrl-alt-f1  It tells me sbin/init doesn't exist, and a bunch of mount failed.  This is strange, because the system did find grub, which is under /boot/grub lol.  Maybe I didn't mount them right after all.

But it did boot up the boot splash (with the progress bar and stuff)... I'm so confused

---

### Post by efguerre on 2006-12-18
> **Shamlou said:**
> As I mentioned before, I have two hard drives. One with Windows on it (slave) and onw with Ubuntu on it (master). I usually change the first boot from BIOS. It's worked fine before until I was installing Frozen Bubbles (on ubuntu) and I accidentally shut the computer off without letting it finish.

It was the next morning when I turned it on and it gave me the following things, as it still does today:

```
Mounting root filesystem
Booting 'Ubuntu, kernel 2.6.15-27-386'

root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
  [Linux-bzImage, setup=0x1c00, size=0x157856]
initrd /boot/initrd.img-2.6.15-27-286
  [Linux-initrd @ 0x1f979000, 0x676242 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
mount: Mounting /dev/hda1 on root failes: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mouting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

```
And after this it's totally stuck. Nothing will work but rebooting (not that that will work properrly either). At least typing won't work. ESC won't work, the Fx buttons won't work, not even with CTRL, ALT or/and SHIFT.

I miss my Ubuntu. I got so used to using it. I had jsut cusomized my desktop and everything just the way I love it. *sniff*

If anyone can help, I'd really appreciate it. It can't be that complicated. It seems as though a few changes in a few files will do the trick. I just don't know what to do and where.

Thanks in advance for your help.
I have the same problem as most of you have it please poste some tips and trycs to make solution to my Ubuntu. What should I do?
Just in case I have exactly the same problem as Shamlou.
thank you very much in advance.

---

### Post by coltrane on 2006-12-20
I had this problem this morning. I have two computers with ubuntu 6.10, one has only ubuntu and a 160G drive and the other ubuntu on a 250G with windows XP on a 80G drive. This problem has only ever happened to the PC that is dual boot with two drives even though ubuntu is basically the same on both and using the same Kernel 'Generic'. Has anyone had this problem with a PC that has only ubuntu and one drive? oddly enough the dual boot PC works OK when it rebooted again, and I can't figure out why. Can't find any corrupted files yet.
:confused:

---

### Post by Methodize on 2006-12-21
Hey guys. well i have this same problem but i was messing around with this: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

trying to get beryl installed on my computer.... EVERYTHING went fine until i had to reboot and change the session. 
i hope this will help anyone trying to fix this problem.

---

### Post by schmappel on 2006-12-21
Had the same problem, turns out menu.lst needed the UUID's... [**This**]("http://www.ubuntuforums.org/showthread.php?t=322885") topic helped me fix it.

---

### Post by amunimanghi on 2006-12-21
Hello everyone,

I encountered this same problem but I was using Arch Linux. Alas, it has come to Ubuntu. In arch, all I had to do was somehow mount my Ubuntu partition, go into the root folder and type ```
sudo mkdir initrd
``` 

I am now gonna boot up my live cd and report back to see if this solves the problem. Btw, I have /dev/hda1 instead of the UUD or that very long number.

---

### Post by Mateo on 2007-01-27
Hey guys, I'm running into this as well.  I did 3 things that could possibly have caused it:

1) apt-get autoremove (doubt this caused it)
2) Forgot to unmount a usb drive before turning the computer off (doubt it)
3) Update manager downloaded some stuff, one of which was kernel source (maybe?)

Anyways, I'm using Ubuntu standard, but using the xubuntu install/live cd to resolve the problem because it loads faster than the ubuntu install/live cd.  Hope this isn't a problem.

I can mount my drive.  It's sda3.  Is this unusual?  Everyone else is declaring theirs as **h**da, did mine get renamed somehow?  sda1 is the windows recovery partition, sda2 is the windows partition, and sda3 is the linux partition.

I tried editing the boot to root=/dev/sda3 like some others suggested, but this didn't do anything.  i'm a little bit stuck as to what to do now.  maybe mount dev/sda3 and run fsck on it?


edit:  ohh and when I get to the error stage, and if I press ctrl+alt+f1 it says something about can't access /sbin/init.  Should I just create that directory?  or is that even a directory....

---

### Post by Mateo on 2007-01-27
ok, now I mounted sda3 at /media/sda3 and then 'chroot /media/sda3' and then ran fsck but it immediately says 

```
fsck.ext2: Unable to resolve 'UUID=faae223e-5c5b-4388-b3d6-bab6f9701640'
```

what could that possibly mean?

---

### Post by Mateo on 2007-01-27
ok, so I simply copied the /sbin/init file from the cd to the sda3 partition and then restarted.  got through about half way through the load screen this time and then fsck started.  It ran to 100% and then wanted to restart the computer.  Then I got this error:

```
/etc/rc5.d/S20checkroot.sh: 407: reboot: not found
```

then some other stuff (not errors) and then it just stops.  can't even ctrl+alt+del to restart.  have to restart by holding the button on the computer.  then when I restart, it repeats the whole thing with fsck.  now I *really* don't know what to do.

---

### Post by Coq_Rouge on 2007-01-31
I experienced this problem today. Installed Ubuntu 6.10 Server a couple of days ago with the 2.6.17 kernel. Due to some problems with my network card I had to install the 2.6.19 kernel.

The computer is a Acer Aspire e380.
Hardware:
AMD Athlon 64 X2 4200+
2 x 250Gb HDD (SATA)
4Gb RAM

The network card on the machine is a *Marvell Yukon 2*. The 2.6.17 kernel do not support this, and the drivers from Marvell do not work. 

I downloaded the 2.6.19.2 kernel from kernel.org, and followed the instructions at [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) to do the update (with the obvious changes). At reboot would not the 2.6.19.2 boot, with the */bin/sh: Can't access tty; Job control turned off* error message. I can still boot into 2.6.17.

/boot/grub/menu.lst 
```

title Ubuntu, kernel 2.6.19.2-custom
root (hd1,0)
kernel /boot/vmlinuz-2.6.19.2-custom root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-2.6.19.2-custom

title Ubuntu, kernel 2.6.17-10-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic

```

There is a Windows install on sda1 (XP recovery) and sda2 (Media center). *fstab* reports the same UUID's as */dev/disk/by-uuid/*.

I have tried most of the possible fixes linked from this and other similar threads with limited success. I hope that someone can figure this out as it is quite anoying.

Coq Rouge

---

### Post by Coq_Rouge on 2007-02-01
Problem solved.

With one more day of fiddeling around I finally found the solution to my problem. As the [http://www.howtoforge.com/]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2?") suggested in step 5 did I copy the *.config* and load it when running *make menuconfig*. As all the harddrives and items like that worked before I compiled the new kernel, I assumed that the *.config* had all the SATA support it needed. It did not. After a bit of fiddeling about, I got into the *Device Driver -> Serial ATA* folder and discovered that *ATA Device support* was not included. I included this and the *nVidia SATA support*, and upon recompiling of the kernel, I could finally boot again.

I hope this can help others out.

Coq Rouge

---

### Post by Cesa on 2007-02-02
Ok, here is my version of the same problem:

I tried the windows installer, and it worked fine at first (more or less, I actually got this error, but it turned out that grub defaulted to sda1, changed to hda1 and it worked fine).

Ubuntu booted nicely, and asked me if I wanted the updates. I installed them and rebooted, but now I have the same problem as some of you in this thread. I get:

```
/bin/sh: Can't access tty: job control turned off
```

CRTL+ALT+F1 shows:

```
root (hd0,0)
Filesystem type is ntfs, partition type 0x7
kernel /ubuntu/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
[Linux-bzimage, setup=0x1c00, size=0x18db5c]
initrd /ubuntu/initrd.img-2.6.17-10-generic
[Linux-initrd @ 0x1f149000, 0x53641c bytes]
boot
mount: Mounting /dev/hda1 on root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

ls -l /dev/hd* gives:

```

brw-rw----  1 0  0  3,  64 /dev/hdb
brw-rw----  1 0  0  3,   1 /dev/hda1
brw-rw----  1 0  0  3,   0 /dev/hda

```

menu.lst is unchanged since before the upgrades (when it worked).

What should I do now? I have no idea what the problem could be.

Oh, and, I'm a newbie when it comes to Linux, so try to take it step-by-step :)

---

### Post by fazza on 2007-02-05
this is really weird - everyone is having the same type of problem with the same error message. Mine happened with banshee. I discovered a new version - 0.11.5 - had been released, so I downloaded it. My computer doesn't like install from source (is it called source when you have to type ./configure and make and stuff?), so I searched for a .deb and found one on this site. It installed fine, except one of the plugins didn't work. So I googled it and found one (a .deb) which wasn't satisfied with the package dependencies. Realising this must have been released as a Feisty program (don't know how it worked on the pc in the first place), i found the right packages right down the dependency tree to the packages that didn't rely on anything. It got a bit long winded, so I stopped. Apt-get errors kept pinging up telling me to 'sudo apt-get install -f' to fix the problem. Occasionally, it said that I could run apt-get autoremove to remove unneeded packages - some of which were programs I use, and some I had just installed. So I returned everything to it's original state (I thought). One of the dependencies I had installed was mono and mono-jit (this is all from memory, so some of the commands/filenames etc may be wrong), which I had had a lot of problems and funny error messages with. I'm thinking this may be a culprit.
     The first time I discovered (actually my mum discovered it) something may have changed was when we went to shut the pc down. We already have power-management issues - the shutdown button is only on the login screen options. (which, btw, is also not editable, gdm-setup doesn't work.) I logged off, and when it came to shutting down, the shutdown wasn't there and there were a different list of commands to usual. I thought maybe this was because I'd installed Feisty packages which had affected this (mono?). Then, this morning, it got about an eighth of the way across the boot up splash screen progress bar, and reverted to the error that almost everyone on this post seems to have had. I've edited the bootup commands (in grub), I've tried typing exit at the /bin/sh prompt, but I can't think of anything else to do. Even knoppix won't run, and the new version is a DVD -we don't have a dvd drive. Windows (98SE) won't pick the partition up, so the only thing I can think of doing is reinstalling it. Which I do not want to do - I have lots of school work and other files, including my parents' files, and millions of programs. (PS I'm running Dapper upgraded to Edgy (I think)).
Sorry this post is so long, you're probably bored by now, but if you can help, please do. I've convinced my parents that Linux is better that Windows, but we've had so many problems.
Thanks
fazza :)

---

### Post by Rongo_Tai on 2007-02-13
See
[http://www.google.com/search?hl=en&newwindow=1&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=bin/sh:+can%27t+access+tty:+job+control+turned+off&spell=1](http://www.google.com/search?hl=en&newwindow=1&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=bin/sh:+can%27t+access+tty:+job+control+turned+off&spell=1)
for solutions to this problem from a number of sources, including Gentoo lists.
It's fairly common, apparently. Basically, the kernel needs a ramdisk bigger than 4096 at boot. Setting it in grub.conf or lilo.conf to 8192 apparently fixes the problem.
Eg 'ramdisk_size=8192' or 'ramdisk=8192' .

If you are stuck at BusyBox just boot via [Ubuntu ?] LiveCD, follow the documentation to mount your root partition, boot partition, and proc (?), then chroot and edit the conf. System should then boot.

An example of a working /boot/grub/grub.conf  ..

-------------------------------------------------------------
default )
timeout 15
spalshimage=(hd0,6)/grub/splash.xpm.gz

Title=Ubuntu Linux
root (hd0,6)
kernel /kernel-2.4.26 root=/dev/ram0 init=linuxrc   ramdisk=8192 real_root=/dev/hde9
hda=ide-scsi hdb=ide-scsi
initrd /initrd-2.4.26

Title=XP
root (hd0,0)
chainloader + 1
------------------------------------------------

Rongo_Tai

---

### Post by fazza on 2007-02-14
wow, thanks... I'll try that now
:)

---

### Post by serlex on 2007-02-15
I'm trying to install feisty on my computer, i downloaded herd 3, burn to a cd. But when i try to build it comes up with the same error 
```
can't access tty
```

I don't know if its hardrive problem or Ubuntu. CD works fine with my laptop, but not with my computer

Any ideas? Thanks

---

### Post by pgawron on 2007-02-20
I was able to get past this error by changing the SATA settings in the bios from legacy IDE support to Native IDE support.

Everything worked great!

---

### Post by fazza on 2007-02-22
> **serlex said:**
> 
...CD works fine with my laptop, but not with my computer...


I've had exactly the same thing - it runs great on my laptop (except I can only shutdown from terminal) but the pc isn't having it atall. Would that be anything to do with the way the laptop manages power and devices etc?

---

### Post by serlex on 2007-02-22
It must be how it manages the devices. If crapy windows work on my computer, cant see why Linux shouldn't! find me a solution :D

---

### Post by gameman12 on 2007-02-27
hah i have the same problem myself

/bin/sh:can't access tty: job control turned off

help!!!

---

### Post by insert_name_here on 2007-03-10
I, too, am getting this error.

My Edgy system had been working fine; I was not upgrading to edgy like others on this thread, and I hadn't messed much with my hard drives.

I think I had ran apt-get autoremove, which someone mentioned could have removed some important package.  Also, my system didn't shutdown correctly from X, and since I forgot how to use 'reboot' to reboot from a ctrl-alt-f# terminal, I had just powered down.  

Any ideas on how to fix, besides reinstallation?

---

### Post by eljaco on 2007-03-11
I'm having this problem on my laptop (and in fear of having it happen on my desktop, I haven't rebooted) after installing Feisty.
Here's what comes up when I do Ctrl+Alt+F1:
> 
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/<large hex number> does not exist. Dropping to shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job contrl turned off
(initramfs)

Anyone have a solution to this?

UPDATE: I was able to run an old kernel version (2.6.17-10-generic) which has the same UUID (and is in the same partition.) This is kind of weird, but at least now I can load up Ubuntu. Also, it seems to have updated all my packages and images (i.e. looks like Feisty, not Edgy) so it might be something with the new kernel I am trying to use (2.6.20-9-generic.)

---

### Post by swoskow on 2007-03-11
Count me in - same problem when installing from the Alternate CD.  I can install from the desktop and it works fine.  I hope someone can find a solution.

---

### Post by estratos on 2007-03-14
This morning I've encountered the same problem. Then, I've inserted the Alternate install CD (6.06) and chosen "Resque a broken system" from the main menu. Then, I selected the partition to use as root filesystem. Reboot and ... it works!!

I hope this helps.

Daniel.

---

### Post by mvoorberg on 2007-03-14
Had the same problem after clean (RAID1 on IDE) install from the Alternate 6.10 CD.  Turns out the grub menu.lst was pointing to the wrong place.  It had "/dev/hda1" instead of "/dev/md0".  After that it's all good.

I haven't yet verified the Raid but I plan to pull a disk and try to rebuild it before I spend too much time with anything else.

-Mark
[www.objectclarity.com](www.objectclarity.com)

---

### Post by wgw on 2007-03-24
/bin/sh: Can't access tty; Job control turned off

I have been having the same (series) of problems described here.

As was described:
> I think I had ran apt-get autoremove, which someone mentioned could have removed some important package. Also, my system didn't shutdown correctly from X, and since I forgot how to use 'reboot' to reboot from a ctrl-alt-f# terminal, I had just powered down. 

I can boot all the way to init_bottom, but it hangs after that.

My main problem is being able to pinpoint the error through the scrolling messages during boot (no splash). Is there a way to capture that scrolling? (dmesg does not work at the command prompt; is there a file I can look at?)

Here are some of the symptoms on my XP/Edgy configuration:

There is no /sbin/init ; in fact, init doesn't exist anywhere as far as I can tell.
There are no uuid device names in /dev (should there be?)

I can boot from the installation cd and see my files;
I have done a get-apt install ubuntu-minimal, standard, Desktop, with no change.
I have done a fsck check. The disk is clean

On my list of things to try, in all the various combinations, is:
A. In grub:
1) increase the ramdisk size:  ramdisk=8192
2) add  a label :  real_root=/dev/hda2
3) synchronize fstab and menu.lst: fstab uses uuid and menu.lst uses /dev/hda2
B. From the CD
4) copy sbin/init to my sbin/init


My menu.lst file seems normal otherwise:

title        Ubuntu, kernel 2.6.17-11-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-11-generic root=UUID=e77a8fce-f839-49bd-8dde-06acb9ca1c2b ro splash
initrd        /boot/initrd.img-2.6.17-11-generic
# quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.17-11-generic
boot

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet
boot


FSTABS:

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=e77a8fce-f839-49bd-8dde-06acb9ca1c2b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=7cdf83ef-3425-499d-893b-920ba36cb91f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/Windows ntfs umask=222,utf8 0 0


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5287    42467796    7  HPFS/NTFS
/dev/hda2            5288        9544    34194352+  83  Linux
/dev/hda3            9545        9729     1486012+   5  Extended
/dev/hda5            9545        9729     1485981   82  Linux swap / Solaris

---

### Post by wgw on 2007-03-25
I have resolved my problem, thanks to [http://ubuntuforums.org/showthread.php?t=383782](http://ubuntuforums.org/showthread.php?t=383782) ( summary here: 
[https://answers.launchpad.net/ubuntu/+ticket/4383](https://answers.launchpad.net/ubuntu/+ticket/4383) )

The recipe I got there was: 

> try to install the sysvinit package, entering on root disk system from a live cd.
then mount /dev/sda1 (or where you have root filesystem) on /somedir

#sudo mount -rw /dev/sda1 /somedir
#sudo chroot /somedir

#sudo apt-get install sysvinit



---

### Post by silverbolt027 on 2007-03-28
I had this same problem, but I didn't even follow the above remedy.  All I had to do was change the menu.1st with grub, or if you can't boot in the first place, just press 'e' on the grub menu, and change it there, then press 'b' to boot. 

the problem I had, was that I deleted a partition, so it changed the number of the partitions...all I did was to change the 'root hda5' to 'root hda4' and on the next line 'blah blah hda6' to 'blah blah hda5', and presto it worked!

Once you are booted up, just remember to change the menu.1st

Good luck!

---

### Post by HwyXingFrog on 2007-04-08
I have tried this with Ubuntu 6.10, Ubuntu 6.10 Ultimate, Ubuntu 5.10, GParted, and Linux Rescue CD.

All of them won't install
I either get the "can't access tty; job control turned off" error, or it won't mount the cdrom

This is a brand new system that I originally had Vista installed on planning on doing a dual-boot with ubuntu ultimate 1.3.

I can't even do just Ubuntu.

I have Intel D965RYCK Motherboard, Core 2 Duo E4300, 500gig WD SATA.

I know I can't do anything with GRUB because I don't even have it installed yet.

Why won't any of this work?

---

### Post by dolaksiz on 2007-05-18
Hi,

I had installed 6.10 one month ago onto an XP computer. There was no problem, and I was really happy with my Ubuntu. Then I formatted the C: drive and installed Vista (by deleting XP). I wasn't happy with Vista so again I installed XP  Then I couldn't see the GRUB, and XP automatically started. So I followed the instructions and restored the GRUB by using Super Grub. Now I can see my old GRUB (with the default values and waiting times I had edited back when I used Ubuntu). But when I try tu login to Ubuntu it crashes. I tried to login with recovery mode and I get a message like:

can't access tty: job control turned off
(initramfs)

and a blinking cursor. I can write anything but it just does not accept them as command lines. CTRL+ALT+F1 (or F2, F3, etc..) does not work either.

I booted with the liveCD. In the terminal I enter,

sudo fdisk -l

and I get,

/dev/sda1 NTFS ... and continues something
/dev/sda2 W95 Ext'd (LBA)...
/dev/sda3 W95 FAT32...
/dev/sda5 Linux...
/dev/sda6 Linux Swap/Solaris.....

I can mount the sda5 by typing,

sudo mount /dev/sda5 /mnt

And I can see all my old files, but what should I change, I don't know.. I made all these by searching in the forum, but I couldn't find a solution.

What should I do?

---

### Post by orengolan on 2007-07-02
I am using Ubuntu 7.04.
had no issues in the past and woke up today into this nightmare.
I am new so please guide me with patience.

after getting this error i can still run some commands like cd and ls,
and move between the folders.
When i hit ctrl+alt+F1 i see : starting up...Alert! /dev/hda1 does not exist. Dropping to a shell!

can anyone help me?
I know what grub is and i know that there is  a way to change the drive that ubuntu is booting from, 
but i don't know how to do all that.

I have an important folder that I want to access and remove to a safer place (my accounting files)
so I don't mind just to get a hold of it and buying a new machine (maybe the dell desktop?).
It should be in my home dir but i don't know how to access it. and even if I will see it, how can I copy the folder to an external usb or something like this?

Thanks!

---

### Post by DigitalAxis on 2007-07-02
The problem (or at least my solution) is that now in Feisty Fawn, what was once /dev/hda is now /dev/sda.

Upon rebooting I discovered the system complaining about not being able to fsck.ext2 my /boot directory (/dev/hda1)... because it's now /dev/sda1

**sudo nano /etc/fstab** (or maybe not, I think you're root already) and then changing any /dev/hdaX lines that are NOT commented out may very well fix your problem.  

It might say something different, but the cause is probably the same.

---

### Post by orengolan on 2007-07-02
i'll try it, but i use ubuntu 7.04 for a few months. it just happend this morning!

---

### Post by tri7 on 2007-07-23
Last week i had exactely the same problem. Everything was working fine and when i rebooted that error appeared. I managed to solve it and maybe it will be of help to others. I have Dapper.

1-Used Damn Small Linux to boot (any live cd will do)

2-Mounted hda1 (my partition) on DSL and managed to check that all my data was there

3-went /boot/grub/menu.lst in my hda1 and noticed there were 2 menu.lst files. These are essencial to boot (from what i read...am also a begginer) one menu.lst and other (some error that occurred...) menu~.lst

4-So just renamed/deleted menu~.lst and all was well

---

### Post by kadnan on 2007-08-19
> **Styan said:**
> Alright! It was the same issue as in one of the previous threads, where the GRUB was pointing here: root=/by-uid/[whole bunch of hex code] rather than: root=/dev/hda1 just edited the line to show /dev/hda1

Prior to my post here, I had no idea how to get into the Grub ... so I started randomly hitting keys (like you do F8 for getting into the windows "grub" lol)  btw, for ubuntu its 'esc' :p

Thanks for all your help guys! Hopefully this will help anyone else with the problem.

i m newbie. Ca you explain the steps how can I edit and set my entry. I also getting same error. Please!

---

### Post by Vanish00 on 2007-08-24
Just recieved this problem today on boot up.  I am a noob at this and reading some solutions I'm still lost on what exactly they did.  Some talk about editing a file others talk about mounting a hard drive from the live cd.  I have no idea how to do either one.  I guess I could edit that file through the live cd, i hope.

---

### Post by DerTod on 2007-09-15
hey,
i've got nearly the same problem. but my problem is that this error occurs when starting from the live cd (without installation). and for mostly all of you tracked  it back to grub (that isn't yet installed on my machine) and I really dont know what to do...
some details:
OS (running): Vista
OS (trying to install): Kubuntu FF
HDD: 160 GB SATA (divided up in 3 partitions and some unallocated space)
PC: Dell Inspiron 1520 (2gb RAM, 1,8 Ghz Core 2 Duo)

---

### Post by ade_kusniawan on 2007-09-16
> **Shamlou said:**
> I had installed ubuntu and was using it normally. One day I was installing Frozen bubble (the game) and I left it to download and install packages, because it was going to take 40+ minutes. We were going out that night and I had forgotten that I was installing something and just turned it off (pressed the power button which does the logout and shutdown automatically). It was the moment I pressed the power button that I realized I had something going on, but it was too late.

The next morning when I turned the computer on. ubunutu wouldn't start. It said: "/bin/sh: can't access tty; job control turned off" Then it would give me "#" on the next line where I can't type anything.

I've been searching forums for some suggestions to people who have had the same problem. Unfortunately, I haven't ran across anything that has helped.

My friend said that I should just reinstall the whole thing. I would, but I don't want to. I don't have any important files that I would lose by reinstalling. But I will feel sorry for losing all my hours spent on customizing my ubuntu (desktop, programmes, etc.). So, I figured that there must be some way to avoid total reinstallation.

I thought maybe I could see what's going on in the system by using the ubuntu live CD and access my hard drive from it, but I don't know how to mount my hard drive. And when/if I get access to my HD with the ubuntu live CD what exactly should I check/change/edit ?

I've used linux for many years, I know the basics, but I'm nowhere near as good as I would like to be. So, I would appreciate the help. Helps me learn at the same time.

I have two HDs in use right now. One is a Master (Ubuntu) and the other a slave (Windows). I don't know if this helps/complicates the situation.

Thanks for your help in advance.
it happend to also after i update my kubuntu with this command
# sudo apt-get install ubuntu update
#sudo apt-get upate
reboot

then after rebooting the system, it looks like

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

please help me....

---

### Post by SeTsU on 2007-09-18
Hi all,

I'm having the exact same problem (I was actually writing this post referring to the "ramdisk" solution, but it already failed one of the reboots while I did so :P) and on my configuration, I have two regular ATA-100 (not SATA) disks plugged in, the one with Ubuntu Feisty being the Secondary Master.

I noticed while on BusyBox that something (dibs on whatever goes after grub) simply doesn't get the partition table for the disk correctly (or so it seems). On my first disk, sda, I get all 3 partitions, plus the generic sda, while on sdb I get none of my four partitions, just the generic sdb.

Can't actually check it, since when I boot successfully, I don't ever get to the BusyBox shell.

Still, the "ramdisk" method DID give me a higher-than-normal successful boot rate, so I'm going to give it a try and increase the ramdisk size a bit more to 12288. I'll be in touch. ;)

EDIT: Well, all seems! ;)

In short, here's a quick how-to for this particular method:

1. Boot your PC and access the Grub menu (using "Esc" for those with no delay)
2. Choose the line for your current kernel, and press 'e' to edit.
3. Select the line that says "kernel" and press 'e' again to edit it.
4. Before "boot=" (actually I believe it can be afterwards, but didn't test) add "ramdisk=8192" (without the quotes), or a higher ramdisk size if needed.
5. Press enter to save the edited line, and then press 'b' to boot the kernel.

If you have successfully booted your system, use your favorite text editor and edit /boot/grub/menu.lst.
Then add the above ramdisk option to the kernel line, save it and reboot to test.

If all goes well, you should be able to boot normally from now on! ;)

Cheers!

EDIT #2: Ok, so it seems it's not quite a definitive solution after all. I just get to boot much more often. :( Meh.

---

### Post by dj_deef on 2007-09-22
one solution to this problem (when it comes after the installation) is to set root=UUID=yourhduuid in menu.lst (grub) and set the device mount by UUID in fstab

I think the error come out because sometimes kernel assings a different name to a device.
i.e. we expect /dev/sda and the kernel calls it /dev/sdb

---

### Post by Saicho on 2007-09-24
> **DerTod said:**
> hey,
i've got nearly the same problem. but my problem is that this error occurs when starting from the live cd (without installation). and for mostly all of you tracked  it back to grub (that isn't yet installed on my machine) and I really dont know what to do...
some details:
OS (running): Vista
OS (trying to install): Kubuntu FF
HDD: 160 GB SATA (divided up in 3 partitions and some unallocated space)
PC: Dell Inspiron 1520 (2gb RAM, 1,8 Ghz Core 2 Duo)

I have the same problem, with a laptop with almost the same specs but but I'm trying to install Ubuntu 7.04 from the LiveCD.

---

### Post by PhantomWA3 on 2007-09-25
I getting the same problem after upgrading to Fiesty, but I have some more info when it bombs out to a command prompt if I then press ctrl->F1 there is the following error messge:

```
Check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hda1 does not exist.  Dropping to a shell!
```

I have managed to boot up using a the generic kernal from grub and once in Ubuntu if I run fdisk -l, i get the following:

```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30024   241167748+  83  Linux
/dev/hda2           30025       30401     3028252+   5  Extended
/dev/hda5           30025       30401     3028221   82  Linux swap / Solaris

```

So hda1 does exist so why is it complaining?

Hope this helps.

---

### Post by PhantomWA3 on 2007-09-25
Looks like I may have to bite the bullet and format then re-install from a fresh copy.

---

### Post by rootguy on 2007-09-27
hi,

Im using debian and had this problem just minutes ago when upgrading to the newest kernel 2.6.21.9.
My first guess was that something was wrong with the drivers for the sata controller and it turned out to be exactely that.
So to fix this problem, look up what sata controller is on your board and reconfigure your kernel.

best regards and good luck

---

### Post by tech9 on 2007-09-27
> **K.Mandla said:**
> Strange stuff. I wish I could reproduce this error so I could tinker with it. :-k

If you can describe what you did to work around this issue, the folks who find a bug report for it might thank you.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/59792](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/59792)

Cheers and thanks.

To recreate this error, 

backup the entire system with this command...

tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

rebuild your PC with Ubuntu; delete and create new partitions & format...

then run this restore command....

tar xvpfz backup.tgz -C / to restore

Finally reboot the system and you will get this error...

/bin/sh: can't access tty; job control turned off
(initramfs)

---

### Post by Mantooth on 2007-09-28
> **Mateo said:**
> Hey guys, I'm running into this as well.  I did 3 things that could possibly have caused it:

1) apt-get autoremove (doubt this caused it)
2) Forgot to unmount a usb drive before turning the computer off (doubt it)
3) Update manager downloaded some stuff, one of which was kernel source (maybe?)

Anyways, I'm using Ubuntu standard, but using the xubuntu install/live cd to resolve the problem because it loads faster than the ubuntu install/live cd.  Hope this isn't a problem.

I can mount my drive.  It's sda3.  Is this unusual?  Everyone else is declaring theirs as **h**da, did mine get renamed somehow?  sda1 is the windows recovery partition, sda2 is the windows partition, and sda3 is the linux partition.

I tried editing the boot to root=/dev/sda3 like some others suggested, but this didn't do anything.  i'm a little bit stuck as to what to do now.  maybe mount dev/sda3 and run fsck on it?


edit:  ohh and when I get to the error stage, and if I press ctrl+alt+f1 it says something about can't access /sbin/init.  Should I just create that directory?  or is that even a directory....

I had this same problem.  It all started after I edited my /boot/grub/menu.lst file.  Whenever I selected any of the linux kernels present the splash screen would stall and then I'd see "... /bin/sh: can't access tty .. " etc.  I didn't realize that after I edited that file, when I turned my machine off, I pulled a usb drive out of the back of my machine.  I didn't think it made a difference.  But after trying a lot of fixes, including restoring the original menu.lst (from windows), I saw this post.  So I put the usb drive back in and everything works.  Hopefully when I properly remove the usb drive it will continue to work.

---

### Post by tech9 on 2007-09-28
> **Mantooth said:**
> I had this same problem.  It all started after I edited my /boot/grub/menu.lst file.  Whenever I selected any of the linux kernels present the splash screen would stall and then I'd see "... /bin/sh: can't access tty .. " etc.  I didn't realize that after I edited that file, when I turned my machine off, I pulled a usb drive out of the back of my machine.  I didn't think it made a difference.  But after trying a lot of fixes, including restoring the original menu.lst (from windows), I saw this post.  So I put the usb drive back in and everything works.  Hopefully when I properly remove the usb drive it will continue to work.

you maybe on to something. I am going to exclude boot in backup process and see if this solves my problem.

---

### Post by DrMilo on 2007-11-19
> **tech9 said:**
> you maybe on to something. I am going to exclude boot in backup process and see if this solves my problem.


Good lord I hope it isn't this again! I've had the queerist things happen when I leave USBs in machines and I wouldn't be surprised if this isn't my problem again.

In my case… waiting for root file system… 20 minutes later blah blah job control blah blah.

My Ubuntu partition is on an IDE drive so I doubt it's SATA. I've unplugged all my SATA devices and get the problem when solely running IDE. 

I also get the problem when I have unplugged all drives except for my SATA CD drive with the live CD, so it isn't because I've edited grub from anything to anything and in any case there are no drives to find except the one it's already read to display the menu!

I have had problems arise from not unmounting USBs and shutting down my machine. Last time it was my power supply going dead. This problem is just strange enough to have USBs at the root of it. So in the past I put the USBs in the jacks cold, switched on the machine, booted up and things worked. I’ll be trying this tonight and post the results tomorrow.

---

### Post by madmod on 2007-12-10
I was trying load Ubuntu 7.10 from an ISO CD-ROM on an old discarded Dell Dimension 4300 that had a corrupted Windows XP.  I got the error '/bin/sh: Can't access tty; Job control turned off' that everyone on this thread appears to be having troubles with.

I then tried installing OpenSUSE 10.3 on the computer and got '/bin/sh: Can't access tty; Job control turned off' again.  Whoops!  What I concluded:  it's not a problem with either Ubuntu or OpenSUSE.

The tower had a CD-RW unit and a DVD-ROM unit.  The performance of those drives seemed weird--sometimes working sometimes not.  BIOS screens only reported the CD-RW!  So I opened the case and checked for what was there.  Both drives on one IDE cable.  CD-RW as master, DVD-ROM as slave.  Then I saw a small crimp in the cable.  I installed a new cable with only the DVD-ROM drive now as master, mostly to simplify the environment and to see if BIOS would pick up now on the DVD-ROM. (It did.)

Voila--clean install with no errors.  I already had Ubuntu on two lab machines already so I installed the OpenSUSE 10.3 (KDE version) to watch the install process.  (very lengthy with numerous 'Next', 'Next", interventions and long downloads before the install was finished; then more update installs later.  The Ubuntu install is a dream by comparison.

In conclusion, I'd recommend you investigate the hardware health of the computer.  Maybe Ubuntu and OpenSUSE installers are simply saying that the hardware isn't acceptable yet.

---

### Post by nostradamnit on 2008-02-11
Hi everyone,

I'm having this same problem, after upgrading Kubuntu 7.10. The upgrade seemed to go well and when I rebooted I got this message. I thought it was cuz i'd just installed a new KVM switch. I then proceeded to leave the machine dormant for a couple of weeks (not my primary machine). I reconnected the keyboard/mouse/video directly and it's still not working?!?

Grub appears to be correctly configured. I deleted a menu.lst~ file from the grub directory, but it didn't help. 

Has anyone been able to successfully fix this error?

Cheers,
Sam

---

