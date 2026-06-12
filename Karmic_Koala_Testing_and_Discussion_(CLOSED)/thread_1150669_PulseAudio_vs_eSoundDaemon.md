---
title: "PulseAudio vs eSoundDaemon"
date: 2009-05-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by panaut0lordv on 2009-05-06
PulseAudio:
-Newer
-'Better'
-5.1 capable
-eSound based
really:
-troublecausing
-unable to share sound server

eSoundDaemon:
-Older
-'Obsolete'
really:
-troublefixing
-I haven't got any crashes or trouble using it

Question:
Why is that? Why PulseAudio, called new version of eSound doesn't work as supposed? Why to break something that was working fine?

---

### Post by gnomeuser on 2009-05-06
esound is bad in every way. It makes assumptions about your hardware and desired configuration. It locks the hardware device and does not provide a non-esound way of accessing it (meaning only esound enabled applications can do sound when esound is running).

Esound does not allow for network transparency, it does not concern itself with policy for situations like having multiple audio devices.

The codebase is filled with ugly hacks.

esound was also abandoned and has not been in active development in years.

---

### Post by taavikko on 2009-05-06
Why esound is still included, as a quick research only few apps/packages depends on it. wouldn't it be wise to demote or drop it all together.

For what purposes it is still needed?

---

### Post by panaut0lordv on 2009-05-06
So I want to use pulseaudio - but this crap doesn't allow me to use rhythmbox, skype, flash and other simultanously.

It is not just my issue! Why pulseaudio can't do that, while old, shitty esd CAN!?!

---

### Post by karolinak on 2009-05-06
I agree with panaut0lordv, its really annoying that I cant use skype and rhytmbox (and so on) simultanously. 

it's the only reason why I always remove my pulseaudio and it's really pissing me off :/

---

### Post by amano on 2009-05-06
Blame the Skype people for not releasing a version that can deal with Pulseaudio well.

---

### Post by panaut0lordv on 2009-05-06
Sure, skype is obsolete, we know :)

But even without skype, my rhytmbox wasn't playing after last pulseaudio boot (bootup sounds or ubudsl was first). So I decided to piss at it and switch to esd again.

---

### Post by gnomeuser on 2009-05-06
> **panaut0lordv said:**
> Sure, skype is obsolete, we know :)

But even without skype, my rhytmbox wasn't playing after last pulseaudio boot (bootup sounds or ubudsl was first). So I decided to piss at it and switch to esd again.

Did you file bugs?

Or did you just go on a pointless rant against PA before even identifying the root of the problem or informing the developers so they could actually fix your problem.

---

### Post by amano on 2009-05-06
> **panaut0lordv said:**
> Sure, skype is obsolete, we know :)

But even without skype, my rhytmbox wasn't playing after last pulseaudio boot (bootup sounds or ubudsl was first). So I decided to piss at it and switch to esd again.

Rhythmbox/Gstreamer is working fine for all of us. Thus the root of your problem might be broken alsa drivers for your card. Pulseaudio is pretty demanding featurewise and exhibited many problems in the audio driver stack that couldn't be noticed when using ESD. But the bugs were there.

---

### Post by panaut0lordv on 2009-05-07
I've red a lot of such bugreports, but I'll give it next chance :)

So, what logs do you need for complex debugging & correct bug report?

---

### Post by smbm on 2009-05-07
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by 23meg on 2009-05-07
> **panaut0lordv said:**
> 
So, what logs do you need for complex debugging & correct bug report?

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by seeker5528 on 2009-05-08
> **gnomeuser said:**
> esound is bad in every way. It makes assumptions about your hardware and desired configuration. It locks the hardware device and does not provide a non-esound way of accessing it (meaning only esound enabled applications can do sound when esound is running).

Have not seen that type of issue with ESD with my hardware for several years, ARTS on the other hand was a PITA. Could be I never saw those issues because I only installed the minimum amount of ESD stuff that was required by packages I had installed.

Pulse makes equally bad assumptions, taking it one step further by saying 'all your sound is belonging to me'. Man that is so 90s. :P

That's really the only issue I have with pulse relative to the stuff I do.

I'm not happy about the Jack deamon grabbing exclusive access to the sound card either, but at least it has a reason since if you are running an application that uses it there is a little more expectation that latency is probably a concern to you.

Both of these should provide an option about whether you want them to grab exclusive access or not. And at least in the case of Pulse the default should be 'do not grab exclusive access'.

Later, Seeker

---

