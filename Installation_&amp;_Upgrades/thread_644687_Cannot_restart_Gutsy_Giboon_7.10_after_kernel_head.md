---
title: "Cannot restart Gutsy Giboon 7.10 after kernel header updates 19 Dec 07"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by reler on 2007-12-19
Like others here today  (19-Dec-2007), I started my Ubuntu Desktop machine and was asked to do an upgrade. 7 packages were suggested and the first one or two of these (at least) included the latest kernel updates. I am not a very experienced linux user so I just said "yes go ahead" and at the end of the upgrade, I was asked to reboot. When I did so I go the message:
  "Error 17: cannot mount selected partition"

I am now running off the DVD and after a little detective work I can report that;
- My grub settings seem unaffected (menu.lst ?). They just don't work !

- If I boot on the DVD, I can see the hard disk and its contents seem to be intact

- If I start to use the Install option from the DVD desktop, when I get to the Partition Manager, if I use the "Manual" option, it complains about their not being a  "/" (root ? Pardon my ignorance).

- the commands on the grub menu that try to start the hard disk system are:[INDENT][I]  root (hd2,0)
  kernel /boot/vmlinz-2.66.22-14-generic
  initrd  /boot/initrd.img-2.66.22-14-generic
  quiet[/I][/INDENT]and are unchanged.
(I should say that the hard disk in question in a SATA disk - the machine has 2 other PATA drives, one of which is WinXP, the other a data drive)

- The Linux (SATA) disk is showing in the file browser as "disk". I'm not sure if this corresponds with the label when it ran previously.

- Looking at the Linux disk, I see both vmlinuz & initrd.img. Looking at the properties of each I see that
- initrd.img is a link to /boot/initrd.img-2.6.22-14-generic, but that it says that it's broken (!)
- For vmlinuz, "Type" is "Link to Unknown" (!) and the Link Target is /boot/vmlinuz-2.6.22-14-generic

Using the file browser, I saw that
- /boot/initrd.img-2.6.22-14-generic did not exist ! (Hence the broken "link" ?)
- There was a file called /boot/initrd.img-2.6.22-14-generic.bak from about 5 weeks ago.
- Using Terminal, I copied this to create a new version called /boot/initrd.img-2.6.22-14-generic
- BUT, rebooting still failed.

BTW, /boot/vmlinuz-2.6.22-14-generic *is* present.

As regards grub, I see in /boot/grub that *menu.lst-* was created as a backup at the time all of this was going on. However it is the same as *menu.lst* and indeed, it still looks like it did before.

I have now pretty well exhausted my little linux expertise here, but I get the feeling that this ought to be failry straightforward for a real expert to sort out.

Can anybody help ?

Thanks.

Reler

---

### Post by dunkgreen on 2007-12-19
Me either.  If I press ESC and use the previous kernel then I can get in but  the latest version hangs. :<

---

### Post by ThaRabbit on 2007-12-19
Try booting your previous kernell (as mentionned above) and restarting the kernell update process?

---

### Post by didli on 2007-12-19
Same problem here but I don't have an old kernel to boot ...

---

### Post by reler on 2007-12-19
Thanks for the responses so far.

> **ThaRabbit said:**
> Try booting your previous kernell (as mentionned above) and restarting the kernell update process?Sorry but how ? As noted above, the message says "Error 17: cannot mount selected partition" - what I forgot to add was that it then says "Press any key to continue" and when you do it takes you back to the grub menu, where everything is as it was before. Pressing Escape here does nothing.

[rant_mode=on] Is this the point where somebody says "You did back up your existing kernel didn't you ?" If so, I will be angry because as somebody that's here because of excessive pain with WinXP, somebody that was seduced by the "everything you need right out of the box" philosophy of Ubuntu, I think that it may need a bit more in the way of warnings as to what the update process is about to do AND a better safety net ! After all, even WinXP let's you restart from the last good configuration.

[rant_mode=off] ;-)

OK, after letting this shuffle around the back of my mind for a while, I think that the message and other stuff outlined in my original post suggest that somehow an entry for the root partition has been knackered somewhere: I'm not an expert on the partition table (?) but if I boot from the DVD, I can see and access everything on the hard drive, but when I boot from it, I get the messages described i.e. it looks like the device cannot be mounted.

So this prompts two questions;
1. If I'm right, is it easy to restore whatever it is that may have gone missing - and if so, how ?
2. As an aside, how might this have happened following the upgrade for the kernel headers ?
3 ...  OK

THREE questions ...

3. Should a kernel back-up have been done prior to applying this update ? How do you do that ? How do you know that you should ?
4. OK, sorry, FOUR questions - if I am barking up the wrong tree entirely, what IS going on here ?

With thanks in anticipation

Reler

---

### Post by MightyMe on 2007-12-19
Having the same problem. HELP!!

Says inconsistent file system after kernel upgrade. There is no option in Grub to boot old kernel. Even recovery option does not work.

Any help would be appreciated.

Thanks

---

### Post by ve1uxe on 2007-12-19
I'm having the same problem too.  My ampache music server cannot restart.  I'm receiving Error 22: partition not found.  Tried the recovery kernel with no luck.  Also, tried the previous kernel version with no luck either.

