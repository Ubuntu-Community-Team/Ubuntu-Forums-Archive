---
title: "Please someone end my pain!"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by ionizd on 2005-11-20
Hello From the U.S!
Unfortunately, I have an ulterior motive for this post. I'm attempting a new install of Ubuntu 5.10 on an older test platform (Pentium III 450 Mhz) and everything seems to go swimmingly until the first reboot from the harddrive. The Grub program attempts to load and...nothing!:???:  No error message, no desktop, no small voice telling me that the computer doesn't like me, nothing! Only a dismal black screen with a flashing cursor at the bottom forever mocking me with its recalcitrant behavior. The live CD loads fine and works like a champ. I tried the Kubuntu install download as well with worse results. It didn't even make it through the first stage of the install. I don't think I'm getting good downloads, or possibly my burner isn't writing the CD's properly, and I'm missing files.
 I'd like to attempt an over-the-net install if I can, but I don't see how to do it or if it's even possible. Any thoughts? I'd really like to verify that this O/S is good enough for my main rig, but if I can't get it working on the test system then no way!

---

### Post by aysiu on 2005-11-20
Did you burn your live CD ISO, too? And that appears to work?
If you're worried about CD corruption, you can [do a checksum on the ISO image you downloaded](http://www.linuxiso.org/viewdoc.php/verifyiso.html).

---

### Post by ionizd on 2005-11-20
Yes, I did download and burn the live CD's, and they do seem to work just fine, but with limitations and missing plugins that I can't be sure are inherent to the live program, since I don't have an installed version to compare it with.

---

### Post by ionizd on 2005-11-20
Hello From the U.S!
Unfortunately, I have an ulterior motive for this post. I'm attempting a new install of Ubuntu 5.10 on an older test platform (Pentium III 450 Mhz) and everything seems to go swimmingly until the first reboot from the harddrive. The Grub program attempts to load and...nothing!:???:  No error message, no desktop, no small voice telling me that the computer doesn't like me, nothing! Only a dismal black screen with a flashing cursor at the bottom forever mocking me with its recalcitrant behavior. The live CD loads fine and works like a champ. I tried the Kubuntu install download as well with worse results. It didn't even make it through the first stage of the install. I don't think I'm getting good downloads, or possibly my burner isn't writing the CD's properly, and I'm missing files.
 I'd like to attempt an over-the-net install if I can, but I don't see how to do it or if it's even possible. Any thoughts? I'd really like to verify that this O/S is good enough for my main rig, but if I can't get it working on the test system then no way!

---

### Post by aysiu on 2005-11-20
It's inherent to the base installation of Ubuntu, as it's dedicated to free software. For more, read this: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by yesplease on 2005-11-20
Aysiu already wrote how to check if your cd is corrupted or not. A good way to download ubuntu is via bittorrent, this program downloads the iso in small parts and checks each part.

If this old computer keeps giving you problems you may consider to install Ubuntu on the new one, that is your goal anyway. Ubuntu is safe to try. If you decide you dont like it, it is easy to remove. If there are problems and you can reach internet (for instance via the old computer) you can ask questions here.

This is not a direct answer to your question but it may save lots of time.

---

### Post by ionizd on 2005-11-20
Well, I burned a new copy of Kubuntu 5.10 install and tried it. It now does the same thing as the Ubuntu 5.10 install-so I'm not inclined to think the problem is with my downloads or the disks themselves. I know the IDE interface is working properly, because Windows 2K install goes like clockwork. Am I just not doing something correctly?

---

### Post by yesplease on 2005-11-20
This could just be a grub problem. You have windows 2000 and ubuntu on the computer? I had a similar problem once and "solved" it by putting grub on floppy. This worked but a real solotion is to edit grub. There is something about that in the rescue mode section of the starterguide [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode).

There are also howtos for editing grub on the forum.

---

### Post by ionizd on 2005-11-21
[QUOTE=yesplease]This could just be a grub problem. You have windows 2000 and ubuntu on the computer? I had a similar problem once and "solved" it by putting grub on floppy. This worked but a real solotion is to edit grub. There is something about that in the rescue mode section of the starterguide [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode).

