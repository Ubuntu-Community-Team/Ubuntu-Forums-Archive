---
title: "Boot problem...help newbie"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mr.Crack on 2009-10-02
Sorry if i am double posting here (newbie), but I recently upgraded from jaunty to karmic on my Toshiba nb205. When i boot the system, it says grub loading...then the screens goes black with a white blinking cursor....It does not even let me choose which kernel i would like to boot from...it simply by passes that screen and automatically loads the kernel that is at the top. Any help would be appreciated. thanks

---

### Post by Mike_IronFist on 2009-10-02
> **Mr.Crack said:**
> Sorry if i am double posting here (newbie), but I recently upgraded from jaunty to karmic on my Toshiba nb205. When i boot the system, it says grub loading...then the screens goes black with a white blinking cursor....It does not even let me choose which kernel i would like to boot from...it simply by passes that screen and automatically loads the kernel that is at the top. Any help would be appreciated. thanks

Well Karmic uses a newer version/setup for GRUB, and the rules for this new version of GRUB are a little different. I'm pretty sure, however, that pressing esc should bring up the menu that lets you select your kernel.

---

### Post by Moop on 2009-10-02
That was happening to me too for awhile. I was able to hit any key and it would drop me to a tty where I could log in. Alt+ F7 would take me back to the gui.

---

### Post by Mr.Crack on 2009-10-02
tried the alt-f7....nothing works..

---

### Post by Vanishing on 2009-10-02
> **Moop said:**
> That was happening to me too for awhile. I was able to hit any key and it would drop me to a tty where I could log in. Alt+ F7 would take me back to the gui.

what are you talking about?
this is not a tty issue, he is talking about grub...


on topic:
which grub are you using? grub or grub2?

---

### Post by MTGap on 2009-10-02
Read this: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Look for the Hidden Timeout that is probably your issue.

---

### Post by LKjell on 2009-10-02
> **Mr.Crack said:**
> Sorry if i am double posting here (newbie), but I recently upgraded from jaunty to karmic on my Toshiba nb205. When i boot the system, it says grub loading...then the screens goes black with a white blinking cursor....It does not even let me choose which kernel i would like to boot from...it simply by passes that screen and automatically loads the kernel that is at the top. Any help would be appreciated. thanks
Holding shift after the bios logo should let you into grub menu

---

### Post by Mr.Crack on 2009-10-02
I just removed grub and installed grub 2....about to reboot.

---

### Post by LKjell on 2009-10-02
> **Mr.Crack said:**
> I just removed grub and installed grub 2....about to reboot.
If you did not have grub2 then this is a bug. Karmic is not suppose to change your boot loader.

---

### Post by Mr.Crack on 2009-10-02
ok...so holding shift works like a charm...this brings me to my next question...will i always have to hold shift...or will the grub menu load automatically as it did in jaunty? This may not be the correct post for this question but, my system shutdowns extremely fast....but after i select the kernel i want to boot...takes about a min and a half to boot up to the login in screen...Any suggestions? thanks in advance

---

### Post by VMC on 2009-10-02
Output "/etc/default/grub" . Look closely at these parameters:
```
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="11"
```

---

### Post by Mr.Crack on 2009-10-02
ok from looking at that code, it seems that I have to edit the grub menu.lst, how do i access the list?

---

### Post by LKjell on 2009-10-02
> **Mr.Crack said:**
> ok from looking at that code, it seems that I have to edit the grub menu.lst, how do i access the list?
The power of search... [http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305+grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305+grub)

---

### Post by Mr.Crack on 2009-10-02
thanks alot man...worked like a charm...problem fixed!

---

