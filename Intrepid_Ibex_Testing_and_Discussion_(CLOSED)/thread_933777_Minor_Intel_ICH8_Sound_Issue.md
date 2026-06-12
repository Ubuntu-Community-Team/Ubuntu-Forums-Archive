---
title: "Minor Intel ICH8 Sound Issue"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Rumplesmigskin on 2008-09-29
From what I can glean from the Internets, a couple of Intel integrated sound cards seem to be being abused somewhat by the Intrepid kernel. I've got an Acer 2920 Gemstone laptop here with an Intel 82801H HD audio controller - worked fine on Hardy, but I now get rather nasty pops and crackles whenever I try to use the sound device.

But it's working at least. Would anyone have an idea of how to restore its former glory?

[Link: Famous alsa-info.sh output]("http://www.alsa-project.org/db/?f=cece99dda0c205ee2b4b7ea5d9986cabdbe344a7")

Other misc. info:
```
lspci | grep Audio: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1b.0 0403: 8086:284b (rev 03)

```

(Another point which may be pertinent: I'm not installing from de.archive.ubuntu.com due to some external traffic limiting, but instead from ftp.wh-netz.de/ubuntu.)

---

### Post by psyke83 on 2008-09-29
> **Rumplesmigskin said:**
> From what I can glean from the Internets, a couple of Intel integrated sound cards seem to be being abused somewhat by the Intrepid kernel. I've got an Acer 2920 Gemstone laptop here with an Intel 82801H HD audio controller - worked fine on Hardy, but I now get rather nasty pops and crackles whenever I try to use the sound device.

But it's working at least. Would anyone have an idea of how to restore its former glory?

[Link: Famous alsa-info.sh output]("http://www.alsa-project.org/db/?f=cece99dda0c205ee2b4b7ea5d9986cabdbe344a7")

Other misc. info:
```
lspci | grep Audio: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1b.0 0403: 8086:284b (rev 03)

```

(Another point which may be pertinent: I'm not installing from de.archive.ubuntu.com due to some external traffic limiting, but instead from ftp.wh-netz.de/ubuntu.)

Have you tried testing sound without PulseAudio running?

---

### Post by Rumplesmigskin on 2008-09-30
Yes - same problem. (Just fixed some bug in an update that removed my user from the audio group - had thought that something else was wrong). 

I'm not sure that the "speaker-test" program uses PulseAudio at all, since it's directly using the ALSA C API to make its pink noise.

I have some free time today so I might try building alsa again from alsa-project.org's sources. I tried using module-assistant and alsa-src already in the repositories, but they wouldn't compile right.

EDIT:
After downloading alsa-driver-1.0.17 from the Alsa Project page, and following the steps described [here]("https://help.ubuntu.com/community/SoundTroubleshooting") for building the drivers from source, the 'make' script dies producing the following:

```
/home/cian/src/alsa/alsa-driver-1.0.17/acore/info.c: In function &#8216;resize_info_buffer&#8217;:
/home/cian/src/alsa/alsa-driver-1.0.17/acore/info.c:90: error: implicit declaration of function &#8216;PAGE_ALIGN&#8217;
make[3]: *** [/home/cian/src/alsa/alsa-driver-1.0.17/acore/info.o] Error 1
make[2]: *** [/home/cian/src/alsa/alsa-driver-1.0.17/acore] Error 2
make[1]: *** [_module_/home/cian/src/alsa/alsa-driver-1.0.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-4-generic'
make: *** [compile] Error 2
```

**ANOTHER EDIT: Works fine after installing the latest development version of alsa-driver, alsa-lib and alsa-utils from the ALSA project web page.**

---

