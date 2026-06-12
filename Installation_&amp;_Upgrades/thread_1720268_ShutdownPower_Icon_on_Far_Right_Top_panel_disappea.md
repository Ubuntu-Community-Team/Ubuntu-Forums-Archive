---
title: "Shutdown/Power Icon on Far Right Top panel disappeared..."
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by sgriggly on 2011-04-03
Hey everyone.

After a recent upgrade, the red power icon in the far right of the upper panel disappeared. In its place is a half obscured copy of my user name, which appears right next to my user name (along with the chat icon). The chat icon/user name is functional, as it is supposed to be, but the half obscured user name that replaced my shutdown/restart power icon is just a bug, and has no function. Not only is it unsightly, but I miss the power icon. Yes, I can right-click on the panel and add one, but it doesn't allow me to drag it all the way to the far upper-right corner, where it is supposed to be located... I found this post in another thread: sudo apt-get install indicator-applet-session, but it did nothing to solve my problem... Any and all help is appreciated! I'm running 64-bit 10.10, btw, if that makes any difference...

---

### Post by Dutch70 on 2011-04-03
Try right clicking the panel & select "add to panel". I'm on 11.04 right now, so I can't test it to see exactly which one it is, but you should be able to find it in there and add it back to your panel. 

If you're successful with that, try locking it to your panel & hopefully that won't happen again.

Also, may I suggest Cairo Dock.

---

### Post by Frogs Hair on 2011-04-03
The applet name is indicator applet session , it is the applet that includes your name. There is also an applet called shutdown and that is its only function.

---

### Post by sgriggly on 2011-04-03
> **Dutch70 said:**
> Try right clicking the panel & select "add to panel". I'm on 11.04 right now, so I can't test it to see exactly which one it is, but you should be able to find it in there and add it back to your panel. 

If you're successful with that, try locking it to your panel & hopefully that won't happen again.

Also, may I suggest Cairo Dock.

like i said, i already tried that... yes, i have a power button on my panel, but it isn't were it's supposed to be, and i can't drag it to where it's supposed to be, the far-right-hand upper corner.

---

### Post by madjr on 2011-04-03
> **sgriggly said:**
> like i said, i already tried that... yes, i have a power button on my panel, but it isn't were it's supposed to be, and i can't drag it to where it's supposed to be, the far-right-hand upper corner.

unlock them.

---

### Post by sgriggly on 2011-04-03
> **madjr said:**
> unlock them.

it isn't locked to the panel... i can drag it around the middle portion of the panel. but i can't drag it to the far right corner.

---

### Post by Dutch70 on 2011-04-03
This things giving you headaches huh. ](*,)

The other icons that are blocking it need to be unlocked before you can move anything across them. 

Whew, I remember going thru that.

---

### Post by sgriggly on 2011-04-03
hmmm... that makes some sense. so, i unlocked username/chat icon. i unlocked time/date icon. next to the left is the wireless icon, that doesn't appear to unlock? same with the blue tooth... then i 
have my SCIM keyboard, also doesn't unlock, and dropbox... 

still can't get that power button over there...

---

### Post by Dutch70 on 2011-04-03
There is a very small area to the left of those icons that you can click to unlock them. They will probably all move together.

---

### Post by sgriggly on 2011-04-03
you did it! yes. thank you! got it. ;)

---

### Post by safarin on 2011-04-03
> **sgriggly said:**
> hmmm... that makes some sense. so, i unlocked username/chat icon. i unlocked time/date icon. next to the left is the wireless icon, that doesn't appear to unlock? same with the blue tooth... then i 
have my SCIM keyboard, also doesn't unlock, and dropbox... 

still can't get that power button over there...

Hi sgriggly,

I also facing this problem before, and a lots of people facing this problem.
And then I found some useful script to reset the this gnome-panel and all of its applet to default.

I already share this script in this threads. How about you try it.

[[SOLVED] Disappearing panel icons]("http://ubuntuforums.org/showthread.php?t=1716534&page=3") 
post #23

If this thing happen again (this happen to me), I reset back.. :P

---

### Post by Dutch70 on 2011-04-03
> **sgriggly said:**
> you did it! yes. thank you! got it. ;)

Great! glad to hear you got it worked out. I can't help but smile a little cause I remember going through the exact same thing. 

By all means, don't ever make the mistake of deleting your network manager icon...lol. 

Best regards
Dutch

---

