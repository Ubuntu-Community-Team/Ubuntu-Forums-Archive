---
title: "Installing Using Bootable Floppy"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by SighKick on 2005-07-23
**Update: 24th July**  I have found a thread about Smart Boot Manager and am hoping this will do the job.  My initial forum search didn't offer this solution, only my search in Installation Help today.

I have an old Packard Bell P120Mhz with 32Meg Ram and a 1.2Gig HDD and wanted to use it to experiment with Ubuntu.

Unfortunately, although the BIOS gives the option to make the CD the 1st Bootable device, it does not find the CD.  It won't find any CD unless it has the image of a bootable floppy written to it.

So the computer will boot from the floppy or the CD with a bootable floppy image on it (Win98 Startup Floppy).

Is there any way to start the installation process of Ubuntu by booting off a floppy first, just as one would have installed Micro$haft Win95 or 98 on older computers?

Can anyone point me in the right direction?  I have tried using NTRawrite to copy \isolinux\isolinux.bin to a floppy disk on a friends suggestion, but no joy.

Help plse  ](*,)

---

### Post by Typhoon on 2005-07-23
I haven't tried this, but you might explore it.

I have installed Debian Sarge on an old laptop that has precisely the problem that you mention. The Debian mirrors have boot disk images - you need the boot.img, root.img and drivers.img.

After that, it installs basic packages from the network.

Works well for Sarge, but you might be able to adapt the process for Ubuntu.

HTH,
Typhoon

---

### Post by SighKick on 2005-07-23
Typhoon,

Thanks for your response.  Unfortunately I don't have the skills to adapt one installation procedure to fit another just yet  :-? 

I do have RH6.5 boxed set which includes books, boot disk etc and I may end up trying to install that to learn more but would really love to stick to ubuntu because I love the concept of what is being achieved by this organisation.

Surely there must be someone out there that has had to install **ubuntu** on an older computer using a **bootable floppy?**

Thanks in advance

Dave of New Zealand.

---

### Post by SighKick on 2005-07-23
**Sheepish *Grin* **  :roll: 

I asked and answered my own question - when I did my initial search on the whole forum I didn't find an answer.  My search on 'Installation Help' came up with just the answer to my problem.  I found....

[https://wiki.ubuntu.com//SmartBootManagerHowto](https://wiki.ubuntu.com//SmartBootManagerHowto)  and also....

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

And it works.....**thanks for listening.**  At least you didn't 'flame' me like does happen in forums when the same question gets asked time and time again.  Perhaps my initial search query wasn't worded correctly?

---

### Post by Tomlin on 2005-07-30
I'm having a problem using this method. I made a floppy using SBM. I boot to it and choose the CD ROM option. It asks if I want to save it and I press the "Y" key. It comes back saying its been saved. I press enter while the CD ROM line is highlighted and a window pops up saying:

Disk error! 0xAA

I've installed 3 different versions of Redhat and one Suse on this machine (as a test before installing on the intended machine). Those installations had ".img" files that were copied to a floppy using rawrite. You booted to the floppy and when asked where the install files were, chose CD ROM. The install proceeded off the CD from there.

I have an old machine whose BIOS doesn't include a "boot from CD" option. It's either floppy or hard drive.

I guess I'm screwed. ](*,)

---

### Post by wvslkr on 2005-07-30
Just use the no option and it should work.  You may have to make a new disk since you saved the one you have.  I have not been able to get SMB to work with the save option but works fine with no.  Gl :)

---

### Post by Tomlin on 2005-07-30
Thanks for the reply. I tried and no go. I also tried in another pc and it worked fine. I guess it just doesn't like that drive, although other distros have had no trouble with it. Looks like I'll have to skip this distro.

Thanks again.

---

### Post by Tomlin on 2005-07-31
Well...I swapped out the CD ROM for a different one and that worked. After the 1st reboot to finish the install, I'm getting:

GRUB Geom Error

So...I'll do a little searching on the forums to see if I can figure this out.

---

### Post by BiggoCharley on 2005-08-01
I've been following this thread for the last few days since it seems to apply to my problem. I made a boot floppy using rawrite as per the instructions on the wiki.ubuntu.com website mentioned above.  I get 4 options when booting up with SBM 1. Quit to BIOS, 2.Reboot, 3. FD0- Floppy , and 4.HD0- Harddisk.  My Cdrom is a parallel port external drive. (Backpack). No option to boot from it on the SBM menu.  Is there a way I can get SBM to recognize this drive? (BTW I also made a boot floppy from the sbm.bin disk image on the Ubuntu CD with the same results.)
Charley

---

### Post by wvslkr on 2005-08-05
@BiggoCharley

Try this link.[http://www.expnet.com/know.nsf/0/92de7e247d77401685256708005da467?OpenDocument](http://www.expnet.com/know.nsf/0/92de7e247d77401685256708005da467?OpenDocument)

Don't know if it will help you or not.  GL. :)

---

