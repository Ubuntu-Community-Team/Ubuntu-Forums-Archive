---
title: "Sound Problems"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by Joseph Elliott on 2006-10-21
Hi, I just replaced my motherboard and now the only sound i get is a constant clicking.  when i unplug the speakers the sound stops and with the old motherboard there was sound so i dont believe its the speakers.  I am now using a ASRock K7VM3 motherboard. everything else works but i cant seem to find a setup utility for the sound.  can anyone help me?.

---

### Post by Kateikyoushi on 2006-10-21
Follow this guide. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

---

### Post by Joseph Elliott on 2006-10-21
Thanks, I follwed the instructions in that thread and compiled the driver the instructions say to return to step 4 of the general help.

sudo modprobe snd-via82xx

if that fails then im supposed to post here if i have already compiled the driver.

the error message i got when i entered the above command was

joseph@joseph-desktop:/usr/src/alsa/alsa-driver-1.0.13$ sudo modprobe snd-via82xx
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-rawmidi.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-pcm.ko': No such file or directory

i restarted my system and checked the bios, everything looks good

tried it again and got this 

joseph@joseph-desktop:~$ sudo modprobe snd-via82xx
Password:
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-rawmidi.ko': No such file or directory
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.15-27-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.15-27-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-rawmidi.ko': No such file or directory
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.15-27-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-27-386/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.15-27-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_via82xx (/lib/modules/2.6.15-27-386/kernel/sound/pci/snd-via82xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_via82xx

i dont know what to do.

---

### Post by rmjb on 2006-10-29
Hello, it seems like the driver didn't compile properly. Can you redo the step that asks you to compile the driver and post the output of that command?

- rmjb

---

### Post by Joseph Elliott on 2006-10-31
Hi, I reinstalled the whole system, sorry rmjb i didnt get to read your question before doing it and everything is working properly now. Something must have screwed up the first time, maybe a bad disk. Thanks for everyones help.  

joseph Elliott

---

