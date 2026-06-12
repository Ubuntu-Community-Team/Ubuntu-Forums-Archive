---
title: "Do You Think Adobe Will Release A Stable Flash Plugin Before Release? Or Ever?"
date: 2008-09-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-09-08
Like many people, I don't like to use closed source plugins that the Ubuntu devs can't modify, but when it comes to Flash, there's not much of a choice if you're into Youtube and Hulu heavily. Not only that, but virtually every website these days uses it in some forms.

I don't think Adobe has ever released a stable flash plugin that I'm aware of. Every Ubuntu release so far has suffered from the "Incredible Disappearing Firefox" bug, at least on my systems. 

With Intrepid, browsing is MUCH worse. Almost every site crashes Firefox if it has too many Flash animations going on. Even if it doesn't crash Firefox, I still have to exit and reopen all my tabs because after watching one flash video, all other flash animations are greyed out.

Of course I understand this is beta, however I don't blame this issue on the fact Intrepid is beta, rather I blame it on Adobe releasing the worst browser plugins on the planet. For me, browsing is a very huge deal and I'm wondering if Adobe is going to get their act together before Intrepid comes out, or if they're going to make us Linux users suffer for the next two or three years with problems they refuse to fix.

Sorry to go off on a tangent, but the whole point in all of this is that I'm wondering the following things and was hoping someone can ease my concerns.

1.) Do you think Adobe will finish Flash 10 before Intrepids release, and even if they do, do you think it will solve any issues?

2.) Has nspluginwrapper matured to the point where it can handle the flash plugin as a separate process and not close Firefox? Or even restart the flash plugin automatically for you if it dies and not make you have to restart the browser manually?

3.) Is there a new nspluginwrapper or flash plugin I can test for you guys to help this process along?

I want to do whatever I can to help out and solve these issues. I know if I knew C++ I would focus most of my free time fixing this if I knew how. :(

At this point I just don't have any faith in Adobe when it comes to releasing a stable flash plugin. Heck, by the time they support 64-bit on their own, 128-bit will be standard by then.

---

### Post by RAOF on 2008-09-09
It's not really an answer to your question, but the recently-updated swfdec-mozilla in Intrepid seems to play youtube fine.  It also managed [aperturescience.com](aperturescience.com) (although it got a bit freaked out by my dvorak keymap).

I can't try Hulu, 'cause I'm not in the USA.  swfdec *might* be good enough for you.

---

### Post by jlacroix on 2008-09-09
> **RAOF said:**
> It's not really an answer to your question, but the recently-updated swfdec-mozilla in Intrepid seems to play youtube fine.  It also managed [aperturescience.com](aperturescience.com) (although it got a bit freaked out by my dvorak keymap).

I can't try Hulu, 'cause I'm not in the USA.  swfdec *might* be good enough for you.

I didn't know Hulu was country specific, that sucks.

Anyway if swfdec can allow me to accurately view myspace profiles, youtube videos, Hulu, and band web sites then that would be more than fine.

Although, I will probably stick with Flash, because if I am not using Adobe's Flash plugin, then I can't help the developers test it so that hopefully other people won't have problems with it when Intrepid goes final.

That was also the main reason I switched to Intrepid, was because it was the only way I could ensure Intrepid to be the OS I need it to be. (By reporting bugs). I do have faith that the developers will find stability work arounds even if Adobe's Flash sucks when it's final. I just wish there was something I could do to help.

For example, if I go to [www.fordidofans.net](www.fordidofans.net), Firefox closes almost instantly.

I am also wondering about Konqueror's implementation in Intrepid. As of right now, I cannot check my gmail on it, or watch youtube videos. Anyone know if it's because Konqueror sucks, or there is a bug I need to report specific to Intrepid?

---

### Post by plun on 2008-09-09
Well, we have a long thread about this issue and Adobe RC1 works just fine. (32 bit)

For some unknown reasons Firefox is really outdated in Intrepid..:confused:   Windowless mode crashes

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)


