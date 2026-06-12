---
title: "Low graphics mode"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by The Recorder on 2010-04-21
Can anyone tell me how to install Lucid using "Low Graphics Mode"?  Yes, this sounds odd, but if I try to install in regular graphics mode, I have problems with reading my SATA drives.

---

### Post by dino99 on 2010-04-21
where is the relation between graphic resolution and sata drives ?

---

### Post by The Recorder on 2010-04-21
> **dino99 said:**
> where is the relation between graphic resolution and sata drives ?

This is a long and complicated story - I guess that if I knew the actual answer, I might be able to solve a problem that I've had since I got my machine some years back.  My machine is an Intel dual core, 3 gig, with an X700 ATI card, and 1 gig of DRAM2 memory.  I have one IDE ATA drive, and two SATA drives.  Everything is fine when I use my ATA drive (Ubuntu is installed and runs great from there.)  However, accessing my SATA drives from there is a long, slow, and tedious process.  This is the same situation if I use Windows XP.  However, when I had Windows XP installed on one of the SATA drives, it worked fine as long as I didn't use any graphics acceleration.  It had installed OK because Windows XP installs in VGA mode.  I've spent scores of hours researching iastor (AHCI) and atapi (IDE) errors ("drive did not respond in time"), and there are lots of people who had/have this problem, but I have never found anyone who actually knows what the problem is.  Anyway, Lucid tries to install, but after about two hours of slow "movement" a disk error kills it all.  So, I want to try to install in "low graphics mode".

---

### Post by wnelson on 2010-04-21
Post a copy of you dmesg output.

---

### Post by kansasnoob on 2010-04-21
OK, first are you aware of this:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)

> Boot options hidden by default on Desktop and Netbook CDs

The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is noninteractive by default. To configure advanced boot options, press any key at the first boot screen. 

But the boot options have changed also. Let me boot a Live CD and review that quickly. I'll be back.

---

### Post by The Recorder on 2010-04-21
> **kansasnoob said:**
> OK, first are you aware of this:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)



But the boot options have changed also. Let me boot a Live CD and review that quickly. I'll be back.

I have tried a few options, but with no luck.  I'm not sure what to put in the path bar...  Will wait for your next posting.

---

### Post by kansasnoob on 2010-04-21
Well, I know they've removed the Safe Graphics Mode from F4. F6 now includes:

acpi=off
noapic
nolapic
edd=on
nodmraid
nomodeset
free software only

It's my understanding that "nomodeset" is supposed to have replaced "Safe Graphics Mode".

I wonder if this would be useful to you:

[http://tldp.org/HOWTO/BootPrompt-HOWTO.html](http://tldp.org/HOWTO/BootPrompt-HOWTO.html)

---

### Post by dino99 on 2010-04-21
One of my configs (oldish) have 2 ide & 1 sata, and i've had to find the right order to plug them on the board: sata like first main on the MB and into bios and set as ahci, all other alternative dont boot.
This story start with Jaunty and have updated my bios too, i suppose that Jmicron's mainboard dont deal well with a fake raid, so some kind of specific motherboard problem.

This main hdd have karmic & lucid on it and grub2 for all the distro
The second hdd is with xp and the third have jaunty.

Is your psu strong enough ? what happen if you try with only one hdd ? Is x700 well identified ?
Have you try radeon.modeset=0 or pci=nomsi as boot parameter ? Are you using fglrx or else ?

---

### Post by wnelson on 2010-04-21
The current Linux Kernel Parameters

[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by The Recorder on 2010-04-21
> **kansasnoob said:**
> Well, I know they've removed the Safe Graphics Mode from F4. F6 now includes:

acpi=off
noapic
nolapic
edd=on
nodmraid
nomodeset
free software only

It's my understanding that "nomodeset" is supposed to have replaced "Safe Graphics Mode".

I wonder if this would be useful to you:

[http://tldp.org/HOWTO/BootPrompt-HOWTO.html](http://tldp.org/HOWTO/BootPrompt-HOWTO.html)

"nomodeset" worked!!!  Installed in 20 minutes.  After I rebooted into the system, I had to uninstall the xserver-xorg-video-radeon and xserver-xorg-video-ati packages to stop the graphics acceleration.  I can't use a second monitor with "fbdev" as my graphics driver, and I'd like to find a way to have some different resolutions other than the default 1280x1024, but I'm very happy.  I've created an xorg.conf file - Guess that I'll have to mess around with that for a while.

Thanks to you and the others for your input.  This is a great place, and sometimes it's a tremendous place.

---

