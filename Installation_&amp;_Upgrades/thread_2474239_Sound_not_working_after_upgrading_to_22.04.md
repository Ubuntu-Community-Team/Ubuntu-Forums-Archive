---
title: "Sound not working after upgrading to 22.04"
date: 2022-04-24
forum: Installation &amp; Upgrades
---

### Post by shashank314 on 2022-04-24
Hello,

I upgrade Ubuntu on my XPS 13 9310 model and now the sound does not work. In the sound setting, I can only see "Dummy output" as the option for the output device. I searched other people have had the same problem but their problem seems to be solved by adding the following lines to /etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=generic
options snd-hda-intel dmic_detect=0
```


That did not fix things for me, after the reboot. I also added the following line to /etc/modprobe.d/blacklist.conf

```
blacklist snd_soc_skl
```

Again nothing changed. I also tried:

```
sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload

```


If I type $aplay -l I get the following output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Generic Analog [Generic Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: Generic Digital [Generic Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: A [USB-C to 3.5mm Headphone Jack A], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


Any suggestions?

---

### Post by launchpad-hansdezwart on 2022-06-01
I seem to have the exact same problem on the same device. I was wondering if you managed to find a solution yet?

---

### Post by Dy1anW on 2022-06-03
I have the same problem as well, and have also tried the same solutions to no avail. I'm on a fresh install of 22.04 (at first I tried do-release-upgrade, but the results were not good, so went ahead with a fresh install). As I recall I had a similar problem when I installed 20.04 on this laptop a few years back, but that issue was very easily solved. Not so much luck this time around.

---

### Post by him610 on 2022-06-03
FWIW: I had a similar issue a few months ago on one of my systems with LTS 20.04.4. It is documented here - [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/700635]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/700635")

---

