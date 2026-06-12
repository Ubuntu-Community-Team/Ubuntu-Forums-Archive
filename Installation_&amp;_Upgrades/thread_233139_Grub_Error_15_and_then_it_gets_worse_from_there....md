---
title: "Grub Error 15 and then it gets worse from there..."
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by burke2134 on 2006-08-09
I think I've completely hosed this file system but hoping someone out there might be able to help me save it...

Have an installation of 6.06 dual-booted with WinXP on a Dell Latitude D800.  Was working fine until it encountered some sort of error on the hard drive and requested an fsck (which I did).  I must've done something wrong because at the end of the fsck procedure I had to click through thousands of files to accept permission changes.  After a reboot I got the dreaded Grub Error 15.

I followed the helpful instructions I found here:

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+loading+error+15]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+loading+error+15")

But didn't have any luck. :(  I have a re-installation started but am desperately hoping that I won't have to reformat the existing partions to proceed or fix the underlying Grub Error issue.

So right now I'm stuck at the 'Manual Partitioning' screen of the ubuntu-6.06-alternate-i386 setup.  The error message I receive when I attempt to 'Finish partitioning and write changes to disk' is:

*"The attempt to mount a file system with type ext3 in IDE1 master, partition #1 (hda1) at / failed.  You may resume partitioning from the partitioning menu."*

I'm using the following options for the partitions:

/hda1
  Use as:                Ext3 journaling file system
  Format the partition:  no, keep existing data
  Mount point:           / 
  Mount options:         defaults
  Bootable flag:         on

/hda5
  Use as:                swap area
  Bootable flag:         off

/hda3 is an ntfs partition used by Windows XP.


Any advice, suggestions, etc. *very* welcome... :)

---

### Post by A2A on 2006-08-09
Hi there,

Try with the    Bootable flag:         [B]off

[/B]Let us know what happens.

A2A

---

### Post by burke2134 on 2006-08-09
Hi,

thanks for the help. :)

same error (i.e. "The attempt to mount a file system... at / failed.") with the bootable flag "off".  :(

---

### Post by A2A on 2006-08-09
Here is what I think, since it has an install on it from before, you would need root access to do anything to it.  i.e sudo access.  (Just a thought)

Thing is, I don't know if that is possible.

Herman and confused57 are the folks that can help you out with this, hopefully they come online sooner rather that later.

P.S:  D/load a copy of Super Grub Disk: [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php) 
Have it handy, I reakon Herman might ask you to use that to rescue the system.  I recommend you burn it to a CD-RW or a CDR.

The Error 15 is when grub is not found.  You can rewrite grub back to the mbr without having to do a complete re-install.  The alternate install CD has this option.
This thread might help: [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=rewriting+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=rewriting+grub)

Let us know what happens,

A2A

---

### Post by confused57 on 2006-08-09
Herman is probably the most knowledgable grub expert in the forum, but until he sees your thread, you might try using the Desktop Live CD to reinstall grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Dualbooting with Linux on a partition located in front of Windows can be tricky, I haven't seen too many people able to do so:
[http://www.ubuntuforums.org/showthread.php?t=225583&page=2](http://www.ubuntuforums.org/showthread.php?t=225583&page=2)

Super Grub Disk is a good idea, also.
Here's Herman's website page on grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Good luck, let us know how it goes.

---

### Post by burke2134 on 2006-08-09
Thanks (everyone) for your help... :)

Here is what I get when I boot with the LiveCD and run grub:

```
grub> find /boot/grub/stage1

Error 15: File not found

grub>

```

When I try to use the LiveCD to reinstall Grub (manual partitioning then jumping ahead to the Grub installation) I run up against the same '...unable to mount...' error. (screenshots attached).  Selecting 'Continue' ends the installation program.  Selecting 'Go Back' takes me back to the 'Manual partitioning' screen.  :(

I need to take the dog for a walk but will check out Herman's Super Grub disk site when I return.  Thanks again for your help. :)

-burke

---

### Post by A2A on 2006-08-09
Hi burke2134, I was having the same issues a couple days ago on my laptop.    Herman and confused57 were very helpful.  There is links and particular instructions that Herman gave me then.  Check it out: [http://ubuntuforums.org/showthread.php?t=229909](http://ubuntuforums.org/showthread.php?t=229909)  Hope it's helpful :-)  Regards, A2A

---

### Post by confused57 on 2006-08-10
> **burke2134 said:**
> Thanks (everyone) for your help... :)

Here is what I get when I boot with the LiveCD and run grub:

```
grub> find /boot/grub/stage1

Error 15: File not found

grub>

```




-burke
May have accidentally found something that may work:
[http://www.ubuntuforums.org/showthread.php?t=224351&page=3](http://www.ubuntuforums.org/showthread.php?t=224351&page=3)
See the last reply on this page.

---

### Post by Herman on 2006-08-10
> Was working fine until it encountered some sort of error on the hard drive and requested an fsck (which I did). I must've done something wrong because at the end of the fsck procedure I had to click through thousands of files to accept permission changes. After a reboot I got the dreaded Grub Error 15.burke2134, This is not a bootloader problem. It seems to me that your filesystem is damaged. I don't know how to repair it. 
If you have you data backed up or didn't have anything important, if I were you I would just format the partition and re-install. 
If you did have something important that isn't backed up, then we can try searching for possible ways to fix the filesystem or recover the data, but I think it will require some effort. 

You could test your hard disk with a live CD to make sure it isn't on the way out with the following code,```
 sudo badblocks /dev/hda
``` If you get no results after waiting a long time,  your hard disk is probably healthy. If it finds any bad sectors, it will give you a list of them. 

Here's a link about filesystems, [http://www.tldp.org/HOWTO/Filesystems-HOWTO.html](http://www.tldp.org/HOWTO/Filesystems-HOWTO.html)

Inside that link you'll find this one, [1.10 Introduction to extent filesystems]("http://www.tldp.org/HOWTO/Filesystems-HOWTO-1.html#ss1.10")

Inside that one, you'll find this one, [6.17 Repairing/analyzing/creating Ext2 using E2fsprogs]("http://www.tldp.org/HOWTO/Filesystems-HOWTO-6.html#ss6.17")

And we could look up the man pages for the following, e2fsck, mke2fs, debugfs, dumpe2fs, tune2fs, if we are keen to learn more. Maybe the answer is somewhere in all that reading. Or maybe someone with the required knowledge will happen along and enlighten us with a method for the repair of ext3 filesystems.
Re-installing only takes around half an hour though. We wouldn't learn anything, and it depends on what data you had.

Regards, Herman :D

---

