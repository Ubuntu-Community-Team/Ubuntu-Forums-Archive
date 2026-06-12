---
title: "Gnome without Pulseaudio, posssible?"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Macchia on 2010-03-15
Since i don't like pulseaudio (too many problems, solved switching to alsa), there's a way to install gnome without it?

---

### Post by Objekt on 2010-03-15
You were able to switch to ALSA on a current Ubuntu distro?  How did you do it?  I've purged Pulseaudio before, but at the cost of having any sound at all.  I had no idea how to fix it, so I went back to Pulseaudio.

---

### Post by Macchia on 2010-03-15
i switched to xfce4 removing gnome and all its dependencies (pulseaudio too)

---

### Post by Psumi on 2010-03-15
you can't record sound in gtk-recordmydesktop without pulse.

---

### Post by Macchia on 2010-03-15
> **Psumi said:**
> you can't record sound in gtk-recordmydesktop without pulse.

what you mean?

---

### Post by Half-Left on 2010-03-15
The distro implements the PulseAudio into GNOME and the gnome volume applet supports it.

You might want try and run the esd daemon and install the gstreamer/xine-esd packages once you delete PA.

---

### Post by Psumi on 2010-03-15
> **Macchia said:**
> what you mean?

jackd is useless anyway, so using pulse for recording audio for your screencast videos using gtk-recordmydesktop is the easiest way to do it.

I had to have two extra programs running to have jackd be able to record audio for gtk-recordmydesktop.

How can I record my audio using gtk-recordmydesktop without pulse then (And using ALSA, NOT OSS), if you don't get what I mean?

---

### Post by Macchia on 2010-03-15
> **Psumi said:**
> jackd is useless anyway, so using pulse for recording audio for your screencast videos using gtk-recordmydesktop is the easiest way to do it.

I had to have two extra programs running to have jackd be able to record audio for gtk-recordmydesktop.

How can I record my audio using gtk-recordmydesktop without pulse then (And using ALSA, NOT OSS), if you don't get what I mean?

How about making Pulseaudio an option instead of force it.

---

### Post by Psumi on 2010-03-15
> **Macchia said:**
> How about making Pulseaudio an option instead of force it.

Fork?

---

### Post by Half-Left on 2010-03-15
> **Macchia said:**
> How about making Pulseaudio an option instead of force it.

Sound never just worked great like it does now days in Linux, it was rather a mess. The hardcore geeks will say Alsa did it all perfectly well before PA came along, which is false. Multiple sound sources and microphones where a regular issue.

---

### Post by Objekt on 2010-03-15
What sound implementation did Kubuntus 8.04 and 8.10 use?  I tried those a couple of years ago on the hardware listed in my signature, but found that only one program at a time could produce sound (or accept microphone input).  That was a Big Problem for many reasons.

Amazingly, I haven't had any sound problems in 9.10, except for a couple of applications that do not use PulseAudio correctly.  I would like to try them with a non-PulseAudio sound implementation, but have yet to figure out how.  I certainly don't want the "first program to run monopolizes sound hardware" bug to crop up again.

---

### Post by Macchia on 2010-03-15
> **Half-Left said:**
> Sound never just worked great like it does now days in Linux, it was rather a mess. The hardcore geeks will say Alsa did it all perfectly well before PA came along, which is false. Multiple sound sources and microphones where a regular issue.

Since you are saying you feel confortable with PA, why people like me who use alsa confortable as you should be forced to use PA? this is why i hope in choosing and not forcing (if i remember correctly linux is the power of choice).
Btw my mic works fine with alsa, bad with pulse.

---

### Post by Half-Left on 2010-03-15
> **Macchia said:**
> Since you are saying you feel confortable with PA, why people like me who use alsa confortable as you should be forced to use PA? this is why i hope in choosing and not forcing (if i remember correctly linux is the power of choice).
Btw my mic works fine with alsa, bad with pulse.

It's not "forced", Canonical made it a dependency on their packages. I've also heard that distros do not set up PA correctly. Fedora do the same with their KDE4 version, of which KDE4 upstream doesn't use PA, it's just optional.

Distros 'pick' the technology hoping it's the best choice and I don't think picking sound servers for Ubuntu will make it do well on the desktop.

---

### Post by Macchia on 2010-03-15
> **Half-Left said:**
> It's not "forced", Canonical made it a dependency on their packages. I've also heard that distros do not set up PA correctly. Fedora do the same with their KDE4 version, of which KDE4 upstream doesn't use PA, it's just optional.

Distros 'pick" the technology hoping it's the best choice and I don't think picking sound servers for Ubuntu will make it do will on the desktop.

well, i call it "forced" because, as you said, some other distros made it optional.

---

### Post by Half-Left on 2010-03-15
> **Macchia said:**
> well, i call it "forced" because, as you said, some other distros made it optional.

no, in KDE4 it's optional. I'm pretty sure if you use a vanilla GNOME, they still use esd.

> For those without PulseAudio, the old (GStreamer) mixer will still be available and has even been augmented with a sound theme tab to match the new interface.

---

### Post by Macchia on 2010-03-15
in Archlinux is an option (this is what i know)

---

### Post by gradinaruvasile on 2010-03-15
In Debian is optional too. And it works better than the Ubuntu implementation if installed.

---

### Post by sonicb00m on 2010-03-16
I think PA is awesome. The only problem I have with it is that there is now way too much latency in Skype to make it usable.

---

### Post by Macchia on 2010-03-16
> **sonicb00m said:**
> I think PA is awesome. The only problem I have with it is that there is now way too much latency in Skype to make it usable.

many programs like skype have latency issues (teamspeak for example)

