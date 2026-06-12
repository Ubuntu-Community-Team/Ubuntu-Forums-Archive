---
title: "Read Error - Grub won't load on External Hard drive"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by Uschiekid on 2013-01-08
I had ubuntu 10.04 installed on an external usb drive (partitioned:  ext4, swap and ntfs), that worked just fine and grub booted as it should  (only when the usb drive was plugged in).

Then I got a bigger drive (2TB, WD) and tried to install ubuntu 12.04, as I did before.  
It appeared to install without a hitch.
But  GRUB wouldn't boot.  I just get a very long initial sony screen, then a  very long blank screen with blinking cursor, then "read error".

I read  that sometimes boot gets put too far into the drive on bigger drives  (although only 300GB of that was in ubuntu formats), so I tried adding  extra partitions /boot and then /boot and /root.  Didn't make any  difference.

So I tried Boot Repair (and I didn't want GRUB on my  main hard drive, so I did use the advanced settings to change that) and  got the following URL which I sent to the email provided, but they also suggested posting it on a forum, so here it is:

[http://paste.ubuntu.com/1508302/](http://paste.ubuntu.com/1508302/)

It's a bit of a mess since there are probably more partitions than needed, but I tried first without.  There is also a record on this URL about my other external HDD...that is sdb, which I don't have plugged in at the time of the boot-repair...not sure if that is confusing.

So, I've  reinstalled about 4 times and repartitioned....both during install and  pre-done with gparted.  since I have no way to get into ubuntu, i'm  really not sure what to do.

Help! :D

---

### Post by fantab on 2013-01-08
Don't plug in both the External devices its probably confusing the System. Assuming that both sdb and sdc are external devices.

---

### Post by Uschiekid on 2013-01-08
> **fantab said:**
> Don't plug in both the External devices its probably confusing the System. Assuming that both sdb and sdc are external devices.

Thanks, yeah, when starting up, i am just trying to start from the new external hdd with ubuntu 12.04.  Nothing else is plugged in and so there are no other versions of ubuntu connected. (yes, sdb is external.)

---

### Post by Uschiekid on 2013-01-09
one other thing that i read might be an issue..

the external drive is usb 3.0

however, my computer doesn't have usb 30, so it is using the drive at usb 2.0

is there any way to work around this if it's the problem?  and is there any way to find out if it IS the problem?  I just bought this drive specifically for this purpose, so I'm gonna be annoyed if it stops me from using it as i want.  I don't even know if they make usb 2.0 with an external 2TB hdd...i didn't think it would be a problem, as long as it was backwards compatible which this one is.

---

### Post by Uschiekid on 2013-01-10
For anyone who comes up against this.

Turns out it's an incompatability problem.  When I tried plugging the hdd into another laptop (strangely enough a much older and with poorer hardware laptop), it ended up booting fine.

So I changed the whole drive back to NTFS and confirmed that my computer (VAIO) wouldn't boot up AT ALL (into windows) with that drive plugged in.

Stupidest of all it's not just a USB 3.0 on a 2.0 that is the issue, as another external hdd, also 3.0 and also fairly large (1TB) boots up fine into windows.  And I can 1 time choose it from the boot menu (esc), which I couldn't do with the 2TB drive (the menu refused to appear and would only allow me to go into BIOS setup...albeit very very slowly).

I tried updating my BIOS...apparently it's up-to-date.  I tried updating the external hdd firmware...it's up-to-date.  Can't see any other solutions.

So, what's the lesson to all this?  try booting with the drive in before doing anything!  What a waste of time!

For others future reference, don't buy a WD 2TB my passport 3.0 usb hard drive, if you have a VAIO (mine is a VGN model available only in Japan) and want to boot from it.

I'm returning mine tomorrow (returned to pristine condition of course!) and buying another Toshiba Canvio which works perfectly on my vaio.

---

### Post by Uschiekid on 2013-01-10
Update:

Bought Toshiba 1.5tb.  Partitioned, installed Ubuntu.  Worked like a charm.  :D

---

### Post by fantab on 2013-01-10
It was probably the GPT partitioning issue. For 2TB or more Drives you have to use GPT partition table... I suspect if that were the issue with your earlier drive... Elders might clarify on this.. 

I am glad that things are a 'charm' again...

---

### Post by Uschiekid on 2013-01-11
> **fantab said:**
> It was probably the GPT partitioning issue. For 2TB or more Drives you have to use GPT partition table... I suspect if that were the issue with your earlier drive... Elders might clarify on this.. 

I am glad that things are a 'charm' again...

Interesting.  Is there a reason that it would work fine on one computer and not on another? 

That for me was the baffling part and left me not knowing what to try, since it seemed compatability related.

---

### Post by fantab on 2013-01-12
Honestly, I am not sure myself. Like I said 'elders' on these forums might be able t to give a precise clarification.

From what I understand it could have been a case of [HYBRID MBR]("http://www.rodsbooks.com/gdisk/hybrid.html"). Your old computer, probably since it did not understand GPT at all, it used MBR and booted ok. But the newer computer, which understood GPT got confused and left you unbootable.  You can read [**[COLOR=DarkRed]srs5694[/COLOR]**]("http://ubuntuforums.org/member.php?u=1032238")'s posts on this forum and I found [**THIS**]("http://ubuntuforums.org/showpost.php?p=9038631&postcount=11"), it could give you some pointers.

Following Links might be helpful:
[http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

Good Luck...

---

### Post by Uschiekid on 2013-01-12
> **fantab said:**
> Honestly, I am not sure myself. Like I said 'elders' on these forums might be able t to give a precise clarification.

From what I understand it could have been a case of [HYBRID MBR]("http://www.rodsbooks.com/gdisk/hybrid.html"). Your old computer, probably since it did not understand GPT at all, it used MBR and booted ok. But the newer computer, which understood GPT got confused and left you unbootable.  You can read [**[COLOR=DarkRed]srs5694[/COLOR]**]("http://ubuntuforums.org/member.php?u=1032238")'s posts on this forum and I found [**THIS**]("http://ubuntuforums.org/showpost.php?p=9038631&postcount=11"), it could give you some pointers.

Following Links might be helpful:
[http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

Good Luck...

thanks for the pointers!  I'll go read them and  see what i learn :)

---

