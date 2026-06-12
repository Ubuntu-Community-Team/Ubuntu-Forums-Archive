---
title: "No Audio Preview in Lucid Beta 1."
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ViperScull on 2010-03-22
When the mouse is over an mp3 file, i hear nothing.

I set the option Preview sound files in the Preview tab of Nautilus Preferences to Always.

Nothing.

I installed vorbis-tools and mpg321.

Nothing.

What am i missing?

---

### Post by dinamic1 on 2010-03-22
deleted

---

### Post by ranch hand on 2010-03-22
Did you set the player for the music in the Nautilus>Preferences>Media tab?

---

### Post by mc4man on 2010-03-22
You should make sure the gst ugly plugin is installed
This takes care of most gst decoding support
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

(the latest gst plugins (lucid) have added amr and wma3 (pro) decoding support

(this ppa gives *karmic* the latest and would be worth adding to lucid *later this year* if they add lucid which seems probable
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by ViperScull on 2010-03-22
> **mc4man said:**
> You should make sure the gst ugly plugin is installed
```
sudo apt-get install gstreamer0.10-ffmpeg
```


That was it. Thanks.

I'll add that ppa when Lucid final is released cause i'll do a fresh install.

---

### Post by wpshooter on 2010-03-22
> **mc4man said:**
> You should make sure the gst ugly plugin is installed
This takes care of most gst decoding support
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

(the latest gst plugins (lucid) have added amr and wma3 (pro) decoding support

(this ppa gives *karmic* the latest and would be worth adding to lucid *later this year* if they add lucid which seems probable
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

If this software is necessary for the sound, etc. in Ubuntu to function correctly, why is it not installed by default ?  

Is this another one of those software rights issues ?  If it is, then it would be nice if this software needs to be installed by the user of Ubuntu to get it to function correctly, then it would be nice if the O/S would give the installer an advisement of this need, somewhere during the O/S installation.

Thanks.

---

### Post by mc4man on 2010-03-22
> If this software is necessary for the sound, etc. in Ubuntu to function correctly, why is it not installed by default ? 

Some plugins, codecs and libraries can't be included by ubuntu due to licensing, patents, whatnot.

They aren't needed for 'sound', but many of the popular audio, video formats will require them for decoding and possibly encoding.

The 'gnome-codec-install' package is installed by default and usually does pop up and will (or attempt) to install the missing plugin
(wouldn't do so on the 'preview', and doesn't always work correctly though most times it does.

A search of gstreamer in synaptic will show you them all

There is the ubuntu-restricted-extras package which will install many of them and more - 
It's mis-configured in karmic, fixed in lucid, but does install more than one might wish  - I'd never use nor recommend

---

### Post by timjohn7 on 2010-03-22
Have you selected "Always" under Edit>Preferences>Preview>Sound Files?
Apologies... I've just reread your original post.

---

