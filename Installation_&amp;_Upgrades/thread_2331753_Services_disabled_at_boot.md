---
title: "Services disabled at boot"
date: 2016-07-25
forum: Installation &amp; Upgrades
---

### Post by patdundee on 2016-07-25
Hi Guys
Just upgrded from 14.04 to 15.04
In 14.04 you could state which services started at boot
How can i do this in 16.04 please
Many thanks
P

---

### Post by howefield on 2016-07-25
If you are asking how to see what is in Startup Applications which on a default installation appears to be blank, use the following commands..

```
cd /etc/xdg/autostart/
```
```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

or, all in one command...

```
cd /etc/xdg/autostart/ && sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

