---
title: "Banshee 1.5.0 released!"
date: 2009-06-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-06-02
Banshee 1.5.0 (aka 1.6 beta 1) is a beta release with tons of new features and fixes. It is the result of six months work by more than 30 people.

[http://banshee-project.org/download/archives/1.5.0/](http://banshee-project.org/download/archives/1.5.0/)

This should really replace Rhythmbox in Karmic :)

---

### Post by jmmL on 2009-06-02
Wow; that looks really good! Unfortunately the PPA for banshee unstable is pretty much dormant: [https://launchpad.net/~banshee-unstable-team/+archive/ppa77]("https://launchpad.net/%7Ebanshee-unstable-team/+archive/ppa")

EDIT: Just found this: [https://edge.launchpad.net/~banshee-team/+archive/banshee-daily](https://edge.launchpad.net/~banshee-team/+archive/banshee-daily)

---

### Post by Incognito-Here on 2009-06-02
Does it know something about inotify?
// Too slow, give this crap up.

---

### Post by kostkon on 2009-06-02
Still no folder watching :(

---

### Post by MaX on 2009-06-02
> **kostkon said:**
> Still no folder watching :(

LOL, this is the most requested feature I've seen on these forums, and it's the thing that keep me from using it at all..

Hopefully the BPM stuff doesn't overwrite the BPM value if there already exists one...

---

### Post by Gourgi on 2009-06-02
importing 25.000 tracks now in banshee 1.5 -> memory usage 1.4 GB.
[[IMG]http://img190.imageshack.us/img190/3314/bansheemem.th.jpg[/IMG]](http://img190.imageshack.us/my.php?image=bansheemem.jpg)

i guess it is normal , the tracks are too many.
i'll test again in normal use after import is done and i'll post back.
> **kostkon said:**
> Still no folder watching :(

soon hopefully
[http://bugzilla.gnome.org/show_bug.cgi?id=385965](http://bugzilla.gnome.org/show_bug.cgi?id=385965)

---

### Post by olskar on 2009-06-02
> **Gourgi said:**
> 


soon hopefully
[http://bugzilla.gnome.org/show_bug.cgi?id=385965](http://bugzilla.gnome.org/show_bug.cgi?id=385965)


Indeed, the patch seems ok :) I think we will have this in 1.60 or earlier.

---

### Post by Incognito-Here on 2009-06-02
Do everything you want, but don't propose this bloatware as default.

---

### Post by davideotape on 2009-06-02
Switched from rythmbox yesterday. Very impressed. Can't remember why I didn't like rythmbox, but banshee works fine for me. Using 32.1 MB of RAM for me whilst playing, which is not a problem with 2GB and only ~700MB being used.

---

### Post by zekopeko on 2009-06-02
> **Incognito-Here said:**
> Do everything you want, but don't propose this bloatware as default.

why is it "bloatware"?

---

### Post by zekopeko on 2009-06-02
i would love a windows build. there isn't a single good windows audio player out there.

---

### Post by zekopeko on 2009-06-02
> **Gourgi said:**
> importing 25.000 tracks now in banshee 1.5 -> memory usage 1.4 GB.
[[IMG]http://img190.imageshack.us/img190/3314/bansheemem.th.jpg[/IMG]](http://img190.imageshack.us/my.php?image=bansheemem.jpg)

i guess it is normal , the tracks are too many.
i'll test again in normal use after import is done and i'll post back.


soon hopefully
[http://bugzilla.gnome.org/show_bug.cgi?id=385965](http://bugzilla.gnome.org/show_bug.cgi?id=385965)

that amount of memory usage isn't normal. file a bug and give as much info as possible.

---

### Post by ghindo on 2009-06-02
I'm still waiting for Banshee to actively watch directories for changes and cut down on memory usage before I'm ready to replace Rhythmbox.> **zekopeko said:**
> i would love a windows build. there isn't a single good windows audio player out there.foobar2000!

---

### Post by olskar on 2009-06-02
> **Incognito-Here said:**
> Do everything you want, but don't propose this bloatware as default.

I don't know what you mean with bloatware exactly but at least it takes up less space than Rhythmbox, if that is what you mean?

[http://www2.apebox.org/wordpress/rants/74/](http://www2.apebox.org/wordpress/rants/74/)

---

### Post by Incognito-Here on 2009-06-02
It depends on the library. Big library takes more memory for rhythmbox,it keeps all metadata in the memory. Banshee uses this crappy sqlite, so it doesn't keep all the data in the memory, but this makes it slow. Just try to list tracks. The difference is very significant on my i7 with 8Gb of memory. I call every sloware as "bloatware" ;)

---

### Post by gnomeuser on 2009-06-02
> **MaX said:**
> LOL, this is the most requested feature I've seen on these forums, and it's the thing that keep me from using it at all..


It's being handled by a plugin, it currently does not work with git master but is being worked on by it's developer. 

Personally I always saw directly invoking inotify as a misfeature and would much rather use Xesam to query an indexer that fills out my database with new entries. At any rate it is hardly a feature that is so vital as to render every improvement Banshee presents over other players null.

---

### Post by Gourgi on 2009-06-02
> **zekopeko said:**
> that amount of memory usage isn't normal. file a bug and give as much info as possible.

what amount of memory usage would be normal for my 25k collection ?

also i would be happy to file a bug report but what info exactly should i fill in ?

banshee --debug is enough?
any memory specific metrics? screenshots?

---

### Post by zekopeko on 2009-06-02
> **Gourgi said:**
> what amount of memory usage would be normal for my 25k collection ?

also i would be happy to file a bug report but what info exactly should i fill in ?

banshee --debug is enough?
any memory specific metrics? screenshots?

1. about the memory: i don't know what is appropriate but 1.4GB isn't. i have a 5k library and i don't remember such a big chunk of ram was used when indexing my library. i think that the biggest banshee usage i have seen was around 100mb on my pc.

2. provide the version of banshee, your system + OS, and the output of banshee --debug from terminal. i would also suggest that you hop on IRC and ask banshee devs if they need anything else.

EDIT: i just realized. perhaps it isn't a bug. perhaps it was only using your memory since it's far faster then disk access and you had a lot of free RAM. but do still file the bug.

---

### Post by davideotape on 2009-06-02
> **Incognito-Here said:**
> It depends on the library. Big library takes more memory for rhythmbox,it keeps all metadata in the memory. Banshee uses this crappy sqlite, so it doesn't keep all the data in the memory, but this makes it slow. Just try to list tracks. The difference is very significant on my i7 with 8Gb of memory. I call every sloware as "bloatware" ;)

What kind of differences do you notice? I can't imagine anything being slow on that rig (unless you've got a rubbish hard drive)

---

### Post by cleentrax on 2009-06-02
Banshee is slowly gaining my respect. I've been vacillating between Amarok 1.4 and Listen (hate Amarok 2). Glad to see so many improvements, but I'm waiting for two things (other than folder watching, which so many already mentioned): 

1. Smart playlists based on Last.fm recommendations especially in combination with audio thumbprints (as in Mirage plugin)
2. Browsing by genre

---

### Post by zekopeko on 2009-06-02
> **cleentrax said:**
> Banshee is slowly gaining my respect. I've been vacillating between Amarok 1.4 and Listen (hate Amarok 2). Glad to see so many improvements, but I'm waiting for two things (other than folder watching, which so many already mentioned): 

1. Smart playlists based on Last.fm recommendations especially in combination with audio thumbprints (as in Mirage plugin)
2. Browsing by genre

number 1. would rock! it would be like genius in itunes. even better.

---

### Post by Incognito-Here on 2009-06-02
> What kind of differences do you notice? I can't imagine anything being slow on that rig (unless you've got a rubbish hard drive)
raid of two samsung f1 1Gb, both about 100Mb per second. After this one other systems seem very slow. So, don't deceive yourself: banshee is very slow. Mono apps are always slow. Even C++-ish Gnote is clearly faster than tomboy. See at this stupid f-spot, how slow it is.

---

### Post by zekopeko on 2009-06-02
> **Incognito-Here said:**
> raid of two samsung f1 1Gb, both about 100Mb per second. After this one other systems seem very slow. So, don't deceive yourself: banshee is very slow. Mono apps are always slow. Even C++-ish Gnote is clearly faster than tomboy. See at this stupid f-spot, how slow it is.

mono troll. i have a slower system and banshee preforms quite nicely. even on my netbook that's using x86 ubuntu and not the netbook remix that is optimized.

---

### Post by Bios Element on 2009-06-02
> **zekopeko said:**
> mono troll. i have a slower system and banshee preforms quite nicely. even on my netbook that's using x86 ubuntu and not the netbook remix that is optimized.

+1 Banshee has always been fast. SQLite isn't slow. Here's something I doubt you know, Firefox uses SQLite. Nice try, but your FUD doesn't hold water.

---

### Post by Incognito-Here on 2009-06-02
I'm not a mono troll, I'm C# developer. The last means I know advantages and disadvantages of this language. So I don't recommend anyone to write desktop apps with this technology, both .NET or mono.

---

### Post by Incognito-Here on 2009-06-02
> Firefox uses SQLite
Thats why it's so slow on linux systems. Try how quick Chromeum find items in its history, and how slow firefox does. Things will change with kernel 2.6.30, but it's too slow know.

---

### Post by Bios Element on 2009-06-02
> **Incognito-Here said:**
> Thats why it's so slow on linux systems. Try how quick Chromeum find items in its history, and how slow firefox does. Things will change with kernel 2.6.30, but it's too slow know.

Slow? It is? Wow. I wonder why I've never noticed...Oh wait, that's right. Because it isn't! Many people are having problems with FF Speed, many are not. But case in point, FF was designed for windows foremost and thus Linux dev is somewhat lacking.

Good for you, Don't recommend it. And while your at it, Don't flame those who do.

EDIT: BTW, History searches with FF are instant. As in, no delay whatsoever.

---

### Post by Incognito-Here on 2009-06-02
upd
Hm, things has changed since version 1.4.0 (I tried 1.4.3) - the scroll become much better. Or the difference was in JFS I've used that time.
But the difference may depend on the fact I've tested on fresh sqlite base, things can change on older base.

---

### Post by lucazade on 2009-06-02
From Incognito-Here profile:

"Interests
    Trolling"

---

### Post by zekopeko on 2009-06-02
> **Incognito-Here said:**
> Thats why it's so slow on linux systems. Try how quick Chromeum find items in its history, and how slow firefox does. Things will change with kernel 2.6.30, but it's too slow know.

it's true that FF is slow on some systems and it's due to the way the linux kernel does writing to the filesystem. this will hopefully be fixed in 2.6.30+ kernels.

the main problem of FF is that it renders html content and the UI in the same thread. there is a project to make this like chrome does it, one UI thread and per-tab/site thread for content.

i found somewhere a line that you can put in the address bar and it will open a tab with FF inside it! pretty cool. this is because firefox UI is just an XML file that you can edit. this also gives it great extension support.

---

### Post by davideotape on 2009-06-02
1. Banshee is not slow for me at all. Full stop. Playlist generation is almost instant, and loading times are not noticably slow or fast.

2. Firefox history search takes me less than half a second. But, I presume that is really slow isn't it? I'm sorry but just because you are a C# developer does not mean you know everything. Ubuntu is designed for everyday users like the majority of posters here, and it all works very well on our comparatively low end systems thank you very much.

EDIT: I'd just like to say I also use BOINC 24/7. And banshee still runs fine.

---

### Post by zekopeko on 2009-06-02
> **Incognito-Here said:**
> I'm not a mono troll, I'm C# developer. The last means I know advantages and disadvantages of this language. So I don't recommend anyone to write desktop apps with this technology, both .NET or mono.

then as a developer you should know that there is a language for every use-case scenario. mono/.NET are good for somethings and C/C++ are good for others. i wouldn't develop a program that requires fast computations in python now would i? but i might want to develop a GUI for that in python and leave the heavy number crunching to the C library underneath.

---

### Post by directhex on 2009-06-02
The "slow" issue.

Rhythmbox does not scale. The reason it does not scale is that for every track in your library, a ListStore entry is created for the track - every track causes that object to grow, and for huge libraries, we're talking a LOT of memory.

Banshee works around this issue through a very clever custom widget (written in C#) which only ever contains as many tracks as you see on the screen, plus 10 in either direction. When you scroll, the custom list is throwing away and repopulating its mini-list, a "viewport" if you will, of your total library. As a result, there is no RB-style bloating with library size due to the list object.

However, the trade off is that the constant refreshing of the object uses more CPU time. That's the trade-off.

---

### Post by SKLP on 2009-06-02
I'm sure the inotify feature will get added, although I don't really see the point to it.
If I were to use the watch feature on my music folder, and add tracks to it from Nautilus or whatever, then sure it would get added to my library, but the file path/name would not be organized by the id3 tag (at least I don't remember RB doing that for me).
So frankly, Banshee ( this is the same behaviour as iTunes, I believe)'s "copy to music library when importing" feature, combined with me adding the songs through the application instead of through nautilus, will make sure my collection (folder structure) is organized (i.e. consistent with ID3 tags) (which is one of the reasons Banshee > RB,  IMO).

As for the Banshee "bloat" issue, it is true that Banshee scales better with large collections though I do believe RB might be a bit lower in memory usage with tiny libraries.
The people mentioning banshee taking several hundred MB have probably just run into some bug, also it's possible memory usage is that high when importing music, but not otherwise.

IMO, Banshee has clearly been better overall since all the 1.x releases, so I do hope Ubuntu will finally move to it as default.

---

### Post by SKLP on 2009-06-02
> **Incognito-Here said:**
> Even C++-ish Gnote is clearly faster than tomboy.
You, sir, are wrong ;-)

It is not *CLEARLY* faster than tomboy. Tomboy is such an app that could be written in language like Python (languages which are orders of magnitudes slower than C# or C++) without people noticing a difference in performance.
Tomboy should have a slightly longer start-up time though, since it's JITed (although this could be helped a bit by AOTing the Tomboy assemblies, if one cares about startup speed that much)

---

### Post by olskar on 2009-06-02
> **SKLP said:**
> I'm sure the inotify feature will get added, although I don't really see the point to it.
If I were to use the watch feature on my music folder, and add tracks to it from Nautilus or whatever, then sure it would get added to my library, but the file path/name would not be organized by the id3 tag (at least I don't remember RB doing that for me)..

I think that is exactly what RB does. If it were not doing that there would be no poinf of having such a feature.

---

### Post by Gourgi on 2009-06-02
> **zekopeko said:**
> 1. about the memory: i don't know what is appropriate but 1.4GB isn't. i have a 5k library and i don't remember such a big chunk of ram was used when indexing my library. i think that the biggest banshee usage i have seen was around 100mb on my pc.

2. provide the version of banshee, your system + OS, and the output of banshee --debug from terminal. i would also suggest that you hop on IRC and ask banshee devs if they need anything else.

EDIT: i just realized. perhaps it isn't a bug. perhaps it was only using your memory since it's far faster then disk access and you had a lot of free RAM. but do still file the bug.

i'm using the daily build from banshee's ppa
so maybe this is a bug , maybe not.
i'll wait a day or 2 and see how banshee deals with my machine's memory and if the bug goes away by another update.
for now my collention was imported, i disabled the bpm plugin, but banshee still eats 1.4GB ram.
in case anyone wants to try here is the ppa for karmic
[https://edge.launchpad.net/~banshee-team/+archive/banshee-daily](https://edge.launchpad.net/~banshee-team/+archive/banshee-daily)

---

### Post by froggyswamp on 2009-06-02
> **SKLP said:**
> 
 It is not *CLEARLY* faster than tomboy.

Give me a break, startup alone is worth switching. There's lots of fantasy around JIT since Java was born yet every jit fan tries to disregard the obvious hurdles, here's a C# fanboy actually giving in:
> 
Per*haps the most ob*vi*ous change for the over*all IDE is that the main UI is now done en*tire*ly in WPF. It sound*ed like a de*cent plan at first but I’m not too happy with it now. Minor dif*fer*ences from the way na*tive con*trols be*have can be pret*ty an*noy*ing, and the five to twen*ty sec*ond load time makes it less use*ful for open*ing ran*dom .cpp files, when 2008 would load them in one or two sec*onds.
[http://int64.org](http://int64.org)

---

### Post by bofphile on 2009-06-02
I'm still waiting for gapless playback. Any idea if it will be implemented soon ? That's one the main reason I'm still using rhythmbox.

---

### Post by Gourgi on 2009-06-02
> **bofphile said:**
> I'm still waiting for gapless playback. Any idea if it will be implemented soon ? That's one the main reason I'm still using rhythmbox.

it seems that a patch is around
[http://bugzilla.gnome.org/show_bug.cgi?id=440952](http://bugzilla.gnome.org/show_bug.cgi?id=440952)
so hopefully will see it soon

cheers to RAOF  :popcorn:

---

### Post by tad1073 on 2009-06-02
disregard this post

---

### Post by kk0sse54 on 2009-06-02
Fantastic so far for me, fixed pretty much the majority of bugs that I've been facing with banshee and is the first release that is actually usable for me. Great job, definitely has become one of the best media players in linux.

---

### Post by tad1073 on 2009-06-02
I couldn't get it to configure, here is the log file.

---

### Post by Incognito-Here on 2009-06-03
> It is not *CLEARLY* faster than tomboy.
It is. Just try to open Preferences, Search All Notes.
Gnote response instantly, tomboy *CLEARLY* needs some short time. It's almost nothing, but the difference is seen. In addition, gnote eat 11.2Mb of memory, while tomboy took around 40Mb. So, tomboy is the first candidate to replace to, gnote is the more appropriate alternative (clone).

---

### Post by psyke83 on 2009-06-03
> **Incognito-Here said:**
> It is. Just try to open Preferences, Search All Notes.
Gnote response instantly, tomboy *CLEARLY* needs some short time. It's almost nothing, but the difference is seen. In addition, gnote eat 11.2Mb of memory, while tomboy took around 40Mb. So, tomboy is the first candidate to replace to, gnote is the more appropriate alternative (clone).

While personally I'd prefer Tomboy to be removed, there are other things to take into consideration.

Tomboy is not the only Mono app installed by default (F-Spot), so you cannot remove the associated Mono dependencies until F-Spot is replaced as well.

Gnote also has the following dependencies, which add up to 2316KB:
```
libboost-filesystem1.38.0 libboost-regex1.38.0 libboost-system1.38.0 libgconfmm-2.6-1c2 libgnomemm-2.6-1c2 libpanelappletmm-2.6-1c2
```

To those who say that Tomboy's load time is not "clearly" slower than Gnote, I suggest you boot your PC with constrained memory via the mem=xxxMB paramater in order to understand the annoyance that users with older hardware face; limiting even to 768MB will cause Mono apps to impact considerably on performance/swap usage on a system with few applications running.

---

### Post by Incognito-Here on 2009-06-03
Yeah, I know. We cannot replace f-spot yet, there are no gtk suitable replacements, but f-spot is a piece of crap too.

---

### Post by Incognito-Here on 2009-06-03
> magnitudes slower than C# or C++
don't mess these two languages. C# is a higher order one, and it's performance in general worse by a degree (in real life "degree" means 2 or more times).

---

### Post by Incognito-Here on 2009-06-03
> **zekopeko said:**
> then as a developer you should know that there is a language for every use-case scenario. mono/.NET are good for somethings and C/C++ are good for others. i wouldn't develop a program that requires fast computations in python now would i? but i might want to develop a GUI for that in python and leave the heavy number crunching to the C library underneath.
So don't use .NET or mono apps at desktop, their startup time is just horrible, that's the most important thing, as well as they have performance issues on some critical tasks.

---

### Post by gnomeuser on 2009-06-03
> **bofphile said:**
> I'm still waiting for gapless playback. Any idea if it will be implemented soon ? That's one the main reason I'm still using rhythmbox.

The reason this is lacking is largely that we need playbin2 in gstreamer to be really solid. What rhythmbox does to get the same functionality is some what a hack and has as such been fairly unsupportable and a leading cause of crashes. 

I would imagine this isn't far behind, hopefully we can manage by 1.6.x if the gstreamer people can recommend application developers using playbin2 but such a time.

---

### Post by directhex on 2009-06-03
> **Incognito-Here said:**
> don't mess these two languages. C# is a higher order one, and it's performance in general worse by a degree (in real life "degree" means 2 or more times).

Whilst in benchmarks, Python is up to 60 times slower than C#. So... yeah. There's orders of magnitude, then there's orders of magnitude.

---

### Post by directhex on 2009-06-03
> **Incognito-Here said:**
> So don't use .NET or mono apps at desktop, their startup time is just horrible, that's the most important thing, as well as they have performance issues on some critical tasks.

Sorry, but complaining about app bloat and startup time on old PCs without mentioning OOo is mad. Or Evolution. Many of an Ubuntu system's default apps are huge, bloated, and clunky - and they manage that without going anywhere near any C# or JITter. Evolution being C, and OOo being C++.

If you have an old, memory-constrained or CPU-constrained device, you use Xubuntu. This isn't news.

---

### Post by SKLP on 2009-06-03
> **psyke83 said:**
> While personally I'd prefer Tomboy to be removed, there are other things to take into consideration.

Tomboy is not the only Mono app installed by default (F-Spot), so you cannot remove the associated Mono dependencies until F-Spot is replaced as well.

Gnote also has the following dependencies, which add up to 2316KB:
```
libboost-filesystem1.38.0 libboost-regex1.38.0 libboost-system1.38.0 libgconfmm-2.6-1c2 libgnomemm-2.6-1c2 libpanelappletmm-2.6-1c2
```

To those who say that Tomboy's load time is not "clearly" slower than Gnote, I suggest you boot your PC with constrained memory via the mem=xxxMB paramater in order to understand the annoyance that users with older hardware face; limiting even to 768MB will cause Mono apps to impact considerably on performance/swap usage on a system with few applications running.Obviously if an application takes up slightly more memory(RAM) and your RAM size is pretty low the swapping will increase, possibly reducing the application performance a bit. This is not something I've noticed though (slowness in tomboy) at all. 

I don't believe Tomboy nor F-Spot is going to be removed, luckily ;-)
Also the ancient RB player will also likely be replaced by the modern banshee :)
In my opinion, ram usage is not the main issue, things which seem more important are Programmer productivity( this one, I believe is great in Mono compared C++/Boost or C/GLib), Speed (i.e. cpu usage of an app for doing x), also it's important to be able to fit alot into the LiveCD. Since mono apps (and I suppose higher level apps in general) have smaller "binaries" (byte code or whatever), It would be nice if we had more and more higher level apps, and less native apps.

Also space could (in the long term) be saved by using IKVM as the default JVM, IronPython/IronRuby as default Python and Ruby implementations, and so on.
This would also help language integration alot as all those languages could "call" each other without any manually created bindings... Just plain awesome :) Also it saves work by allowing all the languages to share a single GC, JIT and so on, and all the dynamic languages sharing code through the DLR (call site caching etc)

(To the Mono haters: just try to imagine the same situation using another VM, which were hypotetically not based on any standard, but created by "LINUX" people themselves. Then you could maybe see Mono for what it is, namely a nice piece of code that could allow nice cross-language integration and increase developer productivity, and not just blame it for being MS stuff or whatever)

---

### Post by puccaso on 2009-06-03
still no friqqn[SIZE=6] "play by genre"[/SIZE]
useless..

this is just a pretty mplayer as far as i'm concerned...

---

### Post by directhex on 2009-06-03
> **puccaso said:**
> still no friqqn[SIZE=6] "play by genre"[/SIZE]
useless..

As a pane in the library browser, you mean?

---

### Post by cdEWoozy on 2009-06-03
> **puccaso said:**
> still no friqqn[SIZE=6] "play by genre"[/SIZE]
useless..

You can create smart playlists that filter by genre. Right-click on "Music Library", select "New Smart Playlist" and create a filter that matches your desired genre.

---

### Post by Incognito-Here on 2009-06-03
> **tad1073 said:**
> I couldn't get it to configure, here is the log file.

> **cdEWoozy said:**
> You can create smart playlists that filter by genre. Right-click on "Music Library", select "New Smart Playlist" and create a filter that matches your desired genre.

Lol, it's like "how to scratch an ear with a foot"

---

### Post by Incognito-Here on 2009-06-03
> **SKLP said:**
> Obviously if an application takes up slightly more memory(RAM) and your RAM size is pretty low the swapping will increase, possibly reducing the application performance a bit. This is not something I've noticed though (slowness in tomboy) at all. 

I don't believe Tomboy nor F-Spot is going to be removed, luckily ;-)
Also the ancient RB player will also likely be replaced by the modern banshee :)
In my opinion, ram usage is not the main issue, things which seem more important are Programmer productivity( this one, I believe is great in Mono compared C++/Boost or C/GLib), Speed (i.e. cpu usage of an app for doing x), also it's important to be able to fit alot into the LiveCD. Since mono apps (and I suppose higher level apps in general) have smaller "binaries" (byte code or whatever), It would be nice if we had more and more higher level apps, and less native apps.

Also space could (in the long term) be saved by using IKVM as the default JVM, IronPython/IronRuby as default Python and Ruby implementations, and so on.
This would also help language integration alot as all those languages could "call" each other without any manually created bindings... Just plain awesome :) Also it saves work by allowing all the languages to share a single GC, JIT and so on, and all the dynamic languages sharing code through the DLR (call site caching etc)

(To the Mono haters: just try to imagine the same situation using another VM, which were hypotetically not based on any standard, but created by "LINUX" people themselves. Then you could maybe see Mono for what it is, namely a nice piece of code that could allow nice cross-language integration and increase developer productivity, and not just blame it for being MS stuff or whatever)

Let's you will use this crap yourself with your windows ;)

---

### Post by Incognito-Here on 2009-06-03
> **directhex said:**
> Sorry, but complaining about app bloat and startup time on old PCs without mentioning OOo is mad. Or Evolution. Many of an Ubuntu system's default apps are huge, bloated, and clunky - and they manage that without going anywhere near any C# or JITter. Evolution being C, and OOo being C++.

If you have an old, memory-constrained or CPU-constrained device, you use Xubuntu. This isn't news.
Lol. Evolution is a piece of crap, I know. Inconvenient, slow, buggy. I wish they will get rid of them.
OO is a piece of crap too. I've never used it for serious purposes, as well as any wysiwyg editor (i'm Latex user). But it launched first time faster than tomboy ;)

---

### Post by Incognito-Here on 2009-06-03
Python is a bad choice too. It's good for extremely rapid development for unix platforms (c# sucks here), but doesn't suit for user apps, it takes to much time to start up too.

---

### Post by directhex on 2009-06-03
> **Incognito-Here said:**
> Let's you will use this crap yourself with your windows ;)

That's not a sentence.

---

### Post by tad1073 on 2009-06-03
I asked for help not an opinion, but just to appease you oh mighty Linux master here is the config.log file in .odt format archived as .tar.gz

> **Incognito-Here said:**
> You noble don please never use "doc" format again at the linux forum. But it's told everything about you already: use your windows.

---

### Post by super.rad on 2009-06-03
Never noticed abnormal ram usage on banshee before but mirage is rescanning my libary (11,000 songs) and is really slow, also noticed it's now using 36% cpu and 417mb ram

---

### Post by davideotape on 2009-06-03
> **super.rad said:**
> Never noticed abnormal ram usage on banshee before but mirage is rescanning my libary (11,000 songs) and is really slow, also noticed it's now using 36% cpu and 417mb ram

Hmm, same happened to me whilst using mirage (though to a lesser extent becasue I've only got a 6.4GB library) I do like mirage though. Very nifty...

---

### Post by super.rad on 2009-06-03
It crashed on me before mirage could finish, not bothering to try and scan it all again as it takes so long, ram usage is down to 60mb now mirage isn't scanning

---

### Post by directhex on 2009-06-03
Mirage is a system hog, no doubt there. But the work it needs to do is nasty, nasty work (I did my degree third-year project on a similar topic, and my app was 100% cpu for ~realtime)

---

### Post by directhex on 2009-06-03
> **tad1073 said:**
> I asked for help not an opinion, but just to appease you oh mighty Linux master here is the config.log file in .odt format archived as .tar.gz

Ehm... I think the point is that the actual log is what's useful. logs can be scanned through with tools like grep. Office document copy/paste is rather less useful

Did you run "apt-get build-dep banshee" to install all the packages required to compile Banshee?

---

### Post by Incognito-Here on 2009-06-03
Lol, and you suggest this bugware to be default?

---

### Post by jmmL on 2009-06-03
> **Incognito-Here said:**
> I said you don't switch sometimes into GNU/Linux for a 30 minutes per day, and keep using your lovely windows all the time kid.
// logs are usually stored as plain text, brainless.

Give it a rest; you're not being terribly constructive.

---

### Post by zekopeko on 2009-06-03
> **Incognito-Here said:**
> I said you don't switch sometimes into GNU/Linux for a 30 minutes per day, and keep using your lovely windows all the time kid.
// logs are usually stored as plain text, brainless.

you are being extremely rude. if you don't like ubuntu's choice of a default music player i suggest that you find yourself another distro. there are 100s of them out there and most don't have banshee as the default player.

and stop bashing mono. there are numerous threads in the community cafe/reoccurring threads sub-forums to yell your FUD there.

and calling somebody brainless just because they don't know in which format to provide the logs is the same as me telling you that you are brainless beacuse you can't produce one mildly grammatically and syntactically correct English sentence. and i you continue i'm gonna report you to the moderators (if somebody already didn't)

---

### Post by directhex on 2009-06-03
> **Incognito-Here said:**
> Haha, I like rhythmbox, but don't like when daydreamers like you want to replace it with this buggy and slow banshee ;)

Name the bug numbers for the specific bugs in the upstream Bugzilla which affect you and you feel should be blockers, please.

Because if you can't cite any, then you're not being even remotely constructive - you're simply heckling.

---

### Post by davideotape on 2009-06-03
> **Incognito-Here said:**
> Haha, I like rhythmbox, but don't like when daydreamers like you want to replace it with this buggy and slow banshee ;)

If you like rythmbox, use it. No ones stopping you. And please stop being so offensive. These forums are meant to be a place where beginners can post for help, where people can voice their opinion, and where constuctive discussions can take place. There is no need to alienate people just because they uploaded a .doc. Can you not just copy and paste the text into a text editor, save a local copy, and kindly ask the user to post .txt files in the future?

---

### Post by ranch hand on 2009-06-03
Let us lern to play nicely children.

---

### Post by tad1073 on 2009-06-03
> **directhex said:**
> Ehm... I think the point is that the actual log is what's useful. logs can be scanned through with tools like grep. Office document copy/paste is rather less useful

Did you run "apt-get build-dep banshee" to install all the packages required to compile Banshee?

I found the last part of his post offensive, but sorry, I wasn't thinking when uploading the cofig.log file. The file was too large to upload by it-self and I forgot about compressing until it was too late.

I just ran apt-get build-dep banshee and how do I scan the log file with grep?

I got it built though.

```
grep ~/Desktop/banshee-1-1.5.0/config.log
```

---

### Post by davideotape on 2009-06-03
> **tad1073 said:**
> I just ran apt-get build-dep banshee and how do I scan the log file with grep?

```
grep ~/Desktop/banshee-1-1.5.0/config.log
```

Depends what you're looking for. Here's a simple guide: [http://en.wikipedia.org/wiki/Grep#Usage](http://en.wikipedia.org/wiki/Grep#Usage)

---

### Post by Bios Element on 2009-06-03
> **Incognito-Here said:**
> So my I opinion is: amateurish stuff on mono must be abandoned. Use Vala (preferred), C, C++, may be D (but not sure) for desktop applications. Other languages bring too much unneeded layers.

Where in the title of this thread does it say "Let's debate programming languages"?

---

### Post by directhex on 2009-06-03
> **tad1073 said:**
> I got it built though.

Good good. Presumably you were missing some build-dependencies then.

---

### Post by 23meg on 2009-06-03
Closed temporarily for tempers to settle. Please keep it civil and on topic.

---

### Post by ricsi-pontaz on 2009-06-10
I tried this new version and I think it's more better than the earlier releases. A lot of bugs fixed, now need a little bit more optimization (memory usage) and I am 100% happy with it. ;)

---

### Post by zekopeko on 2009-06-10
> **ricsi-pontaz said:**
> I tried this new version and I think it's more better than the earlier releases. A lot of bugs fixed, now need a little bit more optimization (memory usage) and I am 100% happy with it. ;)

how much is it using compared to rhythmbox on your machine?
and what is the size of your library?

---

### Post by frodon on 2009-06-10
Ok, i jailed the 3 last off topic posts.

To those interested by mono dicsussions, here is an appropriate thread to post your opinion :
[http://ubuntuforums.org/showthread.php?t=293623](http://ubuntuforums.org/showthread.php?t=293623)

Please keep this thread on topic or it will be closed for good.

---

### Post by zekopeko on 2009-06-10
> **frodon said:**
> Ok, i jailed the 3 last off topic posts.

To those interested by mono dicsussions, here is an appropriate thread to post your opinion :
[http://ubuntuforums.org/showthread.php?t=293623](http://ubuntuforums.org/showthread.php?t=293623)

Please keep this thread on topic or it will be closed for good.

thank you.

---

### Post by meho_r on 2009-06-10
> **puccaso said:**
> still no friqqn[SIZE=6] "play by genre"[/SIZE]
useless..

this is just a pretty mplayer as far as i'm concerned...

One word: gmusicbrowser.

After disaster with Amarok 2.1, I think I'll give Banshee a go. Reading about it I stumbled upon beforementioned gmusicbrowser which looks as the most powerfull (or feature-full) player I've seen till this very moment. In fact, too many options I would say :) We'll see...

---

### Post by waspbr on 2009-06-10
I would like to see banshee have more extensions, much like songbird. So far I use two players, songbird for my lossy library and banshee for my Flac library. 

Songbird however can monitor my library folder also since I dont turn off my computer (its also very silent) I like to use it as a wake up alarm... So far I can only use songbird for that... 

tho I like banshee a lot, for some odd reason it is my favourite player.


go figure

---

### Post by directhex on 2009-06-10
> **waspbr said:**
> I would like to see banshee have more extensions, much like songbird. So far I use two players, songbird for my lossy library and banshee for my Flac library. 

Songbird however can monitor my library folder also since I dont turn off my computer (its also very silent) I like to use it as a wake up alarm... So far I can only use songbird for that... 

tho I like banshee a lot, for some odd reason it is my favourite player.


go figure

There's an alarm extension awaiting upload to Debian

---

### Post by waspbr on 2009-06-11
lol, cool monkey island avatar, thx for the tip

---

### Post by ad_267 on 2009-06-11
I had to switch from Banshee back to Rhythmbox due to annoying static in some songs. I had hoped 1.5 might have fixed this but it hasn't. Running Banshee 1.4 on Kubuntu 9.10 I don't have this problem though.

One thing I really don't like about Banshee though is the silly keyboard shortcuts and the inability to jump to a song in the list by typing the first letters of the artist/album/song name ([http://bugzilla.gnome.org/show_bug.cgi?id=399655](http://bugzilla.gnome.org/show_bug.cgi?id=399655)).

---

### Post by Incognito-Here on 2009-06-11
> One thing I really don't like about Banshee though is the silly keyboard shortcuts and the inability to jump to a song in the list by typing the first letters of the artist/album/song name ([http://bugzilla.gnome.org/show_bug.cgi?id=399655](http://bugzilla.gnome.org/show_bug.cgi?id=399655)).
Impossible by design, it's because of their list, which only keeps +10 and -10 songs from visible ones.

---

### Post by directhex on 2009-06-11
> **Incognito-Here said:**
> Impossible by design, it's because of their list, which only keeps +10 and -10 songs from visible ones.

Not at all impossible - merely involves work to implement type-ahead find on that widget.

The question, I suppose, is "why" - isn't that what the search box is for?

---

### Post by ad_267 on 2009-06-11
> **Incognito-Here said:**
> Impossible by design, it's because of their list, which only keeps +10 and -10 songs from visible ones.

I'm pretty sure it's still possible, it shouldn't be that hard just to jump to a song within the track list. It can't be too much different from using Ctrl+J to jump to the playing song.

I think the main hurdle is that it conflicts with the keyboard shortcuts.

---

### Post by ad_267 on 2009-06-11
> **directhex said:**
> The question, I suppose, is "why" - isn't that what the search box is for?

No, the main issue with the search box is that it removes all songs from the list that don't match the search terms. It's also just less convenient.

It's a pretty intuitive thing to do, I'm surprised more people don't see this as a problem. It's also the default behaviour for this kind of widget. There's more talk about it on the bug page.

The annoying static is probably more of an issue for me though...

---

### Post by Incognito-Here on 2009-06-11
If they would do this possible, it would mean they are using one big list of tracks actually, just like rhythmbox ;)

---

### Post by ad_267 on 2009-06-11
> **Incognito-Here said:**
> If they would do this possible, it would mean they are using one big list of tracks actually, just like rhythmbox ;)

Nope not at all.

How is this any different from grabbing the scrollbar and moving it to a different position?

---

### Post by directhex on 2009-06-11
> **Incognito-Here said:**
> If they would do this possible, it would mean they are using one big list of tracks actually, just like rhythmbox ;)

You've made it abundantly clear that you don't understand the technology, so how about not making statements about what is or isn't possible?

It's not been implemented because nobody has written code to do it - the main developers don't care about the feature, and there are no patches to do it from anyone who DOES care.

---

### Post by Kow on 2009-06-11
I'm surprised this has not been mentioned yet (I don't think so anyways): The Rhythmbox library importer DOES NOT work in 1.5.0. Whether it is disabled or simply doesn't work I do not know. I do know that it is fixed in the latest git and I am currently importing my Rhythmbox library.

EDIT: All of the entries in my Rhythmbox library imported into Banshee 1.5.0 git snapshot from today successfully.

---

### Post by Incognito-Here on 2009-06-11
You think sqlite is fast enough to instant inline search, as RB and other apps using this method do? Firefox example proves it isn't, so, they need either to keep db in the memory as FF does, but in this case banshee will eat two times more memory than RB, or use sqlite while inline search, and users would say "banshee is so fu%king slow..."

---

### Post by Swarms on 2009-06-11
> **Kow said:**
> I'm surprised this has not been mentioned yet (I don't think so anyways): The Rhythmbox library importer DOES NOT work in 1.5.0. Whether it is disabled or simply doesn't work I do not know. I do know that it is fixed in the latest git and I am currently importing my Rhythmbox library.

EDIT: All of the entries in my Rhythmbox library imported into Banshee 1.5.0 git snapshot from today successfully.

1.5.0 is a development version, it wouldn't be required.

---

### Post by gnomeuser on 2009-06-11
> **Swarms said:**
> 1.5.0 is a development version, it wouldn't be required.

actually the problem was that the path to the rhythmbox databases changed since the code was merged. It was a simple fix, now the importer checks both the old and the new path and all is well.

---

### Post by olskar on 2009-06-11
A big annoyance for me with Banshee is that I have to use Ctrl+J to jump to currently playing song. This should really be done automatically when starting playing a song, that happens in every player I've tried and is probably something that will confuse new users.

However I was told that they use this, imo stupid, J shortcut due to problems with focus without it? Anyone know something about that?

---

### Post by directhex on 2009-06-11
> **olskar said:**
> A big annoyance for me with Banshee is that I have to use Ctrl+J to jump to currently playing song. This should really be done automatically when starting playing a song, that happens in every player I've tried and is probably something that will confuse new users.

However I was told that they use this, imo stupid, J shortcut due to problems with focus without it? Anyone know something about that?

I've been frustrated before when looking for a track to play and having the browser jump to somewhere different - so I prefer the shortcut key requirement

---

### Post by Kow on 2009-06-11
> **gnomeuser said:**
> actually the problem was that the path to the rhythmbox databases changed since the code was merged. It was a simple fix, now the importer checks both the old and the new path and all is well.

LOL doh! I was trying to figure out why the 1.5.0 development release wasn't properly finding rhythmbox libraries. I actually looked at the code and it looked fine. I just realized I was looking at the latest git master (which had the fix) and not the actual 1.5.0 release code. But this is important because in order for ubuntu to switch to banshee the rhythmbox migrator working at 100% is a requirement. IMO, banshee is very similar to rhythmbox and I don't have an issue switching. Both will suite the userbase ubuntu is primarily geared towards just fine. Banshee is about 5mb smaller too which is a lot of additional space, relatively speaking for the ISOs. The 1.6.0 release of banshee should prove it's worthiness of replacing rhythmbox. It's written in C# too! :)

---

### Post by froggyswamp on 2009-06-11
Why is Banshee so slow to startup? Isn't it written in C++?

---

### Post by gnomeuser on 2009-06-11
> **froggyswamp said:**
> Why is Banshee so slow to startup? Isn't it written in C++?

It's written in C# and C. Language choice really doesn't gaurantee performance, you can write bad code regardless, some tools just make it harder.

If you run banshee-1 --debug --debug-sql you should be able to find timings. If you capture a log of that output the developers will be able to see where your problem lies.

Start up time is being heavily profiled so daily snapshots from the banshee-daily ppa should continue to improve this.

That being said I don't find 1.5.x slow to start on my machine.

---

### Post by Incognito-Here on 2009-06-11
It's written in C#. It is so slow at startup because of JIT.  They were startup speed comparison at [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/) before, but they don't do them now. As I remember, C# programs were about 35 times slower at startup and 2 times slower in general than C or C++ programs.
Just try to compare some C# apps with their native equivalents (on windows too). Tomboy vs Gnote - they are clones, but gnote startup time is sooo much faster. Banshee vs RB - the same situation. Native programs (not all, but most of them) reacts instantly, but both mono and .NET programs usually have little delays. It's their pain and it cannot be resolved because of their design.

---

### Post by captaincrook on 2009-06-12
Dang no Hardy builds. Does anyone know if the Last.fm "Now Playing" bug is fixed?

---

### Post by Amaranth on 2009-06-12
Ideally Banshee would automatically jump to the currently playing song until you select another item in the list or scroll the list manually. Then it would go back to automatically if you pressed Ctrl-J.

---

### Post by gnomeuser on 2009-06-12
> **captaincrook said:**
> Dang no Hardy builds. Does anyone know if the Last.fm "Now Playing" bug is fixed?

If you told us whuch bugnumber you filed this as upstream it would be trivially easy for us to tell you. ;)

---

### Post by olskar on 2009-06-12
> **Amaranth said:**
> Ideally Banshee would automatically jump to the currently playing song until you select another item in the list or scroll the list manually. Then it would go back to automatically if you pressed Ctrl-J.

That was a good idea. Perhaps it could even go back automatically to the currently playing song after ~30 (or something) seconds of no scrolling or selecting another item manually?

---

### Post by ad_267 on 2009-06-12
> **olskar said:**
> That was a good idea. Perhaps it could even go back automatically to the currently playing song after ~30 (or something) seconds of no scrolling or selecting another item manually?

Or just whenever the song changed next. It could also be an option that could be enabled and disabled from a menu.

---

### Post by directhex on 2009-06-12
> **olskar said:**
> That was a good idea. Perhaps it could even go back automatically to the currently playing song after ~30 (or something) seconds of no scrolling or selecting another item manually?

File a wishlist bug - I though your concept has merit

---

### Post by MaX on 2009-06-12
> **olskar said:**
> I think that is exactly what RB does. If it were not doing that there would be no poinf of having such a feature.


No that's not it.. He doesn't want to have control over his own files.
Rhythmbox lets me put teh files where I want them and then I tell rhythmbox where they are.

Banshee (itunes) wants me to let banshee decide where and how my music should be organised

---

### Post by MaX on 2009-06-12
> **Incognito-Here said:**
> It's written in C#. It is so slow at startup because of JIT.  They were startup speed comparison at [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/) before, but they don't do them now. As I remember, C# programs were about 35 times slower at startup and 2 times slower in general than C or C++ programs.
Just try to compare some C# apps with their native equivalents (on windows too). Tomboy vs Gnote - they are clones, but gnote startup time is sooo much faster. Banshee vs RB - the same situation. Native programs (not all, but most of them) reacts instantly, but both mono and .NET programs usually have little delays. It's their pain and it cannot be resolved because of their design.
Isn't that just the first time? It would be stupid not to store the compiled version?

---

### Post by directhex on 2009-06-12
> **MaX said:**
> Isn't that just the first time? It would be stupid not to store the compiled version?

Optimizations are disabled when using AOT

---

### Post by gnomeuser on 2009-06-12
> **MaX said:**
> 
Banshee (itunes) wants me to let banshee decide where and how my music should be organised

Please be fair, you have a great deal of control over the layout (via gconf keys for the more advanced layout options, a sane default has been picked) if and only if you elect to let Banshee manage your music collection. This however is a choice, you don't need to have Banshee layout your files for you, you can do it yourself in any format you wish and unless you enabled the options to copy on import and keep files in sync with metadata then it will stay that way.

---

### Post by frustphil on 2009-06-12
Banshee, a mono-based app shouldn't be a part of Ubuntu by default. It should only be available for download by the users.

---

### Post by ad_267 on 2009-06-12
> **frustphil said:**
> Banshee, a mono-based app shouldn't be a part of Ubuntu by default. It should only be available for download by the users.

This isn't the place for that, this thread has already been locked once. Go away. If banshee is a better application than Rhythmbox then it should definitely be included instead.

---

### Post by wedderburn on 2009-06-13
> **frustphil said:**
> Banshee, a mono-based app shouldn't be a part of Ubuntu by default. It should only be available for download by the users.

Don't troll, its inclusion is because its best of breed.

Average users don't give 2 cents about what its written in as long as it does the job well.

---

### Post by ad_267 on 2009-06-13
> **Incognito-Here said:**
> It's worse, until it doesn't have library watching. RB has cleaner interface, faster, has all essential features and doesn't have so many minor bugs and glitches banshee does, RB just works, banshee for geeks who are not lazy to manually add new tracks and looking for workarounds for sh1tload of banshee bugs. Some rarely used features don't make a sense.

I never said it was better. I just said if it was then it should be included. I'm actually using Rhythmbox instead of Banshee at the moment.

---

### Post by Incognito-Here on 2009-06-13
Another thing I hate about these mono projects is that they are making "crossplatform" software. It means this software is an alien on every platform. For example: tomboy, instead of using gvfs to synchronize notes through ssh using sshfs. Banshee doesn't work with gvfs directly too.

---

### Post by SKLP on 2009-06-13
> **Incognito-Here said:**
> Another thing I hate about these mono projects is that they are making "crossplatform" software. It means this software is an alien on every platform. For example: tomboy, instead of using gvfs to synchronize notes through ssh using sshfs. Banshee doesn't work with gvfs directly too.You do know that GVFS provides a fuse bridge which allows any app to access its "mounted" shares. Actually it's the (I would say) main advantage over the older Gnome-vfs system

---

### Post by qamelian on 2009-06-13
> **wedderburn said:**
> Don't troll, its inclusion is because its best of breed.

That is very much a matter of opinion. I certainly don't consider it "best of breed" as it has never worked right any time I have installed it to try it, including this latest version. If it becomes the default player, I'll just need to remove it and replace it with an application that does work the way I expect it to.

---

### Post by Incognito-Here on 2009-06-13
> **SKLP said:**
> You do know that GVFS provides a fuse bridge which allows any app to access its "mounted" shares. Actually it's the (I would say) main advantage over the older Gnome-vfs system
I know, but having place mounted at the sidebar is much better than navigating through hidden ~/.gvfs. In addition, if the app knows about gvfs it can suggest you to mount a place, it's all about consistency and integrity. Mono stuff usually don't know anything about it, so it shouldn't be in default install. The clear point: CONSISTENCY and INTEGRITY. These things as important as quick startup. As I've mentioned mono apps doesn't have **ALL** these things: they break consistency, they break integrity, they are slow. Don't add another bloatware into the default install. If a program is written in C/C++ it can'be optimized to launch instantly. But if it's written in mono it isn't.

---

### Post by zekopeko on 2009-06-13
> **qamelian said:**
> That is very much a matter of opinion. I certainly don't consider it "best of breed" as it has never worked right any time I have installed it to try it, including this latest version. If it becomes the default player, I'll just need to remove it and replace it with an application that does work the way I expect it to.

that's why it's gonna be tested in this development cycle. so file bugs to make it rock.

---

### Post by Incognito-Here on 2009-06-13
> **zekopeko said:**
> that's why it's gonna be tested in this development cycle. so file bugs to make it rock.
make it launch in 1 second if you can lol :D:D:D

---

### Post by zekopeko on 2009-06-13
> **Incognito-Here said:**
> I know, but having place mounted at the sidebar is much better than navigating through hidden ~/.gvfs. In addition, if the app knows about gvfs it can suggest you to mount a place, it's all about consistency and integrity. Mono stuff usually don't know anything about it, so it shouldn't be in default install. The clear point: CONSISTENCY and INTEGRITY. These things as important as quick startup. As I've mentioned mono apps doesn't have **ALL** these things: they break consistency, they break integrity, they are slow. Don't add another bloatware into the default install. If a program is written in C/C++ it can'be optimized to launch instantly. But if it's written in mono it isn't.

**GVFS**
I wonder then why do my network shares appear in the sidebar yet also are in .gvfs? I guess that it never occurred to you that perhaps implementing sidebar entries for gvfs is up to the developers. Well i'm not surprised. You manage to disappoint in following logic. But you do have a lot of imagination.

**Cross-platform**
your argument fall in the water since Qt is also cross-platform.
and it integrates nicely on Windows, Mac or Linux.
Not to mention that it's written in your "holy" C++. So does GTK+ but only in C.
And mono is faster then python in various benchmarks. See:
[http://www.python.org/community/pycon/dc2004/papers/9/](http://www.python.org/community/pycon/dc2004/papers/9/)
Note that python is the preferred development language of Ubuntu.

**Speed**
You claim that you have a machine with a core i7 processor. so do please explain to me how banshee starts under 4sec on an 1.6Ghz ATOM processor running of a 5400rpm disk? It starts even faster on my main machine which is still slower then the one you claim to have.

**Optimization**
Mono can't be optimized? Please. As directhex pointed out you have no technical knowledge nor experience to know if something can or can't be optimized. I remember when Banshee 1.0 came out. They had a splash screen (just like Amarok which still has one by default) because it took more then 5sec to start. But in 1.2 it was gone and banshee continued to improve it's startup time. And they are still optimizing it. Amarok takes far more time to start than Banshee on very machine I own. And it's written in C++. What could that mean? That perhaps you can create a bloated application in any language? And that banshee isn't bloated compared to some media player?

---

### Post by psyke83 on 2009-06-13
> **zekopeko said:**
> 
**Optimization**
Mono can't be optimized? Please. As directhex pointed out you have no technical knowledge nor experience to know if something can or can't be optimized. I remember when Banshee 1.0 came out. They had a splash screen (just like Amarok which still has one by default) because it took more then 5sec to start. But in 1.2 it was gone and banshee continued to improve it's startup time. And they are still optimizing it. Amarok takes far more time to start than Banshee on very machine I own. And it's written in C++. What could that mean? That perhaps you can create a bloated application in any language? And that banshee isn't bloated compared to some media player?

I have to call BS on this paragraph. Amarok takes longer to startup because it has to load all the QT/KDE libraries into memory (usually for the first time) on a GNOME desktop. If you try to execute "kdeinit"* on a GNOME desktop, you'd see a noticeable delay before it completes, perhaps also because it is looking for daemons that are not running on a GNOME system (arts and so on). Running a KDE application on GNOME causes "kdeinit" to be invoked by default.

Note: this is for a KDE3 system, I haven't tested KDE4 much. This may have changed for KDE4 applications, but the QT/KDE library overhead remains unavoidable.

---

### Post by olskar on 2009-06-13
> **Incognito-Here said:**
> make it launch in 1 second if you can lol :D:D:D

Nothing in Ubuntu is launched in 1 second or less. A simple app like gedit takes about 2 seconds to open.

---

### Post by xebian on 2009-06-13
Just for curiousity I've tried the Ubuntu live A2.  How come Banshee is not there? Only RB?  If Banshee is going to be the one, wouldn't it be proper to have it in place so it can be user tested more?

---

### Post by zekopeko on 2009-06-13
> **psyke83 said:**
> I have to call BS on this paragraph. Amarok takes longer to startup because it has to load all the QT/KDE libraries into memory (usually for the first time) on a GNOME desktop. If you try to execute "kdeinit"* on a GNOME desktop, you'd see a noticeable delay before it completes, perhaps also because it is looking for daemons that are not running on a GNOME system (arts and so on). Running a KDE application on GNOME causes "kdeinit" to be invoked by default.

Note: this is for a KDE3 system, I haven't tested KDE4 much. This may have changed for KDE4 applications, but the QT/KDE library overhead remains unavoidable.

Who said i was starting Amarok on a Gnome system? I was starting amarok on a KDE system and it still took it's sweet time opening. Not to mention that for some reason it opesn in the tray. Good luck finding it. The point is that on the same little netbook banshee starts faster (on Gnome and KDE) then amarok on a KDE system.

---

### Post by taavikko on 2009-06-13
> **xebian said:**
> Just for curiousity I've tried the Ubuntu live A2.  How come Banshee is not there? Only RB?  If Banshee is going to be the one, wouldn't it be proper to have it in place so it can be user tested more?

Banshee haven't yet replaced RB, hence not in the alpha2.

Testing can be done after manual installation of it.

---

### Post by zekopeko on 2009-06-13
> **taavikko said:**
> Banshee haven't yet replaced RB, hence not in the alpha2.

Testing can be done after manual installation of it.

I'm thinking that they are waiting for Banshee devs to release 1.6.
It would be a couple of weeks beacuse they are trying to fix some of the things Ubuntu devs said were show-stoppers.

---

### Post by xebian on 2009-06-13
> **taavikko said:**
> Banshee haven't yet replaced RB, hence not in the alpha2.

Testing can be done after manual installation of it.

Ok.  Just wanted to see what's all the fuzz about Banshee.:)

I'm a KDE4 user so can't install it.

---

### Post by psyke83 on 2009-06-13
> **zekopeko said:**
> Who said i was starting Amarok on a Gnome system? I was starting amarok on a KDE system and it still took it's sweet time opening. Not to mention that for some reason it opesn in the tray. Good luck finding it. The point is that on the same little netbook banshee starts faster (on Gnome and KDE) then amarok on a KDE system.

Alright then. However, people could have easily understood you to mean Amarok on GNOME, since we're talking about comparisons to Banshee (which uses GTK).

---

### Post by taavikko on 2009-06-13
> **xebian said:**
> 
I'm a KDE4 user so can't install it.

But why, of course you can ;)

```
devil@elite:~$ sudo aptitude install banshee
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  banshee binfmt-support{a} brasero{a} cli-common{a} devicekit{a} devicekit-disks{a} freepats{a}
  gamin{a} gconf2{a} gnome-icon-theme{a} gnome-keyring{a} gnome-mime-data{a} gnome-mount{a}
  gstreamer0.10-plugins-bad{a} gstreamer0.10-plugins-base{a} gstreamer0.10-plugins-good{a}
  gstreamer0.10-x{a} gvfs{a} gvfs-backends{a} libart2.0-cil{a} libass3{a} libatasmart0{a}
  libavahi-glib1{a} libbeagle1{a} libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a}
  libbonoboui2-common{a} libboo2.0-cil{a} libbrasero-media0{a} libcamel1.2-14{a} libcdaudio1{a}
  libcdio-cdda0{a} libcdio-paranoia0{a} libcdio7{a} libcroco3{a} libdca0{a} libdevkit-gobject0{a}
  libedataserver1.2-11{a} libenca0{a} libexempi3{a} libgail-common{a} libgail18{a} libgamin0{a}
  libgconf2.0-cil{a} libgcr0{a} libgdiplus{a} libgdu0{a} libglade2-0{a} libglade2.0-cil{a}
  libglib2.0-cil{a} libgmyth0{a} libgnome-keyring0{a} libgnome-vfs2.0-cil{a} libgnome2-0{a}
  libgnome2-common{a} libgnome2.24-cil{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a}
  libgnomeui-0{a} libgnomeui-common{a} libgnomevfs2-0{a} libgnomevfs2-common{a} libgnomevfs2-extra{a}
  libgp11-0{a} libgsf-1-114{a} libgsf-1-common{a} libgtk2.0-cil{a} libgvfscommon0{a} libiptcdata0{a}
  liblaunchpad-integration1{a} libmms0{a} libmono-addins-gui0.2-cil{a} libmono-addins0.2-cil{a}
  libmono-cairo2.0-cil{a} libmono-corlib2.0-cil{a} libmono-data-tds2.0-cil{a} libmono-data2.0-cil{a}
  libmono-getoptions2.0-cil{a} libmono-i18n2.0-cil{a} libmono-posix2.0-cil{a}
  libmono-security2.0-cil{a} libmono-sharpzip2.84-cil{a} libmono-sqlite2.0-cil{a}
  libmono-system-data2.0-cil{a} libmono-system-web2.0-cil{a} libmono-system2.0-cil{a}
  libmono-zeroconf1.0-cil{a} libmono0{a} libmono2.0-cil{a} libnautilus-extension1{a}
  libndesk-dbus-glib1.0-cil{a} libndesk-dbus1.0-cil{a} libneon27-gnutls{a} libnotify0.4-cil{a}
  libnotify1{a} libpam-gnome-keyring{a} libpolkit-gnome0{a} libproxy0{a} librsvg2-2{a}
  librsvg2-common{a} libsexy2{a} libsgutils1{a} libshout3{a} libsoup-gnome2.4-1{a} libsoup2.4-1{a}
  libsqlite0{a} libtaglib2.0-cil{a} libtotem-plparser12{a} libunique-1.0-0{a} libvisual-0.4-0{a}
  libvisual-0.4-plugins{a} libwildmidi0{a} libwnck-common{a} libwnck22{a} libxres1{a} mono-2.0-gac{a}
  mono-2.0-runtime{a} mono-common{a} mono-gac{a} mono-jit{a} mono-runtime{a} notification-daemon{a}
  podsleuth{a} policykit-gnome{a} sg3-utils{a}
0 packages upgraded, 126 newly installed, 0 to remove and 0 not upgraded.
Need to get 59.6MB/60.4MB of archives. After unpacking 177MB will be used.
```

---

### Post by xebian on 2009-06-13
> **taavikko said:**
> But why, of course you can ;)

```
devil@elite:~$ sudo aptitude install banshee
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  banshee binfmt-support{a} brasero{a} cli-common{a} devicekit{a} devicekit-disks{a} freepats{a}
  gamin{a} gconf2{a} gnome-icon-theme{a} gnome-keyring{a} gnome-mime-data{a} gnome-mount{a}
  gstreamer0.10-plugins-bad{a} gstreamer0.10-plugins-base{a} gstreamer0.10-plugins-good{a}
  gstreamer0.10-x{a} gvfs{a} gvfs-backends{a} libart2.0-cil{a} libass3{a} libatasmart0{a}
  libavahi-glib1{a} libbeagle1{a} libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a}
  libbonoboui2-common{a} libboo2.0-cil{a} libbrasero-media0{a} libcamel1.2-14{a} libcdaudio1{a}
  libcdio-cdda0{a} libcdio-paranoia0{a} libcdio7{a} libcroco3{a} libdca0{a} libdevkit-gobject0{a}
  libedataserver1.2-11{a} libenca0{a} libexempi3{a} libgail-common{a} libgail18{a} libgamin0{a}
  libgconf2.0-cil{a} libgcr0{a} libgdiplus{a} libgdu0{a} libglade2-0{a} libglade2.0-cil{a}
  libglib2.0-cil{a} libgmyth0{a} libgnome-keyring0{a} libgnome-vfs2.0-cil{a} libgnome2-0{a}
  libgnome2-common{a} libgnome2.24-cil{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a}
  libgnomeui-0{a} libgnomeui-common{a} libgnomevfs2-0{a} libgnomevfs2-common{a} libgnomevfs2-extra{a}
  libgp11-0{a} libgsf-1-114{a} libgsf-1-common{a} libgtk2.0-cil{a} libgvfscommon0{a} libiptcdata0{a}
  liblaunchpad-integration1{a} libmms0{a} libmono-addins-gui0.2-cil{a} libmono-addins0.2-cil{a}
  libmono-cairo2.0-cil{a} libmono-corlib2.0-cil{a} libmono-data-tds2.0-cil{a} libmono-data2.0-cil{a}
  libmono-getoptions2.0-cil{a} libmono-i18n2.0-cil{a} libmono-posix2.0-cil{a}
  libmono-security2.0-cil{a} libmono-sharpzip2.84-cil{a} libmono-sqlite2.0-cil{a}
  libmono-system-data2.0-cil{a} libmono-system-web2.0-cil{a} libmono-system2.0-cil{a}
  libmono-zeroconf1.0-cil{a} libmono0{a} libmono2.0-cil{a} libnautilus-extension1{a}
  libndesk-dbus-glib1.0-cil{a} libndesk-dbus1.0-cil{a} libneon27-gnutls{a} libnotify0.4-cil{a}
  libnotify1{a} libpam-gnome-keyring{a} libpolkit-gnome0{a} libproxy0{a} librsvg2-2{a}
  librsvg2-common{a} libsexy2{a} libsgutils1{a} libshout3{a} libsoup-gnome2.4-1{a} libsoup2.4-1{a}
  libsqlite0{a} libtaglib2.0-cil{a} libtotem-plparser12{a} libunique-1.0-0{a} libvisual-0.4-0{a}
  libvisual-0.4-plugins{a} libwildmidi0{a} libwnck-common{a} libwnck22{a} libxres1{a} mono-2.0-gac{a}
  mono-2.0-runtime{a} mono-common{a} mono-gac{a} mono-jit{a} mono-runtime{a} notification-daemon{a}
  podsleuth{a} policykit-gnome{a} sg3-utils{a}
0 packages upgraded, 126 newly installed, 0 to remove and 0 not upgraded.
Need to get 59.6MB/60.4MB of archives. After unpacking 177MB will be used.
```

Looking at all those junks to be installed makes me shiver ;)

Not that I can't but I just won't.

---

### Post by zekopeko on 2009-06-13
> **xebian said:**
> Looking at all those junks to be installed makes me shiver ;)

Not that I can't but I just won't.

i don't get this "pureness" thing.

---

### Post by zekopeko on 2009-06-13
> **psyke83 said:**
> Alright then. However, people could have easily understood you to mean Amarok on GNOME, since we're talking about comparisons to Banshee (which uses GTK).

i was replying to the whole "banshee is slow,bloated bla bla bla" thing and simply pointed out that you can write bloatware in anything. and banshee is far from bloatware.

---

### Post by Incognito-Here on 2009-06-13
> **olskar said:**
> Nothing in Ubuntu is launched in 1 second or less. A simple app like gedit takes about 2 seconds to open.
Seems you have huge iowaites, one my computer suffers from it. Everything was OK until 2.6.20.
// Gedit isn't lightweigh app, but takes about 0.7 seconds on the q6600 + Intel P35 + 8Gb + 1Tb Samsung F1 with Ext4 i'm using right now ;)

---

### Post by Incognito-Here on 2009-06-13
> **zekopeko said:**
> i was replying to the whole "banshee is slow,bloated bla bla bla" thing and simply pointed out that you can write bloatware in anything. and banshee is far from bloatware.
banshee is bloatware, this is a truth. The fact amarok is bloatware doesn't make banshee any faster ;)

---

### Post by zekopeko on 2009-06-13
> **Incognito-Here said:**
> banshee is bloatware, this is a truth. The fact amarok is bloatware doesn't make banshee any faster ;)

bloatware compared to what? MPD? sure. rhythmbox? no. amarok2? no. ;)

