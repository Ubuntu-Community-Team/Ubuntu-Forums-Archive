---
title: "Realtek ALC1200 sound problem"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by mandrecu on 2008-08-05
Hello:

I have sound problems with Realtek ALC1200 on Ubuntu 8.04 64bit. 
The card is not detected correctly. 
The motherboard is Asus M3N78N Pro. 
Any suggestions?

---

### Post by esatap on 2008-09-08
I have exactly the same problem with Ubuntu 8.04 32bit.
The sound has static and stutters randomly. 
Haven't found any solutions yet.

However, the sound works fine, if I download something, 
or move around the cursor.

---

### Post by iucoen on 2008-09-21
This has been fixed in the kernel tree:
[http://lkml.org/lkml/2008/8/4/110](http://lkml.org/lkml/2008/8/4/110)

This problem applies to all newer nVidia HDA chips.

---

### Post by -Curtains- on 2008-09-25
I can confirm this on my m3n78 PRO Mobo. How would I go about fixing it? I'm not too experienced with kernel updating and the like.

Cheers for any help :)

---

### Post by Gravatas on 2008-09-25
Hello

It's my first post.I'm a beginner with Ubunt and linux,but i like them.I think I have the same problem. After having the laptop open for some hours i come back home and see that there is no sound etc.For example I try to open an mp3 with Amarok and it says playlist finished etc. sorry if my post is on the wrong thread

p.s. i have a realtek soundcard :S

---

### Post by Zaff on 2008-09-26
any news on this issue ? I have the same card, with the same sound problem and it's really annoying.
I also have to reinstall the Nvidia graphics driver everytime I restart, but I'm probably going to install another graphics card anyway.
I really would like sound to work properly.

---

### Post by alizais on 2008-09-27
> **iucoen said:**
> This has been fixed in the kernel tree:
[http://lkml.org/lkml/2008/8/4/110](http://lkml.org/lkml/2008/8/4/110)

This problem applies to all newer nVidia HDA chips.

I have Conexant High Definition SmartAudio 221 and NVIDIA High Definition Audio as my audio drivers (I don't know why Vista device manager lists two). Do you think that this kernal fix can bring back my sound? 

I used to have static sounds when I was on ALSA and upon someone's suggestion I installed OSS. But now I have no sound at all. Is it a good idea to try the kernal fix? And if so, I'll look for instructions on how to go about this.

---

### Post by -Curtains- on 2008-09-28
No advice anyone?

---

### Post by Zaff on 2008-09-28
how can we get the kernel fix ??? that's what I'm wondering. There are no explanation as to how to do this...

---

### Post by Zaff on 2008-10-03
I've patched the kernel with that fix mentionned earlier and it works (no more crakling). I've explained how I did it here : [http://ubuntuforums.org/showthread.php?p=5898266#post5898266](http://ubuntuforums.org/showthread.php?p=5898266#post5898266)
This will be fixed in Intrepid so I don't know if it's worth fighting for. After all the problem will be gone in a month.
But still.

---

### Post by -Curtains- on 2008-10-05
Excellent, will check it out.

Wish me luck! haha

---

### Post by alexh3791 on 2008-11-01
> **Zaff said:**
> I've patched the kernel with that fix mentionned earlier and it works (no more crakling). I've explained how I did it here : [http://ubuntuforums.org/showthread.php?p=5898266#post5898266](http://ubuntuforums.org/showthread.php?p=5898266#post5898266)
This will be fixed in Intrepid so I don't know if it's worth fighting for. After all the problem will be gone in a month.
But still.

I am running Intrepid, but I am still unable to get any sound. Any ideas on what I should do? Should I try the kernel fix listed above?

---

### Post by Rodney9 on 2008-11-02
I have the 'Realtek ALC1200, 8-channel High Definition Audio CODEC' on my Asus PQ5 Pro Motherboard.

I bought this because Asus have a linux manual and I googled it for linux and came up with many good reviews.

I have sound, but only one sound at a time, how do I get Ubuntu 8.10 64 bit to play multiple sounds at the same time ie: say the time and play streaming audio ?

---

### Post by Rodney9 on 2008-11-02
I fixed this, double click on the volume icon in the top panel and this will bring up the Volume Controller for your chip ( mine is the Realtek ALC1200 ) then click Preferences and add all Tracks to be Visible, make sure there are not muted and turned up.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-24
> **alexh3791 said:**
> I am running Intrepid, but I am still unable to get any sound. Any ideas on what I should do? Should I try the kernel fix listed above?

i also have this problem

---

### Post by willytax on 2009-01-17
I've the same problem: asus m3n78 pro with alc1200 audio chip under debian testing 64bit. The audio chip is not recognized at boot time. The only way to get audio is to type in terminal:

```
sudo rmmod snd_hda_intel
```

then

```
sudo modprobe snd_hda_intel
```

Now you should have sound but not control on volume so you have to logoff and logon again.

I made a little script that runs at the end of the boot process, before the login screen, that substantially unloads and loads snd_hda_intel again.....and it works for me:cool:

---

### Post by afon on 2009-02-01
Thanks! It realy works. 
I think i'll write the same script too

---

### Post by djamu on 2009-05-14
Proper fix for this problem here 

>[http://ubuntuforums.org/showthread.php?p=7279149#post7279149]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149")

---

### Post by mcpish on 2009-08-09
I have an ASUS P5QL Pro motherboard with the ALC1200 HD Audio chipset too.

However I managed to fix this with another method.

RealTek has a Linux driver which works perfectly in Ubuntu even though the notes don't specifically list the ALC1200 HD Audio chipset.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3)

Download the linux driver from this page and follow the instructions in the Readme for the  for the "Azalia controller" chipset. This driver even enables the SPDIF output on the P5QL motherboard.  Then follow this wiki to enable the Pulseaudio ALSA plugin:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

This will enable all sound from all applications and let you independently mix and set volume for each app if you want.

I have perfectly working digital audio from my P5QL Pro motherboard over a coaxial SPDIF RCA cable to an A/V Receiver.

---

