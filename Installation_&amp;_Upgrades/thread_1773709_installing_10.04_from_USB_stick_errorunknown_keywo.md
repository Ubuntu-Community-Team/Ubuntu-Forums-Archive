---
title: "installing 10.04 from USB stick error:unknown keyword in configuration file: gfxboot"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by resero on 2011-06-02
Hello, my first question here!
What I've done (all this in ubuntu 11.04):
1) I downloaded ubuntu 10.04 LTS iso image using the bit torrent protocol, the link is from ubuntu.com.
2) I make a bootable USB stick using Startup disk creator.
3) booting from the USB I get:
*unknown keyword in configuration file gfxboot*
*vesamenu.c32: not a COM32R image*
*boot:*

it sticks in a loop repeating the last two lines.

Looking for help here and there, I found compatibility issues between older versions.[the fix ]("http://ubuntuforums.org/showthread.php?p=9948980") editing syslinux.cfg doesn't apply, the file is already like that.

NOTE:
* I already installed 10.04 in this desktop using a live CD and everything went OK.
* I already installed 11.04 in this desktop using this procedure (making the USB in 10.04) and everything went OK.

Thank you in advance.

---

### Post by sidzen on 2011-06-02
For some reason it is refusing to recognize Graphical GRUB.

See [this link]("https://heshambahram.wordpress.com/2010/05/05/live-usb-with-ubuntu-10-04-lts/")

---

### Post by resero on 2011-06-02
I already solved this issue, trying some old posts advices. 
In the prompt *boot:* I tiped *live* and the installer just started.

---

### Post by sidzen on 2011-06-03
> **resero said:**
> I already solved this issue, trying some old posts advices. 
In the prompt *boot:* I tiped *live* and the installer just started.
  Please mark it SOLVED, then!

---

