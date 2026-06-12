---
title: "Cannot boot into 18.04 after install; screen freezes after disk unlock"
date: 2018-05-27
forum: Installation &amp; Upgrades
---

### Post by liquidcross on 2018-05-27
I can run the 18.04 installer just fine, but after the reboot, I unlock my encrypted disk as usual, but then the mouse cursor appears and the whole system freezes. Any ideas? Maybe a display issue or something? I was running 16.04 without any problems before, and I've run into the same issue with 18.04 whether I try to upgrade or do a clean install.

I'm running a Thinkpad R60, with 4GB RAM, an SSD and T2700 processor.

---

### Post by donald187 on 2018-06-07
I had the same problem.  The only difference is that my disk is not encrypted.  What solved the problem for me was to get to the grub menu.  (If it doesn't come up by itself, which mine does, I read you can press and hold the shift key as it's booting up.)  Choose advanced options.  Select recovery mode.  Then a popup appears where I select resume.  Then select ok.  I could then get into my account but the screen resolution is messed up a bit.

I log in to my account.  Once logged in I type in a terminal.
```

sudo gedit /etc/gdm3/custom.conf

```

Enter my password.  Uncomment the line #WaylandEnable=false by just deleting the # sign.  Save.  Reboot.  And that solved the problem for me.

---

### Post by liquidcross on 2018-06-07
I ended up installing Lubuntu to get around it, but thanks!

---

### Post by donald187 on 2018-06-07
You're welcome. :)

---

