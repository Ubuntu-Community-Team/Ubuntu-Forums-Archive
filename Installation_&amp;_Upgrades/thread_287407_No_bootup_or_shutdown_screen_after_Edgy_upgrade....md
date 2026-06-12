---
title: "No bootup or shutdown screen after Edgy upgrade..."
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Culito on 2006-10-28
This might be posted elswhere but I can't find it yet...

I had a pretty much trouble free upgrade to Edgy, except the X server didn't install correctly, but I got that figured out fairly quickly.

The only thing now is where the boot up and shutdown progress screens were, my monitor just says "input mode not supported".  Is this a resolution issue, or is the progress screens not there anymore?

I liked the graphical boot and shutdown when it was there!

---

### Post by khedron on 2006-10-28
The only time I can remember having one of those is when my resolution was misset. Try disabling the higher resolutions under 'dpkg-reconfigure xserver-xorg' to see what happens.

---

### Post by Culito on 2006-10-28
Once the login screen pops up, everything is normal.  My max resolution is already set in xorg.conf...

---

### Post by frankelr on 2006-10-29
Your problem is somewhere with your monitor and/or the vesa driver for your video board.  edit the grub loader (display edit options using esc) for the Grub line .....ro ... quiet splash.  Add vga=791

If this works for you then its your LCD monitor; if it doesn't work try vga=788.  If this works the vesa driver doesn't do 1024 properly for your video board.  The vga=788 sets splash video to 800x600 which should work on anything.  If nothing worked remove the quiet splash entry.  After tryout you will need to edit menu.lst and perform a sudo update-grub

Bob

---

### Post by Culito on 2006-10-29
Thanks.
Are there any other settings to try?  791 doesn't work, and 788 makes the logo so big it wraps around the screen!  Also when I do a sudo upgrade-grub, I lose all my changes...

---

### Post by steve_mckay on 2006-11-24
sudo dpkg-reconfigure linux-image-$(uname -r)

That should fix the 'too big' splash image.  Also check that /etc/usplash.conf has the correct resolution.

---

