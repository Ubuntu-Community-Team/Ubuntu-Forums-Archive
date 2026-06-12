---
title: "Ouch!  Update kernel broke 10.4 today!"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by rsgrimes on 2011-01-26
Hi,

The graphical update manager suggested I update my Ubuntu 10.4 today, and I noticed it included a new kernel.  I let it do its thing, and rebooted when prompted.  Now, the system boots normally, and allows me to log on as always.  But, when the logon prompt is removed, all that is left on the screen is the background.  No menu bar at the top, no task bar at the bottom, and nothing from my desktop shows up.  Right-clicking does not bring up any context menu.  Nothing I try with the keyboard or mouse does anything; seems to have hung somewhere after the login credentials have been accepted, but before the Desktop and menus have been set up.

What can I do?  I can't even open a shell to poke about a bit!

Thanks!
-Bob

---

### Post by rsgrimes on 2011-01-26
I should perhaps emphasize that I was not upgrading from a previous version; I was attempting to update my existing 10.4  install.

---

### Post by plucky on 2011-01-26
Can you boot the previous kernel from the GRUB Menu?

> No menu bar at the top, no task bar at the bottom, and nothing from my desktop shows up. Right-clicking does not bring up any context menu.

What does ALT+F2 open?

Or ALT+F1

---

### Post by rsgrimes on 2011-01-26
On this install (under VMWare) I do not see the Grub menu, so I cannot try the previous kernel; the system simply comes up to the graphical (Gnome) login screen.  How do I get the grub menu to display during boot?

When should I hit Alt-F2 or Alt-F1 to answer your other questions?  Do you mean during Grub?  Once the desktop background has been shown, nothing happens when I hit them.  

Thanks!
-Bob

---

### Post by davidmohammed on 2011-01-26
when booting, press and hold the shift button - your grub should be display listing all the kernels available.

---

### Post by rsgrimes on 2011-01-26
davidmohammed, thanks!  I got the Grub menu now.

plucky: Okay, here is what I get in the Grub menu

```

Ubuntu, with Linux 2.6.32-28-generic
Ubuntu, with Linux 2.6.32-28-generic (recovery mode)
Ubuntu, with Linux 2.6.32-27-generic
Ubuntu, with Linux 2.6.32-27-generic (recovery mode)
Ubuntu, with Linux 2.6.32-26-generic
Ubuntu, with Linux 2.6.32-26-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

```The two most recent kernels (-28 and -27) do not work, but -26 does - I get the menu and task bars after logging in.  Note that these were normal, as opposed to "recovery" mode.

So I was just about to ask you, what now?  But in documenting the above, I decided to try the -28 recovery mode, and was able to get to the command line login prompt, as opposed to starting Gnome.  When I logged in that way, I got an error message from proprietary driver that indicated a problem, and entered an infinite loop waiting for the device!  So it was my fault; on Monday, I had tried to get this to load automatically on login, but it didn't work.  (I cannot explain why that didn't cause today's problem then, but eliminating the offending command from my .profile allows everything to work.

Still, you two helped me to find and fix my problem, even though it was not what I thought it was, so you both earn a very hearty "Thanks!!!"

-Bob
:oops:

---