### Post by Nullack on 2009-05-08
> **seeker5528 said:**
> Pulse makes equally bad assumptions, taking it one step further by saying 'all your sound is belonging to me'. Man that is so 90s. :P

Thats an underlying architectural principle of PulseAudio's design. Its not a problem. Its like saying the X server wants to run the show and claiming its a problem.

---

### Post by Gnea on 2009-05-08
Part of the 'problem' with Pulseaudio in Ubuntu is that it doesn't have much in the way of automatic setup detail, the way that other distributions have it.  For many, this isn't a problem and they can figure it out.  For others, such as the OP, this creates a lot of confusion and frustration.  

There are specific howtos (See [https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")) that explain how to get pulseaudio to behave correctly.  But different soundcards and systems react differently.

:guitar:

---

### Post by psyke83 on 2009-05-08
> **Gnea said:**
> Part of the 'problem' with Pulseaudio in Ubuntu is that it doesn't have much in the way of automatic setup detail, the way that other distributions have it.  For many, this isn't a problem and they can figure it out.  For others, such as the OP, this creates a lot of confusion and frustration.  

There are specific howtos (See [https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")) that explain how to get pulseaudio to behave correctly.  But different soundcards and systems react differently.

:guitar:

Since Jaunty, a specific PulseAudio guide isn't really necessary (except perhaps to purge obsolete configuration files left over from distribution upgrades, or to inform users about basic PulseAudio functionality). The developers have really done a good job integrating it into the system this time to the point where it Just Works. In comparison, integration in Hardy was a mess, and Intrepid only marginally better.

The complaints I see in this thread are that Skype + another application cannot mix sounds (although those other applications work together fine). Well gee whiz, you may be surprised to know that it's Skype fault - it tries to access your sound card directly via the ALSA API. In the past, this behaviour didn't cause a lot of problems if you were using ALSA's dmix, but now it causes issues with PulseAudio - and it really is Skype's fault.

You can fix this by changing the default sound card in Skype's options, though. Certain applications need tweaking as well, such as WINE and legacy OSS applications. My guide documents some of the most common offenders.

P.S. Most of the instructions on the wiki page for PulseAudio are redundant. For example, users don't need to create a .asoundrc or asound.conf files if they're using Intrepid or newer, Flash doesn't need any special setup, etc.

---

### Post by lswb on 2009-05-09
> **panaut0lordv said:**
> PulseAudio:

<...skipped...>
Question:
Why is that? Why PulseAudio, called new version of eSound doesn't work as supposed? Why to break something that was working fine?

That is the linux way; if it ain't broke, fix it.

---

### Post by seeker5528 on 2009-05-09
> **psyke83 said:**
> 
The complaints I see in this thread are that Skype + another application cannot mix sounds (although those other applications work together fine). Well gee whiz, you may be surprised to know that it's Skype fault - it tries to access your sound card directly via the ALSA API. In the past, this behaviour didn't cause a lot of problems if you were using ALSA's dmix, but now it causes issues with PulseAudio - and it really is Skype's fault.

If Skype is using the Alsa API and Skype + Dmix + someother application works fine, then how can it be Skype's fault that adding pulse to the mix causes these same application not to work together?

Later, Seeker

---

### Post by seeker5528 on 2009-05-09
> **Nullack said:**
> Thats an underlying architectural principle of PulseAudio's design. Its not a problem. Its like saying the X server wants to run the show and claiming its a problem.

If I were to hit Ctrl+Alt+F1, run something and the out put was unnecessarily being routed though some X windows stuff on the way to the display because the xserver is still running then yes it would be the same thing. 

If I go into the options of an application and set it to use alsa out put, I want it to use alsa output, I don't want the output to be hijacked by something else.

Similarly if I took the trouble to download OSS, compile it, install it, and set the applications to use it, I don't want that output being hijacked along the way.

I have no problem with Pulse being installed by default and applications being set to use it by default *if* it doesn't grab exclusive access to the sound card by default, and doesn't hijack alsa or OSS output by default. (OSS in this case being the downloaded from 4Front, compiled, and installed OSS, not the alsa-oss compatibility stuff)

Even if it does grab exclusive access to the sound card by default, it wouldn't be so bad if I could go check/uncheck a box somewhere to change that.

Later, Seeker

---

### Post by gnomeuser on 2009-05-09
> **seeker5528 said:**
> If Skype is using the Alsa API and Skype + Dmix + someother application works fine, then how can it be Skype's fault that adding pulse to the mix causes these same application not to work together?

Later, Seeker

They abuse the ALSA API, they even admit so on their forums. They also don't care one bit about their Linux port, I have bugs filed with them going back years that are still open and valid. 

They haven't updated their Linux port in about a year. No current Linux distros are actually supported. 

There is no 64 bit build available.

The list of grievances goes on, but as for why it doesn't work with pulseaudio proper the answer is simply that skype is implemented in such a way as to misuse alsa in ways as of yet unimagined by mankinds frail minds. We can't fix Skype, only people with access to the source code can.

Also worth noting would be that skype doesn't work right on the nokia n810 either (hangs up calls after 2½ hours, randomly hangs the device and crashes) nor my cellphone (hangs up calls, constantly resyncs, hangs the phone and as the master piece it can occasionally decide to lock up the entire device requiring a cold restart).

---

### Post by markbuntu on 2009-05-09
The biggest problem with pulse in ubuntu is that the entire sound system is misconfigured by default. Setting autodetect in Sound directs alsa and oss apps to not use pulseaudio and directly address the hardware drivers. This is a default for conflict, confusion, frustration and anger as only the first opened app will have access to the hardware. If the sound system was properly configured a lot of the problems people experience would go away.

Skype is just a bad joke. It does not work with the latest qt libs so you need to get the static version from medibuntu so you have the old qt libs it needs. Skype also makes assumptions about hardware in its alsa driver that are no longer valid snce the alsa hardware drivers have moved to the kernel. The defaults it installs with are just wrong. There is a lot more wrong with skype than just its inability to use pulseaudio.

Bad applications are no reason to complain about pulseaudio but you can complain about the bad pulse implementation in Ubuntu.

---

### Post by defaria on 2009-05-09
> **markbuntu said:**
> The biggest problem with pulse in ubuntu is that the entire sound system is misconfigured by default. Setting autodetect in Sound directs alsa and oss apps to not use pulseaudio and directly address the hardware drivers. This is a default for conflict, confusion, frustration and anger as only the first opened app will have access to the hardware. If the sound system was properly configured a lot of the problems people experience would go away.

Please then tell us what a "properly configured" sound configuration is instead of just bitching about it.

> Skype is just a bad joke. It does not work with the latest qt libs so you need to get the static version from medibuntu so you have the old qt libs it needs. Skype also makes assumptions about hardware in its alsa driver that are no longer valid snce the alsa hardware drivers have moved to the kernel. The defaults it installs with are just wrong. There is a lot more wrong with skype than just its inability to use pulseaudio.

Bad applications are no reason to complain about pulseaudio but you can complain about the bad pulse implementation in Ubuntu.

The real problem is that there is apparently no standard. Neither Skype nor any other audio application should be in the business of assuming anything, rather they should be coding to a known standard. Since their isn't one they are forced to make assumptions. You should not bad mouth applications that are thusly forced...

---

### Post by psyke83 on 2009-05-09
> **markbuntu said:**
> The biggest problem with pulse in ubuntu is that the entire sound system is misconfigured by default. Setting autodetect in Sound directs alsa and oss apps to not use pulseaudio and directly address the hardware drivers. This is a default for conflict, confusion, frustration and anger as only the first opened app will have access to the hardware. If the sound system was properly configured a lot of the problems people experience would go away.

Skype is just a bad joke. It does not work with the latest qt libs so you need to get the static version from medibuntu so you have the old qt libs it needs. Skype also makes assumptions about hardware in its alsa driver that are no longer valid snce the alsa hardware drivers have moved to the kernel. The defaults it installs with are just wrong. There is a lot more wrong with skype than just its inability to use pulseaudio.

Bad applications are no reason to complain about pulseaudio but you can complain about the bad pulse implementation in Ubuntu.

Incorrect. 

Firstly, the Sound preference application only applies to GStreamer applications (Totem, Rhythmbox, etc.). It is only system-wide by virtue of GNOME's official applications using the GStreamer framework. Other applications don't give a damn.

Secondly, when it is set to Autodetect, it will try to use the GStreamer sinks in the following order: PulseAudio -> ALSA -> OSS. This is the ideal configuration. Note that if you choose the ALSA output for GStreamer applications, audio will be routed to PulseAudio through the PulseAudio ALSA plugins anyway. Setting this option to OSS will prevent audio from being routed to PulseAudio - in this case, you need to use the padsp wrapper.

The real problem is that the user interface for sound in GNOME is counter-intuitive, because it does not properly account for the way PulseAudio functions - and it's not Ubuntu's fault. 

The Sound preference application should explicitly inform users that it applies only to GStreamer / "official" GNOME applications, rather than giving the impression that it can affect every application installed on your system (Skype, VLC, WINE, pretty much any non-GNOME application). Ideally, users should also be made aware that setting this to ALSA will cause audio to be routed to PulseAudio through the PA ALSA plugins.

Many users suffering with PulseAudio problems usually set their GStreamer sink to OSS, and because they hear sound they will assume that the problem is fixed. Unfortunately, they usually have no idea that this completely breaks sound mixing on their system and other application will continue to suffer the consequences of a broken PulseAudio configuration.

In my opinion, we need to ship the PulseAudio Volume Control by default, and perhaps think of ways to encourage upstream GNOME to smoothen their PulseAudio integration on the user-interface front - or else we could do the work in Ubuntu ourselves.

I agree about Skype, though. If you have a Windows installation and have seen the most recent release on that platform, you'll realize that the Linux client is barely maintained in comparison.

---

### Post by markbuntu on 2009-05-10
It has been a mystery to me why pavucontrol is not included in the install since Hardy. And it looks like it will not be in Koala since it is listed in reccomends instead of depends. module pulse-jack is also stripped out and libasound2 is crippled once again. Also it does not look like the kernel will be fixed so we can have glitch free. Instead we get tsched=0 and a degraded resample-method=sinc-source-linear. It is my fervent hope that all this can get fixed before October.

There are a lot of applications besides the ones you mention that are not automatically routed to pulse when Sound is set to autodetect, flash for one. The Gstreamer defaults are also wrong, and so are the xine defaults but that is more to accomodate kubuntu which is not supposed to come with pulse.

Anyway, the entire thing becomes a mess. Regardless of what does what and what is supposed to do what, it is all very confusing for the average user and does not work. It should just work, OOB.

In answer to defaria.

The alsa api was such a mess that there was no real standard for coding applications (over 10,000 possible api calls) but now there is with pulse (and phonon for KDE) which provide simplified standard apis for coding sound in applications. 

There is very little the community can do when closed source application developers are unwilling to update their code to conform to standards, or even fix bugs.

I was not complaining so much as explaining the situation. Between myself and psyke83 we have written the guides for getting sound working in Hardy,Intrepid and Jaunty that many thousands of people have used with great results. Do I need to post links?

---

### Post by bcschmerker on 2009-05-10
I noticed that some settings in other packages may complicate the situation.  From my own experience, I have to recommend against setting any Accessible Sounds in the Login Window Preferences (/usr/sbin/gdm-setup), as GDM will then hog the sound resources, leaving both ESounD and PulseAudio unusable.

On my now [ECS-equipped](http://www.ecsusa.com/) Everex ([AMD Athlon X2](http://www.amd.com/) MPU, [nVIDIA nForce 405/GeForce6100](http://www.nvidia.com/)) running 8.04-LTS, I currently have Sound Preferences set as follows, in order to get the best of the PulseAudio installation (including PulseAudio-ESounD-Compat) on my system:
```

[Devices]
*/Sound Events/*
Sound playback:  ESD - Enlightened Sound Daemon
*/Music and Movies/*
Sound playback:  ESD - Enlightened Sound Daemon
*/Audio Conferencing/*
Sound playback:  ESD - Enlightened Sound Daemon
Sound capture:  PulseAudio Sound Server
*/Default Mixer Tracks/*
Device:  HDA Nvidia (ALSA mixer)

```

With both the pulseaudio and pulseaudio-esound-compat packages installed, I have a PulseAudio installation that is backwards-compatible with most EsounD applications, excepting the deprecates mentioned elsewhere this Thread.

---

### Post by defaria on 2009-05-10
> **markbuntu said:**
> In answer to defaria.

The alsa api was such a mess that there was no real standard for coding applications (over 10,000 possible api calls) but now there is with pulse (and phonon for KDE) which provide simplified standard apis for coding sound in applications.

I find it hard to believe there are over 10,000 possible API calls. If I told you once I've told you a million times - never exaggerate! :)

> There is very little the community can do when closed source application developers are unwilling to update their code to conform to standards, or even fix bugs.

I was not complaining so much as explaining the situation. Between myself and psyke83 we have written the guides for getting sound working in Hardy,Intrepid and Jaunty that many thousands of people have used with great results.

Guides should not really be required. It should just work. It just works on Windows - why does it not just work here?

> Do I need to post links?

Of course you do.

---

### Post by markbuntu on 2009-05-10
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)


[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)


[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)


[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)


[http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)


[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)


[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by defaria on 2009-05-11
As has been said before, this is incredibly complex. To that I'd add "needlessly complex". The need to "server" sounds across your network is not generally something that people care about nor care to do (setting up a media server, perhaps, but that's different.

Thanks for the links however, labels for those links would have been appreciated. I'm on Jaunity so it seems to me that [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384) is most relevant to me. I can spend 4-5 hours consuming all this information (and I probably will do that eventually) but my basic quest right now is pretty simple - I'd like to get Boxee working. Boxee has lots of problems for me. Posting in the Boxee forums people say, paraphrasing... "PulseAudio sucks! Uninstall it. Then Boxee will go away". Of course they didn't both telling me what to use in its stead nor how to get rid of pluseaudio, etc... Right now most sound stuff works well so I'm a little hesitant to rip out one method of doing sound for another, not yet defined method of doing sound (I believe I've heard some say "Use esound" while others say use "alsa"??).

Again, I've never experience such complexity, choices, configuration options and indeed problems while on Windows. I'm no Windows fanatic - in fact I have no Windows anymore - but this sound stuff is, as I've said, unnecessarily complex.

---

### Post by markbuntu on 2009-05-11
Well I totally agree with that. My best experience with sound on linux was with Mandriva. Everything worked OOB.

---

### Post by BwackNinja on 2009-05-11
@defaria

The x server is obviously, a server too and you can redirect graphical programs across your network and even across the internet if you want to. Maybe needless, I'd say its probably rare but not unusual for someone to do that, but it doesn't mean it shouldn't be there.

And about boxee, it is a fork of xbmc, and and xbmc boasts pulseaudio support.

Esound isn't just not a good idea, but entirely deprecated. No gnome program uses it now (others still may, and many players such as mplayer and vlc have esd backends (plus a backend to everything else too (yay nested parenthesis!))).

I'm also a proponent of a configuration option for everything that could be useful more than one way, within reason of course. Pulseaudio has a lot of them, but not enough make their way out of config files in my opinion.

---

### Post by justken on 2009-05-11
Psyke83 - Thanks for the helpful posts and even more helpful 'howto' - I had a few issues with skype (delays, not running with exaile, etc.) and, after a bit of searching, found this.  You'll note that I don't post often but just wanted to say that the explanation of how things are with pulse and the solutions to those things that can be solved were spot on for clarity and usefulness.

---

### Post by crjackson on 2009-05-11
@psyke83 and markbuntu

After choosing your configuration(s), is it mandatory that PA Volume control be started on every boot (check box enabled in settings) in order for it's settings to persist?

I would like to choose the settings, then forget about it without the additional icon loading in the notification area.

---

### Post by panaut0lordv on 2009-05-11
The best fix I've managed to do after MANY hours of troubleshooting.

Install pulseaudio specific packages (eg. libsdl1.2debian-pulseaudio) + compatibilities (eg. pulseaudio-esound-compat alsa-oss). Remove all oss and esound.
Delete pulse&alsa configs from /etc
Reboot.

Everything should be recreated now correctly. Software mixing fine, no glitches - like it should be. Strange it can't be done in out of box installation.

---

### Post by psyke83 on 2009-05-11
> **crjackson said:**
> @psyke83 and markbuntu

After choosing your configuration(s), is it mandatory that PA Volume control be started on every boot (check box enabled in settings) in order for it's settings to persist?

I would like to choose the settings, then forget about it without the additional icon loading in the notification area.

It's not necessary - that's just a configuration program that saves the setting to your user configuration in the ~/.pulse/ folder. *However*, you need to understand that PulseAudio keeps a cache of the recently used sink per-application, and it ignores the "global" setting for these cached applications - this can be confusing.

A practical example to illustrate:

a) You have two sound cards and install Ubuntu. PulseAudio chooses card1 as its default sink, but you want card2 as the default.

b) You try to play an mp3 in Totem, and realize it's using card1, so you open the PulseAudio Volume Control and change the default sound card (sink) to card2.

c) You then try to play an mp3 in Totem once more, but it still uses card1.

d) You try to play the mp3 in Rhythmbox (which you haven't yet run since installing Ubuntu), and it uses card2, which is what you would expect.

This is because PulseAudio remembers the last-used sink per-application, and any saved applications will override the global sink you defined. Only applications that have never been run before will use the proper sink (in the example, Rhythmbox), and for the applications that have already been used, you will need to manually re-assign sinks in PA Volume Control's playback tab for each application that has been run in the past (in this example, Totem).

To overcome this silliness, simply delete your user configuration in ~/.pulse/, and immediately set the new default sink. This is one of the reasons why a guide may be important for users.

---

### Post by seeker5528 on 2009-05-11
> **psyke83 said:**
> 
This is because PulseAudio remembers the last-used sink per-application, and any saved applications will override the global sink you defined. Only applications that have never been run before will use the proper sink (in the example, Rhythmbox), and for the applications that have already been used, you will need to manually re-assign sinks in PA Volume Control's playback tab for each application that has been run in the past (in this example, Totem).

Is this because Pulse doesn't have a concept of a default card or is this a configuration thing?

Seperately, since asoundconf is gone now, is there some alternative that provides a similarly easy alsa way to set the default card or are we stuck manually creating/editing our own config files for this case? 

Later, Seeker

---

### Post by psyke83 on 2009-05-11
> **seeker5528 said:**
> Is this because Pulse doesn't have a concept of a default card or is this a configuration thing?

Seperately, since asoundconf is gone now, is there some alternative that provides a similarly easy alsa way to set the default card or are we stuck manually creating/editing our own config files for this case? 

Later, Seeker

It's a configuration thing. In PA Volume Control (pavucontrol), click the Output Devices tab. You'll see a list of sound cards there, and you can right-click on a device to set it as default. That's functionally equivalent to using "asoundconf set-default-card yoursoundcard" - in fact it should be simpler for a newcomer, since it can be done via a GUI.

The problem is that PulseAudio also remembers the last-used output device for each *application*, and will use the application's last-used output device - even if it's not the system default. It's not a bug per se, but a testament to the complexity of PulseAudio (and how it can confuse users who don't know precisely how these things operate).

We could fix this by patching PA in Ubuntu to "clear" the per-application cache each time the default output device is changed... but as it stands, we don't even ship the pavucontrol application in a default installation of Ubuntu yet.

---

### Post by crjackson on 2009-05-11
> **psyke83 said:**
> It's not necessary - that's just a configuration program that saves the setting to your user configuration in the ~/.pulse/ folder. *However*, you need to understand that PulseAudio keeps a cache of the recently used sink per-application, and it ignores the "global" setting for these cached applications - this can be confusing.

A practical example to illustrate:

a) You have two sound cards and install Ubuntu. PulseAudio chooses card1 as its default sink, but you want card2 as the default.

b) You try to play an mp3 in Totem, and realize it's using card1, so you open the PulseAudio Volume Control and change the default sound card (sink) to card2.

