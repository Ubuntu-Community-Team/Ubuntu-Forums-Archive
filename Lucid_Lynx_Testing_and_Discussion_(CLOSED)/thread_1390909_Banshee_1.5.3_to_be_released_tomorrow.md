---
title: "Banshee 1.5.3 to be released tomorrow"
date: 2010-01-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Swarms on 2010-01-26
According to this planet post: [http://gburt.blogspot.com/2010/01/banshee-release-schedule.html](http://gburt.blogspot.com/2010/01/banshee-release-schedule.html) from developer the next version of Banshee will be released tomorrow.

According to [OMGUBuntu]("http://www.omgubuntu.co.uk/2010/01/whats-new-in-banshee-153-folder.html")
These features will be added:
[LIST]
[*]Sync of playlists
[*]Folderwatching at last!
[*]Enchanced control of coverarts
[*]Audiobooks library extension
[*]Support for Google Nexus One
[/LIST]

Sounds fantastic and I am sure 1.6 will be a solid release (March 31)

I am aware that Lucid being LTS, they should probably stick to Rhythmbox for now, but I believe Banshee would be the better choice for Lucid+1

---

### Post by gnomeuser on 2010-01-26
[OMG Ubuntu has screenshots](http://www.omgubuntu.co.uk/2010/01/whats-new-in-banshee-153-folder.html)

Please note that the folder watching extensions depends on Mono 2.4.3, as of today Lucid only has 2.4.2.3 which is insufficient. Additionally hyperair has not yet to my knowledge started building snapshots nor unstable releases for Lucid in the PPAs.

So fine gentlemen, there is a challenge for you to take on.

---

### Post by Nadir on 2010-01-26
> **Swarms said:**
> 

I am aware that Lucid being LTS, they should probably stick to Rhythmbox for now, but I believe Banshee would be the better choice for Lucid+1

Is it still a memory hog compared to Rhythmbox ?

---

### Post by zekopeko on 2010-01-26
> **Nadir said:**
> Is it still a memory hog compared to Rhythmbox ?

You have it confused with Songbird.

---

### Post by pomnikus on 2010-01-26
> **zekopeko said:**
> You have it confused with Songbird.
No, he's right (check attachments). In this configuration rhythmbox is more powerful, but still lighter (64-bit). Enabling extensions in banshee increases the difference.

---

### Post by phenest on 2010-01-26
> **Nadir said:**
> Is it still a memory hog compared to Rhythmbox ?

Isn't that a Mono issue?

---

### Post by pomnikus on 2010-01-26
> **phenest said:**
> Isn't that a Mono issue?
Please, no more mono flamewars :)

---

### Post by phenest on 2010-01-26
> **pomnikus said:**
> Please, no more mono flamewars :)

That was not my intention. Just merely stating that the issue could be taken up with the Mono devs.

---

### Post by Merk42 on 2010-01-26
> **phenest said:**
> That was not my intention. Just merely stating that the issue could be taken up with the Mono devs.

I'm sure, but as you can see from the poster above you, that's what happened anyway.

---

### Post by phenest on 2010-01-26
> **Merk42 said:**
> I'm sure, but as you can see from the poster above you, that's what happened anyway.

Wish I hadn't mentioned it now. There's always one idiot that spoils it, without giving a thought to aiding development of said package, instead of calling it...

> **kahumba said:**
> Mono crap

---

### Post by gnomeuser on 2010-01-26
> **phenest said:**
> Isn't that a Mono issue?

Having things like a VM does add a bit of overhead. This is the price you pay for the advantages that gives you, instead of hunting a certain class of bugs the Banshee developers are free to improve the application - or put simply "pure awesome comes at a price".

I believe the quality of Banshee speaks positively in favor of this trade off. It is incredibly powerful, packs more features than you can dream off and has a vibrant contributor community. 

Memory consumption can be improved an you will notice that over time it has been in Banshee. There's always a smart trick or two one can play, new methods to detect bottlenecks and excessive work, improvements to the underlying system. 

