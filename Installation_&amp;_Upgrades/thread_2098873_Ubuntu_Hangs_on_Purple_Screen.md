---
title: "Ubuntu Hangs on Purple Screen"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by BulletproofIdeal on 2012-12-27
So I just finished getting Ubuntu (12.10 x64) and Windows 8 dual booting on my UEFI enabled laptop. I installed from the LiveCD and then installed the necessary updates after the installation (as well as some other applications like Gnome Shell, VLC, etc). I then went to reboot the OS and now I hang on the purple screen. I attempted the nomodeset solution found [here]("http://ubuntuforums.org/showthread.php?t=1613132") however it has no effect. Not sure if its worth noting but my ```
linux /boot
``` line does not end with ```
quiet splash
``` but rather ```
quiet splash $vt_handoff
```. As well booting Ubuntu in recovery hangs on loading initial ram disk. [Here's]("http://paste.ubuntu.com/1471522/") my boot info from boot-repair. For the record my Windows installation still works fine.

---

### Post by conradin on 2012-12-27
Can you get into an alternate terminal? press ctrl + alt + F4
and log in that way?

perhaps pressing tab or esc durring boot will give you a better idea about whats happening before it gets hung up.

alternatively, you could try booting into a livecd, and reading the dmesg log.

---

### Post by BulletproofIdeal on 2012-12-27
I can boot from a livecd (that's how I got the boot info) I'll try to get the log file and I'll try your other suggestions.

---

### Post by BulletproofIdeal on 2012-12-27
So I tried mashing ESC and Tab and I got a black terminal screen which showed the Tab and ESC chars in then my screen flashed again and I got the load screen and am currently in Ubuntu. I'm very confused by this I don't see why mashing either of these buttons would cause the OS to boot.

---

### Post by BulletproofIdeal on 2012-12-27
This was not repeatable I can't get back in after an attempt to replicate it. I will post the dmesg when I get the chance.

---

