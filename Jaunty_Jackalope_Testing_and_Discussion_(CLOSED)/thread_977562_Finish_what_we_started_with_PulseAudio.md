---
title: "Finish what we started with PulseAudio"
date: 2008-11-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rockin_goliath on 2008-11-10
I have to say, I am a much more relaxed man now that PulseAudio is the default sound server. I have very few problems now, except the surround sound bug, which should be fixed soon.

However, the GUIs that we provide no longer integrate with the systems they are supposed to be controlling. When one opens Preferences-Sound and clicks on an item, you are presented with a list of ALSA devices (which display several entries for the same device, which is very confusing), a list of OSS devices (again, multiple entries for the same device) and then a choice between the PulseAudio, ALSA, and OSS servers themselves. When you click on "Default Mixer Tracks," you are not changing the default global sound output, just the tracks that will be displayed in the volume applet. If someone really wants to configure their audio, they need to install padevchooser, which is very confusing to use and most of the time provides way more configuration options than the user is looking for. I'm sure you all agree this needs some tidying up.

I propose that we merge both the Volume Applet and gnome-sound-properties. This new GUI should only list the devices detected by the PulseAudio sound server, instead of PulseAduio, ALSA, and OSS and the servers themselves. The devices should be given human readable names instead of something like "Audigy 2 ZS [SB0353] (rev.4, serial:0x10031102) Multichannel Capture/PT Playback (ALSA)" (yes, that is actually how my sound card is listed). Audigy 2 ZS would be just fine. "Sound Events," "Music and Movies," and "Audio Conferencing" options should all be removed, and replaced with one, global control for the sound output and one for sound input. There would be one tab for output and one tab for input. Depending on which device you selected, the corresponding volume controls would appear below. When a new audio device is plugged in, such as a USB headset, it automatically becomes the global default. Finally, the volume applet should control only the volume of the currently selected device. If you are using a laptop and you have headphones plugged in, your laptop's volume buttons should control the headphone volume, not the master volume (which wouldn't do anything). 

Anyone who wanted configurations any more complex than these, such as network audio or per-application volumes, could install padevchooser. See the attached mockup for my *perfect* Gnome audio GUI. Forgive my GIMP skills. Of course, the tab for system sounds would be there as well.

What do you all think of this? Is this doable? Better still, is something like this *planned*?

---

### Post by MaX on 2008-11-10
A friend of mine just installed 8.10 and here mic registers output in PulseAudio (after we turned on Mic Boost) but it won't transfer that sound into Empathy... For me it works so the conversation is kind of one-sided...
These kind of things make people irritated about Linux in general, I could probably troubleshoot the problem but we are 400km apart so it's kind of hard when the remote desktop doesn't work either, I don't even get a can't connect message.

---

### Post by plun on 2008-11-10
**_GNOME Media_**

    *   Replace gnome-volume-control with a PulseAudio mixer, and/or a higher-level device control UI 


[http://live.gnome.org/RoadMap](http://live.gnome.org/RoadMap)


According to PAs mailing list padevchooser is soon deprecated... 


I am running PA ver .14 from GIT and everything works for the first time...:) also "rock solid" except for streams but that error can probably easily be nailed during better testing for Jaunty.

---

### Post by Colonel Kilkenny on 2008-11-10
I have to agree. All the sound controls are horrible and confusing.
And there should be a way to choose the current physical setup (2 chan, 4.1, 5.1, 7.1, etc.) as well. With pictures to demonstrate the configuration it would be even better.

---

### Post by Gina on 2008-11-10
+1

---

### Post by Slug71 on 2008-11-10
+1 again.

The whole sound thing in general for Linux seems to be very bloated.

---

### Post by raccoonone on 2008-11-10
Agreed. Sound issues are my biggest problem in 8.10, I constantly have to restart Pidgin because the sound stops working after a few hours of use.

---

### Post by Stochastic on 2008-11-10
Agreed.  Sound issues are kinda giving Ubuntu a bad rap.  Aditionally, if a program required a different sound server, there's no real method of indicating that to the new user unless the individual programs display their own message.  It'd be nice if Ubuntu auto-launches jack or oss or whatever if that's all the specified program will work with (or at least post an error message to the screen that mentions such audio servers need to be installed).

A large number of advanced computer musicians who are new to linux audio try to run jack dependent programs without realizing they need to start jack first.  Then they complain that the given program (or worse linux audio in general) is broken.

---

### Post by gnomeuser on 2008-11-11
The following might be interesting.

