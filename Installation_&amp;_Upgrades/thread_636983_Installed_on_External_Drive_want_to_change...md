---
title: "Installed on External Drive want to change.."
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by Mular on 2007-12-10
Hey guys,

Heres the deal I installed Ubuntu 7.10 on an external drive because I just wanted to mess with it.. I actually really like it.. And due to the way my external drive works (spins itself down after 10mins of inactivity -manufactor says this can't be changed) I really would like to move the OS since USB isn't as fast and plus its putting a lot of wear on my hard drive atleast I think it is lol..

 I would like to repartition part of my internal drive and move over the linux install can you do that? Or would I have to wipe everything and reinstall?

Thanks!

---

### Post by logos34 on 2007-12-10
post the output from these two commands:

sudo fdisk -l

df -h

---

### Post by Mular on 2007-12-10
Not home yet but I will defin do it when I do..

I mean how I have it installed, am I wrong in doing so? I mean what I am really concerned about is ruining my hard drive early from the spinning up and down stuff.. Not really a big deal running it through usb I guess the system would be faster though if I had it on the internal?

Is moving the system without having to reinstall to a different drive possible ?

---

### Post by logos34 on 2007-12-10
yes, you can move it by making an image/clone.  You copy it over using dd command or a utility like partimage or clonezilla (the latter apps are nice in that they only copy the USED blocks and not empty disk space).  The partitions have to be the same size though, so you need to make sure that you can clear enough space on the internal for two extra partitions (limit is 4).  It'll definitely run faster on the internal, but I've had ubuntu on usb and didn't notice the speed diff all that much.  From what I've read the issue of spin up wear and tear on the drives is exaggerated, but I may be wrong.  But you may be able to set the spinup/down with hdparm, in spite of what the manufacturer says...worth checking.

from the manpage for hdparm:
>  **-S**     Set  the  standby (spindown) timeout for the drive.  This value
              is used by the drive to determine how long  to  wait  (with  no
              disk  activity)  before  turning  off the spindle motor to save
              power.  Under such circumstances, the drive may take as long as
              30  seconds to respond to a subsequent disk access, though most
              drives are much quicker.  The encoding of the timeout value  is
              somewhat  peculiar.   A  value of zero means "timeouts are dis&#8208;
              abled": the device will not automatically enter  standby  mode.
              Values  from  1 to 240 specify multiples of 5 seconds, yielding
              timeouts from 5 seconds to 20 minutes.  Values from 241 to  251
              specify  from  1  to  11 units of 30 minutes, yielding timeouts
              from 30 minutes to 5.5 hours.  A value of 252 signifies a time&#8208;
              out of 21 minutes. A value of 253 sets a vendor-defined timeout
              period between 8 and 12 hours, and the value 254  is  reserved.
              255  is  interpreted  as 21 minutes plus 15 seconds.  Note that
              some older drives may have very  different  interpretations  of
              these values.

---

### Post by Mular on 2007-12-10
Oh hrm I would rather use the external drive if the spin down thing could be taken care of, thats really my only concern. It seems plenty fast to me, the only real issue I had was I tried using Wine and running Starcraft just to see and it ran kinda choppy - granted my machine is a p4 with 2gigs of ram so I should run it just fine - not sure if this was a wine thing since it is emulating or if thes USB. Not really a big deal though since thats why I kept windows just curious.

So how would I put this command in? I tried some of the harddrive commands and it error'd out, how do I find out what hard drive I need to is that where the fdisk -l comes into play?

---

### Post by logos34 on 2007-12-10
yep, fdisk will show drive designation. e.g. if usb is sdb, then

sudo hdparm -S<value> /dev/sdb

Here's an excellent page:
[http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance)
(--> 'spindown' section)

---

### Post by Mular on 2007-12-11
Hey just wanted to thank you for your help. Last night I ended up just reformatting the drive because you know what grub wasn't working right and I just couldn't get it to work because sometimes when first booting up my USB drive wasn't intiated so grub wouldn't work right even if it was configured properly.

It went well though, I used Partition Magic in windows to move around some of my partitions. The only oddity was that when I first went to install Ubuntu on my external drive I picked my big partition as my linux swap (since it didn't say format I figured it would be fine) anyways now windows sees it sometimes as a linux swap instead of NTS file system =/

Anyways so ubuntu is now on my internal drive, I made 3 partitioned like I read here in one of the posts - one for /root /home and /boot. So far so good! The only real annoying issue I had was the splash screen would make my screen so undisplayable singnal. After searching a bit I found a nice post on how to fix that..

I have a favor to ask though, I been struggling with mounting things. I know there are scripts out there that do it for you, but I really want to learn. So I figured out for the most part how to mount an iso file, but what I don't know is say I have an external drive mounted (since that mounts auto when you plug it in) So I unmount it, now how do I get it back.. How do I figure out what drives are connected to my system and then how to mount them?

Thanks again

---

### Post by logos34 on 2007-12-11
> **Mular said:**
> Hey just wanted to thank you for your help. Last night I ended up just reformatting the drive because you know what grub wasn't working right and I just couldn't get it to work because sometimes when first booting up my USB drive wasn't intiated so grub wouldn't work right even if it was configured properly.

It went well though, I used Partition Magic in windows to move around some of my partitions. The only oddity was that when I first went to install Ubuntu on my external drive I picked my big partition as my linux swap (since it didn't say format I figured it would be fine) anyways now windows sees it sometimes as a linux swap instead of NTS file system =/

Anyways so ubuntu is now on my internal drive, I made 3 partitioned like I read here in one of the posts - one for /root /home and /boot. So far so good! The only real annoying issue I had was the splash screen would make my screen so undisplayable singnal. After searching a bit I found a nice post on how to fix that..

I have a favor to ask though, I been struggling with mounting things. I know there are scripts out there that do it for you, but I really want to learn. So I figured out for the most part how to mount an iso file, but what I don't know is say I have an external drive mounted (since that mounts auto when you plug it in) So I unmount it, now how do I get it back.. How do I figure out what drives are connected to my system and then how to mount them?

Thanks again

ok, glad it's more or less working now.

The commands

**mount**

and 

**sudo fdisk -l**

will show all the drives connected and partitions currently mounted.

To remount external usb partition make a permanent mountpoint and manually mount it there (as opposed to '/media/usb' or '/media/disk' where the system automounts it when hot-plugged):

sudo mkdir /media/myusb 

sudo mount -t ext3 /dev/sdb1 /media/myusb

Is that what you were looking for?

---

