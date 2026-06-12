---
title: "Changed to Gnome from KDE but windows are jacked"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by fregas on 2010-06-14
Hi all,

I had kubuntu running for a while and decided i wanted to switch back to the gnome interface.  I installed the ubuntu-desktop package w/ apt-get and then changed my session default at the next login.  That worked flawlessly.  However, all my windows in firefox, add/remove programs, synaptics package manager etc. are missing the title bar with the close/minimize buttons.  its like they are still using KDE versions of their programs.  I can't do updates using update manager or synaptics because at one point i get a dialog box but its completely white and I can't see any text or buttons.  So some programs just aren't working right.

is there a relatively simple way to fix this or do i just need to reformat and start over?

Thanks, ubuntu rules.

craig

:confused:

---

### Post by RetchingRabbit on 2010-06-20
Try ```
metacity --replace
```

HTH!

---

### Post by wilee-nilee on 2010-06-20
If you want to fully remove KDE and have Ubuntu or Xubuntu look at this site. You can copy and paste the whole desktop setups to install and remove. Make sure your looking at your distro though when you do it.
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by fregas on 2010-06-20
> **RetchingRabbit said:**
> Try ```
metacity --replace
```HTH!

that worked but only for the current session.  if i reboot or log out, it goes back to the way it was.

---