[https://fedoraproject.org/wiki/Desktop/Whiteboards/VolumeControl](https://fedoraproject.org/wiki/Desktop/Whiteboards/VolumeControl)
[https://fedoraproject.org/wiki/Desktop/Whiteboards/VolumeApplet](https://fedoraproject.org/wiki/Desktop/Whiteboards/VolumeApplet)

What I crave the most is a way to set up my sound setup correctly for 5.1 using a nice GUI. openSUSE does this but according to upstream their patch is insufficient and very ugly.

---

### Post by Timon&amp;Pumba on 2008-11-11
It may be a long shot, because a simple and clear GUI does not even exist, but for surround sound support I would like to propose the following.
[LIST=1]
[*]let the user choose their sound setup from a list (2.0, 5.1, 7.1, etc.)
[*]the system (pulseaudio I think) should output sound to each channel consecutively, and the user should point to the correct speaker that is playing the sound.
[/LIST]

It has some benefits:
[LIST]
[*]If hardware detection is not perfects, there is a way to correct it
[*]We can support multiple configurations, for example useful when the user both (not at the same time) watches movies on its monitor and on its tv, being 90 degrees rotated.
[/LIST]

[IMG]http://www.microsoft.com/windows/windowsmedia/images/howto/wma9_pro_playback06.gif[/IMG]

---

### Post by Stochastic on 2008-11-11
> **Timon&Pumba said:**
> 
[*]let the user choose their sound setup from a list (2.0, 5.1, 7.1, etc.)


It should be noted that there's also 4.0, 8.0, and 8.1 (even 16.2) setups that are common in more academic spatialization - the more flexibility the better (though that flexibility is kinda what's created this whole sound config mess in the first place).

---

### Post by plun on 2008-11-11
The challenge with this is probably Alsa

This is the wiki for Surround Sound

[http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound)


Jaunty runs with **Alsa 1.0.18** and I have detection errors with
my Audigy 2 card and also with my USB sound system.

---

### Post by garba on 2008-11-11
I was going to start a thread about this problem myself. I couldn't agree more. Exposing low level stuff like OSS/ALSA/Pulseaudio to the end user is ridicolous.

---

### Post by MaX on 2008-11-11
> **Stochastic said:**
> It should be noted that there's also 4.0, 8.0, and 8.1 (even 16.2) setups that are common in more academic spatialization - the more flexibility the better (though that flexibility is kinda what's created this whole sound config mess in the first place).

Why settle for this, why not X.Y.

I have 2.1 sound most of the time... sometimes 3.1 sound, neither is "standard" but I do have it. So why can't I send bass signals to my subwoofer?

---

### Post by mdurham on 2008-11-11
Sound? Sound on Linux a mess? What do you mean?

---

### Post by crjackson on 2008-11-11
> **mdurham said:**
> Sound? Sound on Linux a mess? What do you mean?

Just looking at this mess, the video driver mess, and reflecting on the trouble I've had since PA was added makes me consider going back to the other side.

---

### Post by Stochastic on 2008-11-12
> **mdurham said:**
> Sound? Sound on Linux a mess? What do you mean?

The funniest part about this is that I can spot at least four arrows missing right away!


There's no way to combine all of these servers together elegantly, from what I can see, as they each have an army of software written purely to adapt to unique audio situations. Thankfully, most of what's drawn here is under the hood away from everyone, and some of it, people won't ever use (esd? jack?) but other people will really need (the only way out my FFADO card is through Jack).  Would it be possible at install time to have a better method of customizing to the particular user?  Is that what's needed here?

---

### Post by ShirishAg75 on 2008-11-12
> **mdurham said:**
> Sound? Sound on Linux a mess? What do you mean?

OT but how were u able to make that diagram?

Another thing Timon& Pumba [http://ubuntuforums.org/showpost.php?p=6150014&postcount=10](http://ubuntuforums.org/showpost.php?p=6150014&postcount=10)

from where did you get that UI for surround sound? That is cool :)

Another thing I read everybody running PA 0.9.13 or PA 0.9.14 or whatever, but on my box its 0.10  0.9.10-2ubuntu9

```

$ dpkg -l pulseaudio
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  pulseaudio                0.9.10-2ubuntu9           PulseAudio sound server

```

I am on jaunty

---

### Post by Slug71 on 2008-11-12
Does NAS need to be there?

Both aRTS and SDL both go to NAS which redirects it to OSS.
Cant aRTS and SDL just go straight to OSS?

---

### Post by MacUntu on 2008-11-12
Linux sound and confusing? Naaa...

> The ALSA library plugin "jack" allows the ALSA library to
play or capture via JACK. (This should not be confused with
the jackd output driver "alsa", included in the jackd
package, which allows the JACK daemon to play back via the
ALSA library.)