> Firefox 3 - serious crashes with Flash v10 and swfdec, unrelated to PulseAudio; Flash v10 works perfectly with PulseAudio (and without the need for libflashsupport), but Firefox 3 has a serious bug with the new "windowless mode" support in the new Flash and swfdec releases. As soon as this bug is fixed, Flash v10 will become a viable alternative to Flash v9, and bug #192888 can be marked invalid: Bug #239182: segfualt in cairo_draw_with_xlib


I also hope that Ubuntus maintainer for PulseAudio **"visits upstream"** and Fedora sits in the same boat and Lennart Poettering works for Redhat...

swfdec crashes with latest pulseaudio


Flash is also about high definition streams and YouTube uses a low quality stream.

---

### Post by The Keeper on 2008-09-09
swfdec 0.8 was released just yesterday. It should work with PulseAudio, does it not?

Can we somehow have swfdec 0.8 in Ibex, maybe even replacing adobe's player by default in ubuntu-restricted-extras package?

---

### Post by Casper Hansen on 2008-09-09
I use the Flash Player 10 Beta and I haven't got any problems after installing libflashsupport - though I don't know if libflashsupport supports Flash Player 10 Beta, but it fixed my problems. 

Youtube runs fine and other flash related sites. Though I have some weird problems accessing [http://reviews.cnet.com/mp3-players/creative-zen-8gb/4505-6490_7-32589081.html](http://reviews.cnet.com/mp3-players/creative-zen-8gb/4505-6490_7-32589081.html) and another site I can't remember. Strange, but it really doesn't bother me.

---

### Post by plun on 2008-09-09
> **The Keeper said:**
> swfdec 0.8 was released just yesterday. It should work with PulseAudio, does it not?

Can we somehow have swfdec 0.8 in Ibex, maybe even replacing adobe's player by default in ubuntu-restricted-extras package?

Well... its more important to first solve Firefox  > then PulseAudio
and Ubuntu must go upstream !

swfdec crashes, tested this weekend...

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/262326](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/262326)

Firefox will also crash because of the windowless mode bug. 

This is **key areas** for Intrepid and for mainstream users which was 
heavily broken in Hardy !

---

### Post by jlacroix on 2008-09-09
If this bug relies on a newer version of Firefox, Libflashsupport, and/or Flash, are those packages going to hit the repositories?

I'm trying to keep my packages identical to what Ubuntu offers in the repositories, so I know things will be fixed without having to do anything special.

---

### Post by RAOF on 2008-09-09
> **The Keeper said:**
> swfdec 0.8 was released just yesterday. It should work with PulseAudio, does it not?

Can we somehow have swfdec 0.8 in Ibex, maybe even replacing adobe's player by default in ubuntu-restricted-extras package?

0.7.4, which is in Intrepid now, works with pulseaudio, yes.

