---
title: "Manual grub installation"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by ralyon on 2009-11-25
I'm having trouble installing grub manually on a new disk. On a working 9.10 system, I went into /etc/default/grub and uncommented GRUB_DISABLE_LINUX_UUID=true and then ran grub install which looks like it removed most of the UUID entries.

I then duplicated the file system from anouther 9.10 system on to a new disk and I have tried sudo grub-install --root-directory=/media/disk /dev/sdb as well as sudo grub, root (hd1,0), setup (hd1) and when I try and boot the new disk I only get a grub> prompt and when I try and do an ls it gives me an Error 27: Unrecognized command.

In 9.04 with grub legacy I used to remove all references to the UUID in the menu.lst file and then duplicate the disk and run sudo grub, root (hd1,0), setup (hd1) and it would boot without a problem. But now I can't seem to do a manual install on to a secondary disk anymore with grub 2. I am doing the duplication on a separate system and the disk that I am duplicating is the only drive in its system (/dev/sda1, not even a floppy or cdrom drive). I have attached my grub.cfg file as well.

In searching, everything I can find seems to assume you are installing grub on the system you will be booting which is not an option in my case. Does anyone know how to install grub 2 the way you could with grub legacy? Thanks for your help.

ralyon

---

### Post by jjcv on 2009-11-25
Have you had a look at this howto for Grub2?

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

---

### Post by jjcv on 2009-11-25
Have you had a look at this howto for Grub2?

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

---

### Post by presence1960 on 2009-11-25
Try installing grub from 9.10 Live CD. See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

---

### Post by ralyon on 2009-11-28
I have to do these on a regular basis and I'd like to be able to do the whole process with a script like I was able to do with grub legacy. Having to boot to a live cd would greatly increase the complexity and time involved.

Thanks for the suggestions though.
ralyon

---

### Post by ralyon on 2009-11-30
The problem is partially my fault. In the process of trying to get this working I installed grub on my host system not realizing that this was grub legacy. I have since removed grub and reinstalled grub-pc. 

Now I can do the grub-install --root-directory=/media/disk /dev/sdb, but I still got an error about the UUID not existing. I removed the "search --no-floppy --fs-uuid --set..." line from the grub.cfg and that lets it boot at least.

2 problems still remain. The first being the obvious editing of the grub.cfg file. I looked in the default grub file and in the linux script file, but I was not able to find where it creates the "search..." line. How do I tell grub to either not include this line or to not include UUID information in this line?

Second is that I am still getting the can't find UUID message on boot which flashes by briefly which after searching I think may have something to do with either the --no-floppy option or because I installed grub from a separate system it might be the UUID of the disk in that system. Although not a big deal it would be nice to remove that message.

Also, I had gone through both of those links before posting jic you thought I might be ignoring you. Sorry I didn't mention that last time.

ralyon

---

