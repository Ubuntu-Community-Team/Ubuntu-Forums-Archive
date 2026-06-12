---
title: "New Install 5.04"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by rosswil on 2005-07-21
Hi All
My problem is the install hangs immediately after installing everything and just before the GUI kicks in to allow the initial username and password. I have tried different HDs on 3 different computers and the install hangs every time. The install CD used   has already installed into a VMware virtual machine so I know it's OK.  I am reinstalling to a separate HD to compare speed between VMware and direct install.
Any help would be very much appreciated.
rosswil

---

### Post by uniko on 2005-07-21
Can you access consoles using CTRL+ALT+nbr 2 - 4? There should be some messages which should help determining the problem.

---

### Post by rosswil on 2005-07-21
thanks uniko,
when I say hang, that's exactly what happens. No access to anything. Could be compared to the BSOD but it is black. No cursor- no nuthin'.
A re-boot goes through the motions but when it gets to where it should put up the brown login screen it also hangs with the B(lack)SOD. No error message- no nuthin'.
Runs perfectly with VMware tho'.
rosswil

---

### Post by uniko on 2005-07-21
Sounds a bit like x server isn't configured right during install. Can you boot into rescue mode using either install-cd or from grub menu (does it show you grub menu at boot?). If you can, you could try to look at /var/log/  for xorg.log or /var/log/gdm/ xx.log 

Also try changing the xorg.conf driver to vesa. (/etc/X11/xorg.conf). Then try startx to get GUI.

Hope this helps.

---

