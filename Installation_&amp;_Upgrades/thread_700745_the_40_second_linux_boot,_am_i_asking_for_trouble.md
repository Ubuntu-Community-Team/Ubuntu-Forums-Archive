---
title: "the 40 second linux boot, am i asking for trouble?"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by Hoaxe on 2008-02-18
alright so i bumped into this neet little article 
[http://linuxgazette.net/147/franci.html](http://linuxgazette.net/147/franci.html)
(there's a youtube video as well) of this dude booting his laptop with some kind of weird hibernation ram write/recall type of thing. My lappy, as all lappies, has a hibernation state, but it doesn't actually turn the computer off.

His "hibernation" starts with his laptop off, when he boots up the memory is called like a state from a separate partition on the drive.

I'm not in the habit of playing with my lappy like this - i use my desktop to indulge in those pleasures. my laptop is my little super portable baby i use to convince others of linux's awesomeness. 

So i'm wondering has anyone tried this with ubuntu? what about a dual boot? should I expect problems? what's your experience been like is what i'm wondering.

thanks.

---

### Post by miriad on 2008-02-18
This sounds like a true hibernation sleep state.

In hibernation, RAM contents are written to your hard drive (Swap space usually), then system power is turned off.

you "hibernation" state seems to be a sleep state, where the computer is put into a low power mode with the CPU and most devices off, just with power to the RAM to hold their contents.

the change between the 2 may be as small as a setting in ubuntu, or possibly a BIOS setting.

Its also possible that your BIOS ACPI doesnt support hibernation (Which is VERY rare with anything new enough to have ACPI.)

---

