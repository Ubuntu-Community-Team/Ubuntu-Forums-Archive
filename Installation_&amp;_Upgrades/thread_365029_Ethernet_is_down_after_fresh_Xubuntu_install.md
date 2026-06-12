---
title: "Ethernet is down after fresh Xubuntu install"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by lael on 2007-02-19
I have recently done a Xubuntu Install on my old HP 8693C.

My ethernet was working well When I first used the Live CD.  After completing the Install, I found that I didn't have connectivity.

The LEDs on the back of the Ethernet Card won't even come on when I plug the live cable into it.

lspci tells me that I have a:
```
01:0a.0 Ethernet controller: Acction Technology Corporation SMC2-1211TX (rev 10)
```

When I do a little googling I found that this card should be compatible with the 8139too kernel Module, which I have installed.

I can't even get the LEDs  to light up on the card. Its like it doesn't power up or something.
This is an older computer

The same type of thing happened when I installed Ubuntu on this box.
Any Ideas?

---

### Post by lael on 2007-02-19
Yea...
8139too was definitely the right module...

So I found the problem:

It was a hardware problem.
And a personnel problem.

See I have this 2 year old...  He managed to disconnect 1 out of 5 Cat5 cables, and it happened to be the one I needed.  Not any of my other machines.  Just this one.

Well thats enough time wasted on a silly problem.

---

