---
title: "booting ubuntu on casper minibook stalls"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by slowwound on 2011-04-03
hi.

i got a casper minibook, and i want to install ubuntu.
first, i tried a live-cd (actually it's a live-usb, since the netbook doesn't have a cd-drive). it booted, but stalled at the plymouth logo.

then i tried the usb-install with the ubuntu 10.10 iso.
it stalled at plymouth again.

then i tried the alternat-cd install.
it stalled a few seconds after the window for choosing languages popped up.

also tried the boot options *nopcmcia* and *nomodeset*. didn't work either.

the usb was prepared using *unetbootin*.
the netbook has an 1.6GHz intel atom, 1GB RAM.

please help me install ubuntu.

---

### Post by Dutch70 on 2011-04-03
Have you checked the md5sum of the downloaded .iso?
[[COLOR="RoyalBlue"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

You may also want to check the cd/usb. That may not be your problem, but it's easy enough to rule it out.
[[COLOR="RoyalBlue"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck")

---

### Post by slowwound on 2011-04-03
no, haven't tried that. i'll try it, thanks for the advice.

i forgot to mention that the same usb-stick, prepared with the same isos, worked perfectly on other computers.

so, do i still need to check md5sum ?
or is the problem somewhere else ?

---

### Post by Dutch70 on 2011-04-03
Not the md5sum, but it is possible that your usb stick has been corrupted. You can easily rule that out by checking it.

---

### Post by slowwound on 2011-04-03
how can i check it ?
by using another usb-stick ?

i used that same usb-stick on another pc, with just the same live-cd on it, and it worked just fine...

---

### Post by Dutch70 on 2011-04-03
I really wouldn't know what else to recommend. 

Post back with your graphics card, and maybe someone else will know more about it.

---

### Post by slowwound on 2011-04-04
it's a *Intel GMA 950 64 MB*.

hope we can find the problem...

---

### Post by slowwound on 2011-04-05
when i hit *ESC* before it stalls in plymouth, it gives me the following error message:

*(process:314): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)*

maybe this helps to find a sollution ?!

---

### Post by slowwound on 2011-04-05
one more information, that might help:

the casper minibook is a msi wind clone.
seems to be the same hardware, bios, and stuff, just different casing.

---

### Post by mörgæs on 2011-04-05
> **slowwound said:**
> when i hit *ESC* before it stalls in plymouth, it gives me the following error message:

*(process:314): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)*

maybe this helps to find a sollution ?!

Post 176 in 
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)
gives a solution to that.

---

### Post by slowwound on 2011-04-07
> **mörgæs said:**
> Post 176 in 
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)
gives a solution to that.

unfortunately it didn't work.

but the funny thing is, that karmic koala (9.10) starts just fine.
so i installed it, did an upgrade to lucid lynx (10.04) and then to maverick meerkat (10.10).

everything works well. but i just don't get it, why maverick doesn't start from usb ?

---

### Post by mörgæs on 2011-04-07
Remember that the 10.10 ISO is different from the 10.10 system you are running today on your machine, as several hundreds bug fixes have been applied.

Good that you got it solved. Please mark the thread so.

---

### Post by slowwound on 2011-04-07
but the 10.10 setup iso worked fine on 3 other PCs i installed ubuntu on...

is there an iso for a 9.10 live-cd somewhere ?

how can i change the thread as solved ?

---

### Post by mörgæs on 2011-04-07
It is not uncommon that a computer prefers a particular release of Ubuntu, with or without boot options. Don't expect 10.10 to work better than 10.04.2 on all machines you encounter.

Hence a good first step is to feed a troublesome computer a selection of the newer releases, if you are to begin troubleshooting. 

Did you try both the 10.04.2 and 10.10 mini-iso's on the minibook? I would recommend this rather than installing 9.10 and upgrading.

You could also try 11.04, though it is in beta. Maybe you are lucky...

'Solved' is in 'thread tools'.

---

### Post by slowwound on 2011-04-07
well, i just tried 10.10 and 9.10.

i may try 10.04 though, when i have more time...

---

