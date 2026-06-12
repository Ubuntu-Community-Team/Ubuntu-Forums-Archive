---
title: "Grub 2 problems"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by TomyVk on 2010-01-25
I had problems with the ubuntu 9.10 installation. Everything was ok till the setup was installing grub2. Ive tried it several times and no success.

After several failed installations ive just installed ubuntu 9.04 what has the old grub loader and it worked without problems, and i just upgraded my ubuntu to 9.10, what works ok now, but i have still the old grub loader.

Grub 2 seems to have problems with my hdd.

I have a SATA WDC WD5000AAKS-0

on a nVidia Corporation MCP61 SATA Controller (rev a2)

It just looks like grub cant find the device by some reason, ive tried even to alter where to install the boot manually cause i have a separate boot partition with a xfs filesystem.

I would upgrade to grub 2 but i'm affraid that i wont work again like at those failed installs.

---

### Post by TomyVk on 2010-01-27
Bump

---

### Post by Leppie on 2010-01-27
what happens exactly when you install grub2?

---

### Post by TomyVk on 2010-01-27
> **Leppie said:**
> what happens exactly when you install grub2?

It just throws out a error. Says cant install grub. Like it cant find my HDD partition.
Everything else in the instalation goes well.

Weird is that the old grub has no problems....

---

### Post by dabl on 2010-01-27
It's not the hard drive -- I have several WD's of the same type.

Can you go into BIOS, to the SATA mode settings, and change it to "legacy IDE"?  That might let you install Grub.  If so, possibly you can change it back to "AHCI" after grub is installed.

---

### Post by TomyVk on 2010-01-27
Well, i wont try it now. I have 9.10 running on the old grub loader. Hope the next version wont mess it up :)

I didn't see any "Legacy IDE" option in my bios tho....

---

### Post by Leppie on 2010-01-27
> **TomyVk said:**
> Weird is that the old grub has no problems....
the old grub is smaller in size (takes less mbr space)

---

### Post by darkod on 2010-01-27
> **Leppie said:**
> the old grub is smaller in size (takes less mbr space)

It's not just that. The OP said "I even manually tried to install boot because I have boot partition".
If you don't mount the partition as mount point manually during install, ubuntu ignores it. So for example, if it's boot partition from another OS you didn't need to worry about it.
My guess is by trying to alter the default, you were asking for something impossible and grbu2 didn't want to do it. For example, it doesn't really want to get installed onto a partition as opposed to MBR. While grub1 doesn't complain. But if you did that, that would mean you're chainloading into grub.
Anyway, if you're happy how it's working right now, use it like that. Maybe it was because of something you tried to do, or you just have specific setup.

---

### Post by Leppie on 2010-01-27
> **darkod said:**
> It's not just that. The OP said "I even manually tried to install boot because I have boot partition".
i know.
i myself have a jfs boot partition, but that doesn't prevent grub2 from installing. xfs is supported by grub2 (i have other partitions using xfs).
the OP also stated "It just looks like grub cant find the device by some reason", so maybe it's a hw issue or just the proprietary sata controller.

---

### Post by TomyVk on 2010-01-27
i have a 100mb xfs /Boot partition its even too much for it.
I used the same on the old grub.
Problem is that grub seems not to recognize the device ID.
Ive tried all options you get when you click on advanced before you start the install. None of them worked.

I even tried to use the "Use entire disk" and i got the same problem.

I don't have windows on my machine.

I'm not the only one who has problems with grub 2. My friend has a newer MB then i have and he runs in the same problem.



I think that grub 2 don't support the new hardware...

---

### Post by oldfred on 2010-01-27
You mentioned an Nvidia controller, were these drives ever in a raid configuration? The drives keep settings that interfere.

---

### Post by TomyVk on 2010-01-27
Nope, i have only this hdd installed.

---

### Post by TomyVk on 2010-03-01
Bump

---

