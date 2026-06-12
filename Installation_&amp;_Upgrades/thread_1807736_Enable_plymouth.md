---
title: "Enable plymouth"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by Burillo on 2011-07-19
Hi all

A little background - my machine has nVidia GT 230M so plymouth never really worked with nVidia's binary driver.  i remember going great lengths (but don't actually recall which exactly) to disable that ugly blinking "Kubuntu 11.04...." thing and replace it with console output. I never used nouveau because it deadlocks my GPU within minutes after booting.

Now i discovered the nouveau "noaccel" option and surprisingly no deadlocks and no performance penalty whatsoever (maybe i don't use anything involving acceleration, desktop looks the same as it did with nVidia binary driver - including all compositing, fancy KWin effects etc.). So i decided to get the splash screen back. Unfortunately, i am not able to, and as i already said earlier, i don't recall what is it that i did to remove it.

I tried reinstalling plymouth packages. I checked upstart entries. My kernel boots with "ro quiet splash" (i'm using BURG). Is there any other place i can look?

---

### Post by Burillo on 2011-07-20
bump

---

### Post by Burillo on 2011-07-24
bump

---

### Post by Burillo on 2011-07-25
bump

---

### Post by Burillo on 2011-07-26
buuuump

---

### Post by dino99 on 2011-07-26
sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure plymouth

---

### Post by Burillo on 2011-07-26
nope, didn't help

still "quiet" console output only

---

### Post by Burillo on 2011-07-28
buuump?
i reeeeeely don't want to install everything from scratch... I think i'll wait for oneiric then

---

### Post by Burillo on 2011-07-28
ooops sorry for doublepost

---

### Post by Burillo on 2011-07-31
strange thing - i upgraded to KDE 4.7 via Kubuntu backports PPA, and i saw a splash screen. it happened only once (on first boot into KDE 4.7). any ideas?

---

### Post by Burillo on 2011-08-02
I have reinstalled natty (crashed my root partition) but for some reason there's still no plymouth.

I am using nouveau. It worked when booting from LiveCD. It **didn't** work on the first boot. It still doesn't work. Any ideas?

---

### Post by Burillo on 2011-08-02
I've played a bit with BURG's GRUB_GFXPAYLOAD setting and checked hwinfo to see which framebuffer modes are supported by my hardware. Turns out that i was trying to set an incorrect framebuffer mode, and this is why it wasn't working.

Now the million dollar question is - why did it work on a LiveCD?

---