c) You then try to play an mp3 in Totem once more, but it still uses card1.

d) You try to play the mp3 in Rhythmbox (which you haven't yet run since installing Ubuntu), and it uses card2, which is what you would expect.

This is because PulseAudio remembers the last-used sink per-application, and any saved applications will override the global sink you defined. Only applications that have never been run before will use the proper sink (in the example, Rhythmbox), and for the applications that have already been used, you will need to manually re-assign sinks in PA Volume Control's playback tab for each application that has been run in the past (in this example, Totem).

To overcome this silliness, simply delete your user configuration in ~/.pulse/, and immediately set the new default sink. This is one of the reasons why a guide may be important for users.

Great, that clears it up a lot. In my case, since I only have one sound card, this shouldn't be an issue then. However, I will probably go ahead and delete the configuration and start from scratch to make sure it's all good. Thanks for the info...

---

### Post by seeker5528 on 2009-05-12
> **psyke83 said:**
> 
The problem is that PulseAudio also remembers the last-used output device for each *application*, and will use the application's last-used output device - even if it's not the system default. It's not a bug per se, but a testament to the complexity of PulseAudio (and how it can confuse users who don't know precisely how these things operate).

We could fix this by patching PA in Ubuntu to "clear" the per-application cache each time the default output device is changed... but as it stands, we don't even ship the pavucontrol application in a default installation of Ubuntu yet.