Just to clarify.  swfdec-mozilla + firefox from the Intrepid repositories works for me *right now* (with pulseaudio from TheMuso's PPA).  I don't believe using Intrepid's standard pulseaudio will break anything.

---

### Post by plun on 2008-09-09
> **RAOF said:**
> 0.7.4, which is in Intrepid now, works with pulseaudio, yes.

Just to clarify.  swfdec-mozilla + firefox from the Intrepid repositories works for me *right now* (with pulseaudio from TheMuso's PPA).  I don't believe using Intrepid's standard pulseaudio will break anything.

Well, this is about "learning the lesson" as Lennart wrote in his blog...

Luke must go upstream and talk with the Fedora guys and maybe Lennart himself.

[http://0pointer.de/blog/projects/jeffrey-stedfast.html](http://0pointer.de/blog/projects/jeffrey-stedfast.html)

> **The Distributions' Role in the Game**

Some distributions did a better job adopting PulseAudio than others. On the good side I certainly have to list Mandriva, Debian[3], and Fedora[4]. **OTOH Ubuntu didn't exactly do a stellar job**. They didn't do their homework. Adopting PA in a distribution is a fair amount of work, given that it interfaces with so many different things at so many different places. The integration with other systems is crucial. The information was all out there, communicated on the wiki, the mailing lists and on the PA IRC channel. But if you join and hang around on neither, then you won't get the memo. To my surprise when Ubuntu adopted PulseAudio they moved into one of their 'LTS' releases rightaway [5]. Which I guess can be called gutsy -- on the background that I work for Red Hat and PulseAudio is not part of RHEL at this time. I get a lot of flak from Ubuntu users, and I am pretty sure the vast amount of it is undeserving and not my fault.

I am rather sure that this is better solved with a new version...:)

---

### Post by plun on 2008-09-09
Maybe this also is important...

**Features/GlitchFreeAudio**

[http://fedoraproject.org/wiki/Features/GlitchFreeAudio](http://fedoraproject.org/wiki/Features/GlitchFreeAudio)

---

### Post by Taxman415a on 2008-09-09
> **jlacroix said:**
> Although, I will probably stick with Flash, because if I am not using Adobe's Flash plugin, then I can't help the developers test it so that hopefully other people won't have problems with it when Intrepid goes final.

That was also the main reason I switched to Intrepid, was because it was the only way I could ensure Intrepid to be the OS I need it to be. (By reporting bugs). I do have faith that the developers will find stability work arounds even if Adobe's Flash sucks when it's final. I just wish there was something I could do to help.

swfdec is flash and that's the whole point of having something like it and gnash (another opensource flash effort) so that developers can test it and modify it. The opensource ones are the ones that we really want to improve and be bug free for Intrepid because you're right, Adobe probably never will come through. swfdec and gnash both have some ways to go as I understand it, but that just means testing and bug reports are all the more important.

I'm not sure why gnash and swfdec aren't joining forces more instead of duplicating effort though.

---

### Post by psyke83 on 2008-09-09
In answer to the title of this thread: Adobe have already released a stable plugin. Flash 10 RC works *perfectly*, but there are issues elsewhere that need to be solved, which is why it's taking a while for the update to appear. This explains everything: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403/comments/14](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403/comments/14)

---

### Post by xebian on 2008-09-09
> **jlacroix said:**
> 

For example, if I go to [www.fordidofans.net](www.fordidofans.net), Firefox closes almost instantly.



No problem here.  Box is asus m2npv-vm nv GE6150 builtin card 6G ram AMD x2 4200.

Hardy 2.6.24-19, NV 177.70, Flash d569, Firefox 3.0.1.  Even Konqueror did pretty well including her official site.  The animated free mp3 page played very well.

Intrepid 2.6.27-2, generic nv driver, Flash d525 Firefox 3.0.1.  Didn't try Konqueror yet but I'm sure it will work.

No libflashsupport.

Thanks for the link though. I'm enjoying her music now.

---

### Post by dabl on 2008-09-09
Kubuntu 8.10 64-bit, updated here.

As of last night FF3 with flashplugin-nonfree, mozilla-plugin-gnash, and mozilla-mplayer was playing the following video sites:

youtube.com
foxnews.com
cnn.com
abcnews.com
[www.bbc.co.uk](www.bbc.co.uk)

But not this one:  [http://www.elsevier.nl/](http://www.elsevier.nl/)

Is that about what you are experiencing?

---

### Post by olskar on 2008-09-09
- Please ignore -

---

### Post by philinux on 2008-09-09
[http://www.fordidofans.net/](http://www.fordidofans.net/)

Plays fine here too. Flash 9.0 r124

---

### Post by plun on 2008-09-09
> **dabl said:**
> Kubuntu 8.10 64-bit, updated here.

As of last night FF3 with flashplugin-nonfree, mozilla-plugin-gnash, and mozilla-mplayer was playing the following video sites:

But not this one:  [http://www.elsevier.nl/](http://www.elsevier.nl/)

Is that about what you are experiencing?

With Adblock Plus disabled also the dutch site works.

--------------------------------------

To the challenge.....  **Adobe 10 will soon be final.**

Adobe 10 Release Candidate works just fine  !!!!

BUT  Please read...!

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182)

[https://bugzilla.mozilla.org/show_bug.cgi?id=435764](https://bugzilla.mozilla.org/show_bug.cgi?id=435764)

So Firefox must be upgraded....

To avoid the mess  :( as with Hardy its probably better to do this as soon as possible....

There are also benefits with a newer PulseAudio version. (also regressions probably)

swfdec is broken with version 0.11.


Its now we have time to test.... and devs communicates with other devs within the eco system, doing nothing will probably end as with Hardy.

A new PulseAudio version was also released today !

---

### Post by jlacroix on 2008-09-09
I'm hoping Firefox 3.0.2 ends all this mess I've been going through.

I need to get something straight, am I supposed to have libflashsupport, or am I supposed to not have it?

---

### Post by olskar on 2008-09-09
> **jlacroix said:**
> I'm hoping Firefox 3.0.2 ends all this mess I've been going through.

I need to get something straight, am I supposed to have libflashsupport, or am I supposed to not have it?

I think not, check [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

### Post by plun on 2008-09-09
> **jlacroix said:**
> I'm hoping Firefox 3.0.2 ends all this mess I've been going through.

I need to get something straight, am I supposed to have libflashsupport, or am I supposed to not have it?

This is the key....

You can use this [ppa]("https://launchpad.net/~fta/+archive") and run a newer Firefox.

During this summer we have tested Adobe 10 and "psyke83" probably knows
this best from the community.

From his thread:

> Firefox 3 - serious crashes with Flash v10 and swfdec, unrelated to PulseAudio; Flash v10 works perfectly with PulseAudio (and without the need for libflashsupport), but Firefox 3 has a serious bug with the new "windowless mode" support in the new Flash and swfdec releases. As soon as this bug is fixed, Flash v10 will become a viable alternative to Flash v9, and bug #192888 can be marked invalid: Bug #239182: segfualt in cairo_draw_with_xlib

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

This works: (as I recalls it)
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

But there was also a "dev call for testing" a new PA version...
[http://ubuntuforums.org/showthread.php?t=904171&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=904171&highlight=pulseaudio)

And today a new PA version was out.So someone must coordinate this !!  IMHO...   Hardy mess risk and this is key areas.

"psyke83" also tried to communicate with devs but it was only a few answers within the mailing list...:(
[B]
EDIT [/B] latest Firefox for Intrepid must include the Windowless mode fix
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.2) Gecko/2008090211 Ubuntu/8.10 (intrepid) Firefox/3.0.2pre

---

### Post by RAOF on 2008-09-09
> **plun said:**
> ...

swfdec is broken with version 0.11.

...

I'm not sure why you keep saying this.  I'm playing [this youtube video](http://www.youtube.com/watch?v=RthZgszykLs) right now with swfdec 0.7.4 and pulseaudio 0.9.11.

It may well be broken for you, but it's not broken for everyone!

---

### Post by jlacroix on 2008-09-09
Well, when it comes to testing Intrepid, I prefer not to use PPA's. Reason being I want to make sure that the issues are fixed in Ubuntu's default repository. That way when Intrepid goes final I'll know that first time installers will not need to jump through those hoops.

From what I read of all the bug reports so far, it seems to me this issue will be fixed next week. Please correct me if I'm wrong.

My only other question is Konqueror, and if that will ever show flash content properly, and if it's inability to render GMail and several other sites is its fault or a bug in Intrepid.

---

### Post by plun on 2008-09-09
> **jlacroix said:**
> Well, when it comes to testing Intrepid, I prefer not to use PPA's. Reason being I want to make sure that the issues are fixed in Ubuntu's default repository. That way when Intrepid goes final I'll know that first time installers will not need to jump through those hoops.

From what I read of all the bug reports so far, it seems to me this issue will be fixed next week. Please correct me if I'm wrong.

My only other question is Konqueror, and if that will ever show flash content properly, and if it's inability to render GMail and several other sites is its fault or a bug in Intrepid.

Well, then its just to hope for the best and your question about a stable Adobe is a big Yes as answer, Adobe 10 is just great compared with earlier versions.

At least for 32 bit.... just to roll it out !

Testing swfdec again...:)  I hope for a better result this time..

---

### Post by RAOF on 2008-09-09
> **jlacroix said:**
> ...
My only other question is Konqueror, and if that will ever show flash content properly, and if it's inability to render GMail and several other sites is its fault or a bug in Intrepid.

It should be able to show flash, and it should be able to render GMail.  Both are bugs which should be filed.

---

### Post by jlacroix on 2008-09-09
> **RAOF said:**
> It should be able to show flash, and it should be able to render GMail.  Both are bugs which should be filed.

I just checked Youtube again with Konqueror just now, and it worked. When did that happen? It was like two days ago last time I checked it.

However, Konqueror has the same bug as Firefox for me, that sometimes Flash stops working after a while. I played a Youtube video in Konqueror and then after about a minute clicked on a different one. Flash stopped working until I went in to a different site. Should I report this finding, or does it fall in line with the Firefox/Flash bug that was already reported?

As far as GMail not working, I checked Launchpad and it appears that it's pointing to a KDE bug, so perhaps that's just KDE's problem? I do find it strange that it worked in 3.5.x.

---

### Post by plun on 2008-09-09
> **RAOF said:**
> I'm not sure why you keep saying this.  I'm playing [this youtube video](http://www.youtube.com/watch?v=RthZgszykLs) right now with swfdec 0.7.4 and pulseaudio 0.9.11.

It may well be broken for you, but it's not broken for everyone!

Well... strange trouble

```
sudo apt-get remove flashplugin-nonfree && sudo apt-get install swfdec-gnome swfdec-mozilla
```


```
locate libflashplayer.so

plun@plun:~/exaile$ locate libflashplayer.so
/home/plun/.mozilla/plugins/libflashplayer.so

```

Somewhere I must have a symlink...:confused:

usr/lib/mozilla checked..


Test station, Swedish National Public TV  [http://playrapport.se/](http://playrapport.se/) > nothing

You Tube crashes.... (your URL)

Time to sleep...:)

---

### Post by Nullack on 2008-09-09
I sincerely hope that the many problems npviewer.bin get fixed. Along with NM 0.7, these two issues are critical in my eyes for the path leading to beta.

---

### Post by xebian on 2008-09-09
> **plun said:**
> 


Test station, Swedish National Public TV  [http://playrapport.se/](http://playrapport.se/) > nothing


Time to sleep...:)

Have no problem with playrapport.se.  Just could not understand what they are saying but the video is stunningly very clear even at large screen.  I could guess some are at Georgia bec of the Russian flag and tanks.

---

### Post by plun on 2008-09-10
> **Nullack said:**
> I sincerely hope that the many problems npviewer.bin get fixed. Along with NM 0.7, these two issues are critical in my eyes for the path leading to beta.

Yup

- Connect to a network

- Watching/Playing Internet Media

- Playing Music with glitch free audio....

Basic needs for a mainstream user.... must just work.

------

@Xebian..  Adobe 10 RC works excellent and this is also a high quality stream...   swfdec fails for me.

---

### Post by psyke83 on 2008-09-10
> **jlacroix said:**
> Well, when it comes to testing Intrepid, I prefer not to use PPA's. Reason being I want to make sure that the issues are fixed in Ubuntu's default repository. That way when Intrepid goes final I'll know that first time installers will not need to jump through those hoops.

In your original post, you asked if there were any new packages you could test... Aside from the official repositories, testing from PPAs are the next best step. Of course, you are taking a leap of faith by assuming there is nothing malicious in a PPA archive, but at least there's accountability since it's hosted on a Canonical-run service, and associated to a user. As long as you know how to downgrade packages, you *should* be testing from PPAs for fringe issues that may need testing before being accepted into the development release (e.g. OpenOffice 3, PulseAudio 0.9.12).

As I said earlier, the problems with Flash will be resolved. It wasn't purely Adobe's fault for these crashes, it was also ours (i.e. the Ubuntu developers & community): 

a) It's been well-known for a long time that "libflashsupport" causes crashes, but it's still included for 64bit users (within the ia32-libs package), and some outdated guides tell 32 bit users to manually install the package, which causes crashes for most users. This can now be fixed, as Flash 10 can work with PulseAudio's ALSA plugins, rendering "libflashsupport" obsolete.

b) Flash 10 RC now depends on external libraries. This isn't an issue for 32bit users, but for 64 bit users it's a bit more complicated. The ia32-libs package (of which the source package is 450mb+) needs to be updated with the new dependencies. This is currently being addressed, but it may take a little time to be released.

c) Firefox currently has a bug in its handling of windowless mode content. This is not Adobe's fault, and the next Firefox update (3.0.2) will resolve the issue. Alternatively, one can disable windowless mode in the Flash plugin as a temporary measure.

d) Older nspluginwrapper versions did not support windowless mode, but the newest release does. I believe this has been addressed with a recent update.

Look at my earlier post referencing the appropriate bug report, and everything is explained.

---

### Post by jlacroix on 2008-09-10
> **psyke83 said:**
> In your original post, you asked if there were any new packages you could test... Aside from the official repositories, testing from PPAs are the next best step. Of course, you are taking a leap of faith by assuming there is nothing malicious in a PPA archive, but at least there's accountability since it's hosted on a Canonical-run service, and associated to a user. As long as you know how to downgrade packages, you *should* be testing from PPAs for fringe issues that may need testing before being accepted into the development release (e.g. OpenOffice 3, PulseAudio 0.9.12).

As I said earlier, the problems with Flash will be resolved. It wasn't purely Adobe's fault for these crashes, it was also ours (i.e. the Ubuntu developers & community): 

a) It's been well-known for a long time that "libflashsupport" causes crashes, but it's still included for 64bit users (within the ia32-libs package), and some outdated guides tell 32 bit users to manually install the package, which causes crashes for most users. This can now be fixed, as Flash 10 can work with PulseAudio's ALSA plugins, rendering "libflashsupport" obsolete.

b) Flash 10 RC now depends on external libraries. This isn't an issue for 32bit users, but for 64 bit users it's a bit more complicated. The ia32-libs package (of which the source package is 450mb+) needs to be updated with the new dependencies. This is currently being addressed, but it may take a little time to be released.

c) Firefox currently has a bug in its handling of windowless mode content. This is not Adobe's fault, and the next Firefox update (3.0.2) will resolve the issue. Alternatively, one can disable windowless mode in the Flash plugin as a temporary measure.

d) Older nspluginwrapper versions did not support windowless mode, but the newest release does. I believe this has been addressed with a recent update.

Look at my earlier post referencing the appropriate bug report, and everything is explained.

I understand what you're saying, however if I install a PPA package and it does fix my issue, then how would I know that the PPA is required or not when Intrepid goes final? My main goal is for this to be fixed for everyone, so when someone installs Intrepid for the first time when it goes final, they won't need to jump through any hoops.

---

### Post by psyke83 on 2008-09-10
> **jlacroix said:**
> I understand what you're saying, however if I install a PPA package and it does fix my issue, then how would I know that the PPA is required or not when Intrepid goes final? My main goal is for this to be fixed for everyone, so when someone installs Intrepid for the first time when it goes final, they won't need to jump through any hoops.

You can know that the PPA won't be required since it's discussed on the bug reports ;). You can see that the pieces are being put together and will be released soon. My post was explaining the complexity (and therefore delay) in the release of the new version of the plugin.

See:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403)
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403/comments/14](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403/comments/14)

