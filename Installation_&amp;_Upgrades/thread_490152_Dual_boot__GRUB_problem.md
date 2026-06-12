---
title: "Dual boot / GRUB problem"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by hans2 on 2007-07-02
Hi!

I've recently installed Ubuntu Feisty Fawn, together with Windows XP, on my new Toshiba Satellite Pro laptop. I don't seem to get GRUB to work properly.

The problem is, that when I start the computer, it doesn't load into GRUB, but a TOSHIBA boot screen shows, and the computer then boots directly into Ubuntu.

However, if I go into Ubuntu, and instead of shutting down the computer, choose Restart, the computer will shut down, restart, and then load into GRUB, just as I want. The TOSHIBA boot screen doesn't seem to ever show, instead the as soon as the computer restarts GRUB pops up. Now, exactly the same thing happens if I go into XP and choose Restart instead of Shut Down from there. Also, if I go the my laptop's BIOS settings, and then exit them, the computer will tell me it need to be rebooted, when it does, GRUB loads and everything works.

So put simply, if I shut down the computer, and then restart it (using the power button), the computer will boot directly into ubuntu, whereas if I, by any means, have the software do a restart GRUB will loads and everything will work just as I want.

I have one 120 GB HDD:
1st partition Windows XP NTFS, 15GB
2st partition swap, 2 GB
3rd partition Ubuntu root, ext3, 10GB
4th partition /home, ext3, everything that's left.

and I'm using IFS drive to share the 4th partition between Windows and Ubuntu.

Now, I have no idea about what causes my problem, or how to fix it. So I came here to ask for help and assistance.

---

### Post by louieb on 2007-07-02
Edit you GRUB configuration file. 
Bring up the run dialog by pressing ALT+F2 and enter 
```
gksudo gedit /boot/grub/menu.lst
```Look for the hidden menu option make sure it starts with a # (this comments the line out)
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```While your there check the value on the timeout line.  (heres mine) 
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        7
```See if that doesn't fix you up.

---