:D

Shouldn't PA as ESD replacement in combination with "make ALSA use PA" be sufficient for most users? Too simple? :)

---

### Post by rockin_goliath on 2008-11-12
A lot of the complicatedness of Linux audio you are all describing no longer applies with PulseAudio. Gstreamer itself now natively uses PA, and PulseAudio also has plugins to handle applications that use ALSA and OSS. As long as developers update their programs to use PA, the mess really isn't that confusing. However, it's on the driver side and device configuration where things get confusing. It's pretty easy to enable surround sound with PA, it just involves editing a conf file, but users shouldn't have to do that. Speaker configurations and volume levels should be automatically detected and configured if possible. It is my understanding that all of this can be accomplished with a good GUI to control the audio systems.

In summary, the lower level stuff is pretty much good (with a few loose ends here and there, I am talking to you SKYPE), we just need to wrap up the transition to PA with a good GUI.

---

### Post by crjackson on 2008-11-14
> **rockin_goliath said:**
> A lot of the complicatedness of Linux audio you are all describing no longer applies with PulseAudio. Gstreamer itself now natively uses PA, and PulseAudio also has plugins to handle applications that use ALSA and OSS. As long as developers update their programs to use PA, the mess really isn't that confusing. However, it's on the driver side and device configuration where things get confusing. It's pretty easy to enable surround sound with PA, it just involves editing a conf file, but users shouldn't have to do that. Speaker configurations and volume levels should be automatically detected and configured if possible. It is my understanding that all of this can be accomplished with a good GUI to control the audio systems.

In summary, the lower level stuff is pretty much good (with a few loose ends here and there, I am talking to you SKYPE), we just need to wrap up the transition to PA with a good GUI.

My primary complaint is that both on Hardy and Intrepid, any application I launch that needs sound works on a 1st come 1st serve basis. Often times when playing a video file, I get an "Unknown Error" related to the device being used by another application (no other applications running though) and can only regain sound by loging off/on again.

It really doesn't FEEL like it's all that great. Only one app. at a time can produce sound, and sound crashing for no reason.

---

### Post by minisori on 2008-11-14
killall pulseaudio

Alsa alone used to work much better in previous ubuntu versions :s

---

### Post by danf_1979 on 2008-11-14
My latest problem with sound is that sometimes it seems to jam, Like those scratched music CDs. Annoying as hell. "Its a kind of magic ic ic ic ic ic ic ic ic ic ic..." :)

---

### Post by Slug71 on 2008-11-15
> **danf_1979 said:**
> My latest problem with sound is that sometimes it seems to jam, Like those scratched music CDs. Annoying as hell. "Its a kind of magic ic ic ic ic ic ic ic ic ic ic..." :)

That used to happen to me too but hasnt happened since 2.6.27 came to Intrepid i think.

My internal Mic no longer works though. In my Volume Control Properties i no longer have an option for Digital. The damn Sound Recorder doesnt work anymore, the minutes tick like damn seconds. The volume also seems to be quieter. :mad:

And now Lukes PPA's for 0.9.13 has broken X :mad::mad:

Bring on Jaunty!

---

### Post by jocko on 2008-11-17
> **crjackson said:**
> My primary complaint is that both on Hardy and Intrepid, any application I launch that needs sound works on a 1st come 1st serve basis.

That's probably because you try to use alsa in some apps and pulseaudio in others. As alsa can't mix audio streams (unless you are using a software mixer or are among the few lucky ones where the alsa drivers actually supports hardware mixing), whichever app use alsa first (pulseaudio or an other app set to use alsa) will gain exclusive access to the sound hardware.
If you make sure you set all your applications to use pulseaudio you won't notice this.
Another thing which will help is to set up the pulseaudio plugin in alsa (I think this is done by default, but if you have a separate /home partition your old configuration in $HOME/.asoundrc will be used instead...), so that every program that is set to use the alsa "default" sound card will be redirected to pulseaudio:
```
asoundconf set-pulseaudio
```

---

### Post by psyke83 on 2008-11-17
As far as I can see, PulseAudio integration has been improved a lot in Intrepid - but it's not without issues.

The main priorities for the next release should be:
[LIST=1]
[*]To have better integration of the PulseAudio GUIs (has already been discussed here), or at the very least, ensure a default installation will provide the current PulseAudio GUI utilities by default.
[*]Finding a way to ensure that users' systems are migrated to PulseAudio **cleanly**. Many Intrepid users suffered problems because they upgraded from Hardy with a suboptimal PulseAudio configuration.
[*]More focus on improving the documentation for PulseAudio in Ubuntu; at least add some useful information in the release notes.
[/LIST]
Most users will get a "perfect" PulseAudio configuration by following [this]("http://ubuntuforums.org/showthread.php?t=789578") guide, but this shouldn't even be necessary.

