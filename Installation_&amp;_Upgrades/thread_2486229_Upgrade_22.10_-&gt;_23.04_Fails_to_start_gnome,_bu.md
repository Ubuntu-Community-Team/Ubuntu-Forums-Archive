---
title: "Upgrade 22.10 -&gt; 23.04 Fails to start gnome, but has updated the base linux dist"
date: 2023-04-23
forum: Installation &amp; Upgrades
---

### Post by gfmoore on 2023-04-23
Spent all day on this and not getting anywhere.

So I am using a HP Proliant Microserver Gen 8, but had loaded 22.04 desktop, This I upgraded to 22.10 a few weeks ago with no issue and this am was asked to upgrade to 23.04. This seemed to get stuck and I get no gnome display desktop. All I get is a blank screen with a flashing underline cursor. I know this because the server has an app called ILO 4 which shows what is happening on the server and acts like a virtual monitor attached to the server. This is no responsive to keyboard strokes

Now I had set up to run headless and connected via Windows (10) rdp using autologin. 

Now no gnome desktop, just a blinking horizontal cursor.

I can ssh into the server and by running a start (tiger) vnc script I can use RealVNC client to get a desktop.

Trying to force rdp to be on and set the password meant that at one stage I did rdp into a desktop, but this crashed. I have attached a (vga) monitor and mouse keyboard to the microserver, but cannot get any desktop screen, just the underline cursor.

The way that this system works means that I use an internal usb stick to load ubuntu 22.04 to display grub menu which then boots Ubuntu 23.04 which is on an ssd. I have sudo update-grub so it can now see the new os so this is working.

The system during boot does display agraphical ubuntu login screen, but jumps straight into a lot of Linux bootup code. I don't get to a login screen and I don't know if it is still auto logging in or not. I have edited sudo nano /etc/gdm3/custom.conf to manually turn off autologin. I have fairly sure it is not using Wayland, but not getting a screen other than ssh I don't know for sure. echo $XDG_SESSION_TYPE shows X11 from the vnc screen. By the way this fails at first with a snap something gone wrong screen...

I've looked at the xorg log and I can see a failure:
   147.115] (II) VESA: driver for VESA chipsets: vesa
[   147.115] (EE) 
Fatal server error:
[   147.115] (EE) parse_vt_settings: Cannot open /dev/tty0 (Permission denied)
[   147.115] (EE) 
[   147.115] (EE) 

I don't know what this means, why would it want to open a tty?




I just don't know what else to try. I am now thinking of trying to reinstall using a usb stick.


Thanks, Gordon

---

### Post by gfmoore on 2023-04-24
So gave up and reinstalled Ubuntu 22.10. After a day, all (mostly) working again - I'm so glad I made notes when I first installed.

As an extra bit of info, creating a Ubuntu 23.04 usb boot drive, failed to boot!!!

---

### Post by symdeb on 2023-05-01
> **gfmoore said:**
> So gave up and reinstalled Ubuntu 22.10. After a day, all (mostly) working again - I'm so glad I made notes when I first installed.

As an extra bit of info, creating a Ubuntu 23.04 usb boot drive, failed to boot!!!

Took me few hours, but my solution is, PURGE (!)  the NVIDIA drivers. Then install Gnome desktop.

---

