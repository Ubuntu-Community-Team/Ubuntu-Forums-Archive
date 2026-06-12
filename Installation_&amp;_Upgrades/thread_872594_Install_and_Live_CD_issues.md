---
title: "Install and Live CD issues"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by cedarhaywork on 2008-07-28
Have tried as many of the options suggested in numerous threads as I could find but no joy, so any suggestions more than welcomed.

Trying to install onto an old(ish) box, each attempt has different issues. The box itself should be powerful enough even tho spec is quite low (512 memory, 40Gb hdd. No dual boot)

Live CD boot, get the initramfs/busybox dialogues. Various different messages depending on which of the kernel parms I try
(*all_generic_ide floppy=off irqpoll pci=nomsi noapic noloapic* in various combinations)

On a couple of occasions I have managed to get the Live cd booted all the way. Once I even managed to install - but it wouldn't then reboot :(

Have tried the alternate cd ... booted off cd and went through a few of the screens but then hardware scan couldn't find the cd

I will try 7.10 tonight, but I expect that to fail (I should note that fedora 9 also has similary issues, although w95, w98, xp all install ok)

Primary master ide, 40Gb
Primary slave - empty
Secondary master - zip drive
Secondary slave - cd/dvd rom

Is there any mileage in swapping round ide connections ? Any other thoughts ? Thanks

---

### Post by railpostau on 2008-07-28
I am no great shakes at this but have you tried PUPPY linux live cd use GPARTED to create a Linux Swap partion on the hard drive.. Have found that this can help take the pressure off the RAM and allow things to load..

You could format the remaining partition to ext 3 giving less work for the RAM..

Other suggestion have you tried XUBUNTU seems to need less resources..

Just some suggestions..

---

### Post by falcon61102 on 2008-07-28
The zip drive may be throwing your install off, unless there is a reason, try switching or just removing your zip drive until after the install.

---

### Post by Partyboi2 on 2008-07-28
You could try ide=nodma as a boot option with the alternate cd.

---

### Post by cedarhaywork on 2008-07-31
Oh well. Tried even more options, disconnected zip etc etc but still no good :(
opensuse (some old version) installed ok
Maybe I will try xubuntu

---

### Post by LTsky on 2008-07-31
I actually have a similar problem with my computer. If I try to put a Live CD into my DVD drive, it does exactly the same thing as you describe.

Not sure if there's a fix though: you may want to try the install with a Live DVD

---