---

### Post by neighborlee on 2009-06-13
> **zekopeko said:**
> i don't get this "pureness" thing.

Why Im wondering, would you characterize it as 'pureness' , what exactly do you mean by this ?

If someone doesn't want to install something because of the 'junk' it installs along with it, and I guess its their right to do so,  as mono supporters have that right to install that,  while disagreeing sometimes passionately about it ( but we hope NEVER rudely or angrily ) ,- why do you react offensively by calling them pure for the ideology, who exactly do comments like this serve ?

cheers
nl

---

### Post by zekopeko on 2009-06-13
> **xebian said:**
> Ok.  Just wanted to see what's all the fuzz about Banshee.:)

I'm a KDE4 user so can't install it.

> **xebian said:**
> Looking at all those junks to be installed makes me shiver ;)

Not that I can't but I just won't.

> **neighborlee said:**
> Why Im wondering, would you characterize it as 'pureness' , what exactly do you mean by this ?

If someone doesn't want to install something because of the 'junk' it installs along with it, and I guess its their right to do so,  as mono supporters have that right to install that,  while disagreeing sometimes passionately about it ( but we hope NEVER rudely or angrily ) ,- why do you react offensively by calling them pure for the ideology, who exactly do comments like this serve ?

cheers
nl

you took my "pureness" comment out of context. xebian says he is a KDE4 user. Banshee is a Gnome app. I was simply stating my more pragmatic view. In the end an app is still an app. Use what's best for you. I run KDE4 apps in Gnome environment and vice versa. What's another 600mb on a 250gb drive (in my case)? ;)

