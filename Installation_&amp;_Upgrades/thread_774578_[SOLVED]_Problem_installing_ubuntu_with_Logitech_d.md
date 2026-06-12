---
title: "[SOLVED] Problem installing ubuntu with Logitech dinovo desktop"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by malaTG on 2008-04-29
Hi everyone,

I am trying to install Ubuntu 8.04 but I am having problem with a non-working keyboard and mouse. I have a Logitech dinovo desktop laser kit(bluetooth). It works fine in windows XP and at the boot screen but when I start the live-cd to install and get the ubuntu desktop the keyboard and mouse stops working. Any ideas?

I have read that there is a couple of issues with Logitechs products but was hoping for a workaround (I like my keyboard and mouse :-))

Hoping for help!

/mala

---

### Post by Baphometus on 2008-04-30
Same here. If you unplug the receiver and plug it back in - it'll work. But I hope there is another, "normal" way around this.

---

### Post by malaTG on 2008-05-15
I just wanted to tell evryone that I solved this issue, at least in a ugly way. Since I don´t have any other bluetooth devices connected to this computer I just removed all bluetooth software from my ubuntudistribution. This way the embedded drivers within the usbreciever were used and everything works fine.

---

### Post by kakao on 2008-07-14
See Bug [123920]("https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/123920") at lauchpad for further information.

Cheers.

---

### Post by stefan_g on 2008-11-14
I found a solution working for 8.04 ([http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)).

Though this solution is meant to be used for some microsoft keyboard, it also works for the Logitech diNovo (at least at  my computer).

However, this method fails for 8.10, apparently due to changes in the way, pairing is done.

The hard way, i.e., deinstalling all bluetooth software, does still work.
But this cannot really be called a solution. So I don't understand why the issue with the diNovo keyboard is marked as solved.

Any ideas?

Best regards, Stefan

---

