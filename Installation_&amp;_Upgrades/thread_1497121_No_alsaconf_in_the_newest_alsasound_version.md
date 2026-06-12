---
title: "No alsaconf in the newest alsasound version"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by gosu94 on 2010-05-30
Ok firstly i'm Polish and i can make mistakes. People who care about Polish side of ubuntu forums(forum.ubuntu.pl) can't help me so i going to ask you.
Ok so i've got a main sound card which is include in my motherboard but it dosn't working(Intel Corporation 82801G)

.And I've got second sound card which working(C-Media Electronics Inc CM8738), but ubuntu detect only first card (Intel) and try use it.
Earlier i used alsaconf to set main soundcard but in the newest alsasound version there gone.So i just dont have a sound.I don't know why but sometimes when i turn on my computer sound is it.But after restart there gone.
I've got Ubuntu 9.04
```
gosu@gosu-desktop:~$ lspci | grep audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
02:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
```

---

### Post by gosu94 on 2010-06-04
up

---