---

### Post by directhex on 2009-06-13
> **zekopeko said:**
> I'm thinking that they are waiting for Banshee devs to release 1.6.
It would be a couple of weeks beacuse they are trying to fix some of the things Ubuntu devs said were show-stoppers.

Any change to/from can be reverted before release.

The Desktop team will likely make the change in time for Alpha 3 - I want to have Mono 2.4 in place first (as it does more space shrinking), and that means waiting a little for there to be a package in Debian which I'm 100% happy syncing (i.e. I await Mono 2.4+dfsg-3)

---

### Post by xebian on 2009-06-13
> **zekopeko said:**
> i don't get this "pureness" thing.

It's not what you think.  like I said I just want to see what's all the fuzz.  Until the live CD has it there's no compelling reason for me to install it plus quite a few bunches.

BTW Kubuntu isn't that 'pure' as it shares some Ubuntu stuff.

---

### Post by captaincrook on 2009-06-14
> **gnomeuser said:**
> If you told us whuch bugnumber you filed this as upstream it would be trivially easy for us to tell you. ;)

Oh, I'm not sure if it was reported. It was talked about on Banshee's Last.fm group page or whatever but if it was actually sent to the bug report I dunno. I'll have a quick look though.

EDIT: Nope, doesn't look like it. I might have to get on it.

