---
title: "Most sounds won't work"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by SandmanCL on 2008-01-07
I have sound working under 7.1, but only with some applications.

I apologize for creating yet another sound problems thread. I've looked through existing threads to no avail.

I have an SiS audio card which plays mp3s fine through xmms and totem, but there are no system sounds, and other sound applications fail.

```
$ lspci -v

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7600
        Flags: medium devsel, IRQ 16
        I/O ports at d000 [size=256]
        I/O ports at d400 [size=128]
        Capabilities: <access denied>
```

Using the alsa-info.sh script found in the Sound Troubleshooting section, this is the output:
[http://pastebin.ca/844833](http://pastebin.ca/844833)

```

$ asoundconf list
Names of available sound cards:
SI7012

$ asoundconf set-default-card SI7012

$ aplay -l
aplay: device_list:204: no soundcards found...
```

xmms playback work fine:

```
$ xmms 01\ -\ Suntoucher.mp3 
Message: device: default
```

... but only after I let /dev/dsp be writeable. Every time I reboot the computer, I do a [FONT="Courier New"]chmod 777 /dev/dsp[/FONT] (stricter permissions would probably work but I'm not too concerned with security for my sound :) )

Playing videos through mplayer gets no sound. Here are the error messages:

```
alsa-lib: confmisc.c:769:(parse_card) cannot find card ''
alsa-lib: conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
alsa-lib: conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
alsa-lib: conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
alsa-lib: conf.c:3982:(snd_config_expand) Evaluate error: No such device

```
I've come a long way -- earlier I wasn't able to get any sounds at all :)
But any help getting me across the finish line would be highly appreciated.

---

### Post by zvacet on 2008-01-07
Did you try to see under **system>preferences>sound ** or system>preferences>volume control.

---

### Post by SandmanCL on 2008-01-07
I don't have those or any other sound-related settings. Nor would expect that adjusting a volume control would fix any of the error messages I supplied in my post :confused:

---

### Post by zvacet on 2008-01-07
> I don't have those or any other sound-related settings.

Do you use Ubuntu,Kubuntu,Xubuntu?

> Nor would expect that adjusting a volume control would fix any of the error messages I supplied in my post 

In volume control you have option to choose between alsa ans oss.That is why I suggested that.

---

### Post by SandmanCL on 2008-01-08
> **zvacet said:**
> Do you use Ubuntu,Kubuntu,Xubuntu?
Xubuntu

In volume control you have option to choose between alsa ans oss.That is why I suggested that.

I see. The closest thing to that that I've found was the audio preferences in mplayer.
I think something must have gone majorly wrong during my install though. Turns out I can't play video either. I'm gonna try re-install from scratch (but not tonight).

Thanks for attempting to help :)

---

