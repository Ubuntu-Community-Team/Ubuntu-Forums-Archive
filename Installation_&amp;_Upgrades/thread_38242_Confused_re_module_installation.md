---
title: "Confused re module installation"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by mingus on 2005-05-30
This one is probably easy for experienced Ubuntu/Debian folks, but I'm still coming up the Linux power curve, and this is my first Debian-based distro.

I am confused about the use of update-modules, modutils, /etc/modutils/ vs /etc/modprobe.d/, and what is the current recommended method to configure modules for boot loading.

Scenario:

Installation on laptop w/Soundblaster Pro audio.  Found ALSA module sb8.  When added to /etc/modules, error at boot module load.  ALSA site showed code to be added to /etc/modules.conf or alt for Debian, any file in /etc/modutils/, and then run update-modules.  Didn't work.  Googling found many refs to update-modules and file modules.conf, but man page says update-modules is an obsolete command.  I had no modules.conf file.  Finally, I guessed apt-get modutils, installed, ran update-modules, that created modules.conf, and then /etc/modules code to load sb8 worked.

So . . . should (why isn't?) modutils be installed?  Update-modules doesn't seem to work without it?  Alternative procedure that I missed?  Replacement for update-modules, since indicated as obsolete?  It seemed update-modules only called files from /etc/modutils; what is function of /etc/modprobe.d/ then?

Thank very much in advance.

--mingus

---