---

### Post by directhex on 2009-06-14
> **directhex said:**
> Any change to/from can be reverted before release.

The Desktop team will likely make the change in time for Alpha 3 - I want to have Mono 2.4 in place first (as it does more space shrinking), and that means waiting a little for there to be a package in Debian which I'm 100% happy syncing (i.e. I await Mono 2.4+dfsg-3)

-3 doesn't build on amd64. Sigh.

---

### Post by gnomeuser on 2009-06-14
> **captaincrook said:**
> Oh, I'm not sure if it was reported. It was talked about on Banshee's Last.fm group page or whatever but if it was actually sent to the bug report I dunno. I'll have a quick look though.

EDIT: Nope, doesn't look like it. I might have to get on it.

If the _developers_ don't know about the bug, it doesn't exist. We cannot fix what we cannot see.

---

### Post by Hairy_Palms on 2009-06-14
I was very opposed to banshee by default back in.. erm.. intrepid i think? due to it using a heck of a lot more ram, and being quite buggy, ram usage in RB vs banshee is now nearly identical, and i can live with it using 4% cpu instead of 2% over Rhythmbox

my only major problem with it now is that it doesnt access daap shares, (im not talking about itunes 7+ shares either) which rhythmbox has no problem accessing.
oh and i do wish they would make the progress bar longer, its a pain for any song longer than about 3 minutes, 

