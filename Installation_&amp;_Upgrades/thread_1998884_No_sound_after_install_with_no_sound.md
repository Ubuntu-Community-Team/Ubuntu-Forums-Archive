---
title: "No sound after install with no sound"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by Doles284 on 2012-06-07
Hey guys, long time reader, first time poster...

I was having some issues with sound on a server backup machine that I have set up with rsync to run at boot and mirror the files on my server and until now, that has been it's sole purpose.

I recently moved it into another spot where it can also be used as a mythtv frontend. So I install the necessary packages and when I went to run MythTV, there was no sound :frown:

After doing lots of ALSA and Pulse troubleshooting, I realised that I had the Sound card disabled in BIOS #-o Genius, I know. I must have turned it off for some strange reason.

Anyway, after enabling it again, there is still no sound. I assume this is because there was no sound detected when Ubuntu was installed, so no sound driver was compiled.

I did some more trouble shooting and even upgraded to the latest Kernel, but it didn't fix the sound problem.

This isn't life and death, I can reinstall or use another machine, but I was really like to make this a multifunction machine and hope there is a quick fix.

It's an Intel Motherboard
```
doles@gibson-backup:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Device a201
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at 50200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
```

```
doles@gibson-backup:~$ sudo aplay -l[sudo] password for doles: 
aplay: device_list:223: no soundcards found...
```

---