This sounds to me like a case of.... What PulseAudio is doing here is correct for what is implemented so far, but the implementation is incomplete.

Clearing the per-application cache seems like a reasonable short term solution, if there is no better way, but then you are trading one problem for a different problem. If this must be done it would probably be better to provide it as a clicky option somewhere or have a dialog that pops up when the default card is changed that gives a short explanation to the user and asks if they want to clear the per-application cache.

In the longer term PulseAudio should provide a default option to the applications so when you go into the application and set which card to use your options would be something along the lines of:

Default
card0
card1

: If default is selected in the application and you set a different card to be the default, you shouldn't have to change anything in the application, because default was selected and whatever the default happens to be at the time it should use automatically.

If the user has gone to the trouble to select a specific card to use, the assumption should be the user doesn't want that changed just because the default changed. It seems like it probably would still be desirable to provide the user an option to clear the per-application cache. 

Later, Seeker

---

### Post by bcschmerker on 2009-06-01
> **bcschmerker said:**
> I noticed that some settings in other packages may complicate the situation.  From my own experience, I have to recommend against setting any Accessible Sounds in the Login Window Preferences (/usr/sbin/gdm-setup), as GDM will then hog the sound resources, leaving both ESounD and PulseAudio unusable.

On my now [ECS-equipped](http://www.ecsusa.com/) Everex ([AMD Athlon X2](http://www.amd.com/) MPU, [nVIDIA nForce 405/GeForce6100](http://www.nvidia.com/)) running 8.04-LTS, I currently have Sound Preferences set as follows, in order to get the best of the PulseAudio installation (including PulseAudio-ESounD-Compat) on my system....The same is true for my Everex as re-equipped with a [Gigabyte MA78GM-S2HP](http://www.gigabyte.com.tw/) with the same AMD MPU as in the above quote, with the exception of the Default Mixer Tracks device (now with a Realtek ALC-889 in for the ALC-660VD):
```
[Devices]
*/Sound Events/*
Sound playback:  ESD - Enlightened Sound Daemon
*/Music and Movies/*
Sound playback:  ESD - Enlightened Sound Daemon
*/Audio Conferencing/*
Sound playback:  ESD - Enlightened Sound Daemon
Sound capture:  PulseAudio Sound Server
*/Default Mixer Tracks/*
Device:  HDA ATI SB (ALSA mixer)
```

---

### Post by aamukahvi on 2009-06-01
> **seeker5528 said:**
> Clearing the per-application cache seems like a reasonable short term solution, if there is no better way, but then you are trading one problem for a different problem. If this must be done it would probably be better to provide it as a clicky option somewhere or have a dialog that pops up when the default card is changed that gives a short explanation to the user and asks if they want to clear the per-application cache.

In the longer term PulseAudio should provide a default option to the applications so when you go into the application and set which card to use your options would be something along the lines of:

Default
card0
card1

: If default is selected in the application and you set a different card to be the default, you shouldn't have to change anything in the application, because default was selected and whatever the default happens to be at the time it should use automatically.

If the user has gone to the trouble to select a specific card to use, the assumption should be the user doesn't want that changed just because the default changed. It seems like it probably would still be desirable to provide the user an option to clear the per-application cache. 

Later, Seeker
The problem is really in the saving behavior. PulseAudio should never save the default sound card on a per-application basis unless it is explicitly set by the user.

This way you would always get output from the current default sound card (determined by PA or set by user) except for those apps that have been set to use something else.

---

### Post by psyke83 on 2009-06-01
> **aamukahvi said:**
> The problem is really in the saving behavior. PulseAudio should never save the default sound card on a per-application basis unless it is explicitly set by the user.

This way you would always get output from the current default sound card (determined by PA or set by user) except for those apps that have been set to use something else.

Has the behaviour changed with recent versions of PulseAudio, though? I haven't tested this behaviour with Karmic's version.

---

### Post by aamukahvi on 2009-06-01
> **psyke83 said:**
> Has the behaviour changed with recent versions of PulseAudio, though? I haven't tested this behaviour with Karmic's version.
I have no idea, just replying to Seeker's comment. :)

---

### Post by seeker5528 on 2009-06-01
> **aamukahvi said:**
> The problem is really in the saving behavior. PulseAudio should never save the default sound card on a per-application basis unless it is explicitly set by the user.

I can't really disagree with that too much, but hat's only a partial solution.

> This way you would always get output from the current default sound card (determined by PA or set by user) except for those apps that have been set to use something else.

If there is no concept of a default interface, as it's own separate construct, that points to the real interface that was chosen to be the default, it makes things unnecessarily complicated. 

If people have to actually physically go into the options of an individual application and choose the output device, they are less likely to do it.

If they have this big fancy mixer that shows all the active applications and the output they are using, and lets people drag the applications from one interface to another, much more likely to be used and just as much of an 'explicitly set by the user' option as choosing from within the program.

Either way, 'Default' should be one of the listed interfaces.

How many problems did ALSA solve by adding 'Defalt' as an option instead of having to choose a specific interface? I don't know either but things did seem to get more reliable.

Later, Seeker

---

### Post by psyke83 on 2009-06-01
> **seeker5528 said:**
> I can't really disagree with that too much, but hat's only a partial solution.



If there is no concept of a default interface, as it's own separate construct, that points to the real interface that was chosen to be the default, it makes things unnecessarily complicated. 

If people have to actually physically go into the options of an individual application and choose the output device, they are less likely to do it.

If they have this big fancy mixer that shows all the active applications and the output they are using, and lets people drag the applications from one interface to another, much more likely to be used and just as much of an 'explicitly set by the user' option as choosing from within the program.

Either way, 'Default' should be one of the listed interfaces.

How many problems did ALSA solve by adding 'Defalt' as an option instead of having to choose a specific interface? I don't know either but things did seem to get more reliable.

Later, Seeker

I think you misunderstand how it works. PulseAudio allows for a default playback device, and also allows you to change playback devices per-application (which is a very appealing feature). You modify these settings in pavucontrol, not within the actual applications.

The issue is that PulseAudio isn't too smart when distinguishing the default playback setting from the per-application settings (after an application is closed, it saves the last used device which can override the default setting the next time the application is run). It's a minor problem and can be easily fixed if either a) the per-application settings are cleared when a new default playback device is chosen, or b) the per-application settings do not save the last used playback device if it is not different from the current default.

