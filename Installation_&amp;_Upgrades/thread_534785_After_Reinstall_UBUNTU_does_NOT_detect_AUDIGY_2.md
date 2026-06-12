---
title: "After Reinstall UBUNTU does NOT detect AUDIGY 2"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by rsampaio on 2007-08-25
I reinstalled UBUNTU on my machine and after the reinstall ubuntu does not recognize my sound card anymore. I have an Audigy 2 Platinum EX. I am a complete newb so if you guys need me to post anything here please just ask. By the way I am using 7.04.

-raph

---

### Post by Pumalite on 2007-08-25
Check your sound driver in System>Preferences>Hardware Information. Post what you find.

---

### Post by rsampaio on 2007-08-25
I posted screenshots of what shows there, I couldnt find the soundcard... maybe I am just blind lol

---

### Post by Pumalite on 2007-08-25
I can't see the controller for your card in the shots. Check your connections, etc

---

### Post by ahurtt on 2008-01-25
Did this problem ever get solved?  I just installed Kubuntu 7.10 for AMD 64 for the first time ever in a dual boot configuration with Windows XP Pro.  I installed a brand new physically separate hard drive for installing Kubuntu on.  The install went fine but the system didn't detect my PCI Sound Blaster Audigy 2 card when I booted into Kubuntu.  Worse yet. . .now when I boot into windows it can't detect the sound card either.  Everything on my windows box had been working fine previously.  Now the sound card doesn't even appear in the windows hardware device manager and my computer has gone mute.

---

### Post by Pumalite on 2008-01-26
Post:
lshw -C sound

---

### Post by bethebunny on 2008-01-26
I am having a similar problem with my new build. AMD64 64-bit 8.04 Hoary Heron (Also had the problem with Gutsy, upgraded to Hoary 'cause I'd heard it was easier to make a driver work with Radeon HD3870 graphics cards, no luck with that yet either x.x)
Sound card works perfectly in Vista, but for sound in Ubuntu I need to plug my speakers back into the Mobo sound slot.

Here's my card as shown in lshw -C sound:  

*-multimedia
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: 3
       bus info: pci@0000:04:03.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106

Any ideas why it might be dumb?

---

### Post by Pumalite on 2008-01-26
Your sound card and the module is loaded. Post the results in the Terminal of the following:
alsamixer

---

### Post by bethebunny on 2008-01-26
It's using my onboard sound card instead of the PCI one. Is there any way to change this?

---

### Post by Pumalite on 2008-01-26
Check in your BIOS

---

### Post by bethebunny on 2008-01-26
I tried messing with some of the alsamixer settings, tried disabling my onboard audio card to no avail. Actually before I started screwing around system sounds such as the startup and logout sounds were played even when the sound card was hooked up, now they don't. Any more ideas?

---

### Post by Pumalite on 2008-01-26
Go back to your onboard sound card and look for appropriate driver

---

### Post by bethebunny on 2008-01-26
A fine solution, but for the fact that the windows driver for my onboard sound card doesn't support halflife 2, which is really the only reason I use windows. So every time I change OSes I need to pull out my comp and move the speaker jack. There should some solution to this problem that doesn't involve physically modifying the computer. Thanks for the help, anyways.

---

