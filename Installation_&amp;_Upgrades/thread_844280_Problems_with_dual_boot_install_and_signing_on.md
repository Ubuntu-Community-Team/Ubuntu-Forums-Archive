---
title: "Problems with dual boot install and signing on"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by MWK-ATL on 2008-06-29
Okay, need lots of help, sorry if this post is too long. . . .

I installed Ubuntu last night as a dual boot with Windows XP and I'm having quite a few problems.  For starters, when I boot up (installed first on computer by way of ubuntu's "windows install", and when that failed, I created a live CD, checked the integrity, etc. and everything was fine with the CD)it gives me the username screen, then the password screen, then disconnects and reloads to the username screen.

Over and over and over.

I can get into Ubuntu by going into a GNOME session, but honestly, I have no idea what GNOME is (I promise I've really been trying to learn, but I'm not great with computers). . . .


I thought maybe if I uninstalled an re-installed, that might work better (just did a destructive system restore on the computer and have nothing stored on it, so I'm not afraid of losing info), but it appears that I've installed Ubuntu to an external hard drive I've connected to the computer.  I didn't mean to do that, but didn't think it was a problem, except now I see that I must have the external HD turned on to boot the computer into either Windows XP or Ubuntu, and I don't like that set-up.  So I went in to do a system recovery, wipe out Ubuntu with FIXMBR, but it's giving me a warning that I could make my hard drive inaccessible.  I'm assuming that means the external where I think I've got Ubuntu installed (it's a 120 GB external, and when you check properties it says it only has 4 GB available, so I'm confident that's where Ubuntu is).  Do I need to do a system restore and run the risk of losing the external?  If there was some way to fix Ubuntu, I'd be willing to try.  I've got other issues as well, mainly that Ubuntu won't connect to our wireless network (using a Linksys USB adapter, since there's no cable in the office for the cable modem) but I need to get this install issue taken care of first.  Sorry for the long post, I'm sure you'll need more info!!!

---

### Post by Pumalite on 2008-06-29
Fix your Windows MBR and then boot a Live CD and (with the external connected), post:
sudo fdisk -lu

---

### Post by MWK-ATL on 2008-06-29
Could you explain that to me in the most simple how-to terms possible?  I'm not kidding when I say I am out on a limb here.  Thanks!

---

### Post by Pumalite on 2008-06-29
Do you have an installation disk for XP?

---

### Post by MWK-ATL on 2008-06-29
No, no Windows Boot Disk; it was an OEM install on the computer.  I can do a complete destructive system restore and it will reset Windows to 'first install' settings.  Is there any way to completely remove Ubuntu and take the computer back to factory settings without the Windows boot cd?

---

### Post by Pumalite on 2008-06-29
Use Super Grub to restore the MBR to Windows:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by MWK-ATL on 2008-06-30
Took your advice, used Super Grub and fixed the MBR (at least I think!), and did a system restore on the computer.  Looks like all the system settings are working fine, but my 120 GB external HD has been reduced to 5 GB, apparently that's where I was storing and booting Ubuntu from.  Any idea on how to clean that up?

---

### Post by Pumalite on 2008-06-30
Use Gparted Live CD and fix your partitions:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

