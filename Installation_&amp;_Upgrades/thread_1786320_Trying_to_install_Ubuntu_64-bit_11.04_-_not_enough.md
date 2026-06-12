---
title: "Trying to install Ubuntu 64-bit 11.04 - not enough space?"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by olel on 2011-06-19
Ok, so I've been trying to install Ubuntu 11.04 64-bit on my new desktop for a couple of days now... I started off by putting Ubuntu on my USB stick because I currently have no CD-ROM in my computer... I then boot with my USB stick, proceed to the install, but then the installation tells me that I lack enough space to install Ubuntu on my machine. 

At first I just thought that Ubuntu somehow thought I wanted to install it on my USB stick, and not my HDD, so I managed to borrow an external CD-ROM, but guess what, same problem.

I have a SSD (60 GB capacity), which should be plenty of space for Ubuntu. I currently have Windows 7 64-bit on it, but there's still over 30 GB of unused space.

Can anyone tell me why this is happening? Thanks! :)

---

### Post by Dutch70 on 2011-06-19
How big is the partition you're trying to install it to? Or are you using the windows installer aka Wubi?

---

### Post by olel on 2011-06-19
There's only 1 partition. However, I just tried installing Ubuntu 10.04 to see if it worked, but it can't detect my HDD. Weird, right? Windows detected my HDD just fine when installing it.

And I'm not sure what you mean with Windows installer or Wubi :P

---

### Post by olel on 2011-06-20
Bump. I'd highly appreciate some help here :)

---

### Post by slooksterpsv on 2011-06-20
Wubi allows you to install Ubuntu (or other distro) on your system but it creates a file of <x> size on the Windows side. It won't be as fast as a native install (like giving Linux it's own partition(s)), but it will still work well.

To do Wubi, connect the USB or external CDROM and open wubi.exe on the cd in Windows.

To install Ubuntu natively side-by-side, are you telling it how much space to allocate or that? Cause you will need to resize the 60GB Partition (which windows is on), down and give Ubuntu something like 10GB of Space for it's ext4 partition (so windows would have 50GB and Ubuntu would have 10).

It should have an option like Install Side-by-side for Windows and give you a bar to drag and specify how much space you want.

---

### Post by olel on 2011-06-20
Sorry, I'm a bit nooby with this. I burned Ubuntu onto a CD, and then booted with it. Then I got an option 'Install Ubuntu on a hard drive'. After that I was prompted to choose language, I chose English and pressed 'Forward', then the installation told me I needed 4.6 GB of space to proceed - I didn't get a chance to tell where I wanted to install Ubuntu.

I'm currently trying to install with Wubi as you said, I'll let  you know what happens :)

Thanks for the help man.

---

### Post by olel on 2011-07-20
I realize this thread is a bit old, but the problem is still persistant! I gave up trying to install Ubuntu on this HDD (I have a Corsair SSD Force Series 3, 60GB). I really don't know what to do now.

Like I said, Windows detects my SSD just fine, but Ubuntu won't detect it at all. I've tried booting up Ubuntu from my CD and launching gparted, but it's completely empty, it won't detect my SSD.

I would highly appreciate some help here :)

EDIT: Is it possible that it's because my SSD is connected to the SATA 3 port? I hope not, because connecting it to a SATA 2 port would be a shame :(

---

### Post by MAFoElffen on 2011-07-21
> **olel said:**
> I realize this thread is a bit old, but the problem is still persistant! I gave up trying to install Ubuntu on this HDD (I have a Corsair SSD Force Series 3, 60GB). I really don't know what to do now.

Like I said, Windows detects my SSD just fine, but Ubuntu won't detect it at all. I've tried booting up Ubuntu from my CD and launching gparted, but it's completely empty, it won't detect my SSD.

I would highly appreciate some help here :)

EDIT: Is it possible that it's because my SSD is connected to the SATA 3 port? I hope not, because connecting it to a SATA 2 port would be a shame :(
A few of my friends "had" this drive... It kept dropping out in Linux.  They both RMA'ed them a few times, then went to other drives.  

You mean this drive right?
[http://forum.corsair.com/v3/showthread.php?t=95825](http://forum.corsair.com/v3/showthread.php?t=95825)

They told me that originally for the drives affected, there was a firmware update, but then figured out that the firmware update didn't work... There was then a time when they were no longer shipping those drives for RMA...  Now they say their working on that.

EDT-- if not look at this post:
[http://ubuntuforums.org/showpost.php?p=11068051&postcount=5](http://ubuntuforums.org/showpost.php?p=11068051&postcount=5)

Funny thing is that the post following that one, in that thread has failure on the same harware as you...

---

### Post by Quackers on 2011-07-21
I don't think SATA3 is supported in Ubuntu yet (or at least some of its controllers).

---

### Post by olel on 2011-07-21
I just plugged my SATA cable from the SATA 3 port to a SATA 2 port, now everything is fine.

---

### Post by Quackers on 2011-07-21
That would answer that then :-)
Have fun!

---

### Post by olel on 2011-07-21
Thanks for the help everyone, I appreciate it.

By the way Quackers, is support for SATA 3 in development? Kind of a shame that my SSD only reads/writes at 250MB/s now, and with SATA 3 it can literally be doubled (550/490). :)

---

### Post by Quackers on 2011-07-22
I really don't know, but I would expect that to be the case :-)

---

