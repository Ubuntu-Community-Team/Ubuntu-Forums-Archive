---
title: "Beta Black Screen IBM Thinkpad R31"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2008-10-07
Beta, Gnome, & X windows result in Black Screen on my IBM Thinkpad R31. Boot proceeds normally through splash, X initiates O.K., get orange screen with pointer, disk activity as Gnome loads, then black screen.  Keyboard won't work, nothing except power off..

- Alpha 5 (not updated) runs fine so hardware is O.K.  This is a dual boot with the Alpha 5 plus the test Beta.
- Beta CD Live CD runs & installs on my Compaq Presario so CD is O.K.
- Beta will even install on the IBM Thinkpad provided I do the install from the initial screen, which doesn't use Gnome.
- install is updated to today, 10/7/2008, with kernel 2.6.27-5.8
- Xfce4 runs O.K., this is what I'm using on the Beta to make this entry

Looking at errors and logs, see bug 277344, there is xsession-errors:

x-session-manager[5567]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'

If I do a "find", there it is:
ls -l /usr/bin/gnome-wm
-rwxr-xr-x 1 root root 4087 2008-09-23 04:18 /usr/bin/gnome-wm

What's Xwindows problem that it can't find gnome-wm? Is gnome telling it to look somewhere else?

Thanks, Jerry
..

---

### Post by tjansson on 2008-10-16
I have the exact same problem on a Thinkpad X30 running a fresh 8.10 beta install.

---

### Post by DevL on 2008-10-21
Clean install of 8.04 followed by an upgrade to 8.10 yeilds the same result on my Thinkpad X30. Ubuntu starts normally up until the login screen. After entering my credentials, black screen with the mouse pointer just sitting there looking sheepish...

---