that said i now use it as my default player, keeping rhythmbox for daap shares.

---

### Post by captaincrook on 2009-06-14
> **gnomeuser said:**
> If the _developers_ don't know about the bug, it doesn't exist. We cannot fix what we cannot see.

Uhh, I know that, just that judging by the talk on the group page or whatever I figured it was hinted someone would report it 'cause everyone was talking about it and what to do. A quick surf to the bug list shows no one actually reported it, so "I might have to get on it" and report it myself. Maybe it got fixed with 1.5.0, which is why I was bummed that there were no hardy packages out right now so I could see.

---

### Post by directhex on 2009-06-14
> **Hairy_Palms said:**
> I was very opposed to banshee by default back in.. erm.. intrepid i think? due to it using a heck of a lot more ram, and being quite buggy, ram usage in RB vs banshee is now nearly identical, and i can live with it using 4% cpu instead of 2% over Rhythmbox

my only major problem with it now is that it doesnt access daap shares, (im not talking about itunes 7+ shares either) which rhythmbox has no problem accessing.
oh and i do wish they would make the progress bar longer, its a pain for any song longer than about 3 minutes, 

that said i now use it as my default player, keeping rhythmbox for daap shares.

I would have opposed Banshee by default for Intrepid too. Rhythmbox was better at that point.

