---
title: "Install Issues with multiple versions of Ubuntu"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by boisie on 2007-12-29
I recieved a computer from my father , as part of his business move, they got rid of it. I then proceedesd to load Fluxbuntu on it. I worked with it by installing Xfce over fluxbox, and it worked. But then I got $50 towards a RAM upgrade for it, and now I have specs of:

Intel P4 1.8ghz
LG CD-RW
Generic CD-ROM (slave)
one Unknown Manufacturer 30GB HDD
Logitech PS/2 mouse
Generic Dell Keyboard
512MB RAM

When I added the RAM, everything broke. I couldn't boot into my Flux copy, or my windows partition. I had been planning on installing Ubuntu 7.10, but when I tried to install, I got a kernel panic

kernel panic - not syncing: VFS:

There was more, I think it was something about the mount point, but at the end it said [104,0]

I then added the 128MB ram back in, and got a kernel panic

kernel panic - not syncing: Attempted to kill init!

That was with a total of 640mb of ram. Of course I can't try less than 512MB or it just won't install. Everything works fine with only 128MB in though. Any help is appreciated, as I have had some trouble with linux installing on this machine before.

---

### Post by Craigus on 2007-12-29
Boot from a live cd and run the memory test - memtest86+. Do any errors occur ?

If so, the memory is either faulty or not compatible with the motherboard.

---

### Post by boisie on 2007-12-29
Yes, thank you for that, my memory is bad from about MB 256 to 512. I'm getting it exchanged tomorrow.

---

