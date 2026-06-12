---
title: "Probs resizing ntfs partion"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by Jager on 2006-03-24
I just downloaded the ubuntu installcd and tried to install it on my laptop.
But when i get to the point of resizing a partion it fails.
I chose my second partion and try to resize it from 96.1 GB to 90 GB but nothing happens.
It doesnt change it.
Any help would be appriciated since im a couple of hours old with this linux thing.

---

### Post by Jagot on 2006-03-24
Have you taken a look at Herman's guide?  If not then check it out:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

If you have written the changes to disk and nothing is still happeneing then you may want to defrag your hard disk a couple of times.  Sometimes the installer doesn't work when fragmented files exist in the partition, though I've never had a problem.

---

### Post by Jager on 2006-03-24
Ive tried that one but it didnt work.
The resizing it self doesnt work.
I ask it to change it but it just puts me back at the manual partion thing.

---

### Post by Jagot on 2006-03-24
Well, providing you are actually writing the changes to disk after you have selected the size to which you want the partition to be, I'm not sure what could be wrong there.  You may want to try and use something else to resize the partition, for example QTParted on a Knoppix Live CD.

---

### Post by aysiu on 2006-03-24
If you're going to have a live CD, you may want to look at PCLinuxOS. [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) has never failed me for resizing and partitioning.

It's always a good idea to have a live CD around, though, for recovery purposes or... whatever.

---

### Post by kaolin on 2006-03-24
I have encountered a similar problem and like to share my 2 cents. When trying to resize a partition nothing happened. But the following procedure worked (saw it from google) I defragged the disk, then used chkdisk /f c: to force windows to check the disk, then defragged again. Then I was able to resize the partition. I am new to linux, so I have no idea why this worked.

---

### Post by Jager on 2006-03-26
[QUOTE=kaolin]I have encountered a similar problem and like to share my 2 cents. When trying to resize a partition nothing happened. But the following procedure worked (saw it from google) I defragged the disk, then used chkdisk /f c: to force windows to check the disk, then defragged again. Then I was able to resize the partition. I am new to linux, so I have no idea why this worked.[/QUOTE]

Well i can verify that this works.
Though you might have to defrag alot.
in my lil screwed head the files where too scattered to cut off a chunk and the defraging made all compact..
Anyways if anyone else has this prob this works.

---

### Post by Herman on 2006-03-26
Most Windows users don't actually know how run scandisk and defrag properly by turning off the background processes first, so the utilities can run uninterrupted. (It's best to run scandisk first too, then defrag). 
[COLOR=Blue][This link]("http://www.geekgirls.com/windows_defrag.htm")[/COLOR] has good instructions and illustrations on how to do that right.  I meant to include that link in the dual boot site but obviously I have forgotten it. Sorry, I'll try to remember it next time I do an update, (soon). :D (Herman)

---

### Post by amar on 2006-04-07
I have a similar problem, when I attempt to shrink my ntfs partition. I have ran defrag and scandisk many times without any success. I have noticed some "unmovable files" near the end of the partition, though i thought that this shouldn&#8217;t be a problem. Any ideas?
Thanks

---

### Post by aysiu on 2006-04-07
[QUOTE=amar]I have a similar problem, when I attempt to shrink my ntfs partition. I have ran defrag and scandisk many times without any success. I have noticed some "unmovable files" near the end of the partition, though i thought that this shouldn’t be a problem. Any ideas?[/QUOTE] Sure. [Use DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

---

### Post by amar on 2006-04-07
Sorry but I didn&#8217;t fancy spending 5 hour downloading another full distro, instead I downloaded the latest version of GParted 0.2.4 as a live cd (took 5 mins) and this worked fine. Don&#8217;t know what the exact problem with the ubuntu versions
Thanks anyway

---

### Post by plors on 2006-04-08
[QUOTE=amar]Sorry but I didn’t fancy spending 5 hour downloading another full distro, instead I downloaded the latest version of GParted 0.2.4 as a live cd (took 5 mins) and this worked fine. Don’t know what the exact problem with the ubuntu versions
Thanks anyway[/QUOTE]
The ubuntuversions of gparted are too old, this has caused a lot of frustration for the gparted (and other apps) developers. Fixing a bug and releasing a new version doesn't help, because most users stick to the old version and keep banging in the same bugs over and over again.

anyway, i'm glad it worked for you :)

---

