---
title: "installation on microsoft virtual pc issues"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by crackers8199 on 2007-01-29
i've tried installing ubuntu several times, and i've had the following issues:

1)  i never seem to get the option to install - every time i click start/install ubuntu, it just seems to start the live version but never give me the option to install

2)  when it runs the live version, the screen is so garbled that i can't do anything...i can barely make out the gnome desktop

what should i do?  i've tried both the desktop iso and the alternate install iso...

---

### Post by crackers8199 on 2007-01-29
it should also be noted that i have tried both 6.06 and 6.10, with the same results...

i've got 1gb of ram and an intel g965 integrated graphics chipset, if that helps too

---

### Post by mysticrider92 on 2007-01-29
I tried running Ubuntu in M$ Virtual PC on our family computer (Athlon 64 3200 and 1.5 gb of RAM) and couldn't really get past the boot screen. I would recommend [VMWare Player]("http://www.vmware.com/download/player/"), it is free and works quite well. There are many images availible for it, including multiple Ubuntu ones.

---

### Post by spd106 on 2007-01-29
Virtual PC doesn't support 24bit colour depth, so you have to change it to either 32 or 16bit and choose safe mode at boot. This should work okay on Dapper (6.06). However Edgy is rather more stubborn, I found the easiest way was to boot into single user mode, then edit the xorg.conf to use 16 bit default. Then **telinit 5**  to enter normal mode.

I have given a more detailed explanation [here]("http://ubuntuforums.org/showthread.php?t=294236")

---

### Post by crackers8199 on 2007-01-30
BAH, this thing doesn't like safe mode either apparently...

/bin/sh: can't access tty; job control turned off
(initramfs)

This whole ordeal is frustrating the hell out of me...I couldn't get FreeBSD working with my graphics card so I gave up on that, and was directed towards Ubuntu by a friend - now I can't get this working either.  This sucks.

Also, why won't this let me install the damn OS?  It keeps trying to run the live version, it never lets me try to install...

---

### Post by Motoxrdude on 2007-01-31
Why not try to use Vmware player instead?
```
sudo apt-get install vmware-player
```
You may have to enable the restricted repos.

---

### Post by spd106 on 2007-01-31
Also consider using the alternative cd, it doesn't have the live environment so it work better. It does take longer than the desktop cd though and you still have to change the vga mode at boot.

---

### Post by crackers8199 on 2007-02-04
ah well, now i got to the installation but it can't mount my cd-rom drive.  i can't seem to win.

---

### Post by Stewcort on 2007-03-17
I found my own answer her if it helps anyone else.

[http://arcanecode.wordpress.com/2007...-step-by-step/](http://arcanecode.wordpress.com/2007...-step-by-step/)

---

