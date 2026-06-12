---
title: "Ubuntu liveCD flashing cursor..."
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by Nissan_350Z on 2012-05-14
Alright, so after a while of waiting for ubuntu to further improve..i found 12.04 to be where i want to begin..so i download the iso and burn it. It boots to the CD fine, it shows the stick figure and a keyboard at the bottom and asks for my language..so i check english and select Install Ubuntu...
It takes a few seconds then goes to a black screen with a flashing cursor. I left it on all night..and it still stays at that flashing cursor.
I dont understand what could be going on, other than a video issue as i can hear the camera sound when i push print scrn on my keyboard. Any ideas? I'm running:
Dell XPS 8100
Core i5 Quad cord 3.2ghz
MSi N520GT 2GB

Using the 64bit version of 12.04.

Thanks! 
Also, feel free to throw some command lines out there, im no newb to linux language. :)

---

### Post by roelforg on 2012-05-14
Could you get to a tty via the ALT-CTRL-F* combi?
Did the KB-caps-led blink?
Try pressing alt-sysrq-r
Does the led blink now (i had that once, weired but that happens sometimes)?

If one of the last 2 questions were true: kernel panic

---

### Post by jawilljr on 2012-05-14
Try turning on [nomodeset](http://ubuntuforums.org/showthread.php?t=1613132)

Jerry

---

### Post by Nissan_350Z on 2012-05-14
wow, thanks! nomodeset works like a charm. I appreciate it. :)

---

### Post by Nissan_350Z on 2012-05-14
next question..it installed fine and restarted to a purple GRUB. I select Ubuntu and the screen goes purple with random dots and lines all over....?

---

### Post by jawilljr on 2012-05-15
Sorry did't see your reply.

Go to the above link I gave you an scroll down till you see this line:

> How to temporarily set kernel boot options on an installed OS (not wubi)

That temporarily sets nomodeset on that boot.

Hopefully it loads to the desktop...then install NVidia's drivers:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

Hope this helps.

Jerry

---

