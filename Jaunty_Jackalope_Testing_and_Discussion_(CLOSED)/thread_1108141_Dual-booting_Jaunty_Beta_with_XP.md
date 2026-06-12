---
title: "Dual-booting Jaunty Beta with XP"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by itsjustarumour on 2009-03-27
Hi All,

Well, I've just taken the plunge and downloaded the new 9.04 Beta (32 bit) - and I want to install it to dual boot on my Win XP laptop. 

I've done this many times before and everything has been very simple, straightforward and intuitive.

However with Jaunty, when I get as far as the Partition Manager there is no option for "Guided resize and use freed space", and also no other options for resizing that I can see (I've tried booting from the CDROM to the Jaunty Desktop, and running the "Install" Desktop icon but same thing).

Is there something blindingly obvious that I'm missing, or is not possible to resize partitions and dual-boot at this stage?  Any wisdom would be welcome - perhaps it IS just me being a numpty! 

Best Regards,

itsjustarumour

---

### Post by ELD on 2009-03-27
I managed to do it using the manual resize option, dual booting fine here.

---

### Post by mamamia88 on 2009-03-27
there wasn't that option?  for me there was.  try using gparted to schrink your windows partition to free up space for ubuntu then create an ext4 partition and install jaunty on that

---

### Post by itsjustarumour on 2009-03-27
> **ELD said:**
> I managed to do it using the manual resize option, dual booting fine here.

Hi ELD, thanks for the post.

Well, I've selected "Specify partitions manually (advanced)", so I'm looking in there. The HDD is 160GB, I've completely wiped it and done a fresh XP install.  The partitions I have are:

/dev/sda1 (ntfs) 160031MB unknown
free space -     8MB

If I highlight /dev/sda1 the options for "new partition table" and "new partition" are greyed out.  If I select the free space, I can't increase it, only (it appears) create a partition of 8MB or LESS).  How did you manage it?

Best Regards,

itsjustarumour

---

### Post by itsjustarumour on 2009-03-27
> **mamamia88 said:**
> there wasn't that option?  for me there was.  try using gparted to schrink your windows partition to free up space for ubuntu then create an ext4 partition and install jaunty on that

Hi mamamia88,

No, there definitely wasn't that option (I'll see if I can get a screenshot to post up here).  In all the how-to's I've looked at, this option exists eg Psychocat's at [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I tried using GParted to shrink the Windows partition, I got the arrows to "drag" the slider-type-thing to change the partition sizes but it didn't do anything...

---

### Post by ELD on 2009-03-27
> **itsjustarumour said:**
> Hi ELD, thanks for the post.

Well, I've selected "Specify partitions manually (advanced)", so I'm looking in there. The HDD is 160GB, I've completely wiped it and done a fresh XP install.  The partitions I have are:

/dev/sda1 (ntfs) 160031MB unknown
free space -     8MB

If I highlight /dev/sda1 the options for "new partition table" and "new partition" are greyed out.  If I select the free space, I can't increase it, only (it appears) create a partition of 8MB or LESS).  How did you manage it?

Best Regards,

itsjustarumour

From what i remember you will need to select the XP partition for use, and then down size it using those tiny little arrows next to it's size.

I am not sure if that will work but it worked when i wanted to make my NTFS movies partition bigger, so no reason why it won't work making an XP partition smaller. Hope that helps.

---

### Post by itsjustarumour on 2009-03-27
> **ELD said:**
> From what i remember you will need to select the XP partition for use, and then down size it using those tiny little arrows next to it's size.

I am not sure if that will work but it worked when i wanted to make my NTFS movies partition bigger, so no reason why it won't work making an XP partition smaller. Hope that helps.

Nope, not working alas :confused:

Heres a couple of screenshots, the first taken from Psychocat's how-to showing the typical options, and the second showing what I'm getting - ie, no "Guided" option!

---

### Post by ELD on 2009-03-27
Can you explain how my method didn't work? It works perfectly for me buddy.

Go to specify partitions manually, select your xp partition (double click it i think?) and a box should come up, select use it, then use the small arrows by the size and size it down, should work fine.

---

### Post by andrewabc on 2009-03-27
The way I do it, is make sure winxp partition is defragmented (so all files are in one spot)

When using livecd and get to manual partitions, you have to shrink winxp partition to get free space. From this free space you will create a ext3 (or ext4) partition, and also a swap partition.
the ext3 needs to be set as /

---

### Post by ELD on 2009-03-27
> **andrewabc said:**
> The way I do it, is make sure winxp partition is defragmented (so all files are in one spot)

When using livecd and get to manual partitions, you have to shrink winxp partition to get free space. From this free space you will create a ext3 (or ext4) partition, and also a swap partition.
the ext3 needs to be set as /

My post is basically saying that :)

---

### Post by mamamia88 on 2009-03-27
weird i could have sworn there was an option anyway i created the partitions via gparted in live cd then installed ubuntu onto the ext4 partions leaving my windows partition untouched

---