Unfortunately, for each single source of information on this forum and various websites that is useful, you'll find ten posts advocating more destructive steps such as:
[LIST]
[*]advising users to install libflashsupport to allow Flash to work correctly with PulseAudio ([and neglecting to mention that Firefox will crash every 5 minutes as a result]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/192888"));
[*]advising users to use the OSS driver as their "Sound playback" device in System/Preferences/Sound (while neglecting to mention that a) the "OSS" drivers are in fact emulated by ALSA and cannot mix sound by default, and b) this preference application only affects GStreamer applications - every other application will be unaffected);
[*]advocating users to OSSv4 (when it's not a supported configuration for Ubuntu, will cause more issues than it will solve, and is not compatible with PulseAudio);
[*]advocating users to install ALSA from source (when the source of their problem is perhaps a simple PulseAudio configuration issue).
[/LIST]
The audio situation on Linux is a mess right now, but some unified effort on the part of distributions can help simplify things a lot.

---

### Post by psyke83 on 2008-11-17
> **jocko said:**
> That's probably because you try to use alsa in some apps and pulseaudio in others. As alsa can't mix audio streams (unless you are using a software mixer or are among the few lucky ones where the alsa drivers actually supports hardware mixing), whichever app use alsa first (pulseaudio or an other app set to use alsa) will gain exclusive access to the sound hardware.
If you make sure you set all your applications to use pulseaudio you won't notice this.
Another thing which will help is to set up the pulseaudio plugin in alsa (I think this is done by default, but if you have a separate /home partition your old configuration in $HOME/.asoundrc will be used instead...), so that every program that is set to use the alsa "default" sound card will be redirected to pulseaudio:
```
asoundconf set-pulseaudio
```

That's correct. Let me also note, however: Intrepid's ALSA libraries have been patched to autodetect PulseAudio, and use the PulseAudio ALSA plugins by default if the PulseAudio server is running. Therefore, this command is only necessary for Hardy.

---

### Post by jerrylamos on 2008-11-17
No audio at all.  Pulse Audio is the sound of silence.  Useless.

IBM Thinkpad R31 Multimedia audio controller: Intel Corporation 82801CA/CAM 

This is a dual boot Jaunty & Intrepid.  I check the latest updates on Jaunty, look briefly for bugs, then boot back to Intrepid as an "ordinary user" looking at news videos & audio, mail, Office, digital photos including video + audio of family solos & quartets, etc.

I'll check Jaunty updates and then try Alpha 1 when available to see if it's any more functional.

Jerry

---

### Post by psyke83 on 2008-11-17
> **jerrylamos said:**
> No audio at all.  Pulse Audio is the sound of silence.  Useless.

IBM Thinkpad R31 Multimedia audio controller: Intel Corporation 82801CA/CAM 

This is a dual boot Jaunty & Intrepid.  I check the latest updates on Jaunty, look briefly for bugs, then boot back to Intrepid as an "ordinary user" looking at news videos & audio, mail, Office, digital photos including video + audio of family solos & quartets, etc.

I'll check Jaunty updates and then try Alpha 1 when available to see if it's any more functional.

Jerry

How can you possibly know the blame is PulseAudio? You're running a development release that's barely started uploading new packages and hasn't even reached the first alpha milestone. You should not expect anything to work correctly at such an early stage. More likely it's an ALSA bug than anything.

If you're referring to no audio in Intrepid, many users are seeing a bug where the PCM volume sometimes gets reset to 0 - that's not PulseAudio's fault either.

If you insist it's PulseAudio, then prove it - do some troubleshooting and file a bug (if applicable). See the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide, Appendix A.

---

### Post by crjackson on 2008-11-17
> **psyke83 said:**
> That's correct. Let me also note, however: Intrepid's ALSA libraries have been patched to autodetect PulseAudio, and use the PulseAudio ALSA plugins by default if the PulseAudio server is running. Therefore, this command is only necessary for Hardy.

I'm talking about a clean install of Intrepid. It has issues out of the box.

---

### Post by jerrylamos on 2008-11-17
Well, I've got an IBM Thinkpad R31 1 gHz and a Compaq Presario 3 gHz, both of which are dual booted with Intrepid and also with Intrepid with sources.list additions for jaunty,

Intrepid they both run System Preferences Sound Sound Playback just fine.  They both do You Tube Flash Video & audio fine, video is actually better than any other Ubuntu I've tried on them yet.

With early jaunty as updated daily, neither gets any sound at all out of System Preferences Sound Sound Playback or anything else I've found.  Jaunty on the Thinkpad R31 boots with sound playback on mute every time, so I set it to 100% on every boot.  Jaunty on the Compaq does remember to keep the volume 100%.

Compaq results for pkill pulseaudio && sleep 2 && pulseaudio -vv command as requested in Pulse Audio Fixes got a 17.8 kb txt file which is attached.

Jerry

---

### Post by ShirishAg75 on 2008-11-18
Just checked on Builds [https://launchpad.net/ubuntu/+builds](https://launchpad.net/ubuntu/+builds) 

apparently PA 0.9.13 being built for Jaunty, before the day is out I'm guessing people would have the new release on their hands (unless there is an FTBS or waiting for some dependancy issue)  Yay!

---

### Post by rockin_goliath on 2008-11-18
Can we have some more suggestions about what we would like to see in a GUI, so that developers have something to work from? More mockups, perhaps?

---

### Post by plun on 2008-11-18
> **rockin_goliath said:**
> Can we have some more suggestions about what we would like to see in a GUI, so that developers have something to work from? More mockups, perhaps?

This is done upstream on **Gnome level**, I have seen mockups.

See if I can find those...

---

### Post by ShirishAg75 on 2008-11-18
Well has anybody been able to play with pulseaudio 0.9.13 ?

---

### Post by plun on 2008-11-18
> **ShirishAg75 said:**
> Well has anybody been able to play with pulseaudio 0.9.13 ?

Yup and its the same as where we left it during Intrepis test.:)


With both ver .13 and .14 there are troubles with streamings...
Less with .14 but I cannot figure it out.  

Typical look during streams

I also switched to Alsa 1.018a so this one must be nailed.

> I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-bluetooth-discover.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-alsa-sink.c: Wakeup from ALSA! OUTPUT
I: module-alsa-sink.c: Underrun!
D: module-alsa-sink.c: Wakeup from ALSA! OUTPUT
**E: module-alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write! Most likely this is an ALSA driver bug. Please report this issue to the PulseAudio developers.**
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!


---

### Post by Slug71 on 2008-11-18
> **ShirishAg75 said:**
> Just checked on Builds [https://launchpad.net/ubuntu/+builds](https://launchpad.net/ubuntu/+builds) 

apparently PA 0.9.13 being built for Jaunty, before the day is out I'm guessing people would have the new release on their hands (unless there is an FTBS or waiting for some dependancy issue)  Yay! 

So why are they trying to make PA work on a Kernel that isnt even going to be in Jaunty?
Seems like a waste of time to me when 2.6.28 already has PA 0.9.13 and Alsa 1.0.18.

---

### Post by jocko on 2008-11-18
> **Slug71 said:**
> So why are they trying to make PA work on a Kernel that isnt even going to be in Jaunty?
Seems like a waste of time to me when 2.6.28 already has PA 0.9.13 and Alsa 1.0.18.

Are you saying pulseaudio is included in the kernel?
I seriously doubt that... As far as I know pulseaudio is still just a sound server and has no direct connection to the kernel whatsoever. It just outputs sound to whatever sound system it finds, using specific output plugins for the specific sound system (alsa, oss, whatever).
But it has to be built against the correct alsa version...
Anyhow, why is it a bad idea to build pulseaudio against whatever alsa version is ready at the moment? There may be bugs to fix or problems to solve that are not dependent on a specific alsa version (as far as I know, the only part of pulseaudio that is dependent on alsa is the actual alsa plugin, the rest should be completely independent of alsa).

---

### Post by plun on 2008-11-18
> **jocko said:**
>  There may be bugs to fix or problems to solve that are not dependent on a specific alsa version (as far as I know, the only part of pulseaudio that is dependent on alsa is the actual alsa plugin, the rest should be completely independent of alsa).

Well...  Alsa is tight with the kernel and as you see from my output
there are tons with underruns.

Those underuns are probably alsa/kernel related for streams.

Just to close all apps and fire up this command
```
[B]
pulseaudio -k; sleep 5; pulseaudio -vv[/B]
```
  

But you have settings for PA to play with.... just to find the best.

psyke83 has also updated his excellent howto:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

(not for Jaunty but everything works the same)

I should have choosed to skip ver 13 and go directly to ver 14... but its breaks "Debian thinking"...:)   "package mess maybe"...

---

### Post by ShirishAg75 on 2008-11-18
Well, 
 I'm on PA 0.9.13 but it seems it doesn't work ... yet. 

Did the following 

a.  Removed the .pulse directory as well as the .pulse-cookie. 
b. Then tried using gnome-sound-properties using pulseaudio it didn't work. 

c. At the end of it all, made sound events as well as sound playback back to ALSA. 

Music is back for the time being atleast.

---

### Post by plun on 2008-11-18
> **ShirishAg75 said:**
> Well, 
 I'm on PA 0.9.13 but it seems it doesn't work ... yet. 

Did the following 

a.  Removed the .pulse directory as well as the .pulse-cookie. 
b. Then tried using gnome-sound-properties using pulseaudio it didn't work. 

c. At the end of it all, made sound events as well as sound playback back to ALSA. 

Music is back for the time being atleast.

You must check with this command

```
pulseaudio -k; sleep 5; pulseaudio -vv
```


Also that you have padevchooser including pavucontrol installed.

Otherwise you are "blind"....  IMHO...

---

### Post by psyke83 on 2008-11-19
> **plun said:**
> Yup and its the same as where we left it during Intrepis test.:)


