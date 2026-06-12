---
title: "Stopping at splashscreen"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by noxmad on 2007-02-11
I've installed ubuntu 6.10 recently which went well (after using the alternate iso) but after rebooting and loading ubuntu with the grub loader the splashscreen seems to be loading with the bar slowing moving across but at about 95% the bar stops and it just sits there.
After 5 minutes still nothing. 
There seems to be some green dots that appear when I press enter but after about 4 presses more do not appear.
I'm more or less a complete noob at linux (installed fedore core which led to problems with windows so I tried ubuntu out) and would much appreciate help with this matter.

---

### Post by noxmad on 2007-02-11
[quote=volksman]Sorry guy....my fix was posted by aberry5555...this worked for me...I'm on the liveCD right now... this could also be done at the grub boot loader....might wanna try removing the quiet splash from your boot string and see where your's craps out....



This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line.

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum![/quote]

I found this fix on the forums but the only problem is when i try and change the driver from ati to radeon, the xorg.conf file is read only and will not let me change it.
How do i get around this?

Maybe volksman the guy who posted this could help?

---

### Post by PatrickE on 2007-02-11
> the xorg.conf file is read only and will not let me change it.
How do i get around this?

Maybe volksman the guy who posted this could help?

Did you add the
[INDENT]sudo[/INDENT]
command?

Only
[INDENT]**sudo** nano /etc/X11/xorg.conf[/INDENT]
will allow you to change the xorg.conf file, since it's owned by root who has exclusive write privileges. (At the prompt type in your user password, and then  you have root privileges.)

Or did I misunderstand your problem?

Patrick

---

### Post by noxmad on 2007-02-11
I'll try the sudo commands cheers.

I presume the password it asks for is the one i entered as my user password alongside my username?

---

### Post by PatrickE on 2007-02-11
> I presume the password it asks for is the one i entered as my user password alongside my username?

You presume right :-D

But be careful with anything you do with sudo. I recommend to backup your xorg.conf before editing it (eg,
[INDENT]cp /etc/X11/xorg.conf ~/xorg.conf.backup[/INDENT]
will copy it as "xorg.conf.backup" to your user home directory.

P.

---

### Post by noxmad on 2007-02-11
> **PatrickE said:**
> You presume right :-D

But be careful with anything you do with sudo. I recommend to backup your xorg.conf before editing it (eg,
[INDENT]cp /etc/X11/xorg.conf ~/xorg.conf.backup[/INDENT]
will copy it as "xorg.conf.backup" to your user home directory.

P.

I tried to make a backup but cannot be too sure if it worked :lolflag: 
But thankyou so much, I finally got ubuntu working and must say it looks sexy ^_^
Been trying to get ubuntu to work for 6 hours with problems installing and then getting it to run but finally the pain is over \o/
Now to get the sound working.

---

