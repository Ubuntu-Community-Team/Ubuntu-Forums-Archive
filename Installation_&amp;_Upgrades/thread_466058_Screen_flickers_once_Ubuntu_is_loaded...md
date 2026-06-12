---
title: "Screen flickers once Ubuntu is loaded.."
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by MattGEri on 2007-06-06
Hey there,

I installed Ubuntu last week and all was working perfectly. Now, I switched screens from a 17" (my GF's dads) to my screen (15"). Everything works fine on start up (I cant read text, see ubuntu loader) until I get to the Log In screen. Once I get to that step, it is unreadable. The screen flickers like crazy and you cant do anything. Well you can log in, but you cant see anything.

Any ideas whats causing this?

Thanks.

---

### Post by Wim Sturkenboom on 2007-06-06
Wrong resolution and/or refresh rates. Modify *HorizSync* and *VertRefresh* in the *monitor* section in the file /etc/X11/xorg.conf to match the capabilities of the monitor; also remove *modes* in the section *screen* that are not supported by your monitor.

When your system has booted, press <ctrl><alt><F1> (or F2 or ..); you will be taken to a console screen where you can login. Login and edit the xorg.conf file with your favorite editor. They say nano is quite easy, so
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.mybackup.conf
sudo nano /etc/X11/xorg.conf

```The first command makes a backup (just in case somethimg goes terribly wrong), the second command invokes the editor.

---

### Post by MattGEri on 2007-06-06
Thanks for the reply.

I went into that file and under screen and monitor is says the name of the old screen and then the modes. Doesnt have HorizSync or VertRefresh. Is there some sort of "default" screen settings I can put in under the screen and monitor sections?

Thanks so much for your help. Really appreciated!

- Matt

---

### Post by MattGEri on 2007-06-06
I got it working by putting in "Generic Monitor".

Thanks for your help Wim!

---

