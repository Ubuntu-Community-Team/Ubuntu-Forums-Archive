---
title: "Problems restoring GRUB 2"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by KillerSponge on 2009-11-18
Hello,

My MBR got messed up by another installation, and now I'm trying to restore GRUB(2) to load my Ubuntu 9.10 installation again. Trouble is, all the guides I found on Google don't seem to work. All the guides for 9.10 want you to do the same: you have to mount the partition you want to boot into somewhere, and then install Grub by doing

```
sudo grub-install --root-directory=/mountpoint /dev/sda
```

My harddisk is sda, and the partition I want to install it to is sda1. I'm getting these error messages:

```
grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!
grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
```

Does anyone have any idea how to fix this? :(

---

### Post by darkod on 2009-11-18
Dumb question: You did mount first right? :)

---

### Post by KillerSponge on 2009-11-18
I think so.

```
sudo mount /dev/sda1 /media/root
```

(after first creating /media/root of course). :)

---

### Post by kansasnoob on 2009-11-18
I found this simple and straight forward:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

It's worked for me numerous times ;)

---

### Post by darkod on 2009-11-18
The command I've seen is like:

mount /dev/sda3 /mnt

Maybe that's your problem. I haven't been in situation to need to restore so far, knock on wood. :)
This article is the shortest and most precise I've seen, both points 2) and 3) are interesting. It might work
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by KillerSponge on 2009-11-18
I'm not sure if it worked. It said it installed fine, and it does give me a grub menu when I reboot, but it looks like the old grub menu that was there before I messed up the MBR. It still displays the Ubuntu installations from a harddrive I removed, and when I try to boot the installation that is still there, it gives me nothing but a black screen.

Does this maybe has to do with the fact that the harddriver sequence changed (the harddrive with the working ubuntu installation is now sda, where it previously was sdb)?

---

### Post by darkod on 2009-11-18
It might. Check grub.cfg to see where it is looking at what, but be careful, you are NOT supposed to edit that file. The methods to edit grub2 are different.
The file is in /boot/grub/ I think.

---

### Post by KillerSponge on 2009-11-18
That seems to be the problem indeed. It tries to boot to hd(1,1), while the only working installation is on hd(0,1). How can I change this? I know I'm not supposed to edit the file directly, and update-grub can't be run from the live-cd as far as I can tell (gives the error message "grub-probe: error: cannot find a device for /."). I tried running the command after I chroot'ed into the mounted partition, but that gives the same error.

---

### Post by kansasnoob on 2009-11-18
If you follow the steps in that link:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

And after running "grub-install /dev/sdX" and maybe "grub-install --recheck /dev/sdX" also run update-grub.

**[COLOR="Red"]Be sure and replace the sdX with proper location![/COLOR]**

---

### Post by darkod on 2009-11-18
The file 10_linux (spelling) is controlling the ubuntu boot. Open it with:
sudo gedit /etc/grub.d/10_linux

and see if you can change it manually. Make a backup copy first. After the change, save and close the file, then run:
sudo update-grub (needed to run after any change to grub2 config files)

---

### Post by KillerSponge on 2009-11-18
I don't really see anything in that file that could help. Also, I can't run update-grub (see previous post) :( Any other ideas on how to change the devices in grub.cnf?

Thanks for all the (fast!) help so far!

---

### Post by kansasnoob on 2009-11-18
Also remember that drives are numbered the same as in legacy (ie: sda = hd0) but partitions actually begin with one (1).

So sda1 in grub2 = hd0,1.

---

### Post by KillerSponge on 2009-11-18
I know, and I saw in grub.cnf that the entry points to hd(1,1), which is wrong, but I don't know how to fix that (other than manually editing the file, which is very much forbidden, or so I've heard ;) )

---

### Post by darkod on 2009-11-18
Sorry, forgot about UUID for a moment. In fact with new grub2 the UUID is more important now. (hd0,1) or (hd1,1) is not that relevant. You can check UUID for all partitions with:
sudo blkid

Then go in 10_linux or grub.cfg and see whether the UUID code is an EXACT match. You could also post the part of 10_linux where 2.6.31 is mentioned (ubuntu) if you need help with that.

---

### Post by darkod on 2009-11-18
From all of this it sounds like grub2 didn't actually get reinstalled. Go back to my post #5 and try the procedure once more, it's very precise. It should work and install new grub2 on your MBR. I am talking about option 2) from that link, Reinstall from liveCD.

---

### Post by KillerSponge on 2009-11-18
The UUID is correct in grub.cfg. But booting into that installation still doens't work. Can't it have anything to do with the hd(1,1) that should actually be hd(0,1)? And if so, how can I change it? :)

---

