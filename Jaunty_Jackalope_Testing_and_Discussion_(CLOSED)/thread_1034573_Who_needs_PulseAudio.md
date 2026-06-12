---
title: "Who needs PulseAudio?"
date: 2009-01-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vhaarr on 2009-01-08
I've been running Ubuntu with ALSA ever since I installed it a few years ago, and once PulseAudio was "forced" upon us a release or two ago, I simply uninstalled ubuntu-desktop and nuked all the pulse packages, and continued running with ALSA.

But now, things have changed.

Now, if I want to use the gnome volume controller, I must have PulseAudio installed for some reason. The volume applet still works, but opening the volume control window does not.

With the new one I can only adjust the master volume, not Microphone (I use both Ventrilo and TeamSpeak, and have to adjust my Mic regularly - every day, between apps) or any other individual controls, since I can't open the application. Clicking "Volume Control..." in the 'dropdown' or whatever you want to call it that you get upon clicking the applet does *nothing* (unless you install pulseaudio, of course).

1. I don't need pulseaudio - ALSA works fine, and it always has for me.
2. PulseAudio makes my sound lag. Not usually when I play something continously, but when I pause it and start again - like a movie or a tune, or anything - I get stuttering. This didn't happen with ALSA.
3. The new volume control requires two clicks to slide, not just click-and-drag to adjust, like the old, vertical one.
4. The new volume control uses a stop sign to indicate reducing the volume output, while the stop sign traditionally means a complete mute, and a minus would represent decreasing the volume.
5. The new volume control does not work if you have it positioned at the edge of your panel.
6. With the new control I scroll my mouse wheel UP to DECREASE the volume. Tell me how that makes sense.
7. This new "dropdown" from the applet does not disappear when you focus another window. Instead you have to click the applet again to close it. So there's *another* click I have to perform. So now we're up to 3 clicks to adjust the volume, compared to click+drag in the old applet.

Anyway, I'm sure points 3-7 will be fixed before Jaunty is released, so I'm not so concerned about those.

What concerns me most is item #1 and #2.

I was at loss to where I could vent my feelings about this, and figured I might as well write it up here. I know that countless other PulseAudio threads have popped up on the forums, for good and bad, and I am not making this thread to
 - Troll
 - Flame
 - Discuss
 - Offend
 - any other negative

I'm simply writing it to *inform*.

Hopefully one of the developers will read it and maybe devote an hour or two to the issue.

That is all.

---

### Post by gnomeuser on 2009-01-08
I have the built in soundcard and an external USB one. Pulseaudio lets me manage them both in context. Aside that I can set volume based on task and application so that background sounds are lower than playing music e.g. 

PulseAudio is great, I am very happy that we have it and looking forward to what it will bring us in the future.

---

### Post by autocrosser on 2009-01-08
> **vhaarr said:**
> 

1. I don't need pulseaudio - ALSA works fine, and it always has for me.
2. PulseAudio makes my sound lag. Not usually when I play something continously, but when I pause it and start again - like a movie or a tune, or anything - I get stuttering. This didn't happen with ALSA.

What concerns me most is item #1 and #2.


You say that you only use ALSA...not Pulse, yet you indicate that Pulse has the problems noted above...Is the experience from the time you last had used Pulse (and is that current?) or is the last time when you first found you did not like Pulse the most current time?

I found the problems you talk about during Gutsy testing & I no longer have them with the current system. Secondly, Pulse, like it or not, is the future & I have actively helped kill bugs that matter to me--not just uninstall the "offensive" part--Testing is all about improving the system--if you do not test, you can not tell if a improvement has helped or not.

The devs included Pulse as a way to make the system better---We in the testing group "should" do our bit & actively check/bug report/help with the development of this system.

---

### Post by Gina on 2009-01-09
When PA was first introduced there were several problems and the simple "fix" was to disable it and use ALSA.  But as time has gone on, most of the bugs have been fixed and PA is now quite usable.  I like the new volume control and think it's an improvement, albeit with a seemingly backwards acting volume control.  Few things are "right" when first introduced and we - the testing group - are here to find the bugs and undesirable "features" and report back.

---

### Post by danf_1979 on 2009-01-12
> **vhaarr said:**
> I've been running Ubuntu with ALSA ever since I installed it a few years ago, and once PulseAudio was "forced" upon us a release or two ago, I simply uninstalled ubuntu-desktop and nuked all the pulse packages, and continued running with ALSA.

But now, things have changed.

Now, if I want to use the gnome volume controller, I must have PulseAudio installed for some reason. The volume applet still works, but opening the volume control window does not.

With the new one I can only adjust the master volume, not Microphone (I use both Ventrilo and TeamSpeak, and have to adjust my Mic regularly - every day, between apps) or any other individual controls, since I can't open the application. Clicking "Volume Control..." in the 'dropdown' or whatever you want to call it that you get upon clicking the applet does *nothing* (unless you install pulseaudio, of course).

1. I don't need pulseaudio - ALSA works fine, and it always has for me.
2. PulseAudio makes my sound lag. Not usually when I play something continously, but when I pause it and start again - like a movie or a tune, or anything - I get stuttering. This didn't happen with ALSA.
3. The new volume control requires two clicks to slide, not just click-and-drag to adjust, like the old, vertical one.
4. The new volume control uses a stop sign to indicate reducing the volume output, while the stop sign traditionally means a complete mute, and a minus would represent decreasing the volume.
5. The new volume control does not work if you have it positioned at the edge of your panel.
6. With the new control I scroll my mouse wheel UP to DECREASE the volume. Tell me how that makes sense.
7. This new "dropdown" from the applet does not disappear when you focus another window. Instead you have to click the applet again to close it. So there's *another* click I have to perform. So now we're up to 3 clicks to adjust the volume, compared to click+drag in the old applet.

Anyway, I'm sure points 3-7 will be fixed before Jaunty is released, so I'm not so concerned about those.

What concerns me most is item #1 and #2.

I was at loss to where I could vent my feelings about this, and figured I might as well write it up here. I know that countless other PulseAudio threads have popped up on the forums, for good and bad, and I am not making this thread to
 - Troll
 - Flame
 - Discuss
 - Offend
 - any other negative

I'm simply writing it to *inform*.

Hopefully one of the developers will read it and maybe devote an hour or two to the issue.

That is all.

I completely sympathize with you, and found none of the answers given acceptable.

---

### Post by ShirishAg75 on 2009-01-12
For point 2 (the tip was given by somebody else) have found that changing the line in 

```
load-module module-hal-detect
``` which is in /etc/pulse/default.pa to 

```
load-module module-hal-detect tsched=0
``` 

improves the sound a lot specifically while playing movies. 

Apparently, the glitch-free audio does something for slower/elder (P3/P4 vintage) PC's. 

See if doing that gives any difference to your sound .

---

### Post by vhaarr on 2009-01-17
> **ShirishAg75 said:**
> For point 2 (the tip was given by somebody else) have found that changing the line in 

```
load-module module-hal-detect
``` which is in /etc/pulse/default.pa to 

```
load-module module-hal-detect tsched=0
``` 

improves the sound a lot specifically while playing movies. 

Apparently, the glitch-free audio does something for slower/elder (P3/P4 vintage) PC's. 


Thanks, that seems to have fixed the glitches!

But I'm not on an older system, I have a Intel Core 2 Duo 8500.

