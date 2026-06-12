---
title: "DVD's in jaunty not working?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cptrohn on 2009-04-08
I added the medibuntu repositories to my sources and then downloaded the restricted extras but I'm still not getting any DVD playback no matter what I do....

anybody know more about this?

---

### Post by bekind2thenoob on 2009-04-08
Try typing

```
sudo aptitude install libdvdcss2
```

into your terminal. That should install the dvd decryption library.

---

### Post by Nullack on 2009-04-08
it still wont work - totem is missing needed patches since resindvd was fixed up

---

### Post by bekind2thenoob on 2009-04-08
Oh mine still works ...I havn't updated since thismorning though...

---

### Post by cptrohn on 2009-04-08
> **Nullack said:**
> it still wont work - totem is missing needed patches since resindvd was fixed up

So that command won't work either?

Hmmm I might have to wipe jaunty and move back to intrepid in that case, I'd hate too do that though.... but I use my laptop to watch movies when I'm out of town.... definately a feature I need...


(oh and I agree about the bluray in your signature.)

---

### Post by amano on 2009-04-08
What program are you trying to use? DVD support in totem/gstreamer is rather poor (but now getting better with every gstreamer/bad and totem release).

Make sure that you have libdvdcss2 installed. I am up to date with the patches and at least some DVDs do work (totem/gstreamer).

---

### Post by bekind2thenoob on 2009-04-08
Well give it a try lol ;)

---

### Post by cptrohn on 2009-04-08
> **amano said:**
> What program are you trying to use? DVD support in totem/gstreamer is rather poor (but now getting better with every gstreamer/bad and totem release).

Make sure that you have libdvdcss2 installed. I am up to date and at least some DVDs do work (totem/gstreamer).

I've tried VLC, Dragon and Mplayer and can't get them to play in any of the 3... I just installed libdvdcss2 via command line and still not getting any playback.

---

### Post by cptrohn on 2009-04-08
> **bekind2thenoob said:**
> Well give it a try lol ;)

Yeah, I just gave it a go and still getting the error that VLC can't play the disk... tried a few different DVD's as well and nothing....

---

### Post by Nullack on 2009-04-08
The story is if you use the XINE backend instead of gstreamer youll get a bunch of other bugs that XINE has which gstreamer and plugins dont.

If you use gstreamer, it wont work. Its slooooooowly getting there with recent dev commits but since we dont have a proper totem compile yet with the new totem patches you wont get proper dvd navigation.

Use SVN mplayer or vlc if you have to for a free dvd player.

---

### Post by bekind2thenoob on 2009-04-08
i just updated my jaunty but left out gstreamer0.10-plugins-bad and gstreamer0.10-plugins-bad-multiverse. I can still watch dvds.

Is their any way for the op to roll these packages back to their previous versions for the time being?

---

### Post by Nullack on 2009-04-08
You cant really watch DVDs though can you? Have you tried going back to the menu? or going back to the chapter selection? or enabling certain subtitle languages? Or enabling different audio streams?

HINT: Its all broken :)

---

### Post by bekind2thenoob on 2009-04-08
Well subtitles are broken, let me just get a dvd with more than 1 audio track, i cant go back to the menu but i can navigate it when it first comes up and i can skip between chapters quite happily.

Plus audio and video quality is fine :) wich is the main thing imo

---

### Post by bekind2thenoob on 2009-04-08
Yep language selection "in picture" is broken but i can switch in the menu when i first play the disk

---

### Post by cptrohn on 2009-04-08
I could reload intrepid and still watch DVD's though right?  Or is this a problem for all versions with medibuntu?

---

### Post by bekind2thenoob on 2009-04-08
Nope will work fine in intrepid

---

### Post by cptrohn on 2009-04-08
> **bekind2thenoob said:**
> Nope will work fine in intrepid

Thats cool... no big deal I guess... I do like Jaunty a lot though...

I might just wait it out and see what happens.... I'm sure there are folks working hard on it...

Thanks for the answers and the help everbody!

---

### Post by Nullack on 2009-04-09
Ok I spoke with the last developer who patched totem and basically he said that its too much work to bring in the all the patches needed from svn and backport them into jauntys totem package.

So it will be karmic koala at the earliest before we see any sort of workable dvd navigation in Ubuntu using the default backend - gstreamer.

---

### Post by nanog on 2009-04-10
i have never used gstreamer for dvd playback and i've been using ubuntu since breezy. 

vlc svn is working brilliantly for me:

```

#svn vlc 
deb http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main

```

---

### Post by taavikko on 2009-04-10
> **nanog said:**
> i have never used gstreamer for dvd playback and i've been using ubuntu since breezy. 

vlc svn is working brilliantly for me:

```

#svn vlc 
deb http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main

```

Yep, do you agree that fresh install and newcomers to *Buntu need to go through the hassle of finding a resolution to solve this?

As it's installed default (gstreamer) it should then work O-T-B.
With minimum action necessary.

---

### Post by warjowuch on 2009-04-10
Does it also NOT work with totem-xine?? I always uninstall the totem-gstreamer package and install totem-xine. For me I have no real trouble.
But, still on intrepid though.
But I have never seen normal full-functional dvd-playback on totem-gstreamer.

---

### Post by Nullack on 2009-04-10
I dont use xine because it has a bunch of other bugs in other areas that gstreamer doesnt have. As well, I want to help improve the quality of the default ubuntu build.

---

