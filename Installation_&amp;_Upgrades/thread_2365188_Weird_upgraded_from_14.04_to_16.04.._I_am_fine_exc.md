---
title: "Weird upgraded from 14.04 to 16.04.. I am fine except a boot problem"
date: 2017-07-03
forum: Installation &amp; Upgrades
---

### Post by nariub on 2017-07-03
So made sure i had the latest updates and was all cool
then did "do-release-upgrade" let it download and install.. took a while..
then it said all done.. didnt see any errors but then i barely babysat it either..
rebooted when it said to.

I have an encrypted disk.
I see the prompt screen for the passphrase.
only the text i type is white on black on the upper left side of the screen instead of stars in the password box.
hitting enter does nothing.. just sits and looks at me  until i reboot into advanced recovery mode
that prompts me for the HD passphrase
I can then resume the boot.. and i have a perfectly functioning desktop until i go to reboot and i get the fake passphrase screen and have to go back to advanced options to get into the desktop..

What gives?
I reinstalled grub
i reconfigured grub
no love man, no love..

Seems to be a plymouth thing
it wont prompt for the encrypted passphrase when splash is set in grub..
so i edited /var/default/grub to say "quiet"
and at least i get prompted and can boot cleanly without recovery mode..
Still wondering whats up with the splash..

---

### Post by nariub on 2017-07-04
Seems to be a splash screen issue with Plymouth.  The progress dots do not blink either.  
Would say it was frozen except that my keyboard input is actually echoed on the top left of the screen.
Dinked around with NVIDIA drivers.  no love
Workaround is to skip the splash for now..

Anyone have a suggestion as to what is causing my splash screen to not prompt me correctly for a passphrase?

---

### Post by raynskitty on 2017-07-04
This same thing happened to me, i found the easy way is to reinstall your OS to 16.04..

---

### Post by nariub on 2017-07-04
Tried installing hwinfo per this thread.. it changed the result in that my keyboard doesnt echo on the top left anymore.
[https://ubuntuforums.org/showthread.php?t=2227035](https://ubuntuforums.org/showthread.php?t=2227035)

---

