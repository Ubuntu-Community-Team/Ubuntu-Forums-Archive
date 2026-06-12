---
title: "Latest Update - Now VIA 8237 onboard sound doesn't work"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by KungfooChris on 2007-01-11
Hey guys,

  I just installed the latest update for edgy and it updated my kernel to 2.6.17-10-386. I did have to reinstall the nVidia drivers with the envy script that I found form searching the forums for it to grab the latest versions of all the files.  Now the only other problem I am having from the update is that my on board sound stopped working.  It still shows the card as detected from the console, and XMMS starts up and plays either by choosing ALSA or ESD.  The problem is that no sound is comming out of the speakers.  I know no connections have changed or anything because I updated, and then continued working and streaming music.  Then I rebooted because I remembered that I had updated and wanted to load up the new kernel.  Once rebooted, my video drivers were all screwed up, and no audio from the speakers.  I have been researching this issue since yesterday.  I have tried using the alsamixer and unmutting everything, and tried to re-installed the alsa driver with 2 or more guides on the forums here.  Does anyone have an idea on how to get my sound back and running.  Re-installing my OS is not an option right now.  So I would really like a fix outside of having to go and purchase another sound card to get my sound back that was working perfectly before the update.

Thanks for your help,

-- Chris

---

### Post by KungfooChris on 2007-01-11
I thought i would also add that I have done the following:

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
:~$ 


Then I did: 

lspci -v: the output was:

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80f3
        Flags: medium devsel, IRQ 209
        I/O ports at c800 [size=256]
        Capabilities: [c0] Power Management version 2


Just thought I would post that real quick, seems those are the first things people ask for this type of problem.

Thanks,

-- Chris S.

---

### Post by arnieboy on 2007-01-11
> **KungfooChris said:**
> Hey guys,

  I just installed the latest update for edgy and it updated my kernel to 2.6.17-10-386. I did have to reinstall the nVidia drivers with the envy script that I found form searching the forums for it to grab the latest versions of all the files.  Now the only other problem I am having from the update is that my on board sound stopped working.  It still shows the card as detected from the console, and XMMS starts up and plays either by choosing ALSA or ESD.  The problem is that no sound is comming out of the speakers.  I know no connections have changed or anything because I updated, and then continued working and streaming music.  Then I rebooted because I remembered that I had updated and wanted to load up the new kernel.  Once rebooted, my video drivers were all screwed up, and no audio from the speakers.  I have been researching this issue since yesterday.  I have tried using the alsamixer and unmutting everything, and tried to re-installed the alsa driver with 2 or more guides on the forums here.  Does anyone have an idea on how to get my sound back and running.  Re-installing my OS is not an option right now.  So I would really like a fix outside of having to go and purchase another sound card to get my sound back that was working perfectly before the update.

Thanks for your help,

-- Chris
open up alsamixer and unmute volume etc.

---

### Post by KungfooChris on 2007-01-11
> **arnieboy said:**
> open up alsamixer and unmute volume etc.

I was going to say something sarcastic and all, but then I went ahead and tried it one last time, and wouldn't you know it I overlooked PCM.  I had everything else unmuted except that one

Go figure,

Thanks bro,

-- Chris

---

### Post by arnieboy on 2007-01-11
if xmms is actually playing the file and no errors are being reported and from the sound card descs, we already know the module for your card is loaded. Kernel Upgrades often mute volumes and this is the only thing which needs to be double checked here. I might be missing something more key.. but I really doubt it.

---

### Post by arnieboy on 2007-01-11
> **KungfooChris said:**
> I was going to say something sarcastic and all, but then I went ahead and tried it one last time, and wouldn't you know it I overlooked PCM.  I had everything else unmuted except that one

Go figure,

Thanks bro,

-- Chris
hmm..

---

### Post by KungfooChris on 2007-01-11
> **arnieboy said:**
> hmm..

well what I was getting at is that I had mentioned that I had already tried that in my very first post.  I had unmuted everything, guess for some reason I didn't catch the PCM.  Anyways, not my VMware is not detecting my sound card :(  I tried to re run the patch that I found at: [http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1611&sliceId=SAL_Public](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1611&sliceId=SAL_Public) which fixed the problem last time, and not change yet.  I am getting ready to reboot to see if that fixes it but I have my doubts. 

-- Chirs

---

### Post by KungfooChris on 2007-01-11
seems all I needed to do was change the setting for that guest OS for the sound card to use /dev/dsp instead of saying 'Auto Detect' now windows has sound again in VMware :)

Thanks again arnieboy for making me go back and check the alsamixer for the 100th time ;)

-- Chris

---

### Post by alexa on 2007-02-01
Hi!
I have the same problem. My system is debian etch 2.6.18-3-686. There is no sound, but XMMS plays everything! There was perfect sound everywhere before upgrade from 2.6.10 to 2.6.18 kernel. In alsamixer I have just unmuted all, but nothing has changed =(. Could you help?

lspci
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

---

### Post by vdcosta on 2007-02-13
I do not have a speaker set and instead only have a pair of headphones.  When I open up alsamixer I can change the volume settings for all playback devices except headphones[off].  Any advice on how to change this?

Thanks.

---

