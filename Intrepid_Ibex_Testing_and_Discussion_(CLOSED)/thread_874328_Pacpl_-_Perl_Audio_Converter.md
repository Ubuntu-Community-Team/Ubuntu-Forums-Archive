---
title: "Pacpl - Perl Audio Converter"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ace214 on 2008-07-29
I'm wondering whether there would be other support to add this to the repositories. I really love this program for audio converting and syncing my PC music collection with my portable player. It used to be in the repos back in Gutsy, I believe. It's a long process to install all the perl modules so it would be great if it was in the repos for a quick deb. The site provides debs but they are slightly old. Perhaps someone here will know why it was removed.

The site is [http://pacpl.sourceforge.net/]("http://pacpl.sourceforge.net/")

---

### Post by picpak on 2008-07-29
Try audio-convert:

```
sudo apt-get install nautilus-script-audio-convert
nautilus-script-manager enable ConvertAudioFile
```

Right-click your audio file and audio-convert will be under the "Scripts" menu.

---

### Post by rockin_goliath on 2008-07-30
You could also try Sound Converter, which is in the Repos. It has a very nice Gnome gui and is really simple to use. If you want, you can right click on an audio file and select "Open with other application" and select Sound Converter from the list. That way you'll have the option of opening all audio files with the Converter. I use this all the time and it's wonderful. I'm not sure what the command line interface is like though.

EDIT: It also uses Gstreamer as it's conversion backend

---

### Post by ace214 on 2008-07-30
I haven't tried audio-convert, but I have used Sound Converter and find pacpl to be greatly superior. I will try audio-convert, but between Sound Converter and pacpl, I would go through the setup process to have pacpl.

---

### Post by aamukahvi on 2008-07-30
I use banshee for this. Just drag the music to the device and it's converted.

---

### Post by cozmicharlie on 2008-07-31
> **aamukahvi said:**
> I use banshee for this. Just drag the music to the device and it's converted.

PACPL has the most exhaustive collection of transcoders available for Linux.  It is one of the only packages that is able to transcode shn files.  

I don't know why it was pulled from the repos.  I agree, I would like to see it added back.  It does have a lot of dependencies but the author of PACPL has included a script that will install all the dependencies needed.  It's actually very easy.  Also, if you are using kde it does integrate into Amarok.  I recently tried out OpenSuse 11 and it installs from yast with all the dependencies - very easy.  It would be nice if something similar was available in Ubuntu.

---

### Post by ace214 on 2008-07-31
Is there a process that end-users can go through to request it be added?

---

### Post by cozmicharlie on 2008-07-31
> **ace214 said:**
> Is there a process that end-users can go through to request it be added?

I don't know what the process entails.  It may have been the decision of the developer not to maintain a version for the repos.  I will ask the developer.

---

### Post by cozmicharlie on 2008-07-31
As I suspected the person that was maintaining the package did not have time to keep it up.  Below is what the PACPL developer wrote about it.

> The only package I personally maintain is for Slackware package (other than the source obviously).  Packages for the other distributions are maintained by various people.  Chad Martin (from linuxappfinder.com) made the Debian package for some time, but eventually became to busy to mess with it.  However, anyone wishing to pick up where he left off is more than welcome.  This includes submitting it to the repositories for Debian/Ubuntu/etc.  Never using said packages, I'm not really sure how to create/submit them.


So if anyone wants to volunteer that would be great.

---

### Post by aamukahvi on 2008-08-01
> **cozmicharlie said:**
> PACPL has the most exhaustive collection of transcoders available for Linux.  It is one of the only packages that is able to transcode shn files.

I generally use flac for encoding and then transcode to mp3 for the Creative player.

p.s. shn... what's that?

---

### Post by cozmicharlie on 2008-08-01
> **aamukahvi said:**
> 

p.s. shn... what's that?

shn is a lossless codec.  It what an early codec developed before flac and common among live music show traders.  Still used extensively for trading live shows on sites like etree.org.  It is not the best because it is no longer being developed and it does not support tags but their is still a lot of trading in shn files.

---

