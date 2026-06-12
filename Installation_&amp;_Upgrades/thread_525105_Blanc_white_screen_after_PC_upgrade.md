---
title: "Blanc white screen after PC upgrade"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by Blondin on 2007-08-13
HELP! Yesterday I have upgraded my PC (new HDD + DVD recorder+battery) and installed some programs during the last week. After reboot and logon window the screen turns white and freezes. But if I press Ctrl+Alt+Backspace I see my wallpaper for second or two. The only thing I can do is to change the session in the logon window, but I don't know how to use the terminal to solve the problem. Any ideas?

---

### Post by gokussj4nr on 2007-08-14
Are you running a video card or using integrated graphics?  If you are using a video card, what type is it, ATI or Nvidia?

---

### Post by scott pruett on 2007-08-14
i just installed ubuntu yesterday; mine does this with users with desktop effects enabled - it's driving me crazy & i have to log in as root (dunno how to switch off the effects from terminal?).  i'm running intgrated graphics.

---

### Post by Blondin on 2007-08-14
I use a video card, ATI Radeon 9600XT, and usually it works well (only without running restricted drivers), at least Beryl almost flies on my old PC. Today I've found another interesting thing - Ubuntu actually works as usual even when I don't see anything because of white screen - I can rotate the "white cube" or call for Ubuntu help (F1 => Alt+Tab => all what I see in this case is the help icon at the bottom of the window)

---

### Post by gokussj4nr on 2007-08-15
Sorry to burst your bubble, after your second explanation my experience was different.  I received only  a white screen, nothing else, nothing was running in the background.  Have you tried an update "sudo apt-get update" to your system, sorry I'm not of more help.

---

### Post by Zer0Nin3r on 2007-08-16
Just finished installing the following upgrades:

```
Commit Log for Wed Aug 15 18:29:35 2007


Upgraded the following packages:
dbus (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
dbus-1-utils (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
flashplugin-nonfree (9.0.31.0.2ubuntu1) to 9.0.48.0.0ubuntu1~7.04.1
gimp (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
gimp-data (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
gimp-python (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
libdbus-1-3 (1.0.2-1ubuntu3) to 1.0.2-1ubuntu4
libgimp2.0 (2.2.13-1ubuntu4.2) to 2.2.13-1ubuntu4.3
libgl1-mesa-dri (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libgl1-mesa-glx (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libglu1-mesa (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libpoppler1 (0.5.4-0ubuntu8) to 0.5.4-0ubuntu8.1
libpoppler1-glib (0.5.4-0ubuntu8) to 0.5.4-0ubuntu8.1
libqt3-mt (3:3.3.8really3.3.7-0ubuntu5) to 3:3.3.8really3.3.7-0ubuntu5.1
libvorbis0a (1.1.2.dfsg-1.2) to 1.1.2.dfsg-1.2ubuntu2
libvorbisenc2 (1.1.2.dfsg-1.2) to 1.1.2.dfsg-1.2ubuntu2
libvorbisfile3 (1.1.2.dfsg-1.2) to 1.1.2.dfsg-1.2ubuntu2
mesa-utils (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
poppler-utils (0.5.4-0ubuntu8) to 0.5.4-0ubuntu8.1
python-launchpad-bugs (0.1.13) to 0.1.13.2
tzdata (2007e-0ubuntu0.7.04) to 2007f-0ubuntu0.7.4
wine (0.9.42~winehq0~ubuntu~7.04-1) to 0.9.43~winehq0~ubuntu~7.04-1

```

And now I'm having the same problems with the white screen and what not.  I do have Beryl installed and I am uising the nVidia drivers as well.  Never had a problem with the display for a long time up until now.  I'll see if I can find some more information and post what I can get.

:KSBy the looks of it, it may have something to do with mesa-utils or libgl1-mesa-glx.

---

