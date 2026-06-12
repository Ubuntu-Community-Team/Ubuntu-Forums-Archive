---
title: "Nvidia overscan correction requires nvidia-setting at startup"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by tuppe666 on 2010-02-14
I finally fixed my overscan using the slider in nvidia-sessions using the PPA as the release one does not have this. The Slider works wonderfully but unfortunately at reboot the settings are lost. If I startup nvidia-settings again it corrects this. I now have it autostarting on login, but this is not ideal. Does anyone know how to fix overscan without having to start nvidia-settings every time I want to correct this.

---

### Post by lidex on 2010-02-14
There's an option in there to "save to x configuration file" when "xserver display configuration" is selected - have you tried that? Or how about:
```
sudo nvidia-xconfig
```

---

### Post by mia1dolfan on 2010-02-14
The option to "save to x configuration file" didn't save that option for me.  I ended up adding the line [FONT="Courier New"]nvidia-settings -l[/FONT] to the file /etc/X11/xinit/xinitrc - right before the last line .../xsession.  The version number is also very important, I'm running NVIDIA GLX 195.36.03.  For reference for other users version 190 has the slider option for overscan.  If someone knows if there is a X11 option, i'd love to know.

Thank you.

---

### Post by lidex on 2010-02-14
Some links:
[http://ubuntuforums.org/showthread.php?t=364252]("http://ubuntuforums.org/showthread.php?t=364252")
[http://forum.xbmc.org/showthread.php?p=459219]("http://forum.xbmc.org/showthread.php?p=459219")
[http://www.linuxquestions.org/questions/linux-desktop-74/how-to-calibrate-tv-under-linux-nvidia-619419/]("http://www.linuxquestions.org/questions/linux-desktop-74/how-to-calibrate-tv-under-linux-nvidia-619419/")

---