With both ver .13 and .14 there are troubles with streamings...
Less with .14 but I cannot figure it out.  

Typical look during streams

I also switched to Alsa 1.018a so this one must be nailed.

PulseAudio's Intrepid (and I assume also Jaunty) /etc/pulse/daemon.conf ships with tweaks to the fragment settings (to reduce stutter). However, these tweaks were for a version of PulseAudio prior to the "glitch-free" code being merged. Therefore, I recommend you comment the two fragment lines in your daemon.conf (see [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578"), Appendix B, question about stuttering).

That *may* stop some of those buffer underruns.

---

### Post by plun on 2008-11-19
> **psyke83 said:**
> PulseAudio's Intrepid (and I assume also Jaunty) /etc/pulse/daemon.conf ships with tweaks to the fragment settings (to reduce stutter). However, these tweaks were for a version of PulseAudio prior to the "glitch-free" code being merged. Therefore, I recommend you comment the two fragment lines in your daemon.conf (see [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578"), Appendix B, question about stuttering).
That *may* stop some of those buffer underruns.

Ok, thanks !

I have tried different values already and also to give PA high priority CPU permission but the overruns comes and goes...

And also just for streamings... :confused:

For the moment I am chrooting so no further tests....:)

---

### Post by Geekkit on 2008-11-19
> **rockin_goliath said:**
> I propose that we merge both the Volume Applet and gnome-sound-properties. This new GUI should only list the devices detected by the PulseAudio sound server, instead of PulseAduio, ALSA, and OSS and the servers themselves. The devices should be given human readable names instead of something like "Audigy 2 ZS [SB0353] (rev.4, serial:0x10031102) Multichannel Capture/PT Playback (ALSA)" (yes, that is actually how my sound card is listed). Audigy 2 ZS would be just fine.

