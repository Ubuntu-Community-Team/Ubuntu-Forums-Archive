---
title: "Gutsy Gibbon quiting to BusyBox during install/livecd start"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by tracer07 on 2007-10-19
i'm trying to install ubunto on a vmware system for now..
C2D T7200, 4GB Ram, Geforce Go 7900GTX

i include a screen capture of what it shows.. allready tried all the stuff in the blackscreen thread..doesnt work.. always the same or similair error..

anybody got a clue?

[[IMG]http://img228.imageshack.us/img228/8185/gutsyinstallya1.th.png[/IMG]](http://img228.imageshack.us/my.php?image=gutsyinstallya1.png)

sorta new to linux.. did fool arround with dapper for a while tho..but nothing like this never happend to me..

---

### Post by mobiSid on 2007-10-19
i've got the same problem (( no ideas how to overcome this :(

---

### Post by ribrib21 on 2007-10-19
I have the same issue except I just get the prompt without an error message. I'm trying to run Gutsy on a P3 700 Mhz. It has an ATI card, if that makes a difference.

Any ideas?

---

### Post by pmoreau on 2007-10-19
Same thing here.  No error message, just drops into BusyBox.

I had a similar problem with the Fiesty CD.  I tried booting it over and over and it would die with some tty error.  Finally, after what seemed 20 or more attempts,  it actually booted!   I loaded Fiesty and have not had the problem since, until now I try to boot the new Gusty CD.

I have a Dual XEON HP WX6000.

They never figured out why Fiesty was do this, and it looks like it continues with the Gustsy CD.

---

### Post by beaseac on 2007-10-19
I am getting a similar issue however my error is something like "ATA7: Soft Reset Failed (timeout)".  However I have seen different errors as well.  Is it possible it does not support the motherboard?  It's a Striker Extreme with RAID with a 500GB single drive.

Thanks!

---

### Post by ribrib21 on 2007-10-19
UPDATE

Tried booting Mandriva 2008 and it worked.

Just replaced the CD ROM drive (which a much faster one) and now Ubuntu looks like it's loading.

---

### Post by pmoreau on 2007-10-19
> **ribrib21 said:**
> UPDATE

Tried booting Mandriva 2008 and it worked.

Just replaced the CD ROM drive (which a much faster one) and now Ubuntu looks like it's loading.

Now that you've posted this it rings a bell.  I remember seeing something about the Fiesty issue that was posted.   There was something about a IDE Reset that was sent to the CDROM and the Ubuntu Boot up NOT giving it long enough to recover before giving up and failing the boot.  Possibly your new CDROM drive recovered quicker.  I do have a new 16X DVD Recorder in my system.  Maybe it's just luck that you get a quicker one.

---

### Post by tracer07 on 2007-10-20
hmm, i'm just booting from a HD image.. ( since i'm doing it in vmware ) 
gonna burn it and see it that helps.. 
hope this gets solved tho ^^ kinda annoying :p

---

### Post by tracer07 on 2007-10-22
seems that did it.. installing fine now :)

---

