---
title: "Multi Booting?"
date: 2004-12-06
forum: Installation &amp; Upgrades
---

### Post by Wok on 2004-12-06
I'm liking what I see when I boot the Ubuntu 4.10 CD so I'm going to do a clean install. I'm thinking of installing a small Windows 98 partition as well as SimplyMepis (not ready yet to give up KDE access). Is Ubuntu likely to handle a triple boot like this? Any reason to install Mepis before or after Ubuntu?

Also, would it work to have a shared Home directory for both Linux partitions?

---

### Post by JonAtkinson on 2004-12-06
You could have a shared home directory quite easily if you create a separate partition for /home. 

For example, if you used:

hda1: Windows (Windows always likes to be at the start of the drive)
hda2: Home Dir
hda3: Ubuntu
hda4: Mepis

Then you could access your home directory in Ubuntu and Mepis. You could even format your home partition as vfat and access it in Windows (though I wouldn't want to think about how FAT deals with unix permissions and such...)

Hope this helps.

--Jon

---

### Post by Wok on 2004-12-06
Thanks, Jon. I'll skip trying to involve Windows in my home dir.

So do you think the multi-booting will just work without a lot of fiddling, or is it likely to be more trouble than it's worth? I suspect I'll almost never open Windows and could get along without it if necessary.

---

### Post by JonAtkinson on 2004-12-06
As far as I know, the GRUB bootloader can deal with lots of very exotic configuration - you might need to google around a little, but what you're asking is far from impossible :-)

--Jon

---

### Post by alainhenry on 2004-12-07
Multi booting is fairly easy to set up, and the installation will recognise the variosuinstalled program.  I found the Ubuntu recognised the three other OS I had on my machine (Windows, Mandrake 9.2 and Mandrake 10.1).  I hsould thus be straightforward., once the partition are OK.  

I would however advise to have a different home partition for each linux distribution, as a number of system parameters (such as gnome session, etc.) are stored in the home directory, and there are lots of possible conflicts between two distros.  

You can still access the different home partitions from every distros if you mount them manually or in /etc/fstab for example.  

Alain

---