---

### Post by Psumi on 2010-03-16
> **Macchia said:**
> many programs like skype have latency issues (teamspeak for example)

Another reason not to use voice chat (Which I dislike, and support charging for on the PS3 for cross-game.)

---

### Post by Macchia on 2010-03-16
> **Psumi said:**
> Another reason not to use voice chat (Which I dislike, and support charging for on the PS3 for cross-game.)

I use voice chat, why not? again, if you feel confortable with PA no problem here but please let me choose what i want to use.

---

### Post by Objekt on 2010-03-16
> **Macchia said:**
> many programs like skype have latency issues (teamspeak for example)

Not sure which Teamspeak you're talking about, but both 2 and 3 have problems.

Teamspeak 2 has a microphone problem.  I have to run the Windows version through Wine in Ubuntu.  Doing it that way works fine, better than running the actual Linux client.  Which is sad.

The latest version of TS2 is a years-old "release candidate" that never made final release.  So it's no wonder the Linux client is worthless.

Teamspeak 3 is so far also a disaster, not a good sign for a beta release.  I don't know whether the same clowns that botched TS2 are involved, but they are putting no effort into making the Linux TS3 client work.  They blame TS3's 100%+ CPU use under Linux on a third-party library.  Translation: it will NEVER get fixed, just like TS2.

Either of these cases aren't really due to PulseAudio, they're due to developers who just don't give a damn whether their software works in Linux.

Such is the hazard of reliance upon proprietary software.

---

### Post by Macchia on 2010-03-16
i'm talking about teamspeak2, there's a linux version that works without problems with alsa but with huge latency problems with PA.
I tried teamspeak3 but since it's still beta doesn't count (tried successfully btw)
Never had any mic problems.

---

### Post by Objekt on 2010-03-16
The question is, can you use TS (either 2 or 3) AND have sound in a game at the same time?  I couldn't do that in Kubuntu 8.04 or 8.10.  No one seems to know whether those releases used ALSA or some early version of PulseAudio, so I don't know whether dumping PulseAudio & getting ALSA working would solve the problem, if I even knew how to do that.

---

### Post by Macchia on 2010-03-16
> **Objekt said:**
> The question is, can you use TS (either 2 or 3) AND have sound in a game at the same time?  I couldn't do that in Kubuntu 8.04 or 8.10.  No one seems to know whether those releases used ALSA or some early version of PulseAudio, so I don't know whether dumping PulseAudio & getting ALSA working would solve the problem, if I even knew how to do that.

Well, teamspeak2 uses OSS and locks the audio device so ts2 audio works but not any other does.
Teamspeak3 works even with 4 audio sources playing because it uses alsa direcly and not oss.
PA unusable with my audio setup even with ts3.

---

### Post by rahilm on 2010-03-16
what did jaunty use?? because jaunty was the last distro to play sound from my headphone

---

### Post by Psumi on 2010-03-16
> **rahilm said:**
> what did jaunty use?? because jaunty was the last distro to play sound from my headphone

It used pulseaudio.

---

### Post by Macchia on 2010-03-16
> **Psumi said:**
> It used pulseaudio.

it was an option, not a dependency if i remember correctly.

---

### Post by Macchia on 2010-03-16
So, anyone can tell me how to install gnome without pulseaudio?
I don't want to switch to other distro but if it's not possibile to leave behind this sound server i'll be force to.

---

### Post by Psumi on 2010-03-16
> **Macchia said:**
> So, anyone can tell me how to install gnome without pulseaudio?
I don't want to switch to other distro but if it's not possibile to leave behind this sound server i'll be force to.

[http://ubuntuforums.org/showpost.php?p=8754516&postcount=3](http://ubuntuforums.org/showpost.php?p=8754516&postcount=3)

add alsa-utils to your list of stuff to install for gnome.

And after you do install all that:

**sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio**

removing gstreamer0.10-pulseaudio is MANDATORY, because it causes alsa not to work correctly if you try to use totem or parole or anything gstreamer based.

After you do this, you'll notice that gnome-volume-manager applet will not work, because it's made to use pulse. One reason why I use xfce stuff instead.

---

### Post by djselbeck on 2010-03-16
You can just remove the pulseaudio package. Of course it removes some other packages too. So you loose the startup sound in gnome and the volume control. but gstreamer applications will fallback to alsa output. I think it is not so cool to remove pulseaudio because it really made a big step forward the last years. And the common problem why people are hating pulseaudio are almost everytime the applictions which are using it not right. Like mythtv for example. The newest 0.23 trunk version has pulseaudio support and audio/video sync is completly messed up. but xbmc for example does sync really well with pulseaudio running. So I think people should stop to blame pulseaudio.

---

### Post by Psumi on 2010-03-16
> **djselbeck said:**
> but gstreamer applications will fallback to alsa output.

No they won't. You have to remove **gstreamer0.10-pulseaudio** before they do that, which is NOT removed if you remove pulseaudio itself.

---

### Post by Half-Left on 2010-03-16
> **Psumi said:**
> [http://ubuntuforums.org/showpost.php?p=8754516&postcount=3](http://ubuntuforums.org/showpost.php?p=8754516&postcount=3)

add alsa-utils to your list of stuff to install for gnome.

And after you do install all that:

**sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio**

removing gstreamer0.10-pulseaudio is MANDATORY, because it causes alsa not to work correctly if you try to use totem or parole or anything gstreamer based.

After you do this, you'll notice that gnome-volume-manager applet will not work, because it's made to use pulse. One reason why I use xfce stuff instead.

Try installing gstreamer0.10-esd then. It still supports esd which is what upstream gnome uses.

---

