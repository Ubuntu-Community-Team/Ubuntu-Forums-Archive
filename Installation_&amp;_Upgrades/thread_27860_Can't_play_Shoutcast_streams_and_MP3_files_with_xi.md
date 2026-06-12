---
title: "Can't play Shoutcast streams and MP3 files with xine-lib?!"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by anton123 on 2005-04-18
Hello,

I am quite surprised. xine-lib 1.0 does have an MP3 plugin in its "plugins" folder. That I know from when I had Knoppix and Mepis. In Ubuntu, this plugin is absent?! Therefore I can not play MP3 files and Internet music streams from shoutcast.com. Why is that so? Is it because people in the Ubuntu team are so scared of that legal bullshit spread around by noisy, money greedy lawyers, that they histerically and constantly see an axe that is about to drop behind their necks if MP3 support is added to Ubuntu?! All Linux distors that I tried come with xine-lib that features the MP3 plugin. Are the people in the Ubuntu team afraid? Well, I am not. If that is the case, I feel quite let down. In either case, what can be done to get MP3 files to play with xine? I can play them with RealPlayer 10 but why can't xine? Last of all, why is ReaPlayer allowed to play MP3 files? I expect and hope to see MP3 support added in Ubuntu by the time the next version comes out.

Thank you very much and I would appreciate any help I can get.

---

### Post by GrumpySmurf on 2005-04-18
> xine-lib 1.0 does have an MP3 plugin in its "plugins" folder... In Ubuntu, this plugin is absent?!

See [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) for information regarding the exclusion of mp3.  In short, it is patent encumbered and the Ubuntu team would obviously like to avoid any legal entanglements.  Red Hat has eschewed mp3 since Red Hat 8.0, and they caught a lot of flak for it over the years.

The good news is, you can in fact get mp3 playback capability.  See [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) for details.  I use XMMS instead of Xine for shoutcast, and it works great.  Right now, I'm listening to my mp3's via Rhythmbox.  

> Last of all, why is ReaPlayer allowed to play MP3 files?

Simply put, Real paid the mp3 patent owners the licensing fees required to include mp3 codecs in their player.  They of course get the revenue through their pro player to pay the royalties to Fraunhofer.  Since Ubuntu is FREE, 100%, all the time, they do not have a revenue stream to pay for the licensing.

> I expect and hope to see MP3 support added in Ubuntu by the time the next version comes out.

See the ubuntuguide for how to install mp3 support to your installation.  I am unaware if this allows you to use Xine for playing mp3s, but several other multimedia packages will work, including Rhythmbox, XMMS and Mplayer.

Good luck.

---

### Post by anton123 on 2005-04-18
Hello,

Thank you very much for providing me with an excellent help resource. Installing the "gstreamer0.8-plugins" did help. Now I am able to listen to MP3 files and audio streams coded in MP3 format with xine. Still, this "legal" crap still amazes me since I acknowledge that patents more than often are born on baseless grounds.

---

### Post by Zilax on 2005-07-30
I have to say that it is fairly ridiculous to not have the capbility to play MP3 out-of-the box. Given today's legal sitituation I can also understand not putting the codec in the distro.

What I cannot understand is why the error message says something useless like 'no codec for audio/mpeg'. That just makes the distro look stupid to the majority of the market. The vast majority of users will simply walk away at this point becuase the true nature of the issue at hand was not communicated in the error message. The error should say that the user has selected a patent encumbered stream and that he or she might look here, here or here to download some non-free software to decode it and the user might also look there, there or there to read about the IP issues surrounding MP3.

---

