---
title: "Keyboard for laptop"
date: 2021-08-26
forum: Installation &amp; Upgrades
---

### Post by hornetster on 2021-08-26
Posted this at AskUbuntu - no response so far:
Just installed Xubuntu on a laptop, and have an issue with numlock on boot up. There is no numlock settings in the bios, and on boot, the numpad in the middle of the keyboard is on. Have just the usual English international at the moment. Is it possible to select a different keyboard type, that will work with a laptop - specifically, will startup without numlock?? Thanks.

---

### Post by not-published on 2021-08-26
You did not mention what brand or model laptop, what year.

You said your keyboard has a middle numeric pad feature due to it's lack of a number pad but also a bios which has no "initial setting".

You did NOT say if you can simply press one button to bring the keyboard back to non-numeric mode.

If all you have to do is press "NUMLOCK" at each boot, then it's probably not worth the effort to answer your question.

You did select your keyboard when installing ubuntu:  I don't know what you did there.  After which that preference is used for (console if you can find ti) and for the Gnome desktop.

The Gnome desktop allows some keyboard changes - I'm unsure if that includes models or just hotkeys.

Xorg, the desktop "server", allows you to change keyboard layout/models and settings on the command line while Xorg is running.  There are a few of these apps.  Some may change model other only features.  There are also "apps" you can get to help you do this.  Google "ubuntu packages" and try searching for gnome keyboard utilities.

Open up your terminal window.  Check the manpages of some of items found by apropos:  at the bottom they will list other apps which also can modify keyboard settings.

$ apropos xk

The utilities listed are capable of changing numlock state and can be place in a (any of many) files which are activated before GNOME begins.

There ARE kernel options and kernel modules concerning certain laptop  features:  I cannot say if your keyboard specificly is among those.

---

### Post by hornetster on 2021-08-26
Thanks for a fairly unhelpful response. Could respond to specific suggestions, but could'nt be bothered....

---

