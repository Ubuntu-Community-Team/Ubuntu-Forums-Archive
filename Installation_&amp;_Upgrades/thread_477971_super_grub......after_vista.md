---
title: "super grub......after vista"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Irti on 2007-06-18
i have a dual boot system .......xp+ubuntu.....and i wanted to upgrade xp to vista...i read somewhere on this forum that upgrading to vista will wipe off my grub......so i will have to work around with super grub..to get my linux running....could someone please explain more about it to me.....also i was wondering if i could install super grub through an external hard drive as its size is pretty small (something around 500 kb) and i dont wanna waste a cd for that.......

---

### Post by OzzyFrank on 2007-06-18
First off, believe me, you do want to "waste" a CD for that, as to boot from that is the most easiest option. And if you ever need it again, there it is. Now, reinstalling GRUB is fairly easy, and I really suggest not making your way through the Super GRUB Disk menu and choosing automatic, as with me it didn't do anything (but then my setup is different, in that I put GRUB on the partition not the mbr... though perhaps that shouldn't matter!). 

Here is an excerpt from my Ubuntu ebook concerning this. Remember to replace the drive path with your own; if sharing one drive with Windows, it will be (hd0) for the whole drive or (hd0,0) for the first partition or (hd0,1) for the second partition (if Windows was there first):

Restoring GRUB

You will either need a Super GRUB Disk or your Ubuntu disc, and as long as your drive references are fine everywhere, it will only take a couple of commands to fix things. You will need to decide if GRUB is going in the MBR (master boot record of the drive) or on the partition. If Ubuntu is sharing a drive with Windows, choosing MBR will get back the GRUB menu and let you boot either. If Ubuntu is installed on another drive, and you use a boot manager to boot your partitions, then choosing to install GRUB on the partition may be better. If one doesn't work, then try the other. Simply enter the first command followed by the other. To get to the command prompt on the Super GRUB Disk, type C; to get to the grub> prompt on your Ubuntu CD, go to command line and enter the following before entering the GRUB restore commands:
grub


Restore GRUB to the Master Boot Record (eg: 1st partition on 2nd drive)

root (hd1,0)
setup (hd1)


Restore GRUB to a Partition (eg: 1st partition on 2nd drive)

root (hd1,0)
setup (hd1,0)


Note sure? Find the Partition where GRUB is

At the grub> prompt enter:
find /boot/grub/stage1

---

### Post by Irti on 2007-06-19
you mentioned that i can restore grub using my ubuntu cd too........??so that would mean that i just have to pop in my ubuntu cd and let it do the work?????

---

### Post by Pumalite on 2007-06-19
> **Irti said:**
> you mentioned that i can restore grub using my ubuntu cd too........??so that would mean that i just have to pop in my ubuntu cd and let it do the work?????

See this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by OzzyFrank on 2007-06-19
Hi. No, I don't think I said you can just pop in the CD and it does it all for you, hehehe! If you read my post, you'll see I mention using the live cd to get to a grub prompt ("sudo grub" at the ubuntu command prompt) then using those commands (with your correct drive address) to restore grub manually. It's really easy, and takes a few seconds. You obviously need to know where to tell grub to put itself, but other than that it is as simple as doing those "root" and "setup" commands.

---