---

### Post by puccaso on 2009-06-15
i stand by my original post...

a modern music player needs a few things
and one of them is a genre browser.. and play by genre.. 
if it can read ID tags, it should at least be able to utilise some of them, play by album, artist, and genre.

without that, it has no use for me.


another point

it should have an option to detatch the playing video from the 
main window.

---

### Post by tgpraveen on 2009-06-15
> **Hairy_Palms said:**
> I was very opposed to banshee by default back in.. erm.. intrepid i think? due to it using a heck of a lot more ram, and being quite buggy, ram usage in RB vs banshee is now nearly identical, and i can live with it using 4% cpu instead of 2% over Rhythmbox

my only major problem with it now is that it doesnt access daap shares, (im not talking about itunes 7+ shares either) which rhythmbox has no problem accessing.
oh and i do wish they would make the progress bar longer, its a pain for any song longer than about 3 minutes, 

that said i now use it as my default player, keeping rhythmbox for daap shares.

my banshee 1.4.3 has daap share support just go in preferences->plugins and there u will see daap extension.

i think rb also does daap thru an extension only. so nota point of complaining.

but currently banshee uses a lot MORE ram than rb.

---

### Post by Swarms on 2009-06-15
> **tgpraveen said:**
> my banshee 1.4.3 has daap share support just go in preferences->plugins and there u will see daap extension.

