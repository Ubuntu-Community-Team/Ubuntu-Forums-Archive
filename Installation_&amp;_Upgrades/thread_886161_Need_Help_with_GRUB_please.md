---
title: "Need Help with GRUB please"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by BDubs588 on 2008-08-10
Ok, so I was looking to add space to my Ubuntu partition.  I booted my windows partition and used partition magic to change the partition sizes.  In the middle of partitioning, I got an error about some floppy disc (I don't have a floppy drive) and it aborted the process.  When I went to reboot, I got GRUB error 17.  I'm at a loss of what to do.  I'm using a different computer right now because I don't have internet access on my machine that I was partitioning on.  I want to keep both the windowsXP and linux partitions but I don't know what to do.  Please help:confused:

---

### Post by bouncingmolar on 2008-08-10
> **BDubs588 said:**
> In the middle of partitioning, I got an error about some floppy disc (I don't have a floppy drive) and it aborted the process. 

That doesn't sound good!

Is there anything still on the hard drive after aborting??  If your partition abortion wrecked your info on your drive you're between a rock and a very hard place.

---

### Post by werries on 2008-08-10
error 17 is usually from a device being requested and its not accessible or found.
Laymans terms, its pointing to the wrong partition and you will have to update grub. This can be done with the live CD. 
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub, if you don't know, use "find /boot/grub/stage1"). (you can also type "root (" and then hit tab, it will show available options)
5. Type "setup (hd0)", to whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by ricolinux on 2008-08-10
I have a similar problem. I was in the middle of doing a normal update when mynsystem froze and I restarted and now I get the following message "Grub 1.5 error 17"
Itried using the Live CD and using terminal when I inquiry for stage1 it responds no such file or commad.
I need to get back to Ubuntu 8.04 Because that'z my main machine it has my e-mail and Samba settings and I use it as server depositary for my Win XP  files. I;d hate to re=install Hardy  over I started with Dapper  and I have been upgrading ever since to the latest 8.04+.
Any advice I should aprecciated very much.
I am an UBUNTU evangelist to all my friends here in my neck of the woods (Sab Francisco BAy Area)
Thanks

---

### Post by falcon61102 on 2008-08-10
> **ricolinux said:**
> 
Itried using the Live CD and using terminal when I inquiry for stage1 it responds no such file or commad.

When you use the LiveCD, make sure that you mount you internal HD before attempting to use GRUB find, otherwise it won't be able to see your system files.

---

### Post by logos34 on 2008-08-10
> **falcon61102 said:**
> When you use the LiveCD, make sure that you mount you internal HD before attempting to use GRUB find, otherwise it won't be able to see your system files.

as counterintuitive as it may seem, / does not have to be mounted for the grub find command to work

---

### Post by falcon61102 on 2008-08-10
Well, I stand corrected... I know it's always helped for me in the past though.

---

### Post by werries on 2008-08-11
You need to use the Find command after the grub command, and use it inside of grub :)

---

