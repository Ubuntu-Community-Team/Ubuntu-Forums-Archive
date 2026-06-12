---
title: "Attempt to mount a filesystem with type ext3 ... at '/' failed"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by gkaragoulis on 2008-11-11
During installation I keep getting this error.  The partitioner gets to 5% and just quits with that error message.  I've read at a bunch of forums and bug reporting sites about this and nobody seems to have an answer.  Anybody else have luck?

---

### Post by gkaragoulis on 2008-11-11
Ok so I was able to get past the error, even though I don't understand why.  Here is what I did:

I booted to the live cd without installing, then tried to install by clicking the button on the desktop.  However, before doing that I ran the command "/bin/update-dev", per someone's suggestion on another site I read.  After running that command the install worked fine!

No ideas why that worked though...

---

### Post by krosenqu on 2009-11-11
> **gkaragoulis said:**
> Ok so I was able to get past the error, even though I don't understand why.  Here is what I did:

I booted to the live cd without installing, then tried to install by clicking the button on the desktop.  However, before doing that I ran the command "/bin/update-dev", per someone's suggestion on another site I read.  After running that command the install worked fine!

No ideas why that worked though...


I received the same error when upgrading my Eeepc 900a with a 32GB super talent ssd.  The error is attached as an image (sorry for the Droid camera phone pic).


I tried your method above but it didn't work for me (nothing appeared to happen).  I've also using the install icon on the desktop with the eeebuntu release AND the latest 9.1 ubuntu release.  Same issue with both.

**_Anybody have an idea of why this error is occurring or how to fix it?_**  Do I have to mount the hard drive somehow?  I can partition the hard drive however I like in partition manager but it doesn't get past this step when installing, even if I format the ssd to ext3 before I run the install.



HOLY COW.  I just realized I'm posting this an EXACT YEAR TO DATE from your post!  Sorry for the resurrection!

---

### Post by krosenqu on 2009-11-11
The solution was that whatever the first partition was always got curropted for some reason. 

So I created a 256MB unpartitioned space at the beginning.

All is well now :)

---

### Post by theaskanison on 2010-02-01
Thank you [krosenqu]("http://ubuntuforums.org/member.php?u=917306") for adding to this thread. I was having this problem installing Ubuntu Remix on my son's Acer aspire one ZG5 until I tried your solution and it went pass this error message :p...to quit unexpectedly after 90% of the installation. :shock:

For some reason remix on my system was bugging out so I decided to install Ubuntu desktop 8.10 instead and it worked (after reading some forums and tweaking little things here and there). Now is upgrading to 9.04: 5 min remaining...I'm keeping my fingers cross!

---

### Post by krosenqu on 2010-02-01
Hopefully you get it working!  

I kept having problems with updating Eeebuntu.  It would crash every time I updated and I had to reinstall the operating system again.  I eventually gave up and installed Windows 7 for now.  I'm waiting for a new version of Eeebuntu to get released before I try Linux again.

---

