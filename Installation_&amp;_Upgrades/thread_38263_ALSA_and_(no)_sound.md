---
title: "ALSA and (no) sound"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by rboss on 2005-05-30
Well, it's a strange problem I have.

The sound card works. At least with the oss-modules. Input/record doesn't work, though.

So I tried ALSA. But that doesn't work either. But it should.

The modules get loaded, no problem there.

$lsmod
snd                    50276  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

I can also change stuff with amixer 

$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]

I have unmuted master and pcm and can also user the gnome-mixer. The applications even can play stuff. But I don't hear anything.

Remember; it works with oss, so the speakers are not the problem (or the cables).

Any ideas?

Oh, almost forgot; it's an onboard via soundcard.
Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

Any help is appreciated..

---

### Post by salman_arabi on 2005-05-31
No sound here also.

I too have same problem. It seems like Xmms is playing the audio file but i am not able to hear any sounds, even system sounds is are not working.

I too have onboard via soundcard
Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller

Please help me as I am working on this for past one week.

Thanks in advance.

---

### Post by salman_arabi on 2005-05-31
Can sombody please help **me** and **rboss** with **no sound**  problem.

---

### Post by rboss on 2005-05-31
Ideas? Anyone? Should I try banging my head against the machine? Could that help? ;)

---

### Post by huh? on 2005-05-31
I use the AC'97 sound chip (on board) and a C-Media card..both work..but !
open the mixer, and click file, and click change card...select the proper card and driver....that seems to work for me most of the time...
but, I still can't sound to work on movie files..not sure why..

---

### Post by salman_arabi on 2005-05-31
Sound worked from me in Alsa , need to make video work

---

### Post by rboss on 2005-05-31
I got sound working again, with ALSA and recording and everthing. But I had to downgrade to 2.6.8; and with 2.6.8 the ati-driver doesn't work. Argh.

Anyway; I did my recording stuff and switched back to 2.6.11, now I can play WoW again.. ;)

---

