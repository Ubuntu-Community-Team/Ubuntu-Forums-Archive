---
title: "Odd Sound Issue on Presario V3000Z"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by atek101 on 2007-04-21
I hope that someone can make some sense of this strange predicament. 

I have a Presario V3000Z (the AMD-nVidia model) that dualboots Windows XP Professional and Ubuntu 7.04 Feisty. Since I installed Feisty, I haven't been able to get sound to work properly in Ubuntu.

Initially, I had 6.10 Edgy and Windows XP. Sound worked fine in 6.10, and I never had a problem, other than my quicklaunch volume controls weren't being utilized completely by the OS. But that was no big deal. 

Since I installed 7.04, however (installed over 6.10, not upgraded), I have not  been able to get sound to work CONSISTENTLY in Ubuntu. Sometimes, when I start it up, I hear all the sounds properly. But most of the time, I get no sound at all. That includes system sounds and even other forms of media (I tried mp3s after installing the correct codecs.) 

Sounds like  hardware concern, doesn't it? Nope! When I boot Windows, sound ALWAYS works properly. I only have the issue when I'm in Feisty. 

I tried the "adduser [username] audio" command to see if maybe my account wasn't consistently receiving sound permissions. But it simply told me that my account already had permission for audio, even when the sound WASN'T  working. 

What's odd is that Feisty APPEARS to have recognized my sound card. I have a Conexant HD Audio card and in the Volume Control menu, it list some kind of "Conexant" device. It also lists some kind of "nVidia" device, though I don't believe I have any such audio device. I've tried setting each device up as the one with primary control, but neither seems to produce sound consistently. 

I'm relatively new to linux and how it operates, so I'm guessing I'm probably overlooking some simple driver loading issue or some simple command that would make sound work consistently. It wouldn't be so unusual in my opinion if sound NEVER worked. But sometimes, it does, and without any reason that I can see. 

Any assistance or advice that anyone could offer me would be greatly appreciated. Some upgrade -Feisty- is if 6.10 can do something so simple and vital that 7.04 can't!

---

### Post by atek101 on 2007-04-21
I'd also like to add that both the 6.10 Edgy and 7.04 Fiesty I installed were the i386 versions. I really have no use for the 64-bit distro.

---

### Post by peteryjk on 2007-04-21
same problem here.... my laptop also Presario V3000 series..AMD 64x2 . No sound at all on Ubuntu 7.04 Feisty.

---

