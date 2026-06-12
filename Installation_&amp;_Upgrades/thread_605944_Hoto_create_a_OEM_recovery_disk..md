---
title: "Hoto create a OEM recovery disk."
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by eldaria on 2007-11-07
Hello, 

I'm setting up a Kubuntu system on a new laptop for a friend.
I'm installing it as a OEM so that she can configure it her self later.

The default setup configures 2 partitions, 
Partition 1. mounted as root, is 227.1GB
Partition 5, mounted as Swap, is 5.8GB

After Installing a basic system 2.2GB is used, so with some extra applications perhaps 3.5GB will be used.

A DVD can fit roughly 4.7GB uncompressed, so a system recovery should fit on 1 DVD.

I figured the easiest is to create 3 partitions, 1 system, 1 home and 1 Swap.

What would be good percentage for distributing the space?

Also, is a system partition of 5 GB too small?
If I compress the image, it really does not matter if I make it 5 or 10GB since all the empty space would be compressed to nothing.

And finally, what is a good way of making a recovery DVD for linux?
Basically user inserts DVD, reboots, and confirms recovery.
Next system will automatically restore system to original state. but keeps the users home directory.

What are your thoughts?

Regards.
Brian.

---

### Post by dabl on 2007-11-07
You are right to go to three partitions, versus the default of two.  A comfortable size for the root filesystem is 6GB.   I have been watching my Gutsy system for a month, and today it is using 56% of a 6GB partition.  You could probably get by with 5GB, but I observed Feisty grow to 4.5GB when I was not conscientious about doing sudo apt-get autoclean and autoremove ...

If it is to be allowed to "hibernate", then you want the swap partition to be at least 1.25X memory size.  If no hibernate, then 0.5GB is probably plenty of space for swap.

The third partition for "/home" can be as much of the rest of the disk as you wish.

I don't know about a "recovery" DVD.  I guess you are thinking of some calamity that cannot be fixed in the recovery mode that Ubuntu installs?  The best thing I have heard about is "apt on CD" -- a utility to preserve your specific combination of installed packages, for restoration after a system upgrade or re-installation of the OS.  It is here:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

HTH  :)

---

### Post by Pevichaey5 on 2007-11-07
hi

great question, i jus installin an oem on me old laptop for me brother for christmas lol 

would really handy to find this out

cheers

[edit]
i'm think just doing a image of the hard drive and setting it as a bootable image and hoping i can use it as a recovery dvd[/edit]

---

### Post by eldaria on 2007-11-08
Ok, I went for a 10GB Partition for the system and 6GB for Swap.
The rest is home drive.

For recovery I could not really find any good way of doing it, so I went for a simple solution.

On this page I found how to dump a partition image to a file.
[http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)

I put the imgae file as a hidden file on the Home drive.

Interestingly enough there were 3.3GB used of 10GB total partition, but the compressed image still became 6.4GB, I guess an empty file system is not really empty?

Anyway, then if her system now becomes messed up, she can just reverse the process, (Or I will do it over the phone.) :-)

---

### Post by vidak on 2007-11-08
I left 7GB for root partition:
/dev/sda2             6,9G  6,0G  624M  91% /
10GB would be better, it seems... There are lots of (probably unnecessary) stuff, however. 
You should decide - do you want to compile stuff (those dev-things eat a lot of space :( )

---

### Post by dabl on 2007-11-08
> **eldaria said:**
> 

Ok, I went for a 10GB Partition for the system and 6GB for Swap.
The rest is home drive.



You wasted about 5.5GB on that swap partition ... but it doesn't hurt anything.

I've never done the dd thing, but it appears to be a good method to do what you wanted.

A filesystem by itself uses some overhead (disk space), so you never have a truly "0.0 MB" partition, even after you delete everything in it.  :)

---

### Post by psusi on 2007-11-08
You should just create a custom oem install script and burn your own oem install cd.  I think there is information on how to do this on the wiki, but I have never tried.

---

