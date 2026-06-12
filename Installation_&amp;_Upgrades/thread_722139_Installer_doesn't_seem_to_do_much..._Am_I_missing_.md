---
title: "Installer doesn't seem to do much... Am I missing something?!"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by DarkStar782 on 2008-03-12
Trying to install Gutsy x64 on a Laptop - Dell XPS M1730.

Specs:
Core 2 T7700
8700m GT SLI
2*2GB DDR2-800


Booting from the disk, I can try a normal install (which then complains it has to run in low graphics mode) or a safe mode graphics install...

If I do the safe mode install, or click continue to the low graphics prompt, it whirrs about at the CD for a few minutes, then gets to a point where it seems to be going through a checklist with items such as "* Starting Bluetooth Services  [ OK ]", and a load of other things all with OK next to them... then it just sits there dead....

I can type stuff at this point but it doesn't seem to respond to any commands...

What am I missing?!

---

### Post by wblancqu on 2008-03-12
Have the same "Starting Bluetooth Services" problem. Installation went fine for me by using the alternate cd installation. Then boot system in safe mode, and edit file /etc/init.d/bluetooth, and put "exit 0" at the begin of it. Bluetooth will be disabled but at least your system will boot (hopefuly). Wait for a kernel patch for this bluetooth issue is the best thing you can do I think.

Grtz

---

### Post by DarkStar782 on 2008-03-12
But it did say "OK" to bluetooth, that was just one thing in a list far too long to type... there was no error message...

I have disabled firewire, the expresscard slot, bluetooth, the internal cellular modem, the NIC in the BIOS to no avail.... will try burning off the alternate CD

---

