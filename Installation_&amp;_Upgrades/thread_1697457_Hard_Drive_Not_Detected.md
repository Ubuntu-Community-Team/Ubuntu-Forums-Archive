---
title: "Hard Drive Not Detected"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by akanwhatnot on 2011-02-28
Hello,

I've done a bit of Googling and at this point am stumped.

Any help would be most appreciated.

My employer asked me look at a DIY built computer where Windows would not boot. You'd get as far as the splash screen and then it would hang. I popped the 320GB WD hard drive in another box and it booted fine. I recovered my employer's files but now I'm asked to get the original  machine running. They don't have a windows install key or disc, so I decided to try Ubuntu.

Obtained 10.10 install disc but when I went to install, it goes to the partition screen but shows no disk.

I then tried installing on a different computer and was successful. I then formatted the 320g drive on that machine and then went back to the original machine and again, no disk shows up when you go to install it. The install screen shows checked 2.6Gb avail, internet connected etc, but on next screen nothing. I checked out disk utility and the hard drive shows up there.

The machine I'm trying to install on has an Asus Motherboard and an Athlon Chip. I checked the BIOS and I didn't see any options regarding IDE legacy support (not sure if that has anything to do with the problem but it's something I saw around the web).

I am reasonably comfortable with linux (although quite the beginner) given specific enough directions, and of course would try to get any needed information to you.

Thanks in advance!
Luke

---

### Post by akanwhatnot on 2011-02-28
Hmmm...ok, put the 320g hard drive I'm having trouble with into the machine I had previously successfully installed Ubuntu on.

Same behaviour. I can view it, format it, mount it, but I can't install to it.

Seems this is specific to the hard drive?

Any help is much appreciated.

---

### Post by guilleme on 2011-03-01
Hi. Can you run ubuntu from the live disk with no problems? 
Do you have any other livecd you can try with? Well, right now I can't think about any other question that could be useful, nor any possible solution, but if I come up with something, I'll post it here. Please let us know any advances. 
See y'a.

---

### Post by Hedgehog1 on 2011-03-01
Assuming you had the cables properly plugged in:

If the problem moves with the drive, the problem is the drive (It is dying).

You were wise (and a little lucky) to get the data off of it.

---

### Post by akanwhatnot on 2011-03-01
Thank you for the response!

After stumbling around the web some more, I ran across some threads discussing how certain Western Digital hard drives can be mistakenly picked up by the LiveCD as part of a RAID array? subsequently causing the problem I'm having. The thread suggested that one way to resolve this problem was to remove dmraid.

I booted into the LiveCD, and ran sudo apt-get -y remove dmraid in terminal. Then attempted the installer again. Success!

The threads I was looking at also suggested that you could remove dmraid through Synaptic.

I'm installing now, and will post a final reply if successful.

---

### Post by akanwhatnot on 2011-03-01
This seems to have resolved my issue. Ubuntu installed and is running smoothly.

Thank you for your responses.

---

### Post by doriard on 2011-03-01
I think I'm having a related problem only Ubuntu recognizes my raid drive (C:) but not my non-raid SATA D: drive.  I want to install Ubuntu on the non-raid D: drive but Ubuntu doesn't even see the drive.  Windows 7 sees it just fine.  If I remove dmraid will that make it so Ubuntu won't see my C: drive?

---

