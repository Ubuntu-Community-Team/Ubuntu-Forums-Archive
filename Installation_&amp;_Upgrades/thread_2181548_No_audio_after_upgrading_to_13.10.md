---
title: "No audio after upgrading to 13.10"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by flopin2 on 2013-10-18
Hello,

after upgrading my laptop's Kubuntu to 13.10 today, my audio stopped working. Here are the symptoms:

In System Settings -> Multimedia -> AV Settings i have there four selectable devices:

Built-in Audio Analog Stereo
Built-in Audio Digital Surround 5.1 (HDMI)
Dummy Output
Built-in Audio Digital Stereo (HDMI)

However, first three are grayed (disabled) and i can not select them. I only can select the last option.
So, when i plug speaker directly into laptop, no audio. When i plug into the external monitor connected via HDMI, it works. So, how do I re-enable the laptop's ouput?

Tried

alsa force-reload

no luck,

apt-get remove --purge alsa-base pulseaudio
apt-get install alsa-base pulseaudio

also no luck. tried also fresh KDE user with clean config, not a beep
Any ideas?

Thank you

---

### Post by raydar on 2013-10-20
|

---

### Post by flopin2 on 2013-11-22
Anybody any hint?

edit:
The situation changed a bit, the devices 

Built-in Audio Analog Stereo
 Built-in Audio Digital Surround 5.1 (HDMI)
 Dummy Output

are no longer grayed, they are gone alltogether :-)

---

