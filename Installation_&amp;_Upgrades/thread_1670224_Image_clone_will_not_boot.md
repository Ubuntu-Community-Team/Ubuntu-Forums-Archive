---
title: "Image clone will not boot"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by homestar on 2011-01-18
My HDD crashed (it wasn't completely disastrous, though). I was able to get my Ubuntu 10.10 partition of the disk with dd_rescue. I can see all of the data in the partition and everything. dd_rescue reported that there were no errors.
 
Now, I have a fresh HDD, and I copied the image that I created with Gparted, and turned the boot flag on. I turn my system on, and all I get is a flashing cursor in the corner of the screen.
 
Any suggestions--I get the feeling that this would be easy for a seasoned user, but I'm not sure where to go.
 
I originally got some information about cloning partitions here: [http://www.ghacks.net/2010/08/01/clone-your-linux-disk-with-ddrescue/](http://www.ghacks.net/2010/08/01/clone-your-linux-disk-with-ddrescue/)
 
But, it doesn't tell you how to reload the image after you make it.
 
Help!
 
homestar

---

### Post by secondsystem on 2011-01-18
I just did this, see here.  Just Run fdisk -l to verify your partition names.

[http://ubuntuforums.org/showthread.php?t=1669397](http://ubuntuforums.org/showthread.php?t=1669397)

---

### Post by homestar on 2011-01-20
I had a feeling it had to do with the boot loader.  I don't know grub that well--I'm used to just installing Ubuntu, which configs grub on its own.
 
What about the swap partition though?  I had a 1 GB partition for the swap.  Do I just make a 1GB partition?  How will the OS know where to look for it?

---

