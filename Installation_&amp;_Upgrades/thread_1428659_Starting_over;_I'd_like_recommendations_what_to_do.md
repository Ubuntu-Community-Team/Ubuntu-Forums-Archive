---
title: "Starting over; I'd like recommendations what to do after new install"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by wizarddrummer on 2010-03-13
Starting over.

Thought I could just place a hard drive with a preloaded Ubuntu install from another machine (a loaner machine) into this one; change a few drivers and be on my way.

Too many errors to count. ALSA; Jack; LiveTex all cratered and I'm tired of fighting this. I've spent more than two days trying to get stuff working and if there's anything I've learned from years of experience there's a time to cut bait and run.

A clean install on the actual hardware I'm using has to be better than the hodge podge I have now.

**What I would like from the community is recommendations for what to do AFTER the install.**

1) where can I find the most **up-to-date** comprehensive and exhaustive list of repositories for the Synaptic Package Manager?

2) I like to do sound and video processing. I would like to have the program applications 
Qsynth, Virtual Midi Keyboard, Muse Score, Csound, GNU Denemo, and many others that either fail to start or produce no sound to work. What, besides the programs need to be loaded in order to make these work?

3) A helpful list of recommendations on what to install along with order preference. In other words 'this needs to be done before this...'  on a new Ubuntu install.

That's it.

I really appreciate it.

In case anyone's interested: Here's a small list of some of the errors I currently have.
[SIZE=1]AlsaModularSynth - Could not open file.

Qsynth1 - Failed to create the audio driver (jack) / Jack server not running.

Errors were encountered while processing:
 texlive-latex-base-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

Qtractor - The audio/MIDI engine could not be started.

Make sure the JACK audio server (jackd) and/or
the ALSA Sequencer kernel module (snd-seq-midi)
are up and running and then restart the session.

apt-get install alsa-utils - Errors were encountered while processing:
 texlive-latex-base-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/SIZE]
Jack configuration files not found; the list is endless. Plus many errors trying to get texlive to work.

---

### Post by UCSBGauchosRock on 2010-03-18
1) Launchpad is an excellent place to start if you are looking for repositories to add to launchpad. For example you can find the repository for gnomenu and dockbarx there as well as many other ones. If you are looking for any specific repositories simply google them if you know the name of the software you would like to install.

2)From the sound of things you need to enable jackd for your user. Generally it should have asked you whether or not to enable it upon program installation. Otherwise It was a terminal command but I cannot recall it.

3)Here are my reccomendations: 
              1. Firestarter(firewall)
              2.Abiword(light alternative to OpenOffice)
              3.Mozilla Plugins(Which ones you want are up to you)
              4.Adobe Flash Player(Or gnash if you are low on system resources)
              5.Compiz Config Settings Manager
              6.Ubuntu Tweak([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) to learn more and download)
              7.Eee Applet(overclocking. Please note overclocking can be dangerous)
              8.Emesene(MSN instant messaging)

---

