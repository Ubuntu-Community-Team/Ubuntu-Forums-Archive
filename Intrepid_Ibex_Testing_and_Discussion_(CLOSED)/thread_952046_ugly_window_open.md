---
title: "ugly window open"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by myddewji13 on 2008-10-18
Hi,

recently installed intrepid and its running great. One comlaint I have is that every time i open an application i get a smear of colors on an empty window for abt 2 sec before the app opens. (see attached) any ideas how to fix this?

---

### Post by anhvu2875 on 2008-10-18
i got the same prob !

---

### Post by myddewji13 on 2008-10-18
found an easy workaround/fix...open up CCSM and hit animations ... under the open animation tab... change from glide 1 to another animation (i chose glide 2) ...opens up a lot cleaner ...

---

### Post by myddewji13 on 2008-10-18
looks like i spoke too soon..it kinda works...like 50% of the time...after u increase the animation delay to 450... anyone got a fix :(

---

### Post by ktp on 2008-10-18
I have been trying to find a good solution to this issue for a while now.

---

### Post by FuturePilot on 2008-10-18
Does everyone having this problem have a Nvidia card?

---

### Post by miwaypet on 2008-10-18
I have the intel 915 chipset with built in graphics, and also have this problem. And there is still some screen flicker as well.

---

### Post by anhvu2875 on 2008-10-19
there is still no solution ?

---

### Post by Aries K on 2008-10-19
Hi, I have a similar problem except on mine when you hover over the top window border on non-fullscreen windows it whites out like this. It will do this on any theme, even the default.

[[IMG]http://img134.imageshack.us/img134/8289/screenshotgb4.th.png[/IMG]](http://img134.imageshack.us/my.php?image=screenshotgb4.png)[[IMG]http://img134.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by mdurham on 2008-10-19
I have nvidia & have very similar problem. It looks like a TV that needs it's horizontal hold adjusting (do they do that anymore?). I also had this problem in Hardy with an older nvidia card.

---

### Post by OutOfReach on 2008-10-19
I have an Intel Integrated graphics and I have this problem too, I see it usually happen when opening Firefox.

---

### Post by xakarix84 on 2008-10-19
intel graphic processor here,
i have this problem in ubuntu 8.10 , kubuntu 8.04 kde4,
but everything fine in ubuntu 8.04 , kubuntu 8.04 kde3.

---

### Post by | MM | on 2008-10-19
nvidia, and i have this problem as well.

---

### Post by anhvu2875 on 2008-10-19
well well , there are many people got the same prob and without solution .

---

### Post by lonniehenry on 2008-10-19
Setting animations to none in ccsm will at least leave the background the same until the page comes up in ff.  Not a solution but better than seeing the ugliness.

---

### Post by philinux on 2008-10-19
Had this issue since April on new pc. I think it's a compiz bug. Or compiz/graphics card clash.

---

### Post by anhvu2875 on 2008-10-19
yes , it looks better after switching off animation effect in compiz !

---

### Post by PC_load_letter on 2008-10-20
I haven't installed Ibex yet, but I have this exact same problem on my Dell Vostro 1400 with Nvidia GeForce 8400GS running Ubuntu 8.04 64bit.

---

### Post by myddewji13 on 2008-10-20
integrated intel here...sorry i didnt mention it...anyways...lots of people have the problem...anyone have a solution?

---

### Post by philinux on 2008-10-20
Found my old thread with my screen print, which was hard to get as it's just so random.

[http://ubuntuforums.org/showthread.php?t=845171](http://ubuntuforums.org/showthread.php?t=845171)

Anyway last post says could it be related to cpu freq scaling.

---

### Post by myddewji13 on 2008-10-20
if i disable frequency scaling and set it to performance the problems solved... kinda dumb though..im not going to set it to max performance just so it looks prettier...although... does anyone know how to automatically go into performance mode once my laptops on ac power? (right now i have to manually switch from the cpu freq scaling applet on gnome)

---

### Post by myddewji13 on 2008-10-20
i found the following:

To change these default values you need to open up the gconf-editor. To do that press Alt+F2 and type
gconf-editor into the run dialog. Now navigate to apps>gnome-power-manger>cpufreq. Here you can change the value of policy_ac and policy_battery to whichever governor you wish to be default for AC power and battery.

from: [http://ubuntuforums.org/showthread.php?t=597998&highlight=cpu+freq+scaling](http://ubuntuforums.org/showthread.php?t=597998&highlight=cpu+freq+scaling)

but the cpufreq option in gconf doesnt exist...any ideas?

---

### Post by philinux on 2008-10-20
I'm on a desktop and looking at the cpu scaling monitor they idle at 1gig and jump up to 2.7gig as soon as a I say launch firefox. So after that test i dont think thats my problem.

---

### Post by myddewji13 on 2008-10-20
> **philinux said:**
> I'm on a desktop and looking at the cpu scaling monitor they idle at 1gig and jump up to 2.7gig as soon as a I say launch firefox. So after that test i dont think thats my problem.

either your looking at ram/swap or you have the wrong units...cpu frequency is usually measured in MHz

---

### Post by philinux on 2008-10-20
Mega Hz since when years ago.. No I'm talking  GHz
See top panel.

---

### Post by Hatfield on 2008-10-20
Nvidia 7600GT(version 177 proprietary driver) here with the same problem.  Noticed it mostly opening OpenOffice, but have noticed it recently with Firefox.
Then earlier today, my screen froze on this "scrambled" effect.  Had Firefox(minimized), Konsole(minimized), and OpenOffice open.  Closed OpenOffice and my Desktop and Plasmoid went scambled and only changed to normal when I moved the cursor over them.  Closed Firefox too and the problem went away.  Haven't had it since.

Also noticed that when I have OpenOffice open, parts of my taskbar disappear when I move my cursor over it.  It is doing that now as I type this.  Close OpenOffice and the problem goes away.

---

### Post by myddewji13 on 2008-10-20
lol..ur right...my bad

---

### Post by Aries K on 2008-10-20
> **Aries K said:**
> Hi, I have a similar problem except on mine when you hover over the top window border on non-fullscreen windows it whites out like this. It will do this on any theme, even the default.

[[IMG]http://img134.imageshack.us/img134/8289/screenshotgb4.th.png[/IMG]](http://img134.imageshack.us/my.php?image=screenshotgb4.png)[[IMG]http://img134.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Anyone else have this problem I mentioned earlier? Is there a way to fix it so when I hover over window borders they do not blank out like in the picture posted? Thanks again.

EDIT: This also happens when a window is overlapped by another window as well.

---

### Post by myddewji13 on 2008-10-22
you could try using emerald...see what happens ..

---

### Post by Aries K on 2008-10-22
> **myddewji13 said:**
> you could try using emerald...see what happens ..

How do I do that? Thanks for your response.

---

### Post by myddewji13 on 2008-10-22
first install:

```
sudo apt-get install emerald
```

then to run:

```
emerald --replace
```

and if you like it open up ccsm and under window decoration in the command section type in emerald --replace

---

### Post by Aries K on 2008-10-23
> **myddewji13 said:**
> first install:

```
sudo apt-get install emerald
```

then to run:

```
emerald --replace
```

and if you like it open up ccsm and under window decoration in the command section type in emerald --replace

Thanks that fixed my problem. Emerald is pretty sweet, I like the themes. :guitar:

---

### Post by mdurham on 2008-10-24
> **myddewji13 said:**
> first install:

```
sudo apt-get install emerald
```

then to run:

```
emerald --replace
```

and if you like it open up ccsm and under window decoration in the command section type in emerald --replace

Thanks myddewji13, that's a lot better. Where do you get the themes from?
Cheers, Mike

---

### Post by Aries K on 2008-10-24
> **mdurham said:**
> Thanks myddewji13, that's a lot better. Where do you get the themes from?
Cheers, Mike

Themes are from [www.gnome-look.org](www.gnome-look.org) under the Beryl section. Enjoy.

---

### Post by myddewji13 on 2008-10-24
ur welcome and thanks aries k ... but anyone have a solution to the initial problem?!??!?!

---

### Post by caryb on 2008-10-24
I have the same problem but I think you are looking too high up the food change for a fix! I don't use Compiz, I use Metacity with KDE4 with the same problem. It only happens with enhanced graphics enabled.

Based on this I think we can deduce that 
a) its not a Compiz problem
b) its not a specific chipset problem
c) its not only Gnome (Ubuntu) but it's in KDE4 (Kubuntu)

I believe this could be at the Xorg level.


2c Cary

---

### Post by myddewji13 on 2008-10-27
bump...so what do i do?

---

### Post by myddewji13 on 2008-10-29
bump :(

---

### Post by snake444 on 2008-10-29
> **Aries K said:**
> Hi, I have a similar problem except on mine when you hover over the top window border on non-fullscreen windows it whites out like this. It will do this on any theme, even the default.

[[IMG]http://img134.imageshack.us/img134/8289/screenshotgb4.th.png[/IMG]](http://img134.imageshack.us/my.php?image=screenshotgb4.png)[[IMG]http://img134.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

i have the same problem.
in fresh hardy install it wasnt, only after updating to ibex it started to be.

also i havent this in 7.04 fresh install but after upgrading to 7.10 it started to be

my solution was every time to do is fresh install.

---

### Post by myddewji13 on 2008-10-29
I fresh installed intrepid three days ago...and that didn't fix the problem...:(

---

