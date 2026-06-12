---
title: "Black Screen after 11.04 upgrade"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by sagi7 on 2011-05-05
Hello,

after 11.04 upgrade my system starts and i hear the gnome start sound
but the screen keeps black. I only see the mouse.
I tried setpci -s 00:02.0 F4.B=30 - without success.

here my 
[Xorg.0.log]("http://paste.debian.net/116070")

best regards

---

### Post by Gotlieb on 2011-05-05
Hi,

How did you upgrade? Via CD or Update Manager? Can you see the terminal? If not you can try opening terminal via shortcut (Ctrl + t) so you can finish the upgrade.

I hope this helped a little bit :)

---

### Post by sagi7 on 2011-05-05
Thank you for your fast reply.

I upgraded via update-manager.
I can start a terminal with Strg+Alt+F1.  And then?

---

### Post by Gotlieb on 2011-05-05
Enter your Login & Password

Enter the following: *[I]sudo apt-get upgrade*[/I] (Make sure that your root) -r

Or Follow this simple instructions below

[http://www.liberiangeek.net/2010/04/how-to-upgrade-ubuntu-via-the-console-or-terminal/](http://www.liberiangeek.net/2010/04/how-to-upgrade-ubuntu-via-the-console-or-terminal/)

One other thing... Where you disconnected from the Internet during the upgrade?

This might be one of the causes.

---

### Post by kansasnoob on 2011-05-05
Please post the output of:

```
lspci | grep VGA
```

---

### Post by sagi7 on 2011-05-05
@Gotlieb: I had done this steps bevore.

@kansasnoob: ATI Inc RS880 (Radeon HD 4290)

---

