---
title: "firestarter in init.d"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by beausimon on 2006-07-02
After installing firestarter, I rebooted, did  a "ps -ef" but did not see the firestarter process. I then started firestarter from the menu, did a "ps -ef" again. This time the firestarter process is there.

Does this mean that the firestarter is not started automatically when I boot up? If so, how do I make it start on boot up?

---

### Post by scxtt on 2006-07-02
when the PC boots, firestarter is running ... once you're in a desktop env. and you 'start' firestarter, you've just editing what it filters ... i've never checked if it's 'running' imediately after install - a reboot might 'fix' the 'problem' ...

---

### Post by wifiabc on 2006-07-02
If you check the /etc/rc?.d  directories you can check if the firestarter init scripts are there.

---

