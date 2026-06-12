---
title: "Firefox 5 takes all available memory"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by hansmex on 2011-07-22
Hello,

I'm not sure if this is the right (sub)forum, but let me explain my problem.

A few months ago I did a fresh install of Ubuntu 11.04 64-bits. It works perfectly.
I'm using Firefox 5.0, and in *About* it says ***Mozilla Firefox for Ubuntu Canonical 1.0***.

Every now and then, Firefox behaves like a runaway train and starts using up all available memory, and using 100% processor time. This has been going on for a week or so. The only remedy is to kill Firefox and restart it.

I'm not sure what causes this problem, but I am starting to suspect that it may be caused by Flash, Java, or some other plug-in or add-on that I have installed.

My add-ons are:
- Adblock Plus 1.3.9
- Adblock Plus Pop-up addon 0.2.7
- Delicious Bookmarks 2.3.1
- Delicious Extension 2.3.1
- Flash-Aid 2.1.1
- Global Menu Bar Integration 1.0.6
- Memory Restart 1.4
- StumbleUpon 3.91
- Ubuntu Firefox Modifications 0.9.1

With the exception of Memory Restart 1.4 all these add-ons have been installed for a long time, without ever causing any problems. The problems started before installing Memory Restart.

My Java version is IcedTea, installed from the repository. I'm frequently using Sweet Home 3D (a Java program) that runs without any problem. It doesn't make a difference whether I have SH3D running or not, the FF problem occurs regardless.

I also have installed ***Ubuntu restricted extras*** version 43. YouTube videos don't cause problems. Vimeo videos cause problems on occasion when switching to high definition and/or to full screen, but that is a known Vimeo problem.

The problems certainly start when I don't use my computer for a longer period of time. I have disabled the screen saver/energy saver, but that doesn't seem to solve the problem. Today I had the problem shortly after visiting a website, reason why I'm starting to suspect that the problem could be linked to some plug-in that website uses. 

Is there anyone who can help me find out what is going on? What steps can I take to (1) isolate the problem and (2) solve it?
My technical knowledge isn't very good, treat me as a newbie... 

If you need more information, I will be happy to (try and) give it to you.
Any help is appreciated.

Hans

---

### Post by Groggster on 2011-07-22
I have also experienced these problems ever since the update from Firefox 4 to 5, and i am also running a 64-bit system. I believe that this is an Java issue, as i have only experienced this while using Java. However i am also having problems with flash, but with different problems, so it is probably unrelated.

---

### Post by dino99 on 2011-07-22
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by oldsoundguy on 2011-07-22
not using 64 bit .. but check your pre-set tabs. Sometimes they do run amok.  Good example is Facebook.  It pops up with a huge memory leak now and then.

My big issue with FF5 is that after installing it and the newest Thunderbird, have lost the hyper-link capability in the eMail. Been several weeks and a multiple bugzilla reports by me and several others and the issue has yet to be fixed.

---

### Post by lovinglinux on 2011-07-22
The first thing I recommend is to install [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/"), configure it to block Flash and other plugins as well or use NoScript with [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/"). Use Firefox for a while to see if the problem persists. The reason why your memory is building up could be because of unnecessary flash content or bad scripts.

However, most likely that your problem is caused by an extension. I have observed that some extension memory leaks depends on the user habits and web sites visited. For instance I had a memory leak on one of my extensions and whenever I opened a new window instead of a new tab, the extension would trigger it's onload functions increasing the memory leak. The same problem didn't happen if I used only new tabs. I was able to pinpoint the problem while editing my Blogger sites, because Blogger opens every editor in a new window.

So, if it doesn't improve with NoScript, disable all add-ons and use Firefox for a while to see if the problem persists. If not, then enable one add-on and test for a while, enable another add-on and test for a while, until you find the culprit.

Also, when the problem appears, open the System Monitor and check which process is using more memory. Them type *about:memory* in Firefox address bar to identify where the memory is going.

You could also tweak your memory and cache settings. See [http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks](http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks)

About the CPU usage, could be flash, a problematic script on a web site or an add-on. In addition the previous steps, I would also [optimize the profile databases]("http://www.webgapps.org/tutorials/firefox/optimization/database-optimization").

---

### Post by hansmex on 2011-07-23
Lovinglinux,

Here are  the results for the first round:
- I disabled all add-ons except StumbleUpon
- I disabled all plug-ins: DivX webplayer, IcedTea web plug-in, QuickTime, Shockwave Flash, VLC multimedia, Windows mediaplayer plug-in.

I left the PC alone for an hour, and when I came back, Firefox was taking up 1.8 GB of memory and using 100% of one of two processors. It was not responsive anymore, so I had to kill the process.

So, if plug-ins and extensions aren't the problem, what is?
Any help would be greatly appreciated.

Hans

---

### Post by lovinglinux on 2011-07-23
> **hansmex said:**
> Lovinglinux,

Here are  the results for the first round:
- I disabled all add-ons except StumbleUpon
- I disabled all plug-ins: DivX webplayer, IcedTea web plug-in, QuickTime, Shockwave Flash, VLC multimedia, Windows mediaplayer plug-in.

I left the PC alone for an hour, and when I came back, Firefox was taking up 1.8 GB of memory and using 100% of one of two processors. It was not responsive anymore, so I had to kill the process.

So, if plug-ins and extensions aren't the problem, what is?
Any help would be greatly appreciated.

Hans

When you left the PC alone, how many tabs were open?  Which process was using memory and CPU?

Disable StumbleUpon as well.

---

### Post by hansmex on 2011-07-23
LovingLinux,

As I wrote: [I][B]Firefox was taking up 1.8 GB of memory and using 100% of one of two processors
[/B][/I]As a process, that's called[I][B] firefox-bin.
[/B][/I]
New suspect: the new Google thingies...

Do you want a screen shot of the System Monitor?

Hans

---

### Post by lovinglinux on 2011-07-23
> **hansmex said:**
> LovingLinux,

As I wrote: [I][B]Firefox was taking up 1.8 GB of memory and using 100% of one of two processors
[/B][/I]As a process, that's called[I][B] firefox-bin.
[/B][/I]
New suspect: the new Google thingies...

Do you want a screen shot of the System Monitor?

Hans

No need for a screenshot. Can you confirm the problem happens with some Google services opened?

---

### Post by hansmex on 2011-07-29
I think I know what is causing the memory leak.

During the entire period I had TWO windows open, each with 3-6 tabs. Two days ago, I closed one window, and the memory leak hasn't occurred since.

So, my guess is, that the problem lies with how FF5 handles two (or more?) windows open at the same time.

Hans

---

### Post by schnurrbidurr on 2011-08-08
Has there been a fix yet? I encounter the same problem with firefox-bin taking upalmost all memory and becoming unresponsive. I'm running 32bit btw.

Is it safe to downgrade FF?
thanks.

---

