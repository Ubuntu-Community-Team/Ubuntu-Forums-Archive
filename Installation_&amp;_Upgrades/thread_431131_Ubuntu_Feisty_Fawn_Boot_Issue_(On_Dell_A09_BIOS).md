---
title: "Ubuntu Feisty Fawn Boot Issue (On Dell A09 BIOS)"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by AdHavoc on 2007-05-02
Okay, so here's the situation.  I have Feisty loaded on my laptop, and decided to put it on my Windows machine as well.  I burnt the .iso image using InfraRecorder, and verified that it worked using another machine.  However, I can never seem to get the CD to boot correctly.  It goes into the Ubuntu splash loading screen, and then freezes.  Occasionally, my BIOS even fails  to recognize it (I have the Dell A09 BIOS)!  I have working Dapper Drake CD's, but I don't want to go through all the trouble of upgrading to Edgy then to Feisty.  What do you recommend?

---

### Post by dannyboy79 on 2007-05-03
there are many possible solutions, have you tried any boot options?

**if you have an nvida graphics chip**
 Boot Live CD
2) press F6 key, remove splash and quiet from line, added single vga=791 <enter>
This allows all messages to scroll across the screen and the vga=791 gives you smaller console text.
3) system boots to single user mode and you are logged in as root
4) sudo apt-get install nvidia-glx (must be connected to net)
5) sudo nvidia-glx-config enable
6) startx

OR

**if you have an ati chip**
Boot live cd
2) press F6 key, remove splash and quiet from line, added break=bottom<enter>
This allows all messages to scroll across the screen and the break=bottom will eventually result in a busybox prompt. it'll be initramfs prompt.
3) you need to edit the xorg.conf driver, you would type in chroot nano /etc/X11/xorg.conf
4) you should now be using the text editor called nano and have the file xorg.conf open, page down until you find the line,
Driver         "whatever"
 and make it so that it has vesa, so it would be
 Driver         "vesa"
then hit control X, this will ask you at the bottom of the screen if you want to save, hit "Y", then it'll ask if you want to name it the same, hit "Y". 
5) now you should be back at the busybox prompt, hit control D
6) this should continue with loading the live cd.

now you should be able to perform the install without it crashing or freezing. once that occurs, this all may happen again when you try to boot your new system. just follow the instrucitons once again. then you should be good to go. also, once you have your install done and you do have an ati card, you won't have good graphics at all using vesa, you'll need to look into using Envy, it's a little automatic program for installing good drivers.

good luck

---

