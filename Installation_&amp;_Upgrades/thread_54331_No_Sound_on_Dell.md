---
title: "No Sound on Dell"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Zcool on 2005-08-04
HIya can anybody help, i cant get any sound on my Dell Optiplex gx1.
When ever i try to play a cd it won't play, just changes to pause symbol for afew seconds then baack to play one.
I've tried it after a normal install and also after the unofficial add-on cd install.
some details of comp are 
General  
Microprocessor type Intel® Pentium® II microprocessor with MMX™ technology 400mhz

Internal cache KB (16-KB data cache, 16-KB instruction cache)

L2 cache memory 512-KB pipeline burst, 4-way set-associative, write-back SRAM

Audio 
Model Crystal Semiconductor 
Chip set 

i've got a newer comp but dont want to go to trouble until i tried it out on this one and i want to know what cd ripping n burning is like. 

Thanx for any help.

---

### Post by chantal on 2005-11-04
Hi Zcool. I'm using Ubuntu 5.04 on my Dell 400 with Pentium 2 - 333MHz, and I've managed to get the Crystal Sound 4236B chip working. It's not perfect as after each boot I've got to type "alsamixer" in the terminal, unmute the first column (Digital output) and increase its volume to max. The second column (PCM playback) has got to be up too. I used the following command to install the  crystal driver while connected to the net:
sudo modprobe snd-cs4236
sudo apt-get install esound-clients
The CS4236 chip is on the motherboard and is connected to the ISA bus rather than the PCI bus, which explains why the Ubuntu install routine doesn't find it.
The Alsa system doesn't fully support the old CS4236 chip, so I leave the Multimedia Systems Selector preferences as follows:
Sound Sink     : Enlightened Sound Daemon (ESD)
Sound Source: Open Sound System (OSS)
Btw, you get to the OSS controls via Applications/Sound & Video/Volume Control
The CS4236 driver should be ok for chips from 4232 to 4237, I've heard.
Sorry it's not very clear as I'm a newbie to Ubuntu too.

---

### Post by holomate on 2005-11-27
[QUOTE=chantal]
sudo modprobe snd-cs4236
sudo apt-get install esound-clients
[/QUOTE]

Error Message:
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.12-10-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
FATAL: Error running install command for snd_cs4236

That might not be the correct onboard sound chip for the GX1 (or possibly Dell made several models of GX1).

---

