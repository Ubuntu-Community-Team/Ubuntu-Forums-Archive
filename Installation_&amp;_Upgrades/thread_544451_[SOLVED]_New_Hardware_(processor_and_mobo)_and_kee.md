---
title: "[SOLVED] New Hardware (processor and mobo) and keep current ubuntu install?"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by jai_mantravadi on 2007-09-06
I have 2 simple questions.
1) If I install a new motherboard, processor, and graphics card with Ubuntu on its own disk, will I need to re-install Ubuntu? Or is there a way to have Ubuntu auto detect my hardware and reconfigure my desktop manager (actually I'm using Kubuntu, but I imagine the process is the same) for my new hardware?

2) If I re-install Ubuntu without formatting a disk, will it keep my old folders? Specifically I have a /usr/multimedia directory where I store photos, videos and MP3s since that is not a default directory for an Ubuntu (or Kubuntu) install, will it overwrite it if I decide to do a fresh install?

Many thanks!

---

### Post by lcg on 2007-09-06
> **jai_mantravadi said:**
> I have 2 simple questions.
1) If I install a new motherboard, processor, and graphics card with Ubuntu on its own disk, will I need to re-install Ubuntu? Or is there a way to have Ubuntu auto detect my hardware and reconfigure my desktop manager (actually I'm using Kubuntu, but I imagine the process is the same) for my new hardware?

Well, reinstalling after a hardware change is a Windows-thing. Probably all current Linux systems automatically detect your hardware while booting. There is one catch, though: X does not autodetect your graphics card, the driver is configured in the xorg.conf file.
You could either use dpkg-reconfigure to change the settings in your xorg.conf or change the driver manually, which IMO is the quicker way.

Since you don't have to reinstall, I assume this takes care of your second question as well?

HTH,
Lars

---

### Post by jai_mantravadi on 2007-09-07
lcg, Thanks!
That answers both questions (although I am curious about the second question in general)! Thanks! I'm actually going to post a different question about graphics cards in another forum because I'm having lots of trouble with 3-D acceleration on a 4 year old computer (Radeon 9800) tried both proprietary and open-source drivers (which both supposedly support 3-D acceleration). I can't get the proprietary drivers to install (always says the Mesa drivers are loaded), and I get a blank (text-mode) screen when I turn on AIGLX with the open-source driver (which is how I get 3-D acceleration according to the HowTo). 
Thanks for the response.
Jai

---

### Post by lcg on 2007-09-08
> **jai_mantravadi said:**
> lcg, Thanks!
That answers both questions (although I am curious about the second question in general)! Thanks!

Well, let's see if I can answer it then, shall we?

> **jai_mantravadi said:**
> 2) If I re-install Ubuntu without formatting a disk, will it keep my old folders? Specifically I have a /usr/multimedia directory where I store photos, videos and MP3s since that is not a default directory for an Ubuntu (or Kubuntu) install, will it overwrite it if I decide to do a fresh install?

That actually depends. If you made a separate partition and mounted it to /usr/multimedia, you can simply add that partition in the installer again without formatting it and it will be mounted automatically after the installation. In that case everything in /usr/multimedia will be right where you left it.
However, if is just a regular directory on your / partition, the contents will be lost because the installer usually formats the / partition before installing anything on it. (You could instruct the installer to skip formatting of the / partition. That is probably not a very good idea, though, since it might leave bits and pieces of the previous installation on your disk, which you no longer need.)

BTW, /usr/ may not be the best place for a shared multimedia directory. /usr actually stands for **U**nix **S**ystem **R**oot and not for "user". A better place might be a /home/shared/ directory or something similar. If you then put /home on a separate partition as well, all the user's home directories and the shared data will be safe in case you decide to reinstall your system.

HTH,
Lars

---

### Post by jai_mantravadi on 2007-09-26
Thanks! That answers what I'm looking for. I'll change over my multimedia dir to home. Hopefully I've got enough space to repartition. If not, I've got a spare drive I can use to swap things around (although its NTFS). Thanks again!
Jai

---

