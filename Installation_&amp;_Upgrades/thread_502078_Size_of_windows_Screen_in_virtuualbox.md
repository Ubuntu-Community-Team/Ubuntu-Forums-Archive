---
title: "Size of windows Screen in virtuualbox"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by ali780 on 2007-07-16
Hi
I have installed window on virtualbox in Ubuntu 7.04. But the WindowsXP screen is small. How can I increase the size?
Thank you

---

### Post by grahamt on 2007-08-17
You have to install the Guest Additions but there's a specific way to do it or else you'll lose the mouse pointer.

1) Click Install Guest Additions... from the Devices menu of the virtual machine window once you've got the guest up and running and logged in.

2) Open a Terminal window.

3) Run: sudo dpkg-reconfigure -phigh xserver-xorg  (you will be asked for your password)

4) Select the screen resolutions you would like to use from the list by hitting the spacebar.  You can leave the display driver as vesa.  We'll change that next.  Tab to Ok and click.

5) Run: sudo aptitude install build-essential linux-header-`uname -r` (That's the backtic (`) symbol)

6) Run: sudo sh /media/cdrom0/VBoxLinuxAdditions.run all  

7) Close the Terminal window

8) Restart the Xserver and log back in

You should now be able to select the additional resolutions from System > Preferences > Screen Resolution

---