---

### Post by Pettman on 2009-01-18
> **danf_1979 said:**
> I completely sympathize with you, and found none of the answers given acceptable.
I'll second that.

PulseAudio does not provide any functionality I want, also it has a tendency to conflict with the JACK audio server that provide functionality that I DO want (occasionally). Adding a piece of software that runs automatically and does not, in my opinion, provide any useful features is a pointless way to increase the amount of code that can contain bugs and thereby cause malfunctions.
I don't think pulseaudio is evil or such but I think it's a bad idea to have it installed and run by default (I know that for some people there is a need for something to replace the nowadays defunct ESD), making it easy to install would in my opinion be a better option.

---

### Post by Slug71 on 2009-01-18
I do agree that Pulseaudio has been a pain in the butt but another thing to consider is that it is still very new too.

Heres a quote from L.P

> Linux distributions such as Ubuntu 8.04 and Fedora 8 introduced PulseAudio as the default audio system arguably before it was ready: PulseAudio developer Lennart Poettering described it as "the software that currently breaks your audio" [2]. He later claimed that "Ubuntu didn't exactly do a stellar job---they didn't do their homework" in adopting PulseAudio.[3]

---

### Post by Glowing Fish on 2009-01-19
> **ShirishAg75 said:**
> 

Apparently, the glitch-free audio does something for slower/elder (P3/P4 vintage) PC's. 

See if doing that gives any difference to your sound .

I don't consider P3 to be that old, especially considering that many Linux users are people who are not wealthy enough, or don't wish to participate in, the constant upgrade cycles of consumerism that sometimes accompany computer use. And there is nothing more modern than P4, as far as I know!

---

### Post by blazemore on 2009-01-19
I always just use ALSA. Pulse is just pointless, it's riduculous and doesn't even let me listen to two things at the same time (Flash and exaile, say)

---

### Post by taavikko on 2009-01-19
> **blazemore said:**
> I always just use ALSA. Pulse is just pointless, it's riduculous and doesn't even let me listen to two things at the same time (Flash and exaile, say)

Then it's poorly configured.
the dev is going towards that minimal or none configuration should be made.

Just installed intrepid to my semi-girlfriends laptop, and pulse just worked o-t-b 
flash+movie(smplayer)+mp3(rhythmbox)
All of them simultaneosly

The big pro with pulse is that it can be used as server, 
example, I play movie with my mininotebook, and audio is played by main comp
through decent speakers.
Alsa can't provide that.

best thing in linux is freedom of choice, there are several programs to do one job, you can choose the one that suites your needs.

---

### Post by uBeer on 2009-01-19
"semi-girlfriends"?? Please elaborate... :D

Yeah, the server thing is great, I use it to play music from my laptop through my desktop on my stereo, really great! And I'm probably gonna use it in the rest of my house as well (student house) from the kitchen to play music in the showers through the server pc :popcorn:

But configuring Pulseaudio until now has been a mess, at least for me. I never know what I'm doing, but hopefully the new user interface will clear things up for me!

---

### Post by blazemore on 2009-01-19
Is that "semi-girl" friend, or semi "girlfriend"

---

### Post by taavikko on 2009-01-19
Seriously offtopic->

> **uBeer said:**
> "semi-girlfriends"?? Please elaborate... :D

You all know the sound that women makes, goes something like this:
nag nag nag nag nag...
Why do you have to be on the computer so much, I wanna do something together..
Yeah yeah, as soon as i'm finished compiling this great new software,

Either stop nagging or come compile with me :grin:
That usually ends in "me throwing her out of my house"

"Is that "semi-girl" friend, or semi "girlfriend""

C'mon guys, that would be best of both worlds... :lolflag:

---

### Post by uBeer on 2009-01-19
> **taavikko said:**
> Seriously offtopic->

Either stop nagging or come compile with me :grin:


Haha, that would be awesome :D
My girlfriend thinks that I boot and compile Kermit (the frog) instead of kernels...

Kinda on topic: alsa 1.0.19 has been released! My USB UA-25EX will now work in advanced mode as well! Nice... Time to get to know Ardour!
Anyone knows if 1.0.19 will be included in Jaunty?

---

### Post by Slug71 on 2009-01-19
> **taavikko said:**
> Seriously offtopic->

You all know the sound that women makes, goes something like this:
nag nag nag nag nag...
Why do you have to be on the computer so much, I wanna do something together..
Yeah yeah, as soon as i'm finished compiling this great new software,


You're not dating my wife are you? :lolflag:


Was wondering if there was gonna be a new Alsa version out anytime soon because there was nothing under 'Development Versions' since v1.0.18.
Seems there are a lot of changes.

Hopefully we get v1.0.19 and PA 0.9.14 soon. :)

---

### Post by Pettman on 2009-01-19
> **taavikko said:**
> The big pro with pulse is that it can be used as server, 
example, I play movie with my mininotebook, and audio is played by main comp
through decent speakers.
Alsa can't provide that.Some people don't need or even want that feature and, as I pointed out earlier, adding additional (and to some people unnecessary) software increase the probability of something malfunctioning. Giving an easy option to install PA would in my oppinion be a better option than having it installed by default and letting everyone who doesn't want it figure out how to get rid of it on their own.

---

### Post by ssam on 2009-01-19
PA can adjust the audio buffer size, so you dont have to compromise between powerusage or latency.

PA fine for me. i believe that it can trigger bugs in the audio drivers that usually go unnoticed, by using more advanced features. I assume that you have filled bugs.

---

### Post by jerrylamos on 2009-01-19
> **taavikko said:**
> Seriously offtopic->



You all know the sound that women makes, goes something like this:
nag nag nag nag nag...
Why do you have to be on the computer so much, I wanna do something together..
Yeah yeah, as soon as i'm finished compiling this great new software,

Either stop nagging or come compile with me :grin:
That usually ends in "me throwing her out of my house"

"Is that "semi-girl" friend, or semi "girlfriend""

C'mon guys, that would be best of both worlds... :lolflag:

Not here!  My wife is on the computers as much as I am.  She does some work on websites and I futz around with new broken Ubuntu's, and we both do a lot of internet news and videos.  She uses 3 computers, I use 4.

Cheers, Jerry

---

### Post by jocko on 2009-01-19
> **Pettman said:**
> Some people don't need or even want that feature and, as I pointed out earlier, adding additional (and to some people unnecessary) software increase the probability of something malfunctioning. Giving an easy option to install PA would in my oppinion be a better option than having it installed by default and letting everyone who doesn't want it figure out how to get rid of it on their own.

