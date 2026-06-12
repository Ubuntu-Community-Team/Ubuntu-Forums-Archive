---
title: "Update to 22.04 deleted programs"
date: 2022-11-08
forum: Installation &amp; Upgrades
---

### Post by francophone on 2022-11-08
Hello all,

I just updated from 20.04 to 22.04 and Scribus has been deleted (I don't remember how I installed it). The config files and such are still present, though.

Some settings from other programs are gone, including localization for Firefox (French), which switched to snap.

How can I find out what else is missing? Is this normal? If so, I shouldn't have updated. The update didn't just delete unused packages, it deleted all kinds of stuff, and I have no idea what programs are broken, missing, etc.

---

### Post by maglin2 on 2022-11-08
I don't upgrade from one release to the next (I reinstall), so I can't help with the general issue.
Scribus is available to install from the Ubuntu software app though (or via synaptic package manager or sudo apt install).

Language preference for firefox menus and page display can be chosen in Settings/General.

---

### Post by ian-weisser on 2022-11-08
Review your /var/log/apt/history.log for the list of removed packages.

Most folks do not suffer random missing packages. Among those who do, the most common cause is previous (unfixed) management mistakes that leave packages orphaned and thus eligible for autoremoval.

---

### Post by francophone on 2022-11-09
Why would Scribus (which is the only missing program) be orphaned? Regardless, I simply reinstalled it with the terminal.

Thank you, going into Firefox's settings fixed that issue. I should have thought of that, given how obvious a solution it is.

I do have another issue, though. I previously had two keyboard layouts installed, the French Azerty one, and a custom variant of it. The latter showed up in the settings,  and the file itself was still present in /usr/share/X11/xkb/symbols after the update. I updated evdev and base (both lst and xml), and using setxkbmap, I can use the layout, but I cannot add it to my input source list in the settings (I removed it as it didn't show up in the input source selector on the menu, thinking that I maybe had to re add it). Another weird issue I noticed is that setxkbmap falsely shows my keyboard layout as being Qwerty (the US variant). Does 22.04 handle keyboards differently than 20.04?

I don't know enough about Xorg and Wayland to know if his would make a difference, but my system is using Wayland. Would that make a difference regarding custom keyboard layouts? I am not worried about shortcuts as I don't use them to change layouts. I generally just use my custom layout.

I am new to this forum, if this should be a separate question, please let me know.

---

### Post by maglin2 on 2022-11-09
> **francophone said:**
> Why would Scribus (which is the only missing program) be orphaned?

Possibly you initially installed it from its PPA? [https://ubuntuhandbook.org/index.php/2021/01/scribus-1-5-6-available-install-ppa-ubuntu-20-04/](https://ubuntuhandbook.org/index.php/2021/01/scribus-1-5-6-available-install-ppa-ubuntu-20-04/)

---

### Post by francophone on 2022-11-10
I think you are right maglin2!

It still feels like 22.04 has trouble with different keyboard layouts, esp. custom ones, though.

---

### Post by grahammechanical on 2022-11-10
When we upgrade from Ubuntu 20.4 to 22.04 we may get a request to authorise the removal of obsolete packages. Why it should remove Scribus I do not know. Is the universe repository enabled? Scribus is in the 22.04 Universe repository.

Regards

---

