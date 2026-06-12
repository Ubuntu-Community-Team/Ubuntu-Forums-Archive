---
title: "no sound after upgrade to 7.10 Gusty"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by marcocec on 2008-01-27
I've installed verion 7.04 all driver work fine, and after upgrade to 7.10 the sound is not working, which command do I use to enable it?? Driver installed right

---

### Post by rrwo on 2008-01-27
It's a common problem, with many causes. First see [the comprehensive sound problems solutions guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound").

---

### Post by Pumalite on 2008-01-27
Post:
lshw -C sound

---

### Post by marcocec on 2008-01-27
root@spud:~# lshw -C sound
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

### Post by Pumalite on 2008-01-27
What is the result of typing this in your Terminal:
alsamixer

---

### Post by marcocec on 2008-01-28
the command was  "lshw -C sound"

---

### Post by Pumalite on 2008-01-28
We are way beyond that. Give me the result of typing 'alsamixer' in your Terminal (followed by 'Enter')

---

### Post by marcocec on 2008-01-29
If I try this "alsamixer" it edit the alsamixer vulum panel

---

### Post by Pumalite on 2008-01-29
Adjust all the volumes to 100%

---

### Post by Metalbuntu on 2008-01-29
> **Pumalite said:**
> Adjust all the volumes to 100%

YES, cause its embarrassing spending 2 days trying to get the sound to work and the computer volume be off.

---

### Post by marcocec on 2008-01-30
I tried but still not to work, it desapeared the OSS mixer in the application bar...
How can I reload it??


PLEASE PLEASE HELP ME!|!! I want to listen to my music:guitar:

---

### Post by marcocec on 2008-01-30
Following a troubleshooting it says that to stop the OSS mixer and then reload it with a command
It doesn't reload ye. Yesterday I've installed the right alsa driver last realase...
How can I do??

---

### Post by marcocec on 2008-01-30
The volume bar it desappered and I don't know I to make reloaded it...
Help me with this and then we'll see the next step to OSS mixer

---

### Post by marcocec on 2008-01-31
I successfully installed all alsa driver into own directories but when I type "alsamixer" I reciev this error

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by Pumalite on 2008-01-31
Try this link:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

