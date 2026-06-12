---
title: "WHOA! What happened to gnome-volume-control!?!?"
date: 2009-01-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-01-12
They redesigned it!

[[IMG]http://img407.imageshack.us/img407/2103/screenshotsoundpreferenbh7.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotsoundpreferenbh7.png)

[[IMG]http://img407.imageshack.us/img407/2660/screenshotsoundpreferenob4.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotsoundpreferenob4.png)

[[IMG]http://img407.imageshack.us/img407/2660/screenshotsoundpreferenob4.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotsoundpreferenob4.png)

[[IMG]http://img120.imageshack.us/img120/1141/screenshotsoundpreferenmp4.th.png[/IMG]](http://img120.imageshack.us/my.php?image=screenshotsoundpreferenmp4.png)

---

### Post by LordVeovis on 2009-01-12
Yup.  Only problem is the mixer is a little harder to use.  Other than that I like it.  You can install gnome-alsamixer for the "easier-to-use" mixer

---

### Post by mdurham on 2009-01-13
Any idea how I can turn up/down the line in? I don't see any way of doing that.
Cheers, Mike

---

### Post by gnomeuser on 2009-01-13
As this work is done by the Fedora project, you can go and see the rationale on the Feature page. Please feel free to suggest improvements via the Talk page or by filing bugs on the GNOME bugzilla. There is also currently lively debate on the desktop-devel-list GNOME mailing list on this new work.

[https://fedoraproject.org/wiki/Features/VolumeControl](https://fedoraproject.org/wiki/Features/VolumeControl)

---

### Post by LordVeovis on 2009-01-13
> **mdurham said:**
> Any idea how I can turn up/down the line in? I don't see any way of doing that.
Cheers, Mike

install gnome-alsamixer

---

### Post by BGFG on 2009-01-14
in my jaunty install, the quick volume adjust will go past the screen edge if the icon is near the end of the screen effectively cutting off some of the graphic.

---

### Post by LordVeovis on 2009-01-14
> **BGFG said:**
> in my jaunty install, the quick volume adjust will go past the screen edge if the icon is near the end of the screen effectively cutting off some of the graphic.

Report this to launchpad so it can be fixed.  Or you can report it to fedora (if they have the problem too) as they actually made it.  File at bugzilla as gnomeuser said above.

---

### Post by mdurham on 2009-01-14
> **LordVeovis said:**
> install gnome-alsamixer

Thanks LordVeovis, I haven't had to do this before. I guess things are changing!
Cheers, Mike

---

### Post by ShirishAg75 on 2009-01-14
alsamixer also works, it uses ncurses so not so pretty looking. gnome-alsamixer is nicer but still stale.

---

### Post by tghe-retford on 2009-01-14
Analogue surround and digital audio output isn't selectable out of the box in the new volume control as it was in the old one. I had to kill Pulseaudio, run alsamixer from the command line and then unmute the IEC958 option and turn up the volume on the front speakers there and then re-enable Pulseaudio before sound would work. I reported it via Launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/317292](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/317292)

---

### Post by Slug71 on 2009-01-14
Does anybody elses mic input suck with this? If i turn the mic input volume right up it comes out all distorted testing with the sound recorder and if i turn it any less than full then it comes out really quiet from the speakers. I also noticed that sliding the mic input also affect the main volume output?

---

### Post by tretle on 2009-01-14
My inputs work better than the previous gnome-volume-control, its more intuitive to set up... was a breaze setting up my usb mic on my webcam and what a great mic it is.

So far I have two problems with this new system.

1. Instead of the tabs being in the order of :

sound effects, input, output, applications 
it should be 
output, input, applications, sound effects.

2. In the output and input tabs it should have access to all connections line in, front speakers, rear, center, sub etc. The current way of accessing the controls is completely unintuitive, I didn't even know you could access them until a couple of Ubuntu re-installations after I started using the new controls.

For those of you that don't know:

You can actually adjust the sound levels of all inputs and outputs of your sound card, its just hidden. You don't need alsa mixer. 

To control them do the following, right click on the volume control applet and select preferences, all of your inputs should be viewable from here(master,pcm,front, surround, center etc). This preferences screen operates differently from the old one even though it looks the exact same.
Highlight one of the options(master, front, pcm etc) then close the preferences and left click on the volume applet and click volume control. Now click on the output tab, The mixer available in this tab will adjust the volume of the input/output that you have selected in the preferences dialog. In order to change other inputs/outputs you must return to the preferences dialog and highlight the input/output you would like to modify next.

This is horrible user interface design, especially with 7.1 systems as this repetitive exercise can get annoying.

Hopefully they will ditch the preferences dialog in favor of exposing all of the inputs/outputs in the gnome-volume-control dialog before the release of 9.04 because if they don't it will be a terrible regression.

---

### Post by Slug71 on 2009-01-14
So i was just playing around with it and it seems output controls the mic and its always on.

---

### Post by Starks on 2009-01-14
I hate how I can't ctrl+click or shift+click to control all of the inputs anymore.

---

### Post by Slug71 on 2009-01-14
> **Starks said:**
> I hate how I can't ctrl+click or shift+click to control all of the inputs anymore.

Yep this new control definitely needs more work yet. I guess its a good start though.

---

### Post by LordVeovis on 2009-01-15
> **Slug71 said:**
> Does anybody elses mic input suck with this? If i turn the mic input volume right up it comes out all distorted testing with the sound recorder and if i turn it any less than full then it comes out really quiet from the speakers. I also noticed that sliding the mic input also affect the main volume output?

I cant get mic intput to be detected anywhere, but it may be user error... not sure.  If I use sound recorder I can switch through all inputs and none of them records from my mic.  all volumes / inputs are not muted.

---

### Post by Martje_001 on 2009-01-15
Credits should go to RedHat btw, not Canonical.

[http://www.phoronix.com/scan.php?page=article&item=gnome_sound_control&num=1](http://www.phoronix.com/scan.php?page=article&item=gnome_sound_control&num=1)

---

### Post by Starks on 2009-02-09
Oh boy...

It seems that we're back to the old interface.

[[IMG]http://img21.imageshack.us/img21/5919/screenshotsoundpreferenlo8.th.png[/IMG]](http://img21.imageshack.us/img21/5919/screenshotsoundpreferenlo8.png)

---

### Post by mdurham on 2009-02-09
> **Starks said:**
> Oh boy...

It seems that we're back to the old interface.
[/IMG][/URL]
about time too!

---

### Post by rockin_goliath on 2009-02-10
NOOOO Why????? Just fix the problems in the new mixer!!! I want sound preferences that I can actually use to choose which device my sound gets outputed to, not which server I feel like using for "types" of applications!

The NEW pulseaudio preferences was leaps and bounds better than the old one in terms of usability, since you can control everything from the same interface. Sure it's a little complicated for surround sound users, I'm one of them, but since most of the time, surround sound levels are only adjusted once, and most users are laptop/2 channel users anyway, the new interface was just what was needed. 

I don't like opening gnome-alsa-mixer to change the volume of the headphones, since they are independent from the master, and I don't like going to pavumixer to right click on applications and selecting which speakers they should play out of. I *should* be able to do it all from one convenient interface. It's a nightmare trying to explain to my Dad how to adjust the volume on his voip headset, set alone trying to explain how to actually get the voip program to output to them. With the new gui, he could have this accomplished in two clicks and 5 seconds. The old one, nine clicks and 20 minutes, *at best*. How can the old interfaces (like gnome-sound-properties) actually be *used*?

PLEASE return the new pulseaudio mixer, and let's sort out the surround sound regressions so we can make everyone happy.

---

### Post by rockin_goliath on 2009-02-10
NOOOO Why????? Just fix the problems in the new mixer!!! I want sound preferences that I can actually use to choose which device my sound gets outputed to, not which server I feel like using for "types" of applications!

The NEW pulseaudio preferences was leaps and bounds better than the old one in terms of usability, since you can control everything from the same interface. Sure it's a little complicated for surround sound users, I'm one of them, but since most of the time, surround sound levels are only adjusted once, and most users are laptop/2 channel users anyway, the new interface was just what was needed. 

I don't like opening gnome-alsa-mixer to change the volume of the headphones, since they are independent from the master, and I don't like going to pavumixer to right click on applications and selecting which speakers they should play out of. I *should* be able to do it all from one convenient interface. It's a nightmare trying to explain to my Dad how to adjust the volume on his voip headset, set alone trying to explain how to actually get the voip program to output to them. With the new gui, he could have this accomplished in two clicks and 5 seconds. The old one, nine clicks and 20 minutes, *at best*. How can anyone actually *use* gnome-sound properties?

PLEASE return the new pulseaudio mixer, and let's sort out the surround sound regressions so we can make everyone happy.

---

### Post by Mr. Picklesworth on 2009-02-10
I'm not running Jaunty at the moment, but someone should post to ubuntu-devel-discuss to find out about this. The new sound configuration interface is Too Promising to kill, even for a minute.

ALSA has always struck me as something like xorg.conf: An ugly corner of the system which configures itself 99.9% of the time and the average user should never need to look at. It makes sense to abstract it with something more approachable.

Speaking of telling applications to play out specific speakers / record from specific inputs, is that possible with the new volume control? I'm without my Jaunty VM right now and never checked. It was always one of my favourite capabilities with pavucontrol!
I love bouncing the output from text-to-speech software into voice chat. "This is my voice, you insensitive clod!" :)

---

### Post by SKLP on 2009-02-10
I just re-installed to Jaunty (alpha 4), and I have still got this, which I love so far...
Why would they remove it??! 
Well, seems I won't be upgrading(from alpha4) for a while :)

---

### Post by Gourgi on 2009-02-10
i also hope we keep it.
it is exactly what i need for my sound control (5.1 surround and external line-in for my tvtime)

---

### Post by taavikko on 2009-02-10
> **SKLP said:**
> I just re-installed to Jaunty (alpha 4), and I have still got this, which I love so far...
Why would they remove it??! 
Well, seems I won't be upgrading(from alpha4) for a while :)

Just pin down current "gnome-media" package, and you should be safe to apply all upgrades.

For removing (regression) it, any volunteers to upload to a ppa the new version ;)
For further testing...

---

### Post by rockin_goliath on 2009-02-10
> **Mr. Picklesworth said:**
> 
Speaking of telling applications to play out specific speakers / record from specific inputs, is that possible with the new volume control? I'm without my Jaunty VM right now and never checked. It was always one of my favourite capabilities with pavucontrol!

In the new volume control, you can adjust the volume of applications. I'm not sure about the output, other than very easily selecting the global output. But if you still wanted to accomplish this and it is not provided for in the new interface, than pavumixer will surely do the trick.

---

