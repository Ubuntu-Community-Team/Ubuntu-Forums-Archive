---
title: "Will I have a problem installing with SATA and IDE drives?"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by wolfmanyoda on 2010-11-17
I've tried Linux a few times over the years, the last time I had to install through Wubi because linux couldn't see my SATA drives.

I'm currently running Windows 7 on a SATA drive and I have an old IDE drive laying around somewehre. My board supports both types of drives.

My questions is, if I try to install Ubuntu onto the IDE drive(not through Wubi), will grub also detect the SATA drive so that I can choose which OS to use on startup?

Thanks

---

### Post by sikander3786 on 2010-11-17
Yes it should definitely see that Sata drive.

The best option would be to boot from a Live CD and test all your hardware including your Sata HDD.

You can try this command from terminal to see your HDDs.

```
sudo fdisk -l
```

Linux has had some problem with a few Sata Controllers but it is good at 99.8 % of them.

---

### Post by screamingturnip on 2010-11-17
> **wolfmanyoda said:**
> I've tried Linux a few times over the years, the last time I had to install through Wubi because linux couldn't see my SATA drives.

I'm currently running Windows 7 on a SATA drive and I have an old IDE drive laying around somewehre. My board supports both types of drives.

My questions is, if I try to install Ubuntu onto the IDE drive(not through Wubi), will grub also detect the SATA drive so that I can choose which OS to use on startup?

Thanks
Doesn't having two hard drives supersede the need for Grub? Can't you just switch when given the prompt at the BIOS screen.I mean I maybe a total boob but that's how I always did it when switching between a live CD and my hard drive

---

### Post by wolfmanyoda on 2010-11-17
> **sikander3786 said:**
> Yes it should definitely see that Sata drive.

The best option would be to boot from a Live CD and test all your hardware including your Sata HDD.

You can try this command from terminal to see your HDDs.

```
sudo fdisk -l
```

Linux has had some problem with a few Sata Controllers but it is good at 99.8 % of them.

Thank you, I didn't think to check through a Live CD.

I'll go download an iso and see what happens.

---

### Post by wolfmanyoda on 2010-11-17
> **screamingturnip said:**
> Doesn't having two hard drives supersede the need for Grub? Can't you just switch when given the prompt at the BIOS screen.I mean I maybe a total boob but that's how I always did it when switching between a live CD and my hard drive

Actually, I don't know what two hard drives will do at boot.

---

### Post by sikander3786 on 2010-11-17
But if you can survive without switching HDDs from Bios and all that, why not following the easier and better path. Grub2 detects almost anyother operating system in there, why not let it do the job for you.

All you need to do is to set the HDD that contains Grub as your first boot device. Grub automatically finds all other OS and adds them to the menu. If it doesn't, it can be manually done by running the update-grub command.

---

### Post by dino99 on 2010-11-17
my system have 2 pata & 1 sata, bios set to ahci (if yours have "compatible" its better than ahci) and its working smootly :)

---

### Post by wolfmanyoda on 2010-11-17
Well here I am running the Live CD.

After some screen flashing and a message saying "invalid RT chipset detected" it booted fine.

My SATA drive was found with no problem and my wireless USB adapter just asked for the key to connect. Way easier than last time I tried linux.

I guess I'll put the IDE drive in later and go for it.

Thanks everyone.

---

