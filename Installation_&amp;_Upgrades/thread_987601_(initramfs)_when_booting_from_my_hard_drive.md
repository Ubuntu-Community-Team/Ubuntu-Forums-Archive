---
title: "(initramfs) when booting from my hard drive"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by glenngds2007 on 2008-11-19
will try to upload a snapshot of my screen to help someone figure out what is going on with my system.  Was booting just fine from hard drive to Ubuntu 8.10 now this garbage.

---

### Post by mren on 2008-11-19
> **glenngds2007 said:**
> will try to upload a snapshot of my screen to help someone figure out what is going on with my system.  Was booting just fine from hard drive to Ubuntu 8.10 now this garbage.
Yes, my machine sometime does that too, I just type exit <enter>, then boot will continues as usual.

Hope that helps.

---

### Post by glenngds2007 on 2008-11-19
Here are two screen shots. as you can see (initramfs) is followed by lots of garbage and the longer I let my system run the longer the garbage gets

---

### Post by glenngds2007 on 2008-11-19
I also get the same thing when attempting to boot off of a Ubuntu 8.10 CD.

---

### Post by glenngds2007 on 2008-11-19
just to let you know the computer was set up to dual boot between windows and Ubuntu and then suddenly this messed up situation.  My computer works just fine when booting windows:(:mad::confused:

---

### Post by glenngds2007 on 2008-11-19
Believe it or not the reason the computer would not boot the Ubuntu 8.10 CD is something about my brand spanking new Sony DVD-RW that Ubuntu does not like.  Luckily I had another DVD drive laying around.  Will try and booting my computer off the hard drive with out that drive and see what happens.

---

### Post by glenngds2007 on 2008-11-19
Guess what my computer booted up just fine now.  I do not know what the heck gives here because I booted the computer at least 5 or 6 times with that drive in place.  I will hook it back up and see what happens.

---

### Post by glenngds2007 on 2008-11-19
I just realized that I downloaded and installed a new kernel yesterday as well as some updates today as well as some updates the day before yesterday.  I do not know which one of those updates is broken but it is badly broken and needs immediate repair. Will file a bug report.

---

### Post by joparo on 2008-11-21
I have encountered that same issue. After weeks of happy ubuntuing I downloaded and installed updates this morning and now after hitting 'restart' the boot takes three times as long and then dies on a black command screen with 'initramfs' at the top left. 
 How do I repair without wiping existing files and programs..
John

---

### Post by glenngds2007 on 2008-11-21
I found that the problem was with a Sony DVDRW/RAM drive that was in my computer.  I know that does not make sense since it booted with this drive just the day before.  Try removing hardware one item at a time until you get a boot.  In the now now I am reporting this post to launchpad so hopefully it can  be fixed.

---

### Post by glenngds2007 on 2008-11-22
I will apologize for any troubles I may have caused.  I discovered on a hardware check on my computer that the data cable was loose on my master DVD drive.  I had noticed all kinds of problems with the system such as locking up when shutting down and then not booting up to Ubuntu 8.10 as mentioned in an earlier post.  If you are having problems with Ubuntu 8.10 at all, please turn off computer, unplug from wall and then make sure all cables are plugged in all the way.

---

