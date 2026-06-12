---
title: "OSSv4"
date: 2009-06-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nystire on 2009-06-20
I'm probably sticking my own neck into the guillotine here, but apart form the fact that ALSA comes with the kernel and OSSv4 does not, why does Ubuntu not upgrade to it?

From most of what I have seen it's simpler to use, the documentation makes more sense and in general it does (nearly) everything that ALSA does with quite a bit less of the overhead.

---

### Post by psyke83 on 2009-06-20
> **nystire said:**
> I'm probably sticking my own neck into the guillotine here, but apart form the fact that ALSA comes with the kernel and OSSv4 does not, why does Ubuntu not upgrade to it?

From most of what I have seen it's simpler to use, the documentation makes more sense and in general it does (nearly) everything that ALSA does with quite a bit less of the overhead.

Various reasons, I suppose...

[LIST]
[*]ALSA has been become ubiquitous on modern Linux systems;
[*]Modern applications no longer support OSS output directly (unless called through an intermediate library such as libsdl or libao);
[*]OSSv4's ALSA emulations is very poor (which makes the previous point even worse);
[*]PulseAudio is becoming common as the sound mixing daemon to replace ALSA's software mixing on Linux system, but it's untested with OSSv4.
[/LIST]

I'm sure there are lots more reasons I can't think of at the moment.

Basically, ALSA gained a lot of momentum since its creation (and in the time that OSS was governed by a restrictive license). Even if OSSv4 is considerably superior to ALSA, it's likely to take quite some time and effort for this momentum to swing back to OSS. I'm pretty sceptical of this, but I do hope that competition between the projects will yield improvements for everybody.

---

### Post by koshcu on 2009-06-20
I just checked and OSSv4 does not support my sound card while alsa supports my card very well.

ALSA supports more sound cards and so it makes a much better default choice.

---

### Post by moles on 2009-06-20
koshcu, what sound card do you have?

---

### Post by Zorael on 2009-06-20
[SIZE="1"]Beware: Here be quotes.[/SIZE]

> **psyke83 said:**
> OSSv4's ALSA emulations is very poor (which makes the previous point even worse);
I haven't tried it myself, but [http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html](http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html) suggests that getting good ALSA-via-OSS should be possible?


As for PA over OSS, see [http://www.pulseaudio.org/ticket/247](http://www.pulseaudio.org/ticket/247). Unless something's changed semi-recently, due to API changes from the 10 year old OSSv3 to the OSSv4 of today, PulseAudio calls functions that no longer exist. Both sides blame the other, with no resolution in sight.
> **lennart (PA developer)][list][*]**status**  changed from new to **closed**
[*]**resolution** set to **[COLOR="Red"]wontfix[/COLOR]**[/list]
Hmm, apparently OSS4 is signaling some POLLxx constant on poll() which OSS didn't do.

Please contact OSS4 upstream and request they fix compatibility with OSS3.

**Oh, and the best thing is to switch to ALSA.**[/quote]
[quote=atrus]I'd love to see some sort of progress here. Pulseaudio devs seem to consider this a bug in OSS (because pulseaudio worked with earlier OSS versions), and the OSS devs think it's a pulseaudio problem because of which dsp it's accessing.

OSS drivers seem to work pretty well, and I'd love to be able to use them properly in the context of pulseaudio.

Here's the OSS dev forum post:

