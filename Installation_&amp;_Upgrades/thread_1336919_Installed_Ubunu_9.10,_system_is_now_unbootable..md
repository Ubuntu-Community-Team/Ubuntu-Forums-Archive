---
title: "Installed Ubunu 9.10, system is now unbootable."
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2009-11-25
I have an old system, its a Pentium 3 system, the motherboard dosen't support LBA48.

So it reads my 160GB HDD as a 136GB HDD.

I installed Windows XP first, using the "entire" drive, which was about 131 or so gigs of space, for XP.

After updating and installing all my Windows apps, I then booted my Ubuntu 9.10 LiveCD, which ignored the bios and could see the full 160gb hdd.

I custom-partitioned it, I gave all but 2 gigs of the unpartitioned space to Ubuntu (setting the mount point as "/"), and the renaming 2 gigs I partitioned as swap, all of them as primary partitions.

Now, when I turn on my computer, after POST I get this:

[B]GRUB loading.
error: unknown filesystem[/B]

The menu dosen't even appear.

Is grub2 unable to read past the 136gb area of the drive, or is there another problem? Is there anything I can do to fix this?

As it is, my PC is basically unbootable right now.

---

### Post by jacobs444 on 2009-11-25
typically if your bios doesn't support it then you need to install /boot to a seperate partition of 512mb  at the very beginning of the drive, it should then work.

---

### Post by Cyber Akuma on 2009-11-25
Yeah, I was hoping that there would be a way to do it with just grub2 itself, but if not, I assumed that I would need to create a boot partition..... however....

At the beginning of the drive? I can't shrink the Windows partition by a few hundred megs and put it there, still within the 136gb limit?

If not, is there any way I can safely move my Windows partition without corrupting it to do that?

And isn't 512megs kinda overkill? Wouldn't 128 or so be more than enough?

And finally, is there a guide anywhere on how to do this? And would it not cause any problems with updating the linux kernel, the updater auto-updating the grub config file, etc?

---

### Post by jacobs444 on 2009-11-25
use the live cd, and gparted(the partition editor under system>administration you can shrink and move your windows partition to the right by 512mb. I think you should use 512, just in case for some reason less than 512 caused me a compatibility issue. As far as the other questions, linux filesystem once mounted, knows where everything is so no you should not have any issues.

---

### Post by Cyber Akuma on 2009-11-25
I've been able to shrink Windows partitions, but any time I tried to move them usually resulted in corruption, so id like to avoid putting a partition before the Windows partition if possible since it would essentially be a move.

Would I be able to shrink the Windows partition by 512 megs and put the boot partition after Windows instead?

And what problems did you run into with partitions smaller than 512 megs before?

And how would I setup the smaller partition as the boot partition anyway? Just set the mountpoint as /boot in the Ubuntu installer when partitioning my drive?

Finally, this would probably set the boot partition as hda4 since its the 4rd partition I would create on the drive, is there any way to reorganize/number them so they would be in order, making the boot partition hda2 instead of 4?

---

### Post by mr clark25 on 2009-11-25
i would back up the windows data and then resize. then you can see whats corrupted, and replace it.

---

### Post by darkod on 2009-11-25
Even better, depending how long ago you installed XP and how far have you got setting it up, it's better to do clean install of XP too. But this time allocate only the space you need for XP to it. I have no idea why you let it take 131GB the first time when you were planning to add ubuntu too, just doubles the work and XP is sometimes problematic with shrinking as you noticed yourself.

If you can afford to clean install XP again that would also allow you to create the partitions in order:
512MB /boot
XP ntfs
Data ntfs (if you want to)
Ubuntu
swap

You noticed yourself the /boot even if you manage to create it now would be hda4. To my knowledge there is no way to change that since hda1, hda2 and hda3 still exist. And it actually might be a problem that hda4 will in fact be first on the beginning of the hdd (if you manage to put it there). Not 100% sure about that, but it might be. I've seen boot problems threads here and a lot of them have some "strange" order of the partitions so it might affect the system behavior.

---

### Post by Cyber Akuma on 2009-11-25
Im far too deep into configuring Windows to start over im afraid, whats wrong with putting the boot partition after windows instead of before?

Also, just HOW do I setup a boot partition? Do I just set the mountpoint as /boot when installing ubuntu as I said or is there something else I have to do?

---

### Post by darkod on 2009-11-25
Yes, you just mount it as /boot during install. You can try putting it after XP, if XP is 131GB the /boot would still be within the visible 136GB. See how it goes since that's the easiest solution right now.

---

### Post by Cyber Akuma on 2009-11-25
I partitioned off 250 gigs from my windows partition and created a 215 meg ext2 partition for boot, this should fall within the 136 gigs limit.

However, grub STILL complains "unknown filesystem"

What else can I do?

---

### Post by Cyber Akuma on 2009-11-26
Argh, this is starting to drive me CRAZY!

Ok, I am 100% completely certain that the problem is due to LBA48, somebody suggested I try this:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

But to replace the "grub-install /dev/sda" command with "grub-install --disk-module=ata /dev/sda" and then run "dpkg-reconfigure grub-pc"

This worked, but now I have a few more problems:

1. The SECOND my computer goes from POST to GRUB, before grub has even had a chance to even look for any config files (meaning modifying any of my config files won't do anything) it puts my screen out of range, and it does NOT recover until I turn my monitor back off and on again. Its not the video mode that sets it out of range, but the process of changing video mode (or rather, grub loading) that does this. Any ideas how to fix this? Because it is seriously driving me out the wall.

2. Grub now takes forever to load, it stays at the "GRUB loading." screen for about a full minute until my menu list comes up.

3. It puts windows at the very bottom of the list every time it runs an "update-grub", considering that it adds a new menu entry for each kernel at the TOP of the list, this effectively makes it impossible for me to set windows as the default, since I need the default by menu location, and this keeps changing every kernel update. Is there any way to make Windows the default regardless of where it is, or set Windows at the top of the list?

4. I can't boot Windows! It just says "error: device format "ata0,1" invalid: must be (f|h)dN, with 0 <= N < 128"

Argh, please help, this has me tearing my hair out!

---

