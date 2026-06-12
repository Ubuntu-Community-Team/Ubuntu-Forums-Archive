---
title: "Can not mount /dev/loop0 clean install 11.04 i386"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by doktorOblivion on 2011-04-29
Trying to install a newly downloaded DVD image of 11.04 this morning on my T410 LT (4 core/4GB).  The image MD5'd okay, burnt it, stuck it in the drive, rebooted, asked me about install lang = english, select install ubuntu, get subject error and it falls into initramfs prompt.

So, I put my 10.04 install CD in and guess what, it works!

Is there a workaround for this issue?

:confused:

I will repeat what I have already posted in the another forum, and I understand install is a difficult part of the system, but there is always some glitch or another just trying to start install with ubuntu.  Once it runs, if it run, I normally see few other problems after that.  Should I wait for this release to stabilize a bit???

---

### Post by Dutch70 on 2011-04-29
Checking the md5sum is good, but did you also check the cd/usb for defects? There could be a problem with the burn. 

Also, selecting "Try Ubuntu" before installing will tell you if it will run properly on your system.

As with any release, it is a good idea to wait a couple months for it to stabilize.

---

### Post by doktorOblivion on 2011-05-02
Well, no luck, this is a definite problem.  I was however able to do the following to workaround the issue:

- Install Maverick via CD image, config internet, etc...
- Run upgrade to Natty over network

The above seems to work, at least there were no obvious issues, but it was from the latest version of Maverick CD iso, not the DVD.

The question therefore still stands, has the base install using a DVD been thoroughly tested?

---

### Post by suryasaha on 2011-10-25
I was having the same problem with a old Dell Optiplex desktop and 10.04.3 LTS even after checking md5sums. The problems was that I was using a rewritable CD (only those were handy). 

**Solution** for me was to use a standard CD-R to create a bootable disk and it worked like a charm. I checked each file on the CD using md5sum.txt in the root directory of the CD (md5sum -c md5sum.txt).

---