+1 From me!

---

### Post by ShirishAg75 on 2008-11-19
Hi all, 
 This is my /etc/pulse/daemon.conf file. 

```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; disallow-exit = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = 20
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = speex-float-1
; disable-remixing = no
; disable-lfe-remixing = yes

; no-cpu-limit = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rtttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 48000
; default-sample-channels = 2

default-fragments = 8
default-fragment-size-msec = 5

```

I am specifically interested in 

```
resample-method = speex-float-1
```

and as given in pyske's thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) 

> You can change the resampler to any of the following, listed in descending order, from highest quality to lowest quality (and therefore, CPU usage):

src-sinc-best-quality, src-sinc-medium-quality, src-sinc-fastest, speex-float-{10-0}, speex-fixed-{10-0}, ffmpeg, src-zero-order-hold, src-linear, trivial 			 		

now within speex-float how can I make it better sound quality?

---

### Post by psyke83 on 2008-11-20
> **ShirishAg75 said:**
> now within speex-float how can I make it better sound quality?

Honestly, the resampler currently is pretty good already. The previous default was "speex-float-3" (though we decided to change it in an attempt to reduce CPU usage; see [this comment]("https://bugs.launchpad.net/paconfig/+bug/190754/comments/143")). The current resampler is higher quality than ALSA's default resampler in dmix.

If you're experiencing distortion, you may need to reduce your mixer levels (to around ~75%), as many AC'97 codecs seem to experience distortion in ALSA.

---

### Post by bash on 2008-11-20
Better Volume Control and managing of sound preferences for PulseAudio just got approved for Fedora 11:

