---
title: "Interrupted Upgrade from 7.10 to 8.04"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by jdpellegrino on 2008-05-27
Ok so I am looking for some help here. I started an upgrade from 7.10 to 8.04 last night and before it could finish the power got cut. So now the installation is totally hosed and I am not sure how to proceed. The best I can do is get to single user mode and I do have both the upgrade CD and the regular CD. I am hoping I can continue the upgrade and/or do a recovery with the CD in single user mode. So how is that done? I realize there may not be enough info here but if someone asks I'll provide whatever information is necessary. Thanks. :)

---

### Post by mano cazalet on 2008-05-27
can you do a normal login or get out to terminal during boot(ctrl+alt+F1) or if not boot to recovery mode and do:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by jdpellegrino on 2008-05-27
> **mano cazalet said:**
> can you do a normal login or get out to terminal during boot(ctrl+alt+F1) or if not boot to recovery mode and do:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

I can't do a normal log in. I went to single user (recovery mode) and at the prompt typed: dpkg --configure  -a
It went along for a while and then died. There were many error along the way along the lines of:

dpkg: depenndenccy problems prevent confiiguration of eog:
  eog ddepends on ....
  ... is not yet configured

dpkg: too many errors, stopping
dpkg: ../../src/pakcages.c:252: process_queue: Assertion `!queuelen` failed.

What else can I try?

ETA: Ok got it. Thanks. :) 

Now how do I remove the older kernels from grub. And not just from the menu but permanently.

---

