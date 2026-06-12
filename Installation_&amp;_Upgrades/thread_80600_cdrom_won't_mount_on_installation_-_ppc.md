---
title: "cdrom won't mount on installation - ppc"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by shinsplints on 2005-10-22
Hello,
Im installing 5.10 on my friend's mac (a crazy attempt to get him to play counter-strike via wine or cedega, but lets leave that conversation for another thread ;) ).  Anyways, i boot with a ppc install disk, kernel loads up, I select a language and keyboard layout.  Then I get up to detect and mount cd-rom, and it fails.  I switch over to a shell and try "mount /dev/cdroms/cdrom0 /cdrom" and get this output:

mount: /dev/cdroms/cdrom0 is write-protected, mounting read-only
mount: /dev/cdroms/cdrom0 is write-protected, mounting read-only
mount: Mounting /dev/cdroms/cdrom0 on /cdrom failed: Invalid argument

(the first line appears twice, not a typing error)
stumped on this.  The computer boots the cd properly yet can't mount the drive, any clue what could be up with this?  I'm going to go try the live cd in the meantime.

---

### Post by Jenda on 2005-10-22
Maybe you should put ./cdrom in the /media subd.: /media/cdrom
Don't forget to create the dir. first:
```
sudo mkdir /media/cdrom
```

---

