---
title: "MP3 lame support problems"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by mspohr on 2005-06-08
Newbie here.  I wanted to put all my MP3s on a laptop and hook it to my stereo as a ripper/player.  I installed Ubuntu 5.04 on an old IBM laptop iSeries.  Install went just fine and works with the hardware.  Good... so far.

Copied my MP3s to the machine.  No MP3 support in default installation.  I was able to successfully install gstreamer0.8-mad and it now plays my MP3s just fine.

Next step was to set up Sound Juicer to rip CDs.  Of course, no MP3 support here either so tried to install gstreamer0.8-lame but now I have problems with liblame0.  At first it couldn't find liblame0 then when I added more repositories (extras), it told me the version of liblame0 3.96.1-0sarge1 was the wrong one.

Rant warning: [As a newbie, I find this very frustrating.  MP3 is not some rare oddball format and to have a default system install that doesn't recognize it is just plain dumb.  (I do understand the license issues but OpenOffice reads and writes Microsoft proprietary formats and is installed by default so I don't know why it can't be easy to install MP3 support.)]

Anyway, does anyone have any idea where I can get a copy of gstreamer0.8-lame and liblame0 that match so I can get on with my life?

/Mark

---

### Post by mingus on 2005-06-08
Use Synaptic to check the version alternatives.  Looks like you installed liblame from debian sarge and not hoary.  Try uninstalling, then installing the hoary version.

You must have the debian repositories turned on in your sources.list.  There is advice in recent forums cautioning against this for compatibility reasons.  That may be what you have just encountered.

Re MP3 & licensing:  You have a lot of company.  This is real pain esp for newbies.  However, the office file format example is erroneous.  This is about patents.  It has become a big problem for all Linux distros because of how onerous, indiscriminate, and inconsistent patent law has become.  Huge bruhaha going on in Europe over this.  One even has to do multimedia adds in SuSE now.  Ubuntu's policy is to not include *any* patent encumbered software, but to instead point out "howto".  A pain, but usually just one-time.

---

### Post by az on 2005-06-08
"You must have the debian repositories turned on in your sources.list. There is advice in recent forums cautioning against this for compatibility reasons. That may be what you have just encountered"

By this, you mean that this is what you think is happening and not this is what _should_ be happening.  To be clear, Using debian repositories is a big source of problems and should be avoided.

---

### Post by mspohr on 2005-06-08
The debian repository is a problem.  I had added that in a desperate attempt to find any copy of liblame0.  If I remove the debian repository, I don't have any copy of liblame0 to install.  When I try to install gstreamer0.8-lame, it tells me I don't have liblame0 (>=3.96.1-1) so it won't install.

I then went through the instructions on the "RestrictedFormats" page and discovered that I hadn't enabled the Universe Multiverse sections  (I didn't even know there were sections...) of the Ubuntu 5.04. (I had other community universe sources so I thought I was covered.)

Anyway, once I added these sections, it found liblame0 of the proper version and I was able to install liblame0 and gstreamer0.8-lame.

Final hurdle was to add gnome-audio-profiles-properties for MP3.  I was confused here since I was looking for a menu item and it wasn't to be found so in desperation I tried the "run application" and it worked.
Anyway... success for now!

I still think this is way too complicated for any normal person.
I have had to spend way too much time and learn way too much about the internals just to be able to read and write mp3 files.  This should be a no-brainer.

Thanks very much for your help.

/Mark

---

### Post by az on 2005-06-08
[http://packages.ubuntu.com/hoary/libs/liblame0](http://packages.ubuntu.com/hoary/libs/liblame0)

Liblame0 is is multiverse.  No need to outside repositories...

---

### Post by mingus on 2005-06-08
azz -

The advice is clear, but in a recent post I saw it debated again, so thought it best to be diplomatic.  Too much so, it appears.

Appreciated the clarity of your post.  I'll do the same in the future.

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=mspohr]As a newbie, I find this very frustrating.  MP3 is not some rare oddball format and to have a default system install that doesn't recognize it is just plain dumb.  (I do understand the license issues but OpenOffice reads and writes Microsoft proprietary formats and is installed by default so I don't know why it can't be easy to install MP3 support.)
[/QUOTE]

I understand your frustration, but believe me, including MP3 support out of the box without paying the patent holder  would be illegal in many countries. And there is no way one can do it while keeping the system freely (in both senses of the word) available. It had been discussed hundreds of times, professional lawyers at RedHat and SuSE had looked into this, etc. 

As for solving your problem, did you try following the instructions in ubuntuguide.org? Worked without any problems for me...

---

### Post by az on 2005-06-08
[QUOTE=mingus]azz -

The advice is clear, but in a recent post I saw it debated again, so thought it best to be diplomatic.  Too much so, it appears.

Appreciated the clarity of your post.  I'll do the same in the future.[/QUOTE]


Sometimes, when I re-read one of my posts, I cannot figure out what I meant to say!  I type like I talk.  When you read my posts, you cannot see me waving my hands...

---

### Post by mingus on 2005-06-08
[QUOTE=azz]When you read my posts, you cannot see me waving my hands...[/QUOTE]

True, but the pic helps get that image across!

---

### Post by az on 2005-06-08
[QUOTE=mingus]True, but the pic helps get that image across![/QUOTE]

All-Bran

---

