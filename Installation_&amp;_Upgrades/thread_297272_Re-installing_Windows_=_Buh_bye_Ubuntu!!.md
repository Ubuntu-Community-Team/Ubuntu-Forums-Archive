---
title: "Re-installing Windows = Buh bye Ubuntu?!?!"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by Tamacracker on 2006-11-10
I dont know where exactly to put this thread, but here's the situation. If this needs to be moved, please do so.

Well basically I have a 20gb Hard drive that's specifically for my Ubuntu operating system and I have a 160gb hard drive that's specifically for my Windows XP. 

The Windows XP HD is the Primary Master

The Ubuntu is the Primary Slave


Ok last night my Windows XP crashed, and I didn't really care about it, so I re-installed my Windows XP (clean install) but now that I have done this, I cannot get my Operating system selection screen back (GRUB?) So now it only loads up Windows XP. 
I then made my Ubuntu HDD load first and XP load second, and it just says there's no operating system. 

So my question to you is... is there any possibility that I can get my Linux to boot up ever again? Or am I better off just wiping the Ubuntu OS off my HD and clean install again?

---

### Post by Tamacracker on 2006-11-10
Bumping it. Gotta run to the store real quick.

---

### Post by Angry on 2006-11-10
What I have done is booted from the live-cd and setup grub from there.

from the terminal (anything after a # is a comment, so do not include in command line:

sudo grub
find /boot/grub/stage1
root (hd0,1) # listed from find
setup (hd0)
quit

then reboot - this should setup grub as your boot loader.

(caveat: I am relatively new to linux as well, however, being as I have done this about 5 times now, I am pretty confident in this application...)

---

### Post by Tamacracker on 2006-11-10
So from the Live CD... it'll fix my problem? Actually... gonna try that right now :)

Thanks bro!

---