[http://4front-tech.com/forum/viewtopic.php?p=8584](http://4front-tech.com/forum/viewtopic.php?p=8584)[/quote]
[quote=Saoshyant]OSS4 is not completely backwards-compatible with OSS3. There's good reasons why this is so. I'm afraid this will be something that pulseaudio will have to deal with, forcing a distinction between OSS3/Free and OSS4 to be necessary. [/quote]
[quote=lennart (PA developer)]Yes, as I said, ALSA's compat with OSS is better than OSS4's.

The OSS4 docs don't contain any information about the meaning of the additional POLLxx codes. The current code assumes that they signal some kind of error (usb audio device unplug and suchlike), which is the reason we react on those codes as we do.

If you want me to help you, try to figure out what those codes mean. I am not really interested in investing my own time in figuring in which way exactly OSS4 differs from OSS.

Or take it the other way: PA supports most things that are OSS3-compatible just fine. If you want it to support OSS4 too, then *you* have to supply the necessary information.[/quote]


I'd LIKE to use OSS. I'd like for it to be the Linux standard and included in the kernel, or at the very least a valid option (apt-get install oss4). There's duplication of effort going on here, and I hate to see it. On one side we have a portable sound system that runs on Linux/Solaris/*BSD/etc, and on the other hand we have a Linux-only system. ALSA was created when OSS3 went proprietary, much like GTK and Qt (ohsnap), and supposedly it's spaghetti, with a "Use the source, Luke" approach to documentation and redundant API calls. Perhaps this has changed (for the better/worse) since.

The blog entry is ages old, but read [http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html) (and the more recent followup [http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)).


Quoting a comment from that followup. The Hannu he's referring to is the developer of OSS.
[quote=Theodore Ts'o]The fundamental problem with OSSv4 is Hannu, unfortunately. OSSv4 is developed by only two developers. ALSA, for all of its flaws, has a much larger developer community. Hannu was too focused on how he was going to make money, and so he closed-source OSSv3 in an attempt to make money. If he had instead gathered a much larger developer community, and continued developing OSS as a hobby, with something else as a day job, when Linux became big, he probably could have gotten a job at one of the major Linux distributions, and possibly have hit it big with the dot-Com IPO lottery.

Consider some of your "Ancient Coding Ideas Finally in English", such as:

[indent]It's best to write code for the customer's demands, they will overlook its negative qualities.

Code that's not written for those buying it will be for naught, and improving it will lead to code repetition.

Those writing for a community should write the code for its own sake, those that came before you will help you.

You will end up getting credit for the work that gets added on as if you yourself did it.[/indent]

or...

[indent]Desire what the community wants, and the community will want what you desire.

Do what they want instead of what you want, and other programmers will desire what you desire.[/indent]


If Hannu had access to your wisdom, perhaps he would have been in a much better position.

What to do at this point is a hard question said:**
> 


Lastly, from a similarly ages old blog post by that Hannu fellow at [http://4front-tech.com/hannublog/?p=5](http://4front-tech.com/hannublog/?p=5). Omitted the parts about it not being GPLd and binary-only.
[quote]The latest Linux 2.6.20 kernel still has the old and obsolete 10+ years old OSS version included. It’s being killed (for a very good reason). However it looks like we are getting a very long funeral. ALSA too has OSS emulation. In fact there are two redundant versions of it: one in the kernel and another implemented in library level. Both of them emulate only the now obsolete 3.8 API version. This is the dead and deprecated OSS.

However this is not the only OSS. We at 4Front have continued working on Open Sound System for all the past years. It has become the real Common Unix and Linux Sound Solution (CULSS). In addtion to Linux it’s now the official sound subsystem for all the Unix variants (other than MacOS). However for many Linux diehards it’s not an alternative because:

[list][*]It’s not in the Linux kernel source tree so it doesn’t exist.
[*]It’s being used also by the public enemies of Linux.[/list]

For the above reasons the benefits of OSS are widely ignored:
[list][*]It’s based on the widely known Unix/POSIX/Linux device model.
[*]It’s fully documented (OTOH some parts of the documentation are still under construction).
[*]The API is simple and compact which makes it very easy to use for programmers.
[*]It has been there for 15 years so practically all applications already support it.
[*]It’s kernel only.
[*]It’s designed to work under general purpose operating systems such as Linux and Unix. There is no need to use any special real time enabled kernels (they can be used but it’s not a requirement).
[*]The limitations and “idiosyncrasies” referred by ALSA’s marketing propaganda have been fixed years ago.
[*]Fully dynamic minor/major device number allocation which permits unlimited number of audio/MIDI/mixer devices.
[*]New device naming that makes applications immune to changes in the device configuration (installing and removing devices).
[*]Transparent virtual mixing that makes it possible for any number of applications to share the same physical audio device(s). This also works for recording and full duplex.
[*]Powerful device enumeration support.[/list]

Then we have ALSA which is:
[list][*]Not documented. Use the Source, Luke!
[*]The API is not compatible/similar with anything else (past, present or future).
[*]Very thin device abstraction.
[*]The API is designed for low/zero latency which makes it very challenging to use in normal applications that don’t have any latency requirements.
[*]Requires redundant layers libraries in addition to the kernel space code (alsa-lib, Jack). This causes increased memory requirements in embedded systems.
[*]Has enormous number of functions (1500+ couple of years ago). Majority of the calls have not been used by any applications (even many applications use different functions than any others). Massive number of unnecessary library functions increases the memory footprint even further. And what about the CPU consumption? And will anybody be ever possible to document (or even test) all of them?
[*]There are multiple (redundant) transfer methods for audio. How does the programmer know which one should be used with given hardware?
[*]Some devices use interleaved channels (for stereo and multich) while some others use non-interleaved.
[*]Static minor number assignment that causes waste of the available device/card space. Number of cards, devices and subdevices possible in the system is limited.
[*]Strange configuration file mechanism that requires degree in LISP programing to understand it.
[*]Sharing of devices is based on the dmix feature that nobody but experts can configure properly.
[*]The API is based on callbacks which requires deep programming knowledge from the developers. Gotos have been considered harmful for decades. Callbacks are even worse (in fact they are a re-incarnation of the famous come-from statement).[/list]

---

### Post by koshcu on 2009-06-20
> **moles said:**
> koshcu, what sound card do you have?

I have an Asus Xonar D2X card which is an AV200 chipset. I checked and OSSv4 supports the AV100 but not the AV200.

---

### Post by hexsel on 2009-06-20
For those that were wondering why the argument for OSS4, it seemed to have popped up on slashdot yesterday, after which it promptly appeared here:

[http://linux.slashdot.org/story/09/06/19/1937210/State-of-Sound-Development-On-Linux-Not-So-Sorry-After-All?from=rss](http://linux.slashdot.org/story/09/06/19/1937210/State-of-Sound-Development-On-Linux-Not-So-Sorry-After-All?from=rss)

It does seem more or less consensual (ok, just a small margin) that OSS4 is a better solution, simpler and lighter but about as flexible.  Yet it also seems like it missed the right timing due to poor licensing choices.

It's going to be very hard to unseat the current players, due to compatibility or plain burnout-syndrome ("What?! Switch the sound system again after we JUST convinced a thin majority that we want Pulse?!")

There's apparently a pretty high cost on switching apps and libs back and forth due to the large api differences.

---

### Post by nystire on 2009-06-20
I must admit to being an avid Slashdot lurker, and I occasional take a stab at writing small cross-platform (Linux, FreeBSD, Solaris 10[The pain...]) applications for a smallish (25 machine) network, which is why I asked the question. The lack of a standard sound API across all of those can be a bit of a pain sometimes, although between FreeBSD and Solaris, at least I have OSS to a certain extent. Changing things to work with ALSA after getting them to work with OSS sometimes makes me contemplate going out and getting committed to the local asylum.

---

### Post by RAOF on 2009-06-21
As I understand it, you should be able to use ALSA, the audio library, everywhere that OSS goes, as alsa-lib has an OSS backend.

Another option would be to use a higher-level sound API; this may or may not be worth it, depending on what you want to do.

---

### Post by nystire on 2009-06-21
Fairly low-latency is not really a possiblity when you start using higher level APIs. Also, even fairly simple things such as setting the sampling and bit rates are much more complex in ALSA, in addition to the fact that the support in most of the other libraries are for the older versions of OSS. And lets not even go into the finger-pointing sessions of who is supposed to fix what, please.

---

### Post by RAOF on 2009-06-21
If low-latency is one of your requirements, why not try [JACK](http://jackaudio.org/).  It seems to be gaining momentum as the de-facto professional audio system, and seems portable across Linux/*BSD/OS X/Windows.

---

### Post by hexsel on 2009-06-21
From what I understood, nystire wants to write apps that work on systems that might not have pulse or alsa, but that do have OSS (e.g. BSD).


> **RAOF said:**
> As I understand it, you should be able to use ALSA, the audio library, everywhere that OSS goes, as alsa-lib has an OSS backend.

Another option would be to use a higher-level sound API; this may or may not be worth it, depending on what you want to do.

---

### Post by RAOF on 2009-06-21
> **hexsel said:**
> From what I understood, nystire wants to write apps that work on systems that might not have pulse or alsa, but that do have OSS (e.g. BSD).

And the alsa libraries are portable (and ported) to *BSD, and have an OSS backend.  The ALSA kernel subsystem & drivers aren't.

---

### Post by zekopeko on 2009-06-21
> **hexsel said:**
> From what I understood, nystire wants to write apps that work on systems that might not have pulse or alsa, but that do have OSS (e.g. BSD).

from [http://pulseaudio.org/](http://pulseaudio.org/)

> PulseAudio has been tested on Linux, Solaris, FreeBSD, NetBSD, Windows 2000 and Windows XP. It should also run on all other POSIX and Windows systems, but may require new backends to handle their sound systems.

it seams to me the only thing you need is a backend on different systems.

---

### Post by autocrosser on 2009-06-21
I see that the dev-list is also talking about this & the best answer I have seen is from Daniel Chen & Luke Yelavich:

> Message: 1
Date: Mon, 22 Jun 2009 09:17:17 +1000
From: Luke Yelavich [EMAIL="themuso@ubuntu.com"]<themuso@(deleted)>[/EMAIL]
Subject: Re: Replace PulseAudio with OSS v4?
To: [EMAIL="ubuntu-devel-discuss@lists.ubuntu.com"]ubuntu-devel-discuss@lists.ubuntu.com[/EMAIL]
Message-ID: [EMAIL="20090621231717.GA5782@strigy.yelavich.home"]<20090621231717.GA5782@strigy.(deleted).home>[/EMAIL]
Content-Type: text/plain; charset=us-ascii

On Sun, Jun 21, 2009 at 07:52:45AM EST, Daniel Chen wrote:[INDENT]> Lower sound quality is a red herring. ALSA's default resampler has
> known and quite audible limitations. The available resamplers in
> PulseAudio demolish the "lower sound quality" FUD. Jaunty shipped a
> configuration using a craptastic one in an attempt to balance CPU
> usage with perceptive quality. Lessons learned: Karmic will ship with
> a much better (but more CPU-intensive) resampler.
[/INDENT]I'd like to add that on a technical level, OSS v4 does audio mixing in the kernel, and uses floating point maths, which is strictly forbidden in the official mainline kernel. Trying to get such code even into the Ubuntu kernel will be similar to getting blood out of a stone.

Luke
And that, I would say---is that.

---

### Post by Zorael on 2009-06-22
> **autocrosser said:**
> And that, I would say---is that.
I guess that rules out getting it into the kernel. Could it be supplied with debs then, perhaps?

There's a discussion thread open now on the OSS forums ([http://www.opensound.com/forum/viewtopic.php?t=3199](http://www.opensound.com/forum/viewtopic.php?t=3199)) on how we might reconcile the two camps.

---

### Post by LKjell on 2009-06-22
If I understand correctly we cannot merge OSSv4 is because of some kernel policy. But cannot we make a compatible layer and merge the OSSv4's API with ALSA and then start to improve ALSA?

---

### Post by zika on 2009-07-01
I am curious about OSS4 but do not want to loose audio that is pretty good on my machine (external DAC and such things ...)...
Is there anybody that (seriously) use OSS4 with Karmic, ext4, amd_64, 2.6.31, external DAC ... ?
Any hints, complaints, reasons why to go to OSS4 from PulseAudio and ALSA ...?
Any answer will be greatly appreciated...

---

### Post by ibuclaw on 2009-07-01
OSS have been long deprecated from the Linux kernel.

OSSv4 has been a small rebirth of this sound system, but afaik, it's nonfree.

I still wouldn't use them, as you have already stated, everything "Just Works" with ALSA at the moment, and so setting up OSSv4 is probably going to cause more negatives than positives. Also bare in mind that there will be few people who use OSSv4 for whatever reason (probably Soundblaster X-fi cards, but I think all is sorted in ALSA by now). So anything that you have difficulties with won't be greatly supported in this forum.

Regards
Iain

---

### Post by Hairy_Palms on 2009-07-01
ossv4 looks like a well designed sound system, and at the moment its free software, however i still wouldnt use it, as theres nothing to stop the lead developer pulling the same trick he did with the old OSS, close sourcing the development and, and with only two developers it wouldnt really be viable to fork if that did happen.

---

### Post by psyke83 on 2009-07-01
Let me remind you that this topic was [recently discussed]("http://ubuntuforums.org/showthread.php?t=1192364") on the forums, and I think also on the ubuntu-dev-discuss ML (probably linked in the older thread).

---

### Post by zika on 2009-07-01
> **psyke83 said:**
> Let me remind you that this topic was [recently discussed]("http://ubuntuforums.org/showthread.php?t=1192364") on the forums, and I think also on the ubuntu-dev-discuss ML (probably linked in the older thread).I am very sorry, my clumsy search did not give me that information. If possible, this thread could be merged with the already existing one ...

---

### Post by 23meg on 2009-07-01
[QUOTE=zika]If possible, this thread could be merged with the already existing one ...[/QUOTE]

Done.

---

### Post by zika on 2009-07-01
> **23meg said:**
> Done.Thank You and my apologies again...

---

### Post by martinbaselier on 2009-07-17
I stumbled upon this discussion yesterday, after I installed OSS to test it. Strangely enough it seems there's a lot of discussion without actual testing of the product. 

I must say the difference in sound quality is amazing. The last time I had such an experience was in the era of dos and the pc speaker, when I discovered modplay, which could play sampled music instead of the bleeping music that was used in most games. I didn't think this would be possible in this time. 

About the license: it's openGPL now. So if they would decide to make it closed source again in the future, which seams unlikely so short after becoming open source again, Anyway if they would, the source would stay available and it could be maintained further by a different crew. 

Seeing the documentation I think if it's far more user friendly than alsa. Of course if it works out of the box it doesn't really matter for most users. But if you ever try changing settings on alsa, you'll discover the hell they created to accomplish that.

Some cards are not supported by alsa, some not by oss, most will be supported by both. The important question would be: Is the amount of cards supported by alsa, significantly higher than that by oss? If that's not the case, switching to oss would be a good choice.

Some thought about jack and pulse, which were mentioned too in this thread. Jack is an extra layer over alsa or oss, it can manage lower latencies, but it still needs alsa or oss to create the communication on the hardware level. 

Pulse is also an extra layer, but with higher latency and I never understood why it should be installed standardly. I've never had any problems with it, but I removed it all the same, since I don't see any necessity for it. Most users just want sound output to work and if it does they're happy. The few users that want to use pulse can always install it themselves. 

Wether or not oss4 will be used as a default in the future, it should at least be available in the repositories, so people can easily install it. Maybe it already is, but I could not find it. The deb they provide themselves is easy enough though.

---

