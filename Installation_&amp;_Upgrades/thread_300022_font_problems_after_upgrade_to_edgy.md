---
title: "font problems after upgrade to edgy"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by lugburz on 2006-11-15
Hi all,
after the upgrade from dapper to edgy I had a problem with the current default font of no-KDE application: usually are small and sometimes not well rendered.

In example now the standard emacs font are very little and the rendering have some interruption, the font in chromium are not readable, see the picture below:

[IMG]http://fcdfhome.fnal.gov/usr/volpig/chromium_font.png[/IMG]

what is the reason?

---

### Post by NoNo_231 on 2006-11-15
Probably this is the solution to your problem [http://www.ubuntuforums.org/showthread.php?t=268024](http://www.ubuntuforums.org/showthread.php?t=268024)

---

### Post by lugburz on 2006-11-15
uhm... I'm reading the thread but seems the same things, I tried also to add the same directories in the xorg.conf file but the results on emacs and Chromium don't change.

---

### Post by NoNo_231 on 2006-11-20
You must change from /usr/share/X11/fonts/(something) to /usr/share/fonts/X11/(something) so to find the right fonts. By adding I am afraid that goes to the first one. Also you have to kill xorg or reboot, in order the change to take effect.

I just changed the part (/X11/fonts) to (/fonts/X11/) to the fontpaths, and didn't add or remove anything.

---

### Post by lugburz on 2006-11-21
I'm afraid that the mistake is the intel driver: my laptop have 2 graphic cards a Nvidia and an intel 945.

With the NVidia I don't have any problem in the fonts while we the intel card I have the problems that I described in the previous post.

---

