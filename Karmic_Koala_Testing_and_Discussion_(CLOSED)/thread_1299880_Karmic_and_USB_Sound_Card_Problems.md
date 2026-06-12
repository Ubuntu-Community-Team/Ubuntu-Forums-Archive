---
title: "Karmic and USB Sound Card Problems"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by koolcracker on 2009-10-24
So I upgraded to Karmic, and I was hesitant on whether or not to post this until the official release came out, but I figured I'd give it a go.

I have a Creative Xmod that worked flawlessly under Jaunty, but now in Karmic for some reason my computer thinks its a 5.1 sound card, which it most certainly is not. It is a simple stereo card, but I can either assign it to be a stereo INPUT, or a minimum of a 4.0 output, and up to a 5.1.

This causes problems because whenever I try to adjust my onboard sound, it thinks its adjusting different channels and my sound cones out all tinny.

Basically, does anyone know why this all of a sudden thinks I'm using a surround sound card and any possible way to get it to go back to a simple 2.0 output?

---

### Post by cucisan on 2009-10-26
i also have an xmod, it gets recognized correctly if you look at dmesg, but i cannot switch to it using the "sound preferences"-gui there is nothing under "sound output" but i can configure it for "sound input"

really strange.. used to work out of the box with jaunty..

volumeknob works though..

edit: ok after logging out/loggin in again i got the same problem as you: 4.0 or 5.1 output.. funky

---

