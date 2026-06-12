---
title: "Wubi Trouble"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by xL717 on 2010-02-20
I decided to try Wubi out and test Linux for myself.  I downloaded, installed it, and everything went fine, but now when I reboot I'm not given the option to boot into it like I should be - it just takes me to Windows by default.  I don't know very much about computers, so I don't know how to go in and change the boot order or anything, and I don't understand why it's not giving me the choice.  I have an HP desktop with Windows XP on it, and I installed Xubuntu.  If I go into my add/remove programs, it says Xubuntu is there, taking up 17,640.00mb, so I know it installed properly.  Why can't I boot into it?  Is there something I need to do, or a way to fix it?  Please go easy on me and explain with as much detail as possible, because I'm a n00b.  Thanks. :)[COLOR=#00c000][/COLOR]

---

### Post by lloyd_b on 2010-02-21
> **xL717 said:**
> I decided to try Wubi out and test Linux for myself.  I downloaded, installed it, and everything went fine, but now when I reboot I'm not given the option to boot into it like I should be - it just takes me to Windows by default.  I don't know very much about computers, so I don't know how to go in and change the boot order or anything, and I don't understand why it's not giving me the choice.  I have an HP desktop with Windows XP on it, and I installed Xubuntu.  If I go into my add/remove programs, it says Xubuntu is there, taking up 17,640.00mb, so I know it installed properly.  Why can't I boot into it?  Is there something I need to do, or a way to fix it?  Please go easy on me and explain with as much detail as possible, because I'm a n00b.  Thanks. :)[COLOR=#00c000][/COLOR]

It's most likely a bug in the installer has set the "timeout" for the Wubi boot screen to 0, so it's automatically booting into the default (Windows).

Follow the instructions in post #2 of [this thread]("http://ubuntuforums.org/showthread.php?t=1363225") and see if it helps.

Lloyd B.

---

### Post by xL717 on 2010-02-21
Thanks, that did the trick.

---

