---
title: "[SOLVED] Nvidia drivers"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2007-11-06
I have checked the post, they are for people that can log in. This is for a friend. He has installed Ubuntu on a HP Pavilion 6000, after he finished installation and restarted, his screen goes blank and can even log in. He's working with live CD until I find the solution. I know in theory what I have to do, but don't know how to do it. What I want is to get in on the xconf and change his video card driver for the generic one,  I think is VESA, then on his session install the driver, and change it back.
Now, the thing is that I don't know how to do it. :oops: even knowing all the theory....

Please help! I would thank you forever!!!:)

---

### Post by Steven_B on 2007-11-06
Boot into recovery mode.
Use vim or nano to edit xorg.conf.  I've generally used vim, but nano is a lot easier to figure out if you aren't familiar with it.
```

cd /etc/X11
vim xorg.conf
OR
nano xorg.conf

```
Once you've done the edits you want, you can try to run the graphical login with "gdm".

Here's a vim micro-tutorial:
"vim filename" opens "filename".
Press "i" to allow insertion of text.
Edit text like most other text editors.
Press escape to quit insert mode.
Type ":save filename" to save the file to "filename"
Type ":q: to quit.

---

### Post by arashiko28 on 2007-11-10
Thanks, problem solved. I'll put in the info, for other users.

If you can log in:
On terminal write:
sudo nano /etc/X11/xorg.conf

go down on the list to DEVICES, look for your graphics card and where it says "nvidia" or "ati" change it for "vesa", ctrl+x to exit, save it. there you can download your drivers and install it.

If you can't log in:
On the GRUB count down, press ESC before it reaches 0
In the menu, choose recovery mode, follow the steps and do the same as above, change your dard name for "vesa" and save it.

Hope this can help someone with the same problems.:lolflag:

---