Why is it so wrong to have pulseaudio installed by default? Because it adds extra features?
Compared to what was installed by default before pulseaudio (esound/esd), what's the difference (feature-wise and quality-wise)?
esd was fully capable of streaming sound to a network computer, just with a lot worse quality than pulseaudio and the only way to configure it was through editing text files, compared to pulseaudio that you can configure through a gui application. So pulseaudio does not add a feature that was not installed by default before, it just advertises it a little bit better by having a gui for configuring it... If you don't want to use it, just don't configure it. Exactly like you probably did with esd before pulseaudio (don't tell me that you did not use esd, as it was not possible to uninstall it without breaking gnome).

Which more feature of pulseaudio do you not want?

Before pulseaudio, with a *properly* configured alsa dmix plugin and *proper* configuration of all applications, alsa did most of the software sound mixing, but much was also done (poorly) in esd.
So audio streams were passed like this:
Application --> alsa (dmix plugin) --> Alsa (hardware)
Or:
Application --> esd --> alsa (dmix plugin) --> Alsa (hardware)

Now, with pulseaudio (if both pulseaudio and alsa are *properly* configured, which may not always be the case), ALL sounds should go this way:
Application --> Pulseaudio --> Alsa (hardware)
A few applications that does not support pulseaudio can instead go like this:
Application --> Alsa (pulseaudio plugin) --> Pulseaudio --> Alsa (hardware).

As I see it pulseaudio is better than what we had before: First of all it replaces all functions that esd had, just does the same things with better quality and is easier to configure. Secondly it takes the software mixing from alsa, and again does this with better quality and more configuration options (or at least a h*ll of a lot easier to access the configuration than before, when the only way to do most things was by editing ~/.asoundrc or /etc/asound.conf).

---

### Post by scaine on 2009-01-19
> **Pettman said:**
> Some people don't need or even want that feature and, as I pointed out earlier, adding additional (and to some people unnecessary) software increase the probability of something malfunctioning. Giving an easy option to install PA would in my oppinion be a better option than having it installed by default and letting everyone who doesn't want it figure out how to get rid of it on their own.

Well, if you don't need it, you don't use it.  I'm not sure why you wouldn't "want" a feature though.  You might use it someday, and let's face it, if PA worked perfectly for you, you wouldn't be complaining about extra functionality then...

I've been lucky, I guess - 4 separate PCs running from 7.10 through to 8.10 and I haven't hit a single PA glitch yet.  For the record, my installs have been on an EEE 701, a Toshiba U-400, a MacMini and a home-built system with a Creative Labs card - can't mind which one.

It's disappointing to hear so many people complain about PA, but I seem to remember similar noises about Compiz-Fusion when it was first introduced.  These days, it just mostly works, and if it doesn't, it's easily turned off.  These things take time.

EDIT : My 200th post!  I'm so proud!  :)

---

### Post by chrisccoulson on 2009-01-19
> **Pettman said:**
> Some people don't need or even want that feature and, as I pointed out earlier, adding additional (and to some people unnecessary) software increase the probability of something malfunctioning. Giving an easy option to install PA would in my oppinion be a better option than having it installed by default and letting everyone who doesn't want it figure out how to get rid of it on their own.

[RANT ON]
Well, hey, I find Ekiga, Firefox, Evolution, Openoffice, Pidgin, GDM, seahorse, gcalctool, brasero, F-spot and all the games unnecessary and they increase the probability of the system malfunctioning, so I don't think they should be shipped with the default install and users should have to install them themselves.

Even better, lets make users download a blank ISO, and they can then add only the bits they need[/RANT OFF]

---

### Post by BwackNinja on 2009-01-19
The thing is this...

PulseAudio provides nice features that the we didn't have before and basically imposes a path where all compatible applications will always be able to mix and be happy. What is unfortunate about this is when you are _not_ using the extra features that pulseaudio provides, then all you've got is increased overhead to do the same thing. Without "pulse", you still have "audio".

Previously, it was made in such a way that you could change away from pulseaudio painlessly and just use alsa or even oss. Now, the transition isn't so painless, the default volume control is tied directly to pulseaudio and lower level volume manipulation is restricted to either the command line or requires the installation of additional software.

Also, despite the GUIs available for pulseaudio manipulation, it is still missing a method for changing the number of channels within a gui, though alsa has this in the old volume control. Is it really so right and the way forward to be forcing users to find a tutorial to find out how to change a text file to simply enjoy anything more than stereo sound? I've read about this and have seen the problems in implementation, but I'd argue that at least a hackish implementation should be included with a big bold warning in red letters saying that it'll restart the sound server and all applications currently playing audio might crash.

There has been major headway regardless because of the new gnome-volume-control. Now the default install will actually be able to _benefit_ from pulseaudio, rather than it just causing problems. I'd say that beyond curiosity, the only reason why anyone would know pulseaudio's existence in hardy would be that it was just like using alsa directly, only it broke more. And took more cpu. The difference in intrepid is that it broke less than before, worked really well by default actually.

Despite that the release of Jaunty will mark 1 year of pulseaudio's inclusion in ubuntu by default, I wouldn't say that pulseaudio is 'ready', I'd say 'ready for the majority of users'.

Scaine's comparison to compiz-fusion probably says the most. People either like pulseaudio and think its fun and useful, or just find it to be slower, full of a bunch of stuff they'll never need, and prevents some apps from working properly.

> **chrisccoulson said:**
> [RANT ON]
Well, hey, I find Ekiga, Firefox, Evolution, Openoffice, Pidgin, GDM, seahorse, gcalctool, brasero, F-spot and all the games unnecessary and they increase the probability of the system malfunctioning, so I don't think they should be shipped with the default install and users should have to install them themselves.

Even better, lets make users download a blank ISO, and they can then add only the bits they need[/RANT OFF]

Welcome to the world of arch linux. The only down side is that you can't really brag about how the default install looks ;P.

PS: Before anyone tries to say that I'm doing any bashing, I always use pulseaudio and have been messing with it since one of the later hardy alphas.

---

### Post by inportb on 2009-01-20
Hm... I certainly don't need PulseAudio; Phonon works just fine for me ;)

---

### Post by RAOF on 2009-01-20
> **inportb said:**
> Hm... I certainly don't need PulseAudio; Phonon works just fine for me ;)

I'm moderately certain that the only overlap between Phonon and PulseAudio is that they are both related to audio in some way.  Pulseaudio is a sound server, Phonon is an abstraction over media playback frameworks.

Phonon takes your mp3 files and converts them into a stream of PCM data to pipe to a sound device; Pulseaudio *is* a sound device which takes a stream of PCM data, does funky things with it, and pushes it out through ALSA to the hardware.

---

### Post by plun on 2009-01-20
> **chrisccoulson said:**
> [RANT ON]
Well, hey, I find Ekiga, Firefox, Evolution, Openoffice, Pidgin, GDM, seahorse, gcalctool, brasero, F-spot and all the games unnecessary and they increase the probability of the system malfunctioning, so I don't think they should be shipped with the default install and users should have to install them themselves.

Even better, lets make users download a blank ISO, and they can then add only the bits they need[/RANT OFF]

Well... "Big Rant"

The challenge now for a newbie is to get the sound to work and then also fix all codecs. 

Jaunty seems to end up in the same mess as Intrepid and Hardy...

PA 9.0.14 is built but not published  :confused:

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/003425.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/003425.html)

In the end, the mess remains for a newbie about codecs.

---

### Post by ShirishAg75 on 2009-01-20
plun, 
 are you sure, it shows 0.9.14 as been released/published. Its the earlier version which shows as unpublished (not 0.9.14)

[https://launchpad.net/ubuntu/+source/pulseaudio](https://launchpad.net/ubuntu/+source/pulseaudio)

---

### Post by Slug71 on 2009-01-20
Just got PA updates and i now have 0.9.14 installed. :)
Now just need Alsa v1.0.19.

---

### Post by plun on 2009-01-20
> **ShirishAg75 said:**
> plun, 
 are you sure, it shows 0.9.14 as been released/published. Its the earlier version which shows as unpublished (not 0.9.14)