[https://fedoraproject.org/wiki/Features/VolumeControl](https://fedoraproject.org/wiki/Features/VolumeControl)

I looks pretty neat and seems to tackle quite a bit of GUI related complaints from users so far. As some of the works happens upstream as well I assume some of not all of this will find its way into Ubuntu and/or GNOME. Keep in mind though this is scheduled for Fedora 11 which comes out after Jaunty, so don't expect this before Ubuntu 9.10.

---

### Post by Geekkit on 2008-11-20
> **bash said:**
> Better Volume Control and managing of sound preferences for PulseAudio just got approved for Fedora 11:

[https://fedoraproject.org/wiki/Features/VolumeControl](https://fedoraproject.org/wiki/Features/VolumeControl)

I looks pretty neat and seems to tackle quite a bit of GUI related complaints from users so far. As some of the works happens upstream as well I assume some of not all of this will find its way into Ubuntu and/or GNOME. Keep in mind though this is scheduled for Fedora 11 which comes out after Jaunty, so don't expect this before Ubuntu 9.10.

Ooo, that looks nice. That and USB headphone support too? That too would be nice although from my experience with this working it would not be a game of catching up to Windows Vista but rather leaving Vista in the dust (I have yet to get USB headphones in Vista working whereas in Linux I have got it sort of working).

---

### Post by psyke83 on 2008-11-20
> **Geekkit said:**
> Ooo, that looks nice. That and USB headphone support too? That too would be nice although from my experience with this working it would not be a game of catching up to Windows Vista but rather leaving Vista in the dust (I have yet to get USB headphones in Vista working whereas in Linux I have got it sort of working).

USB headphones work fine with PulseAudio, but the GUIs needs some improving to make things more intuitive.

Read the FAQ and Appendix B of: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Note: ALSA is currently screwed in Jaunty. Don't expect sound (headphones or otherwise) to work correctly right now.

---

### Post by Geekkit on 2008-11-20
> **psyke83 said:**
> USB headphones work fine with PulseAudio, but the GUIs needs some improving to make things more intuitive.

Read the FAQ and Appendix B of: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Note: ALSA is currently screwed in Jaunty. Don't expect sound (headphones or otherwise) to work correctly right now.

Thanks for that info. I will wait for at least the candidate release version.

---

### Post by plun on 2008-11-21
> **psyke83 said:**
> USB headphones work fine with PulseAudio, but the GUIs needs some improving to make things more intuitive.

Read the FAQ and Appendix B of: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Note: ALSA is currently screwed in Jaunty. Don't expect sound (headphones or otherwise) to work correctly right now.

Well... if its Alsa or PA which is "screwed" can be a question ?

I didn't spoil much time with PA 0.9.13 but it was impossible to run with Alsa l.0.18.

Recompiled PA 0.9.14 and everything works again including USB output to a sound system.

PA 0.9.14 requires a autoconf version higher then in Jauntys repo, available within Debian experimental.

Without checking I am sure that Fedora 10 uses ver 14 code...:)


EDIT  also compiled 1.0.18a and this is maybe important...

> WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.


---

### Post by Changturkey on 2008-11-22
If Ubuntu is using Pulse, where is the Pulse GUI? It is still the standard one "bar" GUI.

---

### Post by olskar on 2008-11-22
> **Changturkey said:**
> If Ubuntu is using Pulse, where is the Pulse GUI? It is still the standard one "bar" GUI.

I think you will find it in Sound&Video after installing pulseaudio-utils or something like that

---

### Post by plun on 2008-11-22
> **Changturkey said:**
> If Ubuntu is using Pulse, where is the Pulse GUI? It is still the standard one "bar" GUI.

Just install **padevchooser** as the package is named, then you will have all Pulse GUIs.   Starters > Sound and Video 

Gnome is working with a new GUI....

Edit...about
[http://packages.ubuntu.com/jaunty/pulseaudio](http://packages.ubuntu.com/jaunty/pulseaudio)

---

### Post by bash on 2008-11-22
> **Changturkey said:**
> If Ubuntu is using Pulse, where is the Pulse GUI? It is still the standard one "bar" GUI.

It isn't there because it simply does not exist yet. There are atm the GUI tools that come with Pulse (which aren't really perfect) and there is still the old gnome-volume-control applet from GNOME. Currently Fedora and Upstream (GNOME) are working on a new, "streamlined" volume control. Which according to schedule will be ready after Jaunty is released.

---

### Post by Changturkey on 2008-11-22
> **bash said:**
> It isn't there because it simply does not exist yet. There are atm the GUI tools that come with Pulse (which aren't really perfect) and there is still the old gnome-volume-control applet from GNOME. Currently Fedora and Upstream (GNOME) are working on a new, "streamlined" volume control. Which according to schedule will be ready after Jaunty is released.

