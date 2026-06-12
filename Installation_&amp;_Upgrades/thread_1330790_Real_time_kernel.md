---
title: "Real time kernel"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by masux594 on 2009-11-18
Good evening to everyone.. 
This is my situation: i've virtualbox with a xp guest. It runs veeeeery slow.. when i start an app in the guest, i see that in the task manager, the CPU goes to 100% of usage and the kernel [xp] usage goes to 100% too.. So, in some forums i've read that i need to install the rt kernel using ```
sudo apt-get install linux-image-rt linux-headers-rt
``` to improve the situation.. but, this command install:

[LIST]
[*]linux-image-2.6.28-3-rt
[*]linux-rt-headers-2.6.28-3
[*]linux-headers-2.6.28-3-rt
[/LIST]
kernel that i doesen't use .. I currently have the [custom]2.6.31.5 kernel installed, so, is there a way to install the 2.6.31.5 realtime kernel instead of 2.6.28?

Sysc, A

P.s. : Tnx for the time!
P.p.s. : I have an AMD 4600+ [2 x 2.4Ghz] on a x64 Jaunty!

---

### Post by masux594 on 2009-11-19
bump =|

---

### Post by masux594 on 2009-11-23
nobody knows? :neutral:

Sysc, A

---

### Post by masux594 on 2009-11-26
.. Hmm, no way? Nobody knows how to install the 2.6.31 rt kernel?? so sad..

Sysc, A

---

### Post by Ollboll on 2009-12-04
install "linux-rt" and you should get the whole package.

---

