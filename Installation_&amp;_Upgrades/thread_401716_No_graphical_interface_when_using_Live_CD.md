---
title: "No graphical interface when using Live CD"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by Edward Hou on 2007-04-04
I was recently trying to install Ubuntu (Edgy) on my computer. I was booting from the live CD and everything was fine until it tried to load the X Windows System. Said something about failing to start the X server, and asking me if I wanted to view the server output.

Well, the output said "(EE) No Devices Detected" and something like "Fatal server error: no screens found." After that I had to deal with the cold blackness of a command prompt, so I rebooted and tried again a few times just to be scientific.

My computer is equipped with some sort of Dell LCD monitor and a "RADEON X300 SE 128MB HyperMemory" graphics. The "HyperMemory" part sounds sketchy. I did some Googling and found that the HyperMemory basically means that it's only a 64MB card and uses 64MB of RAM.
Edit: I meant it emulates a 256MB card by using 128MB of RAM, not 64MB.

Can anyone tell me what I should do to get a graphical interface running on this computer?

---

### Post by ndefontenay on 2007-04-05
Dell screens can bring some surprises.
I've had records of friends who couldn't make it run. Apparently it would work specifically with the original dell PC.

Can you try to configure your xorg.conf

---

