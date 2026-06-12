---
title: "[SOLVED] Flash Won't Work In Firefox"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by emotionlovesyou on 2008-01-26
I'm having trouble getting the sound to play in Firefox on websites like [YouTube]("http://www.youtube.com") and [Pandora]("http://www.pandora.com"). I hear sound when it's embedded in the HTML like on this site: [NeverStopSeeing.com]("http://www.neverstopseeing.com") so I think it's an issue with Flash.

(I've read a couple how-tos but nothing has seemed to help.)

[COLOR="Silver"]I'm running Ubuntu 7.10 (Gutsy Gibbon) on an HP Pavilion dv2000[/COLOR]

---

### Post by diablo75 on 2008-01-26
1.  Download [this file ]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")and save it to your desktop.

2.  Right-click on the file and click "extract here"

3.  Open a terminal window.  You will be put into your home folder by default.  Go to your desktop by typing
```

cd Desktop
```
It's case sensitive.

4.  Type:

```
cd install<tab-key>

OR

cd install_flash_player_9_linux

```

The tab key will auto-complete the rest of the command for you.  Hit enter, and you'll then be in the folder that was just created when you extracted the tar archive.

From here type:

```
sudo ./flashplayer-installer 
```

The defaults should work fine, so just hit Enter over and over until it's installed.

Good luck!

---

### Post by emotionlovesyou on 2008-01-26
I've actually done this before but I do run across one small problem. It usually gives me a prompt for the Firefox installation path.

```
Please enter the installation path of the Mozilla, Netscape, or Opera browser (i.e., /usr/lib/mozilla):
```

What's the best way to determine this? (I *have* tried the suggested directory, of course.)

---

### Post by diablo75 on 2008-01-26
The path name should be:

/user/lib/firefox/

Try that.

---

### Post by emotionlovesyou on 2008-01-26
Okay, I used that. The installation finishes successfully, but I still don't hear any sound in the browser on Flash applications. ](*,)

---

### Post by diablo75 on 2008-01-26
Your sound problem likely has nothing to do with flash, but have you been able to produce sound from other apps yet?  Perhaps your sound mixer needs to be adjusted.  Be sure that your PCM channel is turned up, since this is your wave device.  Also, turn your master volume up.  The mixer should be accessible via a little speaker icon on your upper task bar.  Double click on it and fiddle around with the options.  You might be able to switch back and forth from alsa and oss in here as well, which you could if adjusting volume levers doesn't cut it.

And in the interest of being thorough, check your power cord and headphone jack connection on your PC...

---

### Post by j0lliyo on 2008-01-28
well if you are using oss and not alsa, only alsa plays sound in flash

at least that's what i found out as to why mine won't play sound from [www.adobe.com](www.adobe.com)

---

### Post by GayRockies on 2008-02-05
Thanks for this thread.  I hope the original poster has gotten his problem worked out.  I was having problem with Flash not working at all on several web sites.  I thought I was going to go insane without Pandora to entertain me while I worked on papers!  (Not completely just a joke....)

In any case, this manual install method worked great for me.  I had already installed Flash when prompted by Firefox, but the most I usually got was a box where a flash object was supposed to be.

(With Pandora happily playing in the background)
Thanks,

M.J.

---

### Post by emotionlovesyou on 2008-02-29
> **j0lliyo said:**
> well if you are using oss and not alsa, only alsa plays sound in flash

at least that's what i found out as to why mine won't play sound from [www.adobe.com](www.adobe.com)

How do I know which one I'm using? I have both installed, but don't see anywhere I can select between the two. Should I completely uninstall OSS?

(I've increased the volume to the PCM and Master as well as other channels. That doesn't seem to help. They were all at half to begin with.)

---

### Post by emotionlovesyou on 2008-03-31
Today is a glorious day!!! Pandora, [Epic-Fu]("http://www.epicfu.com/"), and YouTube are back!

First of all thanks for all your guys' help. I appreciate it even though none of it helped. But I *did* get Flash working again. I ended up having to reinstall Ubuntu because of another issue I was having which was entirely my own fault I'm ashamed to say, but sure enough when I booted for the first time, I thought I would give Pandora a try and yeeeeeeeeeeeeeeehaaaaa! It works.

I'm just posting this for people who might be having the same trouble. Try everything above first, but if you can't get it to work just reinstall.

:KS:KS:KS:KS:KS:KS:KS

---