### Post by andrewabc on 2009-03-27
> **mamamia88 said:**
> weird i could have sworn there was an option anyway i created the partitions via gparted in live cd then installed ubuntu onto the ext4 partions leaving my windows partition untouched

If your partitions were already made, then you would not need to create more partitions. Windows would install on the partition you select.

When installing ubuntu go to manual and select the ext4 partitions you already created and install it to there.

---

### Post by mamamia88 on 2009-03-27
yeah i know i had finished an experiment with fedora and decided to go back to ubuntu so i wiped my hd and created 3 partitions 1 for home 1 for root and the other for xp installed xp first then installed ubuntu so xp would automatcially get added to grub

---

### Post by itsjustarumour on 2009-03-27
> **ELD said:**
> My post is basically saying that :)

I'm really sorry chaps, but this still doesn't seem to be working as it should.

- I've de-fragged my XP installation first
- I haven't done anything to create extra partitions, I simply installed Windows XP on a blank hard disk, and then tried to install Ubuntu on there as well (general consensus seems to be this is the best way of doing it as it adds XP to the Grub menu automatically afterwards, and its always worked perfectly for me before).
- If I try and install directly from the live CDROM (or boot from the CDROM to the Jaunty Desktop and use the "Install" icon), I don't get any options to resize either of the 2 partitions, and I don't get any little arrows to drag or anything.
- If I boot from the CDROM to the Jaunty Desktop and try using GParted to change the size of the XP partition, I do get little arrows, but dragging them doesn't actually do anything/the relevant arrows are greyed out.

:confused:  :confused:  :confused:


EDIT - Screenshot Attached

---

### Post by itsjustarumour on 2009-03-27
> **mamamia88 said:**
> weird i could have sworn there was an option anyway i created the partitions via gparted in live cd then installed ubuntu onto the ext4 partions leaving my windows partition untouched

Hmmm... it seems I can't do that.  As my XP partition takes up 99% of the drive by default, I can't leave it untouched - I have to shrink it - but the little arrow is greyed out. And conversely, I can't INCREASE the size of the 8MB free partition, as the arrow to make it larger is also greyed out.


EDIT - Screenshot Attached

---

### Post by Sylslay on 2009-03-27
Somebody try wipe all hdd, than istall fresh Windowz XP on fiew GB, upgrade windowz to latest patch .... he he and than run Live CD and create new Swap and EXT4 partion.
Question is?
Any hasle with GRUB boot sector? Seen some post about that ext4 is not good for GRUB, and they recken to use small ext3 only for GRUB files.
PS.Did not use dual boot for 4 months, and figure out that I need some windowz to upgrat some phone softwere and data card.

---

### Post by IsmailBhai on 2009-03-27
no guided option because you don't have any free space left.  open up gparted and create a free space first.

---

### Post by andrewabc on 2009-03-27
itsjustarumour

I've had this problem before as well.
What happens when you click on "edit" for the ntfs?
Can you manually enter the size of it? If so, put in a smaller size (to resize). That should make some free space after you "apply changes". Then you can create new partitions. out of free space

---

### Post by itsjustarumour on 2009-03-27
> **andrewabc said:**
> itsjustarumour

I've had this problem before as well.
What happens when you click on "edit" for the ntfs?
Can you manually enter the size of it? If so, put in a smaller size (to resize). That should make some free space after you "apply changes". Then you can create new partitions. out of free space

Thanks for the post.  Nope - can't change it that way.  Stick a number in the box, "Resize" button is greyed out, and when I hit "Return" the number just goes back to what it was.

---

### Post by itsjustarumour on 2009-03-27
Everyone, thanks for your posts, but after a bit of research it seems I'm getting something very similar to this known bug:

"Jaunty install resize partition fails on Latitude D630"

[https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/326604](https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/326604)

My laptop is actually a HP Compaq 6720s, but seems to be the same thing.  My symptoms are different, but the output I get when running a test is similar to these guys.

ALTERNATIVELY - it might be the same problem as this post:

[http://www.gs1.ubuntuforums.org/showthread.php?t=1017684](http://www.gs1.ubuntuforums.org/showthread.php?t=1017684)

---

### Post by andrewabc on 2009-03-27
Go to:
system->admin->partition editor
And try resizing winxp partition from there. Make sure the winxp partition is not mounted (right click on it and tell it to unmount if no options are available).

---

### Post by ELD on 2009-03-28
In this shot -> [http://ubuntuforums.org/attachment.php?attachmentid=107798&d=1238185030](http://ubuntuforums.org/attachment.php?attachmentid=107798&d=1238185030)

That is what i was talking about, select NTFS and then there will be arrows next to the size of the partition since you have now selected to use it.

---

### Post by itsjustarumour on 2009-03-28
@ELD I did find the little arrows, however I couldn't operate them as they were greyed out...

@All However, having read some forum posts that gave me some ideas, I HAVE now had some success!  :)

- I booted into XP, and disabled the memory swap space
- I then de-fragged the HDD again (3rd time!)
- I then opened a CMD prompt in XP and ran a chkdsk /r

... and this appeared to find and fix some disk errors (I was suprised about this, its a fairly new laptop which had just had XP and Intrepid installed with no problems before I completely wiped it to start again)  

Anyway, when I tried to install Jaunty again, everything went just fine! I got a "guided" option this time to resize the XP partition (it also explained exactly what it was doing, that this was the correct option to have 2 OS's installed side by side and both accessible from the GRUB menu etc etc - all very well laid out and reassuring!). And the little resizing arrows that had previously been greyed suddenly worked - yay! :) 

Everything appeared to go perfectly... except now when I reboot, XP is missing from my GRUB menu.  I've tried a few fixes for this so far to no avail, and I'm starting to worry that the Jaunty installer has overwritten something it shouldn't have done... XP is installed first on the disk btw, as I believe it always should be.

Hmmm... scratching my head now!

---

### Post by andrewabc on 2009-03-28
grub problem is very weird. I've never had that problem.

If you do some google searches I'm sure others have had the same problem and could probably manually edit grub, or somehow have grub redetect installed OSs

---

### Post by itsjustarumour on 2009-03-28
> **andrewabc said:**
> grub problem is very weird. I've never had that problem.

If you do some google searches I'm sure others have had the same problem and could probably manually edit grub, or somehow have grub redetect installed OSs


Well, thanks for the help anyway Andrew.  I've never had a problem with GRUB before either, I've done quite a lot of dual boots and they've all worked fine.  I've tried fixes from a couple of forum threads, but no joy so far.  But I'll keep looking...

Cheers,

Itsjustarumour

---

### Post by itsjustarumour on 2009-03-28
Heres a copy of my menu.lst, and a screenshot of my partition setup. 

Whatever I do I still can't get XP to appear in my GRUB menu... theres no mention of XP in menu.lst, and I can't mount my XP/ntfs partition.



> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=92c1e9c0-3744-4398-909c-acbe083736fc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=92c1e9c0-3744-4398-909c-acbe083736fc

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		92c1e9c0-3744-4398-909c-acbe083736fc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=92c1e9c0-3744-4398-909c-acbe083736fc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		92c1e9c0-3744-4398-909c-acbe083736fc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=92c1e9c0-3744-4398-909c-acbe083736fc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		92c1e9c0-3744-4398-909c-acbe083736fc
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by andrewabc on 2009-03-28
When in ubuntu
places menu->removable media->any partitions listed there? Might be "187.1gb Media" or label of partition "Acer" ?

---

### Post by itsjustarumour on 2009-03-29
> **andrewabc said:**
> When in ubuntu
places menu->removable media->any partitions listed there? Might be "187.1gb Media" or label of partition "Acer" ?

All sorted now!

I could see the XP partition like you say, but I couldn't mount it - was getting an error message as per attached screenshot. I downloaded a couple of tools that would check the XP ntfs partition for errors from within Ubuntu, but I couldn't find anything wrong.  So I got my XP disk out, booted in Recovery Console and ran chkdsk /r from there... it DID find (and correct) a couple of disk errors.

Rebooted, XP was still missing from the GRUB menu, but once in Ubuntu I could now mount the XP partition OK.  From there it was easy enough to add the following to the very bottom of my /boot/grub/menu.lst (below where is says "### END DEBIAN AUTOMAGIC KERNELS LIST"):

> title Windows XP
root (hd0,0)
makeactive
chainloader +1

... and XP was appearing in the GRUB menu just as it should. :):):)

Anyway - thanks for you help, and enjoy your Sunday!

Cheers,

Itsjustarumour

(Marking thread as solved)

---

### Post by andrewabc on 2009-04-15
> **itsjustarumour said:**
> @ELD I did find the little arrows, however I couldn't operate them as they were greyed out...

@All However, having read some forum posts that gave me some ideas, I HAVE now had some success!  :)

- I booted into XP, and disabled the memory swap space
- I then de-fragged the HDD again (3rd time!)
- I then opened a CMD prompt in XP and ran a chkdsk /r

... and this appeared to find and fix some disk errors (I was suprised about this, its a fairly new laptop which had just had XP and Intrepid installed with no problems before I completely wiped it to start again)  

Anyway, when I tried to install Jaunty again, everything went just fine! I got a "guided" option this time to resize the XP partition (it also explained exactly what it was doing, that this was the correct option to have 2 OS's installed side by side and both accessible from the GRUB menu etc etc - all very well laid out and reassuring!). And the little resizing arrows that had previously been greyed suddenly worked - yay! :) 

Everything appeared to go perfectly... except now when I reboot, XP is missing from my GRUB menu.  I've tried a few fixes for this so far to no avail, and I'm starting to worry that the Jaunty installer has overwritten something it shouldn't have done... XP is installed first on the disk btw, as I believe it always should be.

Hmmm... scratching my head now!

Thanks for this info. I tried installing ubuntu tonight and I was unable to resize partition! There was 100gb free on the xp drive. Tried gparted, and installer but neither worked. I defragged xp. checkdisk said it was clean and no errors (without even checking! aka the 60 minute check every sector didn't happen, it just said everything was fine.). So I have to do diskcheck some other way. hopefully the command prompt works.

---