### Post by vmikalinis on 2007-04-21
Same problem here with a Gateway Laptop with athlon 64 /ati / ac97 sound. :(

---

### Post by atek101 on 2007-04-21
I think that the key to solving this problem is probably figuring out how Feisty handles, recognizes, or loads sound devices differently than Edgy. I ALWAYS had sound in Edgy.

---

### Post by atek101 on 2007-04-21
Do you guys dual boot with Windows? Could that have something to do with the device problem? It seems like after I load windows I loose sound in Fiesty. But then again, shutting down a session of Fiesty and rebooting  doesn't bring the sound back.
 
EDIT: Nope. If Windows using the device makes the difference between sound and no sound, it's surely not clear how or why. I booted Ubuntu immediately after -hibernating- Windows and got sound.

Changing Ubuntu's sound preferences (Preferences -> Sound) doesn't seem to make a difference, either. It recognizes an nVidia ALSA device (Legacy drivers in Windows?) and a Conexant Audio device OSS (Conexant HD Audio Drivers in Windows). In Edgy, it only recognized nVidia ALSA drivers, and I consistently had sound in Edgy. So I set all types of inputs/outputs on ALSA in Fiesty just like it was in Edgy. No difference. I could have it set to Conexant or nVidia ALSA and occasionally get sound with either. Having Autodetect on or off on input/outputs makes no difference either. As far as I can tell, these conditions all seem to be consistently inconsistent!

What else could cause Feisty to utilize my sound devices properly only SOME of the time? It always works with my quicklaunch buttons, even when I don't get sound. It truly makes no sense whatsoever as far as I can see.

---

### Post by Thomaseov on 2007-04-27
> **atek101 said:**
> I think that the key to solving this problem is probably figuring out how Feisty handles, recognizes, or loads sound devices differently than Edgy. I ALWAYS had sound in Edgy.

I'm having a similar problem with feisty.  Sound worked fine under edgy on one of my computers, but is behaving bizarrely under feisty.  I get sound, but my controls are all messed up with the volume buttons adjusting the mic volume instead, but the mic remaining aloof from  these same controls for voice conferencing...basically the controls are scrambled and ineffective.  What is different in how feisty handles sound...that way we can fix our problems...anyone?

Thomas

---

### Post by El Viejo Lobo on 2007-04-28
I have problem with the volume up/down/mute buttons. This started after installing Feisty on a Presario V2000 and having sound and microphone input problems.
Here is the link:   [http://ubuntuforums.org/showthread.php?t=422862](http://ubuntuforums.org/showthread.php?t=422862)

---

### Post by josephus on 2007-04-30
Have any of you tried playing with how the options in /etc/modprobe.d/alsa-base

I think that you are using snd-hda-intel drivers

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

there is a section about changing 'flavours'. give that a go.

---

### Post by atek101 on 2007-05-01
Well I'm relieved I'm not the only one experiencing these strange troubles. I'll look into the hda-intel sound driver  Howto and see what it does. 

So far as messing with alsa-base, I tried copying Edgy's alsa-base into Fiesty to see if that would fix the problem. No luck there. 

It seems like HDA-Intel drivers are common for use with my hardware in many Linux distributions. The odd thing is that each distro manages my sound hardware differently! All that I have tried but Ubuntu Fiesty succeed in producing sound on my speakers.

---

### Post by LDRoamer on 2007-05-01
Sound has quit working on my Compaq Armada 1750 after an updgrade from Edgy to Feisty. In mycase the sound chip is an old es1869. I have tried everything I can find to make it work but nothing has succeeded. I have concluded that something is just broken in Feisty and until its fixed I won't have any sound. The sound chip does get detected and shows up but you cannot unmute the sound. By changing around various switches and/or altering settings in my bios I was able to unmmute the sound but all that came out of the speakers was a loud screeching. 

It seems to me that it some sort of hardware conflict.  If I try loading sound with the exact same settings that worked in Edgy the computer acts very sluggish and it takes it minutes to get to a working desktop where it would load in seconds previously. Commenting out the sound card driver returns the speed of the machine to normal. 

I also notice errors in dmesg that were something like: unable to grap 0x220. 220 is one of the ports my sound chip uses. I went into the bios and changed the port to 0x240. That didn't help. Once I rebotted demsg reported: unable to grap 0x240.  Feisty is making something conflict with the sound chip but I have no idea what it is.

I guess I should have waited before updgrading my Edgy installation as it was working perfectly.

---

### Post by atek101 on 2007-05-17
I tried the alsa flavors...thought for sure m2-2 was right, but it didn't fix the problem.

---

### Post by ktucker on 2007-06-25
I found a solution here (not fully tested but so far I can at least play sounds now):
[http://ubuntuforums.org/showthread.php?t=433514&highlight=cannot+hear+sound+in](http://ubuntuforums.org/showthread.php?t=433514&highlight=cannot+hear+sound+in)

Briefly, change the permissions of devices listed in /dev and /dev/snd

cd /dev
ls -l /dev/* | grep audio

and then for each one 'chmod 666 <name>'
e.g. 
sudo chmod 666 dsp

---

### Post by agent-s on 2007-07-05
i was looking into the chmod suggestion, but I'm already in the audio group, so it wouldn't do anything for me

---

### Post by ldegryse on 2007-09-15
Try this : 
**If you application sounds works, but your system sounds does not (login, logout, error sounds...) try removing the .asoundrc* files from your own directory (e.g. with 'rm .asoundrc*'). It should make the system sounds work without a reboot.**

If still not working, have a look at following link : 

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

It might help.

Regards

---

