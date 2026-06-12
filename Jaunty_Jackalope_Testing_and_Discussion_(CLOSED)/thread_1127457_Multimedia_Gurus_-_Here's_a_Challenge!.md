---
title: "Multimedia Gurus - Here's a Challenge!"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by invenit on 2009-04-16
I upgraded from intrepid to jaunty yesterday and everything is great, except for some multimedia. I fixed flash easily enough & RealPlayer works OK, but I am unable to play any files in mpg or wmv format. Moreover, I cannot access the Windows media in sites like [http://www.archaeologychannel.org/index.asp](http://www.archaeologychannel.org/index.asp) 

Anybody know how to get this multimedia working again? TIA.

---

### Post by Therion on 2009-04-16
Have you installed non-free codec support?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by invenit on 2009-04-16
> Have you installed non-free codec support?

Yes, installed, but mpg & wmv does not work. When I double-click an mpg file, Totem starts up, then immediately crashes. Or, if I try to access Windows media at the Archeology Channel - Firefox acts like it's starting mplayer and the file is clearly downloading, but never plays.

---

### Post by scaine on 2009-04-16
I just tried the 300K link there and after about 5 seconds of "streaming" the video starts playing - a girl telling me that the site is non-profit, blah, blah, blah.

I installed non-free-codecs from MediBuntu, but I don't remember don't much else special to this install - other than the fact that it's a fresh install from around alpha3.

---

### Post by Therion on 2009-04-16
> **scaine said:**
> I just tried the 300K link there and after about 5 seconds of "streaming" the video starts playing - a girl telling me that the site is non-profit, blah, blah, blah.
You're doing better than I am then: The vids on that site crashed my Firefox repeatedly... HARD.  

And I'm at my office behind a **WinXP** box!

---

### Post by jmmL on 2009-04-16
To my (non-guru) ears, it sounds like you don't have w32codecs installed. They're available in the medibuntu repository

First
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list  
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 

```
This adds the medibuntu repo to your sources.list, and then installs the key.

Then```
sudo apt-get install w32codecs
```

---

### Post by scaine on 2009-04-16
Well, the non-free-codecs meta package includes the w32codecs.  I'm sure I installed that, but otherwise, this is a pretty bog-standard Jaunty install.  It's good to see that Ubuntu is getting better with streaming video.  It used to be the case that you couldn't play any embedded vids outside of YouTube (which isn't really "streaming video" - it's just a big download disguised in a flash object).

---

### Post by jmmL on 2009-04-16
Ah yes, you're right. I always get confused between non-free-codecs and ubuntu-restricted-extras.

Intrestingly, I can't get any of the videos on that site to work; it just says "waiting for video" and I've got no need for realplayer, so I haven't installed that. No spectacular crashes though.

---

### Post by peakshysteria on 2009-04-16
Noguru, nomagic. [**[COLOR="Red"]Medibuntu[/COLOR]**]("https://help.ubuntu.com/community/Medibuntu") fixes your sorrows for sure. As it did with mine.

---

### Post by paradigm2 on 2009-04-16
> **jmmL said:**
> Ah yes, you're right. I always get confused between non-free-codecs and ubuntu-restricted-extras.

Intrestingly, I can't get any of the videos on that site to work; it just says "waiting for video" and I've got no need for realplayer, so I haven't installed that. No spectacular crashes though.

Javascript enabled?  Do you have anything like noscript installed?

---

### Post by jmmL on 2009-04-16
> **paradigm2 said:**
> Javascript enabled?  Do you have anything like noscript installed?

The only things I've got like that would be adblock and flashblock, but I know that they aren't the problem.

I'm not too concerned; video works fine on other sites (embedded in flash or specified using those fancy new <video> tags). My only other guess would be geographic location; I'm in the UK.

EDIT: I'm running minefield nightly though, so perhaps something borked in today's updates.

---

### Post by invenit on 2009-04-16
Thanks for your responses, folks. So far, no joy. I've explored your suggestions (and some others as well). I will probably do a fresh install when jaunty is final.


SOLVED! My Dell Dimension 3000 has Intel's 82865G Integrated Graphics Controller. The forum discussions/stickies in the multimedia section sent me to [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) for the solution.

---

### Post by pelle.k on 2009-04-16
Totem uses the gstreamer codecs, and VLC uses it's own built in codecs, so i usually install ubuntu-restricted-extras for totem, and VLC in case totem doesn't play a file.
w32codecs is mplayer and xine specific, so those won't help you there.
Regarding firefox, it depends on what plugin you have installed, and what plugin is used fo a specific media type on the web page.

---

### Post by gwenn on 2009-04-16
:D Xine works pretty good with this site for me!
Only one issue : the image is too small for my tastes;)

---

### Post by PGHammer on 2009-04-17
> **invenit said:**
> I upgraded from intrepid to jaunty yesterday and everything is great, except for some multimedia. I fixed flash easily enough & RealPlayer works OK, but I am unable to play any files in mpg or wmv format. Moreover, I cannot access the Windows media in sites like [http://www.archaeologychannel.org/index.asp](http://www.archaeologychannel.org/index.asp) 

Anybody know how to get this multimedia working again? TIA.

Actually, I use vlc (VideoLan) for both (in Kubuntu, Vista, and Windows 7 as well; this is a triple-boot box).  VLC even plays old-school files in AVI format (which, oddly enough, Windows Media Player has issues with).  And you don't have to hunt for codecs, either (irrelevant in Linux, and so far unnecessary in Windows; 64-bit in all cases).

VLC is installable via your method of choice.

---

### Post by PGHammer on 2009-04-17
> **pelle.k said:**
> Totem uses the gstreamer codecs, and VLC uses it's own built in codecs, so i usually install ubuntu-restricted-extras for totem, and VLC in case totem doesn't play a file.
w32codecs is mplayer and xine specific, so those won't help you there.
Regarding firefox, it depends on what plugin you have installed, and what plugin is used fo a specific media type on the web page.

That's why I like VLC (instead of Totem); I don't need codecs (or xine, either).  I use Amarok 2 (new with Jaunty/Kubuntu) for audio, and VLC for video.  You can also use VLC as a helper for Firefox.

Even better, if you multi-boot with Windows (or installed Jaunty via Wubi, as I did) you can play videos on the Windows partitions without hunting down codecs (at the most, you need decent Xvideo support in your display driver, as that's what VLC uses by default).

---

### Post by syko21 on 2009-04-17
VLC chokes hard on realmedia files though. For your inbrowser issues try using gecko-mediaplayer

---

### Post by SketchyClown on 2009-04-17
> **syko21 said:**
> vlc chokes hard on realmedia files though. For your inbrowser issues try using gecko-mediaplayer

[b]x2!!

[/b]

---

