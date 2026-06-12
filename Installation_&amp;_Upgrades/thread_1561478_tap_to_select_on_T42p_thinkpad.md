---
title: "tap to select on T42p thinkpad"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by wahoobob on 2010-08-26
Under 8.04 I did this to get the tap to select working on my thinkpad with a trackpoint in the keyboard.  Is this still the same under 10.04?  I'm not the greatest with the terminal so I want to check before I start a change.

Code:
sudo apt-get install sysfsutils  -Once that is installed, do;

Code:
gksudo gedit /etc/sysfs.conf  -and add this line to the bottom, then save it.

Code:
devices/platform/i8042/serio1/serio2/press_to_select=1

(several days later)
OK, I went ahead and tried it and this is the way to get the trackpoint working - I originally had one too many spaces in the code but now I beleive the code as shown is correct for you people with a thinkpad (and maybe others) who want to use the trackpoint with tap.

AGAIN! Now it stopped working after a reboot.  Does this command not make it permanent??

---

### Post by wahoobob on 2010-09-01
bump---

---

