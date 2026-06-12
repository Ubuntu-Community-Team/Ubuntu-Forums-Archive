---
title: "installing"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by brihy1 on 2006-12-08
i downloaded and burned the ubuntu 6.1.0 and am installing it i have win xp on the computer and when the install starts it has the option of resizing the partition so i do that and the install continues and the cursor has a spinning wheel,is anything happening? does this install process take awhile?

---

### Post by aysiu on 2006-12-08
It usually takes about 20 minutes for the whole installation.

The spinning wheel could be a number of problems:

1. **Not enough RAM.** I get a total freeze if I try to install on my old computer (766 MHz, 128 MB RAM) using the live CD.

2. **Bum disk.** The ISO might have corrupted during download or burn. If you're not sure about how to prevent that, read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

3. **Faulty hardware?** Doubtful, since you probably have a perfectly fine XP installation.

---

### Post by brihy1 on 2006-12-08
i have a dell optiplex 900 mhz 382 mb ram and xp pro runs fine,i also partitioned my drive with a ext  3 and swap but when i try to install it says no root file found?i ran the check cd for defects and its fine.

---

### Post by Seti on 2006-12-08
I've also been having some trouble installing Edgy Eft, never used to have problems with previous Ubuntu releases. It seems that now when I do a clean install, the installer doesn't like my partition scheme for some strange reason. Now I haven't changed my partitions around or anything, but it always wants to use /dev/hda5 as /, which I don't want to do because I have another linux system there. If I tell it to put / on /dev/hda1, and click next to proceed, it invariably tells me "No root filesystem". I never used to get this on previous releases. Now I have to play games with it, such as deleting /dev/hda1, remaking it as reiserfs, rebooting, and all this monkey business in order to get it to work. Typically I have found that it finally accepts making /dev/hda1 as root and proceeds, but not before giving me a major hassle. There is nothing wrong with my hardware, the CD or the ISO image burnt on the disc. 
Any ideas????

---

### Post by drphilngood on 2006-12-08
> **Seti said:**
> I've also been having some trouble installing Edgy Eft...
...Any ideas????

Try the [Alternate Installer CD]("http://www.mirrorservice.org/sites/releases.ubuntu.com/edgy/").

---

