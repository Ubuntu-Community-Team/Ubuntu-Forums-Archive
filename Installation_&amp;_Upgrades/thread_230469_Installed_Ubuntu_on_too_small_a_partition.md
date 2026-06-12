---
title: "Installed Ubuntu on too small a partition"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by rempel on 2006-08-06
Help me please - I have everything set up and don't want to start over.

I installed Ubuntu on a 4GB partition. At first I had 1.5GB free but now it's 98% full. I keep all my files on a different partition, it's just the system and the applications I have installed with synaptic.

My question is whether I can resize the / partition without wiping out my Ubuntu installation, or if I can migrate some large folder onto another partition. Resizing would be my preferable option.

It's a 74.56GB drive, starting with a 6GB NTFS partition, then two 32GB FAT32 partitions for sharing data, and then finally the remainder for Ubuntu. I know I should have left more, but this is my situation now.

Please help!

---

### Post by rempel on 2006-08-06
By the way, I have an identical drive that I can back everything up with. I'd also be open to re-installing everything on the other drive, provided I can move all my Evolution data over - is there a way to do this?

---

### Post by jimmygoon on 2006-08-06
I'm not good enough (:P) to tell you how to do this but you can image your partition onto another drive and then remake the Partitions and image it back I think...

... or you can try to use a live disc (gparted or sysrescuecd) and resize the ext3 .... I think its supports resizing ;)

---

### Post by kebes on 2006-08-06
You can create an image of the Linux partition (and the other partitions) onto your second drive, then change the partition sizes and reload the images into the right spots. A linux program called "partimage" allows you to do this (similar to the "Ghost" program):
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

The "System Rescue CD" is a LiveCD that has partimage on it, along with a bunch of other useful system tools. It might also help:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)


You didn't mention what version of Ubuntu you're using, but if it's a recent one (Dapper, i.e. 6.06) then you can boot back into the install CD, and use the partition manager (go into the "install" process, and complete the first couple of steps) to change things.

The partitioning section of the installer has an option to "resize" partitions. This will, in principle, let you do what you want: you can resize all the partitions (and even move them) so that Ubuntu now has enough space. If it works, all the data in the partitions will be maintained and you won't have to do anything else.

However resizing partitions is always dangerous! Be sure to BACK UP YOUR DATA!


So if I were you, I would back up my data, and then try resizing. If that doesn't work, then just reformat your first drive (with a better space allocation), reinstall everything, and copy over your data.

---

### Post by kebes on 2006-08-06
Just an afterthought: when I said "reinstall and copy over your data" it's worth noting that nearly all of your "personal" settings (about how programs behave, etc.) are stored in your "home" directory. Typically every program in Linus creates a directory in "/home/username" ... the directories are hidden because they start with a period, ".", but you can see them by going:
$ ls /home/username/ -laF
You should notice directories like ".kde" and ".mplayer" and so on. If you save everything in your home directory (including these hidden settings directories) and then restore them after a reinstall, nearly everything will be back the way it was before.

I'm not sure about Evolution specifically (I don't use it), but I suspect that it stores its settings in:
/home/username/.Evolution/

Hope that helps.

---

