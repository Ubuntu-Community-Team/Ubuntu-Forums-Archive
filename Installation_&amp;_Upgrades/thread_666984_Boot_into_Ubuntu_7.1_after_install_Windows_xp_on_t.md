---
title: "Boot into Ubuntu 7.1 after install Windows xp on top."
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by tnh5g3zpi7bzcev on 2008-01-13
HI. I've searched for this answer and either cannot find someone to explain it in plain English or their advice just doesn't work. I had Ubuntu 7.1 installed fine. I decided to install XP over the top to another partition. Now I can't gain access back into Ubuntu, only boots into XP.  This is how my partitions go:

sda1 = Linux root install
sda2 = Linux Swap
sda3 = Extended
sda4 * = XP NTFS  root install

I've booted into Live cd and typed some grub commands into terminal and after reboot, I still boot into XP without any choice to boot into my Ubuntu partition.

Can someone give some clear instruction on how to do this properly...And maybe this time it will work. It can't be THAT difficult :)

Thanks!

---

### Post by PmDematagoda on 2008-01-13
Use [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download") to install GRUB back onto the MBR, after that is done you can boot Ubuntu again and add the required entry for XP so that you can dual-boot properly.

---

### Post by tnh5g3zpi7bzcev on 2008-01-14
Nice! I got Ubuntu back. But now it only boots Ubuntu and I don't see windows xp as an option when I press on ESC during Grub boot. I can get into both using supergrub cd but...

Where in SuperGrub is the option to fix and show all operating systems within the grub boot options?

Or can I do this manually somehow?

Thanks!

---

### Post by beg4mercy on 2008-01-14
I am in the same position as this guy was, i'm gonna spend all today and tomorrow getting it so I can boot both the OS. I'll try this supergrub and I'll keep you posted if I can get XP to be recognised by grub..

---

### Post by PmDematagoda on 2008-01-14
If your Windows installation is located in sda4, then you should make an entry in menu.lst which looks like this:-
```
title		Microsoft Windows XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1
```

You can open the menu.lst for editing using:-
```
gksudo gedit /boot/grub/menu.lst
```

Add the entry for Windows at the bottom of the file and save the file.

---

### Post by tnh5g3zpi7bzcev on 2008-01-14
I edited menu.lst as you stated. Ok, at first I thought it wasn't working, but I went back into menu.lst and found that "hiddenmenu" option had somehow been uncommented (possible by SuperGrub) and I couldn't see the menu so it was still booting into XP. So, I commented it out, increased the hang time from 3 to 5, and now I can boot both OS.

Thanks PmDematagoda!

---

### Post by PmDematagoda on 2008-01-14
Glad to have been able to help:).

---

