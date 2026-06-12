---
title: "Buy playback codecs"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by taavikko on 2008-10-01
Can anyone open videos from this site 
[http://web.mit.edu/nnf/research/phenomena/viscoelastic_jet.html](http://web.mit.edu/nnf/research/phenomena/viscoelastic_jet.html)
If not, it asks to search and install missing plugins, without finding them,
Then the funny part, theres an button to buy these missing plugins from canonical store...

Do you approve this kind of a behaviour?
To me it sounds like RH/Fedora...

Does this means we must buy codecs from fluendo/canonical to be able to watch media content from internet?
Or are we still able to install ubuntu-restricted-extras in the future, without any regressions?

Videos didn't work for me, errors in size and such.
the purpose for this rant is just to ask your opinions.

It was also hard to determine right category for this one, but ended up in here, since it's come up in dev of II.

---

### Post by macroshaft on 2008-10-01
I believe that there are certain codecs that cannot be bundled for free for complicated reasons I cannot recall. I seem to remember reading somewhere that this was canonical's way of providing these codecs to us without breaking the law. As such all the code we have been previously accessing for free will be unnafected.

I suppose we should all take a minute to think about how privilaged we are to have this world class operating system for free, with all these brilliant apps for free and that the business model it's built on is only so compatable with the rest of the world, if someone invents something that impacts on our internet experience and then hogs the rights to it there's nothing any linux bod can do.

I don't think I have any problem with our feature set being extended in this way. The problem would be if this began to outweigh the free and became the norm.

---

### Post by taavikko on 2008-10-01
My mistake, forgot to mention that one in the first post.
This idea is to provide legal way of playing media content.
Since different countries have different laws.

I'm not complaining about ubuntu as an OS, but canonical as a company.
What happened to medibuntu? Why cant use that one to provide codecs?
Still illegal. If you pay money for those codecs, its legal.

---

### Post by macroshaft on 2008-10-01
I understand but I think this is a sticky subject to be honest, let's face it audio/video content has been for some time and I can only see it getting worse as CD sales decline.

Perhaps it's fine for codecs but charging for software like this would defeat the object of ubuntu?

---

### Post by ronacc on 2008-10-01
it is not Ubuntu's fault that the person who made the video made the choice to use a propriatary codec , complain to them not Ubuntu ,It is not like there are no suitable "open " codecs for the job .

---

### Post by philinux on 2008-10-01
Even with vlc it spits out this.

[COLOR=#ff0000]No suitable decoder module:[/COLOR]
 [COLOR=#ff0000][COLOR=#000000]VLC does not support the audio or video format "**IV50**". Unfortunately there is no way for you to fix this.


[/COLOR][/COLOR]IV50 stands for Indeo Video version 5.0. Indeo was a subdivision of Intel and was bought by Ligos a few years back and vanished into thin air

---

### Post by macroshaft on 2008-10-01
Hit the nail on the head!

Mind you a large part of the problem is that none of us have any backbone, they do these stupid things and everyone just goes along with it. Whatever the vid they want to watch is it's obviously too tempting to resist and stand for what they believe in!

Having said that it's good to see everyone made a stand for that firefox user agreement fiasco, I don't think the users here are going to be pushed around that easily, hehe.

---

### Post by plun on 2008-10-01
Tested and for sure this is a mess....

We cannot do anything about different laws in different country's.
Mr Ballmer also talks about "thieves".

The Medibuntu repo must be enabled and w32codecs installed

This is a Indeo 5 video


Mplayer plays this file....


```
plun@Plun:~$ mplayer /home/plun/Desktop/T41_thin_coiling.aviMPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/plun/Desktop/T41_thin_coiling.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [IV50]  160x360  24bpp  58.227 fps  3036.0 kbps (370.6 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 355.
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Creating new registry
Decoder supports the following YUV formats: YUY2 IYUV UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2f)
VDec: vo config request - 160 x 360 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 160x360 => 160x360 Planar YV12 
Selected video codec: [indeo5ds] vfm: dshow (Intel Indeo 5)
==========================================================================
Audio: no sound
Starting playback...
V:   7.4 432/432  5%  1%  0.0% 0 0 
GNOME screensaver enabled

```



**Nullack got a master thread for Video.**
[http://ubuntuforums.org/showthread.php?t=882453](http://ubuntuforums.org/showthread.php?t=882453)


Also this thread...
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


For the moment I am using the vlc plugin for Mozilla, totem-mozilla is
"out of order" for mostly all commercial streamed videos.

---

### Post by taavikko on 2008-10-01
> **ronacc said:**
> it is not Ubuntu's fault that the person who made the video made the choice to use a propriatary codec , complain to them not Ubuntu ,It is not like there are no suitable "open " codecs for the job .

The issue is not really about those videos working or not..
But the fact that ubuntu is pushing people to buy codecs through canonical.store.

As long as the packages from the repos work, im happy.
How many of you are willing to buy these codecs?
How many newcomers will buy those, just because they may not be aware of installing them through the repos.

How much you pay for codecs in windows? ffdshow + ac3filters they work.

Deal between canonical and fluendo is not an bad thing, dont get me wrong!
He who asks is not the fool, but the one who pays...

---

### Post by philinux on 2008-10-01
Yep Mplayer plays it just fine.

---

### Post by plun on 2008-10-01
> **taavikko said:**
> T
Deal between canonical and fluendo is not an bad thing, dont get me wrong!
He who asks is not the fool, but the one who pays...

Well... I also checked this with Totem and it seems that the GUI for
missing codecs maybe must be changed.

It must be a "hint" about Medibuntu. IMHO....

I am not going to file this bug but its probably needed....:cool:

OP files one...:D

---

### Post by ronacc on 2008-10-01
> **taavikko said:**
> The issue is not really about those videos working or not..
But the fact that ubuntu is pushing people to buy codecs through canonical.store.


He who asks is not the fool, but the one who pays...

Are they "pushing people" to buy non-free codecs or just informing them that they are available ?  Would it be better not to make the offer and have people say Ubuntu is broken it won't play ".xyz" files ?

---

### Post by plun on 2008-10-01
For the record so everyone easily can see it.

GUI

[IMG]http://ubuntu-pics.de/bild/3903/buy_20JF1D.jpg[/IMG]


Button to Canonical

[https://shop.canonical.com/index.php?cPath=25](https://shop.canonical.com/index.php?cPath=25)


I cannot see a single word about Medibuntu.

---

### Post by taavikko on 2008-10-01
> **plun said:**
> Well... I also checked this with Totem and it seems that the GUI for
missing codecs maybe must be changed.

It must be a "hint" about Medibuntu. IMHO....

I am not going to file this bug but its probably needed....:cool:

OP files one...:D


Right on the money :) That's what I was after. 


[QUOTE=ronacc]Are they "pushing people" to buy non-free codecs or just informing them that they are available ? Would it be better not to make the offer and have people say Ubuntu is broken it won't play ".xyz" files ?[/QUOTE]

After byuing those codecs from canonical.store, they say, ubuntu is expensive system, i thought it was free...

Ubuntu is free, as distribution. Software you want to use, and may be forced to use, has a price tag on it.

IMO it would be better to market those software somewhere else, than popup
from missing plugins, that allows you to buy it.
(that's after install missing plugins fails to find any)

---

### Post by macroshaft on 2008-10-01
Let me get this straight, there is a way to make this work by enabling the correct repos but there is no mention of this on the codec search app, just a link to the pay-per-screw ones?

I'd have no issue with 'there is a basic one for free but pay for bells and whistles if you like' but to sweep the freebie under the carpet and gently usher people to the checkout is wrong.

---

### Post by philinux on 2008-10-01
> **macroshaft said:**
> Let me get this straight, there is a way to make this work by enabling the correct repos but there is no mention of this on the codec search app, just a link to the pay-per-screw ones?

I'd have no issue with 'there is a basic one for free but pay for bells and whistles if you like' but to sweep the freebie under the carpet and gently usher people to the checkout is wrong.

Well this is certainly new in intrepid then. I just switched to my Hardy install which uses totem plugin by default. It seems to work 99.9% of the time. This is what I get, and certainly no offer to buy a codec.

---

### Post by taavikko on 2008-10-01
Totem-plugin-viewer launches ->
gnome-codec-install which is part of gnome-app-install

[https://launchpad.net/ubuntu/+source/gnome-app-install](https://launchpad.net/ubuntu/+source/gnome-app-install)
quickly browsed through and didn't find any clues what triggers the
canonical.store...

First time I saw this was today...

---

### Post by plun on 2008-10-01
> **taavikko said:**
> Totem-plugin-viewer launches ->
gnome-codec-install which is part of gnome-app-install

[https://launchpad.net/ubuntu/+source/gnome-app-install](https://launchpad.net/ubuntu/+source/gnome-app-install)
quickly browsed through and didn't find any clues what triggers the
canonical.store...

First time I saw this was today...

Yup, it seems to be the correct package to file a bug about.

> gnome-app-install (0.5.8-0ubuntu1) intrepid; urgency=low

  * AppInstall/activation.py, AppInstall/distros/Default.py:
    - support a generic way to add a link button during codec
      install into the UI for additional actions
  [B]* AppInstall/distros/Ubuntu.py:
    - link to the codec page in the canonical shop[/B]



Also this wiki about this... rather funny "draft notes"...


[https://wiki.ubuntu.com/CodecInstallationIntrepid](https://wiki.ubuntu.com/CodecInstallationIntrepid)


.

---

### Post by taavikko on 2008-10-01
Bug filed:
[https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/276786](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/276786)

If anyone agree, comment and mark confirmation.

---

### Post by plun on 2008-10-01
> **taavikko said:**
> Bug filed:
[https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/276786](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/276786)

If anyone agree, comment and mark confirmation.


A confirm and a comment... thanks for filing this bug !

---

### Post by robzon on 2008-10-01
I think they're doing a good thing. There are countries where you have to pay to be able to legally play some video content and Canonical makes it easy for that users. It simply allows them to legally use the OS with just a few clicks. I don't see how it's a bad thing. They don't support the idea, they just accept that this problem exists and created an easy temporary solution. There's no sign of them preferring proprietary solutions over the free ones. They give you the possibility to use closed codecs as there's no legal alternative. I'm sure they wouldn't do it if there was.

---

### Post by plun on 2008-10-01
> **robzon said:**
> I think they're doing a good thing. There are countries where you have to pay to be able to legally play some video content and Canonical makes it easy for that users. It simply allows them to legally use the OS with just a few clicks. I don't see how it's a bad thing. They don't support the idea, they just accept that this problem exists and created an easy temporary solution. There's no sign of them preferring proprietary solutions over the free ones. They give you the possibility to use closed codecs as there's no legal alternative. I'm sure they wouldn't do it if there was.

Well, go back and look at the GUI again.

There must be options for a user, not just rush and buy a codec.

The bad guys uses this tactic for fake apps...


Also probably a URL to Ubuntus wiki about restricted formats.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

.

---

### Post by smartboyathome on 2008-10-01
Well, if we do include even a "hint" of Medibuntu, that can give companies grounds to make Ubuntu illegal in the US and quite possibly even the UK. Even though some countries don't have the restrictive laws in place, its better to go along with the most restrictive than the least restrictive and step on everyone's toes.

---

### Post by plun on 2008-10-01
No I dont think so but I am also not a lawyer...:)

Please read the wiki
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Points to Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

With this disclaimer
> 
Disclaimer

Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country.

See Ubuntu's Free Software Philosophy and the FreeFormats page for a more comprehensive discussion of these issues. 


UK is a member of EU as also my country, also OPs country Finland. 

As I showed, there was no problem to watch this file without buying a codec, Mplayer just played it.

So this must be clarified and I know that Fedora have had exactly the same discussion about this.

---

### Post by RAOF on 2008-10-01
> **plun said:**
> ...
UK is a member of EU as also my country, also OPs country Finland. 

As I showed, there was no problem to watch this file without buying a codec, Mplayer just played it.

So this must be clarified and I know that Fedora have had exactly the same discussion about this.

Right.  Mplayer, with the almost-always-copyright-infringing (without even going into patents) w32codecs package, played it.

As far as I can see, the only real problem with the new codec install dialog is that it doesn't give any indication whether the pay-for codecs will actually play the file that triggered codec-install.  In this case, they won't, so the button shouldn't be shown.

Oh, and the patent fun is also a problem for Windows, IIRC.  Certainly  ffdshow doesn't have licenses from the MPEG group, and the various others who own patents on different compression/streaming/etc technologies.

---

### Post by bruce89 on 2008-10-01
In this case, the videos are encoded using Indeo 5 (or whatever it's called). No wonder they don't work (they wouldn't on XP by default either).

---

### Post by SonicSteve on 2008-10-01
Isn't this avi format part of ubuntu restricted extra's? That's not medibuntu. Do the restricted extras have the same illegal status as medibuntu?

These vidoes played perfectly for me BTY I haven't installed anything from medibuntu except the DVDcss2 stuff.

---

### Post by bruce89 on 2008-10-01
> **SonicSteve said:**
> Isn't this avi format part of ubuntu restricted extra's? That's not medibuntu. Do the restricted extras have the same illegal status as medibuntu?

They are essentially the same thing. u-r-e is for lazy people so they don't have to install things manually.

---

### Post by RAOF on 2008-10-01
This video won't play without a copy of the relevant Windows directshow dll - what the w32codecs package contains.  That's very clearly not redistributable, which is why it doesn't appear anywhere in the archives, not even in multiverse.

Ubuntu-restricted-extras, however, is different.  That installs software which implements algorithms for which various companies own patents, and this is much murkier than the clearcut copyright violation that is w32codecs.

The medibuntu *3rd party* repository contains software of various statuses, from the outright illegal in many places (libdvdcss falls afoul of the DCMA in the USA and similar legislation in Australia, for example) to software they clearly don't have a license to redistribute like w32codecs but that you *may* be legally able to use - depending on whether EULAs are enforcable in your juristiciton and that you own a copy of Windows.

---

### Post by ronacc on 2008-10-01
well I installed the medibuntu w32 and w64 codecs ( I'm amd64) and although synaptic says they are installed looking in /usr/lib/codecs they are not there , the avi's from post 1 of this thread will not play . I have d/l'd the w32codecs_20071007-0medibuntu3_i386.deb should I just go ahead and hand install them ?

---

### Post by plun on 2008-10-02
> **ronacc said:**
> well I installed the medibuntu w32 and w64 codecs ( I'm amd64) and although synaptic says they are installed looking in /usr/lib/codecs they are not there , the avi's from post 1 of this thread will not play . I have d/l'd the w32codecs_20071007-0medibuntu3_i386.deb should I just go ahead and hand install them ?

Looked a little and it seems to be a problem with 64bit and dll files
32bit must use some sort of "wrapper".

Reference
[http://ubuntuforums.org/showthread.php?t=569402](http://ubuntuforums.org/showthread.php?t=569402)

[http://avifile.sourceforge.net/](http://avifile.sourceforge.net/)

The codecs are for me installed within **/usr/lib/win32**

And you also have Mplayers own codecs to try.
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)


Rather delicate challenge also that this example comes from mit.edu...

.

---

### Post by ronacc on 2008-10-02
oh well we are testing and its time for the beta so I'll be brave and try the mplayer.hu codecs again , installing them back in aplha1 was how I discovered the permissions getting changed bug so I was a little reluctant to do that again . the w64 repo package only installs 3 .so files which I guess is the wrapper, the w32codecs package actualy contains the codecs plus the same files (I don't know if they are identical but they are the same name and size ) , I tried to install the w32codecs by forcing the arch but it balked because it wanted to overwrite the files installed by the w64 package, thats when I stopped and asked for advice.

---

### Post by plun on 2008-10-02
Ok... this is from Mplayers readme
> 
TEP1: Installing Binary Codecs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

MPlayer has builtin support for the most common audio and video formats. For a few formats no native decoder exists and external binary codecs are required to handle them, for example newer RealVideo variants and a variety of uncommon formats. This step is not mandatory, but recommended for getting MPlayer to play a broader range of formats. Please note that binary codecs only work on the processor architecture they were compiled for.

Unpack the codecs archives and put the contents in a directory where MPlayer will find them. The default directory is /usr/local/lib/codecs/ (it used to be/usr/local/lib/win32 in the past, this also works) but you can change that to something else by passing the '--codecsdir' option to './configure'.

ttp://www.mplayerhq.hu/DOCS/README




There must be a readme for Medibuntus w32codecs somewhere  ???

---

### Post by ronacc on 2008-10-02
I went ahead and used --force-all on the medibuntu w32codecs , mplayer seems to find them now (they installed to /usr/lib/codecs ) but gives an elfclass error . all this  to test a .avi file , what fun ;)

---

### Post by philinux on 2008-10-02
Aha, this explains it. Yesterday I got the file to play in Intrepid, with mplayer, which is a 32 bit install. While Hardy, 64 bit, would not play it.

---

### Post by plun on 2008-10-02
> **ronacc said:**
> I went ahead and used --force-all on the medibuntu w32codecs , mplayer seems to find them now (they installed to /usr/lib/codecs ) but gives an elfclass error . all this  to test a .avi file , what fun ;)

OK... then we at least knows, maybe "worthless knowledge".

Back to topic and Fedoras "CodecBuddy"
[http://fedoraproject.org/wiki/CodecBuddy](http://fedoraproject.org/wiki/CodecBuddy)


It will be a lot of discussions about this button to Canonical/Fluendo...

100% sure....

---

### Post by rockin_goliath on 2008-10-02
It certainly is unfortunate that internet users are put in a situation where they need to purchase a codec in order to view content legally. However, I applaud Cannonical for offering this service, because at least it provides some assurance to internet users who would like to operate fully under the copyright and patent laws that they can do so and still enjoy internet content.

With that said, I cannot imagine that Cannonical enjoys selling this service, because they certainly do not get the codecs for free, and it goes against the Ubuntu philosophy of "software for everyone." It must also be difficult to support a separate software repository that requires a payment to gain access to, separate from all the other repositories. I think that Mark Shuttleworth, Cannonical, and the Ubuntu community should do whatever we can to promote open source codecs on the internet, such as using .ogg videos in HTML5's new video tag rather than some obscure file that no one wants to buy.

---

### Post by plun on 2008-10-02
> **rockin_goliath said:**
> It certainly is unfortunate that internet users are put in a situation where they need to purchase a codec in order to view content legally. However, I applaud Cannonical for offering this service, because at least it provides some assurance to internet users who would like to operate fully under the copyright and patent laws that they can do so and still enjoy internet content.

With that said, I cannot imagine that Cannonical enjoys selling this service, because they certainly do not get the codecs for free, and it goes against the Ubuntu philosophy of "software for everyone." It must also be difficult to support a separate software repository that requires a payment to gain access to, separate from all the other repositories. I think that Mark Shuttleworth, Cannonical, and the Ubuntu community should do whatever we can to promote open source codecs on the internet, such as using .ogg videos in HTML5's new video tag rather than some obscure file that no one wants to buy.

Of course this is the case.

But visit every "newbie forum" and all questions !

Now its just a button to a Internet store as solution.....
[B]
95% of all users doesnt know what a codec is !![/B]

A few "nerds" knows it...


Intrepid for the moment:

- Totem-mozilla is out-of-forder, IMHO
 
- Adobes Flash works great on 32 bit, RC version, Gnash and swfdec can play low quality basic flash

- VLC plugin for Mozilla works for nearly all formats. Just great !!

-  mozilla-mplayer plugin untested, probably works much better then totem-mozilla


This howto now got 170000 views and also translated 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


The world is still commercial and we cannot fix this now...this situation just leads to less Linux and Ubuntu users because of broken functionality.

---

### Post by taavikko on 2008-10-02
Lot of answers in the thread...
few got lost in the rails, but thats okay ;)

Issue with this "buy from canonical" only concerns gnome,
I've been told that KDE users are not affected.

Like plun said, totem-mozilla is out of order.
In Finland we have this general broadcasting company called "yle"
similar to BBC.
They have service called "live archive" (I translated it from elävä arkisto)
which holds video and audio footage, since the beginning of this company.
Intrepid users are unable to view contents from it. At the moment.
Hardy worked fine. 
yle has announced switching their format of use, to be changed so everyone
regardless which OS in use, are able to enjoy the contents.

So how can we, as users and advocates of free software, promote the use of free software in web. So everyone would be able to view and enjoy
rich media experience?

I suspect everyone here understand why companies are being started..
To make money, but with what cost?
Every country have their own legislation, but if someone could explain to me, how can goverment (democratic nation) force me to pay for software...
If I buy DVD-player, I already pay for "copyrights"[1] If I buy blank DVD's, I pay for "copyrights"
If I buy DVD-movie, I cannot watch it in my ubuntubox...
Because of patents and copyright infrigments...
When did the world go haywire?

To the issue, medibuntu has provited tools to watch restricted content, 
It at least should deserve to be mentioned along with canonical.store.

[1] "copyrights" means that every sold blank CD/DVD we pay few 0.x&#8364; sents
to balance the loss of income due to piracy. (in Finland anyway)
[http://en.wikipedia.org/wiki/Private_copying_levy](http://en.wikipedia.org/wiki/Private_copying_levy)

sorry for mispelling and such, hard to translate some words, cause not an native language.

---

### Post by ronacc on 2008-10-02
All we can do is express our displeasure to companies that make the choice to use closed codecs to encode their content . Hopefully as linux becomes more popular they will pay attention to our wishes . Don't buy content from buisnesses and sites that use propriatary non-free encoding and let them know why you aren't buying , they are in buisness to make money , that they will pay attention to .

---

### Post by Nullack on 2008-10-02
I was wondering when this topic would come up :) Im still on Holidays at an internet cafe but Ill chime in

Just about everything needed can be done via free codecs and I couldnt care less if using a certain decoder was legal in my country. Nor could the courts in my country, as no one has ever been convicted against such "offences". In fact, I would think it likely to be overturned by jury rather than enforced.

The only thing I miss is being able to decode WMA Pro audio, but thats coming in future ffmpeg builds and some work was done at the GSOC.

---

### Post by wilsong on 2008-10-03
I think they should offer the FREE over over anything with a HUGE page saying "DOWNLOAD THE FREE OPTION" and then at the very bottom put a small little link warning "if you are in the USA or countries that have some sort of copy right if you use the free version you might be doing something illegal" and then provide a link to a site that may let you purchase

because I am in the US and I will probably no matter what not pay for a codec, even if content i want is in the wrong form, I want freedom to play things and do stuff the whole court libdvdcss stuff and the DMCA  is horrible.. 

GNU is awesome lets all program something to tear down the walls... if someone wants to start a project for Indeo Video version 5.0 to write some free codec to decode it be my guest! 

I will be honest and say that I wont pay for music, movies, software, ect unless i feel that the artist or movie i like is something i really enjoy or like and even then i may not, i just feel 1 money is too tight (maybe if i was a millionaire i wouldnt care as much) and two i love the Utopian ideas and everything that started linux.  I hate when people bend to the will of DMCA , RIAA, any big wealthy power 

I still cant believe the court banning code!! making shirts that had the code of libdvdcss illegal! how lame!!!!! i understand intellectual property, but if someone creates a way to decode your encoded intelligence (singal, movie(video) music(audio))  but they do it a different way to recreate the same, or near same thing (like mp3 compression its not the "same" as a CD quality but pretty close) then you cant fault them! I really hope ubuntu changes this!

---

### Post by plun on 2008-10-03
> **Nullack said:**
> I was wondering when this topic would come up :) Im still on Holidays at an internet cafe but Ill chime in

Just about everything needed can be done via free codecs and I couldnt care less if using a certain decoder was legal in my country. Nor could the courts in my country, as no one has ever been convicted against such "offences". In fact, I would think it likely to be overturned by jury rather than enforced.

The only thing I miss is being able to decode WMA Pro audio, but thats coming in future ffmpeg builds and some work was done at the GSOC.

Well..

I have full respect for different democratic country's jurisdiction within this area.

Also that we have copyrights and I just hope that all free copyrights will be the future.

I have no respect for a few mega company's which tries to rule the world.

Within the European Union we don't have any software patents !


So I just don't want any "killswitch" for a user to buy a codec without
facts and why a user should buy it.

Most important is to choose todays best solution within Intrepid.

totem-mozilla  :(


Enjoy your Holiday !...:D

---

### Post by wilsong on 2008-10-03
point people to this page, 

[https://help.ubuntu.com/ubuntu/desktopguide/C/common-tasks-chap.html](https://help.ubuntu.com/ubuntu/desktopguide/C/common-tasks-chap.html)

it will tell how to install the old stuff, just sucks there isnt 1 step package to enable all this if you live in a country where its not illegal (even if you did you should still have the choice) i believe its all about choices thats the problem MS got in with windows it didnt give people a choice.. if you have a choice to pick one or two and you pick 2 instead of 1 and you break a law, atleast ubuntu can say they were given a choice.. saying theres "no matching codec" but saying i can buy one is very misleading because im fixing to be able to play this video by installing something free after doing some research.. makes me so mad! grrr.. whats next RIAA pop up warnings when i try to enable mp3 playback? Nag screens everytime i try to play an mpeg! GRR

---

### Post by taavikko on 2008-10-03
> **Nullack said:**
> I was wondering when this topic would come up :) Im still on Holidays at an internet cafe but Ill chime in

Just about everything needed can be done via free codecs and I couldnt care less if using a certain decoder was legal in my country. Nor could the courts in my country, as no one has ever been convicted against such "offences". In fact, I would think it likely to be overturned by jury rather than enforced.


You're having vacation on a internet cafe? ;)

Civil disobedience, could be worthwhile, but it wouldn't make things any better. Ubuntu couldn't be published internationally, if it didn't care about those legal issues. (Linux Mint (ubuntu derivate) can be downloaded in only handful of mirrors, due to those built-in changes ???)

---

