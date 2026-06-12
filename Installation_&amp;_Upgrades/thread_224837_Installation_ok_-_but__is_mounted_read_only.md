---
title: "Installation ok - but / is mounted read only?"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by abalone on 2006-07-28
Hello!

During install from the "server" installation CD I edited the partition table with hdb1 as swap and hdb2 as root FS (Reiser), mount options "default". So far, so good; installation went without a hitch, surprisingly.

But when I *boot* my brand spanking new Ubuntu, I get something about skipping journal replay due to the filesystem being read-only. 'mount' lists hdb2 with "(rw,notail)". Still can't write to it, though.

Once or twice it worked, and I apt-got kubuntu-desktop and nvidia-glx without any problems; ran KDE in all its glory... and edited fstab to tack on an 'rw' (that was my next best idea at the time but it didn't help at all in the long run). 

Now I again cannot do anything because I can't modify a thing.

And all I was trying to find out is if Ubuntu had acquired working power management by now. =P~ 

Sigh. 

Something I'm not getting? No doubt, but what?

---

### Post by abalone on 2006-08-19
Never mind, installation deleted.

Power management not working either though after about a whole day of trial-and-erroring I got standby-to-RAM to mostly work.

Window decorations, desktop background and assorted graphics (e.g. GIFs in Firefox) are broken after resuming. 

I've flipped every true/false in /etc/default/acpi-support and played with acpi_sleep=s3_bios and s3_mode in the GRUB menu but nothing helped.

What does help in a depressingly clumsy kinda way is changing something about KDE's appearance, like a single colour or the button style, and then the background graphic. 

Hm.

Could that be put in a resume script somehow, so I don't have to do it manually every time? There must be a way...

---

