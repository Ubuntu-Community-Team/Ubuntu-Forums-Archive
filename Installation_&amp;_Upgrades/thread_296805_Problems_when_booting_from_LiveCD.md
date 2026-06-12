---
title: "Problems when booting from LiveCD"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by Adyehh on 2006-11-10
Hi,

I recently aquired a LiveCD copy of Ubuntu.
I beleive it is the latest version to date.

On booting the CD, the menu sucsessfully appears and I select option 1 (Start or Install Ubuntu)
This appears to work as the orange loading bar fills up.
But from that point the screen goes blank.
I have left it for atleast 5 mintues and there is no change.

Im running a 2.8ghz AMD chip with 1gb RAM and 200gb HDD.
Both HDD's and Optical drives are IDE connections.
Nvidia FX5700 AGP card.

Are there any special options I should be selecting on running this?
Any help is appreciated.

Ad

---

### Post by adwait on 2006-11-10
Try using the Graphics Safe Mode (look on the bottom of the screen..)

---

### Post by Adyehh on 2006-11-10
Sorry, already tried that.
I should have stated it.


Ad

---

### Post by gnarula on 2006-11-10
this happened with me too when i tried to install it on my system. Probably u have a hdd witha silicon controller. Here is the trick which worked with me:

Boot up with the LiveCD. When u get to select what to do, i mean when u get all the options like to access the Live CD or to check the disk, press F6 and then add the following:

noapic nolapic

press enter adn boot from the disk as usual. U may experience a bit of slow performance with the LiveCD but the installed system works Great!

For more info see post #13 of this topic: [http://ubuntuforums.org/showthread.php?t=288669&page=2&highlight=noapic](http://ubuntuforums.org/showthread.php?t=288669&page=2&highlight=noapic)

---

