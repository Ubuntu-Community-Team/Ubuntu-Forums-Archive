---
title: "Hung at Grub command-line after 16.04 installation.  How to fix?"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by csete on 2016-04-22
I just attempted to do a replace installation of 15.10 with 16.04.  This is a Dell XPS 15 machine dual-booting Windows 10.  I chose the option during installation to replace 15.10 with 16.04 and the installation appeared to complete successfully.  When it got to the end however the graphical interface was shut down, the DVD was ejected from the drive and then it hung on the text screen without shutting down.  When starting the computer, I land at the GNU GRUB command-line environment and I'm unsure how to proceed to repair things.  Can anyone point me to the right information to fix this up?

Thanks,
Craig

---

### Post by csete on 2016-04-22
I used Super Grub 2 to get booted into the Ubuntu installation and the "Permanent repair" commands from [https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux) to try to fix this, but I still end up at the Grub command line.

---

### Post by csete on 2016-04-22
I was able to resolve this using the instructions referenced above to get booted into Ubuntu and then using boot-repair to actually fix the problem.  Booting from Super Grub 2 on CD didn't work because it was then in legacy boot mode.  The instructions for setting Grub up correctly in the link above didn't work either.  

I seem to remember this happening to me previously.  I'm not sure why the installer doesn't like my hardware, but hopefully if others hit this problem they will be able use this information to help themselves.

---

