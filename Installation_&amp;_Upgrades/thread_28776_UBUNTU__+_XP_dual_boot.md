---
title: "UBUNTU  + XP dual boot?"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by tekno on 2005-04-21
I am trying to boot ubuntu + XP ... i got my Windows on /dev/hda5 ... and UBUNTU on /dev/hda1 is it posible DUAL BOOT? 

thanks

---

### Post by dataw0lf on 2005-04-21
.... What exactly are you asking?  Does it show XP on your GRUB menu?

---

### Post by janesy on 2005-04-21
its very easy, all i did is have an existing XP install on my 200gb drive, use partition tragic and creat a linux partition and when i was installing ubuntu it asked me to install "grub" on the master boot record. 


now i get some options on which OS to boot.

---

### Post by tekno on 2005-04-21
NO i don't have the XP option in the GRUB

---

### Post by gizmospc on 2005-04-23
I am also trying to do this with winXP pro ubuntu 64 bit, with XP on an existing 120gb hd and ubuntu on a 20gb hd.  Every time I've tried this I end up getting no option to install any sort of OS selector, and I have to use the repair console of XP to restore the master boot record.

---

### Post by crane on 2005-04-23
Did you install XP first? 
You have to install XP then ubuntu (or Linux)

After that if you still have problems or if you have allready done this , post try looking at ( and posting) you /boot/grub/menu.lst file.

---

### Post by gizmospc on 2005-04-23
XP was installed first on the 120gb drive.  I set the 20gb to slave, installed it, and began loading ubuntu.  I successfully formatted the 20gb drive (also seeing and not destroying thankfully the windows 120gb drive), and let ubuntu install.  When I reboot there is still no option for OS selection, just grub loading and booting ubuntu.  I tried interrupting the grub (where it says press, i think F2, to see a menu) and found the different linux boot options, but couldn't figure out how to get xp added to the list.  

I will try posting the command you mentioned a bit later when there's time.

Another thought... does this have to do with ubuntu being the 64 bit version or does this not matter?  Just a thought...  :-k

---

### Post by tread on 2005-04-23
Here is my grub entry:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

You should fine it in /boot/grub/menu.lst

Also, shouldnt windows xp be hda1? I dunno if Windows XP can handle booting from say hda5 .. since Microsoft never really intended it to be dualboot?

---

