---
title: "Problem reinstalling Ubuntu 6.10"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by droogthib on 2007-04-08
So, hey!

Well, I'd like your help with a problem I'm having here:

I was trying to upgrade my Ubuntu 6.10 to Ubuntu 7.04 Beta, using the alternate cd of the Feisty Fawn. But after the upgrade, the system couldn't start. It was getting stucked at the loading and I was getting some message errors about the "/user" files when I tryend to start it in recovery mode.
So I though "well, I'll reinstall my Ubuntu 6.10 and everything is going to be alright", 'cause I have separated /home partition (it's hda5).
So, here is what's happening:
My hd has 40gb and is parted like this:
hda1 - Windows XP
hda2 - the partition for the "/" at Ubuntu
hda4 - swap
hda5 - /home

So at first I tryed to reinstall the Ubuntu Edgy Eft by the Alternate Cd, but it wasn't recognizing my partitions and it wanted to create new ones. So I burned the live CD and tryed to solve it by the graphical installer. It recognized my partitions, but at the time I chose the "hda2" as the "/" partition, it gave me the error saying that there was no partition chosen to be the "/" files. 
I tryed to format my hda2 partition, using "sudo mkfs.ext3 /dev/hda2" and it gives me the same error. I even tryed to format my windows partition, using "sudo mkfs.ntfs /dev/hda1", just in case...but I get the same error every time.
Oh yeah, and I checked the cd for defects before I tryed to use it...

Please...help me?

---

### Post by rugglesworth on 2007-04-08
You need to delete the old hda2 partition, you cannot reuse it.  So, once you launch the 6.10 graphical installer, you should perform the following actions:

1.  delete hda2 (Right click this partition and hit delete/remove/whatever)
2.  make a new partition in the empty space created.  format it ext3
3.  hit continue
4.  select the new partition to be /.  I think it will still be hda2, but I'm not sure.  Regardless, you should know it by its size.

Good luck

---

### Post by droogthib on 2007-04-08
Hey, thanks for the answer, brother.

So, is there a way to do it using the terminal? 'Cause the gparted is not showing my partitions. It shows only the entire HD (as /dev/hda) and it gives me only the option to create new partitions. Only after I choose to use the HD, at the graphical installation, they appear. But I can only select then to each function ("swap", "/" etc.). I can't edit them =/

So, I think I'll have to do it by the terminal...=/

---

### Post by droogthib on 2007-04-08
And, yeah, the partition has 9GB

---

### Post by droogthib on 2007-04-08
So, ahn, at the gparted, my hd appears as "not-alocated" (don't if this is the exact translation. Portuguese is my mother tongue...).
And the gparted does not allow me to edit it before it's formated

---

### Post by droogthib on 2007-04-08
Sorry for one more post, but it seems that there's no "edit" option.
So, I found the command fdisk. But it returns me the following error:
"Não foi possível abrir /dev/hda", which means, in english, that it couldn't open /dev/hda.
This is weird, 'cause I'm using live cd and I already could mount my home partition (/dev/hda5) and access all my files in there. I tested it and it worked.

---

