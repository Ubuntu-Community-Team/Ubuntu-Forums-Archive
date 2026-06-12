---
title: "installs but doesn't boot to desktop"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by blattr on 2006-06-30
Let me first say that I'm very new to linux and ubuntu. I just installed i386 of dapper drake onto my computer from a cdr. Everything seemed to install fine and I was asked to remove the cd from the cd-rom drive. My computer now boots looks like it boots into Linux and then promts me for my username and password. After I enter them, I seem to go straigt to the command line (?) and I have no idea where to go from there. I've tried reinstalling it and it doesn't seem to fix the problem. Any help?

---

### Post by jarland on 2006-06-30
I suppose my first thought would be to type "startx" in the command line & see what kind of response you get. If it's properly configured & just not starting automatically, that will take you to the desktop. But I'm going to bet it's going to bring up an error message instead.

---

### Post by stychman on 2006-06-30
Did you install the desktop CD or the server install CD?

---

### Post by blattr on 2006-06-30
ahh. Yeah, I think i installed the server cd. I don't have at least 192mb or ram, which is what the documentation at the ubuntu website seemed to say I need for the desktop cd.

---

### Post by jarland on 2006-06-30
Try the desktop cd. If it's really too slow for you, try either Xubuntu or Ubuntu Lite.

---

### Post by taurus on 2006-06-30
I recommand you use XFce4 as your window manager due to large amount of RAM.  You dont' have to reinstall.  Just boot your server up and at the prompt, type
```

sudo apt-get update
sudo apt-get install xubuntu-desktop

```

---

### Post by ubuntu_demon on 2006-06-30
I just wrote some detailed instructions on how to get from the server install to a normal desktop install. It's right here :
[http://www.ubuntuforums.org/showthread.php?t=206782](http://www.ubuntuforums.org/showthread.php?t=206782)

Please test it!

---

