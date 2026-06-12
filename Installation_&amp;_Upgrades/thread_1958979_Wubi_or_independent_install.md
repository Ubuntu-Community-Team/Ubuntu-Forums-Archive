---
title: "Wubi or independent install?"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by ankush981 on 2012-04-15
Hello,

I currently have Linux installed through Wubi, but there are a couple of things I don't like about it. First of all, for some very strange reason, the grub menu gives me an error when I select Ubuntu (saying something like "error: you need to load the kernel first"), and the grub menu reappears. If I then then wait for 4-5 seconds and press Enter again, Ubuntu starts correctly. I wonder why this is, and whether I should worry about it.

Secondly, when I look inside the Linux's FAT32 partition from Windows, I don't see the directory structure, but rather single "disk" files like "home.disk", etc. This makes me suspect that Wubi stores things in the form of compressed files, which are unpacked on the fly.

So the question is: which is a better idea: Wubi or independent install leading to dual-boot? Also, suppose Windows crashes someday and I end up overwriting the MBR, will the normal methods of GRUB rescue work the same way for Wubi-installed Linux?

---

### Post by darkod on 2012-04-15
I would say the proper dual boot is always better.

If windows crashes, depending what exactly is the problem, you might not be able to boot wubi either. In some cases you can access the wubi data from a ubuntu live mode, or even windows.

But for long term use, start planning a dual boot. Wubi was never meant to be a long term install, just a quick try.

---

### Post by jadtech on 2012-04-15
its alway better to do an install on its own partition each way has its merits, if you are sure you have room on your HD and you have all the back ups and recovery disk for windows and Ubuntu use Wubi to get a feel for linux before your attached to the set up do the full install..
the install from wubi is a full version running on window its not compressed it is you linux root partition that will exspand to the size max size you orginally set it for .disk is an exetension windows understands rather then .hda2 that is how I under stand it .. 
 
as far as compressed files your working in a fat partition all Files are compressed fat is a compression format :)
drives are  far larger today makes things a bit easyer but  if it wasnt for compression window 7 might be 199 TB bloated on its own forget the programs we run on it ..

1 byte system would be 8bit to have 32bit system native as it were would take 4bytes of HD space for 1MB 8 bytes for 64bit..
fat compression changes the game a bit fat 32 compresses this x4 meaning a windows system that takes up 80 gigs with out compression would take 4up 640 gigs of HD space 64bit would be worse as it splits 32bit in half..

linux will run on the same format even with its own partition and no matter how you install it if have to reinstall windows it is going to mess up the MBR some how ...

---