[Directhex compares mediaplayers and their consumption](http://www2.apebox.org/wordpress/linux/113/)

I would like to think though that there are more important factors to a media player than saving 12 megs of ram. Having a properly designed framework that ensures easy additions and constant deployment of new features. Having active development community that is responsive to bugs. Having a codebase that is easy to get into. Not taking [4½ years and counting](https://bugzilla.gnome.org/show_bug.cgi?id=310774) to get proper device synchronization into your applications (read: providing users with the features they want and need, in a timely fashion).

Banshee with the 1.5 series has solved every blocker that was preventing it from becoming the default media player in Karmic. It has aligned with the GNOME release schedule and is thus dependable and very suitable for Ubuntu to follow during a release cycle. Every thing speaks for Lucid+1 finally presenting a truly better media experience thanks to Banshee.

---

### Post by Zoot7 on 2010-01-26
> **Swarms said:**
> [LIST]
[*]Sync of playlists
[*]Folderwatching at last!
[*]Enchanced control of coverarts
[*]Audiobooks library extension
[*]Support for Google Nexus One
[/LIST]
I've been waiting for the Folderwatching for a while now. :) 
Banshee is by an absolute landslide my favourite media player in Linux, and if I could, I'd use it in Windows too.

---

### Post by gnomeuser on 2010-01-26
> **Zoot7 said:**
> 
Banshee is by an absolute landslide my favourite media player in Linux, and if I could, I'd use it in Windows too.

1.6 will ship with support for OS X an Windows as well. You can even follow the changes in git, a lot of effort is being put into making this work well.

---

### Post by Zoot7 on 2010-01-26
> **gnomeuser said:**
> 1.6 will ship with support for OS X an Windows as well. You can even follow the changes in git, a lot of effort is being put into making this work well.
That I didn't know, thanks for the info! :)

---

### Post by amano on 2010-01-26
> **Zoot7 said:**
> 
Banshee is by an absolute landslide my favourite media player in Linux, and if I could, I'd use it in Windows too.
C'mon. Banshee is probably the last player on earth that doesn't offer gapless playback. Which is a basic feature (ANY live album will sound awful).

---

### Post by zekopeko on 2010-01-26
> **amano said:**
> C'mon. Banshee is probably the last player on earth that doesn't offer gapless playback. Which is a basic feature (ANY live album will sound awful).

There is a gapless playback branch IIRC. It just hasn't been merged yet.

---

### Post by Zoot7 on 2010-01-26
> **amano said:**
> C'mon. Banshee is probably the last player on earth that doesn't offer gapless playback. Which is a basic feature (ANY live album will sound awful).
Yeah there's a fair few shortcomings no doubt. 
But the equalizer is the main thing I'm going on, it's the only player I've found with a good equalizer that doesn't either sound terrible or distort music. All the other players that I used to like seem to be ripping the equalizer out of them with new versions.

---

### Post by JoeWheeler on 2010-01-26
It's great for me, ipod support is good, playback is great

The only thing I want is a method to get .aa audiobooks on my ipod

---

### Post by gnomeuser on 2010-01-26
> **JoeWheeler said:**
> It's great for me, ipod support is good, playback is great

The only thing I want is a method to get .aa audiobooks on my ipod

I suspect that you'd have to consult Audible's customer service to get the required specifications to implement such support.

Alternatively you'd have to defeat the DRM, then extract the mp3 data and transfer that. 

Option 1 seems unlikely to get a response, option 2 seems likely to give a much unwelcome lawyery response.

---

### Post by JoeWheeler on 2010-01-26
> **gnomeuser said:**
> I suspect that you'd have to consult Audible's customer service to get the required specifications to implement such support.

Alternatively you'd have to defeat the DRM, then extract the mp3 data and transfer that. 

Option 1 seems unlikely to get a response, option 2 seems likely to give a much unwelcome lawyery response.

Hehe spent MANY hours on option 1 to no avail

I know amarok can do it so it must be possible, but i don't like the amarok interface

---

### Post by uBeer on 2010-01-27
It's official now on the website. Now we only have to wait for launchpad/repositories to be updated...

---

### Post by hachel on 2010-01-28
is that normal? That a website announces the release of a new version and prompts people to download it and then you can't do that?

---

### Post by uBeer on 2010-01-28
Well, the source is available, so you can build it yourself. Building for all platforms takes time, so they want to make sure that people get the source first.

There is already an OS X build, so I'm using that in the meanwhile, but there are some problems, especially with keyboard shortcuts acting when you're entering info for something...

But at least it runs quite ok on a pc installation of snow leopard :P

---

### Post by pomnikus on 2010-01-28
WTF? Check the screenshot:
[http://img-fotki.yandex.ru/get/3808/pomnikus.0/0_262f6_26515ac0_orig](http://img-fotki.yandex.ru/get/3808/pomnikus.0/0_262f6_26515ac0_orig)
BTW, there is no folder watching.
```

banshee:
  Installed: 1.5.3+git20100126.r1.7412596-0ubuntu1
  Candidate: 1.5.3+git20100126.r1.7412596-0ubuntu1
  Version table:
 *** 1.5.3+git20100126.r1.7412596-0ubuntu1 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by hachel on 2010-01-28
apparently folder watching requires a newer version of mono as the one currently installed in karmic (and lynx apparently)

---

### Post by Zoot7 on 2010-01-28
I built it myself from source this morning. Once it hits the repos I'll revert to that.

---

### Post by MacUntu on 2010-01-28
> **pomnikus said:**
> WTF? Check the screenshot:
[http://img-fotki.yandex.ru/get/3808/pomnikus.0/0_262f6_26515ac0_orig](http://img-fotki.yandex.ru/get/3808/pomnikus.0/0_262f6_26515ac0_orig)
BTW, there is no folder watching.
```

banshee:
  Installed: 1.5.3+git20100126.r1.7412596-0ubuntu1
  Candidate: 1.5.3+git20100126.r1.7412596-0ubuntu1
  Version table:
 *** 1.5.3+git20100126.r1.7412596-0ubuntu1 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status

```

Hello, Joe! :D

---

### Post by afv on 2010-01-28
> **hachel said:**
> apparently folder watching requires a newer version of mono as the one currently installed in karmic (and lynx apparently)


It has been updated:

```

mono-runtime:
  Installed: 2.4.3+dfsg-1
  Candidate: 2.4.3+dfsg-1
  Version table:
 *** 2.4.3+dfsg-1 0
        500 http://archive.ubuntu.com lucid/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by amano on 2010-01-28
> **zekopeko said:**
> There is a gapless playback branch IIRC. It just hasn't been merged yet.

I know it and I hope that this will be merged for 1.6. But until that 1.5.3 is utter useless...

---

### Post by JohnJackson on 2010-01-28
> **pomnikus said:**
> WTF? Check the screenshot:
[http://img-fotki.yandex.ru/get/3808/pomnikus.0/0_262f6_26515ac0_orig](http://img-fotki.yandex.ru/get/3808/pomnikus.0/0_262f6_26515ac0_orig)
BTW, there is no folder watching.
```

banshee:
  Installed: 1.5.3+git20100126.r1.7412596-0ubuntu1
  Candidate: 1.5.3+git20100126.r1.7412596-0ubuntu1
  Version table:
 *** 1.5.3+git20100126.r1.7412596-0ubuntu1 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status

```

Is that a various artists CD? If so you have to right click on the tracks, edit track information and set the compilation artist.

I'm guessing need to enable the folder watching plugin.

---

### Post by dagrump on 2010-01-28
Well, I just got batch of libmono stuff! Could be some of the files you're waiting on. +/- 60 lines related to mono at the end of the install, seems it replaced a batch.

---