[https://launchpad.net/ubuntu/+source/pulseaudio](https://launchpad.net/ubuntu/+source/pulseaudio)

Yup...  It was built yesterday and then put in queue for unknown reasons. (you can check build logs) 

My analog output went crazy but my USB sound output works great... 

Running a very special PC for the moment...ordered a new MB and processor  ;)

---

### Post by inportb on 2009-01-21
> **RAOF said:**
> I'm moderately certain that the only overlap between Phonon and PulseAudio is that they are both related to audio in some way.  Pulseaudio is a sound server, Phonon is an abstraction over media playback frameworks.

Phonon takes your mp3 files and converts them into a stream of PCM data to pipe to a sound device; Pulseaudio *is* a sound device which takes a stream of PCM data, does funky things with it, and pushes it out through ALSA to the hardware.

Makes sense. Phonon's also supposed to replace aRts, which is KDE's old sound server, so I'm guessing there're some server-like qualities in Phonon as well (i.e. software mixing). Anyhow, my Phonon setup uses ALSA directly instead of PulseAudio.

---

### Post by dprestemon on 2009-01-22
Well, for me, PulseAudio has been a disaster.  After two years using Ubuntu exclusively, I am forced, unhappily, back to Windows XP because I have no usable audio.  I can't listen to music.  I can't listen to my favorite radio stations.  Hell, I can't even get through the log-on theme before the stuttering starts. 

I have an 8-month old system with dual core AMD processor, 2 gb RAM and built-in Azalia HD audio.  I have tried every fix/tweak/adjustment I could find on this forum with no luck.  I even turned off the built-in audio and tried an old SoundBlaster Live card.  It made no difference whatsoever.  Essentially, my computer running Ubuntu with PulseAudio is an expensive paperweight.

---

### Post by inportb on 2009-01-22
You should remove PA, then.

---

### Post by platykurtic on 2009-01-23
Pulse audio has been nothing but misery. Since intrepid my audio has had a habit of cutting out randomly; usually when I've left totem or a flash movie window open in firefox for a while, but not reliably. I upgraded to jaunty early in hopes of fixing this, but nothing changed. This is really pathetic for ubuntu, I can't recommend it to friends if it's going to be doing **** like this. There's undoubtebly some configuration to fix this that I can find on the forums, but I shouldn't have to for something as simple as sound working when I haven't changed anything

---

### Post by bash on 2009-01-23
I have to say I have had no problems with PulseAudio so far. Finally the old cruft of ESD is gone and Pulse actually offered me the chance to do things that were not at all possible with the old way (or only through lots of tweaks). I can now easily with no extra setup listen to multiple audio-streams at the same time, including things like Flash/Banshee/Skype. Further it finally enabled me to have proper microphone and headset hot-plugging on my Laptop. So I quite like PulseAudio and find it brings many benefits. So I also am quite happy about the new volume control/gnome-sound-prefs that is going to land in GNOME 2.26 and will offer simple and clean options and a chance to do per-application volume control in a sane gui.

---

### Post by Pettman on 2009-01-25
> **chrisccoulson said:**
> [RANT ON]
Well, hey, I find Ekiga, Firefox, Evolution, Openoffice, Pidgin, GDM, seahorse, gcalctool, brasero, F-spot and all the games unnecessary and they increase the probability of the system malfunctioning, so I don't think they should be shipped with the default install and users should have to install them themselves.

Even better, lets make users download a blank ISO, and they can then add only the bits they need[/RANT OFF]

With the exception of GDM and seahorse non of those programs are automatically run by default and neither seahorse nor GDM hogs hardware resources like PA does so you comparison is, in my opinion, lacking relevance.

> **jocko said:**
> Why is it so wrong to have pulseaudio installed by default? Because it adds extra features?The thing that is wrong with having PA installed by default is that it breaks things. Since they started shipping ubuntu with PA it got a lot trickier to use JACK, the audio in wine usually get distorted if PA is running, and PA makes it a lot more cumbersome to access the mixer controls for the different audio outputs which makes it hard to set up the audio output on my laptop properly. I wouldn't mind having PA just taking a few MB on my hard-drive as long as it does not conflict software that I do want to run, but it does and therefore I think it is bad to have it installed and run automatically by default. In hardy it was not so bad as removing it was pretty straight forward (just remove the packages) but in intrepid the Xserver won't start if you remove it (or you can get rid of it but then you have to do a bit of hacking).

---

### Post by Bios Element on 2009-01-25
PA works for me. That's all I honestly care about. Flame me all you want, But just because your system has a hard time installing it, Doesn't mean that everyone else does. Sure there are bugs, Thus why we have the forums. But just because you have problems doesn't mean the system is worthless.

---

### Post by Gina on 2009-01-25
My sound works fine though the volume was a bit low until I installed gnome-alsa-mixer and turned up some controls that weren't otherwise available.  I presume it's using PA if that's the default - I just did a fresh install of a recent daily build on my AMD64 with ext4 and apart from installing g a-m I did nothing other than use the tools provided to get perfect sound.  The other machines running Jaunty are updated daily and are fine too.  (Laptop and K6-2)

---

### Post by Yellow Pasque on 2009-01-25
Even if PulseAudio works perfectly (big IF), it still consumes resources (CPU cycles, RAM) and adds latency to playback. Also, some of us don't even use ALSA. I use OSS4 because it doesn't skip and it just sounds better for my card.

> You should remove PA, then.
That's a great idea, and it's one of the first things I did with my Jaunty, but then I can't use GNOME's volume control and access all of the sound preferences.

The real question is: Why does the GNOME 2.25 volume control depend explicitly on PulseAudio? It should depend on gstreamer, so that any gstreamer backend can be used. Pulse and ALSA are Linux-only and non-portable. Is GNOME purposely restricting itself to a Linux-only desktop environment?

