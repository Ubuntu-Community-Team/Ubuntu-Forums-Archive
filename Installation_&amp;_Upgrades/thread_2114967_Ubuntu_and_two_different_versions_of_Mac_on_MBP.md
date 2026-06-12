---
title: "Ubuntu and two different versions of Mac on MBP"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by szymciolop on 2013-02-11
Sorry if I'm posting on the wrong thread, I haven't found a better one.
I have MBP with Ubuntu 12.10, and Mac OS X Snow Leopard and Mountain Lion. I would like to get rid of stuff like rEFIt or chainloading dozens of times. Before the installation of second Mac OS X i simply used:

```
menuentry 'Mac OS X'
{
  search --file --no-floppy --set=root /usr/standalone/i386/boot.efi
  chainloader (${root})/usr/standalone/i386/boot.efi #-v
}
```

and also a script in StartupItems which blessed grubx64.efi every time I booted into Mac.
But now, my past solution doesn't work. I would be a lie, if I told I know how to write all those grub scripts. I saw many solution, but only this one worked for me, and now it isn't. And that is why I am asking you for help: what should I write to make this work?

And this are my partitions:
```
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            322.0 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
   4:                  Apple_HFS Mountain Lion           38.7 GB    disk0s4
   5:                 Apple_Boot Recovery HD             650.0 MB   disk0s5
   6:       Microsoft Basic Data Untitled               137.9 GB   disk0s6

```

Sorry if the topic isn't very Ubuntu related, but I thought this is the best place.

---