Aw, after Jaunty...

---

### Post by antiloop on 2008-11-23
Sound in Linux and Ubuntu really is a mess... hope they sort it out and less bloat please.

---

### Post by plun on 2008-11-24
I think a lot are resolved now....  patches and corrections from Debian Experimental
(PA GIT patches which also Fedora uses)

> pulseaudio (0.9.13-2ubuntu1) jaunty; urgency=low

  * Merge from Debian experimental, remaining changes:
    - Don't build against, and create jack package. Jack is not in main.
    - Remove --disable-per-user-esound-socket from configure flags, as we still
      want per user esound sockets.
    - Remove stop links from rc0 and rc6.
    - Change default resample algorithm and bubffer size.
    - Add alsa configuration files to route alsa applications via pulseaudio.
    - Move libasound2-plugins from Recommends to Depends.
    - debian/pulseaudio.preinst: When upgrading from intrepid, remove
      /etc/X11/Xsession.d/70pulseaudio, as this was used to minimize a race
      condition when starting GNOME in intrepid. This race should not exist in
      jaunty once libcanberra is built to use pulseaudio as a backend.
    - Do not spawn a pulseaudio server if clients fail to find a running server.
    - Regenerate autotools files for ubuntu.

pulseaudio (0.9.13-2) experimental; urgency=low

  * Rename libpulsecore5 to libpulsecore8 to correctly reflect the soname
    (Closes: #503612)
  * 0003-make-sure-to-use-64bit-rounding-even-on-32bit-machin.patch
    - Fix rounding errors on 32 bit machines. From upstream git
  * 0004-properly-remove-dbus-matches-an-filters-when-unloadi.patch
    - Properly remove dbus filters when unloading the bluetooth module
  * 0005-Fix-two-typos-that-broke-tunnels.patch
    - Fix tunnels. From upstream git


[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001049.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001049.html)




> libcanberra (0.10-1ubuntu1) jaunty; urgency=low

  * Merge from Debian experimental, Remaining changes:
    - Use the Ubuntu sound theme as the default and fallback theme.
    - Update libltdl build dependency.
  * Build-depend on quilt.
  * Build against pulseaudio.

libcanberra (0.10-1) experimental; urgency=low

  * New Upstream Version
  * Move "canberra-gtk-play" from libcanberra-gtk-dev in libcanberra-gtk0.
  * Add gnome-session-canberra to play log in/out events.
  * Add 52libcanberra-gtk-module_add-to-gtk-modules to /etc/X11/Xsession.d to load
    the GTK module.
  * 0001-Remove-debug-warning-about-GtkSettings-from-2.13.4.patch,
    debian/control,
    debian/README:
    + do not depends on GTK 2.13.4 yet
    + remove debug message about that from canberra-gtk-module
  * Add tdb-dev dependency, for lookup caching.

[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001060.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001060.html)



I can hear the jungle drums again....:)

---

### Post by psyke83 on 2008-11-24
> **plun said:**
> I think a lot are resolved now....  patches and corrections from Debian Experimental
(PA GIT patches which also Fedora uses)






I can hear the jungle drums again....:)

It's still a regression from 0.9.10. For example, try the ALSA output from VLC. It doesn't work with 0.9.13. Also, GStreamer applications (Totem) seem to stutter as a result of PulseAudio.

---

### Post by plun on 2008-11-24
> **psyke83 said:**
> It's still a regression from 0.9.10. For example, try the ALSA output from VLC. It doesn't work with 0.9.13. Also, GStreamer applications (Totem) seem to stutter as a result of PulseAudio.

Well... I still got PA 0.9.14 installed and also Alsa 1.0.18a.
Ubuntus sound was just a scratchy noise before..

ColinG is absolutely clear about Fedoras patches and latest Alsa,  LennartP is away for the moment.

A big step forward nevertheless to take "the Experimental step"...

I also dont know why LennartP switched to autoconf, 2.63 for PA 0.9.14 ?

Its also better to take a real mess now in the beginning...IMHO.  


See if I downgrade or wait for more patches...:)   Clean PA-GIT is perfect for me. (for the moment...)


Another issue... I don't understand is why PA doesn't load everything....

[http://paste.ubuntu.com/76340/](http://paste.ubuntu.com/76340/)

Also testing with a little more priority...:)



EDIT   Typical output...  Exaile running LastFM

[http://paste.ubuntu.com/76346/](http://paste.ubuntu.com/76346/)

EDIT... the same with Rhythmbox
[http://paste.ubuntu.com/76352/](http://paste.ubuntu.com/76352/)


.

---