I've commented on GNOME's bugzilla: [http://bugzilla.gnome.org/show_bug.cgi?id=566835](http://bugzilla.gnome.org/show_bug.cgi?id=566835)

> Pulse, like it or not, is the future
Not for me (and a lot of other users).

---

### Post by Yellow Pasque on 2009-01-25
BTW, for anyone else having trouble with the volume control that can't access their sound preferences:
```
gstreamer-properties
```

I still haven't figured out the terminal command for event sound preferences (mainly because I don't use system/event sounds and haven't put effort into it.)

---

### Post by RAOF on 2009-01-25
> **Temüjin said:**
> ...
The real question is: Why does the GNOME 2.25 volume control depend explicitly on PulseAudio? It should depend on gstreamer, so that any gstreamer backend can be used. Pulse and ALSA are Linux-only and non-portable. Is GNOME purposely restricting itself to a Linux-only desktop environment?
...

Because GStreamer doesn't do the same thing as pulseaudio.  There are useful things for a volume control that pulseaudio does that GStreamer doesn't - setting a system-wide volume, and migrating your audio when you plug in your USB headset, for example.

That said, I'd expect the gnome-volume-applet to regrow a gstreamer-backed mode; this is the most sensible result.  Pulseaudio when available, GStreamer otherwise.

Finally, pulseaudio is certainly not Linux-only; it's not even POSIX only.  It runs on Windows and OS X and Solaris and...

---

### Post by jocko on 2009-01-25
> **Temüjin said:**
> Pulse and ALSA are Linux-only and non-portable. Is GNOME purposely restricting itself to a Linux-only desktop environment?

Yes, alsa is for linux, but you are wrong about pulseaudio, from [http://www.pulseaudio.org/:](http://www.pulseaudio.org/:)
> PulseAudio has been tested on Linux, Solaris, FreeBSD, NetBSD, Windows 2000 and Windows XP. It should also run on all other POSIX and Windows systems, but may require new backends to handle their sound systems.Perhaps it's not used that much outside linux (yet?), but it's not limited to linux only as you claim. Gstreamer? Why? It doesn't do what pulseaudio does, and only a limited subset of applications use gstreamer. I've always found the sound quality in gstreamer applications poor and choppy, with no configuration options whatsoever. Ever tried to do something as simple as playing a video with dolby digital surround sound in totem and get proper passtrough via spdif to a surround reciever? Even if it's an option in the settings in totem, I've never got it to work, while it's very simple to get to work in vlc, mplayer and other apps that are not tied to gstreamer. 

Pulseaudio is at least the closest there is to something that can replace the silly mess with alsa software mixer plugins and esd and whatever else crap you had to mix in to get decent sound from more than one source at the time. It's not perfect (yet), but for most of us it's easier AND better quality than the options, so it should definitely be default (but I agree that it should be possible to use any backend for the sound in gnome, for people that want other setups or are just generally against pulseaudio).

Some of the things people are complaining about with pulseaudio are not directly problems with pulseaudio but with misconfigured alsa and pulseaudio. Sometimes the misconfiguration is because people keep trying to set up alsa as before, causing conflicts between the alsa software mixer plugin (or other plugins) and pulseaudio. In other cases it's because the default configuration in ubuntu could be better.
It's of course bad that pulseaudio and oss4 doesn't work together, and it's even worse that the pulseaudio and oss4 developers just blame each other for the incompatibility instead of trying to solve the problem...

---

### Post by Yellow Pasque on 2009-01-25
Noted about other OS's, but I thought a lot of other UNIX/BSD OS's were using OSS/4 since UNIX vendors (I know at least Sun) contracted the devs to support it. I wonder if P.A. works better with OSS4 on non-Linux OS's.

> Pulseaudio is at least the closest there is to something that can replace the silly mess with alsa software mixer plugins and esd and whatever else crap you had to mix in to get decent sound from more than one source at the time
OSS4's vmix works nicely.. ;P

---

### Post by RAOF on 2009-01-25
> **Temüjin said:**
> ...

OSS4's vmix works nicely.. ;P

But, apparently, is a severely limited design, at least on linux.  Should anything want floating-point audio samples - either audio clients or soundcards (and apparently floating-point-preferring or floating-point only soundcards are coming), the mixing-in-kernelspace design has problems, since kernel code needs crazy hax to do floating-point.

---

### Post by amano on 2009-01-25
> **RAOF said:**
> 
That said, I'd expect the gnome-volume-applet to regrow a gstreamer-backed mode; this is the most sensible result

BTW, what is that applet, that hit Jaunty? According to the gnome-media release manager it is NOT the new pulseaudio enabled volume applet:

[http://www.hadess.net/2009/01/nb-it-doesnt-actually-look-like-that.html](http://www.hadess.net/2009/01/nb-it-doesnt-actually-look-like-that.html)

> Ubuntu's mixer applet is a different UI on the old mixer applet in gnome-applets, and not the PulseAudio-powered volume applet now in gnome-media.

In addition to the article being outdated (the treeview with the one-by-one sound event customisation is already gone), it also invents new features such as «the ability to adjust the alert volume on a per-alert basis». God knows where they got that from.

/The guy who did the last gnome-media release

Doesn't Ubuntu want a PulseAudio powered applet?

---

### Post by RAOF on 2009-01-25
That applet is pulseaudio powered, I believe.

The reason we might want it rather than the upstream applet is that the upstream applet provides only a notification icon, which is only shown when something is playing audio.  I, personally, find this an inexplicable UI design choice.  We *do* have this applet in Ubuntu, it's just not shown while the actual panel applet is active.

---

### Post by amano on 2009-01-26
Hmm. Maybe that should be coordinated with Bastien Nocera. Rather have it fixed upstream to be shown permanently than creating another delta to upstream (it should be possible to show something even if nothing is playing audio, see Pidgin which has a connected and disconnected state).

And please check if the old applet uses PulseAudio or not (I am not sure what Bastien hints at in his blog post).

---

### Post by bash on 2009-01-27
> **RAOF said:**
> That applet is pulseaudio powered, I believe.

The reason we might want it rather than the upstream applet is that the upstream applet provides only a notification icon, which is only shown when something is playing audio.  I, personally, find this an inexplicable UI design choice.  We *do* have this applet in Ubuntu, it's just not shown while the actual panel applet is active.

RAOF do you know more about this:

[quote=GNOME 2.25.2 Release notes]========================================
 NEWS: gnome-media-2.25.5
========================================

Version 2.25.5
===============
- Fix the volume applet not showing up in some cases[/quote]

Maybe it was just a bug that the upstream volume didn't appear all the time. At least that is what the release notes suggest. Sadly compile a whole new GNOME point-release is way over my head, so I can't check myself if the upstream volume slider is now persistant.

---

### Post by chrisccoulson on 2009-01-27
> **bash said:**
> RAOF do you know more about this:

 Originally Posted by GNOME 2.25.2 Release notes
========================================
NEWS: gnome-media-2.25.5
========================================

Version 2.25.5
===============
- Fix the volume applet not showing up in some cases

Maybe it was just a bug that the upstream volume didn't appear all the time. At least that is what the release notes suggest. Sadly compile a whole new GNOME point-release is way over my head, so I can't check myself if the upstream volume slider is now persistant.

I believe that was [http://bugzilla.gnome.org/show_bug.cgi?id=568320]("http://bugzilla.gnome.org/show_bug.cgi?id=568320"). It didn't work though because the volume applet also has a race with Pulseaudio at the moment (which is in the Gnome Bugzilla somewhere). If PA starts before the applet, the status icon doesn't get refreshed and the applet doesn't work

---

### Post by chrisccoulson on 2009-01-27
The applet race with Pulseaudio is this bug: [http://bugzilla.gnome.org/show_bug.cgi?id=564311]("http://bugzilla.gnome.org/show_bug.cgi?id=564311")

---

### Post by plun on 2009-02-05
Testing PA 9.015....;)

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003068.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003068.html)


[[img]http://ubuntu-pics.de/thumb/9374/snapshot8_73sFyn.png[/img]](http://ubuntu-pics.de/bild/9374/snapshot8_73sFyn.png)


Also Alsa 1.0.19.... Just great !8)

---

### Post by olskar on 2009-02-05
> **plun said:**
> Testing PA 9.015....;)

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003068.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003068.html)


[[img]http://ubuntu-pics.de/thumb/9374/snapshot8_73sFyn.png[/img]](http://ubuntu-pics.de/bild/9374/snapshot8_73sFyn.png)


Also Alsa 1.0.19.... Just great !8)

Still impossible to use skype with pulseaudio :(

---

### Post by Bios Element on 2009-02-05
> **olskar said:**
> Still impossible to use skype with pulseaudio :(

And Skype is at fault for that. Not The Dev's fault that Skype never updates their "Linux" Client. Lazy buggers...

---

### Post by plun on 2009-02-05
> **olskar said:**
> Still impossible to use skype with pulseaudio :(

I am not using Skype but I checked psyke83's master howto

> **Skype:** Open Skype's Options, then go to Sound Devices. You need to set "Sound Out" and "Ringing" to the "pulse" device, and set "Sound In" to the hardware definition of your microphone. For example, my laptop's microphone is defined as "plughw:I82801DBICH4,0".  

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Probably works as mostly all after some "nerd-level" tricks...;)

---

### Post by olskar on 2009-02-05
> **Bios Element said:**
> And Skype is at fault for that. Not The Dev's fault that Skype never updates their "Linux" Client. Lazy buggers...

Yeah, It is because skype still only supports alsa or something, right? 

Still pulseaudio makes every sound on my computer scratchy until I use killall pulseaudio. Can't blame that at Skype at least ;)

---

### Post by markbuntu on 2009-02-05
I like pulseaudio. I cannot imagine how I would use all my sound hardware and applications without it. Unfortunately, Ubuntu us still doing a less than stellar job of implementing pulse, nevermind the nightmare with Hardy.

All the complaints about pulseaudio and wine and skype and audacity etc should be directed to those devs, they are the ones writing bad code, making faulty assumptions about harware that applications should not be doing in any case. The wine devs even fessed up to it. Thanks to pulseaudio all this bad code is being exposed and fixed now instead of later.

Another complaint I hear all the time is that pulseaudio increases latency. This is simply not true. Pulseaudio has lower latency than dmix or esd when remixing and if it is not remixing has zero latency.

There is a module pulse-jack that is available from the debian repos but not from the ubuntu repos. There is even a version for pulse 0.9.14. This makes no sense to me. Jack is in the repos, pulseaudio is in the repos, why not the module that connects them? 

Or even the jack alsa modules left out of libasound2? 
What's up with that?

Some people's bad feelings about pulseaudio are now deeply rooted due to a faulty implementation of something that was not quite ready. The biggest mistake was no pulseaudio volume control in the desktop seed and default sound settings guaranteed to cause trouble. That was just stupid and for some it was just too much. You really can't blame them. It took me a good month to figure it all out.

---

### Post by deepclutch on 2009-03-05
and what do you mean by ALSA works?Isn't it esd which is actually working earlier?
--
Is there anyway ,by which I can have latest pulseaudio(.9.14) build available for my Intrepid?I have seen few ppa repos.but the package for Intrepid is lacking

---

### Post by BGFG on 2009-03-07
on my 64 bit system PA works perfectly. I just now ran Exaile, Some flash video on youtube, A video in smplayer and A song in Alsaplayer. All simultaneously. All soung audible. Since my intrepid install I've done nothing to pulse and it just works.

So i say keep it and improve it.

---

### Post by jocheem67 on 2009-03-07
Well....removing pulse and restoring esound/alsa gave me back my hercules RMX, configured through 'system-preferences-sound' and 'asoundconf set-default-card'

> sudo killall pulseaudio

sudo apt-get remove pulseaudio

sudo apt-get install esound

sudo mv /etc/X11/Xsession.d/70pulseaudio /etc/X11/Xsession.d/70pulseaudio.org

This basically gave me a working "just alsa" configuration.....
Jack is also easily configured now ( for using Mixxx and Audacity )

Bottomline:

even if and when PA may be the way to go, I do feel that these steps are too complicated to get back to a working configuration _whenever PA is the cause of problems_

Pfffff.....these aren't even all the necessary commands, and for me a rather experienced user, it took time to figure this all out.
The whole PA discussion has already cost ubuntu new users....it's just too complicated.

---

### Post by 3rdalbum on 2009-03-07
Anyone play Blu-ray discs on their Linux computers? If you do, you'll know that the audio on BDs tends to be a very low volume. I have to turn my speakers up to over 3/4 in order to get a good volume out of them, and that's with increasing Mplayer's volume control to full.

But if I want to run Pidgin at the same time, every time someone sends me a message, logs on or leaves, I get blasted out of my seat by an incredibly loud alert sound. Well, it's only loud because I've got the volume turned up for the blu-ray! With Pulseaudio, I can just turn down Pidgin's individual volume control. I can do that today with Ubuntu Intrepid.

When Pulse becomes mature and well-integrated with the Ubuntu desktop, everything will be great. It's actually looking like Pulseaudio will be "one sound server to rule them all".

---

### Post by k@e on 2009-03-07
Unless Pulseaudio does work flawlessly with Wine, no crackling sound that is, I will uninstall it everytime I do a fresh install of Ubuntu. And no, padsp + OSS driver or pasuspender is not an option. I don't care whose fault it is, I'll blame both sides equally.

I praise those developers who spend their time on writing a Pulseaudio driver for Wine.

---

### Post by Bios Element on 2009-03-07
> **k@e said:**
> Unless Pulseaudio does work flawlessly with Wine, no crackling sound that is, I will uninstall it everytime I do a fresh install of Ubuntu. And no, padsp + OSS driver or pasuspender is not an option. I don't care whose fault it is, I'll blame both sides equally.

I praise those developers who spend their time on writing a Pulseaudio driver for Wine.

It does most of the time. And last I looked, Wine isn't installed by default...

---

### Post by jocheem67 on 2009-03-07
But it's used quite a lot.

Pulse should just be simpler to set up, but I guess in time it will be.

For now, more dis...than advantages....
A personal view where others would disagree, but that's the point :

when talking ubuntu, we shouldn't be forced into editing config-files anymore...or at least less and less..

---

### Post by markbuntu on 2009-03-07
The problem with wine and pulseuaudio is due to wine, not pulseaudio. The wine devs have fessed up to this and are trying to fix it.

---

### Post by psychok9 on 2009-03-07
> **ShirishAg75 said:**
> For point 2 (the tip was given by somebody else) have found that changing the line in 

```
load-module module-hal-detect
``` which is in /etc/pulse/default.pa to 

```
load-module module-hal-detect tsched=0
``` 

improves the sound a lot specifically while playing movies. 

Apparently, the glitch-free audio does something for slower/elder (P3/P4 vintage) PC's. 

See if doing that gives any difference to your sound .

Your fix have solved my problems with sound stuttering and last Jaunty updates!
Q6600@400FSBx3.2GHzx1066MHz DDR2!
CMI8788 Sound Card!

---

### Post by lamborghiniwang on 2009-03-14
Well, I guess i have to agree with you that PA seems to be causing most of the complains ever since it was forced into Hardy. most of the problems were gone after Intrepid was released, but I am having the same kind of problems after upgrade to Jaunty. I know Jaunty is still in Alpha, but still it is a pain in the a**. As many people were saying that PA is still new, but shouldn't that be the reason to put PA as an optional package for general users? For those whom absolutely need to have PA, they can install that, while for those of us who only want to have a audio system that can play mp3, watching video and chat with friends over Skype, we really don't need all those fancy features in PA.

People can always come up a cooler ideas or introducing cooler features, but I think for most of us, the rule of thumb has always been "don't fix it if it is not broken", and clearly ALSA is not broken, and the new feature of PA clearly don't worth the seemingly endless hassles, at least at this point. The bottom line is, PA doesn't seem to be ready.

---

### Post by markbuntu on 2009-03-14
Most of the problems with pulse in jaunty are due to a few things, trying to use pulse 0.9.14 which is just a bunch of bug fixes instead of 0.9.15 which the pulse devs recomend, trying to use the glitch free model on a kernel that cannot support it (this has recently been abandoned thank goodness) and a bunch of not fully tested alsa drivers in alsa 1.0.19. 

These are not particularly problems with pulseaudio.

If you want to get on the real bleeding edge, use KDE4 and Phonon which is definitely not all there yet.

---

### Post by Polygon on 2009-03-14
pulseaudio works perfect for me, and has the added bonus of actually getting my microphone working when it never worked before.

Pulse audio will be great in future releases

---

### Post by billstei on 2009-03-14
I would gladly use PulseAudio if/when Wine can use it, and as long as it doesn't interfere with Jack.

---

### Post by markbuntu on 2009-03-14
> **billstei said:**
> I would gladly use PulseAudio if/when Wine can use it, and as long as it doesn't interfere with Jack.

If you launch wine with padsp wine and set wine to use oss it should work with pulseaudio for almost all windoze applications. Otherwise you need to wait for the wine devs to fix their faulty alsa plugin or make a pulse plugin which would probably be easier.

You can get the module pulse-jack from the Debian repos and jack and pulseaudio can happily coexist. With it you can push any pulse using app through jack with all the pulse and jack goodness.
It works for me and a lot of other people using hardy and intrepid 32 and 64 bit and their ubuntustudio versions.

There is more on that here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by kayosiii on 2009-03-15
Which begs the question -- when is ubuntu going to move jackd into the standard repos... I don't have to recompile everything in standard just to get it to work with my soundcard.
(or pull from debian)

---

### Post by olskar on 2009-03-15
> **kayosiii said:**
> Which begs the question -- when is ubuntu going to move jackd into the standard repos... I don't have to recompile everything in standard just to get it to work with my soundcard.
(or pull from debian)

You can file a request (Main inclusion request) to have it moved from there, then it will propably happen if the reasons are good enough. Worked for me earlier :) Good luck!

[https://wiki.ubuntu.com/MainInclusionProcess](https://wiki.ubuntu.com/MainInclusionProcess)

---

### Post by plun on 2009-03-15
> **kayosiii said:**
> Which begs the question -- when is ubuntu going to move jackd into the standard repos... I don't have to recompile everything in standard just to get it to work with my soundcard.
(or pull from debian)

Is it broken ?

Jackd package description
[http://packages.ubuntu.com/jaunty/jackd](http://packages.ubuntu.com/jaunty/jackd)

active bugs for the moment
[https://launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bugs](https://launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bugs)

:confused:

---

### Post by olskar on 2009-03-15
> **plun said:**
> Is it broken ?

Jackd package description
[http://packages.ubuntu.com/jaunty/jackd](http://packages.ubuntu.com/jaunty/jackd)

active bugs for the moment
[https://launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bugs](https://launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bugs)

:confused:

I guess he wants to move it from universe to main? :confused: But I can't see why really, enabling the universerepo would be simplier

---

### Post by markbuntu on 2009-03-15
It seems that the reason jackd is not in the main repos has to do with its use of some non-free code in the freebob interfaces for firewire support. Why this precludes entirely any support for jackd in alsa by the truncation of libasound2 ( removal of alsa-jack libs) and the exclusion of the pulse-jack modules in even the universe repo seems to be supported by ridiculously convoluted reasoning at best.

Pressure must be applied to the people making these decisions to point out the inherent contradiction between the underlying tenets of ubuntu their position.

---

### Post by rv65 on 2009-03-15
PulseAudio has broken OSS a couple of times. Now it's working just fine for some reason. The 2.6.28-9 kernel must have done something weird. I also have OSS 4.2 since I have an X-Fi and I could never get the creative driver to work.

Maybe it's that new pulseaudio version that fixed it.

---

### Post by ugkbunb on 2009-03-15
Lennart posted about this... 

I had many of the problems people listed above... however after switching to Arch PulseAudio finally loads like it should in user-mode and with a custom real-time preempt kernel I have been able to fully eliminate glitchy/skippy audio playback. This is with 0.9.15-test5...

tsched=0 works because it is disabling glitch-free audioplayback wich relies on a kernel latencies being low.


> [pulseaudio-discuss] Distribution kernels and glitch-free (Packagers, read this!)

Lennart Poettering
Sun, 22 Feb 2009 11:37:31 -0800

Heya!

As one result of the alsa-time-test testing (see that last mail of
mine regarding broken sound drivers) input I got from folks, I learned
how very different the different distribution kernels actually
behave. They are much more different than i actually assumed.

Apparently OpenSUSE ships a kernel (2.6.27.7-9-pae) that causes
scheduling latencies of > 210ms. That is a lot. That is really really
really a lot. Other non-Fedora distributions apparently do something similar.

The parameters in the glitch-free logic are tuned for Fedora-kernels
that easily give latencies of 5ms or so. 

ALSA artificially limits the overall buffer size to 64k (i.e. 371ms on
44100hz/2ch/s16le). That this size is not that much when speaking of
scheduling latencies of 210ms should be obvious.

Now, the glitch-free mode in PA is a major departure from the
traditional playback mode. In traditional playback mode the sound card
buffer is filled as soon as at least one 'fragment' of it ran
empty. Usually 4 fragments or so are used, i.e. the fill level will
oscillate between 'full' and 'full minus one fragment size minus the
scheduling latency'. If we have a buffer of 371ms we have a fragment
size of 91ms. With a kernel like that OpenSUSE kernel hence the fill
level oscillates between 371ms and 70ms. Which of course is usually
good enough to not get a drop out. Should a drop out happen nonethless
we continue as if nothing happened given that fragment settings cannot
be reconfigured during runtime.

Now, let's have a look what this means for glitch-free mode. In g-f
mode we disable sound card interrupts (and get rid of 'fragments'
entirely) as far as possible to minimize power consumption. We
schedule audio via system timers instead of the sound card's fragment
logic. Instead of already filling up after a single fragment was
played we delay the fill up until only 10 ms are still left in the
buffer (in PA 0.9.14 that is, i increased the default to 20ms now on
.15). i.e. with a Fedora scheduling latency of 5ms the buffer fill
level will hence oscillate between 371ms and 5ms. Still good enough to
not get into drop outs. If a drop out happens nonethelless we will
double the 10 ms to 20ms and go on. If that still turns out to not be
enough we double again, and so on. If this logic with these parameters
is run on an OpenSuse kernel, drop-outs will necessarily happen right
away. Because 10ms minus the sched latency of 210ms equals
FAILURE. And doubling the wakeup time again and again will require
quite a number of iterations, i.e. more than just a few underruns at
the beginning. Also the doubling will quickly come near to the full
buffer size of 371ms causing a lot of CPU to be eaten, since we will
wake up very very often.

So, what do we read from this?

0) Fedora is awesome, other distributions suck ;-)

1) For ***** sakes: get your bloody kernels fixed. Enable preempt, set
   HZ to 1000. Get rid of low-quality drivers that block the
   CPU. Latencies of 210ms is *REALLY NOT NECESSARY*.

2) If you want to stick with your crap kernel, then either disable g-f
   entirely or adjust the #defines at the top of
   src/modules/alsa-sink.c and src/modules/alsa-source.c.

Thank you very much,

Lennart

---

### Post by biasquez on 2009-03-15
i'm using pulse 9.15. sometimes i have noises listening some song but there is serious problem: sometimes, pulse crashes and i must reboot pc if i want to have sound..

errors:
kernel: [16161.977587] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
pulseaudio[4242]: core.h: Assertion 'pa_object_refcnt(pa_object_cast(o)) > 0' failed at ./pulsecore/core.h:159, function pa_core_assert_ref(). Aborting.

---

### Post by plun on 2009-03-15
> **olskar said:**
> I guess he wants to move it from universe to main? :confused: But I can't see why really, enabling the universerepo would be simplier

Well.... then its for him to file a bug broken or not  !!!

---

### Post by kayosiii on 2009-03-15
> **plun said:**
> Well.... then its for him to file a bug broken or not  !!!

This has been in the tracker for a long time.... We were promised that they would look at moving jack to main for Jaunty but that looks not to have happened. While this is the case it means no support for Jack in....

pulse-audio 
alsa
lib-xine
vlc

all of which have the components to talk to jack (and thus my sound card) none of which work on Ubuntu without having to recompile them from source. This quite frankly is not something I want to be doing every time I update Ubuntu...

---

### Post by kayosiii on 2009-03-15
> **markbuntu said:**
> It seems that the reason jackd is not in the main repos has to do with its use of some non-free code in the freebob interfaces for firewire support. Why this precludes entirely any support for jackd in alsa by the truncation of libasound2 ( removal of alsa-jack libs) and the exclusion of the pulse-jack modules in even the universe repo seems to be supported by ridiculously convoluted reasoning at best.

Pressure must be applied to the people making these decisions to point out the inherent contradiction between the underlying tenets of ubuntu their position.

In that case libffado/libfreebob should be moved into restricted... none of the firewire code is in jackd itself.

---

### Post by crimsun on 2009-03-16
> **vhaarr said:**
> I've been running Ubuntu with ALSA ever since I installed it a few years ago, and once PulseAudio was "forced" upon us a release or two ago, I simply uninstalled ubuntu-desktop and nuked all the pulse packages, and continued running with ALSA.

I blogged about such a decision at [http://drowninginbugs.blogspot.com/2009/02/pulseaudio.html]("http://drowninginbugs.blogspot.com/2009/02/pulseaudio.html").

In short, it's great to complain about things, but be aware that responding to everyone's complaints takes away resources from fixing the bugs. I don't get paid to fix these bugs (none of the work I've invested in Ubuntu has ever been compensated), so feel free to jump in and help me resolve them for Jaunty.

> **vhaarr said:**
> 1. I don't need pulseaudio - ALSA works fine, and it always has for me.

Good for you. Just because "it has always worked" doesn't mean "it has always been the right way" - we're uncovering these bugs thanks to PulseAudio.

> **vhaarr said:**
> 2. PulseAudio makes my sound lag. Not usually when I play something continously, but when I pause it and start again - like a movie or a tune, or anything - I get stuttering. This didn't happen with ALSA.

So don't use PulseAudio, but be aware that not using PulseAudio likely moves your complaints into the noise range.

PulseAudio 0.9.14 is the safer bet for Jaunty, but you can bet we'll be moving to 0.9.15+ ASAP.

> **vhaarr said:**
> I was at loss to where I could vent my feelings about this, and figured I might as well write it up here. I know that countless other PulseAudio threads have popped up on the forums, for good and bad, and I am not making this thread to
 - Troll
 - Flame
 - Discuss
 - Offend
 - any other negative

I'm simply writing it to *inform*.

Hopefully one of the developers will read it and maybe devote an hour or two to the issue.

Which issue? I have a shedload of bugs that I spend virtually every waking non-work hour on. Are you volunteering to assist me? If so, great!

---

### Post by Flag on 2009-03-16
Dear Crimsun,

I surely appreciate what you, the development team and all other volunteers are working at.
As info, I'm running Ubuntu ( mainly ) for years now as # 1 distro, with W$ as virtual machine for a number of reasons.
Now, what the average user ( not the ones looking for challenges ) wants is an OS that suits his needs out of the box. In my opinion this should include a working audio system, so at this stage ( aplha 6 ) it's fine we have to adjust things here and there to get it working, but once the final release is there it should be working straight away, including eg Skype.
Seen the number of posts and threads re PA it is clear that lots of people are struggling with it, again - my opinion - this shouldn't be.
It's easy to say --- if you don't like it, don't use it --- that's not the issue, people complaining are using it, otherwise they couldn't file their complaints, if they don't file their complaints, you ( and thanks again for your work ) can't react.
If I look at my own system, it's a simple Acer Aspire 7520, I install a final Ubuntu release and I can't use, eg again Skype ( I use it a lot like millions others ),I need to " google " for hours to try this, try that, add this, add that, change this, change that etc. etc. The bottomline is it works - more or less - but sound quality is lousy. 
So to answer the header : Do I need PA - in a final release ? Yes, if it works. No if it doesn't.

---

### Post by Polygon on 2009-03-16
to counter your argument, i could never get skype to work with alsa, i spent hours googling and googling. Why should we include alsa when it doesn't work? With pulseaudio i am able to easily use my microphone with skype.

See what i did there? the complaints go both ways.

pulseaudio is far better then alsa. there are so many factors of things that can go wrong (for example, skype is a closed source application, it might be THEIR problem)

---

### Post by markbuntu on 2009-03-16
> **kayosiii said:**
> In that case libffado/libfreebob should be moved into restricted... none of the firewire code is in jackd itself.

Well, they say that freebob has some restricted code in it and when ffado is improved and jack moves to ffado then they will put jack in main. That is what they say anyway in the launchpad bug report requesting the module pulse-jack and is there reasoning for excluding any way to connect jack with pulse. I think it is just a bunch of bull*** myself so I stay out of it and just get the module pulse-jack from the debian repos.

---

### Post by markbuntu on 2009-03-16
> **Polygon said:**
> to counter your argument, i could never get skype to work with alsa, i spent hours googling and googling. Why should we include alsa when it doesn't work? With pulseaudio i am able to easily use my microphone with skype.

See what i did there? the complaints go both ways.

pulseaudio is far better then alsa. there are so many factors of things that can go wrong (for example, skype is a closed source application, it might be THEIR problem)

The issues with skype are definitely problems with the skype devs making faulty assumptions and not implementing ALSA standard protocols which pulse strictly enforces.

You should be glad that pulse is bringing all this to light so it will all be fixed now. Even the audacity devs have started to fix their crappy alsa driver after doing nothing about it for 3 years.

---

### Post by Flag on 2009-03-17
This seems to narrow down to Skype, which wasn't my main issue, though I have Skype working pretty much OK under 8.04 and sofar under 9.04, alpha yes, it doesn't.
So I boot 9.04, try to play a MP3, all I hear is cracking, statics. Shut it down and restart it's OK. Skype with all kind of different settings just produces a crackling irritating sound once I play back the test call.
Seen the fact that I don't have sound issues under 8.04, despite the comments towards the Skype team, which make sense, and the fact I do have problems with 9.04 the conclusion seems to be clear.
I'm not complaining, I'm just reporting, I'm trying out 9.04 since alpha 2 and I'm convinced it could be the best Ubuntu distro sofar provided an essential thing like sound works straight away in the final release, not just for me, but fore all potential users, they are not waiting for, willing to spend hours to get this working, they will want something running straight away after install.
With all respect to the people involved in development.

---

