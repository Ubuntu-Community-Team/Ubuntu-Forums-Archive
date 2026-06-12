---
title: "Corrupt console text on installation of Hardy server"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by echofire on 2008-05-20
Hello,

I have just installed 8.04 Server, on a scrap-box parts Pentium III with 1GB RAM. The installation and boot steps went smoothly, but on booting the console display is corrupted.  Duplicated and missing characters.  It is possible to log in but barely possible to make out the console output for the messed up display.  Reminiscent of the wrong baud rate or noisy lines on old style terminals.  The same with Alt-F1.  Feisty desktop CD boots fine and Alt-F1 from there works fine.  Installation CD checks OK.  Memory checks OK.  I cannot get in through ssh as get 'connection refused' and I'm unable to check config as I can't read the screen.  It looks as if 8.04 server, but not 7.04, the installation routine, or GRUB, has configured the console terminal wrongly.  Any ideas ?

Thanks

---

### Post by dstew on 2008-05-20
Try the kernel options **vga=791** or **vesa=force** and see if that helps. What kind of display do you have? Old-style CRT, or an LCD?

---

### Post by echofire on 2008-05-22
Thanks dstew.  Neither of these worked but vga=788 solved the problem.  This is an old-style CRT.

Nick

---

