---
title: "no sound or free DMA engines..."
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by kfealz on 2007-08-24
I just installed Feisty on my newly built rig and have been having some problems.  Luckily because of the amazing support of the ububtu community, i haven't had to post anything on the forums until now because searching google has turned up everything i've needed. Thanks! :)

So here's my problem..

I have Intel HD Audio plugged into the AAFP port on my ASUS P5B wifi mobo.  At first, I had AC97 cable plugged into it and I had sound for a few minutes, then it disappeared.  So I switched the cables to see if it would make a difference.  With either cable plugged in, I hear the ubuntu startup sound, but as soon as the desktop loads, there is an 'X' over the volume button which says, "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured." when clicked.   DMESG returns "[  774.400769] n<1>hdaudio: hda: No free DMA engines."  I have searched google to my limit and can not find the reason for this.  Any ideas?  Also, a friend had me try "cat /proc/asound/cards" thinking i would get some helpful output, but I do not have an "asound" directory.  

Any help would be greatly appreciated.  Thanks!

---

### Post by kfealz on 2007-08-24
UPDATE:

OK, this may simplify things... When I run "soundoff" then "soundon" my sound comes back, though the error message still comes from clicking on the volume manager.  I just tried running rhythmbox and movie player at the same time playing different mp3s and it worked, but if I load firefox and go to pandora.com (awesome site btw), my sound disappears and the DMA errors start coming.

The following are the output of dmesg after soundoff & soundon:
[ 3123.643889] n<6>ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 3131.412730] usbcore: deregistering interface driver ossusb
[ 3135.222474] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[ 3135.225756] hdaudio: Unknown HDA codec 0x11d4198b
[ 3135.253326] usbcore: registered new interface driver ossusb


hope this helps narrow it down for you all.  I'm still stumped, but at least I have some sound :)

---

### Post by kfealz on 2007-08-24
Also, if it helps, I just installed Cedega and passed its OSS test, but failed the ALSA test.

---

### Post by kfealz on 2007-08-26
still no ideas?

---

### Post by kfealz on 2007-08-29
This was my solution.
[http://4front-tech.com/forum/viewtopic.php?p=6159#6159](http://4front-tech.com/forum/viewtopic.php?p=6159#6159)

---

