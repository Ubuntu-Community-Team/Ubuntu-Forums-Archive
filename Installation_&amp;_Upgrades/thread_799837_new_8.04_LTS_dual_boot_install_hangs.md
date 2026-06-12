---
title: "new 8.04 LTS dual boot install hangs"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by Franc88 on 2008-05-19
Hi folks,

I am finally making the plunge into putting a linux distro into my laptop.  From what I've read and heard, ubuntu seems to be a good one for linux newbies.  So I d/l'd the image and burnt a copy to cd and tried to install it on my Dell 8600 laptop.  I am trying to do a dual boot with Windows XP.  

Since I'm doing a dual boot, the HowTo stated I needed to do a manual partition of the HD, make it logical, setup a swap and root.  So I created a 20gig root and a 4 gig swap.  When I click on continue, dialogue box says "partitioning" but it just sits there.

At this point I wait, and wait, and wait.  Meanwhile, my cd-r/dvd-r is spinning and spinning and sounds like a broken record stuck on the same track.  So I try and eject it but no go.  So I turn off the laptop.

I rebooted, started from CD again and this time, selected the "guided" partitioning of the HD.  This went a bit smoother and partitioning went fine.  The system started installing files but when it got to about 15%, it stopped with an error stating that the CD copy might be bad and to try to burn a new copy at a slower speed or do an install in a "colder" environment or that the HD needs to be cleaned.

Well I've tried everything I can think of to get this distro to install but no go.  I've defragged the HD before the install but I did it again and tried to install, no go.  I've tried to do manual partitioning again but no go.  Basically, I've taken about 24hours of trying to get this distro just to install.

Oh, and I did check to make sure a Dell 8600 laptop was compatible with ubuntu.  It stated it was but no comment on how well it does with this newest release.

Does anyone have any ideas of what I can be doing wrong or what I can try?  I'm comfortable using cmd line since I've used cmd line before windows 286.  I used fdisk and debug to low lvl format rll and mfm drives in the old xt boxes.  

Thanks in advance for any help or suggestion.

---

### Post by logos34 on 2008-05-19
> **Franc88 said:**
> The system started installing files but when it got to about 15%, it stopped with an error stating that the CD copy might be bad and to try to burn a new copy at a slower speed or do an install in a "colder" environment or that the HD needs to be cleaned.


Did you also verify the md5sum of the downloaded .iso?

---

### Post by Franc88 on 2008-05-19
> **logos34 said:**
> Did you also verify the md5sum of the downloaded .iso?

Yes I did.

---

### Post by jtrindle on 2008-05-19
Did you actually do a new burn of the CD at lower speed?

I would recommend trying the alternate CD and using a text-based install.  This uses less RAM and that leaves more left over for CD buffers.  Going the alternate CD / text mode route was the only way I could install on a 128MB RAM system.  I had the same issues you did, with the install dying part-way through, and the CD drive seeking like crazy.

---

### Post by Franc88 on 2008-05-19
Thanks, I'll try and reburn the image at a slower speed and get the alternate CD.

---

### Post by Franc88 on 2008-05-19
UPDATE:  got ubuntu 8.04 to install and dual boot on my laptop.

Here's what I ended up doing.  

1.  D/l alternate cd iso image and burnt it at a slow 4x speed
2.  cranked the a/c and fans so the room was at a cool 65 degrees to eliminate heat issues
3.  rebooted with cd in drive and did a manual partitioning of the hd.
4.  partitioned a 20gig root, 4gig swap, and a 1gig primary for boot loader.
5.  let cd install files and restarted.
6.  dual boot screen came up and let me boot to ubuntu.

Now I'm just trying to see what devices work and doesn't.

thanks to all that helped and i hope this helps someone too.

---

