---
title: "Issues with Karmic on MBP 5.1"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aybara on 2009-09-24
I have installed Karmic on my MBP 5.1, and it works pretty well. I have a couple of issues though, and maybe someone else has run into others.

1. Wireless is not working. I installed the restricted Broadcom drivers I was offered, but I still have only wired networking.

2. Sound works out of the box, but when I plug in headphones, sound still plays on the internal speakers.

---

### Post by Niels den Otter on 2009-09-25
I don't have your first problem. Wireless works fine using the STA drivers (bcmwl (5.10.91.9+bdcom-0ubuntu4) karmic) and current networkmanager.

On my macbook I have the same sound problem. Difficult travelling by train ;-)

-- Niels

---

### Post by alexmurray on 2009-09-25
See my post [here]("http://ubuntuforums.org/showpost.php?p=8008119&postcount=12") for getting the wireless drivers properly installed.

I also have the same audio problem (speakers not being muted when using headphones) so I just work-around this by turning down the master volume (by using the volume control keys on the keyboard) when using headphones since the headphone volume is not affected by the master volume - although it seems if you set the master to zero headphones are muted as well, but if you have master at just above zero headphones work fine and speakers don't produce any audible sound)

---

### Post by Aybara on 2009-09-26
After yesterdays update I removed all broadcom packages on my system, and then:

1. Added the STA driver, and got wireless working.
2. Rebooted, and STA driver and wireless was gone.
3. Added the STA driver again, and wireless was working.
4. Rebooted, and it was still there.

Not logical, but at least I ended up with working wireless.

alexmurray: Thanks for the soundadvice, it was sound advice. Do you think we need a fix/patch in alsa to get this working, or is it Ubuntu that doesn't tell alsa to do the right stuff?

---

### Post by alexmurray on 2009-09-26
Its a problem with the upstream ALSA driver - it doesn't have support for detecting when headphones are plugged in from what I know.

---

