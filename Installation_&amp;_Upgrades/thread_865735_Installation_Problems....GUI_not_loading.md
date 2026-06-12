---
title: "Installation Problems....GUI not loading"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by dave2k77 on 2008-07-20
This is my first time loading Ubuntu. I am trying to run it alongside Windows XP but when running the installation the GUI is not loading. I see the Ubuntu logo and the status bar, but after that, it goes straight to the command line instead of GUI that is expected. How do I fix this problem?

---

### Post by tuxxy on 2008-07-20
Login with the user/pass you entered at installation, then type this command

```
startx
```

If it does the same thing when you startup again then try to reconfigure xorg before you startx

```
sudo dpkg-reconfigure xserver-xorg
```

---

