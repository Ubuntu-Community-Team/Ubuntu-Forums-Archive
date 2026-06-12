---
title: "Setting up Ubuntu with a Secure Network"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by Cephyr on 2005-08-22
Hey there

So I set up Ubuntu all fine and dandy, and I must say it has quite the sexy interface. I like.

But, it's not connecting to our home network. I think I know why.

Back when I had windows (24 hours ago), you needed a network key (I think that's what it was called) in order to connect to the network. I THINK this was a WEP key. It was hexadecimal and was something like 6B1B6BFCCB (that's not the actual code, just something like it).

Now, I can't find anywhere to put this wirelss key in Ubuntu. Where do I write it in? I can't seem to find it anywhere.

Thanks a bunch.

---

### Post by nocturn on 2005-08-23
[QUOTE=Cephyr]
Back when I had windows (24 hours ago), you needed a network key (I think that's what it was called) in order to connect to the network. I THINK this was a WEP key. It was hexadecimal and was something like 6B1B6BFCCB (that's not the actual code, just something like it).

Now, I can't find anywhere to put this wirelss key in Ubuntu. Where do I write it in? I can't seem to find it anywhere.

Thanks a bunch.[/QUOTE]

Is your system a laptop with a wireless card?
If your card was detected during install, it would have asked for the key...., what brand/type of card do you have?

---

### Post by Wes24 on 2005-08-23
I think you can find it if you go to System-->Administration-->Networking. Then click on your WLAN device and then on properties. There you can enter the WEP key.

Btw, let me know whether it works, because every time I try to enter a WEP key, Ubuntu freezes. Does anyone know how I can find out what causes this freeze (because I am a total newbie:))?

---

### Post by Cephyr on 2005-08-23
A-ha! Well, I've found the problem, but I think I'm in even deeper doo-doo.

Ubuntu isn't detecting my wireless card. I've got a WMP11 (version 2.0, fortunately.) by linksys. So, I tried ndiswrapper. This didn't work. When I tried to modprobe ndiswrapper it gave me a "operation not permitted" error. So, now I'm off to go try linux wlan. We'll see if this works.

---

