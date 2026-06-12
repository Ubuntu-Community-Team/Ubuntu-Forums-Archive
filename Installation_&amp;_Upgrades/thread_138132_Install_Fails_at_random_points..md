---
title: "Install Fails at random points."
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by balrog900 on 2006-03-01
At randon points throughout the install it will just fail. Sometimes it makes it through the base install and then fails when installing the other packages, other times it won't even make it through the base install. I'm using an old cd drive but I don't see how that could be an issue as the information can only be read at the speed of the drive. I'm using an 80gb seagate, 1.7ghz pent celeron, 1gb of ram, and a ge-force 5200. The last error i got was "The debootstrap program exited with an error (return value 1)" But the error is different every time. The disk was burned at 8x on my laptop. This is quite frustrating and i've had the same problem with all other distros of linux other than fedora core 4. Help woul dbe appreciated.

---

### Post by earobinson on 2006-03-01
my guess is a bad cd burn and read errors are causing the problems. you should [order some cd's ol for free]("https://shipit.ubuntu.com/").

---

### Post by taurus on 2006-03-01
I recommand you burn it again but this time with a slower speed like 4x.  Sometimes the installer chokes on itself if you burn the CD at a higher speed...

---

### Post by earobinson on 2006-03-01
ya burning again is also a good idea lol oops forgot to say that. but you might as well order the free cd's also then you can give them out :)

---

### Post by mozkill on 2006-03-01
this is also the kind of thing that you will see if you have a bad piece of RAM.  you should download and run "memtest86" on your machine and run a ram test.  also, some bios will support increasing the ram voltage by 0.25 volts... that might help or it will make the system not boot. LOL

---

### Post by balrog900 on 2006-03-01
Ok i tried the new cd burn. I get the exact same (if not worse) problems. The ram should be good, seeing as i've been running fedora core 4 on this computer for the last few months. However there is something else i might want to mention. I wanted to switch platforms BECAUSE fedora core 4 one day after a reboot stopped working. What could have even caused that. My friend said he'd heard fedora was just unstable in some aspects, so i assumed that had been the problem now i'm not so sure.

---

### Post by balrog900 on 2006-03-01
I managed to fix the problem installing ubuntu by removing a stick of ram..oddly enough it seemed to not like the other stick being in there. They are both the same type of ram etc. Odd eh? Now i've installed it i've put the ram back in and i'll see how that goes, if i don't post back then it worked...if i do then it failed miserably and i'm stuck at 512mb

---

### Post by taurus on 2006-03-01
Some mobos would take one but some would take two, dual, at a time so better which with your mobo's manual...

---

### Post by Bartender on 2006-03-02
balrog -
The previous suggestion to get memtest sounds very appropriate in your situation.  It's not hard.  I'm no expert and was able to do it.  It's a small download which you execute to create a bootable floppy.  When you're done making the floppy you go into BIOS, tell the PC to boot from A drive, then insert the memtest floppy and restart.  (This is within Windows - Ubuntu has a memtest function built in but I'm not familiar with it)
Oh, yeah, I'd do this with just the questionable stick of memory in place.  memtest will start running tests on the installed memory.  You have to watch for a while to figure out what's happening.  It has - um - I don't remember exactly, but it throws different bits of info at the memory, testing it about eight or ten different ways.  memtest will keep looping thru these tests until the next Ice Age, so if you just let it run for a couple of hours and don't get any errors then the stick passed.  If it didn't pass, random memory errors are gonna keep causing weird phenomena and the stick should be kept out of your PC.
Just for practice, I'd test the other stick too...

---

