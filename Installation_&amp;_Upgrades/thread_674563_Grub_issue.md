---
title: "Grub issue"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by simmba on 2008-01-21
Ok so here is the deal. I was trying to install Ubuntu onto my external hdd. I popped in my live cd and rebooted, nothing new to me at this point. I made sure to select my external hd and i do the rest as normal. after i complete the install i wanna make sure everything went right. I turned the machine off and i unplugged the hd. I turned on the pc (an xp only machine) and it says grub error 21. i believe it was 21. I didnt want grub to install onto the machine at all can anyone help me remove grub?

---

### Post by torgrot on 2008-01-21
Boot off of the Windows CD select recovery console at the prompt type FIXMBR, that will put the Windows MBR back on your hard drive.  You will need to instal grub to the external drive.

torgrot

---

### Post by simmba on 2008-01-21
Alright thanks im gonna do that in just a few minutes. can you help me out on installing grub to external?

---

### Post by torgrot on 2008-01-21
I have never done that so I will defer to others more knowledgeable than I am.

torgrot

---

### Post by Smbrandes on 2008-01-21
I would highly recommend making a supergrub disk. google it. Anyway, it is pretty useful for such things.

---

### Post by simmba on 2008-01-21
Ok thanks for the help guys and I will look into that super grub.

---

### Post by torgrot on 2008-01-21
Check out this thread in the forum [http://ubuntuforums.org/showthread.php?t=80811&highlight=Grub+usb+drive](http://ubuntuforums.org/showthread.php?t=80811&highlight=Grub+usb+drive)
There are instructions for creating a bootable USB drive with Ubuntu.

torgrot

---

### Post by rosegarden78 on 2008-01-21
I would try backing up your data from the LiveCD.  Then clean install or repair Windows - my XP disc has an option to reinstall old installation.  Then clean install Ubuntu.

---

