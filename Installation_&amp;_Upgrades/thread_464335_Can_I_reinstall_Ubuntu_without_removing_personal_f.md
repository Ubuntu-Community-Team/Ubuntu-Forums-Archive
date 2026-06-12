---
title: "Can I reinstall Ubuntu without removing personal files?"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by mu:te on 2007-06-04
Hey there,

to make this long story a short story.. I was messing with my graph card driver and all of a sudden I can't boot. Everytime I turn on the computer I just get huge terminal screen (called CTRL+ALT+F1 I think..) and unable to load the graphcard.

So I was haping that someone could guide me how to reinstall Ubuntu 7.04 without removing my files? In nother worlds formatting Ubuntu. =)

---

### Post by kdarkentity on 2007-06-04
well im not sure on that but y dont u try booting from a live cd and mount your partition with what u want to save and back it up onto cd's ...or u could try fixing w/e it is u messed up with your graphics card

...this prob isnt very helpfull but hey w/e im bored lol

---

### Post by galvao on 2007-06-04
I don't believe you'll have to do it. I think I've did the same thing you did last night - My graph card is a NVidia 6200 and I still can't get it to work. Thing is, if you really did it like me there's a little software that you install that will cleanup your xorg.conf file. It's called Envy and one place that you'll find a link to it is here: [http://albertomilone.com/wordpress/?p=85](http://albertomilone.com/wordpress/?p=85)

Notice that I'm assuming you have a Nvidia card and tried to install new drivers as I've did, so if my guess is completely wrong forget everything you read, since Envy is for NVidia only.

Hope I've helped a little.

Good luck, 

Install

---

### Post by cowkiller on 2007-06-04
if you were messing with your graphic card maybe you typed something wrong into your xorg.conf file (I think it was in /etc/X11/ )
try typing from the scree you are in "sudo dexconf" (without " of course), then reboot and cross fingers.

Next time you edit your xorg.conf file make sure to copy it to a backup, to replace it if the same thing happens.

This Envy application also installs ATI cards owner drivers, just in case you've got one.

good luck!

---

### Post by mu:te on 2007-06-04
> **cowkiller said:**
> if you were messing with your graphic card maybe you typed something wrong into your xorg.conf file (I think it was in /etc/X11/ )
try typing from the scree you are in "sudo dexconf" (without " of course), then reboot and cross fingers.

Next time you edit your xorg.conf file make sure to copy it to a backup, to replace it if the same thing happens.

This Envy application also installs ATI cards owner drivers, just in case you've got one.

good luck!

How can I install a program if I cant access my computer?

---

### Post by cowkiller on 2007-06-05
> **mu:te said:**
> How can I install a program if I cant access my computer?

Nono, you didn't understand it. You don't have to install any program. When you start your PC, the system gets you to this huge terminal screen(CTRL+ALT+F1), right? Once in this screen, just typing "sudo dexconf" your system will return your xorg.conf file to the defaults, then type "sudo reboot" . It wouldn't have to give any more problems next time you reboot. No install, no anything.

Once you've fixed this graphic issue, you can install Envy from [Here]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.4-0ubuntu4_all.deb"), and then install ATI or Nvidia driver.

---

### Post by galvao on 2007-06-05
Oh, just to add: Envy installs TNT drivers too, if I remember correctly.

---

