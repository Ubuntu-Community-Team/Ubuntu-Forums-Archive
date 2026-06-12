---
title: "HP DV9000 Alternate Install Issues"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by Tubes6al4v on 2008-03-12
Ok, I have been sifting through the tons of threads on here and across the Linux community for the past few days trying to find a solution to my problem...

I have an HP DV9000
- AMD 64 bit Processor
- Vista Ultimate (HD has been split in half with the Vista Partitioner)
- Built in nVidia Graphics card
...etc


So I want to install a dual boot of Linux and Vista, but here are my experiences...

Ubuntu 64 bit Live CD Burnded to a DVD:
- Begins install, but eventually begins a repeating string of buffer errors and whatnot. At this point I can hear the DVD Drive cease to spin. I have to manually shut down after hours of waiting.

Ubuntu 64 bit Live on a CD:
-Same issue

Ubuntu 64 bit Alternate CD:
- Goes  through the whole installation process, but fails to install the "Base System". The issues begin when it reaches some GNUpg file, and then a bunch of other files fail after it. It does complete the install, but says that the Base System did not install correctly.

Mandriva 2008 
- Runs into the same issue as the Live Ubuntu about 65% of the way through. 


Ok, So from what I have read is that the DV9000 does not work well with the Live CD, and does not work well at all with Ubuntu Build 7.10, so I may try 7.04. 

Supposedly Mandriva works well with my Model Laptop, but it keeps hanging up.

I am suspecting that it has something to do with my DVD drive  loosing contact with the install session. I think I read somewhere that the Graphics takes up too much system resources, but I still run into issues with the text based installers and with low graphics.


I will pick up a usb drive to see if I can use one of those to run the install (which would eliminate the DVD drive from being the issue). Are there any OS's that work well through USB install?

OR does anyone have any tips on how I can get this rolling?



Thank you for any help!

---

### Post by Tubes6al4v on 2008-03-13
Update on the attempts:

Knoppix Live CD boots up wonderfully, but apparently it does not install well onto the hard drive. I do not know the extent to which I am limited by just using the live CD, so I would like to have a better HD install going on.


I burned a copy of Fedora 8    64bit and attempted to boot up the installation, but to no avail. It actually only gets to the screen where it says the copyright information (the very first screen), and the DVD stops spinning! How does this random crap keep happening?!?


Anyway, I am currently burning a copy of Open Suse 10.3 64bit and will try that. Supposedly it is a little bit more Hardware friendly?

---

### Post by Ptero-4 on 2008-03-13
SuSE might be the one to work. Specially since it's M$ sponsored, so it might have the "secret keys" that your laptop is probably requesting (which M$ only bundles in their products). Good luck on getting suse to work. But don't expect to get a "real" linux distro going in that box.

---

### Post by Pumalite on 2008-03-13
This might help:
[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by Tubes6al4v on 2008-03-14
SO I have already searched through those sites looking for solutions. What I am begining to think the issue is is the cd-rom not communicating with the install correctly. I may try installing from a thumbdrive, but if there is a firmware update for the TSST TS-L632M DVD burner, that would be wonderful.

---

### Post by Pumalite on 2008-03-14
Good luck.

---

### Post by TimelessRogue on 2008-03-14
I was having the same problem with installing the Hardy Heron on my new HP dv9623 (AMD Athlon 64 duo core) with both the Alternate and Live cd.  Alternate hung and wouldn't complete.  Live acted the same way but at a different point.  So, thinking I might have a bad cd, I burned a new copy of the Live cd ... the 32-bit version this time.  All went well and I have a fully functioning system ... except for wireless of course (the Broadcom thing).

Now ... all of this was with the 32-bit cd since, unless I'm wrong, there have been problems with the AMD 64 and the 64-bit version.  So try the 32-bit Live rather than the 64-bit.  That just may be the solution to your problem.  In any case, the 32-bit will run on a 64-bit system but not the reverse.

Gonna give the latest 64-bit version another go and report back regarding success or not ... hopefully not the latter ...

---

### Post by TimelessRogue on 2008-03-16
Well now ... I've gone and done it ... again.  Seems I'm always taking that one step beyond ...

Downloaded, burned and installed Hardy 64 last evening on this HP dv9623.  And since data is on another partition, I tossed the 32 install I did the other day and started with a nice clean disc.  So far all is well ... at least for the moment.  Installed all the updates plus a few others and haven't had a chance to check it all out, but as of now, there's nothing that doesn't work well.  Except that son-of-a-booger Broadcom BCM43xx wireless ... but I'm working on that this morning.  And I had to fiddle with my eth0 setup, but so what ...

And so there it is ... up and running with 64 ...

---

### Post by Pumalite on 2008-03-16
Hardy Heron 64 bit is lightning in a Core 2 Duo.

---

