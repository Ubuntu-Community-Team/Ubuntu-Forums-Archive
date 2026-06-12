---
title: "Disable Compiz Before Start Live"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Madefh on 2008-10-31
Hiho!

I'm trying to test the Ipex, but I can't get any screen. I eard about the Ipex brings Compiz enabled, but my Graphics card don't support that (Unichrome9)... Then, how can I disable the Compiz BEFORE start the X in the live CD? I tried some things like Graphics Safe Mode and force the vesa but the Ipex don't start because X crashes...

How Can I Disable the Compiz before start X Server at Live CD?

Thanks.

---

### Post by jerrylamos on 2008-10-31
It's a little tricky.  For some reason they refuse to have a "no compiz" boot.

t is possible to remove compiz on CD Live if you can catch it during gnome desktop load.
    On intial boot push F6 and delete (backspace) over quiet splash
    Watch for message that gnome desktop is being loaded, well into the boot.
    X windows will intitate with some flashing of the screen.
    Quick do Ctrl-Alt-F1 to get a command line.  Might have to do the Ctrl-Alt-F1 a few times.
    While boot is still going on, on the command line do
sudo apt-get remove compiz
sudo apt-get remove compiz-core
Ctrl-Alt-F7

In my case, desktop then comes up O.K.

Jerry

---

### Post by Madefh on 2008-11-01
I tryed to do that, but when I go back to tty7 (Ctrl+Alt+F7), the screen are freezed and I can't do anything more. Really freeze the computer.

Thanks.

---

### Post by mingohills on 2008-11-15
Just an FYI.

When I ran the installation, compiz wasn't there.  Only after my first update did I have compiz installed.  There were 75+ updates, and compiz was buried in the middle.

---