I was in the process of updating my other server and I don't want to restart now until this problem is fixed!!!

Any and all help is appreciated.

---

### Post by bouchecl on 2007-12-19
This morning's kernel was problematic on many fronts. I got a kernel oops related to my automounted nfs4 shares. I had to comment these in /etc/fstab to write this post.

---

### Post by reler on 2007-12-19
> **bouchecl said:**
> This morning's kernel was problematic on many fronts.As evidenced by a growing number of other threads :(
> **bouchecl said:**
>  I got a kernel oops related to my automounted nfs4 shares. I had to comment these in /etc/fstab to write this post.I am pretty much a linux-newb ... is this a way to help me get *my* system going again, forgetting the header update ?

Reler

---

### Post by ThaRabbit on 2007-12-19
You could try manually placing the apparently missing kernel file there?

Renaming the .bak should work in my mind :)

 I'll upload the file I'm using (initrd.img-2.6.22-14-generic) if you wish :)

---

### Post by JackandJohn on 2007-12-19
Same problem here; I thought it was specific to my machine because of some bios issues

-Background: I am running 7.10 on a Dell Optiplex 320; I cannot use GRUB because of a bios thing (I forget the details)
-I need to run LILO, and append the kernel with "pci=nomsi" to be able to boot at all


When I saw the changelog for the 2.6.22-14 kernel update, I saw something about this exact issue (auto-msi, or something?), and this was confirmed on the first reboot; it hung when it said that is detected an msi bug and was disabling it (Yay, I thought, until it sat there for a while)

I can boot the old kernel through lilo, but cannot use the new kernel at all.
I hope my details help someone that knows enough to know what's wrong.

---

### Post by garry4o on 2007-12-19
I have a similar problem with 7.04. There were 6 updates, which completed successfully, and like you, it told me to reboot. Mine will read the first two files, displaying a single orange bar in the boot window. Then it halts and goes nowhere. Previous generic wont start either, and neither will the recovery boots (which I don't understand and have yet to see any discussion about what recovery is supposed to do, and how it will help me). I posted in general help, with no replies at all. Luckily, I can rebuild to yesterday, but for what. The fixes (in 7.04) at least) were all security issues, so I would like to use them, but to spend an hour to rebuild, and have the same result is, by some, the definition of insanity.

---

### Post by ve1uxe on 2007-12-19
Ok, This seems weird, and maybe it's because I'm not all that familiar with Grub.  Looks like the latest update had overwritten my original /boot/grub/menu.lst file.  My ampache server was originally a dual-boot system, but I wiped out the old XP partition and went all Ubuntu.  After everything was said and done, all ubuntu was working out of (hd0,0).  After this morning's update, when my Error 22: no partition found error popped up, I noticed that the entry for all of my kernels had changed to (hd0,1).

Once I changed to (hd0,0) and rebooted, all is golden.  So, I went into /boot/grub and noticed that the menu.lst file times had changed after the upgrade from this morning to the time of the upgrade.

Is there another reference point that an upgrade would use to update the root points in menu.lst?

Thanks,

---

### Post by reler on 2007-12-19
> **ThaRabbit said:**
> I'll upload the file I'm using (initrd.img-2.6.22-14-generic) if you wish :)That would be most kind, thanks.

---

### Post by Nem1976 on 2007-12-19
I had the same exact issue from the updates this morning.

 I booted to a 2nd install of ubuntu I had you should be able to use the live cd as well do it.  But I backed up the initrd.img-2.6.22-14-generic that was modified from this morning to initrd.img-2.6.22-14-generic.old 

Then copied the initrd.img-2.6.22-14-generic.bak to initrd.img-2.6.22-14-generic and rebooted

I then had to fsck my drive since it had issues from be trying to boot it and after it cleaned the drive I'm back up and running.

---

### Post by MightyMe on 2007-12-19
Ok I tried something that worked with help from previous posts. Don't know if this is the correct way of doing it though. Any feedback would be appreciated.

1. Start LiveCD and mount you disk.
2. Goto /boot directory and rename "initrd.img.2.6.22-14-generic" to something else. Then rename the backup file "initrd.img.2.6.22-14-generic.bak" to "initrd.img.2.6.22-14-generic". (Check /boot/grub/menu.lst to get the file name right)
3. Reboot

Worked for me and the interesting thing is that after having logged in and run the update manager - no kernel upgrades were listed. Have they been removed or has my kernel actually been upgraded?

---

### Post by didli on 2007-12-19
> **ThaRabbit said:**
> I'll upload the file I'm using (initrd.img-2.6.22-14-generic) if you wish :)
I will apreciate it too.

---

### Post by ThaRabbit on 2007-12-19
I've sent the both of you a PM with a link.

Regarding people renaming their .bak files... It seems to me that you are reloading your older kernel, though I could be wrong. It may be that the system thinks it has installed the latest kernel while it is actually running the older version :confused:

I'm not too familiar with this process, perhaps somebody with some more advanced knowledge can help out here.

---

