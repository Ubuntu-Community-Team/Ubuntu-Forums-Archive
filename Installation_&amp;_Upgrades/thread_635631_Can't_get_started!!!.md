---
title: "Can't get started!!!"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by jkjk222 on 2007-12-08
Hello....I burned Ubuntu 7.10 Desktop i386 to a cd, and have been trying to get the program to work.  I had previously created a second partition on my HD, and Ubutu DID seem to install to that second partition.   In the Ubuntu folder, I see one .exe file (Uninstall Ubuntu), and 5 sub-folders.

Now, when my machine boots on the new CD, I am given a choice to start with Vista, or with Ubuntu.  Choosing Windows is just like it's been in the past.  Choosing Ubuntu is not so good....I get an opening Ubuntu screen, then  a black screen and I'm told "enter 'help' for a list of built-in commands".  There's several dozen commands, sort of like DOS.....but choosing the various commands doesn't get me going at all.  What am I failing to do that I ought to?    Thanks for the help.

---

### Post by PmDematagoda on 2007-12-08
Give this a try:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

