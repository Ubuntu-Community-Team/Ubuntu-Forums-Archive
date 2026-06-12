---
title: "Sound/Video Problem With Hardy"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by ceaseallfeeling on 2008-04-29
I JUST installed Hardy, and have had a ton of problems. I can't play audio files anymore, at all, whether it's just basic sending/ receiving chat noises for pidgin, or music files in Rythmbox. In fact, Rythmbox crashed after I tried a few different files. The only sound/ video working is with youtube, that I've seen so far.

Every time I try to play a video/sound file with totem mplayer, I get this message
[B]
Failed to connect stream: Invalid argument[/B]
With videos, the video will flash up for a fraction of a second, then I will get that error. 

I have an Inspiron 530,Intel®Pentium® dual-core processor E2160 (1MB L2,1.80GHz,800 FSB), 128MB NVIDIA GeForce 8300GS, if thaat helps anyone. 

This is incredibly frustrating... please, if anyone knows how I can get my sound/ video back, I'd be very grateful to hear it.

---

### Post by mindwip on 2008-04-29
I get the same thing, i am using Kaffeine to play all my videos and music. But DVDs are a no go, i get a really bad picture with the codec, but i am sure things will be updated soon.

Tried VLC, totem, rythem, gxine, ogle-- the best is kaffeine or at least in 8.04

---

### Post by cmmichael on 2008-04-29
After two days with Hardly Hearing, I am thinking of returning to XP. 
I got the no sound effect on installation, then found a workaround here:

[http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)

Now, after a reboot, the system seems to have an automatic setting for audio back to the non-working alternative. This is looking more like the linux that I was warned about years ago - a great system if you are a software developer.

---

### Post by martrn on 2008-04-29
> **cmmichael said:**
> After two days with Hardly Hearing, I am thinking of returning to XP. I got the no sound effect on installation, then found a workaround here: [http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/) Now, after a reboot, the system seems to have an automatic setting for audio back to the non-working alternative. This is looking more like the linux that I was warned about years ago - a great system if you are a software developer.

This is not the way to rebuild sound kernel modules from the source, that will work with every system.

This is the sound trouble shooting page:
```
https://help.ubuntu.com/community/SoundTroubleshooting
```

When or if you have the unfortunate position of reaching Using alsa-source, you have two options,  One being make / build / configure.

The other to use module assistant:

Ensure you know the exact name of your alsa sound card it will be on this page : [http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")
then:
sudo apt-get install build-essential 
sudo apt-get linux-headers-$(uname -r) 
sudo apt-get module-assistant alsa-source
sudo module-assistant

While in module-assistant you have to ensure that you get the source, configure for only your sound card.  Compile it and then intall it.

It appear to me you missed one small step

And as for ..."..This is looking more like the linux that I was warned about years ago - a great system if you are a software developer...."...

Why don't you ask your sound card manufacture the reasons why they don't make sound card drivers for linux ?

---

### Post by ceaseallfeeling on 2008-04-29
Alright, I checked the os_part, restarted, and the problem still seemed to have fixed itself... I'm a little freaked out still, but hopefully the problem is solved.

---

### Post by phrawzty on 2008-04-30
> **ceaseallfeeling said:**
> Alright, I checked the os_part, restarted, and the problem still seemed to have fixed itself... I'm a little freaked out still, but hopefully the problem is solved.

Hi there,

What do you mean, exactly, by "os_part" ?  I'm also having problems with sound support for my Inspiron 6400, and if you've found a fix, i'd love to give it a try myself. :)

```
$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

***edit*** : After following the steps in the community documentation, then rebooting, i once again had sound.  WTG Hardy. :P

---

### Post by cmmichael on 2008-04-30
I solved the problem by deinstalling PulseAudio and reconfiguring to ALSA. It's also necessary to check the volume settings as per this post:

[https://bugs.launchpad.net/ubuntu/+bug/192040](https://bugs.launchpad.net/ubuntu/+bug/192040)

note to martrn: to answer your question - my soundcard maker (Intel) did install a Linux driver on the soundcard (ICH9 chipset). A better question would be why did the Ubuntu developers introduce a new audio program for Hardy without providing for proper configuration on install, or a simple way to reconfigure back? They knew it didn't work with Skype. This is the user-friendly OS I've been hearing about?

---