### Post by reler on 2007-12-19
Thanks though I gotta say that I'm not too hopeful here: remember, when I reboot I get "Error 17: cannot mount selected partition". So as I said earlier, that seems to be the initial problem.

I'll see what happens though. Thanks.

Reler

---

### Post by VladimirCZ on 2007-12-19
> **didli said:**
> Same problem here but I don't have an old kernel to boot ...

The same situation here. No old kernel ...

Booting seems to freeze at a point when the kernel is connecting my DVD drive. Before this upgrade I had no problems with booting or hardware detection and support.:confused:

---

### Post by Nem1976 on 2007-12-19
> **ThaRabbit said:**
> I've sent the both of you a PM with a link.

Regarding people renaming their .bak files... It seems to me that you are reloading your older kernel, though I could be wrong. It may be that the system thinks it has installed the latest kernel while it is actually running the older version :confused:

I'm not too familiar with this process, perhaps somebody with some more advanced knowledge can help out here.


While I totally agree this may not be the best solutions it's currently the only thing that I can do to get my Work machine back up and running.  Atleast I can keep working for now and deal with possible issues later.  If someone has any better ideas on what to do then I'm all ears.

My issues is I get a message says something about my UUID not being correct.  Then I get dropped down to a (initramfs) prompt and can't do anything from there since I don't know any commands to try for that.

---

### Post by reler on 2007-12-19
As anticipated - no dice.

My INITIAL problem is that whatever the system needs is the Error 17 message. I shall hunt for this for a bit more because the rest is useless until I get past that.

Any further ideas folks ?

Thanks

Reler

---

### Post by rsambuca on 2007-12-19
> **ve1uxe said:**
> Ok, This seems weird, and maybe it's because I'm not all that familiar with Grub.  Looks like the latest update had overwritten my original /boot/grub/menu.lst file.  My ampache server was originally a dual-boot system, but I wiped out the old XP partition and went all Ubuntu.  After everything was said and done, all ubuntu was working out of (hd0,0).  After this morning's update, when my Error 22: no partition found error popped up, I noticed that the entry for all of my kernels had changed to (hd0,1).

Once I changed to (hd0,0) and rebooted, all is golden.  So, I went into /boot/grub and noticed that the menu.lst file times had changed after the upgrade from this morning to the time of the upgrade.

Is there another reference point that an upgrade would use to update the root points in menu.lst?

Thanks,

You have to change the line that starts:

# groot=(hd#,#)

That is what is referenced when grub is updated.  And you have to leave the # sign in front.

---

### Post by ThaRabbit on 2007-12-19
quick thought, is your Ubuntu actually installed on hd2,0 ?

Try checking your device.map file:
```
/boot/grub/device.map
```

Might be as simple as grub just looking for the installation on the wrong partition?

Reference:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by VladimirCZ on 2007-12-19
> **ThaRabbit said:**
> quick thought, is your Ubuntu actually installed on hd2,0 ?

Try checking your device.map file:
```
/boot/grub/device.map
```

Might be as simple as grub just looking for the installation on the wrong partition?

Reference:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

I thoutght the same and checked UUID in /boot/grub/menu.lst which is used for booting. And it was wrong :mad: :

--- menu.lst ---
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=**[COLOR="Red"]2a1c29c1-572d-4bbe-87d0-3188e8126f21[/COLOR]** ro quiet splash nohz=off
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
---

Having replaced the UUID value with the right one, I could boot and I have been using the updated system without problems since.:)

---

### Post by reler on 2007-12-19
OK, more by luck than judgment, I have got going again ... but I am not sure why !

What you need to know: this box used to be an NT box. Then I got a second hard drive and installed XP Pro on that. Then eventually, I got fed up with XP and bought a big SATA drive and installed Gutsy Gibbon on it a couple of months ago (after first temporarily disconnecting the Windows drives).

So I guess (though I am not certain now as it was a while ago) that the first grub command that I had to start Linux at that time was **root (hd0,0)**

When I reconnected the other two drives, I had to finesse the menu.lst entries to say **root (hd2,0)** so that it would boot into linux. I figured hd0 & hd1 would be my two existing PATA disks and that hd2 must be my new SATA disc with linux on it. And it worked. I added commands to give a boot option for XP too, though I rarely use it now.

So, after thinking about the "missing file" stuff earlier, I concluded that ...
> **reler said:**
> 
My INITIAL problem is that whatever the system needs is the Error 17 message. I shall hunt for this for a bit more because the rest is useless until I get past that.
So I started looking at menu.lst again. The backup that the system seems to have taken at the time when the update occurred this morning is exactly the same as the new version created - I checked this with Kompare. Then I started looking at fstab, though I am not really sure I know what it all means.

Anyway, the first entry says:
[b]# Entry for /dev/sdc1 :
UUID=blahblahblah...[/b]

I remembered from the installation that /dev/sdc indicated my SATA drive, but figured that if anything, this line in fstab should say */dev/sdc0* because all we linux people (!) start counting from zero, right ? 

I remember that I also found /boot/grub/device.map that seems to map device names for the mnemonics e.g. hd0 is /dev/sda, etc. It said **(hd2)	/dev/sdc**

