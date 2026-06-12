---
title: "Stuck during installation (resolution issue?)"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by grimsniffer on 2007-04-28
Hey guys,

Well, I'll give you guys some details before I go down to my problem.
I'm working on an 4400+ AthlonX2 AMD machine,
Video card: XFX Nvidia 7950GT
1GB RAM
Using an LCD 19" wide-screen monitor connected through DVI
(more information can be provided, not sure how much it'll be relevant though)

Started installing Ubuntu last night, problem is my CD burner isn't working - so I downloaded the USB netinst, and used my 1GB flash card to install it.
The installation booted up, everything was fine. Went through the steps, formatted the hard-drive, etc. I chose to install the Kubuntu desktop (From my previous experience with Linux, I prefer KDE over Gnome). Then it asked me about screen resolutions - I chose the resolution I normally work with(1440X900). Then I see a progress bar, which gets stuck at 6% and asks me to "please wait..." left that for over an hour, and nothing.
I booted up the computer and tried installing again - same thing. Booted it up a third time, installed again, tried to choose a few other options for the resolution, to give the computer some choices - nothing.
At the moment, I tried rebooting a fourth time and choosing no resolution (which according to the installation is equivalent to choosing them all and letting the system decide) - still, same thing. The progress bar just gets stuck at 6% and asks me to please wait.

Please please please - if anyone knows what the problem is, I would VERY much appreciate your help. :)


Thanks,



Sincerely, Grimsniffer.


P.S.
Before posting I looked through the forum for a similar problem and didn't really find anything. So if there's some thread about this already, I do apologize.

---

### Post by kagashe on 2007-04-28
> Before posting I looked through the forum for a similar problem and didn't really find anything. So if there's some thread about this already, I do apologize.


This[ thread]("http://ubuntuforums.org/showthread.php?t=379807") may help you.

It is suggesting to break the installation process just before GDM (or may be KDM in your case) loads, edit xorg.conf file to use "vesa" driver initially instead of the driver chosen by the CD.

After installation you can change to proper Nvidia driver.

kagashe

---

### Post by grimsniffer on 2007-04-28
Thanks for the help,

Tbh while I was writing this and looking through other threads, the screen was stuck on the other computer. And well, it took it over an hour, but it actually continued. The installation was completed successfully (silly me)... Just didn't think it could take so long, so I was sure it was stuck.

I do have another issue now - if anyone has an idea as to it, because I'm stuck here too:
The installation is complete, I rebooted. When I reboot, and remove the flash drive the system simply won't boot. It hangs when it's supposed to boot from the hard-drive and does nothing. Num-lock works on the keyboard, ctrl-alt-del works, but nothing else does, and the only thing I see on the screen are the previous POST lines.

I tried to boot it from floppy again, and this time it won't even do that. When I try to boot from floppy I get a screen filled with a continuous loop of "GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB, etc." all screen.
And no, I didn't install grub (was no need, since Kubuntu is to be the only OS on the computer). I wasn't even asked about grub during the installation, which is why I find this very odd.

Any thoughts?

I'm gonna try to tinker with it some more meanwhile.


Thanks.

---

### Post by Loki-uk on 2007-04-28
The install hangs at 6% and 85% for ages :) not that I've done a lot of installs lately (about 20 in the last 2 weeks lol).

But if you wait it'll work.

Loki

---

