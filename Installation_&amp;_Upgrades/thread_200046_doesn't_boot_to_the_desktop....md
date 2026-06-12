---
title: "doesn't boot to the desktop..."
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by tubunu on 2006-06-19
I was asked to help a friend install Dapper on an old-ish laptop with 128MB of RAM. 128MB is listed in the minimal requirements list, but when I try to boot the live CD it just doesn't EVER get as far as the desktop. It just loads forever and ever and ever... wasted about 5 hours trying to reach the desktop. No luck. 

Does that mean I can't install Dapper? Can I install it without having to wait for the live CD to boot the desktop? Maybe some command line....?

Please help. Thank you.

---

### Post by aysiu on 2006-06-19
128 MB of RAM is a bit little for the Desktop CD (I know--I have a computer with 128 MB of RAM).

I would use the Alternate Install CD instead.

---

### Post by Winblowz on 2006-06-19
You could install the "alternate install cd" from the Ubuntu downloads page. It was made for situations exactly like yours. I've never used it personally, but I think it uses a  text-mode installation.

---

### Post by tubunu on 2006-06-19
OK, but is there a newbie howto for text mode install?

---

### Post by aysiu on 2006-06-19
This one focuses on dual-boots, but it gives you a sense of what the text-mode install looks like:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

You can either do a regular install from the Alternate Xubuntu CD... or do a server install from the Alternate Ubuntu or Kubuntu CD and then ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

---

