---
title: "Add XP to Ubuntu and dual-boot?"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by perstromgren on 2007-01-08
Cheers!

I am a new-comer to running Linux, but used SysIII (!) back in the mid seventies. Unix/linux has come a long way since then! Anybody can pull down Ubuntu and load it nowadays. Good work!

I have installed Ubuntu on my lap-top and I did leave an extra partition in case I wanted to run Windows. Well, now I want to try that.

This is what I have:
```
[FONT="Fixedsys"]
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671   83  Linux
/dev/hda2             638         765     1028160   82  Linux swap / Solaris
/dev/hda3             766        1402     5116702+   b  W95 FAT32
/dev/hda4            1403        4864    27808515   83  Linux
[/FONT]
```

/dev/hda3 was what I had in mind for Windows XP. Will that do? Can I load XP onto that and dual-boot?

I know that one is supposed to do the other way around (add linux onto windows), but I was not aware of that, I'm afraid. I did read the thread about the extra drive with XP on it, but it did not seem to be usable for me.

Any pointers or other help would be great! Even a "sorry, lad, can't be done" would be appreciated!

Per.

---

### Post by meng on 2007-01-08
You can do this certainly, XP may prefer to be on an NTFS partition though. Anyway, you'll need to re-install grub after Windows installation, because the MBR will be overwritten with the Windows bootloader.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by logos34 on 2007-01-08
You really should put winxp on a ntfs partition.  

Here's a [page]("http://www.psychocats.net/ubuntu/partitioning") you might find helpful.

---

### Post by atlien on 2007-01-08
Be careful with your XP install. I installed XP on a completely separate drive and it still overwrote my MBR (??) preventing me from having dual boot capability.  I had to re-install GRUB to get to Ubuntu.

The experts of this forum saved me once again.;)

---

