---
title: "uninstall ubuntu 7.10 on hp compaq w/ win xp"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by shellbo on 2008-01-13
i installed ubuntu 7.10, 2 days ago.. lots of problems so far
i have also win xp installed, both running on hp compaq nx6310 laptop
i would like to uninstall ubuntu, restore the hard disk space on xp to what is was prior to installing ubuntu, and start over fresh
i will reinstall ubuntu, folks, i just want my machine back to what is before i give it another go
can someone please list the steps i need to take in order to do this successfully
i'm a newbie, and i must admit that i am having trouble with some of the language 
so after a day's searching, i'm posting this message in hopes that i can finally make sense of everything i've found so far
thanks in advance

---

### Post by logos34 on 2008-01-13
Restore windows bootloader using XP install CD (>recovery console>**fixmbr**) or Super Grub Disk.

Boot from ubuntu live cd.  Go to system>admin>gnome partition editor, or

sudo gparted

delete ubuntu partitions.  Then resize/expand XP partition back into the empy space.

---

### Post by shellbo on 2008-01-13
thank you very very much:)

---

### Post by logos34 on 2008-01-13
> **shellbo said:**
> thank you very very much:)

ok, sure thing.  Hope to see you back here soon.  Sometimes it can be frustrating at first trying to migrate  from windows to linux, but if you stick with it you'll find a way.  I transitioned by fits and starts (I started out on Suse)...it always seemed one thing or another didn't work quite right, or there were windows-only programs I just couldn't leave behind.  But one day it just occurred to me that there were workarounds and replacements for everything--most of the time BETTER replacements.  Who needs iTunes?  Do you really need MS Office, or can you instead use OpenOffice? Adobe Photoshop?  And on down the list.  Games is the one thing you need windoze for.  I don't play games, and the only reason I still run XP (x64) dual boot (beside it being a free trial version--I haven't paid for it in over two years) is the better to help others get away from it!  It's like kicking the smoking habit.

---

### Post by shellbo on 2008-01-14
all right, so i thought i had this time, but apparently not. 2 main issues:
1) i don't have gnome partition editor in the installed version already on my computer- will the livecd necessarily have it?
2) once i've deleted the ubuntu partition, how do i resize/expand the XP partition?
thanks.

---

### Post by Partyboi2 on 2008-01-14
Yes, you will need to use the ubuntu live cd or [gparted live cd]("http://gparted-livecd.tuxfamily.org/") 
To resize xp, after you have deleted ubuntu, highlight the windows partition and click on resize/move then expand it to how big you want. then press "apply"

---

### Post by shellbo on 2008-01-14
so i'm actually resizing the xp partition from ubuntu?
before i boot xp again?

---

### Post by Partyboi2 on 2008-01-14
You will be resizing the partition from the live cd which is either the ubuntu live cd or the gparted live cd, depending on what one you are using
before you boot windows.

---

### Post by shellbo on 2008-01-14
thanks and wish me luck!

---

