---
title: "Skype Freezes on Maverick"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by Sugi on 2011-01-22
I have been trying to fix skype for a while now and it's failing to resolve anything. It's like skype is frozen in time, and stops workings.  

I've tried this method, but it doesn't help me.
sudo chmod ugo+r libpulse.so.0.12.2
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/646862](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/646862)

More details on the freezing issue:
Skype freezes [kinda], it's like it's frozen in time, but I can click on the interface and change options, but nothing changes, it shows that the same friends are online even though they have signed off, I can message them but a yellow '!' mark appears by the message.

My Error:
> (<unknown>:9878): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:9878): Gtk-WARNING **: Loading IM context type 'ibus' failed


How are people getting skype to work with their maverick box?


Ubuntu 10.10 x64
Skype 2.1.0.81

Sugi

---

### Post by Sugi on 2011-01-22
Where does everyone install their skype from?  software center or deb?  Can anyone provide links?

Sugi

---

### Post by Sugi on 2011-01-24
I have reinstall skype through the ubuntu software-center, and it appears it has helped a little. In the last 24, it has only crashed once, which is a BIG improvement from crashing about every half of an hour.  Though, I am worried it's going to start crashing a lot soon.

Sugi

---

### Post by Sugi on 2011-01-30
I guess, the crashes is over with since the reinstallation.  I wish, I could have found what the issue was before.  This really ins't solved, but the problem is gone now.

Sugi

---

### Post by Sugi on 2011-02-06
It looks like the crashing problem is back again, hasn't anyone else found a solution to this yet?

Sugi

---

### Post by Sugi on 2011-02-07
Bump for new information.

Sugi

---

