---
title: "My keyboard goes back to usa key layouts-help"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-05-02
Whenever I set my keyboard to the local it resets back to usa key layouts when i close the computer the reopen it again, i am using Hardy.
I can I correct this ?

---

### Post by bobnutfield on 2008-05-02
Hello,

I had the same issue when I upgraded on my desktop.  To solve this, I went to:
System>Preferences>Keyboard.  There, on the local tab, you can change to your local keyboard layout.  But you must remove the USA keyboard from the list or Hardy, for some reason, will revert back to it on reboot.

Hope this helps.

Bob

---

### Post by unutbu on 2008-05-02
If bobnutfield's solution does not work for you,
edit your /etc/X11/xorg.conf file:

```
gksudo gedit /etc/X11/xorg.conf
```

Search for "XkbLayout".

It probably says
```
    Option         "XkbLayout" "us"
```

Change 'us' to the two-letter localization code that you want. If you don't know what it should be, post and we can help.

---

