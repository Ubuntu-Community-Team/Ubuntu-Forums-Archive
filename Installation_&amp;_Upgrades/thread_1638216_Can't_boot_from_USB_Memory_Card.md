---
title: "Can't boot from USB? Memory Card?"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by Huzudra on 2010-12-05
I have an ancient Sony Viao PCG Z505R here that I'm trying to get to boot from anything other than the internal HDD. I have nothing but the notebook, a bum battery, and power brick. In BIOS there is...HDD, floppy, CDROM. the machine is lacking 2 of the 3, only having a 2.5 IDE drive. 

Is my ONLY option to install some kind of linux onto a CF card, then use a 2.5 IDE to CF adapter to boot from?  I'd rather see how some forms of linux handle on this thing before sinking money into it. Some dipwad has installed XP Pro...thing has 64MB Ram, 6.4GB HDD, 366 PII.  30 minutes after flicking the power switch we have a desktop.

How about Wubi?

---

### Post by davidmohammed on 2010-12-05
with 64MB of RAM, you'll never get ubuntu to install on it - you need a min of 512MB/1GB of RAM.  You'll need to try something like puppy-linux for such an ancient machine.

---

### Post by Huzudra on 2010-12-05
> **davidmohammed said:**
> with 64MB of RAM, you'll never get ubuntu to install on it - you need a min of 512MB/1GB of RAM.  You'll need to try something like puppy-linux for such an ancient machine.

yes, I was planning on using puppy linux actually, ubuntu isn't really the question here, its how to get something onto this machine. thankyou though, i'll toss in another 128mb ram when/if i can get any kind of linux going on it to see how she handles.

---

### Post by davidmohammed on 2010-12-05
...

actually you could just try installing the hard-drive into another laptop and install puppy linux onto it.  Once done, transfer back into the ancient laptop.

I've done this a few times, sometimes it works, sometimes not.  Usually you can then just go into recovery mode and correct any-stuff that doesnt work.

Alternatively - does the laptop offer PXE booting?  if it does, you could PXE install whatever linux distro you intend to use.

---

### Post by Huzudra on 2010-12-05
> **davidmohammed said:**
> ...

actually you could just try installing the hard-drive into another laptop and install puppy linux onto it.  Once done, transfer back into the ancient laptop.

I've done this a few times, sometimes it works, sometimes not.  Usually you can then just go into recovery mode and correct any-stuff that doesnt work.

Alternatively - does the laptop offer PXE booting?  if it does, you could PXE install whatever linux distro you intend to use.

Don't have another laptop or ide adapter handy right now, whats PXE? this thing has 3 options which are Hard drive, removeable disk (floppy) and CDROM. It lacks either of the last two.

---

### Post by Huzudra on 2010-12-06
Ok, finally got through a wubi install of Xubuntu by turning off the memory and space checks, its booting right now slowly....or its hung. it did complain something about acpi apci or someting and is now spitting a bunch of jibba jabba about ata200 (didn't catch the exact messages) and now I'm at terminal. So...kinda win but still fail.

do they make a wubi for Puppy? :p

Ok, it was ata2.00 error unc abort and ata2.00 error something else. I'll try with some different installer options.

trying live-cd mode from wubi installer boot....

---

### Post by Huzudra on 2010-12-16
Could I install GRUB from within windows and then could GRUB let me point at a live-usb to boot from and then from the live-usb install whatever I'd like?

---

### Post by sgosnell on 2010-12-16
No CD drive, no USB, no floppy, and you want to install a modern OS?  You need a newer computer.  What you have would make a half-way decent doorstop, not much more.  If you can't boot from USB or have no optical drive, and can't put the HDD in another computer, you're SOL.

---

### Post by Huzudra on 2010-12-17
> **sgosnell said:**
> No CD drive, no USB, no floppy, and you want to install a modern OS?  You need a newer computer.  What you have would make a half-way decent doorstop, not much more.  If you can't boot from USB or have no optical drive, and can't put the HDD in another computer, you're SOL.

Thanks for the encouraging words there buddy, that's a n extremely helpful comment. I'm trying to get puppy linux on there, this machine meets its requirements. 

How about you come here so I can give you a thwack with my doorstop. Help or leave please.

---

