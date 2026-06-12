---
title: "I broke my sound."
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by RageMachine on 2013-11-09
Well as the title says i brokes my sound.... I just got my duo boot windows 8 and ubuntu 12.04 working a few days ago, no problems everthing was soomth, started wathing some youtube videos and noticed that my 5.1 sround wound wasnt workig right. so i did some googing and found that i had to edit the daemon.conf, so i did and now my sound dusnt work at all.thx in advance hope we can get it fixed.

i have 5 souund devices all work but the onbored 5.1
name of sound device : speackers built in audio
things ive tryed to get it working again:

restoring the config file - didnt work
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
then reinstalled and forced a reload - didnt work

system specs:

GA G1 Sniper M5 mobo
intel core i7 4770K
8gb ram
Gigabyte GTX 760
2tb hdd 
2 ssds one for windows 8 and one for ubuntu

edit: i just noticed that i am also missing the sound icon from the top right now. 
solved icon error with 

sudo apt-get install indicator-sound

---

### Post by prshah on 2013-11-09
> **RageMachine said:**
> that i had to edit the daemon.conf, so i did and now my sound dusnt work 

Hello,

Can you please post your daemon.conf file, so that we can see what changes you have made.

Sound indicator not appearing is typically because pulseaudio is not running; can you start pulseaudio daemon (service) from the terminal, and report back error messages (Esp those related to daemon.conf): Dash-Terminal, then give the command```
pulseaudio --start
``` and please report back output.

---