The latter option makes the most sense.

---

### Post by seeker5528 on 2009-06-01
> **psyke83 said:**
> I think you misunderstand how it works. PulseAudio allows for a default playback device, and also allows you to change playback devices per-application (which is a very appealing feature). You modify these settings in pavucontrol, not within the actual applications.

I don't see anything in that description that leads me to believe I misunderstand how it works. Yeah, I'm not a developer, so I don't know all the nitty gritty details.

But from a logic perspective everything that has been said indicates, you can choose which physical card PulseAudio will use by default, but PulseAudio has no device independent concept of a 'Default' interface that it presents to the user when they chose which output (or input?) to use. 

> The issue is that PulseAudio isn't too smart when distinguishing the default playback setting from the per-application settings (after an application is closed, it saves the last used device which can override the default setting the next time the application is run).

If you have a concept of a default that is available on the application side of the equation, all applications can default to that unless the user selected to map it to a physical output. Then PulseAudio wouldn't have to be smart about how it detected the interface and saved the setting. You would have four cached output scenarios:

Cache doesn't exist, so is created and set as 'Default'.

Previously cached as 'Default' so continues to be used.

Previously cached as some specific physical interface so that continues to be used.
   

> It's a minor problem and can be easily fixed if either a) the per-application settings are cleared when a new default playback device is chosen, or b) the per-application settings do not save the last used playback device if it is not different from the current default.

