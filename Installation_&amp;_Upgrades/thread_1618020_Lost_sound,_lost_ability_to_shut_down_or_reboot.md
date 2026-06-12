---
title: "Lost sound, lost ability to shut down or reboot"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by wliebenberg on 2010-11-10
About two weeks ago I installed Ubuntu 10.04 from disk onto my HP Compaq nx8220, then promptly downloaded and installed more than 200 MBs of updates, and everything was fine, apart from the fact that my laptop would no longer detect my sound card (aplay -l shows no devices), and it had lost the ability to shut down when I click on shut down. It would simply sign me out of my account, and the only way to shut down is to hold to in the power button. 

Alsamixer shows I have an Intel ICH6, and the chip is Analog Devices AD1981B.

I followed the Sound Troubleshooting suggestions on the Ubuntu web site and purged and reinstalled the ALSA drivers. This required a restart, and then sound worked and I would be able to shut down and restart normally. Or shall we say, sound 'sort of' worked, in the sense that I would still hear sound coming from the laptop speakers when I had a headphone in the headphone jack. 

However, whenever I do restart the laptop, I lose my sound again, as well as the ability to shut down and restart!

Since then I have followed another sticky under the Multimedia and Video forum that explained how to rebuild ALSA from source, and I've also added changes to the alsa.conf file. I've also added my sound module snd-intel8x0, to /etc/modules. Nothing has changed. The only thing I saw after having rebuilt ALSA and having made the conf and modules additions, was that I had sound afterwards, but that the sound would echo whenever it played, sometimes for five or six times.

A subsequent restart has once again nullified the entire effort and I am back where I started. Alsamixer has also disappeared, i.e. the alsamixer command no longer works.

---