This didn't seem to be changed (the date modified was from last month) but I figured that ***something*** in the upgrade had nadgered something in a way that meant that entries in these apparently interconnected files were now wrong. So I rebooted and started editing the line being used to start the system on the grub menu.

(If you don't know what this means, somebody mentioned it earlier: when the grub menu comes up with your choice of start options, before it timesout and chooses the default option, highlight the line that you want and hit "e" (for edit). Then you can do this again for any line that you want to amend on the fly).

I just started messing around with the first line, the one that had said **root (hd2,0)**. I tried changing to to hd1, but when I tried **root (hd0,0)**, it worked !

I still don't understand why.

Whilst I am here - thanks for those who helped here. Good luck to all of you still struggling in the wake of these kernel header changes.

Finally, is there a good book/web page where that I can read that will straighten me out on all these config files and stuff ? I am not very experienced when it comes to Linux, much less Ubuntu and (as must be obvious), I am blundering around quite a bit !

Thanks again

Reler

PS: prior to posting this, I see that ThaRabbit has suggested checking /boot/grub/device.map. As noted above, I did not change this and I have not (consciously) been anywhere near these files since installation. I only ever take the suggested updates from the system. Whether something has tweaked something, I cannot say.

I'm just glad to be running off my hard drive again !

PPS - Audacity still doesn't work :-(

---

### Post by reler on 2007-12-19
> **VladimirCZ said:**
> I thoutght the same and checked UUID in /boot/grub/menu.lst which is used for booting. And it was wrong :mad: :
> snip <
Having replaced the UUID value with the right one, I could boot and I have been using the updated system without problems since.:)

I assume that you mean the UUID in the fstab, like I quoted in my long post ;-)

Funny - I checked that too but it was the same !

Is it like this *every* time the kernel headers are updated ? With all of the other problems that seem to have occurred today, it looks like mayhem !

Reler

---

### Post by ThaRabbit on 2007-12-19
> **reler said:**
> PS: prior to posting this, I see that ThaRabbit has suggested checking /boot/grub/device.map. As noted above, I did not change this and I have not (consciously) been anywhere near these files since installation. I only ever take the suggested updates from the system. Whether something has tweaked something, I cannot say.

I'm just glad to be running off my hard drive again !

PPS - Audacity still doesn't work :-(

That file looks like this:
```
(hd0)   /dev/sda
(hd1)   /dev/sdb
```

I wanted you to check there if the hd no. mentionned in your menu.lst file was still correctly pointing to your linux installation. Checking devices.map should have led you to the same conclusion. The thing being that your devices.map file probably didn't change but your menu.lst file probably did change.

Somehow, your grub hd parameters got scewed :)

From the menu.lst file:
```
When you edit menu.lst, notice these lines:
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers **_will be modified**_
## by the debian update-grub script except for the default options below
.
.
.
### END DEBIAN AUTOMAGIC KERNELS LIST
```

In my case:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4f3d8b4-fd5f-4be0-8a6a-1937e0a52353 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4f3d8b4-fd5f-4be0-8a6a-1937e0a52353 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

So I'm assuming your Ubuntu boot data was also in this auto updated section, probably the cause of this all.

Why my update went perfect and yours crashed is beyond me...

Glad you got it working

---

### Post by VladimirCZ on 2007-12-19
No I mean the UUID which is used in menu.lst and this should be the same like you have in fstab for the root partition.

The right value can be acquired by a command:
ls /dev/disk/by-uuid/ -l

It was strange that in my menu.lst was some completely wrong value which even was not equal to any UUID of my partitions. Wierd, isn't it?

---

### Post by Nem1976 on 2007-12-19
Ok so I had some spare time to play with this a little more and I put the updated initrd.img-2.6.22-14-generic back into play and checked my UUID in the fstab and the menu and both are Identical.  When I try and boot it just hangs for like 5-10 mins then comes up with an error about the UUID being wrong.  

I put the initrd.img-2.6.22-14-generic from November 7th back in there and I can boot properly,  Again this is just a bandaid until I can figure out why it won't work properly with the newest update.

Anyone else have any suggestions?

---

### Post by rsambuca on 2007-12-19
> **Nem1976 said:**
> Ok so I had some spare time to play with this a little more and I put the updated initrd.img-2.6.22-14-generic back into play and checked my UUID in the fstab and the menu and both are Identical.  When I try and boot it just hangs for like 5-10 mins then comes up with an error about the UUID being wrong.  

I put the initrd.img-2.6.22-14-generic from November 7th back in there and I can boot properly,  Again this is just a bandaid until I can figure out why it won't work properly with the newest update.

Anyone else have any suggestions?

Post the output of the following three commands:

cat /etc/fstab
blkid
cat /boot/grub/menu.lst

---

