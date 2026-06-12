---
title: "No sound either with OSS or ALSA?"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by RSahlgren on 2008-03-30
I don't have any drivers wrong or something. So i guess it's the settings.. But how to i fix this..

---

### Post by Pumalite on 2008-03-30
Post:
lshw -C sound

---

### Post by RSahlgren on 2008-03-30
Here:

```
*-multimedia:0 UNCLAIMED
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=5 mingnt=4
  *-multimedia:1
       description: Multimedia controller
       product: SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 2
       bus info: pci@0000:04:02.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=32 mingnt=84 module=saa7134
```

---

### Post by Pumalite on 2008-03-30
You have two cards. One is not recognized by th kernel. The 2nd one is recognized and the module is loaded. It might be a matter of configuration.
What's the result of typing this in your Terminal?:
alsamixer

---

### Post by hps on 2008-03-30
I was about to post the same question so if its ok  could you help me out      here is the output for 
 lshw -C sound



 *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP55 High Definition Audio
       vendor: nVidia Corporation
       physical id: f.1
       bus info: pci@0000:00:0f.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2


Thanks in advance and other than this problem my upgrade went in with no problems

---

### Post by RSahlgren on 2008-03-30
Here:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

---

### Post by Pumalite on 2008-03-30
Alsa has to be linked to the first card.
You could try this; but I give no assurances at all. You may end up with both cards UNCLAIMED:

sudo apt-get install linux-backports-modules-generic

---

### Post by RSahlgren on 2008-03-30
Now what?

---

### Post by RSahlgren on 2008-03-30
I have another question, If i get the sound working on ubuntu, can i get it working over wine. For an example steam games?

---

### Post by Pumalite on 2008-03-30
Reboot.

---

### Post by RSahlgren on 2008-03-30
It did as you said it might do. I don't have any device now..

---

