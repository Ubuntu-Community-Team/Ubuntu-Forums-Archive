---
title: "Windows 7 Partition"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by louintoronto on 2012-08-30
I've been using Ubuntu for a few months now and loving it, but there a few things I miss from my old Windows days: iTunes, Potoshop, printer software, etc. I decided I was going to re-install Windows 7 from a purchased disk alongside Ubuntu, but I haven't been able to.
I think that what I need to do is create a partition on my hard drive in the ntfs format of a suitable size and install Windows onto there.

Is that correct? If so, how do I go about doing this?

Thank you all for your help.

---

### Post by oldfred on 2012-08-31
Welcome to the forums.

Windows requires a primary NTFS partition with the boot flag (or active flag in Windows). I believe gparted creates a XP type NTFS partition. Most say that works but others have said they had to reformat again before installing. 

There are at least two different NTFS partition boot sectors - PBR. One says to boot with ntldr for XP and the other is bootmgr to boot Vista or 7. But normally an install of 7 converts the PBR to the bootmgr as part of the install.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by louintoronto on 2012-08-31
Thanks for the quick response!

I have been having some difficulty using GParted. Specifically, the space currently mounted for Ubuntu and the other for cryptswap together take up the entire hard drive. Even though only 1/10 of the space on the Ubuntu partition is in use, when I right-click it or go to the partition heading at the top of the page I do not get the option to split it.

Why? How do I go about doing that?

---

### Post by Gordonbp531 on 2012-08-31
> **louintoronto said:**
>  when I right-click it or go to the partition heading at the top of the page I do not get the option to split it.



That's not how you do it. You have to RESIZE the Ubuntu partition first, and then create a new partition on the free space.
And to answer your original post - Itunes sucks! It's so full of DRM and there are so many posts on the internet about not being able to reconnect, and the library going missing etc etc that I gave up on it years ago. Plain MP3 downloads do me fine - I can use them in whatever location **I** desire, not where Itunes tells me.
As for Photoshop, tried The Gimp? It's used by many professionals as an alternative to Photoshop....

---

### Post by oldfred on 2012-08-31
Any of these should help on gparted:

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

