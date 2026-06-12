---
title: "feisty install: partition problems"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by nalle on 2007-04-27
I did a clean install of Feisty and added a new hard drive on a computer and ran into some problems:

The names of the hard drives (sda, sdb) keep on switching around thus causing problems with booting up (gives fsck errors, mounts 1 hd twice), but still booting, I've changed the information to fit grub in fstab and reconfigured it a couple of times, but that doesn't fix the problem. 
The bios doesn't seem to recognise the other hd (which I put recently) in the IDE list, but it does give it as an option for first/second hardrive, so could it be a problem with BIOS? I already fixed a problem with the computer booting to a screen with a single smiley which was apparently the computer trying to boot from the wrong hd. 

Also, when I mount the other hd, it works for a moment and then starts giving errors saying that it is write-protected. I've chmoded, chown, etc. and the problem persists. I'm thinking of reformatting it, in case that would help..but I have a feeling it won't.

Motherboard: P5GD1-VM
HD causing problems: Maxtor 80gb (serial ATA)

I'm not e newbie, but this problem has me stumped so if anyone can help, please do :confused:

---

### Post by zvacet on 2007-04-28
[http://ubuntuforums.org/showthread.php?t=275728&highlight=two+drives]("http://ubuntuforums.org/showthread.php?t=275728&highlight=two+drives")

---

### Post by nalle on 2007-04-29
Thank you for the link, but it missed the point a bit: I am not dual booting and the problem is something that comes before grub with which the thread deals with. 
The F8 at the beginning would help if the system didn't start up at all, but it does.The hds are just given their place in different order before grub starts linux, but it doesn't affect the fact that the system is booted from the same drive every time.
The problem hasn't recurred now more then a few times, so it is not that big a deal.

But the second problem is:
I've tried to get the second hd to not become write protected by chowning the ownership to myself. This fixes the problem for me, but even though I have chmoded read/write group privlidges to other users, they still have the problem: first it works, then suddenly the hd starts giving errors that it is write protected. Remounting with rw gives the same error : "this drive is write protected" or something like that.

---

### Post by nalle on 2007-04-29
I was too fast to say: I just tried to get into the second hd and the folders, which are owned by my user. Here is the text when trying to change permissions and when trying to remount:

[INDENT]
Couldn't change the permissions of "kirjallisuus" because it is on a read-only disk

mount: block device /dev/sdb1 is write-protected, mounting read-only
[/INDENT]


And it worked just a few minutes ago.

---

