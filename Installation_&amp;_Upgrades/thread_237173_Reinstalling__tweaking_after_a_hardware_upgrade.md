---
title: "Reinstalling / tweaking after a hardware upgrade"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by Solver on 2006-08-15
I just upgraded most of my PC. Windows not being adaptive to such changes, I reformatted its partition and reinstalled. Then booted from a 6.06 Live CD, got GRUB back into place and booted into my Ubuntu installation.

It seems that the OS recognized most hardware changes fairly well, but it didn't figure out the CPU. My new one is a Pentium D, but Ubuntu only sees one CPU. I searched the forums, and apparently installing a different kernel can help get the second CPU core recognized, but Pentium D can also run 64 bit programs.

So, I think I should try installing the AMD64 version. Is that a stupid thing to do for some particular reason? Checking the 64-bit forum, itseems there are only problems with a few software packages.

To upgrade to 64-bit, can I do something like a dist-upgrade, or do I need to download the 64 bit ISO and do a reinstall? If I do a reinstall, is it an acceptable idea to tar my home folder, and then untar it on the new system, to bring my configuration back? Will it indeed bring my config back, or create trouble for the system? I know backing configs up in Windows is a nightmare, but I've heard that doing this with the home dir in Linux is a possible solution.

---

