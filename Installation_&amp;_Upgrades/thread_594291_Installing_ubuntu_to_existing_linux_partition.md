---
title: "Installing ubuntu to existing linux partition?"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by tejvenim on 2007-10-27
How do I overwrite the current linux partition with ubuntu?

Primary partition windows xp, mbr points to windows xp

Secondary partition fedora partition

Fedora has an option that allow me to install boot loader in first sector of linux partition, so i install fedora boot loader into first sector of fedora parition because I don't want fedora to mess with my windows xp nor mbr. I edit boot.ini to enable me to load fedora with windows xp boot loader. Works perfectly.

Currently I tried ubuntu 7.10 live CD and like it. I hope to install it over my fedora.

My question: I want to install/overwrite this fedora parition with ubuntu 7.10, and i don't want to make any changes to windows xp nor MBR, i want the ubuntu 7.10 boat loader to be written to the first sector of this fedora partition.

How can I do it?

---

### Post by It_Was_Luck on 2007-10-27
Well considering you don't want to mess with your MBR, even though thats probably the easist, best way to go [can be fixed by simplying typing in "FIXMBR"] 

Anyway why don't you just overight the fedora partition with Ubuntu, then simply edit the boot.ini to load ubuntu with windows xp, just like you did for fedora.

Now I'm not familar with fedora but I think it would work the same, but on the other hand, I could be completely wrong...

hth

---

### Post by logos34 on 2007-10-27
If gutsy desktop install/live cd is the same as feisty, when you get to the 'Ready to install' screen click on[ 'Advanced' button]("http://img519.imageshack.us/my.php?image=feistydual18cv5.png") lower right and replace the default (hd0) with** (hd0,1)**, or **/dev/sda2** (or hda2 if that's how the installer sees it)

---

