---
title: "a unified way of booting os's"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by sefs on 2010-12-07
Hi there I want to set up a system with two windows oses.
a) Windows 7
b) Windows XP

Windows 7 will be installed to one partition, and xp will be restored to a second partion from a ghosted image.

I don't want the headache of having to guess who or what is fighting to control the boot sector.  When the fight is over I simply want to walk up stick in a cd run a utility and install a booter/loader over what ever is there.  I want to be able to do it adhocly so it must be able to on install always scan for any already installed OSes and set them up in a nice selection menu at boot.

GRUB 2.0 came to mind.

What I want to know is if that sort of thing is possible.  Can I install/restore multiple OSes to a disk, and then when all is done pop in a live CD and install/repair GRUB 2 to the system? Even if UBUNTU or any linux is not on the system and have it perform the above scenario as described?

Thanks.

---

### Post by oldfred on 2010-12-07
If you want to directly boot from grub2 you will have to be sure to separate the windows installs. Normally windows moves the boot files from the second install into the first and then with boot.ini (XP) or BCD (Vista or win7) let you choose what to boot. Once boot files are moved grub cannot boot the second install.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)


If you just install a grub2 partition you will have to manually add boot stanzas for each install. Not difficult, just create a writable grub.cfg (normally it is not writable) and just put in your boot stanzas.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition")
old grub partition
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition")
Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_")

---

### Post by sefs on 2010-12-07
So let me get this straight, 

I can 
1) set up a small partition
2) install grub2 to that 
3) manually setup the cfg file to point to any other os thats resident 

and thats it?

I found a good explanation of something close to what I want to do here...
[http://ubuntuforums.org/showthread.php?p=10212677](http://ubuntuforums.org/showthread.php?p=10212677)

---

### Post by oldfred on 2010-12-07
Herman is the one I linked to in my previous post.

And that is how I am booting my 4GB flash drive to loop mount ISOs.

---

### Post by sefs on 2010-12-08
> **oldfred said:**
> Herman is the one I linked to in my previous post.

And that is how I am booting my 4GB flash drive to loop mount ISOs.

Thanks for the help! It is exactly what I needed I believe :)

---

