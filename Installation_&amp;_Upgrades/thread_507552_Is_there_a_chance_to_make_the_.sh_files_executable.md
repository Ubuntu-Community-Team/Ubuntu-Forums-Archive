---
title: "Is there a chance to make the .sh files executable on a recorded CD?"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2007-07-23
Good day,
I have a problem here. I have made a CD-ROM based repository and it has the .sh files that one has to run to install stuff from there. But when the CD is recorded the files are not executable anymore so I have to copy them to the desktop and execute from there. Is there any chance to be able to execute these files right off the CD/DVD? Thank you in advance!

---

### Post by bernied on 2007-07-23
The question is why are they not executable? This is maybe because of the entry for the device in /etc/fstab, or maybe some ubuntu magic. Have a look in the disk manager, see if there are any options for allowing files on cd to be executable.

---

### Post by PryGuy on 2007-07-23
Well, one will have to manually edit fstab for that. I'm looking for the out of the box solution.

---

### Post by bernied on 2007-07-23
Do you mean you want a cd with scripts that will be executable on a ubuntu system, without the user having to alter any settings?

Sorry, I don't know.

---

