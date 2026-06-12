---
title: "Install then transplant"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by Harin on 2007-04-13
Alright guys, here's how this story goes:

First, I'm fairly certain I've read everything I could find on this forum about installing without a cd drive, none of them worked so I'd like to try this method.

Just to clarify, I'm trying to install ubuntu 6.10 onto a computer that lacks a cd drive, cannot boot from usb or the net, and that no longer has an operating system on it (xp died the day after the cd tray lost a cog, I added in a new cd drive but I guess the bios doesn't recognize it.) I can boot from floppy but of the three other computers I have none of them have a floppy drive, which means I can't make any disks for the dead one, I don't mind buying an external one if it'll help me resolve this.

I just tried installing ubuntu onto the hard drive by transplanting it into a newer computer and then putting it into the dead one. The installation completes succesfully and runs fine on the newer computer but when I put it back in the dead one after the ubuntu loading screen has run its course, the display goes all funky, much like an acid trip at a hendrix concert must've been. I was wondering if there was a way I could load a bunch of generic video drivers or something during the install just to be safe, and hope the dead one picks one that works. 

Yes I realize I sound quite idiotic, but I've run out of solutions and although I'm not technologically retarded, I'm not exceptionally gifted either. Any help will be greatly appreciated.

Harin

Edit:

1. The newer computer has a nvidia graphics card, I'm assuming the installation install specific drivers to this? Is there a method for uninstalling the specific drivers and then installing generic ones after the installation but before putting it into the other computer?

2. I basically figured out what's wrong I think, I need to  configure i810 drivers from recovery mode (can't boot into the gui os, but this works) I have no idea how to do this.

---

### Post by kidders on 2007-04-13
Hi there,

Your added comments (re Nvidia drivers & what to do next) seem sensible. :-) The file you want to edit is at **/etc/X11/xorg.conf** ... you can read all about it all over the place. The most important thing to tweak is the "Driver" directive in the "Device" section of the configuration file.

For the sake of speed & sanity...[LIST]
[*]You should make small, incremental changes, and only tweak things you understand the effect of.
[*]Make liberal use of the contents of /var/log/Xorg.0.log ... when something goes pear-shaped, the end of it is often the most helpful part.
[*]Start test X servers simply by running **X**, rather than doing **/etc/init.d/**[?]**dm restart** (which does lots of stuff that's not necessary for testing).[/LIST]I hope that helps.

---

### Post by az on 2007-04-13
> **Harin said:**
> Alright guys, here's how this story goes:

First, I'm fairly certain I've read everything I could find on this forum about installing without a cd drive, none of them worked so I'd like to try this method.

Just to clarify, I'm trying to install ubuntu 6.10 onto a computer that lacks a cd drive, cannot boot from usb or the net, and that no longer has an operating system on it (xp died the day after the cd tray lost a cog, I added in a new cd drive but I guess the bios doesn't recognize it.) I can boot from floppy but of the three other computers I have none of them have a floppy drive, which means I can't make any disks for the dead one, I don't mind buying an external one if it'll help me resolve this.

I just tried installing ubuntu onto the hard drive by transplanting it into a newer computer and then putting it into the dead one. The installation completes succesfully and runs fine on the newer computer but when I put it back in the dead one after the ubuntu loading screen has run its course, the display goes all funky, much like an acid trip at a hendrix concert must've been. I was wondering if there was a way I could load a bunch of generic video drivers or something during the install just to be safe, and hope the dead one picks one that works. 

Yes I realize I sound quite idiotic, but I've run out of solutions and although I'm not technologically retarded, I'm not exceptionally gifted either. Any help will be greatly appreciated.

Harin

Edit:

1. The newer computer has a nvidia graphics card, I'm assuming the installation install specific drivers to this? Is there a method for uninstalling the specific drivers and then installing generic ones after the installation but before putting it into the other computer?

2. I basically figured out what's wrong I think, I need to  configure i810 drivers from recovery mode (can't boot into the gui os, but this works) I have no idea how to do this.

Yep.  Your video card is autodetected upon installation, but it is not autodetected if you change your hardware.

Boot into recovery mode (in the grub menu) and then run

dpkg-reconfigure -phigh xserver-xorg

then run

init 2

all should work fine after that...

---

### Post by Harin on 2007-04-14
Thanks for the replies guys, I tried the x11/xorg thing but it doesn't seem to work correctly for me, the command runs but opens up a gibberish filled screen. Az I tried your method, after I run the init 2 command it says that x window failed to open. the error it outputs is that "no screens were found". The details above it say that no valid modes were found and screens were found but none have a usable configuration. When modifying the xserver file, I selected i810 from the list and left the rest as default. The detailed xserver info says that a lot of font paths weren't found, it says to run the mkfontdir command (I don't know how to use this) and the rest is meaningless to me. I've left it open though, so if you guys need to know anything specific from there please let me know. Thanks again for all your help, I don't mean to be a bother, I'd just like this to finally work. Thanks again.

Edit:

I just tried a fresh install, and reconfigured the xserevr-xorg file from recovery mode, when I try to run the startx command, I get the following errors:

(ee) I810(0): No Valid Modes found
(ee) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by kidders on 2007-04-15
Hey again,

You need to take care that sensible values are provided for your screen/graphics card ... especially if you let Ubuntu guess them for you. When something breaks, my usual approach is to start basic ... *terribly* basic ... and once X starts to cooperate, get more adventurous.

So, perhaps you could start with a generic, low-resolution, low colour depth (and so on) setup, with no advanced features like GLX/compositing/etc. Make sure you have an idea of what everything you're telling X to do means. Xorg is terribly finicky, but once you can persuade it to start at all, you'll be almost done. From there, it's just be a matter of performance tuning ... making liberal use of CTRL+ALT+Backspace, and **sudo nano -w /etc/X11/xorg.conf** hehe.

Valid "modes" are usable screen resolution, colour depth (and perhaps refresh frequency) combinations. You might expect to see them specified this way (although there are other ways of writing them) ...

```
Section "Screen"

    ...
    ...

    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection

    ...
    ...

EndSection
```

---

### Post by mgmiller on 2007-04-15
> I added in a new cd drive but I guess the bios doesn't recognize it.

Check the jumpers on the new CD rom drive.  They are often shipped set to "cable select" and need to be changed to match your hardware configuration.  If the CD is on the same cable as your hard drive, set the CD jumper to slave.  If it is on a differenet cable from the hard drive, set it to master.  Your BIOS should now see the new CD drive.

---

