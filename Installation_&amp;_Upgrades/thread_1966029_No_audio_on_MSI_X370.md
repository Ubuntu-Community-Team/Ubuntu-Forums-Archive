---
title: "No audio on MSI X370"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by leopoldbirkholm on 2012-04-26
Hello, hello dear members of Linux Ubunut Forum :KS,

I have this computer:
Manufacturer: MSI 
Model: X370
CPU/APU: AMD E-350
GPU: AMD Radeon HD6310
WiFi: Realtek RT8188CE
Audio: Unknown
HDD: 500 GB Sata 2

My issue. I have problem with audio. I have no audio. It works when I tried Fedora 16 but then WiFi did not work. And I like Ubuntu anyhow a bit more.

Now, I am stunned. Where do I start troubleshooting? What should I start search for? What strings should I Google with?

Thank you for taking the time to read my post! Thank you! ):P

---

### Post by leopoldbirkholm on 2012-04-30
Problem with audo on an MSI X370 running Ubuntu 12.04 LTS.

Step 1.
After a weekend with rest, I got some ideas.
Search the problem with the phrase “find audio settings ubuntu 12”. Found this article: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and this thread from Ubuntu forums: [http://ubuntuforums.org/showthread.php?t=1825882](http://ubuntuforums.org/showthread.php?t=1825882)

Step 2.
On the Sound Troubleshooting guide I did step 1, 2 and 4. Step 4 gave this result:
```
~$ sudo aplay -l
```
Output:
```

**** List of PLAYBACK Hardware Devices **** 
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: SB [HDA ATI SB], device 0: ALC269VB Analog [ALC269VB Analog] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0

```

Step 3.
I then looked at the thread and typed in first 
```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` 

An edit window opened and I searched for the row ```
options snd-hda-intel model=XX
```. I replaced the value to ```
auto
``` as suggested and rebooted.

Step 4.
Still no audio. Going through the steps again and post an update on Ubuntu Forums.

---

### Post by leopoldbirkholm on 2012-05-03
Last update. The audio on my MSI X370 works now. I have no clue to why it does. I will now marked it solved.

---

