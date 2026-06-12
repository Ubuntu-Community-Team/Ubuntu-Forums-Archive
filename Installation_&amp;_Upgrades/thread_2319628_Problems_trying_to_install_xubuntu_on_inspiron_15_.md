---
title: "Problems trying to install xubuntu on inspiron 15 7000"
date: 2016-04-06
forum: Installation &amp; Upgrades
---

### Post by Dave_Berry on 2016-04-06
[FONT=arial]Hi, I've been trying to install Xubuntu on my dell inspiron 15 7000 and I'm having issues.
[B]
Specs;[/B]
CPU - [COLOR=#000000]6th Generation Intel® Core&#8482; i7-6700HQ Processor (6M Cache, up to 3.50 GHz)
RAM - [/COLOR]
HD - 128GB Solid State Drive + 1TB 5400 rpm Hard Drive
GPU - [/FONT][/SIZE][COLOR=#000000][FONT=Trebuchet MS][FONT=arial]NVIDIA® GeForce® GTX 960M 4GB GDDR5[/FONT]
[/FONT][/COLOR][FONT=arial]link to laptop for full specs ; [/FONT][URL="http://tinyurl.com/ho4dxt6"][FONT=arial]http://tinyurl.com/ho4dxt6[/FONT]
[/URL][FONT=arial]
The machine comes with 2 HD's, so I created a partition on the SSD of 50GB formatted to EXT4 hoping to get it installed there. The machine has UEFI which I read online can cause issues, in addition I've disabled fast boot on windows as I read online you needed to do that. Made a bootable USB on windows and restarted and I get the error; [/FONT][FONT=arial]nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ UNK08 ]

Read online this has something to do with the laptop using the NVIDIA graphics drivers? I attempted to add nouveau.modset=0 to the grub command line, this didn't seem to do anything. Does anyone have any thoughts? or advice how xubuntu deals with the fact the machine has onboard graphics as well as NVIDIA graphics too? I read on Arch linux they use something called bumblebee in order to handle it?

Thanks in advance.[/FONT][FONT=Trebuchet MS]

[/FONT][COLOR=#000000][FONT=Trebuchet MS]
[/FONT][/COLOR]

---

### Post by mörgæs on 2016-04-06
Which versions of Xubuntu have you tried?

---

### Post by Dave_Berry on 2016-04-06
Just 14.04 Trusty Tahr. Thought it might be the USB drive so I've created and tried a couple, to no success.

---

### Post by mörgæs on 2016-04-06
I suggest that you try 16.04.

---

### Post by Dave_Berry on 2016-04-06
Worked like a charm! thank you!!

---

### Post by mörgæs on 2016-04-06
Good, enjoy and spread the word.

---

