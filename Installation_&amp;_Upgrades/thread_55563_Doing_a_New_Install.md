---
title: "Doing a New Install"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by cjoshuav on 2005-08-09
Well, my "play" install on 5GB has worked out so well that I'm getting a 100GB hard drive and I'm going to set up a genuine dual-boot system.

Here's my plan for the partitioning:

- 10GB for the WinXP partition (the OS, all my Windows productivity apps like Office, EndNote,  Dreamweaver, etc.) - NTFS

- 10GB for the Linux partition (the OS, all my Linux app's that are the equivalent of the above) - Ext3

- 5GB for the Linux swap file - Ext3

- 75GB for Windows Games, MP3's, all of my graphics, documents, etc... (this will be shared by Windows and Linux) - Fat32

I'm a little uncomfortable with making that large of a Fat32 partition.  I'm open to other suggestions.  I know I can fit my app's on a 10GB Windows partition, but I'm not sure about the Linux one.  I'm also thinking about making a straight 30GB partition for games (I review them).

I welcome your thoughts.

Joshua

---

### Post by fng on 2005-08-09
a side note : 
a swap partition doesnt need a filesystem. it has it's own partition type (82).

and 5 gb's for swap?
that's way 2 much
Normally you should reserve between 1x and 2x of your actual RAM for swap.

---

### Post by cjoshuav on 2005-08-09
2x actual RAM puts me at 4GB.  I don't use any swap file at all in Windows, but my understanding is that Linux memory management isn't as good and that I'm better off creating a swap partition.

With 2GB of RAM can I get by without a swap partition?

Joshua

---

