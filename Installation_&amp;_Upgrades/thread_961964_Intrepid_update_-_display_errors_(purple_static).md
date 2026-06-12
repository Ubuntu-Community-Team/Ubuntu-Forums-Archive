---
title: "Intrepid update - display errors (purple static)"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by graham-cracker on 2008-10-28
I (attempted) to upgrade to Intrepid today from a fully updated Hardy.

I am now getting some very nasty display errors. As the xorg server starts up I get purple static, on the login screen I have some severe distortions (see attachment), when I am logged in I have a heavy amount of purplish static (see attachment).

I attempted to regenerate the xorg.conf file by running:
sudo dpkg-reconfigure xserver-xorg

But that didn't help. I have the following graphics hardware:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

Any ideas?

---

### Post by Pumalite on 2008-10-28
Go into Recovery Mode and try 'xfix'

---

### Post by graham-cracker on 2008-10-29
That didn't appear to change anything. What does xfix do?

---

### Post by graham-cracker on 2008-10-29
After some web searching and with the help of:
sudo lspci -v

It looks like sisfb (a required module for my graphics card) is not being loaded on startup.

A temporary fix was to:
Switch to a different terminal (Ctrl-Alt-F2)
Log in
Insert the sisfb module (sudo modprobe sisfb)
Switch back to X (Ctrl-Alt-F7)
Restart X (Ctrl-Alt-Backspace)

This appears to fix the problem (until you restart). If this works for you, than add sisfb to your /etc/modeules file so that it is inserted on boot like so:
Open a terminal
type: sudo nano /etc/modules
Add the following line to the end of the file:
 sisfb
Save and exit (Ctrl-X)
Restart and see if it works.

---

