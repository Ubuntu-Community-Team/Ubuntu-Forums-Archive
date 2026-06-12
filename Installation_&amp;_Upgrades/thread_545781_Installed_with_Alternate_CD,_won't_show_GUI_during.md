---
title: "Installed with Alternate CD, won't show GUI during bootup or X"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by upgrdman on 2007-09-08
I just built a new computer, AMD 6000 with an nVidia 8800 video card. I believe the video card may be the root of my problem because it is such a recent model. I have tried the Fiesty and Gutsy liveCDs, but my screen turns black after it loads the kernel. I went ahead and installed Fiesty with the alternate CD and the install went well.

But as I mostly expected, I still have the problem. Shortly after grub brings up Ubuntu my screen just turns blacks and stays that way. I see the HDD light flicker here and there so I do not think the system is freezing up. However even when I attempt Ctrl-Alt-F1 or F2 or F3 to bring up a command line I still get nothing.

I am dual booting on that computer with WinXP, so I know the video card is functional. I kind of expected this type of problem, but I do not know what course of action to take. Any tips or comments are welcome.

--Farrell F.

---

### Post by forestpixie on 2007-09-08
if you get a command prompt - run this command 

```
sudo dpkg-reconfigure xserver-xorg
```

If you don't get to a command prompt - start with the recovery option and then run the command - when you get to the video card choice - 

- choose nvidia, if it doesn't work start the process again and choose vesa

---

### Post by upgrdman on 2007-09-10
I got it all working. For anyone with the same problem I was having, this is how I got it all working.

1. Install Ubuntu with Alternate CD (text mode installer)
2. Edit in Grub and remove "quiet splash" and add "vga=normal" This disable the graphical booting, and you see a *lot* of text during bootup
3. Boot, then make this change permanent by modifying /boot/grub/menu.lst
4. Run "sudo dpkg-reconfigure xserver-xorg"
5. Start X, setup networking correctly, then download ENVY.
6. Run it... it worked perfectly with my nVidia 8800!

I have not tried to get graphic bootup (splash) working because I always leave my computer on and could care less about boot up.

Done.

-Farrell F.

---

