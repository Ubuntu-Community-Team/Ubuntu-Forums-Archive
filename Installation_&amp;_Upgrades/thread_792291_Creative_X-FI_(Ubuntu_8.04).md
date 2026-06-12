---
title: "Creative X-FI (Ubuntu 8.04)"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by DestriAero on 2008-05-12
Installed Ubuntu with no problems. Installed the drivers for X-Fi it seems. I have 2 sound cards (on-board turned off, so two in slots). One of them shows up as default. The X-Fi doesnt show up in the menu dialog.

So I ran "asoundconf list", which returned no result.
Then I ran "lshw -C sound" which returned the following:
```

  *-multimedia:0          
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=sbxfi latency=32 maxlatency=5 mingnt=4 module=sbxfi
  *-multimedia:1
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant
       physical id: a
       bus info: pci@0000:02:0a.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20 module=cx8800
  *-multimedia:2
       description: Multimedia audio controller
       product: ES1370 [AudioPCI]
       vendor: Ensoniq
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=audiopci latency=32 maxlatency=128 mingnt=12 module=audiopci


```

It seems that the X-Fi is recognized, however I cant get sound to play through it and it does not show up in the volume mixer or the sound dialog.

Any help?

Thank you.

---

### Post by DestriAero on 2008-05-12
Trying to Check the permissions on my cards, but I cant understand this. Any help people?

```

t@sonyvaiodesk:/proc$ ls -l /dev/dsp*
lrwxrwxrwx 1 root root 23 2008-05-12 19:41 /dev/dsp -> /dev/oss/audiopci0/pcm0
lrwxrwxrwx 1 root root 23 2008-05-12 19:41 /dev/dsp0 -> /dev/oss/audiopci0/pcm0
lrwxrwxrwx 1 root root 23 2008-05-12 19:41 /dev/dsp1 -> /dev/oss/audiopci0/pcm1
lrwxrwxrwx 1 root root 20 2008-05-12 19:41 /dev/dsp2 -> /dev/oss/sbxfi0/pcm0
lrwxrwxrwx 1 root root 22 2008-05-12 19:41 /dev/dsp3 -> /dev/oss/sbxfi0/pcmin0
lrwxrwxrwx 1 root root  8 2008-05-12 19:41 /dev/dsp_in -> /dev/dsp
lrwxrwxrwx 1 root root 23 2008-05-12 19:41 /dev/dsp_mmap -> /dev/oss/audiopci0/pcm0
lrwxrwxrwx 1 root root 23 2008-05-12 19:41 /dev/dsp_out -> /dev/oss/audiopci0/pcm0


```

---

### Post by DestriAero on 2008-05-12
Help please. It is kinda annoying with an album to record, a 300$ sound card and no way to use it.

---

### Post by DestriAero on 2008-05-13
Come on please

---