P.S. Preview packages in a PPA will usually become obsoleted, provided the packager has followed the appropriate guidelines regarding package versioning. Usually it's not a problem to test "preview" packages for low-key updates when there's a high chance it will be included in the official release, as the release version will be considered a newer version.

---

### Post by caryb on 2008-09-10
For your info I added the FF PPA & installed FF 3.0.2PRE & flash is worse! I have the greyed out box where I used to have the flash boxes in youtube etc. This is not the Saviour we are looking for.


Cary

---

### Post by RAOF on 2008-09-10
> **jlacroix said:**
> I understand what you're saying, however if I install a PPA package and it does fix my issue, then how would I know that the PPA is required or not when Intrepid goes final? My main goal is for this to be fixed for everyone, so when someone installs Intrepid for the first time when it goes final, they won't need to jump through any hoops.

In general, you wouldn't.  However, the pulseaudio PPA that we're referring to is the PPA of the prime Ubuntu audio maintainer, and he's uploaded these packages to it precisely for testing before rolling out to the greater archive (if, infact, they test well).  This was announced on the ubuntu-devel mailing list, and bounced to a post in this forum.

---

### Post by SunnyRabbiera on 2008-09-10
For me i have been using flash 10 beta, and it seems to actually work better then flash 9 in general.
But i guess i am a lucky person with it

