---
title: "AC97 sound not working"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by skyde on 2005-02-10
Well I installed Ubuntu today but found out that I have zero sound. I can't hear anything. Asked some of my friends and they told me that something wrong with my mixer settings. Started up Alsamixer and put everything to full strength. Response was nothing.

I did do a few searches on the forums here, but I wasn't able find anything specific to my problem.
Sounds worked fine with winblows so I don't think there is nothing wrong with bios ie. not disabled.

An lsmod | grep snd_   brings out this. If this helps with the answer?

snd_via82xx            26660  3
snd_ac97_codec         59268  1 snd_via82xx
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_via82xx,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7296  1 snd_via82xx
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
gameport                4736  2 snd_via82xx,analog

If you need more info lemme know. I am fairly new to Linux so feel free to talk to me like I am an idiot :)

Best Regards
~skyde

---

