---
title: "problems in Jaunty beta"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Claus7 on 2009-03-27
Hello,

using ubu 9.04 I have noticed some problems. You tube even though has a very good quality with flash 10 installed from synaptic, it has no sound.

Also if I want to install some packages from synaptic which contain the name restricted I get an error.

Which is the best place to report things so as Jaunty to be improved? I think that the first step should be the forums,no?

Regards!

---

### Post by Vevmesteren on 2009-03-28
Same problem here...No sound in Flash player. I installed the Pulse Audio Server, and see Flash Alsa plugin flash when it tries to play...

---

### Post by Claus7 on 2009-04-06
Hello,

while tampering with my graphics card, I saw that while the system was loading its settings, pulse audio had a red asterisk in front of it.

I still have not made you tube with sound to work. I have sound in other applications. I do miss sound also in the opening screen (I miss it a lot I should say).

I have installed jaunty beta and I have made all the upgrades till the time of writting.

The restricted packages after the upgrade do not seem to complain any more.

Regards!

---

### Post by Claus7 on 2009-04-06
Hello,

I was able to hear sound while I was prompted to put my username and password following this guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

yet still no sound in firefox even typing aoss firefox...

Any ideas? Has anyone faced the same problem?

The reinstallation of flashplayer via synaptic didn't make any difference.

Regards!

---

### Post by Claus7 on 2009-04-06
Hello,

