---
title: "HOWTO: PulseAudio Fixes (distilled)"
date: 2008-07-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by psyke83 on 2008-07-22
[COLOR="Red"]**EDIT 081114: Please read the up-to-date guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)**[/COLOR]


This guide is a distilled version of my _[PulseAudio Fixes & System-Wide Equalizer]("http://ubuntuforums.org/showthread.php?p=4928900")_ thread, intended for Intrepid testers. This guide will quickly configure PulseAudio for Intrepid and get your sound working properly - no fuss, no detailed explanations for each step (see my Hardy guide for that)! This is the way PulseAudio *should have been* configured for Hardy and *should be *configured for Intrepid. Read the FAQ below for more details.
[COLOR=Red]
NOTE: This guide is only suitable for **U**buntu 8.10 (i.e., the standard GNOME release). Although Kubuntu and the other flavours can be configured for PulseAudio, as far as I know they do not use PulseAudio by default.[/COLOR]

[SIZE=3]**PulseAudio Fixes**[/SIZE]

[1a]("https://bugs.launchpad.net/bugs/257403"). [COLOR="Red"] Optional: Follow this step if you wish to avail of any future updates to PulseAudio or Flash packages in my PPA. Since October, most fixes have been committed to the official repositories, so this is no longer important.[/COLOR]

Add the following lines to /etc/apt/sources.list:
```
$ gksudo gedit /etc/apt/sources.list
```
```
# PulseAudio Fixes & Adobe Flash - Preview Packages (psyke83)
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main
```

[1b]("https://lists.ubuntu.com/archives/ubuntu-devel/2008-August/026221.html").[COLOR="Red"] Optional: Follow this step if you wish to test PulseAudio 0.9.12 from Luke Yelavich's PPA. This step is **not** recommended, due to stability regressions.[/COLOR]

Add the following lines to /etc/apt/sources.list:
```
$ gksudo gedit /etc/apt/sources.list
```
```
# PulseAudio 0.9.12 - Preview Packages (TheMuso)
deb http://ppa.launchpad.net/themuso/ubuntu intrepid main
deb-src http://ppa.launchpad.net/themuso/ubuntu intrepid main
```

[2]("https://bugs.launchpad.net/bugs/198453"). Configure libao applications to use PulseAudio:
```
$ echo "default_driver=pulse" >~/.libao
```

[3]("https://bugs.launchpad.net/bugs/192888"). Perform the following steps to remove obsolete configuration files, ensure "libflashsupport" is not installed & you have the all the necessary packages up-to-date:
```
$ rm -r ~/.pulse ~/.asoundrc*
$ sudo apt-get update && sudo apt-get dist-upgrade
$ sudo apt-get remove libflashsupport
$ sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio
```[COLOR="Red"]NOTE: Choose **Y**es to allow unsigned packages to be installed.[/COLOR]

4. Go to System/Preferences/Sound. Set all "Sound playback" options to "Autodetect", and set "Sound capture" to "ALSA". 

5. Reboot for changes to take effect!

[SIZE=3]**Downgrade PulseAudio 0.9.12 -> 0.9.10**[/SIZE]

If you previously tested Luke's packages but wish to downgrade, here is a convenient method to downgrade packages:

1. Manually remove/comment Luke's PPA (aka TheMuso) from your /etc/apt/sources.list.

2. Update your repository lists, and and downgrade the PulseAudio packages:
```
$ sudo apt-get update
$ sudo apt-get install libpulse-browse0/intrepid libpulse-mainloop-glib0/intrepid libpulse0/intrepid pulseaudio/intrepid pulseaudio-esound-compat/intrepid pulseaudio-module-gconf/intrepid pulseaudio-module-hal/intrepid pulseaudio-module-x11/intrepid pulseaudio-module-zeroconf/intrepid pulseaudio-utils/intrepid libpulsecore5/intrepid padevchooser/intrepid pavucontrol/intrepid paprefs/intrepid libasound2/intrepid libasound2-plugins/intrepid
```
[COLOR="Red"]NOTE: If asked, choose **Y**es to install the package maintainer's version of configuration files.[/COLOR]

3. Logout & back in, or restart your computer.

[SIZE=3]**Frequently Asked Questions**[/SIZE]

**Q. What exactly is PulseAudio?**
A. From the [homepage]("http://www.pulseaudio.org/"):
> PulseAudio is a sound server for POSIX and Win32 systems. A sound server is basically a proxy for your sound applications. It allows you to do advanced operations on your sound data as it passes between your application and your hardware. Things like transferring the audio to a different machine, changing the sample format or channel count and mixing several sounds into one are easily achieved using a sound server.Simplified: PulseAudio is responsible for playback and mixing of audio on your system. It is not a sound driver - in fact, it runs on top of the [Advanced Linux Sound Architecture]("http://www.alsa-project.org"). Aside from all the cool effects PulseAudio provides, it serves as a replacement for ALSA's sound mixing ([DmixPlugin]("http://alsa.opensrc.org/DmixPlugin")) - thus allowing multiple applications to share access of your sound card.

**Q. PulseAudio? Bleh! I don't want it on my system.**
A. Well... tough! PulseAudio is *already* installed and active on Intrepid (and Hardy) by default; it replaces ESD (ESound Daemon) for system sounds, and most of Ubuntu's default applications already use it (Totem, Rhythmbox, and any other applications using the GStreamer framework). Although some high-profile applications also support PulseAudio (such as VLC and mplayer), most applications use plain ALSA or OSS output, and thus don't have native PulseAudio support.

**Q. If PulseAudio is already installed, why do I need this guide?**
A. While PulseAudio has been installed by default since Hardy Heron (8.04), we dropped the ball when it came to the configuration part. A quote from the main PulseAudio developer, [Lennart Pöttering]("http://0pointer.de/blog/projects/jeffrey-stedfast.html"):> Some distributions did a better job adopting PulseAudio than others. On the good side I certainly have to list Mandriva, Debian, and Fedora. **OTOH Ubuntu didn't exactly do a stellar job. They didn't do their homework. Adopting PA in a distribution is a fair amount of work, given that it interfaces with so many different things at so many different places. The integration with other systems is crucial. The information was all out there, communicated on the wiki, the mailing lists and on the PA IRC channel.** But if you join and hang around on neither, then you won't get the memo. To my surprise when Ubuntu adopted PulseAudio they moved into one of their 'LTS' releases rightaway. Which I guess can be called gutsy -- on the background that I work for Red Hat and PulseAudio is not part of RHEL at this time. I get a lot of flak from Ubuntu users, and I am pretty sure the vast amount of it is undeserving and not my fault.Here are some common examples to illustrate the current audio situation in Intrepid: 
[LIST=A]
[*]Totem and Rhythmbox - these applications can play audio simultaneously, as they both use the GStreamer framework - and the GStreamer framework has native PulseAudio support.
[*]Totem and Neverball - if you try to use these applications together, only one will successfully play audio, and the other will fail. Totem will successfully use PulseAudio (through GStreamer). Neverball uses the SDL libraries for sound, however, and the ALSA driver for SDL is installed in Ubuntu by default. This will cause a conflict.
[*]Totem and Adobe Flash - again, it is not possible to use both of these applications simultaneously, as Totem uses PulseAudio (through GStreamer), but Flash only has ALSA support and thus cannot use PulseAudio by default. This will also cause a conflict.
[/LIST]
Due to this misconfiguration of PulseAudio, audio mixing will appear broken for many applications in Ubuntu. This guide will configure PulseAudio the way it *should be* configured, and will resolve ~99% of these audio mixing issues (including the examples listed above).
[COLOR="Red"]Update 07/10: The PulseAudio ALSA plugins are now enabled by default! Some issues remain (mostly for 64 bit users), which should hopefully be resolved soon.[/COLOR]

**Q. How can I verify if PulseAudio is working correctly?**
A. Go to Applications/Sound & Video/PulseAudio Device Chooser - this will load the "PulseAudio Device Chooser" applet into the notification tray, giving easy access to common PulseAudio GUIs. Left-click on the applet and click "Volume Control...". If an application is currently playing audio via PulseAudio, there will be an entry for the application in the Playback tab of PulseAudio Volume Control. If a program is playing audio but doesn't show an entry, the application is bypassing PulseAudio and your system is misconfigured - you're going to suffer from audio mixing problems. For more details, see **Appendix B** of the _[full guide]("http://ubuntuforums.org/showthread.php?p=4928900")_.

