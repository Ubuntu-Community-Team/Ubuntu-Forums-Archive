---
title: "Intel video performance."
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by volanin on 2009-04-17
I installed Jaunty RC 64-bit today on my Macbook 2,1.

[b]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS,
943/940GML Express Integrated Graphics Controller (rev 03)[/b]

But the performance was awful.
With Intrepid I get 1200 FPS with glxgears and everything is smooth.
But with Jaunty, I could only get 300 FPS and the window movements were horrible.

I tried UXA, then Kernel 2.6.29 and 2.6.30, and disabling compiz.
Nothing worked at all.

Does anyone also has this problem?
Is there anything I have not tried?

For now, I reverted back to Intrepid, but I'd like to find a solution
since the Final version is out next week!
Thanks!
:)

---

### Post by simius on 2009-04-17
I have the same chipset and had the same problems. Got them fixed (everything working fluently, including Compiz and gnome-shell, almost no X crashes) with:

- kernel 2.6.30-020630rc2-generic
- xserver-xorg-video-intel version 2:2.6.99.1+git20090416.b9716b83-0ubuntu0tormod
- some git versions of other related packages, available somewhere on Launchpad
- these lines in /etc/X11/xorg.conf```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod" "exa"
        Option          "EXAOptimizeMigration" "true"
        Option          "MigrationHeuristics" "greedy"
EndSection
```I'm not sure where I got everything from, but you might google for the packages. But absolutely don't try these things if you don't want to break your system.

---

### Post by volanin on 2009-04-17
Thanks a lot for these pointers.
I am going to try them as soon as final is out!
:)

[QUOTE=simius]...almost no X crashes...[/QUOTE]
Oh man...!

---

### Post by FFuser on 2009-04-17
> **volanin said:**
> I installed Jaunty RC 64-bit today on my Macbook 2,1.

[b]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS,
943/940GML Express Integrated Graphics Controller (rev 03)[/b]

But the performance was awful.
With Intrepid I get 1200 FPS with glxgears and everything is smooth.
But with Jaunty, I could only get 300 FPS and the window movements were horrible.
...

For now, I reverted back to Intrepid, but I'd like to find a solution
since the Final version is out next week!
Thanks!
:)

Since I have exactly the same system as you I can confirm the problems.

As simius proposes installing kernel 2.6.30 and intel direver 2.6.99.1 improves the perfomance with an order of magnitude...

But I don't recommend it since that kernel does have some problems with sound and other issues. So you have 3 options

