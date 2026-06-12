---
title: "Toshiba M35X-S149 install/LiveCD failure"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by Resurrection on 2008-01-21
Ok, checked the similiar threads with no duplication of my problem found.

I am a successful Ubuntu user since 5.04 on my desktop.  I have an old Toshiba M35X-S149 laptop which I have decided to add on Ubuntu as well.  But I can't even get into an actual desktop environment using the current 7.10 LiveCD.  Machine boots from the CD just fine.  CD is in good shape as it is freshly burned, I verified the disc using its built-in checker on my desktop, and the CD will boot perfectly on my desktop without any hangs or snags.  Even recognizes my wireless trackball mouse on that machine (Kudos to the developers on that one!).  

However, when trying to boot into the live environment on the laptop, it just seems to hang at the light-tan screen prior to launching the Gnome Desktop. I get about 3/4 of the screen being a light blue color and the right 1/4 of the screen is that light tan.  It seems to recognize most of the hardware without any problems as even the touchpad on the laptop works at this point.  In the CLI portion prior to the Gnome boot, it gives a notice about not supporting the ACPI of the laptop, but that shouldn't be an issue since it is plugged in to a wall outlet.

Finally, I don't want to just flat out try an install, as I would prefer to dual boot this machine.  I guess I could wipe out everything and use the alternate install CD, but I would prefer not to do that if necessary.    Anyone have any answers on this?  I would prefer to try the LiveCD environment first, just to see how it works with that specific hardware.  Any possibility of booting it from an external drive instead?  Is this a better solution to dual booting in this case?

---

### Post by pollywog on 2008-01-22
Hey I know that it's a long shot, but I had a similar issue on my SR1830nx compaq. Gutsy live cd  would hang about 3/4 of the way through booting. Tried it several times, same result. I shuffled thru all of my live cd's, and the only Ubuntu version that would boot was Kubuntu 6.10- nothing later, or gnome. Ultimately I found a BIOs update, installed it, and bam! The live cd boots. Is this your problem? Probably not, but just thought I'd throw that out there.

---

### Post by Resurrection on 2008-01-22
Thanks for the reply, I will check to see if a Bios update is availible and try that.  Thanks.

---

### Post by Resurrection on 2008-01-23
Well, updated the Bios, to no avail.  Bios updated fine, but 7.10 still just goes to a tan screen and then just runs and runs and runs, with no error messages or notices of any kind, but I let it run for an hour before giving up on it.  The laptop has a 1.5 Celeron in it with 512 Ram, so while not great, it should run Ubuntu or at least boot the LiveCD within a reasonable amount of time.

Any other ideas, or should I just give up hope on this machine?

---

### Post by Resurrection on 2008-03-27
Bumping my own very old thread, I managed to get Ubuntu running on this laptop.  I had to use the alternate install CD after the windows install decided to corrupt itself and not work anymore.  Works great, touchpad and wifi work right with no tweaking.  Power management support seems to work pretty well.  I am very pleased with Gutsy.  Installing went fine with no issues, I was very pleased with it.  

This can probably be marked as solved, at least for Ubuntu 7.10, I just wanted to note it in case someone else tries it in the future or with a similar Toshiba model.

---

