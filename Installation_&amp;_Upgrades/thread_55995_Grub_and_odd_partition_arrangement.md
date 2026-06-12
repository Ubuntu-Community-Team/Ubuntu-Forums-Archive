---
title: "Grub and odd partition arrangement"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by walkingbeard on 2005-08-10
I've just installed Ubuntu.  My partitions are as follows:

/dev/hda1   ext3                         Ubuntu installed here
/dev/hda2   extended
    /dev/hda5   ntfs                      XP installed here
/dev/hda3   swap
/dev/hda4   fat32                        Swapping files between XP & Linux with old kernels
/dev/hdb1   ntfs                          Data

How do I set up Grub to have an option to boot from that hda5 partition?  I can't work it out.  I've tried:

     title Windows XP
     root (hd0,4)
     makeactive
     chainloader +1

... but this doesn't seem to do it.

I configured that with webmin's grub plugin.

When I try to boot Windows, I get this:

root (hd0, 4)
Filesystem type unknown; partition type 0x7

chainloader +1

Error 12:  Invalid device requested

Cheers for any help,

Beard

---

### Post by blind0wl on 2005-08-11
Try this in your grub menu.lst instead:

```

title=Windows XP
rootnoverify (hd0,4)
makeactive
chainloader +1

```

---

### Post by walkingbeard on 2005-08-11
[QUOTE=blind0wl]Try this in your grub menu.lst instead:

```

title=Windows XP
rootnoverify (hd0,4)
makeactive
chainloader +1

```[/QUOTE]
 I was wrong up here.  The Error 12: Invalid device requested comes after the makeactive.

I took out the makeactive and it went to chainloader +1 and nothing happened.

I take it that you use rootnoverify because grub doesn't understand ntfs and because you don't need grub to understand.

---

### Post by pja on 2005-08-11
Hi!

I noticed that you are logged on and you might be able to help with a related problem.

I have corrupted my boot loader (two hard drives - WinXP and Ubuntu) and don't know how to get at Ubuntu without doing a complete re-install.

Any thoughts?

Regards,
Peter   :-?

---

### Post by walkingbeard on 2005-08-11
[QUOTE=pja]Hi!

I noticed that you are logged on and you might be able to help with a related problem.

I have corrupted my boot loader (two hard drives - WinXP and Ubuntu) and don't know how to get at Ubuntu without doing a complete re-install.

Any thoughts?

Regards,
Peter   :-?[/QUOTE]
 The only ways I can think of are to see if either the Ubunto CD or website has a rescue disk image to download.  Sorry!

---

### Post by walkingbeard on 2005-08-11
I've now got the following:

```
rootnoverify (hd0, 4)
chainloader (hd0, 4)+1

``` 

I found this in some other post somewhere. It doesn't work. I got:
Device string unrecognizable

---

### Post by blind0wl on 2005-08-11
Yeh Chainloader +1 is to actually grab the first sector from the start of the partition, so leave that line alone.  Makeactive is also usually required.  Your on the dot with the rootnoverify line, it just means grub needs to boot something that it wont understand.  Make sure your lines dont have the spaces in between the 0,4.

You are sure that windows resides on hda5??  If you were to mount that partition in Ubuntu, does it come up with all the correct folders?

---

### Post by blind0wl on 2005-08-11
[QUOTE=pja]Hi!

I noticed that you are logged on and you might be able to help with a related problem.

I have corrupted my boot loader (two hard drives - WinXP and Ubuntu) and don't know how to get at Ubuntu without doing a complete re-install.

Any thoughts?

Regards,
Peter   :-?[/QUOTE]

How was it setup originally?  Did you have grub boot ubuntu and winxp?  If that is so, you'll need a knoppix or similar type boot disk to chroot into your system and run grub again to get it into the mbr of your hd.  I can step you through the process if you can get a knoppix type boot disk.  Maybe start a new thread for this and let me know where it is...

---

