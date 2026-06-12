---
title: "Fresh installation on Sata"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by snake_eyes on 2010-02-15
Hello,

I'm trying to install the Ubuntu Desktop 8.04.4 LTS on GiGABYTE motherboard with SATA Cable, unfortunately when it go to step 4 which is the Prepare partitions it didn't detect anything, although the My HD is 500GB 

I tried to install windows XP it installed smoothly :(

So how do I fix this issue? Although the CD is the Original from the Ubuntu Company.

Cheers,

---

### Post by darkod on 2010-02-15
If you boot into the live desktop can you see the hdd in Gparted and fdisk?

---

### Post by snake_eyes on 2010-02-15
I'm able to install the windows unlike the ubuntu, that's mean that the HD was detected but I thing there is something I missed, I would appreciate if you can share you information....

---

### Post by darkod on 2010-02-15
Leave windows aside, you already said you can install it.
Boot with ubuntu cd, select Try Ubuntu option, that will load the so called live desktop, running ubuntu from the cd.
Open Gparted (System-Administration) and see if you can see the disk there.
Also in terminal type:
sudo fdisk -l

to see if it can read it. So far I am aware of an issue when a disk has been used in raid the installer not to see it, but that is only for 9.10, not for 8.04.

---

### Post by snake_eyes on 2010-02-15
> **darkod said:**
> If you boot into the live desktop can you see the hdd in Gparted and fdisk?
no I'm not able to detect it, "No Devices Detected" :(

Any help?

---

### Post by darkod on 2010-02-15
Double check your connections and the BIOS settings you have. There might be SATA Type setting in BIOS, try with AHCI, or Native IDE, etc. But not RAID.
It's very strange not to see it at all, especially since XP can see it. Look around. Check for loose cables, etc.

---

### Post by snake_eyes on 2010-02-15
I'm connecting the CD via IDE and the HD via SATA, so is this connectivity with effect this installation?

---

### Post by snake_eyes on 2010-02-15
> **darkod said:**
> Double check your connections and the BIOS settings you have. There might be SATA Type setting in BIOS, try with AHCI, or Native IDE, etc. But not RAID.
It's very strange not to see it at all, especially since XP can see it. Look around. Check for loose cables, etc.

I tried with AHCI and it works well :)

thank you alot...

Cheers,

---

### Post by darkod on 2010-02-15
> **snake_eyes said:**
> I'm connecting the CD via IDE and the HD via SATA, so is this connectivity with effect this installation?

If you use Native IDE mode for SATA, maybe. Can you plug the hdd into different SATA connector on the board? Power off the computer first.

The first 2 SATA connector might be shared with IDE. I don't have IDE devices so I can use them as SATA but in your case it may be a problem.

---

### Post by darkod on 2010-02-15
> **snake_eyes said:**
> I tried with AHCI and it works well :)

thank you alot...

Cheers,

Great. No problem. :)

---

### Post by loyo on 2010-02-15
Does the ubanto have bug? can not recognize the sata HDD in this hardware?

---

### Post by darkod on 2010-02-15
> **loyo said:**
> Does the ubanto have bug? can not recognize the sata HDD in this hardware?

What are you talking about? Do you also have a similar problem? If you didn't notice changing the SATA mode to AHCI resolved the issue the OP was having. And ubuntu has nothing to do with this most likely. It's up to the BIOS settings and how and where devices are connected to the motherboard.

---

