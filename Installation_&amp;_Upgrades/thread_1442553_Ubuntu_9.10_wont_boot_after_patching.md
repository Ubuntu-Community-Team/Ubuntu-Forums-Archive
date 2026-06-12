---
title: "Ubuntu 9.10 wont boot after patching"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by Huckola on 2010-03-30
Hi all

First time post and a n00b with linux, so might need some hand-holding.

Ubuntu 9.10 running as a guest on VMware esxi v4.0

I used the gui update manger and applied a whole lot of updates about 1 hour ago. During the update process it prompted me to use the "maintainer" version or "current", for what I have no idea, I wasn't paying much attention, and I guess thats where all the trouble began ;)

There were no other prompts, just the one above.

Anyway I said use the "maintainers" version. The Update then completed and I rebooted. Only to have the screen sitting blank and black.

I hit alt-f1 and the following appears:

<start>

Gave up waiting for root device.   Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/blah blah blah does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in command.

(initramfs) _

<end>

Obviously its packed a sad with the disk/partition

I have no idea of where to start on this.

Thanks in advance!

---

### Post by Huckola on 2010-03-30
I've been doing some reading, and I dont seem to have a /mnt or fstab file/directory. So I guess I the o/s doesnt know the mount point?

Now I'm wondering that my choice to use "maintainers" version might have been something to do with one of the systyem config boot files huh....

---

### Post by Huckola on 2010-03-30
Ok yay me.

I typed:

Mount /dev/disk/by-uuid/<big long hex number> /

And now I have the my file system back.

This is like learning DOS for the first time, but trickier !!!

Still yet to get the o/s loaded, but time for some zzzzzzzzzzzzz's.

---

### Post by Huckola on 2010-03-31
Sorted !!!

After much shagging around with LiveCD, grub, busybox and toooo many reboots, the solution was a lot easier than I imagined.

The problem was as "busybox" cleary indicated:

"ALERT! /dev/disk/by-uuid/blah blah blah does not exist. Dropping to a  shell!"

Yes, the UUID was invalid !!! How it got changed I have no idea, perhaps was all my fault when I chose "maintainers" version, but how it chose some other device's UUID (and what is actually was) I have no idea.

By doing a ls /dev/disk/by-uuid/   it showed me what the UUID of my disk SHOULD be.

Whereas the system was trying boot from a totally different UUID

Solution: [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

So I followed the above, and it booted, I made permanent changes to /boot/grub/menu.lst (after shagging around with file permissions) for the first entry and put in the CORRECT UUID. Saved the file

What a trip !!! 8-)

---

### Post by Huckola on 2010-03-31
Ok, my fault !!!

Funny how once you've resolved a stuff up, you now know exactly what "key-words" to search upon.

This thread covered exaclty what I encountered, except the author did what I SHOULD of done ;)

[http://ubuntuforums.org/showthread.php?t=1350031](http://ubuntuforums.org/showthread.php?t=1350031)

I'm gonna have a pretty good guess at where the old UUID came from too. Originally my Ubuntu installation was on a stand-alone machine. Months back I used VMware's P2V utility and copied the physical machine over to my esxi server, say no more!!!

Cheers.

---

