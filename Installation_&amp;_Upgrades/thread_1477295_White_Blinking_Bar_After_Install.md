---
title: "White Blinking Bar After Install"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by MilesLong on 2010-05-08
Maybe I'm doing something wrong. I don't doubt it, I have used Linux Distro's in the past (Like some old school Mandrake and Redhat) But the LiveCD on the Kubuntu disk does not work. It freezes about 4 minutes into the startup, then when I install, I have to use the Alternative Disk to get it to install. Once it installs I get a single white line in the top left hand corner of the screen. That's it. 

Motherboard: Gigabyte P35-DS3L (Original) 
CPU: Intel Dual Core E2180 2.0GHz
RAM: 4GB of PC26400 GSkill
Display: NVIDIA GeForce 7600GT

If I'm doing something wrong, or something is obviously an issue, please let me know, I'm looking to replace my desktop and I'd love to use this Distro. Thanks for the help in advance. I've heard wonderful things about this forum and how nice the people are here. 

Miles

---

### Post by Zorael on 2010-05-08
As a foreword, try mashing Enter when it's stuck. I got this on my other machine, and then it turned out it was asking me to enter a new *label* for the live image. But the splash screen was hiding it so it never showed until I booted with the splash disabled. I shrugged it off as computer dementia.

First, you'll want to be *extra* sure neither the downloaded ISO image nor the medium is corrupt. In the boot menu there should be an option that checks each file.

Alternatively, if you downloaded normally over the web, then download the .torrent file, open it up in your torrent manager of choice, and point it to download onto your existing ISO file. That should make it hash the file and redownload any chunks that don't match the .torrent.

If you burn it to a CD, as opposed to copying over to a usb stick with for instance [UNetbootin](http://unetbootin.sourceforge.net) (which by the way is fast and really easy), then burn it in very low speeds. 2-4x perhaps.

---

All of the above would be for the live cd/usb, of course. On your finished alternative installation, try booting it without the splash screen. Boot to the Grub2 bootloader, edit the entry for the newest kernel (Ctrl+E? it should say on the screen), navigate down to the **linux** line, and replace **splash** at the end with **_no_splash**. Then hit Ctrl+X to execute the entry. See if it says anything of interest.

If it doesn't, redo the same procedure and while modifying the kernel entry, also remove **quiet** to make the boot more verbose. Look for error messages.

---

### Post by Catharsis on 2010-05-08
Zorael gave very good advice; I hope you follow it before trying anything I have say.

How long do you let it wait there? Is the disc activity light still flashing? I get this too for a bit while ureadahead reads everything to ram.

Also, this worked for other people:
[http://ubuntuforums.org/showpost.php?p=9235797&postcount=16](http://ubuntuforums.org/showpost.php?p=9235797&postcount=16)

You could also try booting into recovery mode. Hold down Shift as you boot and then choose the recovery kernel.

---

