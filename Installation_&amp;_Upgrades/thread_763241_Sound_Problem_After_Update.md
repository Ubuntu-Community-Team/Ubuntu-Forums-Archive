---
title: "Sound Problem After Update"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by amtur_poet on 2008-04-22
I just updated and did the necessary restart for Ubuntu 7.10, but now the sound stopped working. It's a constant mute symbol in the sound icon, and whenever I try to change the settings, I get this error message: "No volume control GStreamer plugins and/or devices found." Is there any idea what update may have caused this, and how to undo it?

---

### Post by Pumalite on 2008-04-22
Post:
lshw -C sound

---

### Post by yahoo on 2008-04-23
I have exactly the same problem - No volume control Gstreamer plugins and/or devices found.

lshw -C sound : 

 *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

What's happened? Getting to not enjoy Hardy right now.

Yahoo

---

### Post by amtur_poet on 2008-04-23
>   *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

That's what the output was.

---

### Post by Pumalite on 2008-04-23
> **amtur_poet said:**
> That's what the output was.
Your new kernel does not recognize the card. Install this:
sudo apt-get install linux-backports-modules-generic
Reboot
Post again:
lshw -C sound

---

### Post by amtur_poet on 2008-04-23
It still doesn't work. I got the same error message.

> *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0


---

### Post by Pumalite on 2008-04-23
I'd do a clean install.

---

### Post by amtur_poet on 2008-04-23
Should I install the new Hardy or my current Gutsy?

---

### Post by Pumalite on 2008-04-23
The new Hardy. I've tested them from Alpha 5 and they are the best OS I've seen in Ubuntu. (I started with 7.04 though)

---

### Post by blindvic on 2008-04-24
I have exactly the same problem. I just installed Hardy beta, but the problem remained.
>   *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2


---

### Post by yahoo on 2008-04-24
The sound problem has been solved for me after the latest update.
Sound now working.
Yahoo

---

### Post by jetpeach on 2008-04-25
do others still have this problem? i'm running Kubuntu 8.04, but have the same "unclaimed" problem for the output of lshw. i'll try the older kernel maybe, see if that fixes it.

lshw -C sound
WARNING: you should run this program as super-user.
SCSI
  *-multimedia UNCLAIMED
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by wandalalakers on 2008-04-25
I don't get the unclaimed error but I don't have sound after the upgrade.

*-multimedia
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by bowenmark on 2008-06-19
After going through the ALSA install all over again, this command worked for me finally:

sudo apt-get install linux-backports-modules-generic

then rebooted, voila.

---

### Post by davsinc2007 on 2008-07-28
Hello I am a newbie and have the same issues as what is in this thread.  I tried what has been discussed with no luck.  I really don't want to re-install Hardy as I have a virtual machine that I installed with a license that will be a pain to re-new.

That being said, I made the mistake of just hitting update on one of the auto update messages.  I don't know which update hosed my sound card.  I am running uBuntu 8.04 and everything was fine until this last update.  I ran the commands listed in this thread.  My output was:
dsinclai@dsinclai-laptop:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
Any ideas on what to check next?

---

### Post by Pumalite on 2008-07-28
Open up all your repos except src and do a:
sudo apt-get update
sudo apt-get dist-upgrade
Then run:
sudo lshw -C sound
again.

---

