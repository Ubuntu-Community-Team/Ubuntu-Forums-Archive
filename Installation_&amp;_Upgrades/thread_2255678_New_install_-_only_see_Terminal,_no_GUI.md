---
title: "New install - only see Terminal, no GUI"
date: 2014-12-06
forum: Installation &amp; Upgrades
---

### Post by amenex on 2014-12-06
The following message appears for ca. 1 second during bootup:
"via-ircc 0000:00:11.0: device not available (can't reserve [io 0x4000-0x407f]"

After that, Terminal appears. That's it. Terminal works, though.

The 'puter is a Compaq Presario 6000 with 500MB of RAM and a 320GB hard drive.
The monitor is a SyncMaster 2253BW.

The install was from a minimal Ubuntu 14.04.1 CD.
 I have hardwired Internet access via FIOS router.

StartX produces a small rectangular box with my username but it's frozen.

The video card hasn't been changed from the original Compaq installation.

Thanks,
George Langford (amenex for short)

---

### Post by Bashing-om on 2014-12-06
amenex; Hi !

Well, as a thought:
> 
The install was from a minimal Ubuntu 14.04.1 CD.


Did you install the "X" requirements ?
i.e.
```

sudo apt-get install xorg

```

What Desktop Environment did you install - and how ?

No Display Manager ( not required ) ?

[INDENT][INDENT]when all else fails, read the instructions
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-12-06
I hope you are not trying to install and use unity on that spec machine; 500MB ram will make it far too sluggish to be of any real use.  Even Lubuntu with the LXDE will be pretty slow, I think, but better than any other of the *ubuntu family.

---

### Post by amenex on 2014-12-06
> **Bashing-om said:**
> amenex; Hi !

Well, as a thought:

Did you install the "X" requirements ?
i.e.
```

sudo apt-get install xorg

```
 

Great result: After installing xorg, startx poduces a bigger frozen screen with my username
than the original frozen screen with my username..

> 
What Desktop Environment did you install - and how ?


Beats me. Ubunto was 'sposed to go ahead with a full install, but evidently hasn't.

That said, I installed Live Ubuntu in a laptop (which I'm using right now) on a USB stick, and 
that's been working perfectly from the get-go (as described in another thread). The GUI came
 along with that installation as a matter of course.

> 
No Display Manager ( not required ) ?


Beats me. I had what appeared to be a choice of many "features" during installation, and
as soon as I clicked on one, the install went ahead with what it was gonna do anyway,
and I never saw that screen again. Most other installations let one pick one _or more_ of
such "features."

If I could get that USB stick to work in the Compaq, I'd try that in an instant, but the
Compaq's USB ports don't like it, even though I can select "USB HDD" in the BIOS
boot order setup.  The instructions for correcting that situation contain the word,
"ordeal" as part of the solution.

George

---

### Post by Bashing-om on 2014-12-06
amenex; Welp;

Let's back up to square 1.

IF this is indeed the "minimal CD" that you have as the install medium, then what gets installed is a bare bones operating system, A core install that will boot the operating system to a terminal, and have networking. And that my friend is ALL.
Beautiful way to "roll your own" and still be in the ubuntu family. It is expected that you know what you want installed onto this bare bones system.

Let's see if 500MB of ram is good enough to support the light weight desktop 'xfce4' - No guarantee at all here.
```

sudo apt-get install xfce4

```

To now start your xfce4 GUI desktop:
Booted to terminal, issue terminal code :
```

startxfce4

```

[INDENT][INDENT]and your adventure begins
[INDENT][INDENT][INDENT][INDENT]system administration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by amenex on 2014-12-06
More progress. I rounded up another DVD burner (the USB variety) and ran the full install of Ubuntu.

Sure enough, that same cryptic message appeared that I quoted at the beginning of this thread. Only
this time it was in bigger type, and orange, and way back at the beginning of the bootup.

The Live DVD installation went on ... interminably slowly, but then another message appeared,
to the effect that an unrecoverable error had occured. The installation continued anyway, until
I was given the opportunity to view the details of the error.  After an even more interminable
wait accompanied by a great deal of DVD drive activity, the details finally appeared:

> Ubiquity has crashed with signal 7 in FT_Load_Glyph(). It's ubiquity 2.18.8 [origin unknown].
A.K.A. 2.14.1-Oubuntu3.2 ... This is not an official Ubuntu package. Please remove any third
party package and try again.

I sent the error report to on high.  I hope to see a cc soon at my email address ...

But the full GUI is here now. The USB DVD drive is slower than you could possibly imagine.

I'm waiting to see if Netscape will start. ... after about ten minutes, a partial tab has appeared ... Not
surprisingly, a warning popup appeared to the effect that an unresponsive script was running ... but
that, too, remains incompletely loaded into the GUI ...

It wasn't the minimal install CD after all, now was it ?

This Compaq 'puter bears a decal that says it was made for Windows XP; it worked OK until it contracted 
an incurable virus that ESET Security couldn't fix..  The infected HDD has long been been destroyed.

Once I see my Internet connection via Netscape, I'll see if I can access Terminal.

All the best,
George

---

### Post by Bashing-om on 2014-12-06
amenex; Oh No !

You ain't got the hosses to run "ubuntu" .

[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)

For a descent experience with "ubuntu" requires at least 2 Gigs of ram .

[INDENT][INDENT]it be the flag ship edition.
[/INDENT][/INDENT]

---

### Post by amenex on 2014-12-07
Progress: It would appear (to no one's surprise) that there isn't enough memory for the 
Live Ubuntu installation to work usefully. See this bug report:
>  [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961) 

I'll get more RAM and continue. The bug report above reveals the cause of the Ubiquity
crash as insufficient memory.

I could not get terminal to run once things settled down overnight. The search function
says it couldn't find terminal anywhere, so I couldn't read the boot message logs.

I was able to mount my NAS and the internal hard drive was also mounted and accessible.

So the installation DVD worked, and the ubiquity crash wasn't a deal killer.

I'm hoping that I can get two 1GB memory modules; I see ambiguous results for the
maximum RAM that the Compaq 6430NX allows; it's either 1GB or 2GB.

Thanks for your help.

George

---

### Post by Bashing-om on 2014-12-07
amenex; Hello;

Doing your homework is a good thing !
Here is another thought.

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.

Which may run acceptably on that hardware. But, more ram would sure be better.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

