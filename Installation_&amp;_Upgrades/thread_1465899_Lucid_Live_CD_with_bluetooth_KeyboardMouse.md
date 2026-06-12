---
title: "Lucid Live CD with bluetooth Keyboard/Mouse"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by TariBuntu on 2010-04-29
Now here's one for you.

All excited about the new 10.04 I booted the freshly downloaded Lucid, just to find out that I can't go past the first screen on the live cd.

My Logitech DiNovo combo is ignored, even the good old pre-9.04 "plug-out dongle/plug-in dongle" routine yields nothing.

Go figure! One step forward, two paces back... :-k

So now I'm back in my trusty Koala, where bluetooth works out-of-the-box, just as it did from the beginning, unable to find out anything further about the anxiously awaited Lucid - apart from the fact that it's violet-ish.

So...

If someone knows a way to boot into it, without re-wiring everything and temporarily changing half of the hardware, let me know. [-o<

---

### Post by Peter09 on 2010-04-30
Looks like this?
 
> [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/553964](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/553964)

---

### Post by TariBuntu on 2010-04-30
Thanks for the post, looks like it's the same thing, though I cannot confirm anything "from inside" since I have no wired peripherals at hand to boot into Lucid...

It's a good thing to know there is a workaround, yet I'd like to find a way to actually enable the devices at boot time.

---

### Post by mesilliac on 2010-04-30
I just got stung by this when I upgraded. No alternate keyboard or mouse, so I couldn't even log in to try pairing.

However it seems that the old behaviour is brought back by changing a udev file. You can follow the instruction in this comment to see if it works for you:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10)

from bug:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288)

Of course you can't change the file on the live-CD... but for those who already upgraded this might help.

---

### Post by TariBuntu on 2010-04-30
> **mesilliac said:**
> I just got stung by this when I upgraded. No alternate keyboard or mouse, so I couldn't even log in to try pairing.

However it seems that the old behaviour is brought back by changing a udev file. You can follow the instruction in this comment to see if it works for you:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10)

from bug:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288)

Of course you can't change the file on the live-CD... but for those who already upgraded this might help.

Many thanks mesilliac. I finally borrowed a USB keyboard to get me started, and did a clean install.

After doing the suggested editing, I am back to bluetooth again. I can't mark the thread solved, though - the initial problem remains for those who are yet to install.

To summarize: People you can get your Logitech dongle running, but ONLY after you somehow managed to install. Described [here]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10").

---

### Post by malrost on 2010-05-01
Confirmed that [this fix]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10") worked for me after installation. 

My Logitech Edge bluetooth keyboard was not functional after install. I had an USB mouse handy and was able to make the changes using the onscreen keyboard.

---

