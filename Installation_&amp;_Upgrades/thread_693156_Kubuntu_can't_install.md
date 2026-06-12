---
title: "Kubuntu can't install"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by breaking on 2008-02-10
I've downloaded the image twice now but when I boot from disc to install, the screen shows its loading the Linux kernel but then goes blank. The CD drive keeps making noises like its loading something but after being left alone for a while it stops and nothing happens. 

I'm using the amd64 desktop image (i have 64bit hardware).

---

### Post by Rocket2DMn on 2008-02-10
Sounds like the LiveCD might just be incompatible with your video card, it's a fairly common problem.  If you're just looking to install, you can use the alternate cd which is a text based installer without a live session, it works very well.  You can get it from Kubuntu's mirrors by selecting the "Alternate install CD" rather than the "Desktop CD".

---

### Post by breaking on 2008-02-10
Thanks for the reply. How do you install with the text based installer? I hear that its very hard to install that way.

I.e. what commands do i need to know?

note: I have an nvidia 8800gtx

---

### Post by Rocket2DMn on 2008-02-10
Although I've never used the text based installer, from what I understand, it's very intuitive - nobody has ever complained about it.  The most difficult portion will be setting up the partitions - are you setting up a dual boot?  If so, I suggest backing up everything important first, because if you're going to resize your existing NTFS windows partition to make room for Kubuntu, it is possible for something to go wrong (though not likely).  If you are dual booting, make sure you defragment your windows drive first.
If you need help with partitioning, post some details like drive size, free space, the amount you want to give to Kubuntu, etc and I'll help you out.

---

### Post by breaking on 2008-02-10
Truth be told I'm happy to wipe my HD (320gb in size) and just make a 100gb OS partition, the necessary swap partition and the remainder - a partition for my files.

---

### Post by Rocket2DMn on 2008-02-10
So no more windows on it?  Then you probably want something like
root (/): 20GB
swap: 2x your RAM capacity
home to keep your settings and data (/home): the rest of the space

These are arbitrary values (except for swap), but your data partition should be way larger than your root partition - the OS + programs is not extremely large (20GB is overkill, but gives you more than enough room to breathe).
Perhaps you want a separate data partition rather than keeping them in your home directory?  Then give as much space as you want to that, make /home a decent size (10 GB?) and give the rest to a data partition.  Again, these are arbitrary, you need to decide for yourself.

---

### Post by breaking on 2008-02-11
I thought the home partition is the data partition. What's the difference?

I.e: - drive C: /root (around 50Gb)
       - drive S: swap partition (around 4Gb)
       - drive F: /home (remaining data)

---

### Post by Rocket2DMn on 2008-02-11
/home has all your configurations, so if you "ls -a" in it you will see a bunch of hidden files and folders starting with a period.  (Ctrl+h to see it in Nautilus).  The that is the partitions on which the /home directory actually lives.  It has folders with usernames in it.
Don't delete any partitions that you have data on.  You may also want to get your hands on an external hard drive to back everything up on.

---

### Post by Partyboi2 on 2008-02-11
Once you have installed ubuntu you will probably need to get the drivers for your 8800gtx graphics card from the nvidia website for you to get the graphics working, see [URL="http://ubuntuforums.org/showthread.php?t=693242"]here
[/URL]

---

### Post by breaking on 2008-02-15
ok, so i successfully installed using the text installer (not that hard really). Then it asks me to take out the cd and reboot - so i did. Then it reboots into a permanent black screen. No error messages, nothing. 

The only possible explanation is that the kernel kubuntu is using isn't compatible with my hardware. My guess is that the Linux kernel can't yet handle ddr3 ram that i use in my system.

I hope there's another explanation because otherwise i'm probably going to have to use Mandriva (my second choice of Linux distro) or maybe Sabayon.

EDIT: I did successfully install opensuse (but i don't particularly like that distro)

---

### Post by Rocket2DMn on 2008-02-15
There is another explanation - it doesn't like your video card (yet).  If it goes through it's loading sequence, then the screen just turns black, your video stuff was not correctly detected.  You can follow this guide to reconfigure X manually(the GUI) - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

