---
title: "Bad upgrade!"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by Zver on 2006-08-18
Hi all!

Today i've upgraded my ubuntu computer and i was dissapointed. Somehow i've upgraded xorg or perhapse his lib and now my desktop is just WILD.

In the same upgrade i've also broke synaptic :o. When I wanted to start synaptic there was error that libvte.so.4 was not found.

I've repaired synaptic like this:
```

cd /usr/lib
ln -s /usr/lib/libvte.so.9 libvte.so.4

```

Now synaptic works but xorg is stil wild.

<b>Now i'm asking youif there is some way to remove this "new upgrades" sow that my desktop will be normal again. Or is there any other way?</b>

I have ATI Radeon 8500 graphic card, DELL 2405FPW LCD display. I'm running normal xorg and i have XGL installed (i've tested it but it runs only when XGL session is started). My graphic driver is fglrx.

---

