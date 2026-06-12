---
title: "Why is Ubuntu so unstable for me?"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by gck303 on 2011-09-19
I have been trying to use Ubuntu for several months now. It keeps crashing, freezing and otherwise being too unstable to use. 

I suspect it is X crashing. The crashes are often caused by using Firefox or Chrome. 

I have tried 10.04 32 bit, 10.04 64 bit and 11.04.

[I]How can I test my hardware?
[/I]
I have a NVidia 8800GT video card. 

*What version is the most stable?*

Please help! I dearly want to use Ubuntu for my daily computer, but it is proving too difficult to get working. 

George

---

### Post by Basher101 on 2011-09-19
For your hardware, type in a terminal```
sudo lshw
``` and post your output in a code box please. As for the stable version download the latest 10.04 LTS version of Ubuntu

---

### Post by ppv on 2011-09-19
If you can provide us with more details about your computer, it would be a bit easier to help. Just let us know the model number or the specs.
 
If you have a 64 bit processor you can for sure use the 64 bit version.
 
The problems you say may be flash related or related to graphics drivers. In the menu, lookout for additional drivers and install the nvidia drivers.

---

### Post by gck303 on 2011-09-19
I have a Gigabyte _GA-EP45-UD3P_ motherboard
with a quad core Intel processor _Q6600_
and a _NVidia 8800GT_ video card

Attached the output from lshw.

I am using 10.04 LTS. Should I be using the 32 or 64 bit version?

I make use of VMWare so would rather use 64 bit so I can use all of my 6GB of memory. 

George

---

### Post by dino99 on 2011-09-19
my way to install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

about 32/64:

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

note: 32 bits is more stable and if you install the generic-pae kernel (with synaptic) then all the ram is used.

note2: you can try to fix graphic driver issue with synaptic:
- remove/purge (right click) all the nvidia packages installed
- remove/purge all the jockey packages installed
- reinstall: jockey-gtk, nvidia-current, nvidia-common, nvidia-settings, nouveau, dh-modaliases
- then reboot and check driver activation (additional drivers, from menu)

you can watch warnings/errors from /home/user/.xsession-errors (ctrl+h to unhide it) and from /var/log/

---

### Post by gck303 on 2011-09-19
> note2: you can try to fix graphic driver issue with synaptic:
- remove/purge (right click) all the nvidia packages installed
- remove/purge all the jockey packages installed
- reinstall: jockey-gtk, nvidia-current, nvidia-common, nvidia-settings, nouveau, dh-modaliases
- then reboot and check driver activation (additional drivers, from menu)

I have already tried using the nvidia drivers and found that the display or computer would freeze. Currently I am using it would having any specific video drivers installed. The unstablity persists. 

Incidentally, I have a dual-dvi and large 30 inch monitor. Could be contributing to the problem?

What would you recommend?

---

