---
title: "No sound in Hardy"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Lagos on 2008-04-29
I upgraded my Gutsy install to Hardy. Everything went smoothly, except my sound stopped working. 
When I go into the sound properties, I can get audio working again by selecting the ALSA driver (pidgn system sounds work), however when try to play a video or audio file in totem, it gives me an error that the audio device is busy. 

Any ideas? 
I have a feeling this has something to do with pulse audio.

---

### Post by Lagos on 2008-04-29
help?

---

### Post by TheVille on 2008-04-29
Hey.

What kind of sound card / audio interface are you using? I have same problem -> No startup sound, no sound in amarok nor xmms. I can't preview system sounds in sound settings... Though I can hear the beep in sound settings' front page "test" button. Also, I can play back mp3's in Totem. Pidgin sounds work as well.. Totally strange.

My setup is: WinXP home / Ubuntu Hardy dual boot (upgraded to hardy this morning, had no problem in gutsy) Fujitsu Siemens Scaleo, intel 2,9 mHz, 512 mb DDR. My Audio interface is ESI emu1010 which is VIA's envy24 chip powered to my understanding, and use the ICE1712 driver.

Anyone got clue about what is going on?

---

### Post by Lagos on 2008-04-29
Im using an m-audio delta66. Worked totally fine under gusty.

---

### Post by TheVille on 2008-04-30
okay. Delta66 utilizes the exactly same envy24 chip so it must be somehow related to that. I found interesting article [http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/) which holds answer to our problems, but I can't test it myself right now (going to work soon). Maybe you could try that and reply how it worked?

The method rebuild ALSA modules, and sound issues should be gone...

---

### Post by Lagos on 2008-04-30
I tried it, but it didnt help. 
Alsa works fine, but totem claims another app is using the audio device. 

I think the problem is with pulse audio.

---

### Post by Pumalite on 2008-04-30
This might help:
[http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)

---

### Post by Lagos on 2008-04-30
> **Pumalite said:**
> This might help:
[http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)

i just did that. didnt help.

---

### Post by Pumalite on 2008-04-30
Post:
lshw -C sound

---

### Post by Lagos on 2008-04-30
^ you just made me realize that my super expensive sound card was actually made by VIA...haha


 *-multimedia            
       description: Multimedia audio controller
       product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
       vendor: VIA Technologies Inc.
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ICE1712 latency=32 module=snd_ice1712

---

### Post by Pumalite on 2008-04-30
Type 'alsamixer' in your Terminal and tell me the result.

---

### Post by Lagos on 2008-04-30
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: M Audio Delta 66                                                       &#9474;
&#9474; Chip: ICE1712 - multitrack                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: IEC958 [H/W In 0]                                                      &#9474;
&#9474;                                                                              &#9474;
&#9474;                       &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;                       &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;  H/W In 0 PCM Out     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;                       &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                         0        0        0         0       80       80      &#9474;
&#9474; < IEC958 >IEC958 1    ADC     ADC 1    ADC 2     ADC 3     DAC     DAC 1     &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by Lagos on 2008-04-30
just to be clear... alsa seems to work. I can hear pidgin, but not totem, and i also dont get any logon/off system sounds.

---

### Post by Pumalite on 2008-05-01
Just in case; turn all the volumes to 100%

---

### Post by Lagos on 2008-05-01
I did. It didnt help. 
Totem is reporting that something else is using the audio device so its not a volume issue.

I think whats happening is that totem is trying to use pulse audio, but pulse audio isn't working correctly with my sound card. I need to either get pulse audio working, or remove it.

---

### Post by Pumalite on 2008-05-01
This might help:
[http://www.google.com/search?hl=en&q=Pulse+Audio+in+Hardy&btnG=Google+Search](http://www.google.com/search?hl=en&q=Pulse+Audio+in+Hardy&btnG=Google+Search)

---

### Post by Lagos on 2008-05-01
I just tried sudo pkill pulseaudio, and now i have audio in totem. So pulse audio is the problem. I guess i need to uninstall it for a perm fix.

---

### Post by Lagos on 2008-05-01
just tried pulseaudio -vv and i got this error..


E: module-alsa-sink.c: Failed to create sink object
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_1412_1712_sound_card_0_alsa_playback_0"): initialization failed.

---

### Post by Pumalite on 2008-05-01
Tere are quiet a few bugs reported on Pulse Audio.

---

### Post by qgfreire on 2008-05-01
I had the same prob. No sound . aplay -l says no soundcard!!!

In the forum I saw that the problem arise principally with Intel 82801DB-...
Somewhere I found that it was because linux-ubuntu-modules-2.6.22... where not well installed.
Going crazy with no soundcard in aplay -l I was prepared to try anything (even tried to apt-get remove alsa, dont do it!!!).

So I did uname -a
and I saw linux-ubuntu-modules-2.6.24-16-386

in synaptic I saw that I have not -386 but -generic.
so I remove all linux-ubuntu-modules and simultaneously I mark the linux-ubuntu-modules-2.6.24-16-386 for installation.


Surprise, surprise!!! No reboot nothing, sound again !

Ubuntu is the best because it's community is the most participating! Don't you think so?

---

### Post by DukeNuke2 on 2008-05-01
> **Lagos said:**
> I did. It didnt help. 
Totem is reporting that something else is using the audio device so its not a volume issue.

I think whats happening is that totem is trying to use pulse audio, but pulse audio isn't working correctly with my sound card. I need to either get pulse audio working, or remove it.

in the upper right corner is the volume tool... right mouse click and then "delete from panel"... reboot you system and try again...

---

### Post by Lagos on 2008-05-01
> **DukeNuke2 said:**
> in the upper right corner is the volume tool... right mouse click and then "delete from panel"... reboot you system and try again...

Tried it, didn't work.

---

### Post by cnewswanger on 2008-05-01
I have the same problem with a M-Audio Delta 1010lt card.
It appears that the driver is not enabled in the kernel!
look here:

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/204974](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/204974)

How to fix it? I don't know.  Does anyone else?
Should I switch back to 7.04? Install another sound card?

---

### Post by Lagos on 2008-05-01
> **cnewswanger said:**
> I have the same problem with a M-Audio Delta 1010lt card.
It appears that the driver is not enabled in the kernel!
look here:

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/204974](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/204974)

How to fix it? I don't know.  Does anyone else?
Should I switch back to 7.04? Install another sound card?

I dont think that bug is accurate. At least not in the final version of hardy. 
I am able to have fully working sound if I: 

1. change the sound options from auto detect to ALSA
2. sudo pkill pulseaudio

So thats proof that the kernel is compatible with the sound card, but the issues im having are with pulse audio. 

So for now i have to pkill pulseaudio everytime i log on. Hopefully the ubuntu team will issue some updates to pulse audio in the near future that fix these issues.

---

### Post by xen-uno on 2008-07-21
Same situation here with an M-Audio 2496. Killing PulseAudio corrects problem with Totem. I've uninstalled all PA code except where dependencies would wipe out multimedia apps ... so the PA process is still reloading everytime after login.

---

