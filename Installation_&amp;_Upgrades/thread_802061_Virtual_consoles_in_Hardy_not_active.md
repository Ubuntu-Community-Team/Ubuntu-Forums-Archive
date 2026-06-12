---
title: "Virtual consoles in Hardy not active"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by briggella on 2008-05-21
I started with a beta install of hardy which I have gradually upgraded to the standard release via updates, but when I try and switch to a Virtual Console, nothing happens. It just stays at the GUI.

If I open a terminal and run

ps -A|grep tty
4694 tty4 00:00:00 getty
4695 tty5 00:00:00 getty
4697 tty2 00:00:00 getty
4700 tty3 00:00:00 getty
4701 tty6 00:00:00 getty
5523 tty7 00:00:01 Xorg
5640 tty1 00:00:00 getty

Then they are all there. Anyone got any ideas?


Further info

I have installed this on a new dual core athlon with an nvidia 6100 graphics card

I have just installed production hardy on a Thinkpad A31 which has run VCs in gutsy and edgy without problem and ran hardy with VCs until I ran the updates. Now the VCs have stopped working on this too. I have checked that the VCs are not switched off in the Xorg.cong, I have run modprobe fbcon and nothing appears to have made any difference.

I notice that googling shows this to be a common problem, but as yet no-one has a solution.

---

### Post by briggella on 2008-05-22
Further Info

I have noticed that if I stop the X server with Ctrl-Alt-backspace, then I can access the VCs if I am quick. Once back at the login gui then nothing happens again. The keys do respond if I check with xev in a terminal. I wondered if this was related to the variation in keyboard layout between the GUI and text mode. The settings are not wildly different to that used in my Gutsy install when it all worked.

Any clues at all?

---

### Post by briggella on 2008-05-24
I have tried all manner of keyboard settings, none of which make any difference. The curious thing is that on the Thinkpad it did work until the updates started to come.


Is this a recurrence of this bug

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/24073](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/24073)

Does it need resurrecting?

---

