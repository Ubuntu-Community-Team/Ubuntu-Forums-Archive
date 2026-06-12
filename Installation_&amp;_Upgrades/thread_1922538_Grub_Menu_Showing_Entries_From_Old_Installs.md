---
title: "Grub Menu Showing Entries From Old Installs"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by VanceVEP72 on 2012-02-09
Situation: I HAD some Linux distros installed on a 3rd HDD on my system. When I installed Ubuntu 11.10 on my new HDD, it created entries in GRUB for those old installs (which have long been wiped off the 3rd HDD). I, for the life of me, can not find a way to get those GRUB entries to disappear.

Here is my setup:

dev/sda1 is my Windows operating system HDD
dev/sdb1 is my Linux operating system HDD
dev/sdc1 is my data HDD

There USE to be Linux installations on dev/sdc1 which were deleted/formatted over when Ubuntu 11.10 was installed on dev/sdb1. Those dev/sdc1 entries continue to plague my systems GRUB menu.

Solution?

Thank you very much in advance!

---

### Post by Firezap on 2012-02-09
There is a program called GRUB Customizer that is pretty easy to use. Its not in the software center, but it allows you to edit many settings easily, including removing items from GRUB. To install it, run ```

[COLOR=blue]sudo add-apt-repository ppa:danielrichter2007/grub-customizer[/COLOR]
[COLOR=blue]sudo apt-get update[/COLOR]
[COLOR=blue]sudo apt-get install grub-customizer[/COLOR]
```Source: [http://sammishts.blogspot.com/2011/10/how-to-install-grub-customizer-in.html](http://sammishts.blogspot.com/2011/10/how-to-install-grub-customizer-in.html)

---

### Post by Bucky Ball on 2012-02-09
> **Firezap said:**
> There is a program called GRUB Customizer that is pretty easy to use. Its not in the software center_..._[]("http://sammishts.blogspot.com/2011/10/how-to-install-grub-customizer-in.html")

Well, it's in Synaptics on 10.10 so see no reason why it should have been removed in more recent releases. Check again. ;)

---

### Post by bogan on 2012-02-09
@**Bucky Bal**l,

In my 11.10 installation, Grub Customizer shows up in both Ubuntu Software Center and Synaptic Package Manager.

But is that not due to Grub Customizer being installed already??

Chao!,  **bogan**.

---

### Post by Firezap on 2012-02-09
Really? It did not show up in synaptic or Ubuntu Software center for me in-till I installed the ppa...Now Im worried...All I get was StartUP-manager...Let me put it this way, If you want to try my suggestion, search the software center first, if its not there, try the ppa.

---

### Post by VanceVEP72 on 2012-02-12
Thanks! Grub Customizer did exactly what I needed.

---

