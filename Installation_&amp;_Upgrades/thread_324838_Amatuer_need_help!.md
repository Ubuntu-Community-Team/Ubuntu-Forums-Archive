---
title: "Amatuer need help!"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by yiannis_t on 2006-12-24
HEllo there! I m a new member of this incredible community and a newcomer to the (k)ubuntu distribution..

As i have never worked with linux (only on vmware for a week to check the features..!)and how to install them i would really apreciate it if you could help me install this distribution to my pc..Please any guidance would be wellcome! :D 

As you assume i m using windows.. :rolleyes: And i m not very happy with it!!!

I have recently bought a new hard drive and i intend on installing linux on it! what are the steps that i should follow to install it..?
The first for example would be:
1) to plug the hd! :) 
2)..

Would it be better if i unplugged the old disk and boot directly from the new one?:confused: 

p.s : I have not plugged yet .....
Thank very much in advance!  :mrgreen:

---

### Post by DirtDawg on 2006-12-24
Actually, you got the first step wrong! :D

It's like this:
1) read [Asiyu's legendary guide]("http://www.psychocats.net/ubuntu/index")
2) install hard drive
3) see 1 for further details

---

### Post by taurus on 2006-12-24
Plug in the second harddrive.

Put the LiveCD in the drive and boot from it.

Click the Install icon to install it.

Tell the installer to use the entire second harddrive (make sure of that or it will wipe your XP off from the first harddrive).

Install GRUB (bootloader) on the MBR so it would allow you to boot Ubuntu and XP.

Keep yourself busy for about 20 minutes and you can remove the CD and boot directly to Ubuntu...

---

### Post by yiannis_t on 2006-12-24
So it is really so simple!!! Ubuntu really is the best!!
Sorry for the stupid(maybe) question taurus but the grub is installled during the installation by itself or should i do something?what is the MBR?

Thank you for your really descriptive answer.. ;)

---

### Post by taurus on 2006-12-24
When you get to that screen, it will ask you where you want to install GRUB so make sure you pick MBR (Master Boot Record) or /dev/hda or (hd0).

Just follow the directions on the screen and you should be good to go.

---

### Post by yiannis_t on 2006-12-24
Thanks a lot pal for your immediate answer!! I 'll definately try it when i go back to my house!!
That way  i will be able to choose where to boot from???via some menu or something?
And something LAST !! It won't be necessary to unplug the master disk in order to install to the second drive linux,uh?

Merry Christmass! :D :D

---

### Post by taurus on 2006-12-24
Don't unplug anything or else GRUB won't find your XP.  Leave the first harddrive (XP) as a master drive and install Ubuntu on the second harddrive, slave...

---