**Q. I cannot get Skype/WINE/an OSS application/xyz working correctly with PulseAudio, what can I do?**
A. Some applications need to be configured properly to work with PulseAudio. Again, this should be configured in the packaging of these applications when possible, but it's not - so we have to live with it. See **Appendix A** of my _[full guide]("http://ubuntuforums.org/showthread.php?p=4928900")_, and upstream's [PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup"). There are still a few applications that do not work correctly, but they are the minority and I trust they will be fixed soon.

**Q. I have configured PulseAudio, but I notice a lot of stuttering in some applications. What's up?**
A. This is a problem with PulseAudio's buffering. It should be resolved in the next release of PulseAudio (the so-called "glitch-free" version). If you can't wait for that, see **Part C** of my _[full guide]("http://ubuntuforums.org/showthread.php?p=4928900")_ to configure the fragment sizes and amounts.

**Q. Where can I find the appropriate bug reports?**
A. If you click on a step number it will link to the appropriate bug report. Remember, the more testing these packages and settings get, the more likely we are to get these fixes included officially.

**Q. I have a question about...**
A. See the Hardy _[guide]("http://ubuntuforums.org/showthread.php?p=4928900")_ first! If it doesn't answer your question, feel free to ask. Remember, this is the "distilled" guide. We're running the Intrepid release, so we're expected to be a little more savvy... ;). 

[COLOR=Red]NOTE: If you're using Intrepid, please ask your question in this thread. Do *not* ask questions in the "full guide" thread, as it is not intended for the development release. Thanks![/COLOR]

---

### Post by Rocket2DMn on 2008-07-22
You are a god amongst men.  I haven't really used sound in Intrepid since I mostly use it for checking against filed bugs, but this seems to have fixed the login sound issue which was very scratchy before.
Thank you.

---

### Post by spamzilla on 2008-07-22
Works perfectly, thanks!

---

### Post by cjm5229 on 2008-07-22
Thanks much, I used your guide to get Hardy sound working, when it first came out, and you gave me advise on fixing the issue I had with sound coming out of my PC speaker instead of my Audio speakers in Intrepid Alpha 1. I already had most of my issues fixed in Intrepid because of your advise earlier, but this takes care of the other problems. Now if we could just get the Ubuntu Devs to set this up right to begin with!

---

### Post by amano on 2008-07-22
> **cjm5229 said:**
> Thanks much, I used your guide to get Hardy sound working, when it first came out, and you gave me advise on fixing the issue I had with sound coming out of my PC speaker instead of my Audio speakers in Intrepid Alpha 1. I already had most of my issues fixed in Intrepid because of your advise earlier, but this takes care of the other problems. Now if we could just get the Ubuntu Devs to set this up right to begin with! 

Filing a bug would be the correct way to bring a topic to the developers' attention.

---

### Post by psyke83 on 2008-07-22
> **amano said:**
> Filing a bug would be the correct way to bring a topic to the developers' attention.

Very true. All the relevant bugs are linked in the original thread, however, and I will shortly post on the ubuntu-devel-discuss mailing list to hopefully stimulate discussion and action towards getting this sorted properly.

This guide can serve to help users, but it's also as a nice summary for developers to see the outstanding issues with PulseAudio.

---

### Post by Rocket2DMn on 2008-07-22
I knew I had seen bug reports on PulseAudio, namely [https://bugs.launchpad.net/gst-plugins-good/+bug/190754](https://bugs.launchpad.net/gst-plugins-good/+bug/190754)
If there are other reports please list them and I will mark appropriate ones as duplicates of others if you want.

---

### Post by psyke83 on 2008-07-22
> **Rocket2DMn said:**
> I knew I had seen bug reports on PulseAudio, namely [https://bugs.launchpad.net/gst-plugins-good/+bug/190754](https://bugs.launchpad.net/gst-plugins-good/+bug/190754)
If there are other reports please list them and I will mark appropriate ones as duplicates of others if you want.

Here are some of the most important bugs; these are well-documented and don't need to be marked as duplicates (especially the Flash bugs):

Default ALSA device must use PulseAudio, otherwise ALSA applications may fail: _[bug #198453]("https://bugs.launchpad.net/bugs/198453")_
Adobe Flash & PulseAudio issues: _[bug #192888]("https://bugs.launchpad.net/bugs/192888")_ and _[bug #239182]("https://bugs.launchpad.net/bugs/239182")_
Stuttering audio (may not be an issue in the "glitch-free" release of PulseAudio): _[bug #188226]("https://bugs.launchpad.net/bugs/188226")_ and _[bug #190754]("https://bugs.launchpad.net/bugs/190754")_

These bugs are pretty closely connected. For example, Firefox needs to be fixed in bug #239182 to allow us to migrate to Flash 10, which in turn requires bug #198453 to be fixed in order to have stable PulseAudio support in Flash. If both of these bugs are fixed, then we can remove the buggy "libflashsupport" package, therefore eliminating the need to fix bug #192888 at all.

---

### Post by Rocket2DMn on 2008-07-22
Cool, it seems PulseAudio has a long way to go.

---

### Post by psyke83 on 2008-07-22
> **Rocket2DMn said:**
> Cool, it seems PulseAudio has a long way to go.

Not as much as you'd imagine. This guide applies the proposed fixes for the worst bug, #198453. As soon as Firefox 3.0.2 is released, bug #239182 will get fixed and #192888 will be marked invalid. When the next release of PulseAudio happens, the remaining bugs regarding stuttering will most likely become invalid.

Oh, and the bug #239182 is completely unrelated to PulseAudio, it's a bug in Firefox exposed by the latest "windowless mode" feature in Flash 10 beta 2 (and the latest swfdec), causing many common websites to crash. The reason why I mention this bug is that when Firefox is patched, Flash 10 will become stable and thus a real alternative to Flash 9. When that happens, all the PulseAudio incompatibilities of Flash 9 can be forgotton. Intrepid is already using Flash 10, so bug #192888 only applies to the LTS release.

Confusing, yes. A lot of work to be done, no ;). The developers just need to collaborate to make sure things get fixed in the proper way.

---

### Post by MaX on 2008-07-22
All I did to fix sound was ```
sudo apt-get install padevchooser
```
and then select the correct Sink choosing Other... and typing the name there from the Pulse Audio Managers Device section.
No need to blacklist the PC-speaker or anything.
(There's a thread on it somewhere here in the forum)

About PulseAudio not being ready... It seems like Ubuntu messes things up when they import it (according to the PA people).

---

### Post by psyke83 on 2008-07-22
> **MaX said:**
> All I did to fix sound was ```
sudo apt-get install padevchooser
```
and then select the correct Sink choosing Other... and typing the name there from the Pulse Audio Managers Device section.
No need to blacklist the PC-speaker or anything.
(There's a thread on it somewhere here in the forum)

About PulseAudio not being ready... It seems like Ubuntu messes things up when they import it (according to the PA people).

Yes, I also wrote a post detailing that method [here]("http://ubuntuforums.org/showpost.php?p=5299675&postcount=13"). The problem is that a) PulseAudio saves the last used sink in the volume-restore.table file, meaning that several apps continue to use the snd_pcsp module even if you have set the proper sink in padevchooser, and b) several users have complained that PulseAudio forgets your chosen sink when you log out. Blacklisting the kernel module is the easiest and most reliable workaround for now. 

The rest of the guide is also necessary to fix real PulseAudio (and not kernel) issues - see the FAQ for details.

---

### Post by philinux on 2008-07-22
To be honest I don't want to fix pulse audio by editing files etc etc. The devs should fix it with an update.

---

### Post by psyke83 on 2008-07-22
> **philinux said:**
> To be honest I don't want to fix pulse audio by editing files etc etc. The devs should fix it with an update.

Sure, that's your choice. But it's not always the best policy to passively sit back and wait for all the required fixes to roll in. Sometimes you need to get your hands dirty; test workaround and confirm bugs based on your findings, etc. The success or failure of a release can be influenced by the (in)actions of the testing community as well as the developers.

---

### Post by RAOF on 2008-07-22
> **philinux said:**
> To be honest I don't want to fix pulse audio by editing files etc etc. The devs should fix it with an update.

You are most welcome to work out how to fix it[1] and post the debdiff on a bug.  It's really not very difficult to get started in Ubuntu development, and fixing a bug that you care about is a great way to jump in.

[1] Generally, a patch which fixes a bug will be accepted, possibly after several iterations.  The initial patch may be rejected because it's not "clean", but this generally comes with some instructions as to how to fix the patch up.

The other big class of rejected patches would be where the patch simply covers up brokenness elsewhere.  At this stage of development, we're much more interested in fixing problems than papering over them.

---

### Post by mattismyname on 2008-07-23
What package do I need to install to get "PulseAudio Device Chooser" in my apps menu?

thanks

edit: I should have searched first.  Answer is "PulseAudio Device Chooser".

---

### Post by psyke83 on 2008-07-23
> **mattismyname said:**
> What package do I need to install to get "PulseAudio Device Chooser" in my apps menu?

thanks

You can't guess by looking at the guide? Well then...

> conn@inspiron:~$ apt-cache search pulseaudio device chooser
padevchooser - PulseAudio Device Chooser

:)

---

### Post by mattismyname on 2008-07-23
(redacted)

---

### Post by mriedel on 2008-07-23
Err, why is it still necessary to manually fix sound on intrepid? Hardy was a shame, I don't get how the devs could mess up sound config so hard. ALSA->Pulse->ALSA was set up so wrong, I don't even get how it could happen. Now how is it even possible it's not fixed in intrepid?

---

### Post by Rocket2DMn on 2008-07-23
> **mriedel said:**
> Err, why is it still necessary to manually fix sound on intrepid? Hardy was a shame, I don't get how the devs could mess up sound config so hard. ALSA->Pulse->ALSA was set up so wrong, I don't even get how it could happen. Now how is it even possible it's not fixed in intrepid?

It's a development release.  If stuff isn't broken in this alpha stage, the developers aren't trying hard enough.  That's why we are here.

---

### Post by amano on 2008-07-23
From Lennart Pöttering's blog ([http://0pointer.de/blog):](http://0pointer.de/blog):)

> Some distributions did a better job adopting PulseAudio than others. On the good side I certainly have to list Mandriva, Debian[3], and Fedora[4]. **OTOH Ubuntu didn't exactly do a stellar job. They didn't do their homework. Adopting PA in a distribution is a fair amount of work, given that it interfaces with so many different things at so many different places. The integration with other systems is crucial. The information was all out there, communicated on the wiki, the mailing lists and on the PA IRC channel. **But if you join and hang around on neither, then you won't get the memo. To my surprise when Ubuntu adopted PulseAudio they moved into one of their 'LTS' releases rightaway [5]. Which I guess can be called gutsy -- on the background that I work for Red Hat and PulseAudio is not part of RHEL at this time. I get a lot of flak from Ubuntu users, and I am pretty sure the vast amount of it is undeserving and not my fault.

If I remember correctly the initial integration was done by Martin Pitt, but early in the hardy cycle he handed this job over to Ted Gould for finetuning. But Ted doesn't seem to have investet too much time into integrating the sound server after the initial effort of Martin Pitt.

---

### Post by psyke83 on 2008-07-23
> **amano said:**
> From Lennart Pöttering's blog ([http://0pointer.de/blog):](http://0pointer.de/blog):)

Thanks, I've extended the original quote in the first post - it helps focus the blame on Ubuntu :).

We do have to keep in mind that the proper configuration for PulseAudio can negatively impact users of Kubuntu (where PulseAudio is not installed as far as I understand), and UbuntuStudio (as JACK and Audacity are not compatible with PulseAudio). There has to be some thought as to the best way to apply the proper PulseAudio configuration without breaking other users' setups (the pcm_pulse plugins do not fallback to ALSA when a PulseAudio server is not available, for example).

I'm convinced it's not impossible - or terribly difficult - to get PulseAudio working correctly by default. All that is needed is some planning and coordination between some developers responsible for different packages and aspects of the system. As Lennart mentioned, the other distributions made a better effort - and we too can do better this time.

I'll write up a post on Ubuntu-Devel-Discuss as soon as I get some free time, to hopefully get things moving (a little faster).

---

### Post by plun on 2008-07-23
> **psyke83 said:**
> 

I'll write up a post on Ubuntu-Devel-Discuss as soon as I get some free time, to hopefully get things moving (a little faster).

Well, I cannot see any reason to dig in the past and blame anyone.

This is a giant mess and we for sure lives in a commercial world.

So please also include this mess with the Pulse mess.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


And thanks for all of your work with this...  its the only way to
make something better.:)

---

### Post by psyke83 on 2008-07-23
> **plun said:**
> Well, I cannot see any reason to dig in the past and blame anyone.

Heh, I was only half-kidding when I used the word "blame" ;). But it is a matter of accountability. PulseAudio gained a bad reputation due to its implementation in Ubuntu Hardy (and will again in Intrepid, unless something changes); you can tell from the entry in Lennart's blog that he received unfounded criticism from Ubuntu users.

By the way, I think it's better to concentrate on the PulseAudio mess, and leave the general multimedia stuff for another day. There's no need mix these issues together right now.

---

### Post by plun on 2008-07-23
OK....

[B]
Can you hear me now?[/B]

[http://arstechnica.com/reviews/os/hardy-heron-review.ars/4](http://arstechnica.com/reviews/os/hardy-heron-review.ars/4)


and a user is using PulseAudio for something and this stuff is often dirty commercial formats which needs dirty codecs.

But I am glad if just swfdec/adobe 10 is fixed, if its any hope for a working Totem module I don't know  ? Seems to be "out of order" within every part of our world..:)

---

### Post by psyke83 on 2008-07-23
> **plun said:**
> OK....

[B]
Can you hear me now?[/B]

[http://arstechnica.com/reviews/os/hardy-heron-review.ars/4](http://arstechnica.com/reviews/os/hardy-heron-review.ars/4)

Excellent link, thanks. I'll be sure to mention it.

---

### Post by plun on 2008-07-23
> **psyke83 said:**
> Excellent link, thanks. I'll be sure to mention it.

Yup and the final part

> I'm convinced that PulseAudio is the best available solution for sound on Linux and I think that it will bring a lot of value to Ubuntu when it is fully integrated, but right now it represents a big regression because it creates lots of problems while most of its significant advantages aren't exposed or accessible to end users out of the box. 

[http://arstechnica.com/reviews/os/hardy-heron-review.ars/4](http://arstechnica.com/reviews/os/hardy-heron-review.ars/4)


"Thats the case"...:)

---

### Post by trikloretylen on 2008-07-24
> **psyke83 said:**
> [1]("https://bugs.launchpad.net/bugs/242966"). Edit "/etc/modprobe.d/blacklist":
```
$ gksudo gedit /etc/modprobe.d/blacklist
```Add the following line to the end of this file, then save:
```
blacklist snd_pcsp
```

It's probably better to edit /etc/modprobe.d/blacklist-custom instead. If module-init-tools is upgraded and has an updated /etc/modprobe.d/blacklist, it will want to replace it.

> **psyke83 said:**
> 
[3]("https://bugs.launchpad.net/bugs/198453"). Configure libao applications to use PulseAudio:
```
$ echo "default_driver=pulse" >~/.libao
```

I used /etc/libao.conf instead, as instructed by an earlier howto. That should also be ok, right?

---

### Post by psyke83 on 2008-07-24
> **trikloretylen said:**
> It's probably better to edit /etc/modprobe.d/blacklist-custom instead. If module-init-tools is upgraded and has an updated /etc/modprobe.d/blacklist, it will want to replace it.

Thanks, I'll update the guide (though perhaps there's an advantage to this behaviour considering that the bug will get fixed properly in the future). By the way, not many people have confirmed or commented on the PC Speaker bug (linked in the guide).

> I used /etc/libao.conf instead, as instructed by an earlier howto. That should also be ok, right?

Yes, it's the per-user equivalent of /etc/libao.conf. PulseAudio is configured to run per-user, so it's always better to configure PulseAudio per-user as well, otherwise applications will fail when there's no server running. Although libao applications are unlikely to be used without PulseAudio running, ALSA applications would be affected. For example, GDM wouldn't play any sound if you configured the pcm.pulse entries in /etc/asound.conf.

---

### Post by plun on 2008-07-24
**To all which I think is really important.**

Please read the whole blog post from Lennart Poettering

**PulseAudio FUD**

[http://0pointer.de/blog/projects/jeffrey-stedfast.html](http://0pointer.de/blog/projects/jeffrey-stedfast.html)


I also believe that this is something for Ubuntus Technical Board to 
look at.

Mr Ballmer and the WIndows community must sit and laugh when the GNU/Linux eco-system breaks down and flaming war starts.


This is just sad after reading Lenarts blog.  :(

---

### Post by trikloretylen on 2008-07-24
> **psyke83 said:**
> Thanks, I'll update the guide (though perhaps there's an advantage to this behaviour considering that the bug will get fixed properly in the future). 

Yes, that's certainly a valid point. Didn't think of that. I've always blacklisted the PC speaker and I've more stuff that I blacklist. I got annoyed when the system wanted to remove my changes in blacklist all the time and was happy to find out about blacklist-*.

> **psyke83 said:**
> By the way, not many people have confirmed or commented on the PC Speaker bug (linked in the guide).

Well, it bit me when pcspkr changed to snd_pcsp. Suddenly it wasn't blacklisted anymore and I heard weak sound from somewhere inside the computer when PulseAudio happily chose PC speaker as default.

---

### Post by psyke83 on 2008-07-24
> **trikloretylen said:**
> Well, it bit me when pcspkr changed to snd_pcsp. Suddenly it wasn't blacklisted anymore and I heard weak sound from somewhere inside the computer when PulseAudio happily chose PC speaker as default.

Right... my intent was to encourage you (or anyone else suffering from this issue) to comment and confirm on the bug, so developers will focus attention on the issue. :)

---

### Post by psyke83 on 2008-07-27
Hi,

To anyone that's followed this guide but still experiences crashes in Firefox on many common sites that contain flash content, you're probably suffering from [bug #239182]("https://bugs.launchpad.net/bugs/239182").

[Felix Geyer]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182/comments/15") has created some patched debs that contain the fix, please test and confirm if they help in the bug report!

i386:
```
$ wget -c http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb
$ sudo dpkg -i xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb
```

amd64:
```
$ wget -c http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_amd64.deb http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_amd64.deb
$ sudo dpkg -i xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_amd64.deb xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_amd64.deb
```

Restart Firefox for changes to take effect. Please comment on the bug report if these patched versions work!

*To revert back to Intrepid versions:
```
$ sudo apt-get install xulrunner-1.9-gnome-support/intrepid xulrunner-1.9/intrepid
```

---

### Post by guyster on 2008-07-28
Hello all, I have a weird issue with pulseaudio, but only after installing the nvidia-177 package.  After I installed intrepid alpha 3 this past weekend, my computer was coming up in low graphics mode and my desktop was huge.  I then installed this nvidia package, and now I'm unable to do anything with pavucontrol or padevchooser.  The error I get is "connection refused".  Anyone know of a work-around for this, or what possibly went wrong with the nvidia install?  Any help or ideas would be greatly appreciated.

Thanks much,


Guy

---

### Post by psyke83 on 2008-07-28
> **guyster said:**
> Hello all, I have a weird issue with pulseaudio, but only after installing the nvidia-177 package.  After I installed intrepid alpha 3 this past weekend, my computer was coming up in low graphics mode and my desktop was huge.  I then installed this nvidia package, and now I'm unable to do anything with pavucontrol or padevchooser.  The error I get is "connection refused".  Anyone know of a work-around for this, or what possibly went wrong with the nvidia install?  Any help or ideas would be greatly appreciated.

Thanks much,


Guy

First of all, get the nvidia driver working properly (this isn't the thread to ask about it). When the nvidia driver is working properly, paste the output of the following:

```
$ pulseaudio -k; wait 3; pulseaudio -vv
```

---

### Post by amano on 2008-07-29
a new pulseaudio version hit the repos: > * debian/patches/0006-pcspkr-last.patch: [B]Load the PC speaker as a sink
     after all other sound card sinks have been loaded.[/B] (LP: #242966)
   * debian/patches/0007-relibtoolize.patch: Regenerate relevant libtool
     bits, because even though libltdl7 is supposed to be API-compatible
     with libltdl3, the package FTBFs without regeneration.

Let's hope that the debian patch fixes the issues for all those who got beeper sound before.

---

### Post by amano on 2008-08-05
[http://pulseaudio.org/milestone/0.9.11](http://pulseaudio.org/milestone/0.9.11)

Pulseaudio 0.9.11 is out. 

I wonder if it will get integrated for Intrepid (although judging from hardy, they didn't spend too much time for that even for the LTS).

Glitch-free playback sounds nice (although chances are that it would be deactivated --> we will see).


EDIT: It is already integrated in the Fedora Alpha:

> * Many improvements, bugfixes, and enhancements from upstream
      * New graphical boot environment
      * Wireless connection sharing
      *** Audio improvements to remove glitches**
      * Security audit tool
      * Improved webcam support
      * Better IR remote control support
      * RPM 4.6
      * OCaml
      * Haskell

[http://lwn.net/Articles/292751/](http://lwn.net/Articles/292751/)

---

### Post by darco on 2008-08-05
> **psyke83 said:**
> Hi,

To anyone that's followed this guide but still experiences crashes in Firefox on many common sites that contain flash content, you're probably suffering from [bug #239182]("https://bugs.launchpad.net/bugs/239182").

[Felix Geyer]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182/comments/15") has created some patched debs that contain the fix, please test and confirm if they help in the bug report!

i386:
```
$ wget -c http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb
$ sudo dpkg -i xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb
```

amd64:
```
$ wget -c http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_amd64.deb http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_amd64.deb
$ sudo dpkg -i xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_amd64.deb xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_amd64.deb
```

Restart Firefox for changes to take effect. Please comment on the bug report if these patched versions work!

*To revert back to Intrepid versions:
```
$ sudo apt-get install xulrunner-1.9-gnome-support/intrepid xulrunner-1.9/intrepid
```

I tried the command for the i386 and I get 

```
wget -c http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb
--2008-08-05 20:42:04--  http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb
Resolving ppa.launchpad.net... 91.189.90.217
Connecting to ppa.launchpad.net|91.189.90.217|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2008-08-05 20:42:05 ERROR 404: Not Found.

--2008-08-05 20:42:05--  http://ppa.launchpad.net/sniperbeamer/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2+ppa1_i386.deb
Reusing existing connection to ppa.launchpad.net:80.
HTTP request sent, awaiting response... 404 Not Found
2008-08-05 20:42:05 ERROR 404: Not Found.

```
Is there a prob with this repo?

darco

---

### Post by Nullack on 2008-08-05
I just checked the packages and it seems with Intrepid were currently on 0.9.10-2ubuntu3

---

### Post by RAOF on 2008-08-07
> **Nullack said:**
> I just checked the packages and it seems with Intrepid were currently on 0.9.10-2ubuntu3

At least in part because 0.9.11 requires ALSA patches and is known to break a bunch of stuff.

---

### Post by psyke83 on 2008-08-14
Finally, it's possible to have a stable configuration that allows Flash 10 & PulseAudio to live together. I have uploaded a deb of the latest Flash package for Intrepid users to my PPA: [https://launchpad.net/~psyke83/+archive](https://launchpad.net/~psyke83/+archive)

As long as you have followed this guide, everything should work perfectly - but I would appreciate some testing anyway :).

---

### Post by zAo on 2008-08-15
Any suggestions on how to configure Pulse on the Server edition of Ubuntu? How can one make it autostart on boot for instance?

---

### Post by landcross on 2008-08-15
Flash 10 & PulseAudio work together OK on my PC. But I have an issue with Totem and VLC which both just close when I try to open a FLV  file.

I had the same issue before installing Flash 10

---

### Post by gabrielsaldana on 2008-08-16
> **psyke83 said:**
> This mini-howto is a distilled version of my _[PulseAudio Fixes & System-Wide Equalizer]("http://ubuntuforums.org/showthread.php?p=4928900")_ thread, intended for Intrepid testers. This guide will quickly configure PulseAudio for Intrepid and get your sound working properly - no fuss, no detailed explanations for each step (see my Hardy guide for that)! This is the way PulseAudio *should have been* configured for Hardy and *should be *configured for Intrepid. Read the FAQ below for more details.
[COLOR=Red]
NOTE: This guide is only suitable for **U**buntu 8.10 (i.e., the standard GNOME release). Although Kubuntu and the other flavours can be configured for PulseAudio, as far as I know they do not use PulseAudio by default.[/COLOR]


Hey, the notice about Kubuntu was not on the original post. Now I dont have any sound! How can I revert what the packages did?

---

### Post by psyke83 on 2008-08-16
> **gabrielsaldana said:**
> Hey, the notice about Kubuntu was not on the original post. Now I dont have any sound! How can I revert what the packages did?

Um, you just quoted the part where it says Kubuntu is not suitable. I don't know precisely how to revert changes 100% as I'm not running Kubuntu.

As long as the installation of PulseAudio didn't conflict/remove any packages, the most likely answer is to simple delete ~/.asoundrc (or restore your original from a backup, if necessary).

---

### Post by psyke83 on 2008-08-20
I (finally) posted on the ubuntu-devel-discuss list regarding PulseAudio (and Flash) integration issues. You can read it here: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-August/005293.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-August/005293.html)

---

### Post by plun on 2008-08-20
Thanks !   Your solution works just great in both Intrepid and Hardy.



Have you been talking to "asac", "fta" and the others in mozilla-team ?  IRC


Ubuntu Core Developers  ?   Ask them  ?

[Cesare Tirabassi]("https://lists.ubuntu.com/archives/intrepid-changes/2008-August/004608.html"), norsetto at ubuntu.com  was maintainer for the last update.

---

### Post by plun on 2008-08-27
Alsa 1.0.17 in repo....

[https://lists.ubuntu.com/archives/intrepid-changes/2008-August/005858.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-August/005858.html)


- Master volume on 100% after install....

Quick test:

- No crackling with the 2.6.27 kernel

:guitar:

---

### Post by plun on 2008-08-28
More challengies..... :)

> 
[B]
PulseAudio 0.9.11 available, call for testing.[/B]

Greetings all,
I have made PulseAudio 0.9.11 available in my PPA(1). This is a call for testing of pulseaudio 0.9.11. I know a lot of users would like intrepid to ship with 0.9.11, but since a fair amount of changes have occurred between 0.9.10 and 0.9.11, I would like to get sufficient testing performed by the comunity at large before trying to push it into intrepid. For best results, please use kernel 2.6.27, as it contains alsa 1.0.17, needed by PulseAudio 0.9.11.

The reason why this is only available now is due to the kernel, and subsequently alsa, being updated so late in the intrepid cycle, something which I hope to address for intrepid+1.

An assessment of whether pulseaudio 0.9.11 is ready will be made after a couple of weeks of testing. I am willing to make updates to the package in my PPA to attempt to address issues as users find them. If you find any issues, please file a bug against pulseaudio in launchpad.

Thanks

Luke
(1)[http://launchpad.net/~themuso/+archive](http://launchpad.net/~themuso/+archive)

[https://lists.ubuntu.com/archives/ubuntu-devel/2008-August/026221.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-August/026221.html)


@psyke 83, maybe to "coordinate" this with your and Luke's ppa  ?

Installing....:)


EDIT about bugs

> On Thu, Aug 28, 2008 at 04:02:21PM EST, Luke Yelavich wrote:
If you find any issues, please file a bug against pulseaudio in launchpad.

To clarify, filing bugs against the ubuntu package is fine, but please indicate that you are filing a bug about pulseaudio 0.9.11 from my PPA.

Thanks

Luke


EDIT 2, upstream changelog
[http://pulseaudio.org/milestone/0.9.11](http://pulseaudio.org/milestone/0.9.11)

---

### Post by psyke83 on 2008-08-28
> **plun said:**
> @psyke 83, maybe to "coordinate" this with your and Luke's ppa  ?


Thanks for pointing me to that post. Unfortunately Luke's ~ppa2 package neglects to install some important libraries. I've posted the debdiff fixing the issue at bug [262322]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/262322").

I haven't uploaded the fixed package to my PPA as Luke may want to keep all the changes central to his PPA. The debdiff allows PulseAudio to correctly run, but the pulse_pcm plugins appear to be broken. I'm investigating this now.

Edit: also filed bug [262326]("https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326") regarding the pcm_pulse problem.

---

### Post by Nullack on 2008-08-28
Top stuff Pyske, mate Ive confirmed those two

---

### Post by plun on 2008-08-28
> **psyke83 said:**
> [262322]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/262322").

[262326]("https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326") regarding the pcm_pulse problem.

OK thanks !

One issue I noticed....

Menu System > Prefs > Sound   and tab Sounds, everything is grayed out for me...

Perfect sound without any "cracklings" anyway....:)

This one is important to get into Intrepid !!!!

---

### Post by vishalrao on 2008-08-31
working fine for me too. although i dont know about the glitch-free part... im not running any cpu-hogging apps, just tried rhythmbox which works fine... (gdm login window ready sound too)...

note: running the "hardware testing" applet, the sound test does seem to crackle to me, just the same as default intrepid alpha4 install... :-( file bug?

---

### Post by Nullack on 2008-08-31
A degree of conjecture and competition is a healthy thing. It is a shame though that some people when involved are not equipped with the rational foresight to construct a logical argument without getting into fallacies.

---

### Post by vishalrao on 2008-08-31
scratch that about "hardware testing crackling" - its not using PA. i guess PA 0.9.11 is working decent enough for me.

i ran PA device chooser from applications->sound&video menu, then started volume control and manager, started rhytmbox and it shows up in the playback stream list of PA, but the hardware testing applet doesnt seem to be there... volume meter doesnt seem to be showing any levels while rhythmbox is playing

---

### Post by amano on 2008-08-31
Slightly off-topic (sorry): The latest wine (1.1.3) comes with some pulseaudio fixes. Maybe this version should be shipped or at least those fixes be backported to 1.0.

I hope that they will ship the glitch-free version of pulseaudio in the intrepid repos soon to get some wider testing.

---

### Post by psyke83 on 2008-08-31
> **amano said:**
> Slightly off-topic (sorry): The latest wine (1.1.3) comes with some pulseaudio fixes. Maybe this version should be shipped or at least those fixes be backported to 1.0.

I hope that they will ship the glitch-free version of pulseaudio in the intrepid repos soon to get some wider testing.

PulseAudio 0.9.11 has more issues than the previous release (which isn't a surprise, as Lennart gave plenty of warning), and though WINE 1.1.3 works, it stutters far too much to be usuable. Unless 0.9.12 is released soon, adds stability, and bug #262322 is fixed, I wouldn't vote for this to be included quite yet.

---

### Post by plun on 2008-09-10
PulseAudio  0.9.12 within TheMusos test ppa :)

Upstream release notes
[http://pulseaudio.org/milestone/0.9.12](http://pulseaudio.org/milestone/0.9.12)

Testing...!

---

### Post by jfernyhough on 2008-09-10
Hm... those 0.9.12 updates killed my PA. His 0.9.11 worked fine...

--edit

There might have been some residual crap from Alpha4 - I did a clean Alpha5 install and upgrade and it seems to be working fine...

--edit

Hmm... with the default config PA doesn't see my soundcard but is instead outputting to null-device. I'll try cleaning my ~/.asoundconf. and restarting X, seeing as I get the GDM logon sound.

---

### Post by plun on 2008-09-10
Yup... stone dead...:)  rejected to load alsa-sink also several permission problem.

New update 2 hours ago.

[https://launchpad.net/~themuso/+archive](https://launchpad.net/~themuso/+archive)

I then removed   /home/username/.pulse

Also a .pulse-cookie  within /home

Then started with  

```
pulseaudio -k; sleep 4; pulseaudio -vv
```


 :guitar:

---

### Post by jfernyhough on 2008-09-10
For me, cleaning .asoundconf worked a treat. Back running now with the last (2hr) updates.

---

### Post by plun on 2008-09-10
> **jfernyhough said:**
> For me, cleaning .asoundconf worked a treat. Back running now with the last (2hr) updates.

Yup...:)

All "scratches" when switching between sound sources seems fixed.

This bug includes some tests...

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/262326](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/262326)

---

### Post by BwackNinja on 2008-09-14
pulseaudio 0.9.12, the first release that I know of where I get good audio with vlc. Putting the file input buffer at 750 ms I get perfect sound (verified with no messages on the terminal) in previous releases I had to put it to 10000 (yes, 10 seconds) to get it to play perfectly. They've gotta be doing something right. 'Glitch Free' pulseaudio is now becoming free of glitches.

---

### Post by zombiepig on 2008-09-14
As far as I know, it's not directly pulseaudio - related, but since this thread is about improving the sound experience in intrepid, it seems like a good place to try and figure out [258703]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703") (all the items on the sound selection tab in sound preferences are disabled).

From the comments in the bug report, it seems like there's a few steps we need to do to fix this problem.

Firstly, we need to change the ubuntu sound theme into a proper freedesktop compliant theme. It needs to follow this spec: 
[http://0pointer.de/public/sound-theme-spec.html](http://0pointer.de/public/sound-theme-spec.html)
This theme needs to be installed to /usr/share/sounds. (I'm willing to have a go at creating the theme from the current ubuntu sound effects.)

Secondly, we need to make sure these sounds actually apply - and from my reading, I think ubuntu needs to follow the instructions in this mailing list post from the creator of libcanberra:
[https://tango.0pointer.de/pipermail/libcanberra-discuss/2008-July/000021.html](https://tango.0pointer.de/pipermail/libcanberra-discuss/2008-July/000021.html)

Quoting this post:
```
Packagers!

If you package libcanberra, make sure to include a script like this
one in your package:

<snip>
#!/bin/sh

if [ -z "$GTK_MODULES" ] ; then
        GTK_MODULES="libcanberra-gtk-module"
else
        GTK_MODULES="$GTK_MODULES:libcanberra-gtk-module"
fi

export GTK_MODULES
</snip>

This script should be sourced in each Gnome session and will enable
the libcanberra gtk module for all gtk programs.

In fedora we install it as "libcanberra-gtk-module.sh" in
/etc/X11/xinit/xinitrc.d/. I assume other distributions have similar
directories.

```

I'm struggling to get this part to work properly, although on launchpad user hggdh managed to make it work by placing the script in /etc/X11/xinit/xinitrc

At the moment, it seems rather silly that all the sound preferences are disabled, and it's definitely going to be a valid criticism users/reviewers will find with intrepid. Let's see if we can come up with a solution for it! :D

---

### Post by plun on 2008-09-15
> **BwackNinja said:**
> pulseaudio 0.9.12, the first release that I know of where I get good audio with vlc. Putting the file input buffer at 750 ms I get perfect sound (verified with no messages on the terminal) in previous releases I had to put it to 10000 (yes, 10 seconds) to get it to play perfectly. They've gotta be doing something right. 'Glitch Free' pulseaudio is now becoming free of glitches.

Yup... it works just great now after a few updates.

Luke seems to have nailed some trouble and the challenge for me is what is default settings.

@zombiepig, thanks for pointing this out, maybe a ping (add to a PA bug) to Luke and pulseaudio is needed ?  "Left hand doesnt know what right hand is doing"...:)

---

### Post by Slug71 on 2008-09-15
I cant seem to get Pulseaudio updated with Lukes PPA.
I get the Partial Upgrade pop-up and then get this:

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

libpulsecore7
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-gconf
pulseaudio-module-hal
pulseaudio-module-x11

---

### Post by psyke83 on 2008-09-15
> **Slug71 said:**
> I cant seem to get Pulseaudio updated with Lukes PPA.
I get the Partial Upgrade pop-up and then get this:

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

libpulsecore7
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-gconf
pulseaudio-module-hal
pulseaudio-module-x11

Packages from a PPA are supposed to be unauthenticated, that's normal. Make sure that you read Luke's original announcement, especially regarding bug reporting.

---

### Post by psyke83 on 2008-09-15
> **BwackNinja said:**
> pulseaudio 0.9.12, the first release that I know of where I get good audio with vlc. Putting the file input buffer at 750 ms I get perfect sound (verified with no messages on the terminal) in previous releases I had to put it to 10000 (yes, 10 seconds) to get it to play perfectly. They've gotta be doing something right. 'Glitch Free' pulseaudio is now becoming free of glitches.

Unfortunately I'm still experiencing stutter. You're using the VLC ALSA backend with the PulseAudio ALSA plugins enabled, right?

You may not be experiencing stutter due to resampling (or a lack thereof). The PulseAudio server uses a sampling rate of 44100Hz. If you play content at the same rate, there's no resampling; but if you play content at a different rate, then it uses the "speex-float-3" resample method, which causes increased CPU and perhaps stuttering. I'll have to experiment more.

---

### Post by Slug71 on 2008-09-15
> **psyke83 said:**
> Packages from a PPA are supposed to be unauthenticated, that's normal. Make sure that you read Luke's original announcement, especially regarding bug reporting.

I read that but how do i get them to install?

---

### Post by psyke83 on 2008-09-15
> **Slug71 said:**
> I read that but how do i get them to install?

This is something that should be considered essential knowledge for testing the development release: don't allow Partial Upgrades unless you know exactly what you're doing. This is one of the most common problems with users testing the development release (though it's more common closer to the beginning of the development cycle).

Update your sources, then install the "ubuntu-desktop" package to see if it pulls in essential packages. Otherwise you may have a conflict elsewhere that you'll need to resolve manually. Learn to use the command-line tools (aptitude/apt-get).

---

### Post by BwackNinja on 2008-09-15
> **psyke83 said:**
> Unfortunately I'm still experiencing stutter. You're using the VLC ALSA backend with the PulseAudio ALSA plugins enabled, right?

You may not be experiencing stutter due to resampling (or a lack thereof). The PulseAudio server uses a sampling rate of 44100Hz. If you play content at the same rate, there's no resampling; but if you play content at a different rate, then it uses the "speex-float-3" resample method, which causes increased CPU and perhaps stuttering. I'll have to experiment more.

I don't have any form of newest-high-end-computer (an athlon64 3500+ with 1gb ram if you want to know), and I do see the higher cpu usage, but I don't get any stuttering. I still don't get sound using the VLC ALSA backend, I was talking about the PulseAudio output for VLC. That was _terrible_ for me because vlc is my favorite program for playing DVDs. The only way I could get stable audio was to either increase the file buffer to 10s (which is terrible to even try to call that a solution, imagine waiting 10s for stuff to start or pause after you press the button) or use the oss output with padsp (which seems even worse to me with native pulseaudio output for vlc _anyway_). My sound card only supports 48000Hz, so I always have to resample, and by default pulseaudio matches the rate that ALSA has.

---

### Post by psyke83 on 2008-09-15
Hey everyone,

I've updated Flash to the latest RC(2) release, it's in my PPA.

I've also made an update to this guide - basically, I've consolidated the information to ensure that users enable both Luke's and my own PPA, and set the appropriate configuration for PulseAudio.

Anyone who previously followed this guide will only need to update their /etc/sources.list and upgrade; and for 64 bit users, ensure they have installed the appropriate 32bit libraries via Getlibs (to get Flash working).

Please everyone, test!

---

### Post by Nullack on 2008-09-16
Awesome. Conn your doing some really great work mate.

Im getting with testing :)

Though, I have a strong view we need this into Intrepid. I'm sure we can all help with a freeze exception rationale.

The period for a PPA shouldnt be long at all and not involve more than a basic smoke test in this case.

---

### Post by Nullack on 2008-09-16
Bit of a test report on AMD64:

This URL:

[http://labs.adobe.com/technologies/flashplayer10/demos/](http://labs.adobe.com/technologies/flashplayer10/demos/)

Still doesnt show the interactive flash thing properly like on my partner's MacBook on OSX running the latest flash 10. However, its probably an Adobe linux flash 10 problem. Generally though flash is better.

On the PPA's I get the expected no auth warning due to not getting you blokes' keys but I also get 404s on muso;s ppa:

W: Failed to fetch [http://ppa.launchpad.net/TheMuso/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/TheMuso/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/TheMuso/ubuntu/dists/intrepid/main/source/Sources.gz](http://ppa.launchpad.net/TheMuso/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found

Its time to get this stuff into Intrepid in my view :)

Con can you update your PPA please - Adobe have released a new flash on Sept 15.

---

### Post by psyke83 on 2008-09-16
> **Nullack said:**
> Bit of a test report on AMD64:

This URL:

[http://labs.adobe.com/technologies/flashplayer10/demos/](http://labs.adobe.com/technologies/flashplayer10/demos/)

Still doesnt show the interactive flash thing properly like on my partner's MacBook on OSX running the latest flash 10. However, its probably an Adobe linux flash 10 problem. Generally though flash is better.

On the PPA's I get the expected no auth warning due to not getting you blokes' keys but I also get 404s on muso;s ppa:

W: Failed to fetch [http://ppa.launchpad.net/TheMuso/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/TheMuso/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/TheMuso/ubuntu/dists/intrepid/main/source/Sources.gz](http://ppa.launchpad.net/TheMuso/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found

Its time to get this stuff into Intrepid in my view :)

Con can you update your PPA please - Adobe have released a new flash on Sept 15.

Hmm, that's odd. Perhaps the archive is case-sensitive; I mistakenly wrote "/TheMuso/" when it was in fact "/themuso/" - I've updated the post. Try adjusting your sources.list and updating again.

The latest Flash in my PPA is the one from September 15th. It still needs some manual installation of libraries for 64 bit users, don't forget.

---

### Post by Nullack on 2008-09-16
Thanks, the case sensitivity fixed the 404.

Conn I saw you had an update in your PPA for flash - whats new in 2?

I can confirm Ive installed all the libs.

[http://labs.adobe.com/technologies/flashplayer10/demos/](http://labs.adobe.com/technologies/flashplayer10/demos/) still isnt right.

Also some pulse issues:

Sep 16 20:35:00 PPP pulseaudio[6163]: main.c: High-priority scheduling enabled in configuration but not allowed by policy.
Sep 16 20:35:00 PPP pulseaudio[6163]: core-util.c: setpriority(): Permission denied
Sep 16 20:35:00 PPP pulseaudio[6163]: ltdl-bind-now.c: Failed to find original dlopen loader.
Sep 16 20:35:00 PPP pulseaudio[6175]: main.c: High-priority scheduling enabled in configuration but not allowed by policy.
Sep 16 20:35:00 PPP pulseaudio[6175]: core-util.c: setpriority(): Permission denied
Sep 16 20:35:00 PPP pulseaudio[6175]: ltdl-bind-now.c: Failed to find original dlopen loader.

Though its ready for Intrepid, its an improvement over stock.

---

### Post by plun on 2008-09-16
Working just fine !  Thanks

I still got some off these from time to time.

> D: protocol-native.c: Requesting rewind due to end of underrun.
D: module-alsa-sink.c: Requested to rewind 65536 bytes.
D: module-alsa-sink.c: Mhmm, actually there is nothing to rewind.
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
I: module-alsa-sink.c: Underrun!
D: module-rtp-recv.c: Checking for dead streams ...



PulseAudio seems to be very CPU sensitive and I have the same issue with enabling High-Priority scheduling... is a RT kernel needed ?

Nevertheless sound must be a priority process....:)  otherwise turn it off.

---

### Post by ScislaC on 2008-09-16
Okay... I initially posted a Flash issue to another thread and Psyke83 said it would be better discussed here. The last piece from that thread which contains the description in a quote is [HERE]("http://ubuntuforums.org/showthread.php?p=5802125#post5802125").

Now in response to that...

Psyke83:
I'm on Intrepid and using FF 3.0.2 and do not have FF2 installed. And yes, libnss3-1d is installed. Anything else you'd like for me to check next?

---

### Post by psyke83 on 2008-09-16
> **ScislaC said:**
> Okay... I initially posted a Flash issue to another thread and Psyke83 said it would be better discussed here. The last piece from that thread which contains the description in a quote is [HERE]("http://ubuntuforums.org/showthread.php?p=5802125#post5802125").

Now in response to that...

Psyke83:
I'm on Intrepid and using FF 3.0.2 and do not have FF2 installed. And yes, libnss3-1d is installed. Anything else you'd like for me to check next?

Are you using 64bit? Refer to the actual guide in this thread (post #1) - your problem is most likely missing 32 bit libraries. This should be fixed in an official capacity soon, but you can use GetLibs to manually install these 32 bit libraries in the meantime.

---

### Post by ScislaC on 2008-09-16
> **psyke83 said:**
> Are you using 64bit?

Nope... 32bit.

---

### Post by psyke83 on 2008-09-16
> **ScislaC said:**
> Nope... 32bit.

Take a look at the following links: 
[http://packages.ubuntu.com/search?searchon=contents&keywords=libnss3.so&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libnss3.so&mode=exactfilename&suite=intrepid&arch=any)
[http://packages.ubuntu.com/search?searchon=contents&keywords=libsmime3.so&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libsmime3.so&mode=exactfilename&suite=intrepid&arch=any)
[http://packages.ubuntu.com/search?searchon=contents&keywords=libssl3.so&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libssl3.so&mode=exactfilename&suite=intrepid&arch=any)

If you have firefox-2, komposer, seamonkey-browser or thunderbird, please temporarily uninstall these packages, and reinstall libnss3-dev.

Be warned: if you fail to uninstall the above packages, libnss3-dev will not install as those packages mark themselves as "Provides" and create symlinks to those libraries. The problem is that the versions in those packages are not compatible with Flash.

---

### Post by ScislaC on 2008-09-16
Problem resolved... when looking through my "local" packages list it listed libnss3-1d, so I forced the version to the intrepid one and it is now working. Thank you for your time and patience Psyke83!

---

### Post by Nullack on 2008-09-16
Psyke, can I ask please that while your PPA is ahead of Intrepid you give us testers a brief changelog of whats happening? This will help to focus the test design on changes. I note weve had 2 and 3 come through recently.

Alexander's view is to synch following A6.

---

### Post by psyke83 on 2008-09-17
> **Nullack said:**
> Psyke, can I ask please that while your PPA is ahead of Intrepid you give us testers a brief changelog of whats happening? This will help to focus the test design on changes. I note weve had 2 and 3 come through recently.

Alexander's view is to synch following A6.

I've been in touch with Alexander. As for the package in my PPA, revisions ~ppa2 and ~ppa3 had very minor changes to adjust the depends on nspluginwrapper, which only affected the build for Hardy.

The ia32-libs package has been updated ([bug #246911)]("https://bugs.launchpad.net/bugs/246911"), so the official flashplugin-nonfree should be uploaded soon.

What problems are you having with the flashplugin-nonfree package?

---

### Post by Nullack on 2008-09-17
Thats great Psyke83 :)

I dont think any of the flash issues Ive found are packaging problems - I think its a code problem in the plugin.

People can test this by going to this URL:

[http://labs.adobe.com/technologies/flashplayer10/demos/](http://labs.adobe.com/technologies/flashplayer10/demos/)

And here on youtube what its supposed to look like:

[http://www.youtube.com/watch?v=NCLDtS1SUZ8](http://www.youtube.com/watch?v=NCLDtS1SUZ8)

---

### Post by psyke83 on 2008-09-18
> **Nullack said:**
> Thats great Psyke83 :)

I dont think any of the flash issues Ive found are packaging problems - I think its a code problem in the plugin.

People can test this by going to this URL:

[http://labs.adobe.com/technologies/flashplayer10/demos/](http://labs.adobe.com/technologies/flashplayer10/demos/)

And here on youtube what its supposed to look like:

[http://www.youtube.com/watch?v=NCLDtS1SUZ8](http://www.youtube.com/watch?v=NCLDtS1SUZ8)

You're correct, it's not a problem in the packaging or any components of Ubuntu. The Linux version of the plugin simply doesn't have 100% feature parity with the Windows version yet, I suspect. Nevertheless, RC2 is a vast improvement over Flash 9 and the other Flash 10 previews.

---

### Post by psyke83 on 2008-09-18
Hi everyone,

Just to keep you apprised... ;)

For 64-bit users: ia32-libs has been updated to include the necessary libraries for the latest release of Flash - this means that GetLibs is no longer necessary. As well as that, the (32-bit) "libflashsupport" library has been completely removed from this package, as it's been known to cause crashes for a long time.

Everyone else: the flashplugin-nonfree package should get updated soon, pending review and approval from the MOTU team.

As for PulseAudio, it seems we won't be getting 0.9.12 in time for release (too many bugs). However, work is being done to ensure that the default ALSA device is set to PulseAudio in Intrepid; this change alone will fix a *lot* of problems.

---

### Post by BwackNinja on 2008-09-18
It may be related to pulseaudio, but I don't think that alsa is closing properly. I have to force-reload (not just reload or restart alsa) to be able to use either alsa or pulseaudio output to alsa. Any ideas?

---

### Post by psyke83 on 2008-09-18
> **BwackNinja said:**
> It may be related to pulseaudio, but I don't think that alsa is closing properly. I have to force-reload (not just reload or restart alsa) to be able to use either alsa or pulseaudio output to alsa. Any ideas?

That would be an ALSA/kernel issue, I imagine. Have you tried something simpler, such as restarting PulseAudio?

```
$ pulseaudio -k && pulseaudio
```

---

### Post by psyke83 on 2008-09-18
Hi,

With the latest updates, Flash should work for amd64 users without the need for GetLibs; I've updated the guide to reflect this.

Can I ask anyone that's got a 64 bit machine to offer feedback on the stability of Flash from my PPA? Do you observe any Firefox crashes or Flash content "disappearing"?

Flash 10 will hit the official repositories soon, and there may be further problems that need ironing out (within nspluginwrapper).

---

### Post by BwackNinja on 2008-09-18
> **psyke83 said:**
> That would be an ALSA/kernel issue, I imagine. Have you tried something simpler, such as restarting PulseAudio?

```
$ pulseaudio -k && pulseaudio
```

I have tried that, though it doesn't change anything. PulseAudio itself _is_ working, its just that it lacks any connection to hardware, aka an alsa pcm. I have a multicast rtp sink loaded and available there and shown in pavucontrol, but the alsa device says it is 'busy' whenever I restart pulseaudio. A restart of alsa through a simple "sudo /etc/init.d/alsa restart" restarts alsa, but the problem persists. Doing an
```
 alsa force-reload 
``` will make it appear even without restarting pulseaudio. But it won't otherwise appear and anything trying to route itself through alsa doesn't work either, not even a simple speaker test with the device specified (so it doesn't default to pulse).

---

### Post by roger99 on 2008-09-18
> **psyke83 said:**
> Hi,

With the latest updates, Flash should work for amd64 users without the need for GetLibs; I've updated the guide to reflect this.

Can I ask anyone that's got a 64 bit machine to offer feedback on the stability of Flash from my PPA? Do you observe any Firefox crashes or Flash content "disappearing"?

Flash 10 will hit the official repositories soon, and there may be further problems that need ironing out (within nspluginwrapper).

Well, personally, i followed your updated guide using the ppa repo's etc, now every single bit of flash content I try to view crashes, rather it disappears leaving a gray box in it place.  Subsequently skype no longer loads either, not finding libQtDBus.so even though it is installed on my system.  Not sure whats causing the flash problem, I know I get 8 or nine instances of npviewer.bin running everytime flash content is loaded and I cannot kill them until I quit firefox.

---

### Post by psyke83 on 2008-09-18
> **roger99 said:**
> Well, personally, i followed your updated guide using the ppa repo's etc, now every single bit of flash content I try to view crashes, rather it disappears leaving a gray box in it place.  Subsequently skype no longer loads either, not finding libQtDBus.so even though it is installed on my system.  Not sure whats causing the flash problem, I know I get 8 or nine instances of npviewer.bin running everytime flash content is loaded and I cannot kill them until I quit firefox.

Let's put aside Skype for a moment...

I've been testing with the i386 build of nspluginwrapper and noticed crashes as well, but it's caused by PulseAudio 0.9.12 on my system. Try to downgrade to Intrepid's version of PulseAudio:

1. Comment/delete TheMuso's repositories in your /etc/apt/sources.list

2. Downgrade packages:

[COLOR="Red"]Big Fat Warning: *please* be careful and check the output to ensure that no vital packages are uninstalled. I'm **not** taking responsiblity for half your system being removed, so verify the removed packages before you continue.

NOTE 1: This procedure should *only* elect to remove libpulsecore7, and install a "NEW" package, libpulsecore5 - do not proceed unless you're happy this is the case.
NOTE 2: When prompted, please choose "y" to install the package maintainer's version of any configuration files.[/COLOR]
```
$ sudo apt-get update
$ sudo apt-get install gstreamer0.10-pulseaudio/intrepid libao-pulse/intrepid libpulse-browse0/intrepid libpulse-mainloop-glib0/intrepid libpulse0/intrepid libsdl1.2debian-pulseaudio/intrepid pulseaudio/intrepid pulseaudio-esound-compat/intrepid pulseaudio-module-gconf/intrepid pulseaudio-module-hal/intrepid pulseaudio-module-x11/intrepid pulseaudio-module-zeroconf/intrepid pulseaudio-utils/intrepid vlc-plugin-pulse/intrepid libpulsecore5/intrepid padevchooser/intrepid pavucontrol/intrepid libasound2/intrepid libasound2-plugins/intrepid
```

3. Assuming the packages were downgraded correctly, reboot.

4. When you've rebooted, launch Firefox. Open two random Youtube pages and play the videos, then right-click on one of them and click "About Flash". 

If Flash continues working, that's a good sign ;)

---

### Post by BwackNinja on 2008-09-18
Figured it out, mpd is the culprit though it worked fine before and I don't remember it being updated recently. I can't tell why it isn't using the pulseaudio output like its supposed to (maybe it is being loaded before pulseaudio and the default is alsa, which would make sense, other than the switchup itself).

I don't know whether or not it would be good to file a bug because of my highly irregular install. I think I'll wait to see if someone else has the same problem first. I guess I'm booting up with no usplash for a quick check next time :P.

---

### Post by roger99 on 2008-09-18
> **psyke83 said:**
> 

[COLOR="Red"]Big Fat Warning:[/COLOR]



lol, no worries, i quite like trashing my system, makes things that little bit more interesting and there's no-one else to blame but myself seeing as I'm the one who decided to run an alpha OS  :)

Although, i'm gonna leave it until tomorrow as i'm half asleep right now.  When i know the outcome of the downgrade etc I'll post again and let you know if it worked.  Cheers for the quick late/early reply by the way.

---

### Post by psyke83 on 2008-09-18
> **BwackNinja said:**
> Figured it out, mpd is the culprit though it worked fine before and I don't remember it being updated recently. I can't tell why it isn't using the pulseaudio output like its supposed to (maybe it is being loaded before pulseaudio and the default is alsa, which would make sense, other than the switchup itself).

I don't know whether or not it would be good to file a bug because of my highly irregular install. I think I'll wait to see if someone else has the same problem first. I guess I'm booting up with no usplash for a quick check next time :P.

MPD is a special-case that needs configuring to work with PulseAudio. See: [http://www.pulseaudio.org/wiki/PerfectSetup#MPD](http://www.pulseaudio.org/wiki/PerfectSetup#MPD)

---

### Post by BwackNinja on 2008-09-18
> **psyke83 said:**
> MPD is a special-case that needs configuring to work with PulseAudio. See: [http://www.pulseaudio.org/wiki/PerfectSetup#MPD](http://www.pulseaudio.org/wiki/PerfectSetup#MPD)

Right, and I have it configured like that. I have only started experiencing this problem in the last few days and I even double-checked my mpd.conf to make sure that didn't change. Everything checks out, but the problem remains. It even goes through PulseAudio when it (mpd) is restarted. That's why I think its a load order issue.

---

### Post by psyke83 on 2008-09-18
> **BwackNinja said:**
> Right, and I have it configured like that. I have only started experiencing this problem in the last few days and I even double-checked my mpd.conf to make sure that didn't change. Everything checks out, but the problem remains. It even goes through PulseAudio when it (mpd) is restarted. That's why I think its a load order issue.

I can imagine therefore: if MPD is launched before the PulseAudio server is running, it falls back to ALSA. When PulseAudio subsequently attempts to launch, it finds the sound card locked (by MPD)...

---

### Post by plun on 2008-09-19
> **psyke83 said:**
> 

If Flash continues working, that's a good sign ;)

Yup it does after downgrade....:^o

I also unchecked your repos and cleaned out /.pulse

Rock solid
```
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
```
[B]
No underruns[/B] which I got with 9.0.12 from time to time.

Small cracklings are back when switching between sources.

This event between every played title

```
D: memblock.c: Memory block too large for pool: 17640 > 16376
```



Another strange issue is how front/rear audio out is controlled  :confused:

Where is channel mapping stored ?

---

### Post by Nullack on 2008-09-19
Good point Plun, and mate I dont understand it either.

How do I tell pulse/alsa whatever how many speakers I want everything mixed too? And to downsample different channells so they sound right in lesser numbers of speakers.

I note totem has a preference for how many speakers for output but thats not the whole story.

---

### Post by plun on 2008-09-19
> **Nullack said:**
> Good point Plun, and mate I dont understand it either.

How do I tell pulse/alsa whatever how many speakers I want everything mixed too? And to downsample different channells so they sound right in lesser numbers of speakers.

I note totem has a preference for how many speakers for output but thats not the whole story.

Well.. I was lost in "the Google jungle" finding out....


Testing Pulseaudio  :lolflag:, I had a broken MS-Soundsystem which I fixed but rear/front remains.

(Low quality mobile photo)

[[img]http://ubuntu-pics.de/thumb/3417/dsc00077_02x8x9.jpg[/img]](http://ubuntu-pics.de/bild/3417/dsc00077_02x8x9.jpg)

:D

---

### Post by plun on 2008-09-19
Annoying Pulseaudio... but it must be overcomed  :)

Clean Alpha 6 install but /home on a separate partition.
Deleted all gnome/gconf settings folders also other files before install.

Installed Alpha 6

Installed padevchooser and all other PA packages follows

Started PA device chooser and no permission for anything.

No permission for restarting or kill PA

The file **/.esd_auth** was belonging to root.

Changed it to user owned and everything works.

Can someone more confirm/check this ?

---

### Post by BwackNinja on 2008-09-19
I think I found the problem. Pulseaudio (at least in 0.9.12) now seems not to be configured as a system-wide daemon anymore. The file in /etc/init.d/pulseaudio relies on /etc/default/pulseaudio which dictates whether it is used as a system-wide daemon and whether it will support module loading. It is set not to be a system-wide daemon (which inherently breaks mpd) which makes the file in /etc/init.d/ not do anything at all, not even display "starting pulseaudio" or "stopping pulseaudio". 

I changed that config file, not hard. Somehow though, some other pulseaudio instances are running _before_ the one in /etc/init.d/ can start and don't have the right options, thus blocking it and stopping mpd from being connected to pulseaudio, so it is connected to alsa instead.

Why can't any problems just be simple? I bet I'm still missing a piece of the puzzle.

---

### Post by psyke83 on 2008-09-19
> **BwackNinja said:**
> I think I found the problem. Pulseaudio (at least in 0.9.12) now seems not to be configured as a system-wide daemon anymore. The file in /etc/init.d/pulseaudio relies on /etc/default/pulseaudio which dictates whether it is used as a system-wide daemon and whether it will support module loading. It is set not to be a system-wide daemon (which inherently breaks mpd) which makes the file in /etc/init.d/ not do anything at all, not even display "starting pulseaudio" or "stopping pulseaudio". 

I changed that config file, not hard. Somehow though, some other pulseaudio instances are running _before_ the one in /etc/init.d/ can start and don't have the right options, thus blocking it and stopping mpd from being connected to pulseaudio, so it is connected to alsa instead.

Why can't any problems just be simple? I bet I'm still missing a piece of the puzzle.

Since Hardy, PulseAudio hasn't been configured as a system-wide daemon (though IMHO, it should have).

---

### Post by markbuntu on 2008-09-19
Will the pulse-jack module be avilable in Intrepid or will I still have to get it from debian?

---

### Post by psyke83 on 2008-09-19
> **markbuntu said:**
> Will the pulse-jack module be avilable in Intrepid or will I still have to get it from debian?

The probability is very high that Intrepid won't get any updates to PulseAudio at all (just some tweaks to the buffering settings, and to enable the ALSA plugins by default).

You should be looking on Launchpad: 
[https://bugs.launchpad.net/ubuntu/+bug/198048](https://bugs.launchpad.net/ubuntu/+bug/198048)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/109659](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/109659)

---

### Post by plun on 2008-09-20
I filed a bug about esd_auth
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/272402](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/272402)

Upgrade to 0.9.12 again... its better despite of some bugs, at least for me.

---

### Post by psyke83 on 2008-09-20
64 bit users: I pushed through an update for nspluginwrapper (1.1.0-0ubuntu3~ppa1). Unfortunately nspluginwrapper doesn't support windowless mode correctly in the latest version of flash, causing frequent crashes for many people. This update disables windowless mode support, which should solve those crashes. Let me know the results!

P.S. This will be an official update after the beta release, unless there's a compatibility update to nspluginwrapper or flash.

---

### Post by plun on 2008-09-20
More findings...

```
D: sink-input.c: Have to rewind 452 bytes on render memblockq.
I: sink-input.c: Freeing input 5 "(null)"
I: client.c: Freed 12 "mozillaSound"

```

Great sound after that... mystery

1.18.RC3 and PA 0.9.12...:-\"

---

### Post by plun on 2008-09-20
Well it broke again..."back to the roots"

Original howto
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

No Equalizer !

Using these values for daemon.conf

no-cpu-limit = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
default-fragments = 8
default-fragment-size-msec = 5
resample-method = speex-float-10


Also found a howto enable front/rear speakers...:)  (psyke83 points to it)


[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)


[[img]http://ubuntu-pics.de/thumb/3457/music_FDqoGh.jpg[/img]](http://ubuntu-pics.de/bild/3457/music_FDqoGh.jpg)

---

### Post by BwackNinja on 2008-09-20
Yea... I'd say that being something so common it really should go somewhere in the gui.

(And don't get me started on what ALSA seems to thing "Master" means...)

---

### Post by bpl07 on 2008-09-21
> **psyke83 said:**
> 64 bit users: I pushed through an update for nspluginwrapper (1.1.0-0ubuntu3~ppa1). Unfortunately nspluginwrapper doesn't support windowless mode correctly in the latest version of flash, causing frequent crashes for many people. This update disables windowless mode support, which should solve those crashes. Let me know the results!

P.S. This will be an official update after the beta release, unless there's a compatibility update to nspluginwrapper or flash.

Still not working for me, do you need to disable windowless mode in flash too?

---

### Post by psyke83 on 2008-09-21
> **bpl07 said:**
> Still not working for me, do you need to disable windowless mode in flash too?

It shouldn't be necessary.

Run Firefox from a terminal and visit a site with Flash content, then paste the terminal output, please.

---

### Post by bpl07 on 2008-09-21
I got it working by downgrading ia32-libs to 2.2ubuntu11 and reinstalling the necessary libraries for flash rc2 with getlibs.  For me, I think the issue was ia32-libs.

---

### Post by psyke83 on 2008-09-21
> **bpl07 said:**
> I got it working by downgrading ia32-libs to 2.2ubuntu11 and reinstalling the necessary libraries for flash rc2 with getlibs.  For me, I think the issue was ia32-libs.

Ok, but it needs to be fixed officially (without downgrading packages or using getlibs).

---

### Post by croxis on 2008-09-21
FINALLY! Pulseaudio just works with this!  Thank you to those who contributed to the repository and the fixes!

---

### Post by no1wantdthisname on 2008-09-21
Anyone get flash working on 64bit?
It's just a gray box.

I'm getting this in the terminal:

```

GCJ PLUGIN: thread 0x1af0840: NP_GetValue
GCJ PLUGIN: thread 0x1af0840: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x1af0840: NP_GetValue return
GCJ PLUGIN: thread 0x1af0840: NP_GetValue
GCJ PLUGIN: thread 0x1af0840: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x1af0840: NP_GetValue return

```

This in kern.log
```

npviewer.bin[8599]: segfault at 0 ip 0000000000000000 sp 00000000ff97ccec error 14 in npviewer.bin[8048000+1a000]

```

This in user.log
```

pulseaudio[5521]: module-always-sink.c: Unable to load module-null-sink
pulseaudio[7460]: ltdl-bind-now.c: Failed to find original dlopen loader.
pulseaudio[7462]: module-alsa-sink.c: Increasing wakeup watermark to 40.00 ms

```

---

### Post by psyke83 on 2008-09-21
> **no1wantdthisname said:**
> Anyone get flash working on 64bit?
It's just a gray box.

Thanks for posting the output. Can you try downgrading the PulseAudio packages from TheMuso's repository (but keep mine enabled), and see if it helps?
[http://ubuntuforums.org/showpost.php?p=5816338&postcount=93](http://ubuntuforums.org/showpost.php?p=5816338&postcount=93)

---

### Post by darkxman on 2008-09-21
> **Slug71 said:**
> I cant seem to get Pulseaudio updated with Lukes PPA.
I get the Partial Upgrade pop-up and then get this:

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

libpulsecore7
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-gconf
pulseaudio-module-hal
pulseaudio-module-x11
Had the same problem. I just used Synaptic Package Manager instead of Update Manager. Hit Mark All Upgrades and then Apply. Those packages installed just fine then.

---

### Post by no1wantdthisname on 2008-09-21
> **psyke83 said:**
> Thanks for posting the output. Can you try downgrading the PulseAudio packages from TheMuso's repository (but keep mine enabled), and see if it helps?
[http://ubuntuforums.org/showpost.php?p=5816338&postcount=93](http://ubuntuforums.org/showpost.php?p=5816338&postcount=93)

Same as before.  I used a fresh profile in firefox and even tried epiphany.

kern.log is still showing npviewer segfaulting.

Here is what shows up in user.log after restarting pulseaudio:
```

Sep 21 19:53:13 pulseaudio[18617]: ltdl-bind-now.c: Failed to find original dlopen loader.
Sep 21 19:53:13 pulseaudio[18617]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Sep 21 19:53:13 pulseaudio[18617]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Sep 21 19:53:13 pulseaudio[18617]: shm.c: Invalid shared memory segment size
Sep 21 19:53:13 pulseaudio[18617]: shm.c: Invalid shared memory segment size

```

---

### Post by plun on 2008-09-22
Findings...

Can anyone check this with Alsa 1.17  ?   (I am testing 1.18RC  )

Segfault.

```
Sep 22 16:07:59 plun kernel: [   19.969751] EMU10K1_Audigy 0000:00:08.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep 22 16:07:59 plun kernel: [   19.973384] ALSA /home/plun/Desktop/alsa/alsadriver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1546: Installing spdif_bug patch: Audigy 2 Platinum [SB0240P]
Sep 22 16:07:59 plun kernel: [   20.077092] input: ImPS/2 Generic Wheel Mouse as /class/input/input5
Sep 22 16:07:59 plun kernel: [   20.134289] alsactl[3374]: segfault at 0 ip b7eb8263 sp bfae18dc error 4 in libc-2.8.90.so[b7e41000+158000]
Sep 22 16:07:59 plun kernel: [   20.136244] alsactl[3399]: segfault at 0 ip b7d4d263 sp bff753ac error 4 in libc-2.8.90.so[b7cd6000+158000]
Sep 22 16:07:59 plun kernel: [   20.137236] alsactl[3397]: segfault at 0 ip b7d12263 sp bfb39f6c error 4 in libc-2.8.90.so[b7c9b000+158000]
Sep 22 16:07:59 plun kernel: [   20.139941] alsactl[3401]: segfault at 0 ip b7e62263 sp bfa89ebc error 4 in libc-2.8.90.so[b7deb000+158000]
Sep 22 16:07:59 plun kernel: [   20.961104] alsactl[3736]: segfault at 0 ip b7ed4263 sp bfefcb3c error 4 in libc-2.8.90.so[b7e5d000+158000]
Sep 22 16:07:59 plun kernel: [   20.963249] alsactl[3737]: segfault at 0 ip b7ea5263 sp bffcfbfc error 4 in libc-2.8.90.so[b7e2e000+158000]
Sep 22 16:07:59 plun kernel: [   20.965282] alsactl[3738]: segfault at 0 ip b7dc8263 sp bf9f1e2c error 4 in libc-2.8.90.so[b7d51000+158000]
Sep 22 16:07:59 plun kernel: [   20.967134] alsactl[3739]: segfault at 0 ip b7ecb263 sp bfcf511c error 4 in libc-2.8.90.so[b7e54000+158000]
```

Also got USB audio output working with kernel  -4  :)

---

### Post by amano on 2008-09-22
I just tested it as well. It ironed out all issues that I had for a long time (e.g. crackling in rhythmbox, I just had to set everything to pulseaudio within Settings--> Sound). I just had to figure out that it didn't default to using all 6 channels but to just 2 channels by default. And by researching this, I found a solution for a very longstanding problem (strong hissing on the subwoofer channel with my  SoundBlaster Live 5.1 (SB0060) as well (though probably not related to pulseaudio as well).


[[Just for later reference: I found a checkbox that can be added in the alsamixer applet: It's called "Sigmatel 4-Speaker Stereo" which probably is not the perfect solution but lets me use my subwoofer with Linux finally]]

---

### Post by douilley on 2008-09-22
Hello, i just upgraded to 8.10 and I cant get any sound out of my computer. Whatever the entry (alsa oss default pulse) I pick in the sound manager, whatever the player i use, there's nothing. I can't access to the gnome system sound in the sound parameters (they're in grey / not click able). Pulse audio is the only card detected when I use alsamixer: this seems strange. However, pulse detects when I play a sound (any player) with the volume meter, but it seems not to reach my headset - which is correctly plugged in, that would have been too easy)
Anyway, i get this error when i type "pulseaudio" in a terminal:
```
W: ltdl-bind-now.c: Failed to find original dlopen loader.
```
A friend of mine told me it could be alsa failing but it seems properly installed too. 
I tried the fixes from the first topic page, as i dont have any idea where the problem comes from, but there was no use.
Any ideas ?

---

### Post by BwackNinja on 2008-09-22
> **douilley said:**
> Hello, i just upgraded to 8.10 and I cant get any sound out of my computer. Whatever the entry I pick in the sound manager, whatever the player i use, there's nothing. I can't access to the gnome system sound in the sound parameters (they're in grey / not click able). Pulse audio is the only card detected when I use alsamixer: this seems strange. However, pulse detects when I play a sound (any player) with the volume meter, but it seems not to reach my headset - which is correctly plugged in, that would have been too easy)
Anyway, i get this error when i type "pulseaudio" in a terminal:
```
W: ltdl-bind-now.c: Failed to find original dlopen loader.
```
A friend of mine told me it could be alsa failing but it seems properly installed too. 
I tried the fixes from the first topic page, as i dont have any idea where the problem comes from, but there was no use.
Any ideas ?

Not an error, just a warning. Its unrelated. As you said, its probably ALSA problems, especially considering that you can't get sound from that in when you switch to it in sound properties. Not being able access system sound is a known issue, and unrelated. Which audio chipset do you have? It might help in finding a solution.

---

### Post by douilley on 2008-09-22
> Not an error, just a warning. Its unrelated. As you said, its probably ALSA problems, especially considering that you can't get sound from that in when you switch to it in sound properties. Not being able access system sound is a known issue, and unrelated. Which audio chipset do you have? It might help in finding a solution.
I have an audigy2 platinium (emu2k something). Should I open a topic in the right section and stop posting here ?

---

### Post by BwackNinja on 2008-09-22
No need to repost somewhere else, this is an intrepid problem.

Bug report here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/259017](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/259017)

and it has a fix.

Have fun in intrepid!

---

### Post by douilley on 2008-09-22
> **BwackNinja said:**
> No need to repost somewhere else, this is an intrepid problem.

Bug report here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/259017](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/259017)
and it has a fix.
Have fun in intrepid!
I dont know why my alsamixer was locked to only one card (pulse) but now it shows the audigy and i could finally unmute it. Thanks alot :)

---

### Post by Gourgi on 2008-09-22
> **amano said:**
> I just tested it as well. It ironed out all issues that I had for a long time (e.g. crackling in rhythmbox, I just had to set everything to pulseaudio within Settings--> Sound). I just had to figure out that it didn't default to using all 6 channels but to just 2 channels by default. And by researching this, I found a solution for a very longstanding problem (strong hissing on the subwoofer channel with my  SoundBlaster Live 5.1 (SB0060) as well (though probably not related to pulseaudio as well).

the solution below was enough to provide me 5.1 sound with equalizer for my soundbaster live! 24bit.
```
gedit ~/.pulse/daemon.conf
```
type in it : 
```

 default-sample-channels = 6

```

here some other relevant files
~/.asoundrc : 
```

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/gourgi/.asoundrc.asoundconf>

```
~/.asoundrc.asoundconf: 
```

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
pcm.!default { type pulse }
ctl.!default { type pulse }

```

**on topic: **
i use this ppa [http://ppa.launchpad.net/themuso/ubuntu](http://ppa.launchpad.net/themuso/ubuntu) for pulse and everything works great! Solid Rock!
i use swfdec 0.8.0-1 for flash playback with pulse 0.9.12
i can use youtube playback,rhythmbox playback and tvtime at the same time without any breakage or problems :D

oh btw, Amd64 here

---

### Post by zombiepig on 2008-09-23
Looks like a bunch of alsa/pulseaudio/libcanberra fixes just got committed. Hopefully these fix a lot of issues :D

---

### Post by plun on 2008-09-23
> **zombiepig said:**
> Looks like a bunch of alsa/pulseaudio/libcanberra fixes just got committed. Hopefully these fix a lot of issues :D

Well... I have perfect sound for the moment including USB output ....:guitar:


psyke83 wrote a downgrade within this message

[http://ubuntuforums.org/showpost.php?p=5816338&postcount=93](http://ubuntuforums.org/showpost.php?p=5816338&postcount=93)

.

---

### Post by zombiepig on 2008-09-23
Well, I'm happy to report that the updates to libcanberra and ubuntu-sounds have fixed the disabled sound preferences problem I mentioned earlier. 

There's still an existing bug that prevents the "window and button" sound effects from working, that's caused by a missing libcanberra-gtk-module in GTK_MODULES. I've filed it as [273507]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507").
Still, a big improvement on before! :)

---

### Post by psyke83 on 2008-09-23
> **zombiepig said:**
> Looks like a bunch of alsa/pulseaudio/libcanberra fixes just got committed. Hopefully these fix a lot of issues :D

They do :). All that's left is a small fix to the PulseAudio configuration (to accommodate Skype), and then to update Flash and nspluginwrapper.

We won't get PA 0.9.12, but that's ok (it's still a bit rough around the edges).

---

### Post by bpl07 on 2008-09-23
> **psyke83 said:**
> Ok, but it needs to be fixed officially (without downgrading packages or using getlibs).

I did some more testing, and I'm convinced that the current ia32-libs has something wrong with it.  With the current version (2.2ubuntu13), no matter what I try I cannot get Flash RC2 (from psyke83's ppa) working.  Installing the library dependencies with getlibs on top of ia32-libs doesn't help either.  However, if I downgrade to the last version (2.2ubuntu11) I can get all versions of flash working by installing the 4 libraries missing from the version.

I don't think it's appropriate for me to file a bug on something that hasn't been released from the ppa yet, but can anyone else on amd64 confirm this issue?  I can make a new thread for this if I need to.

---

### Post by psyke83 on 2008-09-23
> **bpl07 said:**
> I did some more testing, and I'm convinced that the current ia32-libs has something wrong with it.  With the current version (2.2ubuntu13), no matter what I try I cannot get Flash RC2 (from psyke83's ppa) working.  Installing the library dependencies with getlibs on top of ia32-libs doesn't help either.  However, if I downgrade to the last version (2.2ubuntu11) I can get all versions of flash working by installing the 4 libraries missing from the version.

I don't think it's appropriate for me to file a bug on something that hasn't been released from the ppa yet, but can anyone else on amd64 confirm this issue?  I can make a new thread for this if I need to.

This thread is the best place at the moment, no need to start a new one. Using the latest ia32-libs (and no getlibs workarounds), can you post the output of Firefox when run from a terminal? Be sure to try to navigate to a page with Flash content before copy & pasting the output.

---

### Post by bpl07 on 2008-09-23
> **psyke83 said:**
> This thread is the best place at the moment, no need to start a new one. Using the latest ia32-libs (and no getlibs workarounds), can you post the output of Firefox when run from a terminal? Be sure to try to navigate to a page with Flash content before copy & pasting the output.

```
> firefox
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
***** NSPlugin Wrapper *** ERROR: NPP_New() wait for reply: Connection closed**
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x10d7880: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
GCJ PLUGIN: thread 0x10d7880: NP_GetValue
GCJ PLUGIN: thread 0x10d7880: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x10d7880: NP_GetValue return
```

Grey box where flash should be.

---

### Post by bpl07 on 2008-09-23
Same page after downgrading ia32-libs and installing the 4 libraries with getlibs:

```
> firefox
GCJ PLUGIN: thread 0x1408880: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x1408880: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x1408880: NP_GetValue
GCJ PLUGIN: thread 0x1408880: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x1408880: NP_GetValue return
GCJ PLUGIN: thread 0x1408880: NP_GetValue
GCJ PLUGIN: thread 0x1408880: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x1408880: NP_GetValue return
GCJ PLUGIN: thread 0x1408880: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x1408880: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x1408880: NP_GetValue
GCJ PLUGIN: thread 0x1408880: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x1408880: NP_GetValue return
GCJ PLUGIN: thread 0x1408880: NP_GetValue
GCJ PLUGIN: thread 0x1408880: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x1408880: NP_GetValue return
GCJ PLUGIN: thread 0x1408880: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x1408880: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x1408880: NP_GetValue
GCJ PLUGIN: thread 0x1408880: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x1408880: NP_GetValue return
GCJ PLUGIN: thread 0x1408880: NP_GetValue
GCJ PLUGIN: thread 0x1408880: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x1408880: NP_GetValue return
(npviewer.bin:19323): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
***** NSPlugin Viewer  *** ERROR: could not reconstruct XVisual from visualID**
*** NSPlugin Viewer  *** ERROR: could not reconstruct XVisual from visualID
*** NSPlugin Viewer  *** ERROR: could not reconstruct XVisual from visualID
```

Flash works, drop down menus aren't covered up, no crashes yet.

---

### Post by bpl07 on 2008-09-23
One last thing, with your version of nspluginwrapper (windowless mode disabled) videos on sites like [www.comedycentral.com](www.comedycentral.com) work, whereas they don't work with the current version of nspluginwrapper in the repository.  Neither one alleviates the ia32-libs issue though.

---

### Post by bpl07 on 2008-09-23
Not to pile on, but more amd64 users are reporting problems now on this [bug report]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403").

---

### Post by amano on 2008-09-24
> **Gourgi said:**
> the solution below was enough to provide me 5.1 sound with equalizer for my soundbaster live! 24bit.
```
gedit ~/.pulse/daemon.conf
```
type in it : 
```

 default-sample-channels = 6

```

Yes. This was the solution that worked for me as well. It should be hooked up to the Pulseaudio GUI somehow because this way it isn't intuitive.

Really everything is working great for me now with PulseAudio .12

---

### Post by 68pontiac on 2008-09-24
Hello all, I've been watching this thread for a few days and I'm having an issue that I can't seem to resolve. I'm still pretty new with Linux and probably shouldn't be using an Alpha release, but the newest kernel fixes other issues I was having, so I'm sticking with it until the final release. I don't have any sound coming from the machine (but I'm certain the speakers work) and typing "pulseaudio" from the command line returns:

```
W: ltdl-bind-now.c: failed to find original dlopen loader.
E: pid.c: Daemon already running.
W: main.c setrlimit (RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c setrlimit (RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
E: socked-server.c: bind(): Address already in use
E: module.c: Failed to load module "module-esound-protocol-unix" (argument: ""): initilization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
E: pid.c: PID file '/tmp/pulse-christopher/pid' not mine!
```

Any help? Suggestions? Thanks a bunch.

---

### Post by mabovo on 2008-09-24
> **psyke83 said:**
> They do :). All that's left is a small fix to the PulseAudio configuration (to accommodate Skype), and then to update Flash and nspluginwrapper.

We won't get PA 0.9.12, but that's ok (it's still a bit rough around the edges).

Interesting to hear about this. 

Another day I was watching Youtuve and tried to start a Skype session at the same time but Skype reported a problem with sound device and refuse to run.

---

### Post by plun on 2008-09-25
> **psyke83 said:**
> They do :). All that's left is a small fix to the PulseAudio configuration (to accommodate Skype), and then to update Flash and nspluginwrapper.

We won't get PA 0.9.12, but that's ok (it's still a bit rough around the edges).

Yup, I downgraded and Luke seems to have done a great job  :)

But where is the latest Flash plugin...!!??

Are they going to ship the beta wild old junk  :confused:

(despite of 64 bits problem, the developer (IA32) seems to be within a datacenter according to Ubuntu Planet)

---

### Post by Slug71 on 2008-09-25
Well at least we may get PA 0.9.11 then. Dont see why 0.9.12 cant make it to Intrepid though. Even if it is a little rough around the edges then at least we have Update Manager for bug fixes etc. Its not like .12 is a beta or RC release and im sure it contains a lot of fixes for the guys still having problems with PA. But even .11 may be a solution.

---

### Post by psyke83 on 2008-09-25
> **Slug71 said:**
> Well at least we may get PA 0.9.11 then. Dont see why 0.9.12 cant make it to Intrepid though. Even if it is a little rough around the edges then at least we have Update Manager for bug fixes etc. Its not like .12 is a beta or RC release and im sure it contains a lot of fixes for the guys still having problems with PA. But even .11 may be a solution.

Erm, no. Version 0.9.11 was a highly experimental release (because the glitch-free merge) and several issues were present, causing issues with many applications - Lennart explicitly warned about possible issues. Although a lot of those bugs were fixed in 0.9.12, there are still regressions compared to 0.9.10.

Luke has done a very good job implementing several bug fixes and tweaks (from bug reports & my guide) for 0.9.10. It's the most stable version available at the moment, and it's too late in the release cycle to add an experimental version.

---

### Post by DavidONE on 2008-09-25
I'd like to increase volume range, which is too low at the moment - i.e. with volume control at 100% it's still too quiet for some music / videos.

I tried PulseAudio Device Chooser -> Volume Control - but this is already set to 100%.

How else can I increase volume?

---

### Post by markbuntu on 2008-09-25
You can go over 100% in the PA Manager but that usually causes distortion but you can give it a try. In the PA Manager go to Devices and click on the number for the stream from your app. Then click Properties. There is a slider there which can go over 100%.

---

### Post by DavidONE on 2008-09-26
Perfect.  No distortion @ 200%.

---

### Post by DavidONE on 2008-09-26
Strike that last post.  Now that I'm playing something with a bit of bass, there's bad distortion.

It's not a hardware issue - XP plays much louder without distortion.

Any other suggestions?  Is it 'raise a bug' time?

---

### Post by markbuntu on 2008-09-26
What apps are you using?
I have noticed that some just play louder than others.

---

### Post by psyke83 on 2008-09-26
> **DavidONE said:**
> Strike that last post.  Now that I'm playing something with a bit of bass, there's bad distortion.

It's not a hardware issue - XP plays much louder without distortion.

Any other suggestions?  Is it 'raise a bug' time?

Both my computers have quieter sound in Linux compared to Windows. It's an ALSA issue, not PulseAudio.

Feel free to file a bug, but it's most likely not related to PulseAudio. Pushing the sound volume beyond the base 100% (0db) *will* cause distortion.

---

### Post by Gourgi on 2008-09-26
> **psyke83 said:**
> Both my computers have quieter sound in Linux compared to Windows. It's an ALSA issue, not PulseAudio.

yup, one of the first things someone notices when turns to linux.
it happens to me too.
i don't really matter cause i use only Ubuntu now :lolflag:

---

### Post by DavidONE on 2008-09-27
> **psyke83 said:**
> It's an ALSA issue, not PulseAudio.

Prompted by that, I did some digging.  Lots of people out there complaining of the same issue.

[http://ubuntuforums.org/showthread.php?t=427891](http://ubuntuforums.org/showthread.php?t=427891) might be a fix for some, but Alsamixergui is already at 100% for me.

There's an existing bug for this - [https://bugs.launchpad.net/alsa-driver/+bug/107232](https://bugs.launchpad.net/alsa-driver/+bug/107232) - I've added a comment.

I found the following in /var/log/messages:
```
HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
```

Anyone know if that 'low' is relevant and how to change it?

---

### Post by mcmanus@ducksong.com on 2008-09-27
I installed the files from this ppa in the hope of resolving some flash instability problems, and now I've got no flash in firefox at all :(

I'm giving ibex a test spin - upgraded from 8.04. I'm running Kubuntu 64 Bit - I know that isn't totally mainstream ;)

I had gone through the various workarounds on 8.04 and stuff more or less worked there using pulse audio and nssplugin. After the upgrade, youtube vids generally stalled after a few seconds and never had any audio. Firefox crashed a lot.

So I found this thread and installed the various pa and flash debs called for in the first post.

PA seems to work. Amarok uses it if set to auto-discover engine - though system settings -> sound -> audio output lists only esd and HDA intel as output devices.

But the larger issue is flash. Before it was instable, now it simply isn't there. Where the vid should be in FF3, I now just have empty white space. about: plugins shows flash 10.0 r12 registered.

any suggestions on what to try?

---

### Post by psyke83 on 2008-09-27
> **mcmanus@ducksong.com said:**
> I installed the files from this ppa in the hope of resolving some flash instability problems, and now I've got no flash in firefox at all :(

I'm giving ibex a test spin - upgraded from 8.04. I'm running Kubuntu 64 Bit - I know that isn't totally mainstream ;)

I had gone through the various workarounds on 8.04 and stuff more or less worked there using pulse audio and nssplugin. After the upgrade, youtube vids generally stalled after a few seconds and never had any audio. Firefox crashed a lot.

So I found this thread and installed the various pa and flash debs called for in the first post.

PA seems to work. Amarok uses it if set to auto-discover engine - though system settings -> sound -> audio output lists only esd and HDA intel as output devices.

But the larger issue is flash. Before it was instable, now it simply isn't there. Where the vid should be in FF3, I now just have empty white space. about: plugins shows flash 10.0 r12 registered.

any suggestions on what to try?

This issue is being investigated (and it's a problem with the official ia32-libs package, not anything in my PPA). Downgrading Flash may help, though.

---

### Post by psyke83 on 2008-09-27
Hi,

Today I've made an update to the guide, considering recent changes to the official PulseAudio packages. Almost all the pieces are together now, except Flash (it's taking a long time due to problems for 64 bit users, and the problem is being investigated).

---

### Post by ktp on 2008-09-28
> **psyke83 said:**
> Hi,

Today I've made an update to the guide, considering recent changes to the official PulseAudio packages. Almost all the pieces are together now, except Flash (it's taking a long time due to problems for 64 bit users, and the problem is being investigated).

Thanks, do you know if there is bug report for the 64-bit user problems?  Luke has done a great job and this is the only remaining issue which I would like to track.

---

### Post by bpl07 on 2008-10-02
> **bpl07 said:**
> Not to pile on, but more amd64 users are reporting problems now on this [bug report]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403").

I posted on this bug report what I believe will be the solution for flash rc2 on amd64.  The most recent version of ia32-libs is missing libgnutls26 library files.  Adding them with getlibs makes it no longer necessary to downgrade ia32-libs to get flash working.

---

### Post by ktp on 2008-10-02
> **bpl07 said:**
> I posted on this bug report what I believe will be the solution for flash rc2 on amd64.  The most recent version of ia32-libs is missing libgnutls26 library files.  Adding them with getlibs makes it no longer necessary to downgrade ia32-libs to get flash working.

I have already have that...wonder how?!

---

### Post by bpl07 on 2008-10-02
> **ktp said:**
> I have already have that...wonder how?!

You already have the 32-bit library installed, or the 64-bit package in synaptic?  I already had the 64-bit package, but not the 32-bit libraries, that's why I had to install them with getlibs.

If you don't have /usr/lib32/libgnutls.so.26 install it with:

```
getlibs -p libgnutls26
```

---

### Post by heavensblade23 on 2008-10-02
Will I have to remove the flash fix packages I got from your PPA when the 'official' fix for 64-bit comes down the pike?

---

### Post by psyke83 on 2008-10-02
> **heavensblade23 said:**
> Will I have to remove the flash fix packages I got from your PPA when the 'official' fix for 64-bit comes down the pike?

No, the official packages will have higher priority.

---

### Post by ktp on 2008-10-02
> **bpl07 said:**
> You already have the 32-bit library installed, or the 64-bit package in synaptic?  I already had the 64-bit package, but not the 32-bit libraries, that's why I had to install them with getlibs.

If you don't have /usr/lib32/libgnutls.so.26 install it with:

```
getlibs -p libgnutls26
```

The 32-bit version.

---

### Post by Vaun on 2008-10-02
psyke,

I'm using your PPA for flashplugin-nonfree and nspluginwrapper and I'm not getting the npviewer.bin crash anymore, but flash is no longer working.  The windows appear grey.  I'm on Intrepid Beta 64.  Is this part of the known 64 issue?

---

### Post by bpl07 on 2008-10-02
> **Vaun said:**
> psyke,

I'm using your PPA for flashplugin-nonfree and nspluginwrapper and I'm not getting the npviewer.bin crash anymore, but flash is no longer working.  The windows appear grey.  I'm on Intrepid Beta 64.  Is this part of the known 64 issue?

This is what I was talking about 5-6 posts above.  The current ia32-libs is missing libgnutls26.  You can install it with getlibs, or wait for the fix.

---

### Post by Vaun on 2008-10-02
Installing libgnutls26 seems to work sporadically.  Still testing it out. Thanks.

---

### Post by heavensblade23 on 2008-10-02
> **psyke83 said:**
> No, the official packages will have higher priority.

Great, thanks...I've been without Flash for days now and it was getting annoying.

---

### Post by psyke83 on 2008-10-02
> **heavensblade23 said:**
> Great, thanks...I've been without Flash for days now and it was getting annoying.

Just to make it clear, the source of the problem is not within the packages in my PPA. The problem is that ia32-libs is missing libraries that Flash requires, as bpl07 and others have mentioned. I'm not pushing ia32-libs updates, as a) I don't have 64-bit hardware, and b) I'm not patient enough to down/upload 450mb source packages ;).

As soon as ia32-libs is updated, Flash from my PPA will work correctly. Regardless, Flash will get an official update from the repositories pretty soon after the ia32-libs issue is resolved, and my PPA won't interfere.

---

### Post by kansasnoob on 2008-10-03
I had to throw you an extra thanks! I've used this Hardy guide a gazillion times:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

And I frequently link to it!

---

### Post by bpl07 on 2008-10-03
psyke83,

What do you think of the pulseaudio fix (#4) mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=925211") for 32-bit applications?  Do 64-bit users need to have the 2 .conf files he mentioned (alsa32.conf and alsa64.conf) to direct linking of 32-bit/64-bit libraries for alsa?  He got the idea from dmitry's post in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693").

---

### Post by psyke83 on 2008-10-03
> **bpl07 said:**
> psyke83,

What do you think of the pulseaudio fix (#4) mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=925211") for 32-bit applications?  Do 64-bit users need to have the 2 .conf files he mentioned (alsa32.conf and alsa64.conf) to direct linking of 32-bit/64-bit libraries for alsa?  He got the idea from dmitry's post in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693").

Thanks for the link. That seems to identified part of the problem for 64 bit users, so I've forwarded the information to Luke. I suspect there's a better way to resolve this, however (e.g. to expand detection in /usr/share/alsa/pulse.conf for 64-bit users without adding extra configuration files elsewhere).

---

### Post by ktp on 2008-10-03
Yes this really worked.

---

### Post by keep-on-smiling on 2008-10-03
hi

I did a fresh install using 8.10 beta downloaded last night and I still have the same old issue as I had with Hardy - when playing music with the sound set to autodetect etc as per a standard install, I get a freeze of rhythmbox and all sound until I reboot.

 lspci gives me:
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

Judging by what I read in this thread the problem seems solved for many people - I am wondering why I still have music hestitating every now and again, and eventually stopping totally, with the freeze happening sometimes after 5 minutes, sometime 30 minutes. I am trying to stick to a default install, so would prefer to use the standard repos. The only answer for me at the moment is to set everything to OSS, which I know is generally depreciated, but at least the music keeps playing.

Is there anyone else running the same hardware as I without issues ?

cheers

---

### Post by ktp on 2008-10-03
Are you on 64-bit?  I had the same issue when app was using ALSA and did not go throw PulseAudio (it was the flash plugin for me).  So if I open up a browser and flash starts, then try to use rhythmbox, rhythmbox would lock up and would have to kill it.  If I closed the broswer then things would work.  

I used "lsof | grep snd" command to see which app was using the sound card.  

But this seems to fixed after applying the workaround above in this thread.

---

### Post by BwackNinja on 2008-10-03
I've generally been ignoring the login sound problem I've been having, but now I'm finally looking into it, I find that it only plays correctly if pavucontrol is open. Otherwise it sounds like something being crushed (kinda like the wonderful sound in "happy weasel stomping day" by Weird Al).

---

### Post by keep-on-smiling on 2008-10-03
Hi

Nope, running a 4-year old pentium 4 here 2.6 cpu with 768 megs ram - never ever had a sound issue until pulse audio was implemented. I ran a highly tweaked Gentoo box for several months until I realised I was having too much fun tweaking, getting nothing much else done (it was getting to the point I was seriously considering buying more dishes to avoid washing 'em quite so often!!) and then decided to give Ubuntu a go, at which point the music issues began.

I have submitted a bug report, so live in hope that the devs will fix this - I could go the tweak route, but would prefer having a default install, so I can suggest Ubuntu to my mates with a clear conscience :)

cheers

---

### Post by ktp on 2008-10-03
not to worry, the dev is working on this issue and hopes to have a fix soon.

---

### Post by psyke83 on 2008-10-03
> **keep-on-smiling said:**
> Hi

Nope, running a 4-year old pentium 4 here 2.6 cpu with 768 megs ram - never ever had a sound issue until pulse audio was implemented. I ran a highly tweaked Gentoo box for several months until I realised I was having too much fun tweaking, getting nothing much else done (it was getting to the point I was seriously considering buying more dishes to avoid washing 'em quite so often!!) and then decided to give Ubuntu a go, at which point the music issues began.

I have submitted a bug report, so live in hope that the devs will fix this - I could go the tweak route, but would prefer having a default install, so I can suggest Ubuntu to my mates with a clear conscience :)

cheers

I suggest you read through these guides to get a feel for how PulseAudio works. The [Hardy]("http://ubuntuforums.org/showthread.php?t=789578") version has more information in the Appendix sections that would be useful to you, especially Appendix B.

The easiest way to test if the issue is PulseAudio or ALSA, is:

1. Ensure you don't have any ~/.asoundrc* or /etc/asound.conf configuration files - they're no longer necessary.
2. Kill PulseAudio:
```
$ pulseaudio -k
```
3. Test a previously problematic application to see if it causes the problem without PulseAudio running.

Also, please link your bug report so I can take a look.

---

### Post by DougieFresh4U on 2008-10-03
```
1. Ensure you don't have any ~/.asoundrc* or /etc/asound.conf configuration files - they're no longer necessary.
```

Are you saying this file is no longer needed or only if you are having problems? Should I get rid of it?

---

### Post by psyke83 on 2008-10-04
> **DougieFresh4U said:**
> ```
1. Ensure you don't have any ~/.asoundrc* or /etc/asound.conf configuration files - they're no longer necessary.
```

Are you saying this file is no longer needed or only if you are having problems? Should I get rid of it?

Ah, you're using the equalizer from my Hardy guide! Don't use it on Intrepid unless you know exactly what you're doing, as it can cause problems. Go to the start of this thread and follow the instructions (which include deleting those configuration files).

Forget about equalized sound until you have a vanilla PulseAudio configuration working correctly.

---

### Post by vishzilla on 2008-10-04
**psyke83**

i followed the guide given in the first page. i get the sound during startup. however after sometime. i get the error message ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```

i killed pulseaudio and tested all the apps with ALSA and it works perfectly fine. am i missing anything.

---

### Post by keep-on-smiling on 2008-10-04
> **psyke83 said:**
> 
Also, please link your bug report so I can take a look.

Hi there psyke83 thanks for all your efforts so far :)

Here's the link you requested - the useful info for you will be my last post in that thread [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/219848](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/219848)

As I mentioned, I am well aware that I could probably tweak this to get it to work - snag is that I need to keep the config default in the related areas to do the bug testing (I do regular re-installs to ensure that) - and in any case I need to be able to say to buds and kin that the system just works - before I can (in all honesty) go convert them from XP or 98.

let me know if there is any more info I can supply

cheers

---

### Post by vishzilla on 2008-10-04
I have noticed another thing. I still have the same problem as mentioned in my previous post. When i kill PA w/ pulseaudio -k and restart using pulseaudio -D --log-target=syslog it works flawlessly or atleast the sound doesn't break. Why is it PA works daemonized.

---

### Post by vishzilla on 2008-10-04
People who get the startup sound and the sound breaks eventually. I managed to find a workaround. I disabled the GNOME Login Sound present in System>Preferences>Sessions. Sound hasn't broken so far. *Crossing fingers*

---

### Post by bpl07 on 2008-10-04
I don't know how long the advice has been to delete the ~/.asoundrc* files, but when I do this I get the login sound and no other sound after that.  I have to kill and restart pulseaudio to get sound working again.  If I have the files, I don't have the login sound but everything else sound related works like it should.  This seems like what vishzilla is talking about.  

So why aren't the .conf files in /usr/share/alsa/ doing their job?  The file pulse-alsa.conf looks a lot like ~/.asoundrc.asoundconf, only it's called by pulse.conf instead of ~/.asoundrc.

---

### Post by psyke83 on 2008-10-04
> **bpl07 said:**
> I don't know how long the advice has been to delete the ~/.asoundrc* files, but when I do this I get the login sound and no other sound after that.  I have to kill and restart pulseaudio to get sound working again.  If I have the files, I don't have the login sound but everything else sound related works like it should.  This seems like what vishzilla is talking about.  

So why aren't the .conf files in /usr/share/alsa/ doing their job?  The file pulse-alsa.conf looks a lot like ~/.asoundrc.asoundconf, only it's called by pulse.conf instead of ~/.asoundrc.

It is absolutely no longer necessary for an ~/.asoundrc file. Luke patched alsa-lib to detect if PulseAudio is running, and dynamically apply the proper configuration.

However, as you've seen, this detection is currently broken for 64-bit users. You simply need to wait for the fix, or apply the proposed workaround earlier in the thread (which applies to any 32 bit applications, not just Flash).

---

### Post by Wise Ferret on 2008-10-04
This is not limited to 64-bit. On my 32-bit system (alc880 sound chipset) I get the same thing: login sound, then sound breaks and I have to kill pulseaudis with pulseaudio -k and restart it. I have put it in a gnome session script.

---

### Post by bpl07 on 2008-10-04
I have an entry in my gnome-session-properties called "PulseAudio Sound System".  The command it tries to run is "start-pulseaudio-x11", but that command does not exist on my system.  Is there another command this should be to start the pulseaudio sound system?  Maybe this is unrelated, I'm mostly just thinking out loud trying to get login sound and everything else sound related to work simultaneously.

---

### Post by bpl07 on 2008-10-04
So it looks like the default sink is not being set at startup.  Here's what I get before killing and restarting pulseaudio:

> > pactl stat
Currently in use: 0 blocks containing 0 B bytes total.
Allocated during whole lifetime: 0 blocks containing 0 B bytes total.
Sample cache size: 0 B
User name: brad
Host Name: ubuntu
Server Name: pulseaudio
Server Version: 0.9.10
Default Sample Specification: s16le 2ch 44100Hz
Default Sink: (null)
Default Source: alsa_input.pci_1002_4383_alsa_capture_0
Cookie: 7a3eca0e

and here's what I get after:

> brad@ubuntu /home/brad                                                          > pulseaudio --log-target=syslog &
[1] 10182
                                                                                brad@ubuntu /home/brad                                                          > ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL front:0

                                                                                brad@ubuntu /home/brad                                                          > pactl stat
Currently in use: 0 blocks containing 0 B bytes total.
Allocated during whole lifetime: 97 blocks containing 204.8 KiB bytes total.
Sample cache size: 0 B
User name: brad
Host Name: ubuntu
Server Name: pulseaudio
Server Version: 0.9.10
Default Sample Specification: s16le 2ch 44100Hz
Default Sink: alsa_output.pci_1002_4383_alsa_playback_0
Default Source: alsa_input.pci_1002_4383_alsa_capture_0
Cookie: f4978b21

This is all without the .asoundrc* files.

---

### Post by ktp on 2008-10-04
did you try removing/deleting .pulse folder in your home directory?  This might help clean up things.

---

### Post by bpl07 on 2008-10-04
yeah, i've gone through the howto at the beginning of the thread several times today.

---

### Post by kingmanowar on 2008-10-06
I have followed the 'howto' and it works great until I try to use my skype usb phone (US Robotics USR809601A). I can use the phone with skype and it works quite well (not as clear as on windows though), however when I unplug/re-plug it, I have some issues. Sometimes I do not have any sound at all on the whole machine (have to log off/log on again). Sometimes all the sounds are redirected to the skype phone, even mp3...

Also if I boot with the phone plugged, pulse audio seems to ignore my onboard sound card (ALC850). If I unplug the phone, I have no sound at all.

Can pulseaudio handle more than one soundcard with the default settings ?( afterall the usb phone is nothing more than a second card I guess). Any suggestions and things to try ?

Thanks a lot

---

### Post by CCCCCC on 2008-10-06
Give you the best recommendation
Serving over 225,000 customers,  AAA PharmacyOnline is your trusted source for the lowest possible prices for all of your prescription needs. At AAA PharmacyOnline your health is our number one concern. Our trained team of doctors and pharmacists make sure your purchasing experience is stress free and enjoyable.  We make sure that you receive the highest quality medications. When it comes to excellent customer service, low prices and fast shipping, we set the industry standards. 
 
We offer a wide range of brand name and generic drugs at economical prices for all your prescription needs. If you find your medication priced lower, we will match that price for you.  
 
If you do not already have a prescription then our medical doctors can work with you to provide you with your prescription. 
 
Visit us: [http://www.aaa-pharmacyonline.com](http://www.aaa-pharmacyonline.com)

---

### Post by psyke83 on 2008-10-06
> **kingmanowar said:**
> I have followed the 'howto' and it works great until I try to use my skype usb phone (US Robotics USR809601A). I can use the phone with skype and it works quite well (not as clear as on windows though), however when I unplug/re-plug it, I have some issues. Sometimes I do not have any sound at all on the whole machine (have to log off/log on again). Sometimes all the sounds are redirected to the skype phone, even mp3...

Also if I boot with the phone plugged, pulse audio seems to ignore my onboard sound card (ALC850). If I unplug the phone, I have no sound at all.

Can pulseaudio handle more than one soundcard with the default settings ?( afterall the usb phone is nothing more than a second card I guess). Any suggestions and things to try ?

Thanks a lot

PulseAudio features hotplugging of sound cards, so the behaviour while the phone is plugged is normal. However, when the phone is unplugged, it should revert back to the onboard sound.

Open the PulseAudio Manager and watch the default sink before and after you plug/unplug the phone. The PulseAudio Device Manager also lets you set the default sink (of which you can find the proper name in the Manager application).

---

### Post by The Warlock on 2008-10-06
Hey, I followed the directions and have a strange problem. After I log in, I get no sound, but if I then kill the pulseaudio process and start it up again, everything works perfectly. I looked in the PulseAudio Manager and under Sinks, it didn't show any devices initially, but after killing and restarting, it showed "ALSA PCM on front:0 (ALC269 Analog) via DMA". Is there a workaround? Did I screw up somewhere? 

(Also, if I just killed pulseaudio and *don't* restart it, sound works fine, I assume through alsa dmix or something).

edit: apparently I'm not the only one with this problem. I'm on 32-bit Ubuntu, on an EeePC 901, if it matters.

---

### Post by psyke83 on 2008-10-06
> **The Warlock said:**
> Hey, I followed the directions and have a strange problem. After I log in, I get no sound, but if I then kill the pulseaudio process and start it up again, everything works perfectly. I looked in the PulseAudio Manager and under Sinks, it didn't show any devices initially, but after killing and restarting, it showed "ALSA PCM on front:0 (ALC269 Analog) via DMA". Is there a workaround? Did I screw up somewhere? 

(Also, if I just killed pulseaudio and *don't* restart it, sound works fine, I assume through alsa dmix or something).

edit: apparently I'm not the only one with this problem. I'm on 32-bit Ubuntu, on an EeePC 901, if it matters.

Did you opt to install PulseAudio 0.9.12? If so, downgrade back to 0.9.10 (instructions are in the guide).

---

### Post by The Warlock on 2008-10-06
> **psyke83 said:**
> Did you opt to install PulseAudio 0.9.12? If so, downgrade back to 0.9.10 (instructions are in the guide).

Nope, I'm running 0.9.10. I just double checked in the PulseAudio Manager.

---

### Post by psyke83 on 2008-10-06
> **The Warlock said:**
> Nope, I'm running 0.9.10. I just double checked in the PulseAudio Manager.

I suggest you file a bug (and yes, it seems others are experiencing the same issue). I can't reproduce it on my system.

Does this problem occur *each* time you login, or only upon the first login when you boot the computer? It could be some kind of ALSA timing issue.

---

### Post by The Warlock on 2008-10-06
> **psyke83 said:**
> I suggest you file a bug (and yes, it seems others are experiencing the same issue). I can't reproduce it on my system.

Does this problem occur *each* time you login, or only upon the first login when you boot the computer? It could be some kind of ALSA timing issue.

Huh, I didn't think to check that. Yeah, it happens every time I log in, not just the first login after boot. Even if I log in, kill and restart Pulseaudio, log out, and log in again, it breaks.

---

### Post by kingmanowar on 2008-10-06
> **psyke83 said:**
> PulseAudio features hotplugging of sound cards, so the behaviour while the phone is plugged is normal. However, when the phone is unplugged, it should revert back to the onboard sound.

Open the PulseAudio Manager and watch the default sink before and after you plug/unplug the phone. The PulseAudio Device Manager also lets you set the default sink (of which you can find the proper name in the Manager application).


I have done some more testing tonight. If I plug/unplug the phone a sink is indeed added/removed. However if I log out while the phone is plugged, when I log in again, the sink for the onboard soundcard is not detected. The only sink I have is the one for the phone. I have the same thing when I boot up the system with the phone already plugged. It is quite annoying.
I am not too sure how to fix that. Is it a bug a feature or a config setting :) ?

---

### Post by psyke83 on 2008-10-06
> **kingmanowar said:**
> I have done some more testing tonight. If I plug/unplug the phone a sink is indeed added/removed. However if I log out while the phone is plugged, when I log in again, the sink for the onboard soundcard is not detected. The only sink I have is the one for the phone. I have the same thing when I boot up the system with the phone already plugged. It is quite annoying.
I am not too sure how to fix that. Is it a bug a feature or a config setting :) ?

Definitely file a bug. Nevertheless, you can edit /etc/pulse/default.pa. Find this line:

```
#load-module module-alsa-sink
```

Change it to:
```
load-module module-alsa-sink device=hw:[COLOR="Red"]x,x[/COLOR]
```

Don't forget to remove the comment (#), and replace [COLOR="Red"]x,x[/COLOR] with the appropriate sound card that you wish to be made default.

Note that this will disable hotplugging and force the sink to remain with your sound card. That means that you will need to move streams to your USB phone manually (via the PA Volume Control).

---

### Post by kingmanowar on 2008-10-06
I have done what you suggested. I modified default.pa and restarted my computer with the phone plugged in. I had the same problem, all the sounds went to the phone. I unplugged the phone, restarted pulseaudio, plugged the phone back and everything is fine again, all the sounds are played through the speakers.

However when I do ```
speaker-test -Dplug:pulse -c6 -l1 -twav
``` the channels are all messed up ! Centre is becoming 'back left'... It was fine before.

Basically, what I would like to do is to have the sounds always through the speakers. Whatever if the phone is plugged or not. I simply want to use the phone as an input for skype.

Thanks a lot for your help.

---

### Post by markbuntu on 2008-10-06
You should be able to do that in the PA Volume Control (pavucontrol). Your sound card and your usb phone will be in the Output Devices section. You can right click on the sound card to make it the default and all your applications will use it. When you use skype, you can just use the move stream function in the Playback section to move skype to the phone. or you can just set up skype to use the hardware directly instead of the default sound card/Pulseaudio.

---

### Post by kingmanowar on 2008-10-06
Well as long as the onboard card and the phone are both detected I know how to set pulseaudio to do what I want. The only problem is when the onboard card sink disappears from pulseaudio. I have to unplug the phone, restart pulseaudio and plug back the phone and then they are both back.

---

### Post by carusoswi on 2008-10-06
Does all the code in steps 1a through 3 go into the sources.list file?  Sorry if I am asking a dumb question, but it's not obvious to me.
Thanks.

Caruso

---

### Post by psyke83 on 2008-10-06
> **carusoswi said:**
> Does all the code in steps 1a through 3 go into the sources.list file?  Sorry if I am asking a dumb question, but it's not obvious to me.
Thanks.

Caruso

No. Anything preceded by "$" means that you input it into a terminal.

Also, please read the step descriptions. For example, installing PA 0.9.12 is not recommended.

---

### Post by BwackNinja on 2008-10-06
Any knowledge of when PulseAudio 0.9.13 will be in the ppa if ever?

---

### Post by psyke83 on 2008-10-06
> **kingmanowar said:**
> I have done what you suggested. I modified default.pa and restarted my computer with the phone plugged in. I had the same problem, all the sounds went to the phone. I unplugged the phone, restarted pulseaudio, plugged the phone back and everything is fine again, all the sounds are played through the speakers.

However when I do ```
speaker-test -Dplug:pulse -c6 -l1 -twav
``` the channels are all messed up ! Centre is becoming 'back left'... It was fine before.

Basically, what I would like to do is to have the sounds always through the speakers. Whatever if the phone is plugged or not. I simply want to use the phone as an input for skype.

Thanks a lot for your help.

Hmm. Revert your configuration to default (i.e., revert the line I earlier asked you to edit), and instead edit the second-last line:
```
#set-default-sink output
```

Change it to:
```
set-default-sink [COLOR="Red"]your_sound_card[/COLOR]
```

You need to put the exact name of your sound card as listed in the PulseAudio Manager.

N.B.: The file ~/.pulse/volume-restore.table saves the last used sink for each PulseAudio client. You'll almost certainly want to delete this file, as many applications may erroneously point to your USB phone. Once this file is deleted, *all* applications should use your onboard sound. All that remains is for you to move the playback source for Skype using the PA Volume Control applet once more.

---

### Post by psyke83 on 2008-10-06
> **BwackNinja said:**
> Any knowledge of when PulseAudio 0.9.13 will be in the ppa if ever?

I haven't spoken to Luke, though I don't imagine he'll be interested (me neither). We're too late in the development cycle, and remaining integration issues need to be resolved for the official packages (to get 64bit, Flash, Skype etc. working). PA 0.9.12 was a regression in terms of stability, and the status of 0.9.13 is simply too unknown & too late in the development cycle...

---

### Post by far_star on 2008-10-06
Help !

I used you method described in your 1st post and now I only get audio out of my 2 front speakers on my Audigy 2 (ex. when playing through Amarok). The alsa mixer does nothing. I did not upgrade pulseaudio. 

If I could, I would undo all the changes but I don't know how. I really don't to have to reinstall Intrepid to fix this. 

Can anyone dig me out of this mess ?

---

### Post by BwackNinja on 2008-10-06
You can have surround sound with pulseaudio: [http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

but otherwise, psyke83 would probably be better at explaining how to undo the changes.

EDIT:
Did you previously have output be to ALSA? If so, just change it back in Sound Preferences.

---

### Post by Nullack on 2008-10-06
Any ETA on the 64bit flash upgrade? Alexander was talking about doing it prior to beta, but I assume time was against us there.

---

### Post by far_star on 2008-10-06
> **BwackNinja said:**
> You can have surround sound with pulseaudio: [http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

but otherwise, psyke83 would probably be better at explaining how to undo the changes.

EDIT:
Did you previously have output be to ALSA? If so, just change it back in Sound Preferences.

Thanks. I tried changing that setting under /etc but the thread you pointed me to did the trick. Funny thing is that I searched for this. I suppose I didn't search using the right terms. Anyway, the only annoyance is that using gnome volume control I have to change the mixer device to the pulse audio one which has fewer options. 

If there is a way to undo the changes I'm still game. I really wasn't having any trouble before (except for flash killing my sound sometimes) and shouldn't have gone around messing around.

---

### Post by psyke83 on 2008-10-07
> **far_star said:**
> Thanks. I tried changing that setting under /etc but the thread you pointed me to did the trick. Funny thing is that I searched for this. I suppose I didn't search using the right terms. Anyway, the only annoyance is that using gnome volume control I have to change the mixer device to the pulse audio one which has fewer options. 

If there is a way to undo the changes I'm still game. I really wasn't having any trouble before (except for flash killing my sound sometimes) and shouldn't have gone around messing around.

Your system was misconfigured beforehand, believe it or not. The symptom of Flash cutting out other audio indicated that the PulseAudio ALSA plugins were not enabled properly.

If your speaker setup is correct now, then I suggest you keep this configuration.

---

### Post by bpl07 on 2008-10-07
So the recent updates to pulseaudio and lib32asound2 added the 2 conf files I mentioned earlier in the thread.  

This still has not fixed my issue of not having sound until I kill and restart pulseaudio.  If I do this, then log out and back in, I don't have the login sound anymore.  For some reason I can't have both login sound and every other sound at the same time.  

What would prevent pulseaudio from setting the default sink at login, because this to me seems to be the problem that's causing the issue.

---

### Post by defconoii on 2008-10-08
Hulu.com does not work at all with these upgrades, it freezes firefox when the browser loads.

---

### Post by psyke83 on 2008-10-08
> **bpl07 said:**
> So the recent updates to pulseaudio and lib32asound2 added the 2 conf files I mentioned earlier in the thread.  

This still has not fixed my issue of not having sound until I kill and restart pulseaudio.  If I do this, then log out and back in, I don't have the login sound anymore.  For some reason I can't have both login sound and every other sound at the same time.  

What would prevent pulseaudio from setting the default sink at login, because this to me seems to be the problem that's causing the issue.

As I said, you may want to file a bug - I can't reproduce this behaviour. In Sound Preferences, I suggest you:

a) Ensure all Playback options are set to Autodetect;
b) Uncheck "Play alerts and sound effects" in Sound Preferences.

Try logging out and back in to see if PulseAudio connects an ALSA sink successfully.

---

### Post by eufrat on 2008-10-08
> **bpl07 said:**
> So the recent updates to pulseaudio and lib32asound2 added the 2 conf files I mentioned earlier in the thread.  

This still has not fixed my issue of not having sound until I kill and restart pulseaudio.  If I do this, then log out and back in, I don't have the login sound anymore.  For some reason I can't have both login sound and every other sound at the same time.  

What would prevent pulseaudio from setting the default sink at login, because this to me seems to be the problem that's causing the issue.

I have this same bug in both msi wind and acer aspire one. Pulseaudio need to kill and restart. Then sounds works. Everything works in my desktop machine with 8.10.

---

### Post by psyke83 on 2008-10-08
> **eufrat said:**
> I have this same bug in both msi wind and acer aspire one. Pulseaudio need to kill and restart. Then sounds works. Everything works in my desktop machine with 8.10.

File a bug and mention it in this thread, then. It's not going to get fixed until that's done.

---

### Post by BwackNinja on 2008-10-08
Based on [http://0pointer.de/lennart/projects/libcanberra/](http://0pointer.de/lennart/projects/libcanberra/) the multi-backend (successively trying different outputs until one works) does not work until 0.8. We have 0.6 in intrepid and it is outputing to ALSA and because pulseaudio is opened per session its probably taking up the device while pulseaudio is trying to get it thus only one can be working at a time. My install is currently a bit too far from the default right now, so I'll just do a reinstall a bit later today. ALSA to pulseaudio should be working right though...

EDIT:
Pulseaudio 0.9.11 or later is needed for libcanberra pulseaudio output. That makes sense then.

---

### Post by Vaun on 2008-10-08
The conflict with pulseaudio conflicting with other gstreamer apps has been fixed by Luke's latest pulseaudio updates to Intrepid.

pulseaudio (0.9.10-2ubuntu7) intrepid; urgency=low

  * Fix some errors in the pid file handling patch, thanks to Mandriva.
  * debian/pulse.conf: Do not use an absolute path when referring to the
    pulse alsa plugin, as this breaks bi-arch configurations. libasound2
    and lib32/64asound2 now include ldconfig files to include the alsa-plugins
    path for the architecture in use.

Date: Wed, 08 Oct 2008 11:20:17 +1100

alsa-lib (1.0.17a-0ubuntu4) intrepid; urgency=low

  [ Mario Limonciello ]
  * debian/patches/bluetooth_configuration.patch:
    - Adds a pointer to the bluetooth configuration file.
      If a user has bluez-audio installed and a heaset paired
      this will allow them to use a headset by the name of
      "headset" (LP: #274950)

  [ Luke Yelavich ]
  * Add files to /etc/ld.so.conf.d for libasound2 and libasound2 bi-arch
    packages. This Allows for alsa plugins to be referred to in alsa
    configuration files without the need for absolute paths, the pulseaudio
    runtime check is one such example. (LP: #273693)

Date: Tue, 07 Oct 2008 17:49:28 +1100

The only issue I'm having at this point is with libcanberra and event sounds.  The only event sounds that work for me at this point are login and start up sounds.  All the event sounds are not working although they sound when activated in sound preferences.

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507")

I think the latest version of libcanberra 0.10 will resolve this.  Hopefully, Luke packages it for Intrepid.

---

### Post by plun on 2008-10-08
The terrible beta version of Flash is soon gone.  :)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008243.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008243.html)

> flashplugin-nonfree (10.0.12.10ubuntu1) intrepid; urgency=low

  * New upstream release candidate (LNX 10,0,12,10) granted
    FeatureFreeze exception (LP: #257403).
  * debian/config:
    debian/postinst:  Update md5sums, filenames, and paths.
  * debian/control:  Conflict with libflashsupport; it was a suboptimal
    hack.  Remove it from the alternate recommends for libasound2-plugins,
    too.


---

### Post by Nullack on 2008-10-08
Good stuff I look forward to testing that.

Once the new flash hits, is there any other configuration items this guide has that the repos dont (excepting the new pulse due to regressions)? if so, why? Lets gets this stuff into Intrepid.

---

### Post by scradock on 2008-10-08
> **plun said:**
> The terrible beta version of Flash is soon gone.  :)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008243.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008243.html)

That version hasn't yet appeared, has it? Yet the Accepted date is September 28th. I still have the horrible hybrid 10.0.1.218+10.0.0.525ubuntu1. 
Does anyone know what's going on?

---

### Post by Nullack on 2008-10-08
Synch to main youll get the goodness now

I note however it still fails on the adobe 10 flash demo

[http://labs.adobe.com/technologies/flashplayer10/demos/](http://labs.adobe.com/technologies/flashplayer10/demos/)

Youtube has a video of what the demo page should look like

---

### Post by scradock on 2008-10-08
> **Nullack said:**
> Synch to main youll get the goodness now

I note however it still fails on the adobe 10 flash demo

[http://labs.adobe.com/technologies/flashplayer10/demos/](http://labs.adobe.com/technologies/flashplayer10/demos/)

Youtube has a video of what the demo page should look like

Yes - it just turned up, a couple of minutes after I posted.

---

### Post by ShirishAg75 on 2008-10-08
Hi all, 
 Widelands doesn't work with pulseaudio [http://ubuntuforums.org/showthread.php?t=942206](http://ubuntuforums.org/showthread.php?t=942206)

Now is that a regression or a bug? If its something that requires changing something here or there then its cool. 

If its a bug say in widelands, then have to file a bug both here as well as upstream, somebody please try it so we can know whom to blame ;)

---

### Post by scradock on 2008-10-09
> **Nullack said:**
> Synch to main youll get the goodness now

I note however it still fails on the adobe 10 flash demo

[http://labs.adobe.com/technologies/flashplayer10/demos/](http://labs.adobe.com/technologies/flashplayer10/demos/)

Youtube has a video of what the demo page should look like

What's failing? I get some activity with some of the shots - it looks solid enough for me. Where do I find the Youtube video, just to check?

---

### Post by Nullack on 2008-10-09
Nah, its broken badly

[http://au.youtube.com/watch?v=NCLDtS1SUZ8](http://au.youtube.com/watch?v=NCLDtS1SUZ8)

---

### Post by danf_1979 on 2008-10-09
First post fixed all my sound issues regarding firefox + flash + other applications. Thanks :).

Will this be on intrepid by default when released?

---

### Post by Pro-reason on 2008-10-09
I've just upgraded to Kubuntu Intrepid 64-bit, and this works fine.  The only trouble is that I have to start Pulseaudio manually.  Perhaps I'll put it in my start-up script.

---

### Post by scradock on 2008-10-09
> **Nullack said:**
> Nah, its broken badly

[http://au.youtube.com/watch?v=NCLDtS1SUZ8](http://au.youtube.com/watch?v=NCLDtS1SUZ8)

Thanks for the link - I get all those effects with the new flashplugin-nonfree.

Trying some of the videos listed below the Astro screen fails - one of them was a .mov, so I probably haven't got the right proprietary codec installed.

For me it looks like a good step forward.....

---

### Post by MJWitter on 2008-10-09
All of the effects work perfectly for me(intrepid Amd64) after the update.

---

### Post by Chazall1 on 2008-10-10
I have used this info for the pasr couple of weeks and pulse and all sounds have worked. I did the updates today and pulse is functioning perfectly, the playback meter works for all my sound apps, vlc, mplayer, smplayer, rhythmbox and in flash on youtube and others. But I do not have sound. I have my login sound that I have set through the System, Admin, Login Window. All is functioning, but I can not here anything. Pulse is  0.9.10.
Any idea what my cause this issue.

Thanks

---

### Post by mc4100 on 2008-10-10
> **Chazall1 said:**
> I have used this info for the pasr couple of weeks and pulse and all sounds have worked. I did the updates today and pulse is functioning perfectly, the playback meter works for all my sound apps, vlc, mplayer, smplayer, rhythmbox and in flash on youtube and others. But I do not have sound. I have my login sound that I have set through the System, Admin, Login Window. All is functioning, but I can not here anything. Pulse is  0.9.10.
Any idea what my cause this issue.

Thanks
Have you tried changing the sink in padevchooser?

---

### Post by Nullack on 2008-10-10
> **Nullack said:**
> Once the new flash hits, is there any other configuration items this guide has that the repos dont (excepting the new pulse due to regressions)? if so, why? Lets gets this stuff into Intrepid.

So now that the RC for flash is in the repos, bumpage for my question RE any other configuration items please.

---

### Post by zombiepig on 2008-10-10
> **Nullack said:**
> So now that the RC for flash is in the repos, bumpage for my question RE any other configuration items please.

Well, libcanberra 0.10 is still needed to fix the missing event sounds, so it'd be nice to see that included in intrepid!

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)

---

### Post by Fracman on 2008-10-11
> **Chazall1 said:**
> I have used this info for the pasr couple of weeks and pulse and all sounds have worked. I did the updates today and pulse is functioning perfectly, the playback meter works for all my sound apps, vlc, mplayer, smplayer, rhythmbox and in flash on youtube and others. But I do not have sound. I have my login sound that I have set through the System, Admin, Login Window. All is functioning, but I can not here anything. Pulse is  0.9.10.
Any idea what my cause this issue.

Thanks

Try to switch off your system sounds and then reboot. Worked for me!

---

### Post by psyke83 on 2008-10-11
> **Nullack said:**
> So now that the RC for flash is in the repos, bumpage for my question RE any other configuration items please.

As far as I can see, no extra effort or custom configuration will be necessary to ensure that everything works.

For a fresh install, PulseAudio will work "out of the box", though the user will need to manually install the PulseAudio configuration tools (if desired). When upgrading, some users may need to delete their ~/.asoundrc* and ~/.pulse/* files to ensure that PulseAudio functions as intended.

There are small niggling issues left, e.g. if you install an SDL game, it will grab the libsdl1.2debian-alsa library, when it should install the libsdl1.2debian-pulse library. That's ok, though - the ALSA SDL drivers work correctly with PulseAudio, and it's better to default to ALSA for Kubuntu, Xubuntu and other flavours that don't use PulseAudio by default.

---

### Post by plun on 2008-10-11
> **psyke83 said:**
> As far as I can see, no extra effort or custom configuration will be necessary to ensure that everything works.



- padevchooser ?  I have never seen any open discussion about this !

- fta updated his ppa repo with this

[B]alsa-lib (1.0.17a-0ubuntu5~fta1) intrepid; urgency=low

  * Use pulse pcmctl by default (patch from Crimsun)
    + debian/patches/use_pulse_pcmctl_by_default.patch[/B]

- libcanberra  ?

---

### Post by psyke83 on 2008-10-11
> **plun said:**
> - padevchooser ?  I have never seen any open discussion about this !

- fta updated his ppa repo with this

[B]alsa-lib (1.0.17a-0ubuntu5~fta1) intrepid; urgency=low

  * Use pulse pcmctl by default (patch from Crimsun)
    + debian/patches/use_pulse_pcmctl_by_default.patch[/B]

- libcanberra  ?

Including padevchooser or the other utilities may be difficult due to size constraints (by the way - padevchooser is already considered obsolete). Integrating the PA Volume control into the panel seems like a better option (though it's probably not going to happen for Intrepid).

I'm not sure if the patch by Daniel is necessary, though I'm sure it'll get pushed if it is - I'm not involved with ALSA development, he is ;).

As for libcanberra, the bug is already filed to upgrade to 0.10 (though I thought that it requires PA 0.9.11+ to function, so we'll see). System sounds appear to be working on my machine anyway.

---

### Post by Chazall1 on 2008-10-11
>  From Fracman. Try to switch off your system sounds and then reboot. Worked for me!
I will try this option tonight. What comand should I run to see what my default sound card is.

Thanks

---

### Post by plun on 2008-10-11
> **psyke83 said:**
> Including padevchooser or the other utilities may be difficult due to size constraints (by the way - padevchooser is already considered obsolete). Integrating the PA Volume control into the panel seems like a better option (though it's probably not going to happen for Intrepid).

I'm not sure if the patch by Daniel is necessary, though I'm sure it'll get pushed if it is - I'm not involved with ALSA development, he is ;).

As for libcanberra, the bug is already filed to upgrade to 0.10 (though I thought that it requires PA 0.9.11+ to function, so we'll see). System sounds appear to be working on my machine anyway.

Ok

I have no login sound, USB out as default...I have been playing around
too much with this...:mrgreen:  (up to ver .13 directly)

Maybe its possible to just install pavucontrol
[http://packages.ubuntu.com/intrepid/pavucontrol](http://packages.ubuntu.com/intrepid/pavucontrol)

Or it must be  :)

Daniel for sure knows what he is doing....

---

### Post by Slug71 on 2008-10-11
Is 0.9.13 in somewhere in the PPA's?

---

### Post by psyke83 on 2008-10-11
> **Slug71 said:**
> Is 0.9.13 in somewhere in the PPA's?

No. Nobody bothered packaging it, simply because there wouldn't be enough time to include it in the official release (hence there's no urgency to test it).

---

### Post by Slug71 on 2008-10-11
Cool, thanks psyke83.

By official release, does that mean 0.9.12 will be in Intrepid? 
I used your instructions to install it when using .27-6 so not sure if it was in .27-7.

---

### Post by psyke83 on 2008-10-11
> **Slug71 said:**
> Cool, thanks psyke83.

By official release, does that mean 0.9.12 will be in Intrepid? 
I used your instructions to install it when using .27-6 so not sure if it was in .27-7.

Too many regressions were introduced in this release. Considering these regressions and a lack of time, the answer is no, it won't be included. 

Luke (TheMuso) has already done some great work by applying the proposed settings and fixes in various bug reports. The result: we have a much improved PulseAudio 0.9.10 compared to Hardy's version.

If you're having audio problems with 0.9.12, which is likely, the instructions to downgrade are in the guide. Kernel versions won't affect PulseAudio (except by potential changes to the ALSA kernel drivers).

---

### Post by Chazall1 on 2008-10-11
I still have no sound after turning off the system sounds and re-booting. Pulse is function fine, the volume meter playback is indicating sound, and in PA Manager the Device Tab I get the sinks combined indication of the audio device I choose. But I here nothing!

Thanks

---

### Post by Slug71 on 2008-10-11
> **psyke83 said:**
> Too many regressions were introduced in this release. Considering these regressions and a lack of time, the answer is no, it won't be included. 

Luke (TheMuso) has already done some great work by applying the proposed settings and fixes in various bug reports. The result: we have a much improved PulseAudio 0.9.10 compared to Hardy's version.

If you're having audio problems with 0.9.12, which is likely, the instructions to downgrade are in the guide. Kernel versions won't affect PulseAudio (except by potential changes to the ALSA kernel drivers).

Nah i'm not having any issues with 0.9.12 on AMD64. Not that i've encountered yet anyway which is why i thought i'd try 0.9.13.
Haven't tried using Skype yet though.

---

### Post by ShirishAg75 on 2008-10-12
Hi all, 
 Pyske83 as well as everybody, I have a question, I have a 

```
/etc/pulse/daemon.conf 
```as well as 

```
~/.pulse/daemon.conf
```Now the first one should be system-wide while the latter for the user, now if both the configurations are different, then logically the latter one should be taken, right?

Another issue/query is that in your full-guide you have mentioned that you need to play with fragment size and stuff to lessen the stuttering, but doing what will get what is not told :(

```

default-fragments = 8
default-fragment-size-msec = 5

```

> 
[COLOR=Red]Note 1: If you still notice stuttering, try modifying the fragment sizes marked in red.[/COLOR]


Make that note a little bit clearer please as big numbers and/or smaller numbers would do what? I personally am confused as to what will give what. 

Lastly there was no ~/.pulse/daemon.conf and I just made one using stuff you said about. 

Looking forward for answers.

---

### Post by psyke83 on 2008-10-12
> **ShirishAg75 said:**
> Hi all, 
 Pyske83 as well as everybody, I have a question, I have a 

```
/etc/pulse/daemon.conf 
```as well as 

```
~/.pulse/daemon.conf
```Now the first one should be system-wide while the latter for the user, now if both the configurations are different, then logically the latter one should be taken, right?

Another issue/query is that in your full-guide you have mentioned that you need to play with fragment size and stuff to lessen the stuttering, but doing what will get what is not told :(

```

default-fragments = 8
default-fragment-size-msec = 5

```



Make that note a little bit clearer please as big numbers and/or smaller numbers would do what? I personally am confused as to what will give what. 

Lastly there was no ~/.pulse/daemon.conf and I just made one using stuff you said about. 

Looking forward for answers.

Apologies, I have an appointment so I have to be brief.

If I recall correctly, the stock PulseAudio configuration in Hardy defined 4 fragments at 25msecs each, which caused stuttering on all my systems. The effects of modifying the fragment sizes and amounts vary wildly depending on your sound card, so there is no way to direct you as to the ideal fragment settings. The settings I proposed were the result of trial and error that resulted in stutter-free sound on all the systems I tested on. I can't guarantee it will work as well for you, though.

The user configuration is given priority over the system-wide configuration. Most of the changes proposed in the Hardy guide have been applied *by default* to the Intrepid packages (including fragment size tweaks), but of course those changes are defined in the system-wide configuration.

Therefore, you should *delete* your user configuration (created as a result of following my Hardy guide) in order to avail of the updated Intrepid configuration. If you follow this guide properly, one of the steps will delete the contents of your ~/.pulse/ directory.

---

### Post by ShirishAg75 on 2008-10-12
ah saw that , apologies psyke83

[]("https://bugs.launchpad.net/bugs/192888")> 3. Perform the following steps to remove obsolete configuration files

Please note I'm using stuff from official repositories only 0.9.10 

I have had another bug but perhaps it was due to this, lemme check back some hours later.

---

### Post by Chazall1 on 2008-10-12
Just wanted to inform everyone that I have my sound back through pulseaudio.

kill PA w/         pulseaudio -k
and restart using
      pulseaudio -D --log-target=syslog
I do have errors in the sys log.
I also ran
pulseaudio --version
W: ltdl-bind-now.c: Failed to find original dlopen loader.
pulseaudio 0.9.10

I know its being worked on.

Thanks for all the support

---

### Post by night-wing on 2008-10-14
For me, this how to didn't work. The sound crackles more than before and system sounds do not play :-(

---

### Post by shane19174 on 2008-10-14
night-wing, I don't know about the crackling, but as far as I understand the missing system sounds are a completely different problem. It's discussed here explicitly: [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507"), and it's related to the package libcanberra, which has 11 open bugs (see here: [https://bugs.launchpad.net/ubuntu/+source/libcanberra]("https://bugs.launchpad.net/ubuntu/+source/libcanberra")).

I too am without sound effects for system events. I haven't tried the fix discussed in the first link above. I'm just waiting to see if it gets fixed on its own.

Shane

---

### Post by ShirishAg75 on 2008-10-14
That one actually has a fix although not a pretty one at [https://bugs.edge.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.edge.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)

---

### Post by phenest on 2008-10-14
> **psyke83 said:**
> First of all, get the nvidia driver working properly (this isn't the thread to ask about it). When the nvidia driver is working properly, paste the output of the following:

```
$ pulseaudio -k; wait 3; pulseaudio -vv
```

I get "connection refused" too.
```
steve@precision:~$ pulseaudio -k; wait 3; pulseaudio -vv
pulseaudio: error while loading shared libraries: libpulsecore.so.5: cannot open shared object file: No such file or directory
bash: wait: pid 3 is not a child of this shell
pulseaudio: error while loading shared libraries: libpulsecore.so.5: cannot open shared object file: No such file or directory

```

---

### Post by BwackNinja on 2008-10-14
@phenest

That means that you at one point had conflicting versions of pulseaudio installed, and there's a mixup somewhere. Its looking for libpulsecore.so.5, while there is probably some other libpulsecore.so there. Either that or you have a missing symlink. Give the output of "locate libpulsecore"

---

### Post by sjk44 on 2008-10-15
Thank you for the PulseAudio Fixes write-up.  I am trying to get my sound system to work.  I can hear sounds from web-based radio, but neither Skype or Rhythmbox work.  When I run PulseAudio from the terminal here is the output:

stanleyk@shuttle:~$ pulseaudio
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: alsa-util.c: Error opening PCM device surround40:NVidia: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=surround40:NVidia sink_name=NVidia"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
stanleyk@shuttle:~$ paconfig
stanleyk@shuttle:~$ pulseaudio
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: alsa-util.c: Error opening PCM device front:NVidia: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=front:NVidia sink_name=NVidia"): initialization failed.
E: main.c: Module load failed.  :)
E: main.c: Failed to initialize daemon.

Do you have a suggestion on how to proceed to solve this problem?  Thank you for taking the time to work with me; I am a real n00bie!

Stan Krasnow:)

---

### Post by phenest on 2008-10-15
> **BwackNinja said:**
> @phenest

That means that you at one point had conflicting versions of pulseaudio installed, and there's a mixup somewhere. Its looking for libpulsecore.so.5, while there is probably some other libpulsecore.so there. Either that or you have a missing symlink. Give the output of "locate libpulsecore"

```
steve@precision:~$ locate libpulsecore
/usr/lib/libpulsecore.so.7
/usr/lib/libpulsecore.so.7.0.0
/usr/share/doc/libpulsecore5
/usr/share/doc/libpulsecore5/README
/usr/share/doc/libpulsecore5/changelog.Debian.gz
/usr/share/doc/libpulsecore5/copyright
/var/lib/dpkg/info/libpulsecore5.list
/var/lib/dpkg/info/libpulsecore5.md5sums
/var/lib/dpkg/info/libpulsecore5.postinst
/var/lib/dpkg/info/libpulsecore5.postrm
/var/lib/dpkg/info/libpulsecore5.shlibs

```

---

### Post by psyke83 on 2008-10-15
> **phenest said:**
> ```
steve@precision:~$ locate libpulsecore
/usr/lib/libpulsecore.so.7
/usr/lib/libpulsecore.so.7.0.0
/usr/share/doc/libpulsecore5
/usr/share/doc/libpulsecore5/README
/usr/share/doc/libpulsecore5/changelog.Debian.gz
/usr/share/doc/libpulsecore5/copyright
/var/lib/dpkg/info/libpulsecore5.list
/var/lib/dpkg/info/libpulsecore5.md5sums
/var/lib/dpkg/info/libpulsecore5.postinst
/var/lib/dpkg/info/libpulsecore5.postrm
/var/lib/dpkg/info/libpulsecore5.shlibs

```

It seems you're using PulseAudio 0.9.12 from Luke's PPA. Try downgrading to Intrepid's official version (see the guide).

---

### Post by BwackNinja on 2008-10-15
Its PulseAudio 0.9.13 in the PPA now :D

---

### Post by keep-on-smiling on 2008-10-15
Hi

Can anyone comment on the stability of the fixes to Pulseaudio in Ubuntu Intrepid - I have kept everything standard, doing updates each day in the hopes of a cure, but have to set everything in sound preferences to OSS now to have continuous sound minus any crashes/freezes or pauses.

Just wondering if I am one of the few with this now - has it been fixed for most of ubuntu intrepid users ?

thanks

---

### Post by CFBauer on 2008-10-15
It won't let me thank anymore so I'm going to reply here to say thanks.

---

### Post by psyke83 on 2008-10-15
> **keep-on-smiling said:**
> Hi

Can anyone comment on the stability of the fixes to Pulseaudio in Ubuntu Intrepid - I have kept everything standard, doing updates each day in the hopes of a cure, but have to set everything in sound preferences to OSS now to have continuous sound minus any crashes/freezes or pauses.

Just wondering if I am one of the few with this now - has it been fixed for most of ubuntu intrepid users ?

thanks

It should work fine by default. There is the possibility that PulseAudio can be misconfigured from Hardy, however. Make sure you delete your ~/.asoundrc* files, as it says in this guide.

Otherwise, look at the [Hardy]("http://ubuntuforums.org/showthread.php?t=789578") version of the guide, Appendix B.

---

### Post by keep-on-smiling on 2008-10-15
hi

thankee thankee :)

will have a look at that right now - would love to be able to have it default, and still work !

cheers

umm one snag - I don't have that file you mention in my home directory - would deleting the .pulse and similar be worthwhile ?

---

### Post by psyke83 on 2008-10-15
> **keep-on-smiling said:**
> hi

thankee thankee :)

will have a look at that right now - would love to be able to have it default, and still work !

cheers

umm one snag - I don't have that file you mention in my home directory - would deleting the .pulse and similar be worthwhile ?

Yes. Step 3 of the guide does this (as well as ensuring you don't have incorrect packages installed).

---

### Post by phenest on 2008-10-15
> **psyke83 said:**
> It seems you're using PulseAudio 0.9.12 from Luke's PPA. Try downgrading to Intrepid's official version (see the guide).

Cheers. All works now including flash.

---

### Post by keep-on-smiling on 2008-10-15
Thanks psyke83

I am going to fiddle around using your guide - I was hoping the devs would get it sorted, but will have to have a go myself.

cheers

---

### Post by keep-on-smiling on 2008-10-15
Hi Psyke83 please would you wave an eyeball over the attached text - it is the result of pulseaudio -k; sleep 4; pulseaudio -vv on a fresh boot.

Basically I need some guidance here !!

cheers

---

### Post by psyke83 on 2008-10-15
> **keep-on-smiling said:**
> Hi Psyke83 please would you wave an eyeball over the attached text - it is the result of pulseaudio -k; sleep 4; pulseaudio -vv on a fresh boot.

Basically I need some guidance here !!

cheers

There seems to be no problems with this output. Try the other troubleshooting steps of Appendix B.

Do you have more than one sound card? PulseAudio may have chosen the wrong default card. In PulseAudio Volume Control, you can right-click on an application entry while it is playing audio, and move the stream to another device.

---

### Post by keep-on-smiling on 2008-10-15
OK back

I have to say that since I added the packages you suggested in the linked guide it does seem better - it used to lock / hiccup / pause within seconds prior to that... umm no, the pauses are still there - and I was not doing anything high cpu-wise - tho at least the sound keeps playing (does not seem to actually freeze) - will leave the box playing music tomorrow while I am at work - if it runs for 8 hours without a freeze I will be happy !!

The pulseaudio applet Volume meter playback shows music is playing happily enough with the meter moving up and down as appropriate.

Another aspect is when I run a test on the sound capture in system/preferences/sound - as soon as I hit the OK button in the small test window, the test window locks and I have to kill the sound prefs window to get rid of it.

oops - foregot: I have only one card, onboard:
Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

looks like I will need to play with the daemon.conf settings to fix the pauses

---

### Post by fjf on 2008-10-16
I have sound from my HDA intel from the analog out.  However, I want to activate the digital (optical) output (which used to work fine in hardy).  aplay -l gives:

 aplay -l
**** PLAYBACK list of Hardware Devices****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevice: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevice: 1/1
  Subdevice #0: subdevice #0

However, the ALC888 digital is not in the System-->preferences-->sound or in padevchooser to be selected.

Any hints?.

---

### Post by keep-on-smiling on 2008-10-16
hi psyke83

the pulseaudio is issue is here again seconds into a song rtythmbox froze - reckon I'll stick with OSS as I have no problems with this - maybe it will be fixed in the final release...

cheers

---

### Post by keep-on-smiling on 2008-10-16
hi

I deleted all the sound-related prefs in the home directory and setting the playback to alsa, with the sound capture set to OSS and default mixer to OSS Mixer - thus far all is stable

---

### Post by BwackNinja on 2008-10-16
Try giving us the output of "pulseaudio -k; sleep 4; pulseaudio -vv" like you did before, but in an interval including when you get pauses in rhythmbox. That should tell us what the problem is.

Default audio output in gstreamer-properties is autodetect, right?

---

### Post by se_landy on 2008-10-16
Hi, I installed intrepid beta today, had some bugs that managed to fix... but I still can't fix the cracking in sound... i read many posts about this bug, and tried some things that didn't work. Could someone please give me step by step instructions how to fix this bug... I am new to linux...

Offtopic: when i start video, it's blinking, in every video player... if someone has a link to fix this... :D

Excuse me for my English... :D

---

### Post by keep-on-smiling on 2008-10-16
hi BwackNinja

um.. nope - the only settings that have been consistently wobble-free is pure OSS in all sound settings - and believe me when I say I have tried every variation I can think of - it is way past my bedtime right now, but will set all back to standard and run the test using that command tomorrow.

it might even be a worthwhile option to re-install afresh, do all my updates and then run the test, as I have been fiddling quite a bit in the hopes of getting this going and thus the system may give misleading info. Would you want me to do this ?

a query before I go sleep: does OSS bypass Pulseaudio at all ?

thanks

---

### Post by psyke83 on 2008-10-16
> **keep-on-smiling said:**
> hi

um.. nope - the only settings that have been consistently wobble-free is pure OSS in all sound settings - and believe me when I say I have tried every variation I can think of - it is way past my bedtime right now, but will set all back to standard and run the test using that command tomorrow.

it might even be a worthwhile option to re-install afresh, do all my updates and then run the test, as I have been fiddling quite a bit in the hopes of getting this going and thus the system may give misleading info. Would you want me to do this ?

a query before I go sleep: does OSS bypass Pulseaudio at all ?

thanks

Yes, it bypasses it completely, what you're doing is not recommended at all. ALSA's OSS emulation doesn't support software mixing.

What I recommend: in System -> Preferences -> Sound, ensure all the playback settings are left to Autodetect. Don't touch them anymore.

Now, if you want to safely disable PulseAudio, go to Preferences -> Sessions, and in the Startup Programs tab, click "Add".

In the dialog, insert the following details:
> Name: Kill PulseAudio
Command: pulseaudio -k
Comment: Keep this item enabled to prevent PulseAudio from starting.

When you log out and back in, PulseAudio should be safely disabled and all applications will default to ALSA.

Edit: I amended these instructions, as it seems that gnome-settings-daemon is responsible for starting PulseAudio.

---

### Post by psyke83 on 2008-10-16
> **se_landy said:**
> Hi, I installed intrepid beta today, had some bugs that managed to fix... but I still can't fix the cracking in sound... i read many posts about this bug, and tried some things that didn't work. Could someone please give me step by step instructions how to fix this bug... I am new to linux...

Offtopic: when i start video, it's blinking, in every video player... if someone has a link to fix this... :D

Excuse me for my English... :D

The video problem is not related to PulseAudio. Do you mean crackling? The problem could be a few things.

Try this:

1. Close all sound applications.
2. Play a video that usually causes crackling, then close the movie player (important).
3. In a terminal, run:
```
$ pulseaudio -k
```
4. Play the same video as in step 2, and close.

Did the crackling stop on step 4? If so, look at the Hardy guide for information on buffering (link at the first post).

P.S. After this test, you will need to log out and back in to restart PulseAudio (or launch it from the terminal).

---

### Post by se_landy on 2008-10-16
That's why I said "Excuse me for my English" :P

this is what I got from terminal (step 3)

pulseaudio -k
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
W: main.c: High-priority scheduling enabled in configuration but not allowed by policy.
W: ltdl-bind-now.c: Failed to find original dlopen loader.

Video is still blinking, and crackling is even worse... :confused:

---

### Post by psyke83 on 2008-10-16
> **se_landy said:**
> That's why I said "Excuse me for my English" :P

this is what I got from terminal (step 3)

pulseaudio -k
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
W: main.c: High-priority scheduling enabled in configuration but not allowed by policy.
W: ltdl-bind-now.c: Failed to find original dlopen loader.

Video is still blinking, and crackling is even worse... :confused:

Some of that output looks strange, did you enable TheMuso's repository? I don't recommend that you use that version, it causes too many problems.

If the sound is still crackling when PulseAudio is disabled, then your problem is something else (with ALSA, perhaps).

---

### Post by se_landy on 2008-10-16
TheMuso??? How to disable it?? and how can I know if I disabled Pulseaudio?? :confused:

---

### Post by psyke83 on 2008-10-16
> **se_landy said:**
> TheMuso??? How to disable it?? and how can I know if I disabled Pulseaudio?? :confused:

Do not follow Step 1b of this guide. If you did follow this step, then you should follow the "Downgrade PulseAudio 0.9.12 -> 0.9.10" section.

Take care if you do not understand the instructions, I can't speak Croatian :).

---

### Post by se_landy on 2008-10-16
Tried the 1a in the first post - didn't work
tried 1b - also no change
tried downgrade - no change
turned off pulse audio in System->Preferences->Sessions - still have crackling sound

Well, I guess I'll have to wait for the final release... 
If someone has any more ideas, please tell me, I'm desperate... :(

---

### Post by se_landy on 2008-10-16
> **psyke83 said:**
> Do not follow Step 1b of this guide. If you did follow this step, then you should follow the "Downgrade PulseAudio 0.9.12 -> 0.9.10" section.

Take care if you do not understand the instructions, I can't speak Croatian :).

I understand English very well, but I'm not so good in writing... :)
As I'm new to linux, I thought that maybe I did't do something from the first post right...:confused:

---

### Post by psyke83 on 2008-10-16
> **se_landy said:**
> I understand English very well, but I'm not so good in writing... :)
As I'm new to linux, I thought that maybe I did't do something from the first post right...:confused:

If your sound is crackling when PulseAudio is disabled, it's not a PulseAudio problem.

---

### Post by DougieFresh4U on 2008-10-16
> **keep-on-smiling said:**
> hi psyke83

the pulseaudio is issue is here again seconds into a song rtythmbox froze - reckon I'll stick with OSS as I have no problems with this - maybe it will be fixed in the final release...

cheers
I have the same problem with rhythmbox also, but music in amarok plays with out stopping as it was in rhythmbox but, after I have played about 10 or so songs w/amarok it starts "skipping" as well as "speeding" through the song. Then I reboot and all is good in amarok for another 10 or so songs and repeat of problem. So repeat the cycle over again.

---

### Post by keep-on-smiling on 2008-10-17
Hi psyke83

hey great - disabling pulseaudio in the sessions section seems good so far - I have set sound playback prefs to autodetect, sound capture to ALSA Advanced Linux Sound Architecture and sound mixer to Alsa Mixer and then rebooted.

thus far I have heard 4 songs with perfect playback - no hops, pauses, glitches or whatever - will leave this running while I am at work and report back later.

One aspect on the side - in the past if I ran the sound capture test in the preferences/sound window, then the small test window ran, but froze when I press the OK button - now after the pulseaudio -k in sessions this does not happen any more :)

My thanks for that suggestion !!

cheers

---

### Post by soapytheclown on 2008-10-17
ive found that killing PA with pulseaudio -k then running pulse audio as sudo with sudo pulseaudio -v works for me, absolute pain in the **** since i have to do it on each boot but atleast it works hopefully this can help someone else out, oh i also added myself to the pulse, pulseaccess and pulse-rt groups dont think it really helped though

---

### Post by olskar on 2008-10-17
Hows pulseaudio on a clean install in Intrepid nowadays?

---

### Post by plun on 2008-10-17
> **olskar said:**
> Hows pulseaudio on a clean install in Intrepid nowadays?

Who knows ?...:)

I dont know what Ubuntus default login sound is for the moment, never heard it.

I also went up to PA ver .13 and its a mystery including Alsa .18RC3

No communications within bug reports also.... just users :(

---

### Post by psyke83 on 2008-10-17
> **plun said:**
> Who knows ?...:)

I dont know what Ubuntus default login sound is for the moment, never heard it.

I also went up to PA ver .13 and its a mystery including Alsa .18RC3

No communications within bug reports also.... just users :(

Luke's PA 0.9.13 packages aren't being tested for inclusion, and they simply don't work for many people.

As for the login sound; it works fine here, and should **for a default install**. There is still the possibility for a race condition due to the startup order, but Luke is working to improve things.

---

### Post by plun on 2008-10-17
> **psyke83 said:**
> Luke's PA 0.9.13 packages aren't being tested for inclusion, and they simply don't work for many people.

As for the login sound; it works fine here, and should **for a default install**. There is still the possibility for a race condition due to the startup order, but Luke is working to improve things.

Yup... I just find it strange that users find solutions and no developer
or maintainer comments any bug report about PulseAudio  :confused:

I went up to .13 just of curiosity and for example **"libcanberra.schemas"** is missing as I can see.

It sounds like "hell" playing ogg files but it works...

We cannot blow Intrepid in the same way as Hardy !!!

A more constructive testing breaks this ! :)   100% sure !

---

### Post by psyke83 on 2008-10-17
> **plun said:**
> Yup... I just find it strange that users find solutions and no developer
or maintainer comments any bug report about PulseAudio  :confused:

I went up to .13 just of curiosity and for example **"libcanberra.schemas"** is missing as I can see.

It sounds like "hell" playing ogg files but it works...

We cannot blow Intrepid in the same way as Hardy !!!

A more constructive testing breaks this ! :)   100% sure !

I don't understand what you mean... PA 0.9.13 has zero chance of being in Intrepid. You're testing packages that won't be part of the install, so why are you complaining?

---

### Post by keep-on-smiling on 2008-10-17
hi psyke83

pulseaudio -k in the session prefs definitely worked - I came home after work to find the music still playing :)

I going to go for a clean install sometime this weekend - and then will do all the updates - and then see how the sound behaves before I fiddle again.

cheers and thanks

---

### Post by plun on 2008-10-17
> **psyke83 said:**
> I don't understand what you mean... PA 0.9.13 has zero chance of being in Intrepid. You're testing packages that won't be part of the install, so why are you complaining?

I just tested to see the difference...  .13 is also "crazy" and needs 
a lot of specials... for example moving everything according your Hardy howto.

Libcanberra-schemas I especially noticed and its also within a bug report for 
Intrepids version.

It is probably also needed for Intrepid...

I also wonder about Consolekit...

> D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded

But the core devs maybe solves it up in their room...:)

---

### Post by keep-on-smiling on 2008-10-18
hi

I grabbed one of the daily snapshots - from 17th Oct and did a fresh install with that, grabbed some music to test and seconds into a tune the sounds lock - Yes I **know** this is a highly unstable, untested version, but I was really hoping that by now pulseaudio might be good.

As a general comment, I tried mandriva 2009 today as well - plenty of bugs there too and the system requires a more powerful machine than I have, but sound seemed fine.

Once again, my only answer is to stop pulseaudio in session prefs and in the services - running autodetect playback and alsa for the rest is fine.

If anyone can suggest tests I can do to nail this problem, please let me know - this install is purely to help bugfix and I just bought 3 gigs more bandwidth in preparation :)

Come on guys and gals, let's try to get the sound sorted in Intrepid - the terminal awaits your instructions !!

---

### Post by ShirishAg75 on 2008-10-19
Hi pyske83, 
 I opened up another thread for a game (widelands) its event sounds and music are not enabled. I have put up what I did [here]("http://ubuntuforums.org/showpost.php?p=5992343&postcount=6") . I also looked up [lpbug]188567[/lpbug] and it seems that there is an issue with libsdl1.2debian-pulseaudio as told by Mr. Alexander's [comment]("https://bugs.edge.launchpad.net/ubuntu/+source/zsnes/+bug/188567/comments/24") on the bug. I am going to try out what he says with widelands as well, let's see where that gets me. Comments, follow-ups welcome either here or at my thread, will be watching both for any ideas you may have.

---

### Post by keep-on-smiling on 2008-10-19
Right, a good night's sleep and back here again - did some perusing of the contents of /var/log/ and ran 

pulseaudio -k; sleep 4; pulseaudio -vv

both without rhythmbox and with, and then added evolution into the mix, and copy/pasted the applicable bits of the logs and the results of "pulseaudio -k; sleep 4; pulseaudio -vv" into a text file - attached.

hope the info therein might be of use to a dev

cheers

---

### Post by keep-on-smiling on 2008-10-19
just a comment - before doing the checks as above, I set the sound prefs back to standard and reboot.

cheers

---

### Post by psyke83 on 2008-10-19
> **ShirishAg75 said:**
> Hi pyske83, 
 I opened up another thread for a game (widelands) its event sounds and music are not enabled. I have put up what I did [here]("http://ubuntuforums.org/showpost.php?p=5992343&postcount=6") . I also looked up [lpbug]188567[/lpbug] and it seems that there is an issue with libsdl1.2debian-pulseaudio as told by Mr. Alexander's [comment]("https://bugs.edge.launchpad.net/ubuntu/+source/zsnes/+bug/188567/comments/24") on the bug. I am going to try out what he says with widelands as well, let's see where that gets me. Comments, follow-ups welcome either here or at my thread, will be watching both for any ideas you may have.

I have freshly installed Intrepid (with no changes to PulseAudio), installed widelands, and sound works out of the box. As I expected, sound works correctly with either libsdl1.2debian-alsa (installed by default) or libsdl1.2debian-pulseaudio.

The bug and comment you linked to refers to a specific bug in zsnes (it uses the libao audio backend, which seems to be broken), and has nothing to do with widelands.

Run widelands from the terminal to see if any debugging output can shed some light on your issue.

---

### Post by psyke83 on 2008-10-19
> **keep-on-smiling said:**
> just a comment - before doing the checks as above, I set the sound prefs back to standard and reboot.

cheers

Try editing /etc/pulse/daemon.conf, and comment (place ; at the beginning) the following lines:

```
resample-method = speex-float-1

default-fragments = 8
default-fragment-size-msec = 10
```

Restart PulseAudio (or logout and back in), and see if your sound remains stable.

---

### Post by ShirishAg75 on 2008-10-19
> **psyke83 said:**
> 

<snipped>

Run widelands from the terminal to see if any debugging output can shed some light on your issue.

Here's the output I get on the console :-

```

$ widelands
WARNING: Failed to initialize sound system: No available audio device

```

Any ideas? Using 2 channels simple speaker.

---

### Post by psyke83 on 2008-10-19
> **ShirishAg75 said:**
> Here's the output I get on the console :-

```

$ widelands
WARNING: Failed to initialize sound system: No available audio device

```

Any ideas? Using 2 channels simple speaker.

There are a few possible explanations:

Either PulseAudio is not configured correctly, which is causing mixing issues, or another running application has gained exclusive access to the sound card, which is preventing PulseAudio from working correctly.

I suggest that you monitor sound applications via PulseAudio Volume Control to ensure they are really using PulseAudio, and ensure you aren't running applications or daemons that may interfere.

Look at the Hardy version of my guide, Appendix B.

---

### Post by Spr0k3t on 2008-10-19
I'm trying to get pulseaudio working correctly on my system but I have not been able to yet.  I followed the guide in the first post of this thread.   I've filed a bug report on this issue as well.  The only way I can get sound is if I disable pulseaudio.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285965](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285965)

Any suggestions are welcome.

---

### Post by psyke83 on 2008-10-19
> **Spr0k3t said:**
> I'm trying to get pulseaudio working correctly on my system but I have not been able to yet.  I followed the guide in the first post of this thread.   I've filed a bug report on this issue as well.  The only way I can get sound is if I disable pulseaudio.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285965](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285965)

Any suggestions are welcome.

I haven't consolidated the information in these guides yet, so you'll need to refer to Appendix B of the Hardy guide (linked to the first post).

There you'll find troubleshooting steps to follow that can help us diagnose your problem. You may also want to attach the verbose PulseAudio log to your bug report (as well as here).

---

### Post by Spr0k3t on 2008-10-19
Troubleshooting from the other guide I got result C.  When I tried to load the volume control an error came up with "Connection failed: Connection refused".  I've attached an output of pulseaudio -vv.  Not sure what I'm looking for.

---

### Post by keep-on-smiling on 2008-10-19
Hi Psyke83

I have commented (added ; at the beginning) those lines - rebooted now and started the terminal with 

pulseaudio -k; sleep 4; pulseaudio -vv

and started rhythmbox after that - will leave it playing for a while and see what happens (also leaving Firefox and Evolution running too, as those would be my usual apps). Out of interest, what was the reasoning behind the commenting of those 3 lines ?

Thus far (5 minutes) it seems good.

Cheers

---

### Post by psyke83 on 2008-10-19
> **keep-on-smiling said:**
> Hi Psyke83

I have commented (added ; at the beginning) those lines - rebooted now and started the terminal with 

pulseaudio -k; sleep 4; pulseaudio -vv

and started rhythmbox after that - will leave it playing for a while and see what happens (also leaving Firefox and Evolution running too, as those would be my usual apps). Out of interest, what was the reasoning behind the commenting of those 3 lines ?

Thus far (5 minutes) it seems good.

Cheers

I saw references to buffer underruns in your verbose output. By commenting those lines, perhaps those underruns will no longer occur. It's a long shot, but let's see if it works.

---

### Post by psyke83 on 2008-10-19
> **Spr0k3t said:**
> Troubleshooting from the other guide I got result C.  When I tried to load the volume control an error came up with "Connection failed: Connection refused".  I've attached an output of pulseaudio -vv.  Not sure what I'm looking for.

It seems you've enabled some of the networking options in PulseAudio, correct? I suggest you delete (or move away) all your user configuration for PulseAudio, then restart PulseAudio.

```
$ rm ~/.pulse/*
$ pulseaudio -k && pulseaudio -vv
```

---

### Post by Spr0k3t on 2008-10-19
> **psyke83 said:**
> It seems you've enabled some of the networking options in PulseAudio, correct? I suggest you delete (or move away) all your user configuration for PulseAudio, then restart PulseAudio.

If I have, then it's something installed from the upgrade to ibex.

> **psyke83 said:**
> ```
$ rm ~/.pulse/*
$ pulseaudio -k && pulseaudio -vv
```

```
$ pulseaudio -k && pulseaudio -vv
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: Failed to kill daemon.
```

---

### Post by psyke83 on 2008-10-19
> **Spr0k3t said:**
> If I have, then it's something installed from the upgrade to ibex.



```
$ pulseaudio -k && pulseaudio -vv
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: Failed to kill daemon.
```

That output suggests that the pulseaudio process didn't exit successfully. Try:

```
$ pkill pulseaudio; sleep 5; pulseaudio -vv
```

---

### Post by keep-on-smiling on 2008-10-19
Hi Psyke83

Well, I am amazed... :) music has played for over an hour with no freezes wobbles, splutters or pauses.

Such a simple correction for such an irritating problem :)

It might be premature, but I think that is that problem fixed (grin)

An interesting aspect is that the sound capture test (set to Alsa as per default) still freezes when I click on the OK window at the end of the test and the terminal outputs a long stream of

D: memblock.c: Pool full

continuing until I manage to kill the window - and yet in the meantime, the music continues perfectly !! This is wonderful !!

What would you like me to fiddle with to try to sort the freeze in sound capture ?

Thank You for the playback fix !!

cheers

PS:

here is the tail end of the sound capture freeze

D: memblock.c: Pool full
D: memblock.c: Pool full
D: memblock.c: Pool full
D: memblock.c: Pool full
D: module-suspend-on-idle.c: Source alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0 becomes idle.
I: source-output.c: Freeing output 1 "ALSA Capture"

---

### Post by Polygon on 2008-10-19
your guide did not work for me. pulse audio is working, but i get no sound from it, and i only get sound if i set in system>prefs>sound and set everything to USB headset (OSS)

---

### Post by keep-on-smiling on 2008-10-19
Hi Polygon

Just a thought: I have been battling for quite some - back from Hardy, doing re-install after re-install, and only now, using a daily build and commenting 3 lines in daemon.conf in the pulse directory as a suggestion by psyke83, have I managed to get sound to behave itself. I would guess that the devs have almost fixed pulseaudio, but you may need to do a clean install of a recent Intrepid to get the benefit.

I too was forced to disable pulseaudio, tho in my case via the session prefs was fine.

Are you running a clean install - or an upgrade from hardy ?

cheers

---

### Post by psyke83 on 2008-10-19
> **Polygon said:**
> your guide did not work for me. pulse audio is working, but i get no sound from it, and i only get sound if i set in system>prefs>sound and set everything to USB headset (OSS)

If you have a USB headset attached, PulseAudio would happily select it as the default sink - which is not what you would want.

Set all the options back to Autodetect in System/Preferences/Sound, and play something in Totem. While it is playing, open the PulseAudio Volume Control, and right-click on the Totem entry in the Playback tab. When you right-click, choose the option Move Stream, and try all available options.

Otherwise, try the troubleshooting steps of Appendix B in the Hardy guide.

---

### Post by Spr0k3t on 2008-10-19
> **psyke83 said:**
> That output suggests that the pulseaudio process didn't exit successfully. Try:

```
$ pkill pulseaudio; sleep 5; pulseaudio -vv
```

k, got that... here's the output attached

---

### Post by psyke83 on 2008-10-19
> **Spr0k3t said:**
> k, got that... here's the output attached

That output indicates that PulseAudio is working correctly, but it has chosen a USB device as the default sink (i.e. default playback device).

See my last reply to Polygon, and try moving the stream during playback of content.

If the above works for you, you can either a) edit /etc/pulse/default.pa or b) use padevchooser to set the proper sink as default.

---

### Post by Spr0k3t on 2008-10-19
> **psyke83 said:**
> That output indicates that PulseAudio is working correctly, but it has chosen a USB device as the default sink (i.e. default playback device).

See my last reply to Polygon, and try moving the stream during playback of content.

If the above works for you, you can either a) edit /etc/pulse/default.pa or b) use padevchooser to set the proper sink as default.

It sort of works.  Meaning I can move the audio to the USB headset, but that's it.  I don't have any other audio.

---

### Post by psyke83 on 2008-10-19
> **Spr0k3t said:**
> It sort of works.  Meaning I can move the audio to the USB headset, but that's it.  I don't have any other audio.

When you move it to your sound card, there's silence? It could be something as simple as the volume. Ensure the sliders are not low/muted via GNOME Volume Control or:

```
$ alsamixer -Dhw
```

Once you can get even one application to play sound correctly on your sound card, then it's simply a matter of configuring PulseAudio to use the correct device by default.

---

### Post by Polygon on 2008-10-19
> **psyke83 said:**
> If you have a USB headset attached, PulseAudio would happily select it as the default sink - which is not what you would want.

Set all the options back to Autodetect in System/Preferences/Sound, and play something in Totem. While it is playing, open the PulseAudio Volume Control, and right-click on the Totem entry in the Playback tab. When you right-click, choose the option Move Stream, and try all available options.

Otherwise, try the troubleshooting steps of Appendix B in the Hardy guide.

wow, that worked!

now how do i make it so it uses that stream by default without having me to move the stream every time i play something?

---

### Post by mc4100 on 2008-10-19
> **psyke83 said:**
> 
<snip>
```
$ alsamixer -Dhw
```


It's funny, I'd just been trying to figure out that command for days. 
Every time I update (kernel? pulseaudio?), it seems to mute the PCM, which was always fixable in gnome-volume-control ... but recently, it only shows "Master"; so eventually, I ended up installing gnome-alsamixer. Do you know of any way to restore functionality in "Volume Control" to the equivalent of alsamixer -Dhw?

---

### Post by psyke83 on 2008-10-19
> **Polygon said:**
> wow, that worked!

now how do i make it so it uses that stream by default without having me to move the stream every time i play something?

You have two options:
1. PulseAudio Manager, Devices tab. Look at the listed sinks - the name should give an indication of usb or pci - the pci card is your "real" sound card. Copy that full sink name.

Edit /etc/pulse/default.pa. On the second-last line you'll see:

```
#set-default-sink output
```

Uncomment (remove #), and change "output" to the full sink name that you copied from PulseAudio Manager. For example, in **my** case (it's unique to each card):

```
set-default-sink alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0
```

**OR**

2. Open the PulseAudio Volume Control, Output Devices tab. Right-click on the desired default sound card, and ensure that the "Default" menu item is checked. You can verify that this setting has taken effect by checking PulseAudio Manager's Server Information. 

The second option is probably better, but if hotplugging interferes with this, then option 1 will set a default sink permanently.

---
N.B. By design, PulseAudio keeps a record of the last used sink for each client that connects. This may result in some applications appearing not to respect your new default sink. The answer is manually switch streams in the PA Volume Control, or to delete this recently-used list:

```
$ rm ~/.pulse/volume-restore.table
```

Edit: adjusted instructions (PA Device Chooser method no longer recommended)

---

### Post by Polygon on 2008-10-19
much love psyke83. Now sound works perfectly, including youtube when other sources of sound are playing. ^^

---

### Post by psyke83 on 2008-10-19
> **mc4100 said:**
> It's funny, I'd just been trying to figure out that command for days. 
Every time I update (kernel? pulseaudio?), it seems to mute the PCM, which was always fixable in gnome-volume-control ... but recently, it only shows "Master"; so eventually, I ended up installing gnome-alsamixer. Do you know of any way to restore functionality in "Volume Control" to the equivalent of alsamixer -Dhw?

The GNOME Volume Control applet should still show all your mixers correctly. Ensure that the selected device is **not** a PulseAudio mixer, such as:
> Playback: ALSA PCM on front:0 (Intel ICH5) via DMA (PulseAudio mixer)

It should be something like:
> Intel ICH5 (Alsa mixer)

---

### Post by Spr0k3t on 2008-10-19
> **psyke83 said:**
> When you move it to your sound card, there's silence? It could be something as simple as the volume. Ensure the sliders are not low/muted via GNOME Volume Control or:

```
$ alsamixer -Dhw
```

Once you can get even one application to play sound correctly on your sound card, then it's simply a matter of configuring PulseAudio to use the correct device by default.

Still no luck.  If I do "killall pulseaudio" I get audio output without any problems... I checked the settings of alsamixer to see if there were any changes on log registers or incorrectly muted options but the settings were identical.  I had this same problem when hardy was released and just pulled pulseaudio out completely.  Later I reinstalled hardy on a new harddrive and got pulseaudio working, but now with the ibex upgrade, I'm back at square one.

---

### Post by psyke83 on 2008-10-19
> **Spr0k3t said:**
> Still no luck.  If I do "killall pulseaudio" I get audio output without any problems... I checked the settings of alsamixer to see if there were any changes on log registers or incorrectly muted options but the settings were identical.  I had this same problem when hardy was released and just pulled pulseaudio out completely.  Later I reinstalled hardy on a new harddrive and got pulseaudio working, but now with the ibex upgrade, I'm back at square one.

Well, all I can suggest is you look at post [#322]("http://ubuntuforums.org/showpost.php?p=5997459&postcount=322") (in fact, all the replies to Polygon also apply for you). You didn't indicate whether there was a choice of multiple sinks beyond your usb device (which I saw in your log).

---

### Post by Spr0k3t on 2008-10-19
> **psyke83 said:**
> Well, all I can suggest is you look at post [#322]("http://ubuntuforums.org/showpost.php?p=5997459&postcount=322") (in fact, all the replies to Polygon also apply for you). You didn't indicate whether there was a choice of multiple sinks beyond your usb device (which I saw in your log).

K, I'll check into that.  However, I didn't know I even had multiple sinks until now.

---

### Post by mc4100 on 2008-10-19
> **psyke83 said:**
> The GNOME Volume Control applet should still show all your mixers correctly. Ensure that the selected device is **not** a PulseAudio mixer.
I remember this is how it was, a mix of mixers (pulseaudio and alsamixer), but now they're **all** Pulseaudio mixers.


Edit: I've attached a screenshot showing all I have to work with. One Playback (Pulseaudio), which provides only the "master" channel. One equally useless OSS one, as shown, and two for Capture.

---

### Post by psyke83 on 2008-10-19
> **mc4100 said:**
> I remember this is how it was, a mix of mixers (pulseaudio and alsamixer), but now they're **all** Pulseaudio mixers.

Then perhaps the ALSA kernel module for your sound card didn't load properly. PulseAudio is only a sound server; it is an ALSA client and thus requires the appropriate ALSA kernel modules to be loaded and functioning properly.

I suggest you check your dmesg log for any mention to your sound card.

---

### Post by Spr0k3t on 2008-10-19
Okay, I really don't know what I'm doing wrong here.  I just went through and verified my sink is set to default to the output of the PCI card (using option #2 in post 322).  I did a "pulsaudio -k; sleep 5; pulseaudio -vv" and there was no change.  I verified on the pulse audio manager that my default sink was the correct sound card (alsa_output.pci_1102_4_sound_card_0_alsa_playback_0).  No dice yet.  I went back and did option 1 by editing the /etc/pulse/default.pa and adding the correct sink to the default... no change.

I can still kill the pulseaudio process and sound is instantly restored without having to restart any apps or streams.

---

### Post by mc4100 on 2008-10-19
> **psyke83 said:**
> Then perhaps the ALSA kernel module for your sound card didn't load properly. PulseAudio is only a sound server; it is an ALSA client and thus requires the appropriate ALSA kernel modules to be loaded and functioning properly.

I suggest you check your dmesg log for any mention to your sound card.

I've updated my above post with a screenshot of gnome-volume-control, and I'll attach another showing:
```
alsamixer -Dhw
```
Would I still be able to see this, if there were problems with the kernel module? (also, sound playback is perfect, just that it mutes itself sometimes, and I can't unmute it (graphically anyway), since gnome-volume-control provides no way to change the PCM).

---

### Post by mc4100 on 2008-10-19
Ah, after digging about, I found a solution:
gnome-volume-control is, oddly enough, **gstreamer** based ...
So I had a look in synaptic and found gstreamer0.10-alsa was *not* installed (-pulseaudio was though): after I installed it, I had access to alsamixer in gnome-volume-control.
Thanks for you help anyway, Psyke83.

---

### Post by jaklumen on 2008-10-20
Howdy.

I responded before in the "full" thread, but some things have changed since then.

I had gotten sound output in Flash to work, but I had to uninstall most of the packages to get things to work.  I got an SB! Live 5.1 sound card [SB0220] to take over sound mixing, which seemed to work. Then after certain updates, I lost all sound.

I upgraded to 8.10 and found I suddenly had options in Preferences -> Sound for the sound card, specifically.  I found the only options in Sound Preferences that would work was to set all sound playback to Multichannel Playback (ALSA) per se the SB! Live card.  I didn't get sound with "Autodetect".

I can't get any sound from Flash whatsoever now.  What seemed to work back in 8.04 was to use the nsidwrapper (I'm probably spelling it wrong) even though I am not using the 64-bit version.  I'm at a total loss on what to do now.

---

### Post by psyke83 on 2008-10-20
> **jaklumen said:**
> Howdy.

I responded before in the "full" thread, but some things have changed since then.

I had gotten sound output in Flash to work, but I had to uninstall most of the packages to get things to work.  I got an SB! Live 5.1 sound card [SB0220] to take over sound mixing, which seemed to work. Then after certain updates, I lost all sound.

I upgraded to 8.10 and found I suddenly had options in Preferences -> Sound for the sound card, specifically.  I found the only options in Sound Preferences that would work was to set all sound playback to Multichannel Playback (ALSA) per se the SB! Live card.  I didn't get sound with "Autodetect".

I can't get any sound from Flash whatsoever now.  What seemed to work back in 8.04 was to use the nsidwrapper (I'm probably spelling it wrong) even though I am not using the 64-bit version.  I'm at a total loss on what to do now.

You mention that you had to remove packages - I have no idea what was removed, so your system could be completely hosed. However, I suspect that your problem is quite simple - PulseAudio is using your onboard sound (or the card that isn't hooked up to speakers) as the default sink.

Here's what I recommend:
[LIST=1]
[*]Follow steps 2-4 of this Intrepid guide (omit 1a and 1b, and if you have already upgraded to PA 0.9.13, then downgrade according to the instructions).
[*]Get rid of nspluginwrapper:```
$ sudo apt-get remove --purge nspluginwrapper flashplugin-nonfree
$ sudo apt-get install flashplugin-nonfree
```
[*]Reboot, or log out and back in.
[*]Read post [#315]("http://ubuntuforums.org/showpost.php?p=5995963&postcount=315") and follow the directions to move streams in Totem.
[*]If you have success from post #315, read post [#322]("http://ubuntuforums.org/showpost.php?p=5997459&postcount=322") and follow the second procedure to change the default sound card[COLOR="Red"]*[/COLOR].
[/LIST]

[COLOR="Red"]*[/COLOR] Note: post 322 is a reply to a user with a sound card and USB audio device. According to your previous posts, your system has two sound cards (none of which are USB). Nevertheless, the same advice applies - you need to configure PulseAudio to select the correct sound card as the default sink.

---

### Post by jaklumen on 2008-10-20
> **psyke83 said:**
> PulseAudio is using your onboard sound (or the card that isn't hooked up to speakers) as the default sink.

Yes. From the Pulse Audio menus (Volume Control and Manager), it is detecting both onboard sound cards.  I should have clarified that there are three pieces of sound hardware:

- The front onboard (to use the jacks on the front of the case)
- The back onboard
- The SB! Live sound card

From the information on Output Devices on Volume Control and Devices on the Manager lists, it would seem that Pulse Audio is not detecting the SB card, which is what the speakers are hooked up to.  I am getting sound through Totem but still no sound through Flash and no sound input through a microphone.

I followed post #315- the sink that worked was alsa_output.pci_1102_2_sound_card_0_alsa_playback_0
or ALSA PCM on front:0 (ADC Capture/Standard Playback) via DMA. I was expecting an entry for the SB card.

Under Sound Preferences there are both drop down options for the SB card under Playback-- 3 for ALSA and 3 for OSS, so I know that they at least show up there.

Does the selection of Default Mixer Tracks make any difference at all?  Right now, I have it set to the SB card with the Alsa Mixer.

I hope I'm understanding everything right.

---

### Post by shu on 2008-10-20
Does anybody use external SB Connect soundcard? It used to work perfectly in hardy, but in ibex it a disaster. Digital out doesn't work at all, I mean it does something, but nothing that could be recognized by A/V receiver. On analog output it's awful too, like there are serious resampling issues, sound is distorted, too slow, etc. Any hints?

---

### Post by jaklumen on 2008-10-21
psyke,

Out in the Google "jungle" I found a post on another forum suggesting to disable onboard sound in the BIOS.  I also created a new ~/.asoundrc (again) according to Part A (core fixes) step five in your [PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?p=4928900") guide.

I went and disabled the onboard sound (specifically, the chip) in my BIOS, and if I understand the ~/.asoundrc script correctly, it sent output to the SB card.  Either way, Flash is giving me sound again.

Not sure if this fixes everything-- I'll have to see which headphone jack is working (if it's the SB jack or the ones on the front of the case-- part of the onboard?) and then go from there.  Thanks for your help, though.

---

### Post by psyke83 on 2008-10-21
> **jaklumen said:**
> psyke,

Out in the Google "jungle" I found a post on another forum suggesting to disable onboard sound in the BIOS.  I also created a new ~/.asoundrc (again) according to Part A (core fixes) step five in your [PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?p=4928900") guide.

I went and disabled the onboard sound (specifically, the chip) in my BIOS, and if I understand the ~/.asoundrc script correctly, it sent output to the SB card.  Either way, Flash is giving me sound again.

Not sure if this fixes everything-- I'll have to see which headphone jack is working (if it's the SB jack or the ones on the front of the case-- part of the onboard?) and then go from there.  Thanks for your help, though.

Don't mix the instruction for Hardy with an Intrepid system. There is no need for any .asoundrc file in Intrepid, as ALSA autodetects the presence of PulseAudio. 

Disabling onboard sound will merely ensure that PulseAudio only has one option to choose - so it's a workaround, not a fix. Setting the default sink (i.e. sound card) is trivial, as I explain a few posts back.

---

### Post by jaklumen on 2008-10-21
> **psyke83 said:**
> Don't mix the instruction for Hardy with an Intrepid system. There is no need for any .asoundrc file in Intrepid, as ALSA autodetects the presence of PulseAudio. 

Disabling onboard sound will merely ensure that PulseAudio only has one option to choose - so it's a workaround, not a fix. Setting the default sink (i.e. sound card) is trivial, as I explain a few posts back.

I'm sorry, but that's not very helpful.

I already implied, although perhaps not directly stated, that I figured it was a workaround and not a permanent fix.

If you wish additional information, I will gladly supply it, but for now I will consider the matter resolved until circumstances or other things dictate that I should seek a more permanent fix.  I am certain it is not properly fixed, but I have already torn out a lot of hair over this, and I do not wish to pursue it further if it currently works acceptably to my satisfaction.

---

### Post by psyke83 on 2008-10-21
> **jaklumen said:**
> I'm sorry, but that's not very helpful.

I already implied, although perhaps not directly stated, that I figured it was a workaround and not a permanent fix.

If you wish additional information, I will gladly supply it, but for now I will consider the matter resolved until circumstances or other things dictate that I should seek a more permanent fix.  I am certain it is not properly fixed, but I have already torn out a lot of hair over this, and I do not wish to pursue it further if it currently works acceptably to my satisfaction.

Sure, the method you used is fine, though there is still the potential for breakage. For example, if you later plug in a USB headset, you'll experience the same problem (PulseAudio will erroneously select the USB headset as the default card). I was just informing you how to resolve the problem without resorting to BIOS settings.

As the saying goes, if it ain't broken, don't fix it ;). I only recommend that you delete the ~/.asoundrc file, as it's no longer necessary. The advantage of deleting this file is that ALSA applications will automatically fall back to the regular "dmix" ALSA device if there is a problem connecting to the PulseAudio server.

---

### Post by jaklumen on 2008-10-22
> **psyke83 said:**
> For example, if you later plug in a USB headset, you'll experience the same problem

I've had too many problems with USB headsets in the past-- more than likely I'll stick to ones that use the stereo mini jacks; therefore I was wondering if the problem was the same or not.

> I was just informing you how to resolve the problem without resorting to BIOS settings.

Yes, I understand, I followed everything as carefully as possible, but I was trying to say that I did not see any specific detection of the SB sound card in Pulse Audio settings.

---

### Post by Chazall1 on 2008-10-22
I have posted before on this issue. Your post worked fine up untill yesterdays update. I have used this info for the past week and pulse and all sounds have worked. I did the updates today and pulse is functioning perfectly, the playback meter works for all my sound apps,... 
I indicated a few days ago I gor sound to work by killing PA
with  pulseaudio -k  and running
pulseaudio -D --log-target=syslog 
it works flawlessly or atleast the sound doesn't break untill last night. I have also ran pulseaudio -v and get not errors, and I have no sound!!!!! But PA is functioning properly

Thanks

---

### Post by Chazall1 on 2008-10-23
I found the problem!!!!
I opened the gnome sound control, and noticed that the PCM volume was muted.
That solved it. I need to pay better attention to details in this post. Thanks for assisting, your page 1 works great.

---

### Post by Spr0k3t on 2008-10-25
God this is just driving me insane.  What steps do I need to take to remove pulseaudio from my system as it's still not working.  I've removed sound cards, usb headphones, enabled onboard audio, disabled onboard audio, added different sound cards but still no luck.  The only thing that has worked 100% every time is if I "$ killall pulseaudio" and from there I have absolutely no problems with sound.

In appendix B of the other thread I have a different result from the three listed possibilities.  I have no audio, but each stream is showing up in the playback of the Volume Control Manager for each application.  I've verified my card is the correct output.  I've checked to make sure the audio levels are not muted, still nothing.

So, can I just completely ditch pulseaudio or is there a definitive way of testing to make sure it's working properly with the system?

---

### Post by kylea on 2008-10-25
I do this via a script and PA works

#!/bin/bash
pulseaudio -k >/dev/null 2>&1
pulseaudio -D
pulseaudio


I have this in the Session start up to automatically do  - but it seems to stopped 'fixing it' automatically.

If I run it after the desktop is loaded it allows PA to work.

Hope this provides some relief!.:)

---

### Post by phorgan1 on 2008-10-25
Your guide for Hardy really helped, but now that I'm on Ibex, there is no joy.  I've done everything you suggested, (and everything everyone's suggested), but no sound at all.  The right drivers are loaded for my intel integrated audio, every test anyone gives me passes with flying colors, everything is exactly perfect--except it isn't, because there's no sound at all.  Any suggestions to help me diagnose this would be gratefully followed.

Patrick

---

### Post by psyke83 on 2008-10-25
> **phorgan1 said:**
> Your guide for Hardy really helped, but now that I'm on Ibex, there is no joy.  I've done everything you suggested, (and everything everyone's suggested), but no sound at all.  The right drivers are loaded for my intel integrated audio, every test anyone gives me passes with flying colors, everything is exactly perfect--except it isn't, because there's no sound at all.  Any suggestions to help me diagnose this would be gratefully followed.

Patrick

EDIT: My apologies. I thought I was replying to the Hardy thread.

It seems a lot of users are having problems with the PCM mixer erroneously being set to 0 or muted.

Check the volume levels:
```
$ alsamixer -Dhw
```

---

### Post by Spr0k3t on 2008-10-26
> **psyke83 said:**
> EDIT: My apologies. I thought I was replying to the Hardy thread.

It seems a lot of users are having problems with the PCM mixer erroneously being set to 0 or muted.

Check the volume levels:
```
$ alsamixer -Dhw
```

Just out of curiosity, what other options are there if the PCM is set correctly.  I don't have the option to mute the PCM.  I've attached a grab of my desktop with two alsamixer -Dhw windows.  The top is prior to running pulseaudio -vv the bottom is after.  Here's my alsa-info.sh output.

[http://www.alsa-project.org/db/?f=c5f0c424a7a8126ddb3e62cb3808f2d79a15266e](http://www.alsa-project.org/db/?f=c5f0c424a7a8126ddb3e62cb3808f2d79a15266e)

I'm stumped.

---

### Post by psyke83 on 2008-10-26
> **Spr0k3t said:**
> Just out of curiosity, what other options are there if the PCM is set correctly.  I don't have the option to mute the PCM.  I've attached a grab of my desktop with two alsamixer -Dhw windows.  The top is prior to running pulseaudio -vv the bottom is after.  Here's my alsa-info.sh output.

[http://www.alsa-project.org/db/?f=c5f0c424a7a8126ddb3e62cb3808f2d79a15266e](http://www.alsa-project.org/db/?f=c5f0c424a7a8126ddb3e62cb3808f2d79a15266e)

I'm stumped.

The "External amplifier" can mute all sound if it is set incorrectly, though this seems not to be the case for you. If your sound works correctly when PulseAudio is not running, then it is definitely a problem in PulseAudio.

What I can't understand is that your output is showing combined sinks and a network presence. This is not the default configuration of PulseAudio (and I don't recommend *any* customization of the PulseAudio configuration until basic functionality is achieved).

---

### Post by Spr0k3t on 2008-10-26
> **psyke83 said:**
> What I can't understand is that your output is showing combined sinks and a network presence. This is not the default configuration of PulseAudio (and I don't recommend *any* customization of the PulseAudio configuration until basic functionality is achieved).

Not sure where you see that.  Not sure where or how that was set up either.  I followed the guide exactly at least six times.  If there's something I can do to reset everything to default and start from scratch, that may help.  Thanks again for putting up with this issue.  I hope, with all the help I'm getting, that we can solve this issue eventually.

I've prepped a spare drive that I'm going to reinstall ibex on... hopefully the raw install will show us where the issue is.

---

### Post by CyberPrime on 2008-10-28
This one solved it! Probably after the fixes provided in the original post. Please include this command in the first post as it will probably help a lot of people!

> **psyke83 said:**
> EDIT: My apologies. I thought I was replying to the Hardy thread.

It seems a lot of users are having problems with the PCM mixer erroneously being set to 0 or muted.

Check the volume levels:
```
$ alsamixer -Dhw
```

---

### Post by ercdvs on 2008-10-28
Followingthis guide but no change on my Dell 1705 laptop.  Sound is still played back as static and pops..

Interesting to note in my kern.log

> 
Oct 28 19:48:43 uberlaptop pulseaudio[5923]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct 28 19:48:43 uberlaptop pulseaudio[5925]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Oct 28 19:48:43 uberlaptop pulseaudio[5925]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted


I should be up to date with everything.. and google is giving mixed results on this.. any ideas on what to try ?

Linux uberlaptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux\

pulseaudio -vv revealed that I am on 0.9.10 ..   trying some of the suggestions in the log output

---

### Post by zekopeko on 2008-10-28
ercdvs is it like cracking noises when you play any audio?

---

### Post by ercdvs on 2008-10-28
> **zekopeko said:**
> ercdvs is it like cracking noises when you play any audio?

yes, any audio..  but here is the strange thing.. I played with some volume levels under the GNOME ALSA mixer ... and suddenly I hear audio properly.

... oh, i also did add myself to the pulse-rt group... but that seemed to have no effect previously.

I still get those errors in the logs though.  very strange.

Technically its working, but I can't see exactly why.

---

