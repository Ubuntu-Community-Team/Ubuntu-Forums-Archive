---
title: "Custom Install Image?"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by null-cipher on 2008-09-09
Hi there, I am the "Ubuntu Guy" in my city of Rotorua, all the way down in New Zealand.
The business I work for, TalkTechNow is one of (the only?) companies in Rotorua that support Ubuntu machines, and OEM build them.

I was however, curious as to how I could make a custom Ubuntu installation ISO image.
We already have a PXE server that Auto installs Ubuntu, I was just wondering if there was a way I could make an image with all the configuration/extra packages/custom art that we have to manually change when we install Ubuntu on our computers.

Perhaps an effective shell script would also be useful?

Any help would be greatly appreciated. :D

---

### Post by Partyboi2 on 2008-09-09
maybe you could use something like [[COLOR=Blue]remastersys[/COLOR]]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

---

### Post by null-cipher on 2008-09-10
Thanks for the suggestion. Remastersys does look like something that I could use. However, further investigation shows that PXELINUX can only boot from "kernel" images. Not disk images.

Hmmm.
I think perhaps a customising shell-script would be more appropriate.

---

### Post by null-cipher on 2008-09-12
I'm going to mark this thread solved, and post elsewhere regarding a shell-script or a .deb.
Thanks for the help. :)

---

