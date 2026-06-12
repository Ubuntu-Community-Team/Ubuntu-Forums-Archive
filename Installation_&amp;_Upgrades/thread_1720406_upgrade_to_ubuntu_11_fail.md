---
title: "upgrade to ubuntu 11 fail"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by geiroffenberg on 2011-04-03
This has turned to be a horrible day.
I have enjoyed ubuntu 10.10 for a while on my dual boot setup with win xp.

Today i decided to upgrade to 11 beta, to give back to the coommunity.

Well, after the upgrade i could boot into ubuntu 11 one time, but it ran very slow.

When i re booted, it could not see my win xp partiotion anymore, and i can not boot into xp anymore.

But as it starts to load ubuntu 11, i get "input no supported" and the screen is blank. I have tested the graphics card and it is fine and works. thats not the problem. Ubuntu 11 upgrade messed up my boot system, and it messed up something with the monitor.

Im not a novice to computers, but i havent ran ubuntu for more than a few months. 
However, right now i've tried everything in my power and knowledge, and am without a computer at all because of the ubuntu 11 upgrade. 

It took a while before i could calm down enough to write this with out falling into the temptation and turn it into a hate message, im just saying.

/geir

---

### Post by Quackers on 2011-04-03
So you are not getting a grub menu when you boot, it seems.
In that case, during boot hold down the shift key. This should bring up the grub menu. Try the recovery item and see if that boots to a desktop.
WHat graphics card is in use?

---

### Post by geiroffenberg on 2011-04-03
> **Quackers said:**
> So you are not getting a grub menu when you boot, it seems.
In that case, during boot hold down the shift key. This should bring up the grub menu. Try the recovery item and see if that boots to a desktop.
WHat graphics card is in use?

Thanks for your reply. i cant tell how much it means! i ve just tried to sleep for three hours because i got so depressed, lol!

Hi, yes i manage to see "grub loading" JUST before the "input not supported" comes up and the screen just turns to black, with that warning sign blinking.

 nvidea geforce (cant remember the number right now)

---

### Post by geiroffenberg on 2011-04-03
Anyways quackers, because of your post, i figured grub must be running in the background! So i remember that the xp partition always ends up in the bottom of the list in grub, so i pushed down arrow a bunch of times and return, and it actually started up xp. At least i'm in. Thanks a trillion  to you.
 
However, its apparant that the ubuntu 11 install has messed up something! :(

---

### Post by Hedgehog1 on 2011-04-03
Several beta testers have had this same grub issue.

The fix for them has been to set the screen size for grub to 640x480

If you would do this:

```
gksudo gedit /etc/default/grub
```

*Change this line:*

**#GRUB_GFXMODE=640x480**

*To this:*

**GRUB_GFXMODE=640x480**

*Removing the '#' turns this line from a comment to an active line.*

After saving and exiting the file, then do this:

```
sudo update-grub
```

You can now reboot, and you should **see** the grub menu.


***The Hedge***

:KS

---

### Post by geiroffenberg on 2011-04-03
thanks the hedge, and quackers. Thats very helpful.
I personally gave up on v. 11 since it ran extremly slow.
I reinstalled 10.10 and everything is back to normal with the execption that ubuntu now can't understand my mobile internet usb stick which has run extremly well up til now. It just finds the usb stick and says it cant mount it because its an unknown filesystem, vfat. Very strange, because thats what surprised me so much in the beginning, that this thing worked out of the box in ubuntu 10.10, despite that the internet seller said it would never work in linux.

---

### Post by geiroffenberg on 2011-04-28
Just want to thank you guys again. Both of you have saved my life, lol.
Hedgehog1, i upgraded to 11.04 today, and the problem with blackscreen on grub menu persisted as before.
Tried your solution from this thread, and it WORKED LIKE HEAVEN!

i'm so happy i could fart rainbows!

---