There are also howtos for editing grub on the forum.[/QUOTE]
 I don't have Windows on this machine at all. I don't seem to have the option to edit anything, not that I would know how to do so if I could. Can I use the live CD to get the desktop up and then edit Grub? How do I get a copy of Grub installed on a floppy? I clicked on the link provided but I didn't find any info useful to me... that could be because I don't know what I'm looking for.
 This is what I'm getting- after the install completes, it shuts down. Upon reboot, it tells me it's loading Grub boot loader- please wait. The cursor is flashing underneath... uhh, forever. That's it.
 One more question- How big does the HDD need to be for this install? On this test machine, I've got a 2.3 Gb Fujitsu. If it were too small, wouldn't the installer tell me? I can post full system specs, but this is what I know off the top of my head;
Pentium III 450Mhz
Asus P2B-S motherboard
generic 400W PSU(tested-it works)
256Mb SDRAM(tested--it works)
Fujitsu 2.3Gb IDE HDD
Maxtor 15.6Gb IDE HDD(Untested-I don't know if it works yet)
generic IDE 32X CD-ROM

---

### Post by yesplease on 2005-11-21
Try the 16GB disk. (My root is more than 2GB already) You can use the small disk for other things later, after the install works.

Your system is good enough. After install you can use ubuntu for a while and decide if you want a lighter desktop than Gnome. But that is all for later. 

Good luck and tell us if it worked or if you have more questions.

---

### Post by ionizd on 2005-11-22
The !6Gb HDD is useless.
 And how do I get a copy of Grub on floppy? I really think that may help me chase this problem down.

---

### Post by yesplease on 2005-11-22
Like I said earlier: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)
your floppy is /dev/fd0.

NB, your system seems good because the live CD works. your hard disk is too small. Try to get a second hand hard disk, or keep using the live cd.  Good luck.

---

### Post by SickTwist on 2005-11-22
ionizd, are you manually partitioning the HDD during the Ubuntu install? If so, ensure there is one primary partition and that the boot flag is set on it. This can all be done via the partitioning utility during the install. Also, be sure that your BIOS is set to boot from the HDD with the primary partition on it.

As for GRUB on a floppy, you may be able to do that during the installation as well. At the point where the installer asks if you want to write GRUB on the MBR, select no. Then when asked where you would like to put it, type this:

/dev/fd0

That will instruct the installer to write GRUB to your floppy drive. I'm not sure if this will actually work (the floppy drive driver might not be loaded during the install) but it wouldn't hurt to try it.

Also, you may want to try booting the install CD with these options:

linux noapic nolapic acpi=off

Just type that on the first screen of the installer (with the Ubuntu logo) and press enter. This is another boot option you could try:

linux failsafe

Let us know how it goes.

---

### Post by ionizd on 2005-11-24
[QUOTE=yesplease]Like I said earlier: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253) your floppy is /dev/fd0. NB, your system seems good because the live CD works. your hard disk is too small. Try to get a second hand hard disk, or keep using the live cd. Good luck.[/QUOTE] You were absolutely correct- the hard drive was to blame. Install was completed satisfactorily, seem to be having some audio glitches, though. Hmm... Decided to go with Kubuntu- I really like the look and feel of it. Thanks for the help. :KS ***EDIT*** Get the following at boot: Sound server informational message: Error while initializing the sound driver: Device /dev/dsp cannot be opened (no such file or directory) The sound server will continue, using the null output device. Also, The speaker icon in the system tray has a red "X" thing over it and when I move the cursor over it, it says, "The mixer cannot be found." A little more help, please?

---

### Post by ionizd on 2005-11-24
Sorry for the double post, but I had a Question and my last post didn't seem to update to newest position.

---

### Post by yesplease on 2005-11-25
Hi, good to see that you where able to install. 

I dont know the answer to your question, but there is a special section for it: [http://ubuntuforums.org/forumdisplay.php?f=114](http://ubuntuforums.org/forumdisplay.php?f=114) .

Before posting a question I recommend checking the Howto section, they are very good [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100) . There you will find the solution to many  problems, good luck :)

---