### Post by Nem1976 on 2007-12-19
```
nem@nem-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=64f0d590-55a5-4d17-ae72-c4d1ae68f82f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=8c9b7d34-2e7c-47fe-9faf-5a004e320f97 /media/sda3     ext3    defaults        0       2
# /dev/sdb1
UUID=e2b10cff-bd6a-4ea2-9787-9b48232c38e6 /media/backup     ext3    defaults        0       2
# /dev/sda2
UUID=326302dd-e552-4bb9-b2dc-dfdb556f5fb6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

```
nem@nem-desktop:~$ blkid
/dev/sda1: UUID="64f0d590-55a5-4d17-ae72-c4d1ae68f82f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="326302dd-e552-4bb9-b2dc-dfdb556f5fb6" TYPE="swap" 
/dev/sda3: UUID="8c9b7d34-2e7c-47fe-9faf-5a004e320f97" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="e2b10cff-bd6a-4ea2-9787-9b48232c38e6" SEC_TYPE="ext2" TYPE="ext3"
```

```
nem@nem-desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=64f0d590-55a5-4d17-ae72-c4d1ae68f82f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=64f0d590-55a5-4d17-ae72-c4d1ae68f82f ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=64f0d590-55a5-4d17-ae72-c4d1ae68f82f ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8c9b7d34-2e7c-47fe-9faf-5a004e320f97 ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8c9b7d34-2e7c-47fe-9faf-5a004e320f97 ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Ubuntu 7.10, memtest86+ (on /dev/sda3)
root            (hd0,2)
kernel          /boot/memtest86+.bin  
savedefault
boot