i think rb also does daap thru an extension only. so nota point of complaining.

but currently banshee uses a lot MORE ram than rb.

I think he mean that it doesn't work in latest version.

---

### Post by directhex on 2009-06-15
> **Swarms said:**
> I think he mean that it doesn't work in latest version.

It's hit and miss. I wish I knew what caused it to not notice shares.

---

### Post by SushiR on 2009-06-15
Oh jeez, it's so slow scanning my music. It'll take AGES - and then I still need to add files from an nfs share. Oh boy... :mad:

---

### Post by Hairy_Palms on 2009-06-15
> my banshee 1.4.3 has daap share support just go in preferences->plugins and there u will see daap extension.

i think rb also does daap thru an extension only. so nota point of complaining.

but currently banshee uses a lot MORE ram than rb.

i know it has daap support, it just doesnt connect and rhythmbox can, which is the issue, it can see all shares fine. it doesnt use any more ram than Rhythmbox anymore here.

[EDIT] its not just the latest, it doesnt work in any version 1.4-1.6beta1 cant remember whether it worked in 1.3 and earlier. if you know how i can debug the issue id be more than willing to try.

---

### Post by directhex on 2009-06-15
> **SushiR said:**
> Oh jeez, it's so slow scanning my music. It'll take AGES - and then I still need to add files from an nfs share. Oh boy... :mad:

Do you have BPM scanning turned on? That slows things down.

And generally speaking, what format are your files? Some formats are slower to scan than others - e.g. ID3v2 tags are very slow as you need to scan the entire file to find all tags, rather than everything being reliably at one end of the file

---

### Post by zekopeko on 2009-06-15
> **directhex said:**
> Do you have BPM scanning turned on? That slows things down.

And generally speaking, what format are your files? Some formats are slower to scan than others - e.g. ID3v2 tags are very slow as you need to scan the entire file to find all tags, rather than everything being reliably at one end of the file

is BPM scanning on by default? i remember another poster with the I/O, CPU issues that had the BPM problem. BPM scanning should be of by default.

---

### Post by wucherpfennig on 2009-06-15
hey. i just downloaded the latest version and was wondering where to find this rhythmbox-migration plugin? anyone knows?

---

### Post by directhex on 2009-06-15
> **zekopeko said:**
> is BPM scanning on by default? i remember another poster with the I/O, CPU issues that had the BPM problem. BPM scanning should be of by default.

It's off by default... but nobody likes unticked tickboxes!

---

### Post by zekopeko on 2009-06-15
> **directhex said:**
> It's off by default... but nobody likes unticked tickboxes!

then why provide them? ;)

---

### Post by biasquez on 2009-06-15
i founded possible bug: exactly, when i plug my mp3 player and i try to sync manually mp3 files with drag&drop, it doesn't work.

---

### Post by Joe_Bishop on 2009-06-15
I have a suggestion: use banshee to test new ideas, but don't make it the default one. The bugs they told about prove it's not ready for typical end user. Too many glitches and inconsistencies. Especially I hate poor d'n'd support. In RB they can copy tracks just by dragging them from the list into the nautilus. This trick doesn't work in banshee, as well as many other annoyances.

---

### Post by Kow on 2009-06-15
> **Swarms said:**
> I think he mean that it doesn't work in latest version.

DAAP works in latest git if the host is rhythmbox. IE: I can load a rhythmbox playlist via DAAP in banshee just fine. DAAP never worked well with Apple products. I was never able to get rhythmbox to successfully connect to an iTunes playlist.

---

### Post by Swarms on 2009-06-15
> **Kow said:**
> DAAP works in latest git if the host is rhythmbox. IE: I can load a rhythmbox playlist via DAAP in banshee just fine. DAAP never worked well with Apple products. I was never able to get rhythmbox to successfully connect to an iTunes playlist.

I meant latest official release, not from git.

---

### Post by ashmew2 on 2009-06-16
I think Rhythmbox should remain the default for Karmic , And everyone who likes Banshee can always install it from the repos or something.Maybe Banshee would be MUCH Stable and have folder watching till 10.04 ? Maybe it could be added then!

---

### Post by amano on 2009-06-16
Until there is no gapless playing feature, Banshee should not be made the default. That is the real showstopper but it is not mentioned within the spec.

