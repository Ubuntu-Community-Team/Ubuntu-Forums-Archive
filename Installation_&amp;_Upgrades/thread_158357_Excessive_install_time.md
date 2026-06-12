---
title: "Excessive install time?"
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by Surtac on 2006-04-11
I was convinced to try Ubuntu 5.10 as an OS for an old machine I have available.  It's a 1GHz AMD Duron with 512MB RAM and a 10GB hard disk.

I ran the LiveCD version on a newer machine and liked the look of it, so started the full install on the older machine described above.

It has now been running for over 24 hours.  Is this excessive?  How long should it take?

---

### Post by Darkriser on 2006-04-11
while install is in progress, press alt+f4 - this is a debug window where you can see details about your installation. isn't any error there?

btw. 24 hours??? god, i installed ubuntu on my laptop (300MHz and 168MB RAM :mrgreen: ) in less than an hour.

---

### Post by Sef on 2006-04-11
> t has now been running for over 24 hours. Is this excessive? 

Yes.

> How long should it take?

It should be total about an hour if you have broadband.

Solution: I would use or burn another disk.  It sounds like yours is bad and stuck somewhere.

---

### Post by Surtac on 2006-04-11
Thanks for the responses people.

I killed that install and moved the hard disk to the newer machine I'd run the LiveCD version on and attempted the install again (I'm using removable hard disk caddies, so no great drama there).

It completed in about 45 minutes with no obvious glitches and runs fine on that machine.  Unfortunately, that's not where i want it to run. :)  And of course it won't boot if I move back to the older box.

I'm suspecting it's something to do with motherboard settings or the cdrom on the older machine. Cdrom i/o seems to be very slow (lots of stop-start activity with long delays in between) but it's a 40x cdrom - it should be ok.  The newer machine has a 52x cdrom/dvd combo, and that device didn't suffer from the stop/starts and delays during the install.

The motherboard in the older box is a Gigabyte 7ZXE.

Any suggestions as to where i should start looking next?

---

### Post by Surtac on 2006-04-13
I've tried resetting the BIOS to 'failsafe' defaults and reinstalling, but it behaves the same.

It seems to go ok up until the step where it is scanning the cdrom.  Scanning \cdrom\pool\main\a, \cdrom\pool\main\b and so on, it seems to take about 20 minutes per selection. 

I'm wondering whether it's a problem with the cdrom driver somehow.  I have actually tried this install with two different cdrom drives now - same results.

Next thing I'll try is to flash the BIOS to a later level ...

Any other suggestions from my much more learned colleagues hereabouts?

---

### Post by Sef on 2006-04-13
Have you checked the cables and leads to the cd -rom/rw to make sure that there are no problems there?

---

### Post by Surtac on 2006-04-13
Thanks - I thought of that this morning and have replaced the cdrom with a cdrom/dvd combo and checked the cables.  Alas, the same result/behaviour.

I've just tried again with the boot parameter acpi=off, and it's doing exactly the same thing.

And I've still got the motherboard bios set to 'failsafe' defaults.

I might have to try flashing the m/b bios to a later level (it's currently F4), but it's not a procedure I've tried before, so am a little loathe to go down that path.

Any other suggestions out there?

:confused:

---

### Post by Sef on 2006-04-13
I suspect it is the motherboard.  What kind do you have?

---

### Post by Surtac on 2006-04-13
The motherboard?

It's a Gigabyte 7ZXE, some 4 or 5 years old - it just predates Windows XP iirc, and as it happens I was never able to get XP to install onto it either, but it ran 98SE quite happily.

Anyway, I shall try flashing a later BIOS version.

---

### Post by Surtac on 2006-04-15
Success!

I flashed the motherboard BIOS to a later version (F8 from F4), and tried again to install Breezy.

This time it went straight on with no problems and no long waits from the cdrom combo drive.

Happy, happy, happy!

---

