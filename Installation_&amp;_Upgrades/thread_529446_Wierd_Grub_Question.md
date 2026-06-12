---
title: "Wierd Grub Question"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by imperial_oz on 2007-08-19
Scenario,

I want to run multiple O.S.s on a single PC for testing purposes.

I want to run Ubuntu, Kubuntu and Red Hat Fedora Core & as well as XP.

Can anybody help me to configure Grub to allow each partition to boot itself. I will allow a single distro to install Grub to the root of the 1st hard disk.

If I am doing this wrong way, Im happy to hear it as long as someone can suggest the best way to run all four O.S.s on this beast.

I have no probs with disk space - 2 x 320 Gb SATA drives, but Grub is giving me grief. I was planning on making each partition self bootable and using something like Boot Magic as my main bootloader but boot magic doesnt seem to like this machine, so I thought that one distro can write to the mbr. Grub seems to only want to install on one partition though...or I could be reading the symptoms all wrong.

Any ideas?

---

### Post by raja on 2007-08-19
Do you really want to install Ubuntu  and Kubuntu separately ? I know it is cleaner that way, but all that is different is the DE.
You will have to install windows of course. Then install Ubuntu with grub on mbr - you should now have windows and ubuntu listed. Now install the rest one by one and put grub in the partition itself - then just add the entries to mbr by hand. Or you could install Ubuntu last and see how much is auto -detected. I currently triple boot between xp, ubuntu and arch, so added the arch entry by hand.

---

### Post by imperial_oz on 2007-08-19
how did you install entries by hand?

I've had a look at this but didnt quite get. I was able to do LILO stuff by hand...but that was some time back now.

Thanks

---

### Post by raja on 2007-08-19
Well, easiest is to install grub locally each time and then copy the entry to the main boot menu.

---

### Post by imperial_oz on 2007-08-19
I have actually been trying to do just that but somehow Feisty installer seems to have problems with that.

I'm probably doing something wrong here but installing Grub locally seems to be a bit and miss. Especially after doing it locally once, it doesnt seem to like doing a second time. It kept referring to the original install.

I will have revisit this a bit more and see what Im doing wrong.

---