```


I can boot to the 2nd partition ubuntu install I have on there that was from a couple months ago and I can atleast get to a command line from there.

---

### Post by rsambuca on 2007-12-19
> **Nem1976 said:**
> I can boot to the 2nd partition ubuntu install I have on there that was from a couple months ago and I can atleast get to a command line from there.

Sorry, I can't see any obvious errors in there.

---

### Post by 0mcg0 on 2007-12-19
Hi, I experienced the same problem after the upgrade.  I've found a work around for my system but haven't figured out how to fix it.  

I'm running a dual boot laptop system with Ubuntu on an external drive partition.  HD0,0 should boot vista and HD1,3 should give me Ubuntu.  At the grub menu I have to edit HD1,3 to HD0,3 to get Ubuntu to boot and HD0,0 to HD1,0 to get vista.  

The drive numbers somehow got switched.  I've looked at the device map file and the grub menu file and all looks ok.  How do I get things back to normal?

---

### Post by Nem1976 on 2007-12-19
> **rsambuca said:**
> Sorry, I can't see any obvious errors in there.

Ya thats why I'm confused.  I can't find anything that stands out thats causing this issue.  is there a way to force a kernal update again to see if maybe some corruption happened while it was being updated?

---

### Post by tajreed on 2007-12-19
I had this problem when I upgraded to 7.1. Could not get -14 to work. It has been fixed for me by adding "all_generic_ide" to the end of the -14 kernel in /boot/grub /menu list. Todays update replaced my  changed -14 kernel with a new one. I had to change it back by again adding "all_.....". Now all is well again.
Next time I won't accept any changes to the -14 kernel.

---

### Post by agibby5 on 2007-12-19
Here's what I did:

Ran the live cd.  Started grub.

At the grub> prompt I entered"

```
find /boot/grub/stage1
```

Then it told me:  (hd0,1)

Then I went rebooted.  **At the grub screen to choose my OS to boot into, i pressed 'e' for edit.  Then I looked for the line with the HD info, and changed it to  (hd0,1) ****this was my hard drive which the OS was actually installed on.  

I think the menu.lst file got overwritten with incorrect values... even my old kernel wouldn't boot.  Once in the new kernel, I edited my menu.lst file with the correct hard drive values... all is well now! :)

---

### Post by liberum on 2007-12-19
I'm on 7.04 but had same issue.  Grub error 17
not sure why the update did this to me but...

I used live cd
opened up the grub/menu.lst file

and... suddenly all my ubuntu entries were pointing to the wrong partition.
pointing to hd0,2 (third partition) when in reality
sda1 ntfs
sda2 linux
sda3 extended
sda5 swap

linux was on the second partition! (hd0,1)
so i changed all the entries (xp was still pointing to hd0,0) and rebooted and good to go.

First time in the last year since i started with ubuntu that i had this sort of error from an update.  usually my major problems are my fault!

---

### Post by liberum on 2007-12-19
Another thought possibly a wild goose chase
Since the update changed menu.lst to look for linux on hd0,2
I thought about it and at one point it was on that part.
originally this laptop had vista and had two partitions on it.  When i installed ubuntu it added two more with linux being on the third partition (hd0,2)

later when i realized i hated vista and removed both hd0,0 and hd0, i then installed XP which actually only created one partition at the front so now linux was on the second partition (hd0,1) while the new xp was on the first (hd0,0)

not sure if that really has anything to do with this kernel update screw up but if there is any backup somewhere that the kernel update may have used when it was installed it may have bounced my grub back to where it was when grub was first installed...

sorry to ramble just cant stop thinking about why such a silly mistake would occur from an automated update.

---

### Post by aiiee on 2007-12-19
If it helps, the update blew away my first entry in menu.lst, which I had modified to be my Windows XP partition.  Luckily I found out how to recreate it.  A hearty **** you to the careless ******* responsible.

---

### Post by rsambuca on 2007-12-19
> **aiiee said:**
> If it helps, the update blew away my first entry in menu.lst, which I had modified to be my Windows XP partition.  Luckily I found out how to recreate it.  A hearty **** you to the careless ******* responsible.

Actually, this is entirely YOUR fault.  If you looked at the grub menu.lst, it says specifically:> #
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
Just because you chose to ignore those instructions and proceeded to put the Windows entry after the line that says "### BEGIN AUTOMAGIC KERNELS LIST" is your fault that it was 'blown away".  Next time, before so harshly criticizing the developers, you should get your facts straight.  In fact the "careless ... responsible" in this case is YOU.

---

### Post by aiiee on 2007-12-19
oh ********.  The instructions are contradictory, and if you are going to be so arrogant and presumptous to think that you have the 'right' to blow away critical boot settings just because you left some cryptic muddled warning then you are too stupid to be working on something like this. How hard is it to make a backup before you overwrite a critical boot file?  No excuse.

---

### Post by liberum on 2007-12-19
rsambuca, does your statement include the error that I had?  Not sure what I did wrong, since I modified my partitions subsequent to the linux install so I had to modify grub menu to point it in the right direction.

Name calling aside, is there something I could do to avoid this in the future?

I did find this at a linuxquestions.org wiki:
"Debian manages the menu file with update-grub. This script checks which kernels are located in /boot/ and generates a menu entry for them. It adds its own configuration options to the menu.lst file. These concern the options that are given to the generated menu entries. Usually, update-grub is automatically run after kernel packages have been installed or removed (at least it's the default configuration for the sarge/testing disribution). If not, update-grub can be added as a postinst_hook and a postrm_hook in the /etc/kernel-img.conf file."

My first thought is DUH!  If I would have thought it through I would have realized that it has to update grub after a kernel change since the grub entry includes the kernel location!  Makes sense now that I have my thinking cap on.

BUT... why the modification to the partition settings? and it was just the linux partition settings not the ntfs partition.

---

### Post by shanerdaner on 2007-12-19
To solve this problem I did this

 sudo gedit /boot/grub/menu.lst


then removed the 14 kernel and the backup recovery mode  then saved it and it reboots fine now!  Anyone know if this is ok?  it works for me....  I have done it in the past and it worked also..

---

### Post by WildeBeest on 2007-12-20
The only thing the upgrade did to me was it removed my dual boot lines from menu.lst.

---

### Post by vincencollins on 2007-12-20
I don't think this is just a grub issue.  Last night I could not start after the kernel update also.  I use lilo and I had to run liloconfig from the live cd to get Ubuntu to boot.

---

### Post by liberum on 2007-12-20
Certainly seems like there is more to this.  Not sure how a community wide explanation would be distributed that would get to everyone, but I would like to know what happened.  Specifically.

Despite being back up after re-setting my partitions in the grub/menu.lst, I know realize I have no sound.

Not sure exactly why but I think this is my fault/problem.  I had to make/iinstall drivers because my laptop didnt work out-of-box, so I think I need to re-install the drivers.

When all is said and done, the simple change to menu.lst for me wasnt that big a deal, but seems like others have it worse.  I just wouldnt want to have people become so annoyed by this one screw-up (seems like a screw-up anyway to me) that they jump ship.  That's sort of how I got to ubuntu after having a hell of a time with fedora core 6.

Oh well, there is always vista.  Sorry bad joke.

Is there a higher power we can appeal to??  This has to be a problem the developers are aware of by now, since I have since multiple threads with high count viewings.

Oh well, back to work.
Ken

---

### Post by reler on 2007-12-20
> **liberum said:**
> Certainly seems like there is more to this.  Not sure how a community wide explanation would be distributed that would get to everyone, but I would like to know what happened.  Specifically.
Me too - though let's NOT instigate a witch-hunt or indulge in name-calling. I suspect that the problem was probably just a human error of some kind (and we all make those). My guess would be that the change presumes a single disk and a single OS. Just a guess.

> **liberum said:**
> When all is said and done, the simple change to menu.lst for me wasnt that big a deal, but seems like others have it worse.  I just wouldnt want to have people become so annoyed by this one screw-up (seems like a screw-up anyway to me) that they jump ship.  That's sort of how I got to ubuntu after having a hell of a time with fedora core 6.

Oh well, there is always vista.  Sorry bad joke.

Is there a higher power we can appeal to??  This has to be a problem the developers are aware of by now, since I have since multiple threads with high count viewings.
I agree - even though I am a Linux newb, I am fairly experienced with PCs and was able to plug away (with help from those here) until I stumbled across an answer. I'm still not entirely sure how this all hangs together and whether I have things in good order now. However, the next time that I see any updates referring to the kernel, I will be doing a certain amount of backing up before I apply them.

More importantly, if Linux distros generally and Ubuntu in particular are to position themselves as viable alternatives to those from people like Microsoft or Apple for the PC user in the street, there needs to be a reliable way of sorting these kinds of problem out, somewhere to go to where these boobs can be noted and suggested corrective action posted.

Or is there one already that I just don't know about ? As I said, I am a Linux newb.

Reler

---

### Post by liberum on 2007-12-20
Well, I certainly wasn't trying to start a witch hunt.  Only interested in an explanation of what happened.  Even if it's me that needs to change the way my grub is set up.

I think that linux (ubuntu in particular) is a viable alternative to MS, although I am a computer geek and love having to get things working so linux is right up my alley.  I think there are probably larger hurdles to overcome then update problems (e.g. marketing and software compatibility).  At some point, it probably is a larger battle of software patents vs. free open source software.  Okay that's as political as I want to get right now (and here).

I do backup regularly, so I am save there.  I actually use a post on I found here to backup using just tar.  Not overly complicated either.

As far as answers to my questions, I have yet to NOT find answers to my questions right here at ubuntu forums.  There are amazing and intelligent people here.  Nice to share in the vast hierarchy of knowledge that has developed here!

---

### Post by reler on 2007-12-20
> **liberum said:**
> Well, I certainly wasn't trying to start a witch hunt.
Apologies liberum - my remarks about witch-hunts and name-calling were meant as a general plea and were not directed at you. I can understand that it came over like that - I should have been more careful with my wording.

> **liberum said:**
> I do backup regularly, so I am save there.  I actually use a post on I found here to backup using just tar.  Not overly complicated either.
Can you point me in the right direction please ?

Thanks :-)

Reler

---

### Post by rsambuca on 2007-12-20
> **liberum said:**
> Another thought possibly a wild goose chase
Since the update changed menu.lst to look for linux on hd0,2
I thought about it and at one point it was on that part.
originally this laptop had vista and had two partitions on it.  When i installed ubuntu it added two more with linux being on the third partition (hd0,2)

later when i realized i hated vista and removed both hd0,0 and hd0, i then installed XP which actually only created one partition at the front so now linux was on the second partition (hd0,1) while the new xp was on the first (hd0,0)

not sure if that really has anything to do with this kernel update screw up but if there is any backup somewhere that the kernel update may have used when it was installed it may have bounced my grub back to where it was when grub was first installed...

sorry to ramble just cant stop thinking about why such a silly mistake would occur from an automated update.

You will also need to edit your /boot/grub/menu.lst file.  There is a line that says # groot=(hd0,2) somewhere in there.  That is the line that tells grub where your root folder is during menu.lst updates.  Since you have changed your partitions around, you should edit the line to look like "# groot=(hd0,1)"  This way, after the next kernel update you should be OK without having any grub errors.

---

### Post by liberum on 2007-12-20
Sure,

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

Its pretty straightfoward.  Just pay attention to what needs to be excluded from the backup.tgz (e.g. the file itself, /media directory) or you will get crazy results!  And it will take awhile usually 10-20 minutes for me.

I will share my first and comical mistake when I ran it for the first time.  I wanted a different file name than "backup.tgz" so I named it "toshiba-original-setup.tgz" or something like that.  Well, I copied and pasted the command from the link above and added "--excluded=/media"... and...

after 10 minutes or so it blew me some error.  Well the problem was that i changed the name of the backup file but I didnt change the name of the excluded file in the command.  So during the backup it was trying to backup itself, which was constantly changing... and it got a little mad.

Hope this helps!  I have found it to be the easiest and simplest way to back up files without the need of another application.

Thanks to A-Star for the TAR post to begin with!

---

### Post by liberum on 2007-12-20
thanks rsambuca!!

ill make that change right now so I dont have to deal with it again.  thanks for teaching me something.  my experience with grub has sort of been trial by fire and i only really get into it when things are working right.

Thanks again

---

### Post by rsambuca on 2007-12-20
> **liberum said:**
> thanks rsambuca!!

ill make that change right now so I dont have to deal with it again.  thanks for teaching me something.  my experience with grub has sort of been trial by fire and i only really get into it when things are working right.

Thanks again

That is basically how I learned too. :)

---

### Post by bidd on 2007-12-20
My symptoms were slightly different on this one but here's how I fixed it.

1.Boot into windows and install [http://www.fs-driver.org/]("http://www.fs-driver.org/"). 

2.Reboot back into windows, fire up explorer and browse the linux partition

3. Open up /etc/fstab and look at the UUID for my / partition.

4. Open up /boot/grub/menu.lst and replace the UUID in the linux entries so they match the entry in fstab.

5. Reboot into linux.

Disappointed that this one could happen really. Could really put people off linux.

---

### Post by snkmad on 2007-12-20
I had the same problem, and looks like i kinda figure it out.
This problem seemed to happen only to people which had changed their menu.lst file.
They changed the root (hdx,x) but didnt changed the #groot=(hdx,x) also.

When a kernel update is installed, it always look into that groot line, to know where it should install the update. 
So if you have modified your menu.lst, but didnt touched the #groot= line, it will revert all the changes you have made to your menu.lst, under that automagically section.

The quickiest solution i found here:
Boot the pc, when it reached grub, i pressed "e" on my ubuntu option.
Then another screen showed, and where it said "root (hd1,1)" i hit "e" again and changed to (hd0,1).
It booted fine to ubuntu, then i run in the terminal:
sudo nano /boot/grub/menu.lst
And did the changes, because the one i did during the boot sequence is only temporary.

Hope this helps, and please correct anything i said wrong.

---

### Post by bananabob on 2007-12-20
snkmad
I dont think that is the answer. Below is my menu.lst and as you can see i have  root (hd0,0) and my groot is # groot=(hd0,0)  and I still can not boot up with 22-14. I have to revert to 20-16.

This problem affect me every time I try to boot with 22-14.

For sometime now I have had a intermittent problem with booting which is exactly the same as is being reported by every one now. All I do is keep rebooting until I get a logon screen. But now with 22-14 I can not do that, it just won't boot at all. Hence my reversion to 20-16.

I don't think this problem is a grub problem. I think that it is in the kernal.

> 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu 7.10, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=69eb4fab-f38b-43f7-8796-39734a877b89 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by liberum on 2007-12-20
well i could never really go with the 2.6.22 kernels (which i think gutsy comes with) simply because on my laptop there are too many problems

and frankly i cannot afford to be an early adopter on some of my other boxes.

your problem seems to be more than a grub issue with the update though.  at least compared to mine.

i am however using a gutrsy vmware appliance simply because thats how i test things, but with a new LTS coming in april I think i will wait to upgrade.  I especially like the LTS' for my servers.

I typically have been afraid of kernel upgrades in the past but this is the first that gave me any trouble really, and it was all self-induced.

I had sound issues with the upgrade but that was my own thing because I have made/installed my alsa drivers post install.  Not sure how to get them to stick after upgrades. Has something to do with backporting but not fluent in that.

nighty night from ohio us of a

---

### Post by flyer40r on 2007-12-20
Just to throw my hat in the ring, I faired better, mine would start, but after the linux headers update of 12-19, my laptop fan now stays on full, and it can't find the wireless card.This install had been flawless with Feisty. Upon upgrading to 7.10, I had to edit the grub configuration to start another kernel to get it to work, but has been stable just long enough for me to start trusting it (a month). I'm pretty sure this 7.10 upgrade has survived linux header updates before. 

I don't know enough about it to know why this update would blow away all the drivers. :mad:

---

### Post by liberum on 2007-12-21
The alsa driver that I make-install for my sound card on my laptop gets broken by the kernel updates but I believe it said something about that at the end of the howto that I read in order to make the driver

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by ThaRabbit on 2007-12-21
make-installed means the program / driver was compiled against the kernell headers at that time.

Naturally, if you change the kernell, you could run into trouble... recompile against the new headers :)

---

### Post by liberum on 2007-12-21
yepper rabbit.

Because I am not linux expert and ever since I had kids my memory doesnt work well.... 

I hcreate a tarball called "toshiba drivers" with the great instructions for my video/sound/wlan drivers.    That way its simple for me to fix anything later down the road.

I am consistently amazed at how incredible the documentation for ubuntu is.

A long time ago (mid 90s) I messed around with red hat and it never was a easy as ubuntu or as well documented (given linux was still somewhat new at the time).

---

### Post by heu on 2007-12-21
well the same happened to me after applying some upgrades to 7.04 on december the 19th. I didnt really pay attention to the upgrades but they looked like some kernel upgrade. I have the following disks arrangement:

hd0 - hda1 Master - ntfs with winblows xp
hd1 - hdb1 - Slave with 3 partitions, 1 ntfs partition which i access (r-w) with ntfs-3g, one ext3 partiton with Kubuntu and the swap partition.

The fstab was already configured using UUIDS and everything was working fine. After rebooting I get an error 22 (no such partition) from grub. I reboot on winblows and check out the menu.lst file and i realize that it had just been edited. There was a back up file and the date and time were those of the time at which the upgrade had been applied. The parameters looked alright though. The fstab file had not been altered and as i said UUIDs were bering used through the whole fstab. All it took to solve the problem was change the grub lines to boot linux from hd1,1 to hd0,1 but curiously the mapping i use on grub to boot winblows didnt need to be touched? Everythings working fine (other than the hard disks are refered to as sda and sdb but it didnt affect me) now but the whole issue is kind of annoying since it seems a reoccurring issue. Does anybody know what caused it and whats the logic behind the changes, which seemed to affect grub more (and they are not reflecting the real jumpering of the hard disks) than anything..at least on my system?
__________________

---

### Post by vincencollins on 2007-12-28
I am now having a problem with my card reader not being recognized and mounted.  Any suggestions?

---

### Post by wonkawilly on 2007-12-30
Hi,

I had an ubuntu server 7.10 fresh installation on a dual processor/quad core Intel Vernonia SC5299WS with a  Quad Core Intel E5335 2,00GHz. 

After last upgrading, the computer was unable to boot with the message 
(initramfs) mount /dev/sdaX /root
mount: Mounting /dev/sdaX on /root failed: Device or resource busy
 
Unfortunately, I don't have any other kernel  (the original one coming with 7.10 server was the only one I haver had on thic computer, and was working perfectly before the upgrade!).

Can someone please suggest me how to recover the system (both using the same 2.6.22 original kernel or installing an older one)? I'm sorry, but I'm rather new with ubuntu linux.

By using the recovering procedure (with the recover kernel option in the original grub menu) shows the same problem (both with the server and the generic kernel).

Regards

---

