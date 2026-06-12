---
title: "Where can I get the bulletproofx failsafe mode"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by stevekrules on 2007-09-10
I cannot install Ubuntu, I always get the xserver graphics error, I made a thread about this before but no one helped me..

I saw from a friend this link [http://people.ubuntu.com/~bryce/BulletProofX/](http://people.ubuntu.com/~bryce/BulletProofX/)

and I was wondering where can I get this? I really want Ubuntu but cannot even run the live cd..

---

### Post by Pumalite on 2007-09-10
You might need Alternate CD. Post specs.

---

### Post by merlinus on 2007-09-10
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

Once installed, you can change the driver to vesa from a command line to get to a gui, where you can search for and install the correct drivers.

---

### Post by stevekrules on 2007-09-10
I've tryed the text-based installer with my old video card but no luck, I haven't tryed with this new one but I guess it's worth a shot, I doubt it'll work though..


Here are my PC specs:
Intel P4 2.4GHZ
1.5gigs of ram
500gig hdd
ati radeon x1300 256mb PCI

---

### Post by merlinus on 2007-09-10
Make sure to checksum your download, and burn as disk image at no more than 4x.

Info on checksum here:

[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

---

### Post by stevekrules on 2007-09-10
> **merlinus said:**
> Make sure to checksum your download, and burn as disk image at no more than 4x.

Info on checksum here:

[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

Okay well, I'm currently downloading the text-based version now, it's going to take about 2hours to download, and I have school & work tomorrow so I wont be able to try it today, only tomorrow at  like 7PM (-5 EST).. I will make sure to checksum the download and make sure Infra Recorder burns it at 4x..

Anything else I should try or I forgot?

---

### Post by merlinus on 2007-09-10
Keep a positive attitude....

:)

---

### Post by stevekrules on 2007-09-10
> **merlinus said:**
> Keep a positive attitude....

:)

:lolflag: I will try, I really want Ubuntu :D

---

### Post by UbuntuniX on 2007-09-12
Good luck, Bacon. :)

---

### Post by stevekrules on 2007-09-13
Sorry for the late reply; I just checked the MD5 checksum and it said it was the same, I burnt it using Infra-Recorder at 4x, and just put it in my pc.. The autoplay thing starts, I restart my PC and it goes into the Ubuntu menu. I hit install and yadada I'm now at the partitioning step.. I picked my HDD, and I partitioned it to 80gigs (it said smallest I could do is 74?)


Now it's been like 10 minutes and it's still here:

[img]http://img528.imageshack.us/img528/4871/getattachmentaspxhs2.jpg[/img]

Did it **** up? Did I pretty much lose all my data? :confused:

It's a 500gig, but I've partitioned it before using Norton partition magic and it didn't take nearly as long..

So it's only partitioning like 250gigs, hopefully it will go to 1% then I would feel better.

(Sorry for sidewards pick, only have a camera phone and it's only how I could fit it into one pic)

edit:
I got annoyed and turned it off, I rebooted into windows and it did checkdisk by itself, no errors and I'm back up.. I have a spare 80gig harddrive that I do not use, could I use that and dual-boot between xp/ubuntu even though they are on different hdd's?

If so do I need to pre-format it to a certain file system then go install it on Ubuntu? (They are NTFS).

---

### Post by stevekrules on 2007-09-13
Sorry for the double-post but I wanted to bump the thread..

Okay so I put in a another harddrive I had, created the partition for ext3 filesystem and installed it.. Restarts, goes into grub loader, I pick the first chose which is like Ubuntu then some numbers, it goes to the Ubuntu loading screen then a black screen with white text telling me to login, I go to login and I get the xserver graphics error telling me no screens were found, it disables xserver and tells me to restart it when configured correctly, I try to login, and I cannot type my password, when I try to type the password I cannot hit anything but enter..

So after failing login 5 times it boots me out of login, I tryed doing "sudo login" but it still does not let me type a password..

so I type "gdm restart" and it restarts the gdm, tells me to login and again xserver graphics error..

How do I fix this xserver graphics error, I read somewhere about changing the driver to vesa or something..

Sorry again for the double post but I really need help :(

---

