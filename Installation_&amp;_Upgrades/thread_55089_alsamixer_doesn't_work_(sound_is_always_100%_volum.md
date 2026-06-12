---
title: "alsamixer doesn't work (sound is always 100% volume)"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by patrickhh on 2005-08-07
alsamixer doesn't work (sound is always 100% volume, mixer settings are ignored)
My soundcard is a "Hoontech DSP 2000"

```
patrick@gulag:~$ uname -a
Linux gulag 2.6.10-5-686-smp #1 SMP Fri Jun 24 18:12:58 UTC 2005 i686 GNU/Linux

patrick@gulag:~$ lspci |grep audio
0000:02:0d.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

patrick@gulag:~$ lsmod |grep snd
snd_ice1712            62788  3
snd_ice17xx_ak4xxx      4192  1 snd_ice1712
snd_ak4xxx_adda         6112  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             10720  1 snd_ice1712
snd_ac97_codec         74336  1 snd_ice1712
snd_pcm_oss            52836  0
snd_mixer_oss          19968  1 snd_pcm_oss
snd_pcm                95780  4 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_timer              25572  1 snd_pcm
snd_page_alloc          9988  1 snd_pcm
snd_i2c                 5920  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         8224  1 snd_ice1712
snd_rawmidi            25024  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
snd                    56580  17 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10400  1 snd
```

Thanks,
Patrick

---

### Post by nuvolablues on 2007-05-23
Same problem for me
any solution?

---

