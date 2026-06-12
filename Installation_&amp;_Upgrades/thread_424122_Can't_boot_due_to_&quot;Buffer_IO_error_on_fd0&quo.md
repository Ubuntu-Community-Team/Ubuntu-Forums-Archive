---
title: "Can't boot due to &quot;Buffer I/O error on fd0&quot;"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by distortedstar on 2007-04-26
I can't boot from the live cd. It just goes to the splash and then ends up with "buffer i/o error fd0.

If i understand correctly, this is my floppy drive. I don't have a floppy drive installed on my dell inspiron 8200. I have an extra battery in the bay. BIOS reports floppy as uninstalled. 

I've tried downloading the iso again and re-buring several times, just in case it was corrupt DL or burn. MD5 sum matches.

Kinda dissapointing, since I've never had any issues booting from any live cd from any distro.

---

### Post by psusi on 2007-04-26
Wow, that is.... really weird...

Which splash screen are you referring to?  The one that comes up after you choose to boot from the menu?  If so, try editing the command line and change splash to nosplash so it doesn't load the splash screen.

---

### Post by distortedstar on 2007-04-26
Yes, I'm refering the screen with the Ubuntu logo and status bar. I did a CTR ALT F1 and got "Loading...Please Wiat" and then after a while the buffer I/O error. I wonder if I should try to start with acpi off. Do you know how to do that?

---

### Post by distortedstar on 2007-04-27
Found out it's a known bug with dell laptop combo drives. 

Launchpad Entry:
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306)

I had to download the alternate install cd and install that way. Never did get the live-cd to work, but at least I'm running Xubuntu Feisty!

---

