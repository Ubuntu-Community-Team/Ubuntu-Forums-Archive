---
title: "Move dual boot to new hard drive"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by javyn999 on 2010-06-24
Hey all.  I'm running 10.04 and Windows 7 64 in a dual boot config on my WD Caviar Blue 500 GB HD.  

I am getting a new WD Caviar Black with a larger cache, and want to move my partitions as is to from the old Blue to the new Black.  My new HD will be the same size as the old one, and I'd like to keep the partitions the same.

A.  Can this be done?  

B.  How?

C.  If it can, will it boot?  I don't care about having to reactivate Windows, but I'd rather not have to mess around with the MBR and Grub to get my new HD to boot.

Any help would be greatly appreciated!

---

### Post by darkod on 2010-06-24
A whole disk clone with CloneZilla should work, although I've never tried it myself.

However have in mind that in that case the partitions on the new disk will carry the same UUIDs and you can't run the old disk next to the new without formatting the old so that partitions get new UUIDs.
Apart from that I think it should work straight away, without needing to reinstall grub2 to the MBR (which isn't a big deal anyway).

---

### Post by javyn999 on 2010-06-24
Thanks for the response, I'm not sure what you mean by UUIDs though?  

Once I get the data moved to the new drive, I intend to format the old drive and give it away.

---

### Post by darkod on 2010-06-24
> **javyn999 said:**
> Thanks for the response, I'm not sure what you mean by UUIDs though?  

Once I get the data moved to the new drive, I intend to format the old drive and give it away.

UUID is unique identifier assigned to each partition when it's formatted. All partitions in your system have different UUIDs.
But when you clone a disk, the partitions will carry their UUIDs to the other disk too. If you use only one of the disks, no problem.
But if you connect both of them later in the machine, there might be confusion because the partitions on both disks will have same UUIDs. And ubuntu uses the UUIDs.

---

### Post by javyn999 on 2010-06-24
Ahh, okay, sounds like I don't need to worry about it then since I'll be removing the Blue.

Do you know much about these Caviars?

I want to get the Black and get rid of my Blue b/c the Black is faster, with a 32 meg cache as opposed to 16...

But...this computer is a workstation for my gf who sings and records music, and I hear the Blacks are much louder.  I wonder if it's too loud and will interfere with her music?  hmm

---

### Post by darkod on 2010-06-24
I don't know that much. And I have a Seagate. :)

---

