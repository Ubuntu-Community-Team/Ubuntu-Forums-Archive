---
title: "I use synaptic but it tells me to insert cd-rom"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by bleakcabal on 2005-06-06
Hi, I installed Ubuntu yesterday. I used synaptic to install Samba but for some odd reason it tells me to enter the Ubuntu cd-rom in drive.

I tought Synaptic used some online package repository to get the latest version of the software. 

Maybe it knew the one on the cd was the same version but right now im wondering if this is the case...

---

### Post by tread on 2005-06-06
It was asking you for the cd cos the one on the cd was the same version as the one on the net. You can remove this behavior by just commenting out the cdrom line in
/etc/apt/sources.list

(note: you need to sudo gedit /etc/apt/sources.list to edit that file)

---

### Post by bleakcabal on 2005-06-06
Ok thanks, I will do that. 

I don't want to have to reach for the cd when I use Synaptic.

---

