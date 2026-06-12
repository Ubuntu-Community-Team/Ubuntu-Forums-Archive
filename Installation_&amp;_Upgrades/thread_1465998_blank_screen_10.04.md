---
title: "blank screen 10.04"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Shigoki-linux on 2010-04-29
hi, i am trying to do a fresh install for 10.04, but upon booting, and selecting language and either "try..." or "install..." i go to a blank screen and my monitor (HP vs17e, about four or five years old) goes into sleep mode. any ideas? or is this just a bug that will be fixed in a few days? and my pc has nvidia GeForce 6150 LE, and have 2gb ram. thanx!

---

### Post by burkleypatterson on 2010-05-26
I'm having the exact same problem! When installing I pressed f6 and selected all of the options in the menu and then tried to boot, and it seemed to work fine. I was able to access the live cd and go through the installation (which completed successfully), but upon restarting, the screen was blank, flickered a bit, and went to sleep. When I turned the sound up I heard the startup music, which leads me to believe this is just a graphics issue. Please help!

Also, the computer I am installing this on is a similarly aged HP

---

### Post by confused57 on 2010-05-26
> **burkleypatterson said:**
> I'm having the exact same problem! When installing I pressed f6 and selected all of the options in the menu and then tried to boot, and it seemed to work fine. I was able to access the live cd and go through the installation (which completed successfully), but upon restarting, the screen was blank, flickered a bit, and went to sleep. When I turned the sound up I heard the startup music, which leads me to believe this is just a graphics issue. Please help!

Also, the computer I am installing this on is a similarly aged HP

I can't really give you a fix, but after you hear the startup sound, press "Enter", blindly enter your password, then press "Enter" again...see if this boots into your installation.  If this works, you might be able to change the gdm login screen resolution or set Ubuntu to boot directly without logging in?

Added:  Found this thread, which may work for you:
[http://ubuntuforums.org/showthread.php?t=1494122](http://ubuntuforums.org/showthread.php?t=1494122)

---

### Post by Catharsis on 2010-05-27
Some clearer instructions:
1) Hold down Shift while booting to get to grub.
2) Press 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.

---

### Post by wilee-nilee on 2010-05-27
> **Catharsis said:**
> Some clearer instructions:
1) Hold down Shift while booting to get to grub.
2) Press 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.

This will hopefully get you in but is not the fix, this method is per boot and not kept.

---

