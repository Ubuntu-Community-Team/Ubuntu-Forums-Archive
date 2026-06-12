---
title: "How is 64 bit these days?"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2010-02-11
I'm FINALLY thinking of moving over to 64 bit & am wondering how it's looking these days---any issues/work-arounds/thoughts anyone have?

---

### Post by Roasted on 2010-02-11
I've used 64 bit for about 2 years now, and haven't found any issues yet.

---

### Post by Merk42 on 2010-02-11
I can't get ZSNES from the repos since it doesn't have a 64bit build.

Other than that, not a single problem and I've been running 64bit back when I only had 1GB of RAM.

---

### Post by philinux on 2010-02-11
> **autocrosser said:**
> I'm FINALLY thinking of moving over to 64 bit & am wondering how it's looking these days---any issues/work-arounds/thoughts anyone have?

Got 64 bit karmic on one drive with 64 bit lucid on the other.

Not a single issue here apart from flash. The 64 bit flash plugin is the one to use. Restricted extras installs the 32 bit version.

---

### Post by leech on 2010-02-11
Which is retarded, since the Debian Sid package has been downloading the 64bit Flash plugin for a long time now, and Ubuntu supposedly synchronizes with Debian Sid.... 

But if you just install the deb package from them, you don't need the nspluginwrapper and all that crap, and it works great.

Leech

---

### Post by SalvoMaltese on 2010-02-11
No problems here on 64bit Kubuntu lucid. (Apart of flash, as stated).

---

### Post by doas777 on 2010-02-11
pretty good. the only issues i've had were trying to get game emu's (pcsx2 for instance) to compile correctly, since some of the depends are 32bit only. largely the nvidia toolkit.

---