---

### Post by psyke83 on 2008-09-10
> **caryb said:**
> For your info I added the FF PPA & installed FF 3.0.2PRE & flash is worse! I have the greyed out box where I used to have the flash boxes in youtube etc. This is not the Saviour we are looking for.


Cary

It has been mentioned before that the 32bit libraries aren't yet ready for 64bit users. You will need to wait for the ia32-libs update or manually install libraries using getlibs.

This guide (*for Hardy*) explains the process in step 1a: [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

I do recommend you wait for the ia32-libs update, or else look for support in the 64bit subforum for getlibs issues.

---

### Post by victorche on 2008-09-15
There is Flash Player 10.0.12.10 RC:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz)

:)

I hope it works better ;) More info about the release here:
[http://labs.adobe.com/technologies/flashplayer10/releasenotes.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes.html)

---

### Post by of_darkness on 2008-09-15
> **victorche said:**
> There is Flash Player 10.0.12.10 RC:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz)

:)

I hope it works better ;) More info about the release here:
[http://labs.adobe.com/technologies/flashplayer10/releasenotes.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes.html)

But it has a severe bug, you must dissable compositing to use Flash Player 10.0.12.10 RC

> For Linux, the hardware acceleration feature will not work if you are using a compositing window manager (compiz).  In this case, Flash Player 10 Beta will always fall back to software.  If you would like to test Flash Player 10 Beta on Linux, please disable your compositing window manager.

to mee it sounds severe if you use compiz or other compositing..

---

### Post by olskar on 2008-09-15
> **of_darkness said:**
> But it has a severe bug, you must dissable compositing to use Flash Player 10.0.12.10 RC



to mee it sounds severe if you use compiz or other compositing..


But hasn't that been the case for some time now? At least with Flash 10?

---

### Post by jlacroix on 2008-09-15
I've never had to disable compositing with Flash. With KDE 4.1 this is REALLY severe because the desktop just isn't the same without it. GNOME has also received some features with compositing that's hard to live without, like changing workspaces with the mouse wheel.

---

### Post by olskar on 2008-09-15
But you had to disable compositing to use hardware acceleration with flash, you do not have to disable it to use flash. If you use compositing it simply not use hardware acceleration

---

### Post by jlacroix on 2008-09-15
> **olskar said:**
> But you had to disable compositing to use hardware acceleration with flash, you do not have to disable it to use flash. If you use compositing it simply not use hardware acceleration

I never noticed a difference either way.

---

### Post by plun on 2008-09-15
This version works just great.....as the RC before.  (32 bit Ubuntu)

The beta in Ubuntus repo is not good.

---

### Post by of_darkness on 2008-09-15
> **olskar said:**
> But you had to disable compositing to use hardware acceleration with flash, you do not have to disable it to use flash. If you use compositing it simply not use hardware acceleration

okaay i dunno i just focused that they told you to dissable compositing to try out flash 10rc.. i havent read the changlogs before to be honest:P

wonder if it works on 64bit ? the last rc dident work.. only the version before does..

---

### Post by olskar on 2008-09-15
> **jlacroix said:**
> I never noticed a difference either way.

Me neither so it's not a serious bug for me at least :)

---

### Post by of_darkness on 2008-09-15
> **plun said:**
> This version works just great.....as the RC before.  (32 bit Ubuntu)

The beta in Ubuntus repo is not good.

well the onme before diddent work on 64bit as they had put in some detection part in the installer :/  i would be intresting to know if this one works on 64bit.. (by the "hack" entiteld in the flash sticky in the 64bit forum here on ubuntuforums..

---

### Post by npman on 2008-09-15
Along the same theme of the original post in this thread...

Do you think Adobe will release 64-bit Flash?

Those of us who use 64-bit are getting more than little tired of having to go through the extra hoops that we have to go through to get Flash on 64-bit.

I fear that the progress being made with Flash 10, will not benefit those of us on 64-bit...

---

### Post by of_darkness on 2008-09-15
> **npman said:**
> Along the same theme of the original post in this thread...

Do you think Adobe will release 64-bit Flash?

Those of us who use 64-bit are getting more than little tired of having to go through the extra hoops that we have to go through to get Flash on 64-bit.

I fear that the progress being made with Flash 10, will not benefit those of us on 64-bit...


i fear it to after the previus version had the 32bit checker built in:/

and thats a real shame as more and more ppl are getting mordern comps and cannot raly use them to the maximum.. 

but sooner or later ppl are probly going over 2 g4bit as the nead to youse more ram then a 32bit mashine can use witout hacks.. and then ppl are going 2 demand 64bit flash plugins.. so soooner or later adobe must realice thje nead and the sence in making a 64bit version.. but howlong .. thats the intresting question..

---

### Post by psyke83 on 2008-09-15
The new RC(2) release of Flash is in my PPA. 64 bit users will still need to manually install some 32bit libraries (a temporary measure until ia32-libs is updated).

You can find instructions (and linked bug reports to explain) in my [PulseAudio Fixes (distilled)]("http://ubuntuforums.org/showthread.php?t=866965") thread. This is the only guaranteed way to get audio working correctly with PulseAudio & Flash, and *needs testing in order to become the official configuration*. So, please test.

---

### Post by pferraro on 2008-09-15
Works great here on 64-bit.
High quality youtube and google videos now work as well.

---

### Post by xebian on 2008-09-15
> **psyke83 said:**
> The new RC(2) release of Flash is in my PPA. 64 bit users will still need to manually install some 32bit libraries (a temporary measure until ia32-libs is updated).

You can find instructions (and linked bug reports to explain) in my [PulseAudio Fixes (distilled)]("http://ubuntuforums.org/showthread.php?t=866965") thread. This is the only guaranteed way to get audio working correctly with PulseAudio & Flash, and *needs testing in order to become the official configuration*. So, please test.

Looks like this is a final release.  It's coded r12 instead of the 'dxxx' for development.

At Adobe's Flash download site, it's telling me I have

```
You have version 10,0,12,10 installed
```

Looking great

---

### Post by jlacroix on 2008-09-15
> **npman said:**
> Along the same theme of the original post in this thread...

Do you think Adobe will release 64-bit Flash?

Those of us who use 64-bit are getting more than little tired of having to go through the extra hoops that we have to go through to get Flash on 64-bit.

I fear that the progress being made with Flash 10, will not benefit those of us on 64-bit...

Absolutely! Adobe will DEFINITELY release a 64-bit version of their flash plugin. It will likely happen around the time that 128-bit becomes standard.

---

### Post by el-mar01 on 2008-09-16
That annoying bug where you would close fullscreen video and it wouldn't continue playing has been fixed (you had to double click on the flash object) .. also fullscreen video is much smoother now.

---

### Post by jagrav on 2008-09-20
With the latest version, 10.0.12.10, the player area is blank when i play some remote movies. On right-click i get a 'Movie not loaded' message. The same movies play fine when loaded locally. This is in FF 3.0.1 and Epiphany. anyone else have this problem?
In Opera 9.51 and Konqueror, however, there is no problem.

---

### Post by knarf on 2008-09-20
Yup, same here in both FF 3.0.2 and 3.1. Loading another movie on the same page (for those pages which have more than one movie) sometimes makes the missing movie show up. The latest flash also dislikes certain types of movie it seems, leading to Youtube stating that 'this movie is no longer available' when it plays fine in older Flash versions...

---

