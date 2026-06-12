---
title: "insert cd to install something"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by Andra on 2007-06-12
hello

I would like to be not dependent on os installation cd inserted in the server. Now, when from remote computer I run command &#8220;apt-get install xxx&#8221;, I can get a message - approx. text - &#8220;please insert Ubuntu cd and press enter&#8221;.

I know that I could make a partition on disk and place there the same iso image I burned on cd. How could I say &#8220;apt-get install xxx &#8211;option if cd needed, try partition nnn&#8221;?

---

### Post by taurus on 2007-06-12
Edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and put a # in front of the line that has **cdrom** in it to comment it out.  Save it with <Ctrl>o and exit with <Ctrl>x.

Then, run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Andra on 2007-06-12
thank you! I will try it next time I encounter this situation.
As far as I understand, I comment out cdrom line and then it will always turn to repositories on internet. And if I need apt-get without ethernet (and work from console), I uncomment the cdrom line.

---