I was able to solve my camera problems reading the following:
[http://ubuntuforums.org/showthread.php?t=966762](http://ubuntuforums.org/showthread.php?t=966762)
[http://ubuntuforums.org/showthread.php?t=945803](http://ubuntuforums.org/showthread.php?t=945803)

it is bad because as these people my camera was working out of the box.

Regards!

---

### Post by xzero1 on 2009-04-06
You might not get any sound if you don't have the required audio codec.

---

### Post by kansasnoob on 2009-04-06
I would start with the first section of this tutorial:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Just to be sure your sound card is recognized!

My next question would be, "have you had audio in a previous version of Ubuntu"?

---

### Post by kansasnoob on 2009-04-06
I also happened to think if it's a flash problem only go to Synaptic and type flash into the search feature. Then scroll through and be sure no gnash or swfdec- is installed.

I personally found that Flash 10.0.12.36 worked better for me than 10.0.22.87. I don't know why.

And remember to restart Firefox after each change! That's a must!

---

### Post by Claus7 on 2009-04-07
Hello,

at least I have some responses to this. Hearing from my surroundings no one faced this bizarre problem. Thank you for your responses:

> **xzero1 said:**
> You might not get any sound if you don't have the required audio codec.
Which sound codec do you suggest? I do not remember if any is required...

> **kansasnoob said:**
> I would start with the first section of this tutorial:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Just to be sure your sound card is recognized!


My next question would be, "have you had audio in a previous version of Ubuntu"?

I tried a similar guide that I post above, which recognizes my sound cards and I also made an index so as to call my pci card at boot. I have sound everywhere I have checked, including a small drum sound before I'm supposed to give my username.

Yes, I had sound both in dapper and after an upgrade to hardy. 

> **kansasnoob said:**
> I also happened to think if it's a flash problem only go to Synaptic and type flash into the search feature. Then scroll through and be sure no gnash or swfdec- is installed.

I personally found that Flash 10.0.12.36 worked better for me than 10.0.22.87. I don't know why.

And remember to restart Firefox after each change! That's a must!

You were correct. I had installed swf, yet the uninstallment and restart of firefox didn't seem to work. For some reason firefox seems to be muted no matter what I try. 
I will also try and see if any previous version exists...

I'm thinking also if it might be any configuration specific to firefox, yet I cannot say that I have made a lot of progress to that. Having sound before and having also sound in other applications puzzles me a little.

Regards!

---

### Post by 4Orbs on 2009-04-07
Hello again, Claus7

Don't know if this will be of any help to you... Whenever I install Ubuntu, the first thing I do after the updates is go to the [Comprehensive Multimedia and Video how-to]("http://ubuntuforums.org/showthread.php?t=766683") here on the forums, and follow its steps from top to bottom. And it sets up everything flawlessly for me in less than an hour (usually, including download time). Flash, java, dvd playback and ripping, cellphone video 3Gp format (Blackberry, etc), streaming things in Apple format. You might be interested in the Gecko Media Player plugin for Firefox. The How-To is currently posted for Intrepid, but is working equally well for me on Jaunty. You only have to change the word "Intrepid" to "Jaunty" in one line of command.

---

### Post by Claus7 on 2009-04-07
Hello 4Orbs,

it seems that the installation of Jaunty, even with so many new features tries to be a nightmare for me. I have to say that I came across the link you posted, yet I didn't consider giving it a try because it had many things that I do not use.

I followed also most of the steps from here to no avail.
[http://ubuntuforums.org/showthread.php?t=590989](http://ubuntuforums.org/showthread.php?t=590989)

Thanks for the link. I tried the medubuntu repos and the only package I was not able to find is:
libavcodec-unstripped-51

I do not want to mess a lot with installations of this and that to my system, because I think that till the stable version comes I'll have problems. Whatever changes I tried which I thought serious, after failure I reverted them back.

I think that I will stick with no flashsound in jaunty...

Regards!

---

### Post by macogw on 2009-04-07
Swfdec v. Adobe should make no difference, except Swfdec has native PulseAudio support and Adobe's....we've got a bit of a hack making it work.

Is it possible pulseaudio isn't running or is crashing sometime after login and before you get to YouTube?

---

### Post by Claus7 on 2009-04-07
Hello,

thank you for your answer. While I was tampering with my graphics card I saw that while the kernel was booting I had a red asterisk in front of pulse audio. Unfortunately, after my graphics card was working I was unable to see such options. 

Could you tell me which command will provide me with the answer whereas pulseaudio is crashing or not?

I will use top and ps ux. Unfortunately I'm not in my pc at the moment. I will type these commands or if any more if they drop by and let you know the sooner I reach my pc. 

Regards!

---

### Post by macogw on 2009-04-07
> **Claus7 said:**
> Hello,

thank you for your answer. While I was tampering with my graphics card I saw that while the kernel was booting I had a red asterisk in front of pulse audio.
That doesn't matter.  It's just saying that it's running per-user not systemwide, because that's how Ubuntu does it.
> 
Could you tell me which command will provide me with the answer whereas pulseaudio is crashing or not?

I will use top and ps ux. Unfortunately I'm not in my pc at the moment. I will type these commands or if any more if they drop by and let you know the sooner I reach my pc. 

Regards!
Um, don't forget the "a" in "ps aux" but yeah...that's it.  I mean, you can pipe it to grep to look for pulseaudio if you don't want to look through the whole list yourself.

---

### Post by xzero1 on 2009-04-07
> Which sound codec do you suggest? I do not remember if any is required...
Audio codecs are required to play most if not all audio streams. I do not know if they are included with the flash player itself. I think not.

This is somewhat the way it went:
In attempting to play a utube video, Shiretoko detected that I did not have the required plugin. I selected sw-dec player, loaded it and again tried to play the video but heard no audio. Shiretoko detected I did not have the audio codec but after downloading this everything worked.

I noticed that one of the posters mentions that sw-dec *has* native pulse audio support. I think the codec came from the "ugly" plugins so you might need to enable multiverse in software sources. BTW, this is on a x2 AMD 64 running 64-bit Jaunty beta.

---

### Post by Claus7 on 2009-04-07
Hello,

@macogw :
so the output of the command: ps aux | grep pulseaudio
claus     3316  0.3  0.4 111312  5600 ?        Ssl  20:27   0:00 /usr/bin/pulseaudio --start
claus     3317  0.0  0.2   7840  2636 ?        S    20:27   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
claus     4071  0.0  0.0   3348   820 pts/0    S+   20:31   0:00 grep pulseaudio

from what I can make out it is working nicely...

@xzero1 : I cannot find a program as Shiretoko. So you are proposing changing player for flash... Is it possible? I was so content up to now. And the video of flash is really good. Still no sound though...

Regards!

---

### Post by xzero1 on 2009-04-07
> @xzero1 : I cannot find a program as Shiretoko. So you are proposing changing player for flash... Is it possible? I was so content up to now. And the video of flash is really good. Still no sound though...Shiretoko is Firefox 3.5 beta....
Sw-dec,gnash and adobe's player all play flash. Adobe is the only 'mature' player as Sw-dec and gnash are basically clones of it.

I would suggest installing pulse audio device chooser "padevchooser". This can show you if pulse audio is attempting to play your stream and what device is playing it. For example if playing a utube video under "PulseAudio Applet->Volume Control->Playback" I can see the alsa-plugin firefox 3.5 vu meter responding to the audio. If this doesn't run then pulseaudio is probably not installed correctly.

---

### Post by Claus7 on 2009-04-07
Hello,

At last I'm getting a clearer picture!
So I installed what you told me to and I opened a tab with a you tube page. There immediately it showed underneath my intel card a bar which has to do with the sound of that page produces. 

Yet, my default sound card is the Live one... I have to inform firefox somehow to use the right sound card. At least this is what I think. Yet. Live is my first sound card as a choice... Very helpful this xzero1!

Regards!

---

### Post by Claus7 on 2009-04-07
Hello,

I do not know what to say! I hear sound! Thank you very much xzero1!

So what I did in order to make it work:

I went in synaptic and typed:
padevchooser

and saw that it was installed. In case it is not I would advice you to install it.

Now I went in Applications -> Sound and Video -> PulseAudio Device Chooser.

I have to say that at the beginning I chose Adjust the Volume Level of Pulse Audio and in the tab Output Devices I was able to see my sound cards. Either way from the same window I selected Playback and in the arrow pointing downwards next to alsa plugin firefox I chose move stream and the sound card Live.

Hope this help someone who might face the same problem.
Regards!

---

### Post by Julian Lewis on 2009-04-14
[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

---

### Post by Claus7 on 2009-04-17
Hello,

after a bug that hit me during an update during beta version of jaunty, I reinstalled my system and updated to release candidate version. In order to make flash in firefox to work, I had to install from synaptic the alsa-oss package. I had once again to select my primary sound card.

Regards!

---

