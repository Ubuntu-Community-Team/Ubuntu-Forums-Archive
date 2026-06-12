---
title: "Error at &quot;Select and Install Software&quot; (6%)"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by rljacobson on 2007-06-17
I am trying to install Feisty Fawn on a (formatted) machine that formerly ran Breezy. Installation precedes normally until the stage labeled "Select and Install Software", at which point the progress bar spends a little bit at 6%, then I get a red error screen telling me something to the effect of "An installation step has failed. Select it again from the menu to try again, or choose a different step."

I have tested the installation media, and it passed the test. How do I proceed?

---

### Post by ajgreeny on 2007-06-17
Which install CD are you using, the alternate install?  If the desktop live CD you don't get to chose the software you install, it is all done as a default.  Perhaps you have a DVD from somewhere.

Definitely worth checking that the CD/DVD is OK before trying anything else and also that the md5sum of the download is OK as well.  You can find the md5sum of all the files available for downloading here:-
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by rljacobson on 2007-06-18
Thank you for your reply. I have solved my own problem. According to [this thread]("http://ubuntuforums.org/showthread.php?t=289472"), the problem is not uncommon and appears to be a bug in the installer. In case someone else has a similar issue, here is a workaround that seems to work:

Since the error occurs *after* the "install base system" step, we can finish the installation to make the machine bootable. Here's how.
1) At the big red error screen, select continue. You will be presented with a menu of installation steps.
2) Complete the menu items labeled "install Grub bootloader" and
3) "finish installation".
4) Your machine is now bootable. Reboot, login, and become root with "sudo su".
5) After possibly mounting your cdrom drive, run "apt-get install ubuntu-desktop".

The ubuntu-desktop package allegedly installs the packages skipped by the "select and install software" step.

---

