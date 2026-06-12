---
title: "Problem with fan, video driver and restart since Gutsy upgrade"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by simonfiction on 2007-10-22
Hi,
I have upgraded to Gutsy a couple of days ago and have been trying to get over a few problems since. Firstly and most importantly, I had a lot of video problems. I was prompted with a screen asking me to configure my monitor and graphics card in some kind of low graphics mode. I did this and couldn't find my model of card (nvidia 8600) but decided there was no harm in trying the "test" button with one of the nvidia drivers. Unfortunately, the test button simply made my screen go blank and after waiting several minutes, had to do a hard reboot. On this reboot, a dialog asking me to configure my monitor and card didn't display at all. I eventually booted into gutsy by restoring a backup of the xorg.conf file from the command prompt but I think I'm using an opensource driver, so no opengl support and compiz doesn't appear to be successfully starting. I don't have any drivers available in the restricted drivers tool though, anyone know why this is? I know there is a proprietary driver available for my card as I was using it in Feisty Fawn. Is there a way of checking which devices are using what drivers?

Secondly, since upgrading the fans in my computer are making a lot of noise. With Feisty Fawn, the fans would make a lot of noise and then seem to quieten down or turn off (?) once it got to the login screen.

Lastly, when trying to reboot my computer from Ubuntu it seems to go through the whole shutdown process but doesn't actually manage to reboot. It just hangs and I have to hold in the power button. i seem to remember having this problem once before but some how it just dissapeared?

Any help is much appreciated,
Thanks!

PS If it helps I'm running a desktop dell Dimension 9200. I can provide more hardwar information if it's needed. Thanks,
Si

---

### Post by simonfiction on 2007-10-23
A quick update on my problem if anyone can help... I've managed to solve my video and fan woes but I'm still unable to restart my computer. Also, I can't seem to launch the compiz configuration tool from the system menu but do successfully have compiz running. Has anyone else experienced this at all?

Thanks,
Si

---

### Post by rakku-toki telkio-kuuni on 2007-10-25
Sorry, I don't have an answer, but a question:

How did you manage to fix you fan noise issue? I have the same problem here...

Thank you

---

### Post by simonfiction on 2007-10-26
The fan issue resolved itself after installing the restricted video card driver from the restricted drivers tool. Hope that helps.

---

