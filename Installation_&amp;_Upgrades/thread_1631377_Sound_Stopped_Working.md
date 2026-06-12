---
title: "Sound Stopped Working"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by thorn1 on 2010-11-26
Hi, sound was working fine yesterday and now nothing.

I found the instructions, Comprehensive Sound Problem Solutions Guide  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

And did the following:

$ aplay -l
aplay: device_list:223: no soundcards found...

(it finds the card)

$ lspci -v

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Dell Device 01ed
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel

$ modprobe snd-
FATAL: Module snd_ not found.

I reinstalled the drivers but still no luck. So I tried get the source and compile them to but I get an error:

modules/alsa-driver/.pc/hwptr_pcm_io_fixes.patch/.timestamp
tar: cd: Not found in archive
tar: Exiting with failure status due to previous errors

I wonder if it's something else. I noticed that I can not get to my second disk, it says "unable to mount file system. Not Authorized" Is this related to the sound problem? Permissions?  It was also working before.

Thanks, Greg

I'm using Ubuntu 10.04 LTS  - the Lucid Lynx

$ uname -a 
Linux gano 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux

---

### Post by khelben1979 on 2010-11-26
I am not sure how things looks like over there, but if the correct driver for the sound device have been loaded, then preventing another sound device from taking over that can be fixed by using something which is called: blacklist.

In /etc/modprobe.d/ you can blacklist the current sound driver which gets used by your Ubuntu system by editing the configuration file.

I am not sure if this is the solution to your problem, but at least it will prevent the intel audio device from getting loaded at startup if you choose to blacklist it.

---

### Post by thorn1 on 2010-11-26
> **khelben1979 said:**
> I am not sure how things looks like over there, but if the correct driver for the sound device have been loaded, then preventing another sound device from taking over that can be fixed by using something which is called: blacklist.

In /etc/modprobe.d/ you can blacklist the current sound driver which gets used by your Ubuntu system by editing the configuration file.

I am not sure if this is the solution to your problem, but at least it will prevent the intel audio device from getting loaded at startup if you choose to blacklist it.


OK, thanks I'll take a look at the blacklist files.

I still find it  strange that it was working yesterday.  I have not messed with anything to do with sound. 

Greg

---

### Post by thorn1 on 2010-11-26
I seemed to have fixed it. I went to do a shutdown and it would only go to the login screen. I powered it off and restarted and the sound is ok and I am able to access the disk. I guess it was in some messed up state. Thanks, Greg

---

