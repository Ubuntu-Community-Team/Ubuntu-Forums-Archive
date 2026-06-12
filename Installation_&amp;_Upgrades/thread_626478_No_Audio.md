---
title: "No Audio"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by Zebadim on 2007-11-29
Hi All,

I have just installed Ubuntu Gutsy Gibbon on my new laptop. Everything seems to be working fine except the audio - there is no sound whatsoever. Considering my absolute lack of experience with Linux systems (yes, another newbie) can someone direct me to a possible solution?

Running the alsamixer command gives the following information:

- Card: HDA Intel; Chip: Raltek ID 268

Thanks in advance.

Zebadim

---

### Post by logos34 on 2007-11-29
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Zebadim on 2007-11-29
Hi,

Thank you very much for the link and attention.

I was reading the instructions provided and the the follwing issues might help diagnose  the problem better:

1) I don't have any sound since the beginning of the instalation.

2) aplay -l command provided:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

3) the lspci -v provided:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

4) the alsamixer only had four things active: Master, PCM, Caller I, and Off-hook

5) The soundcard is working with Windows Vista

6) I tried to look for the driver in the Alsa project but the site seems unavailable, I will keep trying.

Thanks in advance,

---

### Post by logos34 on 2007-11-29
> **Zebadim said:**
> 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
      
...

6) I tried to look for the driver in the Alsa project but the site seems unavailable, I will keep trying.

It might be **snd-intel-hd**

Try this check:
[http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)

---

### Post by xc3RnbFO8P on 2007-11-30
> **Zebadim said:**
> Hi,

Thank you very much for the link and attention.

I was reading the instructions provided and the the follwing issues might help diagnose  the problem better:

1) I don't have any sound since the beginning of the instalation.

2) aplay -l command provided:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

3) the lspci -v provided:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: **COMPAL Electronics Inc Unknown device 0025**
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

4) the alsamixer only had four things active: Master, PCM, Caller I, and Off-hook

5) The soundcard is working with Windows Vista

6) I tried to look for the driver in the Alsa project but the site seems unavailable, I will keep trying.

Thanks in advance,

I got the same on my Znote laptop, and this thread helped.

[http://ubuntuforums.org/showthread.php?t=551615]("http://ubuntuforums.org/showthread.php?t=551615")

I installed the latest alsa driver

1. Delete /lib/modules/`uname -r`/ubuntu/media/snd-hda-intel/snd-hda-intel.ko  (or rename it snd-hda-intelx.ko)
2. Re-compile alsadriver
3. gedit /etc/modprobe.d/alsa-base
4. add the line "options snd-hda-intel model=**toshiba**"
5. If the file /etc/modprobe.d/snd-hda-intel.modprobe exists then make sure the options snd-hda-intel line has model=toshiba

The file    **snd-hda-intel.ko**  in my computer  is in /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda
and  /usr/src/alsa-driver-1.0.15rc1/modules

---

