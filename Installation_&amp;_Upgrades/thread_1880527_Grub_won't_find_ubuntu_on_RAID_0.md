---
title: "Grub won't find ubuntu on RAID 0"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by Sompom on 2011-11-13
I've been working on this the whole weekend and I'm totally stuck. To be clear, I do have Grub installed, and it boots Windows fine, but it doesn't see Ubuntu. I've used a live usb, chrooted into the Ubuntu install and run update-grub, but it did no good.
Partitions:
1: MSI recovery
2: Windows boot area
3: Windows 7
4: Swap
5: Ubuntu
I believe the RAID controller (BIOS-based) sets the whole two drives up as a logical partition, which is why I can have 5. The partitions list is from memory (five minutes, I know) so I might have mis-remembered. If anyone thinks they look wrong for some reason, I'll use a live boot to go look.

Anyway, just a restatement of the goal of this post, has anyone had any experience with RAID 0, or does anyone know how I can add the Grub option manually. I used the command line to get into Ubuntu, but it dropped to the repair console before fully booting, I probably didn't include something important.

---

### Post by darkod on 2011-11-14
One question, did you install ubuntu with the alternate install cd or the standard desktop cd? Because for raid you need to use the alternate cd, it has built-in support for raid.

---

### Post by Sompom on 2011-11-14
I used the normal CD, and it installed fine. I partitioned manually, and it detected the two drives as one. At the end Grub threw up with some error, so I had to use a live boot to install it. My understanding is that RAID support was built into the 9.04 release and has been there ever since, but I've been wrong before.

---

### Post by darkod on 2011-11-14
The package for bios raid or dedicated controller raid is dmraid and it is built-in since 9.10. But still the recommendation is to use the alternate cd. I don't know if it installs grub2 correctly, have never tried it.

This link has a procedure how to add grub2 after the install, try to reinstall it to make sure it's fine:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Watch out to use the correct procedure, it has a section about using the Live CD (desktop cd).

---

### Post by Sompom on 2011-11-14
So, I just live booted and used boot-repair to reinstall grub (again).
Here is the log
[http://paste.ubuntu.com/738896/](http://paste.ubuntu.com/738896/)
I made sure to use dmraid, as that sounds like the most correct one and it is mentioned in your previous link. I'll reboot now and see what has happened.

---

### Post by Sompom on 2011-11-14
> **Sompom said:**
> So, I just live booted and used boot-repair to reinstall grub (again).
Here is the log
[http://paste.ubuntu.com/738896/](http://paste.ubuntu.com/738896/)
I made sure to use dmraid, as that sounds like the most correct one and it is mentioned in your previous link. I'll reboot now and see what has happened.

Yes! It worked! Having compared the two options, mdRAID and dmRAID, I'm sure it was inexperience that caused me to be failing thus far... mdRAID is linux fake RAID, whereas dmRAID is software RAID, which is what the BIOS is obviously using
Thank you for helping, as I did use some tidbits from that link (which I had seen before but never bothered to read... stupid me.)

---

### Post by darkod on 2011-11-15
Glad you got it running. Actually, it's the other way around. mdadm is the package for software linux raid, and dmraid is the package for fakeraid. It's called fakeraid because people usually use the bios raid, and not a dedicated raid card.
Bios raid simply uses cpu and memory resources, it doesn't have on its own, and that's why it got called fake raid.
Dedicated raid card obviously has its own resources, it's not "fake", but I think the same package dmraid is used.

---

