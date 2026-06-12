---
title: "Dapper, Edgy and Feisty in one box???"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by albesan on 2007-02-14
Hello team,

Been looking around, found a few how to's, but I still have some questions...

I'm running Dapper. I have an internal 120Gb disk. I'm wanting to keep using Dapper but I would like to have testing systems of Edgy and Feisty within the same disk. Until I can move onto one of them safely.
What would be a partition scheme to do this like? 
I'm new to all this, I'm guessing the boot partition will be only one, right?
What about the swap partition?

If anybody has any ideas they'll be welcome.

thanks

a.

---

### Post by jerrylamos on 2007-02-14
Well I've got Dapper, Edgy, Xubuntu and Win98 in one box and am usually running Feisty daily updates from CD to follow some bugs I've found.  That's quad boot plus CD boot too.

What happens is Grub gets control from the master boot record and then gives you the choice of which Linux or Win98 to run.  This is all in /boot/grub/menu.lst (that's a lower case Lst) in whichever linux that was installed last.  

As far as I can tell, any of the Linux's can use the same swap partition tho I haven't tried that.

The only restriction on who goes in what partition is Win98 or XP since they will only boot from partition 1 on the first hard disk.  Windows doesn't have a problem by being booted up by Grub.

I find 20G is gobs of room for Linux except whichever one may have digital picture files in it. I actually have 3 hard drives, one is partitioned 4G for Win98 ( printer head clean and cartridge change utilities I haven't found for linux yet if ever) 20 G for Dapper.  The second is two 20G partitions, and the third has Xubuntu.

Best luck I've had is with Gparted Live from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).
I was hosed by Feisty Fawn Herd 2 partitioning as might be expected from early software...

When I want to add a linux, I use Gparted to set up a partition for it, leaving the rest of the unallocated space as is.  Then on Install of the linux I do manual partition and try to make sure it is going to use the partition I had set up.

Fun.  Cheers, Jerry

---

### Post by vigleik on 2007-02-14
How about, say, one extended partition with 3 logical partitions of about 10-15GB each, to hold each of the / partitions and home, then one swap partition to be shared between them and a data partition also to be shared between them.

Sharing /home partitions is a bad idea, but putting home on the root partition for each install and then keeping all your data on a different partition should work nicely. If you think you might want to install a fourth distro to play with you should plan ahead for that and make the extended root partition into 4 logical partitions.

---

### Post by albesan on 2007-02-15
hello, thanks for the replies,

@jerrylamos- Yes I have gparted live cd, and I set the partition scheme as I think is best, but like you say: "try to make sure it is going to use the partition I had set up." I always go yellow there,
Last time I tried I ended up with a 25gb of swap which was suppossed to be for another distro/version.

Anyway I guess there is nothing else for it. Thanks for the help.

a.

---

### Post by albesan on 2007-02-15
hello again, I've installed Edgy but now lost Dapper in my grub menu,
I've been looking at how to the edit the grub menu but I'm not sure of where my dapper was.
It was a 1 partition for root (sda1), 1 for swap (sda3), 

I can't remember the kernel versions I had on Dapper and I m not sure how to add the dapper entries to the grub menu.

I can boot into Edgy but the disk manager is not there anymore (at least I can't find it) and I can't mount the other partitions to check on the information I'm missing.

my grub/menu.lst looks like this:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.19.1-rt15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.19.1-rt15-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.19.1-rt15-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.19.1-rt15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.19.1-rt15-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.19.1-rt15-generic
boot

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


how do you guys/girls go about sorting this sort of thing? ? Thanks for any help, 


a

---

### Post by confused57 on 2007-02-15
You can use the live cd to (re)install grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

What I do is use one Linux distro's grub on the mbr & additional distros I install their grub to their root partition & just add an entry to the grub on the mbr to boot the other distro, using chainloading.  Chainloading would have an entry like this:

title    Edgy
rootnoverify (hd0,4)
chainloader +1

When you follow the above link, the command:
```
find /boot/grub/stage1
```
you'll get something like:
```
root (hd0,0)
root (hd0,3)
root (hd0,4)
```

If you want the Linux on (hd0,0) as your grub on the mbr, you'd enter:
```
root (hd0,0)
setup (hd0)
```

If you want to install the Linux grub on (hd0,3) to it's root partition:
```
root (hd0,3)
setup (hd0,3)
```

then enter quit to exit.

When you boot up you'll boot to the Linux on (hd0,0), just add a chainload entry similar to the one I listed above.  This is the method that I use, see this link:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by vigleik on 2007-02-16
Your other partitions should still be there, they might just be a little bit harder to get to. For example, if you lost sda1, the following should work. Create a new directory called sda1 (or whatever) in /mnt/, then do "sudo mount /dev/sda1 /mnt/sda1". Then you can check the other grub for the missing entries. Of course, a more permanent fix is advisable to be able to accesss any partition at any time. For that, you might have to edit your /etc/fstab. Looking at your other fstab should give you a hint as to how to do that.

---

### Post by albesan on 2007-02-16
Great stuff team, thanks a lot for all that.

I managed to find out the info in the dapper partition by booting from a Live cd and looking in it with "Disks", (why is the Disks application gone in Edgy??)

Anyway, I then updated /boot/grub/menu.lst accordingly , and now I can wich one I want.


After that using gparted I copied the whole patition with Edgy on and duplicated it. 
I the went on to upgrade this second copy to Feisty. The normal live installer wouldn't let me specify the partitions/mountpoints.
I did upgrade but I can't boot the 2.6.20-x kernel... I added it to the menu.lst but feisty seems to have different way to addressing directories???
 ( root=UUID=*really long string* ) 

I really don't know. I changed that to a path but with the same result, file not found.

With all this messing about with the grub menu I think there is one per system, I don't know much but would this be healthy??


any coments appreciated, thanks


a.

---

