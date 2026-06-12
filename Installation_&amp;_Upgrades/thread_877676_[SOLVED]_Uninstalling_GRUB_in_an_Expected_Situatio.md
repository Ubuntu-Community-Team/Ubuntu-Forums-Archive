---
title: "[SOLVED] Uninstalling GRUB in an Expected Situation."
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by Audacitor on 2008-08-02
Okay, so I'm working on converting a friend of mine from Windows to Ubuntu.  We spent eight hours today having fun with Compiz Fusion and getting everything setup for her.

We installed Ubuntu on an external hard drive, leaving her Vista installation intact, so as to smooth the transition process.  Since she doesn't need her laptop during the Summer, she let me take it home with me so I could do some of the geekier stuff on it.

When I got home, I tried to boot up, but it told me it had an I/O error while loading the necessary boot files.  It did this multiple times.  I couldn't load into either Ubuntu or Vista before this happened.  I formatted the external hard drive with the intent of reinstalling Ubuntu.

I had thought an I/O error was an issue on the software level.  Turns out it meant hardware (I'm a Linux semi-newbie; I don't have a working installation of Ubuntu for my own, although I'm quite capable of setting it up.  However, I mostly rely on geek-sense to get me where I'm going).  The external drive was overheating.  You can move about three GBs of before you hit an I/O error.  This means I can't reinstall Ubuntu. Or GRUB.

I'm getting another external drive tomorrow.  I'd still like to get into Vista though.  My friend isn't especially tech savvy (though the potential is there) so she has a cluttered desktop and lots of startup items that she doesn't need and dearly hates, and I'd like to clean things up for her.

So, in summary:
1.  Computer tries to load GRUB from external hard drive.
2.  Computer can't.  External hard drive doesn't work.
3.  Cannot boot into recovery mode to get rid of GRUB.
4.  I have a LiveCD.

---

### Post by Partyboi2 on 2008-08-02
Download and use [[COLOR=Blue]super grub[/COLOR]]("http://www.supergrubdisk.org/") to restore the mbr for vista. Then you should be able to boot back into vista.

---

### Post by Audacitor on 2008-08-02
I'm afraid I'm having some problems installing SGB.  I'm using [these instructions]("http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB."), and I've already tried [this solution]("http://www.supergrubdisk.org/wiki/SGD_Howto_make#Common_errors").  Here's the problem:

```
grub> device (hd3) /dev/sdb2

grub> root (hd3,0)

Error 22: No such partition

grub> setup (hd3)

Error 12: Invalid device requested

grub>
```

As it stands now, I have a the thumb drive with a 200GB FAT32 partition with SGB in it waiting for this to happen.  What should I try?

---

### Post by Partyboi2 on 2008-08-02
Unfortunately I have only used the super grub cd not the usb option, so I am not familiar on how to set it up, maybe someone  else might know.

---

### Post by logos34 on 2008-08-02
try these instructions:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk)

---

### Post by Audacitor on 2008-08-03
Sorry for the long wait for a response.  I got it to work.  I was able to get access to an additional CD burner, so I put SGB on that instead.  The long wait comes from configuring and perfecting her installation; I wanted to get her laptop back to her as fast as possible.

Thanks for your help, guys.

---