### Post by Funnnny on 2010-02-11
Installed 64bit since Jaunty and it ran fine.
only 3 problems, 1 is flash ( but I don't use flash anyway, just block it ).
2 is Pcsx2, I do testing and some little coing in Pcsx2, and it need a 32bit system, a chroot is accepted
3 is codec, I once met some problem with codec, and managed to solve it...
Other than that, I've never had any problem

---

### Post by mannheim on 2010-02-11
Although the native 64-bit flash plugin works better than the 32-bit one in most situations (on a 64-bit install), it does have bugs. The only one that I've come across is that the 64-bit plugin doesn't work with Amazon's video-on-demand site.

So sometimes using the 32 bit flash plugin is the best compromise.

---

### Post by Slug71 on 2010-02-11
Hey autocrosser,
Ive been using 64bit since Intrepid i think and its been going very well since then. 64bit flash works great too. I think i usually have the 32bit libs installed anyway as i think it gets dragged in with Java. But goes well. Give it a whirl for sure.

---

### Post by zika on 2010-02-11
> **Slug71 said:**
> Hey autocrosser,
Ive been using 64bit since Intrepid i think and its been going very well since then. 64bit flash works great too. I think i usually have the 32bit libs installed anyway as i think it gets dragged in with Java. But goes well. Give it a whirl for sure.If You use Java from 64-bit plugin Sun site, then You could make a totally 64-bit OS... I think I did...

---

### Post by walkerk on 2010-02-11
Same story with sidux. 64bit is running without issues...

---

### Post by Sophont on 2010-02-11
I have 64 bit running on my Studio XPS 16 for a few months now (started around Beta 5 of Karmic Koala).
Zero problems. Compiz, Flash, etc... everything works.

---

### Post by cariboo on 2010-02-11
The only problem I've run into in the last couple of years, is with windows only wireless devices, most 64-bit windows drivers don't work with ndiswrapper.

---

### Post by xebian on 2010-02-11
Been using 64bit since Edgy and never looked back.

---

### Post by autocrosser on 2010-02-11
Sounds good--I'm re-arranging my box in the next couple of days (have a hot-swap unit & a WD black 750G coming)--so it sounds like a great time to do some "spring-cleaning" & have wanted to move to BOINC-64 for some time now......

---

### Post by nrs on 2010-02-11
I don't know if it's the case in Ubuntu, but for me in Arch, 64 bit flash is capable of bringing my system to its knees when you try to watch something in fullscreen and move the mouse. I don't have the problem with 32 bit flash. A problem I do have with 64 bit flash in Ubuntu is sometimes all there is a white box, and I have to restart Firefox.

---

### Post by Merk42 on 2010-02-11
> **nrs said:**
> ...flash is capable of bringing my system to its knees when you try to watch something in fullscreen and move the mouse....

That is the case with pretty much any non Windows OS, Mac included. Flash is coded horribly.

---

### Post by el_itur on 2010-02-12
I've found the flash performance pretty much "good enough" for what I've asked it to do: online video.

I'm just a casual flash games player, and that is my main annoyance, although I think it's more due to bad flash developers than to bad plugin performance.

Anyway, the issues with a pure 64bit system aren't that bad these days and those that araise are fun to fix :D .

Give away the fear and join the 64bit bandwagon :D :D

---

### Post by nrs on 2010-02-12
> **Merk42 said:**
> That is the case with pretty much any non Windows OS, Mac included. Flash is coded horribly.
I agree the performance isn't as great as Windows, but like I said, I don't have this problem when using 32bit Flash in Arch. It's still slower, but not UNGH slow. My mouse doesn't pause and then fly to the other end of the screen.

---

### Post by autocrosser on 2010-02-12
No fear---just lazy--been meaning to move for the last couple of testing cycles--but 32 is the old familiar---so I've taken the low-energy way......this time is boring enough that it looks like a good one to change my comfort-zone. :D

---

### Post by bronquel on 2010-02-12
Go for it!  flash was the only concern i had, it seemed to use a lot of my CPU...  I suppose we would need to know what you use your computer for and we could give you a more specific answer...  For the most part I haven't noticed a huge difference between 32 and 64.

---

### Post by autocrosser on 2010-02-12
I use it for day-to-day & testing use.....I don't think I'll have too much problem "pushing" the system with flash.

My system? Gigabyte X58 (UD4P) with a i7-940 running @ 3.7 with 6G of G.Skill DDR3-2000 memory & with the new WD 750G I'll be pushing 2TB of drive space---no help needed--thanks though--been here from before Dapper drake in the testing group--just was seeing how 64 looked these days....

After the re-sort I'll have 6 total OS installs--the rest will still be 32bit--I'll change things a "bit" at a time......

---

### Post by ranch hand on 2010-02-12
I have never used Ubuntu on anything but 64 but have had 32 bit install on it and I can tell you that the 64 bit stuff runs better unless I turn off half my cpus.

Don't use flash much but never really had any problems when I did (do).

boinc runs like a scalded cat.

---

### Post by SevenMachines on 2010-02-12
> **ranch hand said:**
> boinc runs like a scalded cat.
:)

 I've probably been using amd64 distribution for a year or two now, never have any problems apart from 32 bit only binary blobs (but i rarely have any inclination to use them), although the 32 bit emulation has improved a great deal and often this isnt a problem anymore. as mentioned previously, you'll probably want 64 bit flash though, its completely stable for me although some 64 bit users get problems and prefer the 32 bit nsplugin version

---

### Post by rasmus91 on 2010-02-12
> I'm FINALLY thinking of moving over to 64 bit & am wondering how it's looking these days---any issues/work-arounds/thoughts anyone have?

64 bit is sweet... You'll need to download the 32 bit libs, but i think thats pretty much it.

For me it works great, and i aint got much to complain about.

---

### Post by Kilz on 2010-02-12
The state of 64bit is so good, [the 64bit section of the forum was closed because its mature. ]("http://ubuntuforums.org/announcement.php?f=343")

---

### Post by kellemes on 2010-02-12
64bit running perfect for me..

---

### Post by Dougie187 on 2010-02-12
> **Merk42 said:**
> I can't get ZSNES from the repos since it doesn't have a 64bit build.

Other than that, not a single problem and I've been running 64bit back when I only had 1GB of RAM.

You can use this repo for ZSNES for 64 bit.

I just use the hardy version still (on karmic). I don't know if the karmic repo has ZSNES in it.

[http://www.tolaris.com/apt-repository/](http://www.tolaris.com/apt-repository/)

---

### Post by Seventh Reign on 2010-02-12
64 bit is rockin.  Like pretty much everyone else here, my only issue is Flash.   I've never experienced any crashes, but getting flash to work with Swiftfox, Firefox 3.7a2 and Chrome has proven to be a pain.  Firefox 3.5 and 3.6 are flawless.

---

### Post by FrancoNero on 2010-02-12
also using 64bit and it's the way to go. Adobe is a bit lazy with updating their 64bit plugin (and it's horribly cpu-intensive in fullsscreen etc, e.g. youtube) but it works with hardly any problem

---

