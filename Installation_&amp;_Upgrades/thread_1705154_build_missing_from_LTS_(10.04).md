---
title: "build missing from LTS (10.04)"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by oliverthered on 2011-03-11
Hi,
Well I'm running Mint 9, based on 10.04 LTS and there are a few things that don't seem to have had very long term support (such as KDE, amarok, minitube etc...)

A lot of these things have some pretty critical bug fixes in, even to the extent of them no longer working.
Some are in places like getdeb... but what I'd really like to do is set up a nice PPA and have a bit robust, with beta (or RC) and more solidly tested releases on a more 'rolling relase' type LTS where the various back-ports or none minor dot releases of softwhere, that none the less have some pretty critical fixes or features in can be pulled from.

This is all the more important since I go round setting up Ubuntu or variants of on other peoples systems and both want ot have a nicly patched up live CD/DVD with as many 'issues' corrected and updates in as possible (people using mobile broadband etc... don't like wasting hundred of megs on downloading when I do an install)..


So the main question is:
Given things like Amarok and KDE are already packaged up for ubuntu (or Kubuntu) and often broken up into sub packages or with various dependancies (and assumably build / config parameters etc..)
Is there somewhat I can goto to find out how (in many senses of the word) the things where packaged in the first place.


And additionally:
Are there any good reasouses about on setting up PPA/s esp if I want to support multiple platforms (e.g. amd64 and 32x86)

And similar to the first, but in relation to places like packages on GetDeb (since I'd like to bundle a load of stuff that's known to work nicely together and with appropriate update pririties, instead of pulling things from un-integrated third party sites [though version lock down should help with that, third party build parameters or patches or otherwise may be an issue]).


Building on the last...
I know I can pull the source down for things... but what about find out what and how in-house or third party patches &co... are applied to the ubuntu source (OpenSSL and things have had issues with buggy patches before.. but also if I'm backporting a kernel I want to make sure it's all patched up and configured and working so people don't have issues)



umm... maybe some more questions... so feel free to eloborate on the ones I've posted or other issues doing similar you've had and want questions like it answered to.. since I'd probably like the answeres to those questions too!

---

### Post by oliverthered on 2011-03-11
I should add, this is work in progress to having a rock solid base lined very long term support variant of Gnu/Linux &co...

At some point I intend to clean up the whole apt/deb system (With some really tight and rich additions) and go for a more modular approach to package archives... that is remove a load of stuff that Joe public or Joe company isn't going to need in general and then have other PPAs etc...  that provide some of the stuff that's been cut out.. or additional stuff that was never in there.... or indeed more of a roling version (abouve or in addition to GetDeb).


I'm also in the process of working on a nice tight system for automatically generating updates and patches (or including workarounds and things people do and helping track down bugs etc...)..

mostly via hooking up a load of stuff to dbus and the like and integrating debugging, event capture and profiling etc... in a nice wrapped up way when things go a bit wonky... maybe even doing auto-delta's on source repositories to find out where the fault was introduced, using some automated playback from the event capture and similar with profiling and function logs etc... to find where the fault is...


dbus stuff basically looks to see what happens and what commands are run when a devies is plugged in... if there's anything manual.. what changes are made... if there's anything new... new modules that wheren't in the base system.. upgraded stuff etc..

then does some forward and back tracking on commands and what have you to part automate the process of capturing what the user (or devloper) does to work around, implement, fix or improve support for the device (or whatever)..

anyhow more on that another time.. but just some ideas about what I'm doing to make it really easy for comminuty working together and easy submission of patches or fixes or workarounds or just info for other people so that they know what the score is... and also to make it really easy for me or other developers to knock that stuff up

---