The latter option makes the most sense.

Of those two options the latter makes more sense, but it is still lacking.

If I have one set of applications that I always want to use card1 and another I always want to use card2 and a third I always want to use the default device whatever that happens to be at the time.

Doesn't matter if PulseAudio has a card *it* recognizes as the default, if *you* can't choose 'Default' as an interface at the time you are selecting the output for the application to use (no matter how that selection is made), you can't get there from here.

Later, Seeker

---

### Post by psyke83 on 2009-06-01
> **seeker5528 said:**
> I don't see anything in that description that leads me to believe I misunderstand how it works. Yeah, I'm not a developer, so I don't know all the nitty gritty details.

It doesn't take a developer to understand, and I'm not one either.

> But from a logic perspective everything that has been said indicates, you can choose which physical card PulseAudio will use by default, but PulseAudio has no device independent concept of a 'Default' interface that it presents to the user when they chose which output (or input?) to use.

So for each application, you want these options: "card1", "card2" ... and "default"? At first that seems somewhat redundant to me, but perhaps it could make things work better.

The way I mentioned: patch PulseAudio so that per-application settings do not save the last-used device (unless the user manually changes it). However, you would need a "default" device in the case where you have manually changed the output device for an application, and wish for it to follow the defaults, yes.

---

### Post by seeker5528 on 2009-06-01
> **psyke83 said:**
> So for each application, you want these options: "card1", "card2" ... and "default"? At first that seems somewhat redundant to me, but perhaps it could make things work better.

Yes, it seems to me like the simplest way to cover the most diverse range of user use case scenarios.

Another hypothetical...

I set a few applications to use card1 and a few to card2, and the rest are defaulted to default.

When I'm using the applications specifically set to card1, I switch the default to card2, when I am using the applications specifically set to card2, I set the default to card1.

Later, Seeker

---