No gapless playing, no mp3 recordings of live shows. Let alone operas and the likes... :(

---

### Post by directhex on 2009-06-16
> **amano said:**
> Until there is no gapless playing feature, Banshee should not be made the default. That is the real showstopper but it is not mentioned within the spec.

No gapless playing, no mp3 recordings of live shows. Let alone operas and the likes... :(

[https://launchpad.net/~banshee-unstable-team/+archive/ppa](https://launchpad.net/~banshee-unstable-team/+archive/ppa)

Experimental banshee-gapless package

---

### Post by JohnJackson on 2009-06-16
> **directhex said:**
> [https://launchpad.net/~banshee-unstable-team/+archive/ppa](https://launchpad.net/~banshee-unstable-team/+archive/ppa)

Experimental banshee-gapless package

Wants me to remove banshee :\

---

### Post by gnomeuser on 2009-06-16
> **JohnJackson said:**
> Wants me to remove banshee :\

It's not a plugin, it's a banshee replacement package with the experimental gapless playback code added. No worries it is expected that it replaces banshee

---

### Post by jmmL on 2009-06-16
> **JohnJackson said:**
> Wants me to remove banshee :\

From looking at the ppa, banshee-gapless seems to *replace* banshee completely. That is, it is a binary replacement with gapless support, not a plugin that enables gapless playback in stock banshee.

I could be entirely wrong.

Edit: Pipped to the post. Confirms my guestimate at least.

---

### Post by directhex on 2009-06-16
Had a play with the experimental gapless patch. Works fine! Except it doesn't work at all if you ever deag the track progress bar whilst playing (i.e. don't try testing it by skipping to the end of a song, 'cos that breaks it). Works only on songs played end-to-end. It's a start though

---

### Post by RAOF on 2009-06-16
That's pretty funky.  I wonder what playbin2's doing there!

Oh, also a disclaimer: this is only gapless for codecs which have a sample-accurate encoded length (ie: virtually everything but mp3).  mp3s won't (necessarily) appear gapless because encoders need to pad the end with silence up to the mp3 blocksize.

---

### Post by JohnJackson on 2009-06-17
> **gnomeuser said:**
> It's not a plugin, it's a banshee replacement package with the experimental gapless playback code added. No worries it is expected that it replaces banshee

Ahhh, must've been too tired to work that one out last night, thanks.

---

### Post by RAOF on 2009-06-17
Hm.  For those playing at home, I can only reproduce the crazy behaviour on seek with FLAC files, not mp3s, m4as, or WavPack files.

---

### Post by quazi on 2009-06-19
So folder watching looks like it's coming alone pretty well.  If you compile and install the file attached here: [http://bugzilla.gnome.org/show_bug.cgi?id=421376](http://bugzilla.gnome.org/show_bug.cgi?id=421376)
it adds itself as a plugin to banshee.

After I deleted some files, it automatically removed them from the library and all playlists (not sure if that's a good thing yet) and upon adding files they immediately showed up in the library.

---

### Post by zekopeko on 2009-06-20
> **quazi said:**
> After I deleted some files, it automatically removed them from the library and all playlists (**not sure if that's a good thing yet**) and upon adding files they immediately showed up in the library.

why do you think that could be a bad thing?

---

### Post by directhex on 2009-06-20
> **zekopeko said:**
> why do you think that could be a bad thing?

Music on network mount, forget to mount it when loading banshee... bye bye playlists!

It's a Rhythmbox irritation

---

### Post by Gourgi on 2009-06-20
> **directhex said:**
> Music on network mount, forget to mount it when loading banshee... bye bye playlists!

It's a Rhythmbox irritation

i get your point
it worths filling a bug ;)

---

### Post by gnomeuser on 2009-06-20
> **directhex said:**
> Music on network mount, forget to mount it when loading banshee... bye bye playlists!

It's a Rhythmbox irritation

Andrés G. Aragoneses and Patryk Zawadzki to the rescue:


[http://bugzilla.gnome.org/show_bug.cgi?id=563630](http://bugzilla.gnome.org/show_bug.cgi?id=563630)

---

### Post by SushiR on 2009-06-20
> **quazi said:**
> So folder watching looks like it's coming alone pretty well.  If you compile and install the file attached here: [http://bugzilla.gnome.org/show_bug.cgi?id=421376](http://bugzilla.gnome.org/show_bug.cgi?id=421376)
it adds itself as a plugin to banshee.

How can I compile that file?

---

### Post by Creative1412 on 2009-06-21
Banshee is one of the best but it got some issus with videos (I use 1.5)
for me i use smplayer with Banshee and uninstalled totem

---

### Post by Joe_Bishop on 2009-06-21
> **Gourgi said:**
> i get your point
it worths filling a bug ;)
banshee doesn't know about gvfs, so no clean way ;)

---

### Post by jedimasterk on 2009-06-23
This is really bad news. All Mono apps should be completely stripped from all Linux distributions. JUST KIDDING!!!! Great News!!:D

---

### Post by ghindo on 2009-06-23
> **jedimasterk said:**
> This is really bad news. All Mono apps should be completely stripped from all Linux distributions. JUST KIDDING!!!! Great News!!:DARGH you had me right till the end!  Good show, sir!

---

### Post by quazi on 2009-06-24
> **directhex said:**
> Music on network mount, forget to mount it when loading banshee... bye bye playlists!

It's a Rhythmbox irritation

The advantage of Rhythmbox is that it at least tells you what you're missing.

One of the big things I miss about foobar2000 is that it doesn't need to access the files to manage playlists.  In fact, I still use foobar2000 to manage my library although I use Rhythmbox/Banshee to actually play the music.

I don't recall exactly what is required to compile the plugin, but I do know that you need the package automake.

---

### Post by Bealer on 2009-06-30
> **Incognito-Here said:**
> I'm not a mono troll, I'm C# developer. The last means I know advantages and disadvantages of this language. So I don't recommend anyone to write desktop apps with this technology, both .NET or mono.

Absolute rubbish. Tell that to Microsoft who are currently building Visual Studio 10 based on WPF. 

Obviously C/C++ apps will be quicker, but the difference can be marginal if well written. And often barely noticeable to the end user.

> **Incognito-Here said:**
> It is. Just try to open Preferences, Search All Notes.
Gnote response instantly, tomboy *CLEARLY* needs some short time. It's almost nothing, but the difference is seen. In addition, gnote eat 11.2Mb of memory, while tomboy took around 40Mb. So, tomboy is the first candidate to replace to, gnote is the more appropriate alternative (clone).

What?

Firstly, just because it uses 40mb, that isn't bad. Maybe it's making more use of the memory, rather than eating up cpu cycles or hard drive spin time. 40mb is hardly a big footprint given that most pc's have well over 1,000mb these days. People often get a little anal about memory usage. It's there to be used.

Secondly, ok it may not be as responsive in some places, but that could be down to inefficient coding, and not the framework it's built upon. Mono should work in milliseconds when sorting objects, so something is clearly not right.

> **Incognito-Here said:**
> banshee is bloatware, this is a truth. The fact amarok is bloatware doesn't make banshee any faster ;)

Banshee is far from bloatware. And it can't be a truth, as it's subjective. I can't see what it contains additionally that is bloating it. I'm sure the majority will agree and say it's not bloated.

---

### Post by RAOF on 2009-07-01
> **Bealer said:**
> ...
Obviously C/C++ apps will be quicker, but the difference can be marginal if well written. And often barely noticeable to the end user.
...

I'd like this particular meme to die.  It's *not* inevitable that C/C++ apps be quicker.  It's often easier to implement something efficiently in C# than C or C++, which means that often things are implemented more efficiently in C# rather than C or C++ (see, for example, Banshee's SQL-backed listview).

Secondly, even given essentially the same code, it's possible for VM languages to be *faster* than native code, although this isn't currently the case for most code.  There are some optimisations that can't really be done statically at compile-time.  IBM did some interesting research a couple of years ago where they demonstrated an experimental emulator for one of their machines that would emulate the machine it was running on *and execute that code faster than on the bare metal*.  I can't seem to find a link to that (particularly cool) research, though I recall it being on arstechnica.com.  If anyone can find it again, I'd love a link :).

EDIT: Oops!  That wasn't IBM's research, it was [HP's Dynamo](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.36.7516) binary translation system.  ([ArsTechnica link](http://arstechnica.com/reviews/1q00/dynamo/dynamo-1.html)).

---

### Post by Joe_Bishop on 2009-07-01
> **RAOF said:**
> I'd like this particular meme to die.  It's *not* inevitable that C/C++ apps be quicker.  It's often easier to implement something efficiently in C# than C or C++, which means that often things are implemented more efficiently in C# rather than C or C++ (see, for example, Banshee's SQL-backed listview).

Secondly, even given essentially the same code, it's possible for VM languages to be *faster* than native code, although this isn't currently the case for most code.  There are some optimisations that can't really be done statically at compile-time.  IBM did some interesting research a couple of years ago where they demonstrated an experimental emulator for one of their machines that would emulate the machine it was running on *and execute that code faster than on the bare metal*.  I can't seem to find a link to that (particularly cool) research, though I recall it being on arstechnica.com.  If anyone can find it again, I'd love a link :).

EDIT: Oops!  That wasn't IBM's research, it was [HP's Dynamo](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.36.7516) binary translation system.  ([ArsTechnica link](http://arstechnica.com/reviews/1q00/dynamo/dynamo-1.html)).
blah-blah-blah, you better do not trust in propaganda/marketing. Their worst things is horrible startup time and lags while gc is working. It couldn't be improved by design.

---

### Post by Amaranth on 2009-07-03
GC stalls? Are we back in the 1980s?

---

### Post by ranch hand on 2009-07-03
> **Amaranth said:**
> GC stalls? Are we back in the 1980s?
Geeze I hope not.  A lot of really crappy music.

---

### Post by pt123 on 2009-07-03
> **RAOF said:**
> I'd like this particular meme to die.  It's *not* inevitable that C/C++ apps be quicker.  It's often easier to implement something efficiently in C# than C or C++, which means that often things are implemented more efficiently in C# rather than C or C++ (see, for example, Banshee's SQL-backed listview).

F-Spot is so slow when loading up the images in full view or in slide shows (they use a pause blur to hide it). Then you have the navigation of it in "explorer" mode which is sluggish to say the least. When you compare it to Picasa on Linux which runs using Wine, it is humiliating. Picasa is so smooth the thumbnails float smoothly across the screen when navigating, and with the slideshows there is no pause blur like F-spot.

You look at Windows none of the major multimedia applications are not written in .Net. Even Microsoft do not write their Windows Media player in .Net.

---

### Post by directhex on 2009-07-03
> **pt123 said:**
> F-Spot is so slow when loading up the images in full view or in slide shows (they use a pause blur to hide it). Then you have the navigation of it in "explorer" mode which is sluggish to say the least. When you compare it to Picasa on Linux which runs using Wine, it is humiliating. Picasa is so smooth the thumbnails float smoothly across the screen when navigating, and with the slideshows there is no pause blur like F-spot.

You look at Windows none of the major multimedia applications are not written in .Net. Even Microsoft do not write their Windows Media player in .Net.

How about, say, The Sims 3?

---

### Post by zekopeko on 2009-07-03
> **pt123 said:**
> F-Spot is so slow when loading up the images in full view or in slide shows (they use a pause blur to hide it). bla bla bla.

You probably missed a part of thread title where it said Banshee.

Here, let me copy it for you, enlarge it and bold it for you.

**[SIZE="5"]Banshee 1.5.0 released![/SIZE]**

---

### Post by Eclipse. on 2009-07-03
> **jmmL said:**
> Wow; that looks really good! Unfortunately the PPA for banshee unstable is pretty much dormant: [https://launchpad.net/~banshee-unstable-team/+archive/ppa77]("https://launchpad.net/%7Ebanshee-unstable-team/+archive/ppa")

EDIT: Just found this: [https://edge.launchpad.net/~banshee-team/+archive/banshee-daily]("https://edge.launchpad.net/%7Ebanshee-team/+archive/banshee-daily")

Unstable team ppa just got updated.;)

---

### Post by ghindo on 2009-07-03
Have there been any updates on those Bashee features which have been keeping it from being the default player in Karmic?

---

### Post by ranch hand on 2009-07-04
> **zekopeko said:**
> you probably missed a part of thread title where it said banshee.

Here, let me copy it for you, enlarge it and bold it for you.

**[size="5"]banshee 1.5.0 released![/size]**
+1

---

### Post by directhex on 2009-07-04
> **ghindo said:**
> Have there been any updates on those Bashee features which have been keeping it from being the default player in Karmic?

There's been a bunch of work on the a11y - but it requires GTK# from trunk, due to Atk bugs in 2.12

The guy who made the first Magnatune plugin is back from the dead and hopefully working on it again at [http://magnatune.code.worldmaker.net/](http://magnatune.code.worldmaker.net/) (contributors welcome)

I think someone at Canonical was looking at the manuals question, but I don't know how far that's gone

---

### Post by gnomeuser on 2009-07-04
> **ghindo said:**
> Have there been any updates on those Bashee features which have been keeping it from being the default player in Karmic?

[http://bugzilla.gnome.org/show_bug.cgi?id=583933](http://bugzilla.gnome.org/show_bug.cgi?id=583933)

As can be seen one is already fixed, the accessibility work is also progressing nicely and raof is working on gapless (why this is a blocker I have no idea, it doesn't seem like a feature we couldn't regress). Last night gabriel posted a new inotify patch.

I would say we are looking good, for those bugs listed as blockers and their swift progress is a testament to what we can expect from the Banshee team in the future in terms of fixing user problems. You also of course get the usual buttload of new features, for GSoC this year work is being done to allow metadata and music sharing using telepathy tubes, Mike Urbanski is working on Podcast as a Service support which looks amazing (along with his cool download manager). 

Banshee is doing good on all fronts.

---

### Post by Bou on 2009-07-04
> **gnomeuser said:**
> Mike Urbanski is working on Podcast as a Service support

Could you elaborate a bit? What's the difference with the current podcast support?

---

### Post by pt123 on 2009-07-04
> **zekopeko said:**
> You probably missed a part of thread title where it said Banshee.

Here, let me copy it for you, enlarge it and bold it for you.

**[SIZE="5"]Banshee 1.5.0 released![/SIZE]**


**[SIZE="5"]Maybe you missed the part where I was replying to another post in this thread regarding Mono![/SIZE]**

---

### Post by 23meg on 2009-07-04
I'm closing this thread. It's been a while since Banshee 1.5.0 was released, and the thread has gone beyond serving its purpose, which apparently was to share that news. Let's move on.

Mono performance issues can be discussed elsewhere (in this forum as well if they are directly relevant to Karmic) in a civil manner by presenting concrete technical data. Legal and ethical issues regarding Mono are known to be and can continue to be discussed in other places within and outside the forums, and there's [a thread dedicated to recurring anti-Mono sentiments]("http://ubuntuforums.org/showthread.php?t=1202591") at the Community Cafe forum.

---

