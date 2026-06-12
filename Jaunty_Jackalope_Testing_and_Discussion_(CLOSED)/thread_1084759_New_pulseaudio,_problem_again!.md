---
title: "New pulseaudio, problem again!"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cabernet54 on 2009-03-02
After last update of pulseaudio, I have sound sistem issue again!! :confused:

---

### Post by dox_drum on 2009-03-02
What kind of problems?

---

### Post by kansasnoob on 2009-03-02
I noticed after updates today that all "system sounds" are accompanied by static, but sound in Totem, VLC and Flash is fine.

Just an Alpha thing I expect.

---

### Post by cabernet54 on 2009-03-02
> **kansasnoob said:**
> I noticed after updates today that all "system sounds" are accompanied by static, but sound in Totem, VLC and Flash is fine.

Just an Alpha thing I expect.

Yes, "sistem sonds" are bad and static zzzz.. but ALSA driver for my Creative X-FI digital are good! :guitar:

---

### Post by crimsun on 2009-03-02
The current version, 0.9.14-0ubuntu10, has tuned delay parameters and reenabled glitch-free.

Most users will experience some audio aberrations (again) while the GNOME login sound is played. After approximately five seconds, the watermark size and buffer size will have settled, so you should no longer experience audio aberrations until the next time that the daemon autospawns.

I am attempting to address the major problems incrementally. For most Ubuntu users, this means:

1) daemon crashes to due snd_pcm_update_avail() not handling -kernel and -lib bogus data;
2) daemon autospawn race conditions;
3) daemon watermark/buffer size instability on initial spawn (which is the cause of your audio aberrations with system sounds).

You'll continue to see numerous PulseAudio uploads until these problems are addressed.

---

### Post by forumache on 2009-03-02
Thanks crimsun for letting us know.

It's always nice when you know that the problem you encountered (again) is getting the developers attention.

---

### Post by kansasnoob on 2009-03-02
> **crimsun said:**
> The current version, 0.9.14-0ubuntu10, has tuned delay parameters and reenabled glitch-free.

Most users will experience some audio aberrations (again) while the GNOME login sound is played. After approximately five seconds, the watermark size and buffer size will have settled, so you should no longer experience audio aberrations until the next time that the daemon autospawns.

I am attempting to address the major problems incrementally. For most Ubuntu users, this means:

1) daemon crashes to due snd_pcm_update_avail() not handling -kernel and -lib bogus data;
2) daemon autospawn race conditions;
3) daemon watermark/buffer size instability on initial spawn (which is the cause of your audio aberrations with system sounds).

You'll continue to see numerous PulseAudio uploads until these problems are addressed.

Thanks! I was not at all worried about ......... it's still an Alpha!

In fact I'm amazed at how well things DO work! Very pleased overall!

---

### Post by talkingwires on 2009-03-02
> **kansasnoob said:**
> I noticed after updates today that all "system sounds" are accompanied by static, but sound in Totem, VLC and Flash is fine.Strange. Amarok and VLC play sound fine, but the update a few days ago killed Flash sound on my system. Despite all the complaints about Pulse in 8.04 and 8.10, this is the first time I've ever had a problem with it.

---

### Post by Garpur on 2009-03-02
I am also having some mystical effects with my sound card and I suspect that it is also related to the update. 
Though in my case I am struggling with getting anything from the **TOSLINK S/PDIF output**. ](*,)

Somehow it seems to work in VLC player when I have Dolby Surround output on my films and also enabled "*Use S/PDIF when available*" and turned on "*Force detection of Dolby Surround*" 

**aplay -l gives:**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When going to *System>System Settings>Sound* I am only shown the "HDA Intel (AD198X Analog)" option, no mentioning of the digital output.

---

### Post by Vaun on 2009-03-02
crimsun,

I posted this bug earlier in development and it was recently fixed, but than later again re-introduced.

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/322344]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/322344")

Recent pulseaudio updates re-introduced distortion.  I rebuilt libcanberra again from master and again the distortion is gone.  I don't know what the correlation is here , but it is somehow related.  Prior to rebuilding libcanberra, audio was not intolerable.

---

### Post by crimsun on 2009-03-02
> **Vaun said:**
> Recent pulseaudio updates re-introduced distortion.  I rebuilt libcanberra again from master and again the distortion is gone.  I don't know what the correlation is here , but it is somehow related.  Prior to rebuilding libcanberra, audio was not intolerable.

Do you mean "...audio was tolerable" in your last sentence? Are you using Luke's (themuso's) PPA packages for alsa-lib and pulseaudio?

---

### Post by Vaun on 2009-03-02
crimsun,


I just installed the packages from your PPA and all is working again.  Re-building libcanberra from master for some reason fixes the distortion.  I did mean "intolerable" meaning the distortion was so bad I could not listen to anything.  I know this is glitch-free being re-enabled, but the libcanberra issue is perplexing.  The only drawback is that certain sound events were quieter than others. 

Same issue I was having:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/336965]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/336965") 

Thanks for the packages.  Will give feedback on testing.

---

### Post by cabernet54 on 2009-03-03
Thank Crimsun and others Guy!!!

Now I am quite :P

---

