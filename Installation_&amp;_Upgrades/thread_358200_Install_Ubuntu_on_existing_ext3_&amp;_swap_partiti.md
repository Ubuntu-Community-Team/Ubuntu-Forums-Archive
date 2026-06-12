---
title: "Install Ubuntu on existing ext3 &amp; swap partitions troubles (noob ahoy)"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by mlk on 2007-02-10
I used partition magic with WinXP to create an extra 3 partitions: two ext3 (about 3 gig each) and a swap file (1gig)

Why does ubuntu try to install itself on my main partition and what can I do about it ?

[img]http://mlkdesign.online.fr/dump/ubunta.jpg[/img]

I've tried changing some flags (I have no idea what most are) but it keeps telling me 'No Root File System' (I edited the following so that my 68gig partition remained untouched, is that the problem ?)

[img]http://mlkdesign.online.fr/dump/ubuntb.jpg[/img]

Thanks for any help

I hope this is not the last bit of Ubuntu I'll ever see =)

---

### Post by mikewhatever on 2007-02-10
Check [this gude]("http://psychocats.net/ubuntu/installing") for some more pictures. The root partition should only have "/" without the quotes, that is your Ubuntu partition.

---

### Post by housam on 2007-02-10
Don't use partition magic to create partitions for ubuntu. Instead use Gparted , it is on the live cd.

---

### Post by mlk on 2007-02-11
Thanks for your prompt replies !

I will try to use gparted :KS

---

