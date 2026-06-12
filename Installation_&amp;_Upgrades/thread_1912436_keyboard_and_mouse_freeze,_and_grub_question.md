---
title: "keyboard and mouse freeze, and grub question"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by extradessert on 2012-01-20
OK 2 questions:

1: I was upgrading a core i5 machine to 10.04 (fresh install upgrading from 9.10) but uinder lucid the keyboard and mouse freeze up randomly and require a reboot to unfreeze.
Happens on both a liveCD or HDD install.

I've asked about this on the #ubuntu irc channel a few times, here's a few notes from that:

-I disabled IRQbalance, no effect that i see
-I don't have any usb HDDs plugged in, only usb thing plugged in is a Bluetooth adapter.

specs (from memory, dont remember exact specs):
          Intel Core i5-250 @2.66ghz
          Asus p7p55d mobo
          Geforce gtx280

2: Before on this machine in 9.10 I set up the GRUB2 menu to hide the menu and display a countdown (and it IS a multi-os system) with disabling a script conditional... but I cant get it working again on 10.04, what is the right conditional to disable to get this working?

---

### Post by mörgæs on 2012-01-21
Have you tried some of the new Buntus?

A year or so ago there were many reports about freezing, and it is an easy test to see if it has been fixed in 11.10.

---

### Post by extradessert on 2012-01-22
ugh.
I 
DONT
like 
unity

Not going to install a new version cause of that, rather stick with 10.04.

Is there any fixes to the freezing other than upgrade to unity ****?

---

### Post by mörgæs on 2012-01-23
I was thinking of Xubuntu 11.10.

---

### Post by duuso on 2012-02-06
Just cleanly installed Ubuntu 11.10 x64 to this IBM R61 laptop and keyboard freezes every now and then, sometimes even during usage. Not so nice. When keyboard doesn't answer, the UI is also more or less unresponsive - mouse still works but if I for example try to close current application/window by moving cursor to upper lef corner, the buttons doesn't appear. Huawei E367 worked out of box, cool as previously there has been hazzle with 3g modems. 

I think I'm downgrading this back to 10.10 as there's seems not be fixes for this freeze issue.

---

### Post by extradessert on 2012-02-29
Xubuntu..hmm 
Although last I tried that (10.04) it was hard for me to adjust to where everything is..don't ask why...

Anyways does anyone have any info on this issue before I go try another distro to see if it will work (lol)?

---

### Post by extradessert on 2012-03-04
Figured out the freezing, the tip in comments [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/632048")  works great.

Now for grub, still cant figure out getting the menu to hide on multi-boot system...

---

### Post by mörgæs on 2012-03-05
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

---

