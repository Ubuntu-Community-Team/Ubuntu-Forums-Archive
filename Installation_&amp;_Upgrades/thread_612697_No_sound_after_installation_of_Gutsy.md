---
title: "No sound after installation of Gutsy"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Donnw on 2007-11-14
I have just done a clean install of Gutsy, everything seems ok but I have no sound output. I have a creative audigy sound card that worked fine in fiesty and is working in windows as normal. It doesn't work from the live cd either.  Looking in hardware information it looks as though it has been detected.  I have also checked the alsa mixer and all seems Ok there too. 
This seems to be a bug in Gutsy as I have never had any problems with other distros. If I cannot get it to work I will have to reinstall Feisty and and then try an upgrade.  Has anyone   got an answer?

---

### Post by Pumalite on 2007-11-14
Try:

sudo apt-get install linux-backports-modules-generic

---

### Post by Donnw on 2007-11-14
Thanks for the very fast reply, I have tried your suggestion but there has been no change

---

### Post by Pumalite on 2007-11-14
Post:

 sudo lshw -C sound

---

### Post by Donnw on 2007-11-14
IDE                       
  *-multimedia     
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 7
       bus info: pci@0000:05:07.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1

Not sure what all this means?

---

### Post by Pumalite on 2007-11-14
It means your card is recognized and the module is loaded. Get all the GStreamers. Also:
sudo apt-get install ubuntu-restricted-extras

---

### Post by IF-Rit on 2007-11-14
i've got a same problem after i **sudo lshw -C sound**
this is a result...
could you analyze mine too....
thanks before

  *-multimedia            
       description: Audio device
       product: SB450 HDA Audio
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

---

### Post by Donnw on 2007-11-14
I have tried loading the restricted drivers and the Gstreamers but there is still no difference

---

### Post by micdhack on 2007-11-14
same problem here also...
i installed on my desktop gutsy and i have:
onboard sound card which is recognized and setuped as default
creative audigy which is as far as i can see recognized but its not on the list to make it as default but it is on the sound maanger
and also a tv which i dont care if its recognized or not 
and last a usb camera mic which is recognized but i will look at it later.

here is my list:
```
  *-multimedia:0          
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: 5
       bus info: pci@0000:00:05.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci
  *-multimedia:1
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia:2
       description: Multimedia video controller
       product: Bt878 Video Capture
       vendor: Brooktree Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=bttv latency=32 maxlatency=40 mingnt=16 module=bttv
  *-multimedia:3 UNCLAIMED
       description: Multimedia controller
       product: Bt878 Audio Capture
       vendor: Brooktree Corporation
       physical id: c.1
       bus info: pci@0000:00:0c.1
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm cap_list
       configuration: latency=32 maxlatency=255 mingnt=4

```

Now since i see that audigy is recognized maybe the problem is telling to the system that this is the default...how can i do this?

EDIT: i tested it using audacious and audigy plays normal but not with 5.1 though...but still i cant find a way to make it default

---

### Post by Donnw on 2007-11-15
I have finally solved the problem after a lot of playing around. The answer was very simple - go to the volume control icon in the right hand corner of the screen, open the Alsa mixer, select the switches tab and uncheck the 'Audigy Analog/Digital Output Jack' option. This must be happening to a lot of people trying Ubuntu for the first time. Does anyone know why this is selected on as Default? Surely most people use analogue speakers as default? As always thanks for the help.

---

### Post by micdhack on 2007-11-15
What are you saying for analog digital jack its true..This must be unchecked..Im guessing alsa doesnt support it.
As for the other problem i solved it by:
Getting the list of sound cards
> sudo asoundconf list
Setting as default the one i want
> asoundconf set-default-card soundcard Replacing soundcard with mine
And i used this command to test my surround 5.1:
> speaker-test -D surround51 -c 6
which after some digging on volume control and enabling from preferences new menus i manage to get it to work

---

