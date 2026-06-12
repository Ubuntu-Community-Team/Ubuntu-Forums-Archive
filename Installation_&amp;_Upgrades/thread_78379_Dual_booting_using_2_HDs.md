---
title: "Dual booting using 2 HDs"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by Chackal on 2005-10-18
Well, I'll explain my situation. Some people asked me to install Ubuntu in an "old" PC (128Mbs ram), with the whole HD for it (10 Gbs more or less). Now, everything is installed but they ask me to put other HD with Windows 2000 already installed. So now I have two HDs, one with Ubuntu and other with Win2000 on it. I need dual-booting, but I have no idea about how to do it.

I would like you to tell me the way to do this. Maybe I have to reinstall and reconfigure Grub? Put it in the MBR? How? The better way is to reinstall Linux (I prefer not to do this)? I mustn't touch the files inside the Win2000 HD...

Thanks in advance, and sorry for my bad English :mrgreen:

---

### Post by jasmuz on 2005-10-18
Try to the installing routine, and when you get to the Install GRUB section, make it reinstall itself, after that just cancel that instalation. 

That should be all.

---

### Post by DutchR_PW on 2005-10-18
Make sure the Ubuntu HDD is the primary master (hda) and the Windows HDD the primary slave (hdb). Then edit /boot/grub/menu.lst (as root, sudo gedit /boot/grub/menu.lst) and add the following at the bottom:

title		Windows 2000
root		(hd1,0)
savedefault
makeactive
chainloader	+1

---

