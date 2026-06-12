---
title: "Upgrading from an ISO image without burning it, is it possible?"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Starlight on 2006-10-27
Hi!

I have a question... I'm downloading an ISO image of the alternative install CD, so that I can upgrade my Ubuntu Dapper using it, because online upgrade didn't work well... Is it possible to somehow mount the ISO file as a CD-ROM and upgrade the system from it, without having to burn the CD?

---

### Post by ntufar on 2006-10-27
Yes, it is possible. You can mount your CD image without burning it:
```

sudo mkdir /xyz
sudo mount -o loop /full/path/to/your/image-file.iso /xyz

```

Now your CD image is mounted under /xyz.

After finishing, unmount and erase the directory.

```

sudo umount /xyz
sudo rmdir /xyz

```

Hope it helps

---

### Post by Starlight on 2006-10-27
Thanks! :) If I do it, then how do I actually upgrade from it? I know that when I use a real CD-ROM, I have to use this command:

sudo apt-cdrom add

Will it also work with the ISO?

---

### Post by chickengirl on 2006-10-27
> **Starlight said:**
> Thanks! :) If I do it, then how do I actually upgrade from it?

I would also like to know this. I can't find any mention of upgrading via CD in the release notes or the wiki - which is strange, because I could swear I've seen it mentioned before.

---

### Post by chickengirl on 2006-10-27
found it -- I was barking up the wrong wiki.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by Bad Seed on 2006-10-27
> **Starlight said:**
> Thanks! :) If I do it, then how do I actually upgrade from it? I know that when I use a real CD-ROM, I have to use this command:

sudo apt-cdrom add

Will it also work with the ISO?
That command didn't worked for me mounting the iso. But what I did was to open the file named cdromupgrade (or something similar) inside /xyz and the upgrade began.

I'm posting this message from Xubuntu Edgy Eft :mrgreen:.

Cheers.

---

### Post by chickengirl on 2006-10-27
> **Bad Seed said:**
> That command didn't worked for me mounting the iso. But what I did was to open the file named cdromupgrade (or something similar) inside /xyz and the upgrade began.

I'm posting this message from Xubuntu Edgy Eft :mrgreen:.

Cheers.

So, is that script not affected by the bug with the update manager? And -- I'm curious -- with the cdrom upgrade, does it upgrade everything that's available from the CD and then pull other packages from the web? (for example all of the regular ubuntu stuff I have, and all the miscellaneous stuff I've pulled from the repos?) Is that how it works?

---

### Post by Bad Seed on 2006-10-28
> **chickengirl said:**
> So, is that script not affected by the bug with the update manager?
Hi chickengirl. I read yesterday on the Xubuntu IRC channel that the bug appears only upgrading using *g**ksu "update-manager -c"* but I forgot to ask if that included *gksu "sh /cdrom/cdromupgrade"* ](*,). 

Originally I wanted to use the second method (changing the repos from Dapper to Edgy and the aptitude dist-upgrade) but because I couldn't use *sudo "apt-cdrom add"* with the mounted iso, I took the risk and launched cdromupgrade from Thunar (I'm pretty sure is the same than doing *"sh /cdrom/cdromupgrade" *but I mention it just for general info)

> **chickengirl said:**
> And -- I'm curious -- with the cdrom upgrade, does it upgrade everything that's available from the CD and then pull other packages from the web? (for example all of the regular ubuntu stuff I have, and all the miscellaneous stuff I've pulled from the repos?) Is that how it works?
When I launched it, the Update Manager asked me for an internet connection, fetched the upgrades availables and the asked me again to download another 90 MB of updates.

Cheers and sorry with my english, I hope it's readable :p.

---

### Post by Bad Seed on 2006-10-28
I forgot to mention something just to clarify. Because I originally planned to use the second method, when I launched cdromupgrade I had already edited my repositories to edgy from dapper.

Also, I had a system hang finishing the installation (nothing to do with [the reported bug]("https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/68027")). The way I completed the upgrade was restarting the computer and then typing *sudo dpkg --configure -a* from a terminal.

Cheers.

---

### Post by dliloch on 2006-10-28
try this...
mount your.file.iso /cdrom -t iso9660 -o loop

that should mount it but can you install from it .. that i don't know..

---

### Post by chickengirl on 2006-10-28
If did the upgrade from gnome instead of xfce, would I still have to worry about the bug?

Or, when they fix the bug will we get an update to the update manager and then will it be safe to upgrade?

---

