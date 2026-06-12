---
title: "system won't shutdown"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by lonewohlf42 on 2012-11-13
I have 3 computers that I upgraded to 12.10. My netbook works well, but the other 2 desktops computers won't shutdown when I tell them to. Instead of shutting down the system login screen appears.

---

### Post by blackbird34 on 2012-11-13
Have you tried doing it with a command to see if it's just some GUI element not working?

```
sudo shutdown -h now
```

---

### Post by lonewohlf42 on 2012-11-14
I tried the command line shutdown like you said and it works, shutdown properly.
But still not working with gui, and when I restart the system (12.10 64 bit) it hangs. I have to
open a terminal and enter unity to reset the unity desktop. After this everything works fine.

---

### Post by lonewohlf42 on 2012-11-16
I used the Boot repair disk and now my system boots up with grub and I can now shutdown my system using the gui. I still have an intermitent problem when I boot up the
system. Sometimes no laucher only background image. Then I type Ctrl+Alt+t and type unity into the terminal and this resets everything. From then on my system works perfectly. Still looking for a solution. By the way, when I use the live ubuntu 12.10 64 bit dvd my system works perfectly every time. This seems to be an upgrade problem. There is
an article in Linux Format magazine about this same problem. They had no solution as of publication.

---

