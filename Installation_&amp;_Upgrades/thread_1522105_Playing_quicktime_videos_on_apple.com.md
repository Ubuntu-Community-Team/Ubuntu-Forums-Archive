---
title: "Playing quicktime videos on apple.com"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Wayne0188 on 2010-07-01
I cant find any solutions that work, I am trying to play the videos on apple.com, i have installed all kinds of pluggins and such that have been suggested, but none seem to work.

How can I get the video's to play as they are meant to on the Apple.com site using firefox in Ubuntu 10.04. It keeps saying that I need to install Quicktime player, I have with wine, no go.

Any suggestions would be great.

---

### Post by davec64 on 2010-07-01
Hi,

Open the Software centre and install **Ubuntu Restricted Extras**

That should solve the problem!  :)

Here some more info:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Wayne0188 on 2010-07-01
i did that, it didn't work, I will try it again though. Doesn't quicktime on windows install a plugin for firefox, or does the imbedded player look for the files on the HDD?
Actually the [B]Ubuntu Restricted Extras doesn't even have quicktime support listed.
[/B]

---

### Post by Wayne0188 on 2010-07-02
let me clarify, I can play quick time videos on my HDD, but the embedded  videos on apple.com will not play, I get the generic message that I  need to dl quicktime player.

---

### Post by davec64 on 2010-07-04
Hi Wayne,

You are using Firefox aren't you?


The Restricted Extras do include Quicktime:
> Ubuntu can play the most popular non-free media formats, including DVD, MP3, Quicktime, Windows Media, and more by following the instructions below. 

This is on the Restricted Extras page here:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

If that hasn't worked try installing the W32codecs (If you're running 64 bit Ubuntu you'll need the W64codecs instead)  from Medibuntu:

[http://packages.medibuntu.org/lucid/w32codecs.html]("http://packages.medibuntu.org/lucid/w32codecs.html")

If you haven't set Medibuntu up as a repository here's the howto:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Once you've set the repository up you'll be able to install via Synaptic or apt. I believe the Firefox plugin is contained within the pack.

Shout if you need anymore help!  :)

---

### Post by Wayne0188 on 2010-07-07
thank you very much, I finally got it working, I actually had to reinstall the default player (totem I think) I uninstalled it when I installed mplayer. anyways thanks for all the help.

---

