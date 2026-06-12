---
title: "Installed but won't run"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by gryzld1 on 2007-12-23
Hello,
I am trying to install Ubuntu on an old PIII Hewlett Packard. The disk is from the Oregon StRUT program and given to me about 2 months ago and is supposed to be a recent version. The install was successful according to the final screen. I am fairly confident the disk is valid as it was used to install this Unbuntu OS on a number of the computers at the StRUT warehouse. I do not have the "flavor" information as it is not written on the disk and I can't open anything to get to  properties info. I tried to perform a clean install and all appeared to go well...right up to the end when the system was configuring all the drivers, etc. on the opening screen. All the systems were deemed OK, monitor and such apparently working and then...nothing but a line (short one, like a letter entry prompt) at the top of an otherwise dark screen once all the boot things were logged through the system. No input from the keyboard or mouse will show up. No activity on the hard drive is registering (neither light nor sound) after this startup routine. 

Is it possible that using the floppy startup disk for windows 98 (don't laugh) could have caused a conflict? Will this system be able to boot from the disk (CD) directly and if so should I try the installation again?

And lastly...does anyone know which key to press to get into the bios configuration screens on this old HP? F2, F3? Delete is not the one and I just don't remember which key. 
 
I have done a fair number of system builds, Operating system installations, clean installs and so on, and am reasonably comfortable doing most computer work. 

Thank you in advance,
The Grizzled One

---

### Post by Craigus on 2007-12-23
> which key to press to get into the bios configuration screens on this old HP?

Probably F1.

> Will this system be able to boot from the disk (CD) directly and if so should I try the installation again?

It should, and that would be a reasonable thing to try. I'd actually run the memory test and CD tests first to make sure all is OK.

---

### Post by PmDematagoda on 2007-12-23
What VGA card do you have? Also when you boot the PC do you see a list such as:-
```

Ubuntu 7.10
Ubuntu 7.10 Recovery Mode
Memory Test
```

---

### Post by gryzld1 on 2007-12-23
The VGA card is an unknown. I inherited this machine. Before the clean install everything worked well. I just want to learn how to used Linux on this one before converting my other machines so  your help is appreciated. Part of the problem is that the boot sequence is all I get and then can do nothing but shutdown via the power button...hence I don't see anything but the blank screen with an entry prompt line (about .5 cm long). 
grz

---

### Post by gryzld1 on 2007-12-23
craigus...thanks for the reply. I think the lines you reference are part of the installation...right at the beginning? So this would be a check to make on a second install attempt, right?
thanks,
grz

---

### Post by nzadLithium on 2007-12-23
you dont need to install again.

i think you probably wiped everything off the pc? so it will automatically boot normal ubuntu because there are no alternative OS.

what craigus is talking about is just after your system starts booting your disk. You should get a countdown timer counting down from 3 seconds. press whatever the key reported there is. you should now get that list craigus said. They are alternative boot options for ubuntu when something goes wrong you can use them to get a terminal.

---

