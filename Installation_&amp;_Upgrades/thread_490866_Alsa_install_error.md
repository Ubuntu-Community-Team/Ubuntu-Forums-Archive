---
title: "Alsa install error"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by skar0059 on 2007-07-02
I installed the alsa-module from source, and I can find the header file in /lib/modules/$(uname -r).  But when I reboot, I get several errors stating 
snd_hda_intel: Unknown symbol snd_verbose_printd
snd_hda_intel: Unknown symbol snd_hidden_kzalloc
....

After the boot the header file does not exist in /lib/modules/



  Does anyone have any suggestions?


  Alsa 1.0.14 install commands
   used:
./configure --with-oss=yes --with-sequencer=yes --with-cards=hda-intel --with-kernel=/lib/modules/2.6.20-16-generic/build --with-debug=detect
make
sudo make install-modules
sudo depmod -ae

---

### Post by djchandler on 2007-07-03
> **skar0059 said:**
> I installed the alsa-module from source, and I can find the header file in /lib/modules/$(uname -r).  But when I reboot, I get several errors stating 
snd_hda_intel: Unknown symbol snd_verbose_printd
snd_hda_intel: Unknown symbol snd_hidden_kzalloc
....

After the boot the header file does not exist in /lib/modules/



  Does anyone have any suggestions?


  Alsa 1.0.14 install commands
   used:
./configure --with-oss=yes --with-sequencer=yes --with-cards=hda-intel --with-kernel=/lib/modules/2.6.20-16-generic/build --with-debug=detect
make
sudo make install-modules
sudo depmod -ae

skar0059,

Didn't the install CD detect your sound card when you ran the trial/install CD?
I don't know for sure about ALSA, but I know there is an xorg.conf created when the trial/install CD runs. You can find the alsa.conf file in /usr/share/alsa. I'll bet one of those is created when the install cd runs. Create a folder in your root directory (not home/root) which you can only do as su. Edit the permissions on the folder so anybody can write to it. 

Boot from the trial/install CD. Become su by hitting alt-F2 and enter

GKSU "nautilus"

Find /usr/shar/alsa. Copy the alsa.conf file to the unrestricted shared directory on your hard drive, or you can use a USB thumb drive or floppy. Reboot from your hard drive and then copy the file in the shared folder over to /usr/share/alsa and reboot. If you had sound while using the trial/install CD, you will have sound after doing this.

If that doesn't work, try using Synaptic to reinstall alsa.

DJ

---

### Post by skar0059 on 2007-07-03
I booted to the live cd, and I do get sound.  But when I run a diff between the alsa.conf files I find no difference.  Somehow the alsa-driver is not loading.  I compared the modprobe.d/blacklisted files and they are the same.  i am not certain why they do not download.  I tried reinstalling alsa from the package manager, but I have had no help

  Check out my pastebin for a more detailed error message (snd_hda_intel)
pastebin.ca/601014

---

### Post by djchandler on 2007-07-03
> **skar0059 said:**
> I booted to the live cd, and I do get sound.  But when I run a diff between the alsa.conf files I find no difference.  Somehow the alsa-driver is not loading.  I compared the modprobe.d/blacklisted files and they are the same.  i am not certain why they do not download.  I tried reinstalling alsa from the package manager, but I have had no help

  Check out my pastebin for a more detailed error message (snd_hda_intel)
pastebin.ca/601014

Maybe alsa isn't the problem. Could be OSS (open sound system). Have you tried playing around with your settings in **Sound** under **Preferences**?

DJ

PS Wish I could be more help -- I'm using a Via 8237. Maybe someone else with an Intel chipset could help. Which Intel chipset are we talking about?

---

### Post by djchandler on 2007-07-03
> **djchandler said:**
> Maybe alsa isn't the problem. Could be OSS (open sound system). Have you tried playing around with your settings in **Sound** under **Preferences**?

DJ

PS Wish I could be more help -- I'm using a Via 8237. Maybe someone else with an Intel chipset could help. Which Intel chipset are we talking about?

Where is this coming from? Is your sound device on a card or motherboard? I wouldn't think this should be in the startup unless you have a REALLY old mother board. That was a slot architecture that never really caught on because of pci coming from intel. Once again, what is the chipset on the motherboard? I do not mean to nag you about this, but this is starting to look more like something going on that the kernel can't handle due to something unusual.
> 
[22.294821] EISA: Probing bus 0 at eisa.0
[   22.294829] Cannot allocate resource for EISA slot 1
[   22.294831] Cannot allocate resource for EISA slot 2
[   22.294833] Cannot allocate resource for EISA slot 3
[   22.294835] Cannot allocate resource for EISA slot 4
[   22.294850] EISA: Detected 0 cards.



Maybe I have just never considered any probing for EISA slots going on. Seems like a time and resource wasting process to me unless your hardware calls for it.

DJ

---

