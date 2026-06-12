---
title: "[SOLVED] Flash v10 Beta 2 crashes - workaround, please test!"
date: 2008-07-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by psyke83 on 2008-07-11
[COLOR="Red"]EDIT: The source of the bug has been identified, there's no need to test this solution any more. Thanks to everyone who contributed.
See here: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182)[/COLOR]

As described in this [bug]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247682"), the latest Flash v10 beta is causing some sites to crash in Firefox 3 for 32bit users. The following is a proposal to fix (or rather, workaround) these crashes. Please report in **this** thread if the following workaround is successful, so we can collect feedback for the bug report.

**Proposed Fix (i386 ONLY):**

1. Remove libflashsupport and flashplugin-nonfree:
```
$ sudo apt-get remove libflashsupport flashplugin-nonfree
```
2. Download & install my i386 nspluginwrapper package:```
$ wget -c http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb
$ sudo dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb
```
3. Reinstall flashplugin-nonfree:```
$ sudo apt-get install flashplugin-nonfree
```
4. Close & reopen Firefox, and test any previously affected sites.

**Example sites:**
[http://polidics.com/](http://polidics.com/)
[http://weblog.infoworld.com/ittroubleshooter/archives/2007/09/remember_when_m.html](http://weblog.infoworld.com/ittroubleshooter/archives/2007/09/remember_when_m.html)
(Please let me know if there are any other sites that crash 100% reproducibly, and I'll add them here)

---

### Post by psyke83 on 2008-07-11
From another thread:

> **xebian said:**
> Why is nspluginwrapper now necessary for 32bits?  It's required for 64bit bec the flash plugin binary is 32bit AFAIK.

You're correct, but it can be also be used on a 32bit system.

Normally, if Flash crashes, it causes Firefox to crash, as it is part of the "firefox" process. Using nspluginwrapper, Flash becomes a separate process called "npviewer.bin", and if Flash crashes, only the "npviewer.bin" process will die, but Firefox will stay relatively immune.

I originally proposed using nspluginwrapper due to Flash v9's instability with libflashsupport on [bug #192888]("https://bugs.launchpad.net/bugs/192888"), starting at comment #37. The recent crashes with Flash 10 aren't PulseAudio-related, but nspluginwrapper also happens to work effectively in this case.

---

### Post by jerrylamos on 2008-07-11
On Ibex Alpha 1, it's a whole lot easier just to install Firefox-2 from Synaptic which works with flashplayer.  Alpha 2 iso looks pretty fat on 7/11; I'll wait a couple days to see if they can trim it down.

Jerry

---

### Post by psyke83 on 2008-07-11
> **jerrylamos said:**
> On Ibex Alpha 1, it's a whole lot easier just to install Firefox-2 from Synaptic which works with flashplayer.  Alpha 2 iso looks pretty fat on 7/11; I'll wait a couple days to see if they can trim it down.

Jerry

It may be easier to use Firefox 2, but the entire purpose of testing the development release is to fix bugs. Downgrading to Firefox 2 (which won't be the default for Intrepid) will not help us *at all*. 

Having said that, I can confirm Firefox 2 (without nspluginwrapper) does not exhibit the crash on a fresh profile. I tested the upstream version of Firefox 3, and it still crashes. So it could be a bug in the interaction between Flash 10 and Firefox 3 (but it appears the Ubuntu patches are not the cause of instability, as the upstream version has the same problem).

---

### Post by VicAlpha on 2008-07-12
tried this website: [http://polidics.com/](http://polidics.com/)

and had a crash

---

### Post by psyke83 on 2008-07-12
> **VicAlpha said:**
> tried this website: [http://polidics.com/](http://polidics.com/)

and had a crash

Go to the following page in Firefox: ```
about:plugins
```

You'll see the "Shockwave Flash" entry in bold. What is the "File name" listed underneath it? 

If it's "libflashplayer.so" you followed the guide incorrectly. If it's "npwrapper.libflashplayer.so", please let me know your system specs.

---

### Post by VicAlpha on 2008-07-12
OK, it's working now but it's Flash 9 not Flash 10. I uselly install Adobe Flash from the Adobe website itself, not from the Ubuntu repos.

---

### Post by psyke83 on 2008-07-12
> **VicAlpha said:**
> OK, it's working now but it's Flash 9 not Flash 10.

This thread is intended for testing Flash 10, I don't need feedback for Flash 9 as it doesn't have this bug. And a manual install of Flash could interfere with this workaround.

---

### Post by VicAlpha on 2008-07-12
Took care of it manually

>     Nom de fichier : npwrapper.libflashplayer.so
    Shockwave Flash 10.0.0 d525

[http://polidics.com/](http://polidics.com/) still crashes

---

### Post by Mayfoev on 2008-07-12
psyke83, it may be wise to add to the howto that :

```
sudo update-alternatives --config xulrunner-addons-flashplugin
``` might be needed in some cases in order to use npwrapper.libflashplayer.so instead of libflashplayer.so

---

### Post by nirv117 on 2008-07-12
[http://www.rottentomatoes.com/?](http://www.rottentomatoes.com/?)  always crashed for me.

I tried the work around and it no longer crashes.

one thing I noticed with the new flash version (even before the work around) was that some video wouldn't show up such as the video clips on espn.com for baseball highlights.  I noticed it starting with the most recent flash update.

---

### Post by spamzilla on 2008-07-12
Those site don't crash for me after doing your workaround, however now, I have no sound.

---

### Post by lundbymads on 2008-07-12
Thank you. Your fix works like a charm!

The Danish National Radio and TV's website [www.dr.dk](www.dr.dk) crashed all the time with the default flash 10 installed. Pretty annoying since it's my preferred start page. :-(

But thanks (a lot) again.

:-) Mads

---

### Post by mhenriday on 2008-07-12
**Psyke83**, other users : I have a **Creative Soundblaster X-Fi** card installed on my **64-bit AMD X2** setup, which led to no few difficulties getting the sound to work on **Ubuntu** prior to discovering **NullHead**, **Temüjin**, *et al*'s wonderful [*_thread_*]("http://ubuntuforums.org/showthread.php?t=571656"), which provided instructions allowing me to get the card to function almost as well on **Hardy** as it does on the **Windows** side of my triple-boot machine. At least until yesterday when I installed the latest version of the **non-free flashplugin** (**10.0.1.218+10.0.0525ubuntu1~hardy1**) ! I suddenly lost all sound on websites like **YouTube**, whereas playing from my own audio files with the **VLC Mediaplayer** was not affected. I'm not experiencing any **Firefox** (as a matter of fact, [**_Swiftweasel_**]("http://http://swiftweasel.tuxfamily.org/"), which browser I prefer) crashes after the installation, but being forced to leave my favourite OS for **Windows** to play a video clip is a pain ! I'd be most grateful for any suggestions which might help me to get things working again on my 64-bit system without installing a 32-bit workaround.... 

Henri

---

### Post by volanin on 2008-07-12
> **mhenriday said:**
> **Psyke83**, other users : I have a **Creative Soundblaster X-Fi** card installed on my **64-bit AMD** dualcore setup, which led to no few difficulties getting the sound to work on **Ubuntu** prior to discovering **NullHead**, **Temüjin**, *et al*'s wonderful [*_thread_*]("http://ubuntuforums.org/showthread.php?t=571656"), which provided instructions allowing me to get the card to function almost as well on **Hardy** as it does on the **Windows** side of my triple-boot machine. At least until yesterday when I installed the latest version of the **non-free flashplugin** (**10.0.1.218+10.0.0525ubuntu1~hardy1**) ! I suddenly lost all sound on websites like **YouTube**, whereas playing from my own audio files with the **VLC Mediaplayer** was not affected. I'm not experiencing any **Firefox** (as a matter of fact, [**_Swiftweasel_**]("http://http://swiftweasel.tuxfamily.org/"), which browser I prefer) crashes after the installation, but being forced to leave my favourite OS for **Windows** to play a video clip is a pain ! I'd be most grateful for any suggestions which might help me to get things working again on my 64-bit system without installing a 32-bit workaround.... 

Henri

Try this:
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Worked like a charm for me.
:)

---

### Post by psyke83 on 2008-07-12
> **mhenriday said:**
> **Psyke83**, other users : I have a **Creative Soundblaster X-Fi** card installed on my **64-bit AMD** dualcore setup, which led to no few difficulties getting the sound to work on **Ubuntu** prior to discovering **NullHead**, **Temüjin**, *et al*'s wonderful [*_thread_*]("http://ubuntuforums.org/showthread.php?t=571656"), which provided instructions allowing me to get the card to function almost as well on **Hardy** as it does on the **Windows** side of my triple-boot machine. At least until yesterday when I installed the latest version of the **non-free flashplugin** (**10.0.1.218+10.0.0525ubuntu1~hardy1**) ! I suddenly lost all sound on websites like **YouTube**, whereas playing from my own audio files with the **VLC Mediaplayer** was not affected. I'm not experiencing any **Firefox** (as a matter of fact, [**_Swiftweasel_**]("http://http://swiftweasel.tuxfamily.org/"), which browser I prefer) crashes after the installation, but being forced to leave my favourite OS for **Windows** to play a video clip is a pain ! I'd be most grateful for any suggestions which might help me to get things working again on my 64-bit system without installing a 32-bit workaround.... 

Henri

Sorry to say this, but you're in the wrong thread. This thread is for testing nspluginwrapper on 32bit systems (and it's the Intrepid subforum, not Hardy). Your system is 64bit, so this thread does not apply to you.

As for your specific issue, you have OSSv4 installed to replace the functionality of ALSA, and OSS may not be as well supported by PulseAudio. You'll need to ask in the other thread for support.

---

### Post by psyke83 on 2008-07-12
> **volanin said:**
> Try this:
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Worked like a charm for me.
:)

Do you have OSSv4 installed? I explicitly state in my guide that OSSv4 users shouldn't follow that guide, as the instructions are for ALSA. It won't work.

---

### Post by psyke83 on 2008-07-12
> **spamzilla said:**
> Those site don't crash for me after doing your workaround, however now, I have no sound.

Try following Part A of my guide (linked in the first post), or at the very least, install "libasound2-plugins". PulseAudio is not configured properly either in Hardy or Intrepid, unfortunately.

I have updated the guide to remove the step that dealt with configuring PulseAudio. Without that configured, Flash will try to get exclusive access of the sound card (the default behaviour in Hardy and Intrepid). If you're too lazy to try fixing PulseAudio, remove the .asoundrc file you previously created.

---

### Post by plun on 2008-07-12
Well,  tested a couple of hours and it seems to be much more stable.

(Mostly all ads junk with Flash is removed with Adblock Plus)


My "reference station" is Swedish National TV and it works
much better (high quality streams)

[http://playrapport.se](http://playrapport.se)

YouTube OK

BBC is still broken but thats a BBC problem as I understands it.


Swedish IDG is a trouble maker but no crashes yet...:)
[http://www.idg.se/](http://www.idg.se/)

Thanks !

---

### Post by knarf on 2008-07-12
On the subject of Swedish flash-encumbered sites... what about [http://www.smhi.se/cmp/jsp/polopoly.jsp?d=5236&l=sv](http://www.smhi.se/cmp/jsp/polopoly.jsp?d=5236&l=sv) , does that work for you? Ever since installing the flash 10 beta this site has produced nothing but "No Access, server does not respond, id=22, type=1" for me. Digging a bit further it turns out this seems to be caused by the absence of a crossdomain.xml file on natvader.smhi.se. I sent them a message about it more than a month ago but have not received a response. Does it work for you?

[SIZE="1"]I would have posted this as a personal message but was greeted by this page when I tried:

"*Sorry! , you should have at least 75 posts to use the Visitors Message.*"

For crying out loud, I only post when I have something to say so I do not amass that many messages. So now this is a public private message, courtesy of this silly BBS...[/SIZE]

---

### Post by psyke83 on 2008-07-12
> **knarf said:**
> On the subject of Swedish flash-encumbered sites... what about [http://www.smhi.se/cmp/jsp/polopoly.jsp?d=5236&l=sv](http://www.smhi.se/cmp/jsp/polopoly.jsp?d=5236&l=sv) , does that work for you? Ever since installing the flash 10 beta this site has produced nothing but "No Access, server does not respond, id=22, type=1" for me. Digging a bit further it turns out this seems to be caused by the absence of a crossdomain.xml file on natvader.smhi.se. I sent them a message about it more than a month ago but have not received a response. Does it work for you?

It may be a bug, but it's not related to the crashes this thread is dealing with.

---

### Post by knarf on 2008-07-12
[offtopic - private]

True, and that is why I would have sent that reply as a private message - if only the board allowed me... see footnote above...

---

### Post by plun on 2008-07-12
> **knarf said:**
> [offtopic - private]

True, and that is why I would have sent that reply as a private message - if only the board allowed me... see footnote above...

Well,  no SMHI is broken also for me...:)  


To the subject....  I cannot crash Firefox for the moment..

Even a heavy Flash site as the Olympic Games runs.
[B]
[http://en.beijing2008.cn/](http://en.beijing2008.cn/)[/B]

But... the flash randomly disappears after a few updates.


Running everything with Adblock Plus turned off....a better test..

---

### Post by psyke83 on 2008-07-12
> **plun said:**
> But... the flash randomly disappears after a few updates.

Yes, unfortunately I'm seeing this problem too. If you visit a site that previously caused a crash, it would appear to work correctly, but Flash will not work if you try to visit another Flash-enabled site. I guess it's not surprising - Flash is still crashing, but the Firefox process remains immune.

Unfortunately this bug seems to be in Firefox 3 itself (or perhaps Firefox 3 is exposing a bug in Flash v10 beta 2). I have an idea to possibly help this situation, I'll post more a little later.

---

### Post by plun on 2008-07-12
> **psyke83 said:**
> Yes, unfortunately I'm seeing this problem too. If you visit a site that previously caused a crash, it would appear to work correctly, but Flash will not work if you try to visit another Flash-enabled site. I guess it's not surprising - Flash is still crashing, but the Firefox process remains immune.

Unfortunately this bug seems to be in Firefox 3 itself (or perhaps Firefox 3 is exposing a bug in Flash v10 beta 2). I have an idea to possibly help this situation, I'll post more a little later.

Yup, maybe its time to add debugging symbols for Firefox and Xulrunner  

I remember this also from Hardys development when you writes it...

Annoying crashes...:)

---

### Post by kbozen on 2008-07-13
the last ubuntu update (with backports) solved the problem; it updated:

- firefox-3.0
(3.0.1+build1+nobinonly-0ubuntu0.8.04.1) hardy-proposed

- flashplugin-nonfree
(10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124 .0ubuntu2) hardy-backports

---

### Post by dmadiedo on 2008-07-13
You are right!

Installing the backport package did the trick for me.

you con download it at:

[http://packages.ubuntu.com/hardy-backports/i386/flashplugin-nonfree/download]("http://packages.ubuntu.com/hardy-backports/i386/flashplugin-nonfree/download")

Thanks!

---

### Post by ronacc on 2008-07-13
just for info . both the smhi and olympics site load and work in opera 9.52 64bit , the olympic site loads and works in firefox but not the smhi site , flash loading fails on that one for me .

---

### Post by plun on 2008-07-13
> **ronacc said:**
> just for info . both the smhi and olympics site load and work in opera 9.52 64bit , the olympic site loads and works in firefox but not the smhi site , flash loading fails on that one for me .

Do you have the wrapper installed ?

Running Opera from terminal gives this for me  32bit, 9.51.
Seems to crash similar as with FF3.

> opera: Plug-in 13400 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.

Gdk-ERROR **: The program 'operapluginwrapper' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 1249 error_code 9 request_code 55 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...


The Olympic site is nevertheless a world wide "mainstream" site for
reference testing...

[http://en.beijing2008.cn/](http://en.beijing2008.cn/)

---

### Post by psyke83 on 2008-07-13
Hey everyone,

This problem is actually a bug in Firefox 3 exposed by the latest beta of Flash. Nightly builds of Firefox (Minefield) dating from 2007-07-08 onwards work correctly without crashes using Flash 10 beta 2 (verified on my system).

See the bug linked in the first post, and here: [http://blogs.adobe.com/penguin.swf/2008/07/addessing_wmode_crashes.html](http://blogs.adobe.com/penguin.swf/2008/07/addessing_wmode_crashes.html)

Using nspluginwrapper is a workaround to prevent you losing your entire Firefox process, but in this case it's not good enough of a fix, as Flash will stop functioning after you visit a problematic site. The latest development release of nspluginwrapper has support for restarting crashed plugins, so it may be a slightly better workaround - maybe someone can try compiling it.

---

### Post by mhenriday on 2008-07-13
> **ronacc said:**
> just for info . both the smhi and olympics site load and work in opera 9.52 64bit , the olympic site loads and works in firefox but not the smhi site , flash loading fails on that one for me . On my 64-bit bit machine, the situation corresponds to that described by **ronacc**, above ; i e, both the **SMHI** and the **Beijing Olympics** site work in **Opera** (**9.51.2061.gcc4.qt3**), but the former fails to load in **Firefox**. Neither in **Opera** or in **Firefox** do I get any sound. The latest update of the non-free flashplayer (**10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124 .0ubuntu2**), which I installed this morning, did not affect the above, nor did it restore sound. The other Swedish sites mentioned in earlier posts work fine, save, of course, that I don't get any sound....

Henri

---

### Post by ronacc on 2008-07-13
@ plun  Yes I have operapluginwraper installed . I'm 64bit if that makes a difference . I had tried the sites first with hardy and opera 9.52  I hadn't migrated intrepid to 9.52 yet so I tried them with intrepid and opera 9.51 and both also worked there .
edit: as mhenriday stated I also get no sound ( I didn't know those pages had sound)

---

### Post by plun on 2008-07-13
> **ronacc said:**
> @ plun  Yes I have operapluginwraper installed . I'm 64bit if that makes a difference . I had tried the sites first with hardy and opera 9.52  I hadn't migrated intrepid to 9.52 yet so I tried them with intrepid and opera 9.51 and both also worked there .
edit: as mhenriday stated I also get no sound ( I didn't know those pages had sound)

Well...  "bless this mess"...:)
[B]
FF3 Nightly build works[/B] and I got good clues within Gentoos forum about Opera...  ronacc was also mentioned with credits ..:KS

---

### Post by psyke83 on 2008-07-13
> **plun said:**
> Well...  "bless this mess"...:)
[B]
FF3 Nightly build works[/B] and I got good clues within Gentoos forum about Opera...  ronacc was also mentioned with credits ..:KS

It would be better to stop commenting here and confirming the [bug]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/247682/") on Launchpad instead. The issue is definitely in Firefox 3.0 and fixed since the 8/7/2008 build. Firefox 2 (and most likely Opera and other browers) is unaffected.

Note that the latest swfdec probably has the same issue in Firefox 3.0 (you can read more about it on the upstream bug).

EDIT: I found an older variant, this is the bug to comment in: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182)

---

### Post by psyke83 on 2008-07-17
A quick update on the Flash situation: the latest nspluginwrapper development build *does* help PulseAudio and Flash v9 to cooperate (when Flash crashes, nspluginwrapper can restart the plugin simply by reloading the page in Firefox).

Unfortunately nspluginwrapper does *not* fix crashes in Flash v10 (in Intrepid), I presume since the bug is actually in Firefox and not Flash. Again, see [bug 239182]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182") for details on that.

If you're running Intrepid with the proper PulseAudio configuration and you're seriously exasperated from Flash issues, you can manually downgrade to Hardy's version of flashplugin-nonfree and use the development build of nspluginwrapper, however. See Part B of my [guide]("http://ubuntuforums.org/showthread.php?t=789578") if you're interested (bear in mind the instructions are for  Hardy, though).

---

### Post by BC7333 on 2008-07-21
Had this problem accessing [www.tivo.com](www.tivo.com) and clicking on support. Was very reproducible.

Used the instructions here and now this site and others mentioned here are ok.

Checked a lot of flash sites, finally found xvideos.com (all in the name of testing of course..) that had some wierd errors and crashed. All kinds of blank windows opened and when I tried to close one FF crashed and disappeared.

Ibex Alpha2

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008071816 Firefox/3.0.1

about:plugins showed Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0.0 d525

Before was Shockwave Flash 10.0.0 525

---

### Post by psyke83 on 2008-07-21
> **BC7333 said:**
> Had this problem accessing [www.tivo.com](www.tivo.com) and clicking on support. Was very reproducible.

Used the instructions here and now this site and others mentioned here are ok.

Checked a lot of flash sites, finally found xvideos.com (all in the name of testing of course..) that had some wierd errors and crashed. All kinds of blank windows opened and when I tried to close one FF crashed and disappeared.

Ibex Alpha2

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008071816 Firefox/3.0.1

about:plugins showed Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0.0 d525

Before was Shockwave Flash 10.0.0 525

Thanks for testing, but as you can see, I edited the first post and commented in this thread to report that nspluinwrapper does *not* help with these crashes using the latest version of Flash. I linked to the appropriate bug report, we simply have to wait for it to get fixed (in Firefox 3.0.2, I guess).

---

### Post by BC7333 on 2008-07-21
> **psyke83 said:**
> Thanks for testing, but as you can see, I edited the first post and commented in this thread to report that nspluinwrapper does *not* help with these crashes using the latest version of Flash. I linked to the appropriate bug report, we simply have to wait for it to get fixed (in Firefox 3.0.2, I guess).

Apologize for not RTFM..

Any undo instructions to get back to initial state, or stay at this state (if update/upgrade) not desired?

---

### Post by psyke83 on 2008-07-21
> **BC7333 said:**
> Apologize for not RTFM..

Any undo instructions to get back to initial state, or stay at this state (if update/upgrade) not desired?

```
$ sudo apt-get remove --purge flashplugin-nonfree nspluginwrapper
$ sudo apt-get install flashplugin-nonfree
```

Again, as I said, we need to wait for a proper fix in Firefox to prevent these crashes.

---

### Post by JJonesey on 2008-08-22
Thank you very much for this solution. I am new to linux and I had been trying to find a solution to this problem since I installed Ubuntu 8.04. This seems to have fixed my problem. Ciao!

C.

---

### Post by JJonesey on 2008-08-22
Thank you very much for this solution. I am new to linux and I had been trying to find a solution to this problem since I installed Ubuntu 8.04. This seems to have fixed my problem. Ciao!

C.

---

### Post by psyke83 on 2008-08-22
> **JJonesey said:**
> Thank you very much for this solution. I am new to linux and I had been trying to find a solution to this problem since I installed Ubuntu 8.04. This seems to have fixed my problem. Ciao!

C.

This thread uses a workaround that's now obsolete. If you're using Hardy, you're better off following these instructions: [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