1: Stay with intrepid and wait for 9.10
2: Keep jaunty but with lower performance
3: Install new kernel and driver and expect a lot of problems
see this post: [http://ubuntuforums.org/showpost.php?p=7078838&postcount=22](http://ubuntuforums.org/showpost.php?p=7078838&postcount=22) for links to these newer packages.

---

### Post by volanin on 2009-04-17
Just curious:

Does the intel graphics in Jaunty with the new kernel and drivers
is/feels faster than the intel graphics in Intrepid?

---

### Post by mabovo on 2009-04-17
> **volanin said:**
> Just curious:

Does the intel graphics in Jaunty with the new kernel and drivers
is/feels faster than the intel graphics in Intrepid?

I have the same chipset on MacBook2,1 too.

My impression is that intel driver bug will be solved only with Karmic when kernel 2.6.30 is released.

For this time on MacBook2,1 is preferable using Intrepid than Jaunty.

---

### Post by psyke83 on 2009-04-17
> **simius said:**
> I have the same chipset and had the same problems. Got them fixed (everything working fluently, including Compiz and gnome-shell, almost no X crashes) with:

- kernel 2.6.30-020630rc2-generic
- xserver-xorg-video-intel version 2:2.6.99.1+git20090416.b9716b83-0ubuntu0tormod
- some git versions of other related packages, available somewhere on Launchpad
- these lines in /etc/X11/xorg.conf```

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod" "exa"
        Option          "EXAOptimizeMigration" "true"
        Option          "MigrationHeuristics" "greedy"
EndSection
```I'm not sure where I got everything from, but you might google for the packages. But absolutely don't try these things if you don't want to break your system.

It should be "MigrationHeuristic", not pluralized. The "greedy" heuristic is the only way to get good performance on my 855GM chipset (with exception to UXA + kernel 2.6.30-rc2).

---

### Post by psyke83 on 2009-04-17
> **volanin said:**
> 
With Intrepid I get 1200 FPS with glxgears and everything is smooth.
But with Jaunty, I could only get 300 FPS and the window movements were horrible.


I know that people are sick and tired of hearing this, but I'll repeat - glxgears is **not** an accurate benchmark tool. Why am I emphasising this so much?

In Hardy, I got approximately 1200fps in glxgears, and an average of 21fps in PlanetPenguin Racer.

In Jaunty (with UXA enabled, and the 2.6.30-rc2 testing kernel), I get 330fps in glxgears - horrible, right? However, I get an average of 26fps in PlanetPenguin Racer with the same settings as Hardy.

Let's all sing along... *glxgears is not a benchmark*....

---

### Post by mabovo on 2009-04-18
> **psyke83 said:**
> It should be "MigrationHeuristic", not pluralized. The "greedy" heuristic is the only way to get good performance on my 855GM chipset (with exception to UXA + kernel 2.6.30-rc2).

Thanks !

---

### Post by philinux on 2009-04-18
I'm using these settings.

```
Section "Device"
	Identifier	"Configured Video Device"
        Option          "AccelMethod""EXA"
        Option          "MigrationHeuristic""greedy"
        Option          "TripleBuffer""true"

```

I know glxgears is not a benchmark but even with these settings it was flickering but cube and effects ok. FPS about 900.

With latest updates flickering has gone. Yeah.....

---

### Post by binbash on 2009-04-18
I am getting 28xx fps >> [http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html](http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html)

---

### Post by Jim March on 2009-04-18
Um...are you sure we need to go all the way to (pre-release) kernel 2.6.30 to get results here?  2.6.29.1 is stable and has the kernel-level modesetting and other goodies for the Intel 945/965 chipsets.  2.6.30 just ain't done yet, right?  Why not stick with .29.1 for now?

---

### Post by cl333r on 2009-04-18
Almost all non-geeks newcommers are likely to just throw Jaunty in the trash can if they use intel video hw and they'll think that Ubuntu is so slow. I think it makes sense writing somewhere on the download page:
"Users of intel video hw are strongly encouraged to switch to a nvidia card" or so with perhaps more explanations at the bottom.
Just my 0.02 $

---

### Post by Jim March on 2009-04-18
When you have a laptop, "switching video cards" ain't easy.  Read: impossible.  And guess where Intel chipsets are most common?

Sigh.

In my case (965/x3100) it hasn't been too bad.  Slightly slower than Hardy but nothing really ugly.

---

### Post by olskar on 2009-04-18
> **cl333r said:**
> Almost all non-geeks newcommers are likely to just throw Jaunty in the trash can if they use intel video hw and they'll think that Ubuntu is so slow. I think it makes sense writing somewhere on the download page:
"Users of intel video hw are strongly encouraged to switch to a nvidia card" or so with perhaps more explanations at the bottom.
Just my 0.02 $

It says a bit about it in the releasenotes;

> Performance regressions on Intel graphics cards

Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases (bug 252094). Many of the issues have been resolved in Ubuntu 9.04, but some remain.

    *

      Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.
    *

      Alternatively, a new experimental acceleration architecture option, "DRI2/UXA", is available for Intel graphics users which our testing has found provides significant performance improvements in some cases, but has also shown risk of severe stability problems. You can opt-in to enable this by running "sudo gedit /etc/X11/xorg.conf", and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf. Users wishing to maximize stability should stay with the standard default acceleration method, "EXA".

      /!\ In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use sudo nano /etc/X11/xorg.conf to revert the UXA option.
    *

      If none of the above helps, some users reported success with using an older driver version. 

However I do think that this bug should have very high priority.

---

### Post by stewacide on 2009-04-19
The new drivers are a complete diaster on my 945 system. I couldn't get desktop effects to load (no hardware Open GL), and trying to play back video in any application crashed it instantly. Enabling UXA resulted in full-screen video corruption (dancing random colours) immediately upon boot.

Reverting to the old drivers solved all issues: [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by Taiebot65 on 2009-04-19
Me too my intel drivers are the only bad thing of this release ...
There should be a warning before normal users upgrade I will see a lots of bad comments resulting in those drivers...

---

### Post by olskar on 2009-04-19
> **Taiebot65 said:**
> Me too my intel drivers are the only bad thing of this release ...
There should be a warning before normal users upgrade I will see a lots of bad comments resulting in those drivers...

There is a warning in the Releasenotes

---

### Post by stewacide on 2009-04-19
BTW, does the new driver - for those who have it working - do anything to address the AWFUL h.264 performance in the non-free flash plugin?

edit -- OK it sounds like UXA would if it was working, so I am sympathetic to what the developers are trying to do here: framey YouTube playback is a deal-breaker for many people when considering Ubuntu/Linux.

Hopefully things get sorted out before release such that cards known to work get UXA, and everyone else gets the same Intrepid experience.

---

### Post by Taiebot65 on 2009-04-19
> There is a warning in the Releasenotes
__________________

I think this should be more like a warning that you are using intels driver and you could have regression.

My mum does not even know what is a graphic card

 we ve detected that your laptop is using intel drivers please note that many users during testing progress have noticed possible regressions would make more sense.... in a warning box

---

