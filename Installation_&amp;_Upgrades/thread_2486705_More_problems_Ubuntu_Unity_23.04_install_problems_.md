---
title: "More problems Ubuntu Unity 23.04 install problems on hp EliteDesk 800 g1 UEFY MOX"
date: 2023-05-08
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2023-05-08
I will be the first to admit, I don't know what I am doing with UEFI and MOX.  System will boot both Ubuntu 23.04 and Win 10 64.  Ubuntu still gives something like "can't evaluate_CRS:12311.

nVidia website says correct video driver is nvidia 390.  However, when I try to install it from the command line, I get questions about UEFI and MOX.  If I try to install driver from synaptic, I get a pk-client-error-quark and something about cannot get a lock because of synaptic.  I would post full error message, but Ubuntu fill not allow me to copy error message.  Perhaps it is in some log file.

John

---

### Post by watchpocket on 2023-05-08
I get my nvidia drivers from the "Graphics Drivers Team" Luanchpad.net PPA:

[http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu)

since they test the drivers for Ubuntu.  It's a safer way to go.  (Apologies if you're already doing that.)

---

### Post by cigtoxdoc on 2023-05-08
Thank you, but my REAL PROBLEM is understanding what are the correct settings for UEFI and MOK.  When I tried installing the nVidia 390 driver, I got a window dealing with MOX.  When I exited out of MOK because I did not know what to do, then a window came up dealing with UEFI.

I think I have a similar with two other PCs that work with 23.04, but do not show the typical GRUB screen at boot.  I have to go into manufacturer's startup screen if I want top boot into Win 11 (yes, some of my clients want their work done in MS Office and Adobe Acrobat).

John

---

### Post by ubfan1 on 2023-05-08
Your 2014 HP is fully UEFI/Secure boot capable.  Nvidia drivers are not signed by Microsoft or Canonical, so the usual way to install them is to turn off secure boot.  You should still be in UEFI mode, so Windows will require a GPT partitioned disk.  You could have always generated your own key (Machine Owner's Key MOK) and signed the Nvidia modules, but that was hardly worth the effort for what you'd gain.  Lately, the generation/signing has been automated, so installing Nvidia should be a matter of accepting the key and installing it.  Then, secure boot enabled or not, things should just work.  I think I did the install on a new machine with secure boot off, installed the key, and forgot about it -- surprised one day to find I was running  with secure boot ON, (Windows must have turned it on).  I was never asked for a key or password in the whole process.

---

### Post by cigtoxdoc on 2023-05-08
Thank you very much, ubfan1.  HDD is already GPT, and Win 10 sysinfo says BIOS mode is UEFI.  Looks like one mistake I made was exiting out of MOK.  PC in question is a back-up for one of my two production PC's, so it has to be ready, if needed (data on separate secure storage).  John

---

### Post by cigtoxdoc on 2023-06-29
Since I made my original post, this problem for some unknown reason solved itself.  How did I find out?  I got distracted, and the boot menu started Ubuntu before I could arrow down to the Windows boot manager.

John

---

