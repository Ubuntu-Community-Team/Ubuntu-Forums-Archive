---
title: "Hard Drive Size Not Recognised for Install"
date: 2014-06-07
forum: Installation &amp; Upgrades
---

### Post by Patrick_Burke on 2014-06-07
Complete newbie - 
Recently bought a 20GB Hard Drive IBM ThinkPad 660x 770 and installed it on to my old IBM think pad T41.
Trying to install Ubuntu 11.04 from CD - 
there is a screen which has a tick next to 'is plugged in to a power source' and ticked 'is connected to the internet' But an X next to 4.4GB available on drive space.
As I have a new 20GB drive I am lost and therefore cannot install - any help gratefully received.:confused:

---

### Post by oldfred on 2014-06-07
Is this a Lubuntu installer?
And is system 32 bit or 64 bit?

Post this from terminal in live installer:
sudo parted -l

---

### Post by Patrick_Burke on 2014-06-08
Thanks for responding which is greatly appreciated.
Sadly I do not know how to find out if this is a 32 bit or 64 bit.

After running the command you kindly provided, I get the following (my italics):
[I]Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label

[/I]Thanks again.
PB

---

### Post by oldfred on 2014-06-08
That error is just saying you cannot write to your sr0 device which is your CD/DVD player. Most DVD are read only so error can be ignored.

I was just curious to what else the parted command might show about existing partitions.

---

### Post by Patrick_Burke on 2014-06-09
Thanks Oldfred - I have decided to take this to one of the 'gurus' at work - it will only cost me a pint but thanks again for your help.

---

