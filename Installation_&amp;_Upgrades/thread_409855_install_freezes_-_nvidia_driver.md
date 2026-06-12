---
title: "install freezes - nvidia driver"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by greenex on 2007-04-15
OK, i found the solution to my problem a long time ago but can't seem to find it again.

Basically, I pop in the 6.10 CD in and it freezes right after it plays the Ubuntu sound and at the Gnome screen.  I remember reading something about pressing F6 during the normal boot to interrupt it, edit some line, then it brings you to a command prompt (without actually having Ubuntu installed yet).  Then edit the xorg.conf and change the nv driver to vesa.

How do I bring the install to the command prompt before installing Ubuntu?

Thanks a bunch!

---

### Post by greenex on 2007-04-15
Ah HA!  I finally managed to find it.  Here it is for just for reference:

> **Bluedog260 said:**
> I managed to find a solution :D :D 

Seems to be some issues with the nVidia drivers, so you do this:

1. Hit f6 on the menu, delete quiet splash from the boot parameter line, and add single. Single stops it loading x and a load more crap.

2. Once booted, type pico /etc/X11/xorg.conf. Find your video card, and change driver "nv" to "vesa".

3. Save (ctrl - o), exit pico (ctrl - x), then type startx. This starts x using the VESA drivers for video.

== Only do the rest if you want to load nvidia drivers for accelerated graphics / better performance (may as well).

4. Once ubuntu loads up, goto programs -> accessories -> terminal. Type /usr/sbin/synaptic into the terminal to start synaptic package manager.

5. Now following these instructions:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

(I'm doing this from memory, but you will get the gist of what I mean).

In repository prefs, make sure all boxes are ticked (ie restricted packages are available). Close, click reload, wait.

6. Back in the terminal, type uname -r to see your kernel version, it's 2.6.17-10-generic.

7. Click search in synaptic, enter: linux-restricted-module. Select the correct one for the above set of numbers, you might have to right click on it and press upgrade/reinstall, but make sure you do it.

8. Now search for nVidia. Find nVidia glx and select install.

9. Press apply in synaptic.

10. Terminal again. Type nvidia-xconfig.

11. Press ctrl-alt-backspace to kill x, enter startx to restart x, and bam :)

[http://ubuntuforums.org/showthread.php?t=330118&page=2&highlight=install+freezes+nvidia+driver](http://ubuntuforums.org/showthread.php?t=330118&page=2&highlight=install+freezes+nvidia+driver)

---

