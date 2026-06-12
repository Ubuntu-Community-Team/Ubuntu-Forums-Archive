---
title: "NooB help with 8.04 fixes"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by somguy2u on 2008-05-01
i have been using 7.10 since christmas flawlessly,and when i tried to upgrade the installation froze on me.  

I rebooted and used recovery mode to finish the install using:
> sudo dpkg --configure -a

once this was completed i rebooted.  the Grub menu now shows two versions of 8.04 with their respected recovery consoles along with the windows boot options.

either one that i chose had errors in the xserver and i followed the on screen instructions to fix it, rebooted (still have the crazy GRUB problem).  i get to the login screen fine, enter the information and it logs in.  screen goes white, no icons, no bars, nothing.  somehow i guess a lot of my settings remained, i hit the Email button on my   keyboard and evolution comes up, same with the audio key, audacious comes up, and all the other things.  but resolution is a very small number and there are no icons, no menu's and i have no idea what to do from here.

i searched but i couldn't find anyone that had a similar problem, if i wasn't searching for the right thing, as i have no idea how to explain this in the search bar,if you could post me to the link i would appreciate it.  i'm frustrated.  any help? :confused:

---

### Post by Pumalite on 2008-05-01
Post:
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by somguy2u on 2008-05-01
i tried this and it didn't fix any of the problems :(

fdisk -l:

divice: /dev/sda1
Boot: *
Start: 1
End: 20022 
ID:7
System HPFS/NTFS

it reads off more after that


SBD1 is tarred thats the HPFS/NTFS
SDB2 ID 83  linux
3    ID 5  Extended
5    ID 82 Linux swap / solaris

---

### Post by somguy2u on 2008-05-01
so i think i lied

the dpkg --configure -a didn't work

i tried it again and the last line is "too many errors, stopping"

it didn't download anything...

---

