---
title: "No sound, snd_intel8x0, ALSA."
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by vedad on 2005-09-28
Hi,
any help with this, please? I have tried all the recepies I have found in forums. None have worked. I get no error messages. The system sound works but no sound comes out when I play a CD. Playing mp3 files with vlc gives neither error message nor sound.

lspci | grep audio gives
----------------------------------------------------------

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

lsmod | grep snd gives
-------------------------------------------------------
snd_intel8x0 29984 1
snd_ac97_codec 64608 1 snd_intel8x0
snd_pcm_oss 47652 0
snd_mixer_oss 16768 2 snd_pcm_oss
snd_pcm 84872 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 23300 1 snd_pcm
snd 50276 6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 9824 2 snd
snd_page_alloc 9604 2 snd_intel8x0,snd_pcm
--------------------------------------------------------------------------------------------------------------

lspci -v gives

----------------------------------------------------------------------------------------------------------------
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
Subsystem: IBM: Unknown device 0537
Flags: bus master, medium devsel, latency 0, IRQ 11
I/O ports at 1c00 [size=256]
I/O ports at 18c0 [size=64]
Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
Memory at c0000800 (32-bit, non-prefetchable) [size=256]
Capabilities: <available only to root>


0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA])
Subsystem: IBM: Unknown device 0530
Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
Memory at e0000000 (32-bit, prefetchable) [size=128M]
I/O ports at 3000 [size=256]
Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <available only to root>


-------------------------------------------------------------------------------------------------------------------------


I have tried to disable sound server at start up. Didn't help.

ANY HELP WOULD BE GREATELY APPRECIATED!

vh

---

### Post by John.Michael.Kane on 2005-09-28
you can try this [http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

