---
title: "Ctrl_Alt+F2 == no console?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-10-10
Anybody else having trouble getting to a console?
I added bug report: [https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/447692](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/447692)

---

### Post by FuturePilot on 2009-10-10
Yep, I filed this yesterday [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/447775]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/447775")

---

### Post by whoop on 2009-10-10
> **FuturePilot said:**
> Yep, I filed this yesterday [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/447775]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/447775")

Me too. My corruption looks much prettier ;-) :lolflag:

---

### Post by Funnnny on 2009-10-10
Looks like we should have a corruption image contest ;)
Usually I have this image when I turn off the computer. And now it gone when I turn off, but happen when I switch the console.
Anyone have the same problem when turn off the computer ( it only happen for 1,2s and then the computer switch off )

---

### Post by VMC on 2009-10-10
This topic reminds me to check on each boot up. I use to have it early on in the alpha series. Not at the moment. I never have those "corruptions" though. It's just blank screen.

---

### Post by hikaricore on 2009-10-10
Do any of you happen to have a vga= flag set in grub?
I had this issue which evidently was related to my nvidia card.
Upon removing it tty terminals work but the resolution is crap, fair enough trade i guess.  :p

---

### Post by VMC on 2009-10-10
> **hikaricore said:**
> Do any of you happen to have a vga= flag set in grub?
I had this issue which evidently was related to my nvidia card.
Upon removing it tty terminals work but the resolution is crap, fair enough trade i guess.  :p

I'm not sure what you about the resolution. It's just a terminal. Or do you notice a difference with using vga= versus none?

By the way, since you brought it up, I wanted to open a topic regarding vga=773, in Jaunty. If I use that , of course grub2 complaints but Jaunty splash works as expected. Using the new gfxload=1024x76 I get a blank screen.

Back on target. whoop, do you have any hires set in grub2 menu?

---

### Post by FuturePilot on 2009-10-10
> **hikaricore said:**
> Do any of you happen to have a vga= flag set in grub?
I had this issue which evidently was related to my nvidia card.
Upon removing it tty terminals work but the resolution is crap, fair enough trade i guess.  :p

No vga= or gfxpayload here.

---