### Post by kansasnoob on 2009-11-18
> **KillerSponge said:**
> I don't really see anything in that file that could help. Also, I can't run update-grub (see previous post) :( Any other ideas on how to change the devices in grub.cnf?

Thanks for all the (fast!) help so far!

You should be able to run "update-grub" if you mount and chroot as explained in that tutorial.

---

### Post by KillerSponge on 2009-11-18
> **kansasnoob said:**
> You should be able to run "update-grub" if you mount and chroot as explained in that tutorial.

I figured that too, but alas. When I do that, it gives me:

```
grub-probe: error: cannot find a device for /.
```

:(

---

### Post by darkod on 2009-11-18
Sorry, have no idea. If it's correct it should work. I still think you should try reinstalling grub2. Here there are also good and clear steps:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Item 13, Reinstalling from LiveCD.

If your reinstall of grub2 was successful few moments ago, the "new" grub.cfg definitely can not point to a hard drive that is no longer even connected, right?

If you boot with livecd and do sudo fdisk -l does it show your hdd as sda or sdb?

---

### Post by kansasnoob on 2009-11-18
I think it's time we look at the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by darkod on 2009-11-18
Or maybe drastic measures. :)
Make a copy of grub.cfg and edit it with sudo gedit. Change the (hd1,1) that you can see in (hd0,1) as you think it should be. Since the UUID is correct, no need to edit that. Do NOT run sudo update-grub afterwards. Just reboot and see if Ubuntu will boot from the menu.
If that works, that is only a short term fix because you still have to find what is making the wrong entry. Otherwise it will be there again first time you run update-grub. But at least it will be easier to troubleshoot from within your ubuntu.

---

### Post by KillerSponge on 2009-11-18
darkod, when I try the method in that thread, I get this error:

```
grub-probe: error: cannot find a device for /boot/grub
```

Is it worth mentioning that fdisk -l mentions my sda1 partition as a "GPT" system and doesn't seem to notice my swap partition? Does this have something to do with the fact that it is a 2TB disk?

Oh, and I attached the results from that script, hope it helps :)

---

### Post by darkod on 2009-11-18
Yes, it does seem related to GPT and 2TB. By the way, GPT is not error, it seems that is sort of partition table for large drives.
You need to start googling for grub2 and GPT. I think that's your issue.
Also, in the results.txt it seems there is residue of grub1 on your drive, hence the entries in grub menu of 8.10 that doesn't even exist any more.
At the end of results.txt you can clearly see you have grub.cfg and stage2. stage2 is not used in grub2 any more, different principle.
Nothing I could find on google with quick look.

PS. What do you think of the "drastic" measure from my post #21? Wish to try it?

---

### Post by kansasnoob on 2009-11-18
OK, obvious problems:

> Partition           Start           End          Size System
/dev/sda1              34 3,897,261,752 3,897,261,719 Linux (usually)
/dev/sda2   3,897,261,753 3,907,027,378     9,765,626 Linux Swap

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="62f16afb-0772-4d6f-a680-4afd857e27db" TYPE="ext4" 
/dev/sda2: UUID="429ee6d5-c08a-4532-870b-72ed3dcc7091" TYPE="swap" 

Nothing else! You have nothing but Ubuntu / & Swap according to that, and they're both on primary partitions, eh? Why?

then:

> # / was on /dev/sdb1 during installation
UUID=62f16afb-0772-4d6f-a680-4afd857e27db /               ext4,acl    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=62793593-30c3-4e5b-b799-8677da45ccd0 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=429ee6d5-c08a-4532-870b-72ed3dcc7091 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Notice the totally different #s?

What's up? What exactly did you do?

Post the current output of:

```
sudo fdisk -l
```

And if it's only one drive as shown in that:

```
sudo parted /dev/sda print
```

Was this a failed external drive install?

---

### Post by darkod on 2009-11-18
If you didn't pick it up in other posts, he removed one drive. Plus it seems there are traces of old 8.10 installation and stage2 file which doesn't even belong in grub2.

I noticed the different UUID of the swap files but I assume he had one on the removed drive too. He really got himself into a mess. :) I'm not smart enough for this. :)

---

### Post by KillerSponge on 2009-11-18
I tried the 'drastic measure', but it didn't change anything :(

About what exactly I did:

I have a mediacenter which had one 1TB drive with Ubuntu 8.10. I wanted to enlarge that to 2TB, but I don't want to have more than one drive at a time in it (since it is always on). But, I don't have another drive large enough to backup all the data on the 1TB drive. So, I put the two drives together in the mediacenter, and made a clean install of Ubuntu 9.10 on the 2TB drive. After that, I copied all the data from the 1TB drive, and removed it. It was then that I started having trouble...

I guess I'll just Google around a bit on the GPT bit.

---

### Post by darkod on 2009-11-18
And now you know not to do that again. :) The strange thing is that UUID identification numbers were introduced just for this situation. You can move drives around, add, etc, and it should still work because it finds the drive by UUID.
Something is really messed up on your system though. :(

---

### Post by KillerSponge on 2009-11-18
Damn it, I really don't want to reinstall the system... That was a lot of wasted effort. :( 

Oh well... Thanks for all the help though!

---

### Post by meierfra. on 2009-11-18
Try this: 

mount /dev/sda1 at /media/root just as before. Then


```

sudo --bind /dev /media/root/dev
sudo --bind /proc /media/root/proc
sudo --bind /sys /media/root/sys
sudo chroot /media/root
grub-install  --force --recheck /dev/sda

```

---

### Post by rfugger on 2011-07-22
If anyone else has this problem, the solution is to create a BIOS boot partition for GRUB2 to use *before* attempting grub-install:

[http://ubuntuforums.org/showthread.php?p=7557255](http://ubuntuforums.org/showthread.php?p=7557255)
[http://en.wikipedia.org/wiki/BIOS_Boot_partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition)

Once that is done, grub-install should work, and then update-grub to restore the menus.

---

