---
title: "WPA2 Personal - Unable to connect"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Brotherbrat13 on 2010-04-18
Using Beta 2.

After lots of pushing and shoving to get my wireless card to work, I can't connect to networks. I can see the network on the list, and can connect to the point of where it asks for my password. I enter my password, and 2-3 minutes later it asks me again (During those 2 minutes, I don't have internet) to enter my password. This continues in an endless cycle until I give up entering the password. Any attempts at helping would be appreciated!

---

### Post by kid1000002000 on 2010-04-25
Confirmed, same problem.  Bump

---

### Post by davidmohammed on 2010-04-25
same here - gave up in the end and changed my router to just give WPA.  That works a treat.

I have read that wicd is better with WPA2 than the default network manager.  Never tried myself though.

---

### Post by Brotherbrat13 on 2010-04-25
Some more Info..

I'm using a Paraphrase, not a pass key generated from a paraphrase.

---

### Post by rbmorse on 2010-04-25
I know this is anathema to some Linux users, but on my machine with an RT2860-based USB wireless dongle I can sometimes get it working by rebooting the system.  Has to be a reboot...restarting the network doesn't do it, nor does logging the user out and logging back in.  Reboot has about a 60% success rate the first time, >90% the second.

---

### Post by Brotherbrat13 on 2010-04-25
Bump

Would love a solution. Don't want to have to re-set up the wireless in all of my family members computers.

---

### Post by Brotherbrat13 on 2010-04-26
Bump. Again.

---

### Post by dagrump on 2010-04-26
It makes it very hard to help some one that gives no info on their hardware or what they have tried. It took a week for some else to even chime in.
There are some things that you need to know or it's just W.A.G. (wild *** guess). Hardware info at least, the more info the better.
I use WPA personal & am not having these issues. I have several different generations of Linksys cards.

---

### Post by Brotherbrat13 on 2010-04-26
WPA2 Personal on the Linksys WUSB100 Ver.2 Wireless USB Stick connecting to a Linksys WRT400N at 2.4 GhZ (The Router also Broadcasts 5 GhZ)

---

### Post by Ibidem on 2010-04-27
Saw something like OP w/ broadcom, b43/wireless-compat (Beta 1).
Saw same thing w/ Atheros AR5007 & Madwifi, using Wicd?!?

The last is odd, given how madwifi is...

---

### Post by lucasta on 2010-04-27
i've always had to use wicd for WPA2 networks.  couldn't find any workaround for the default gnome network manager

---

### Post by homeless4ever on 2010-04-27
I don't know if this will help, but I have this same problem with my RT2870-based wireless card and I solved it by blacklist the rt2800usb module.

---

### Post by Miguel on 2010-04-27
> **rbmorse said:**
> I know this is anathema to some Linux users, but on my machine with an RT2860-based USB wireless dongle I can sometimes get it working by rebooting the system.  Has to be a reboot...restarting the network doesn't do it, nor does logging the user out and logging back in.  Reboot has about a 60% success rate the first time, >90% the second.

No need to reboot. Before doing that, I'd find which one is the kernel module that makes your wifi card "work". Try unloading and reloading the module. In my case (Intel WiFi Link 5300) it's iwlagn, and this is how I do it:
```

$ sudo modprobe -r iwlagn
(wait a bit)
$ sudo modprobe iwlagn

```

Of course, as soon as you remove iwlagn you lose any posibility of wireless connection until you insert the module again.

EDIT: You could have a peek at dmesg to see why the module would be the culprit.

---

### Post by Brotherbrat13 on 2010-04-29
I will try some of the fixes when I get home today, hopefully before the forum closes.

---

