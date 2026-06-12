---
title: "Gnome Shell"
date: 2009-05-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by panaut0lordv on 2009-05-06
What is going to bring?
When will be uploaded?
Do you expect major breakage?

Say what you think.

---

### Post by autocrosser on 2009-05-06
You can build & test Gnome3 right now--it changes the desktop experience in several ways--some I really like---some I don't. 

I have been active in testing Gnome3 & "as of this moment", the build is stable with no real breakage......

More info including building it:  [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

If you want to follow it, get an account on bugzilla--the project is under the "other" projects area & build/run it--report bugs & check it out for yourself...

As you started the thread I was thinking about---I'll post my thoughts & build notes here from time to time...the project has gone a fair ways in a short time...as for inclusion in Karmic-----I don't think so. My guess it will land square in our next LTS release--so I'm betting we really don't see it until 10.10 :(

There is "going" to be a "choice" in gnome to run 2 or 3---I'm going with 3 as soon as I can.

---

### Post by taavikko on 2009-05-06
> **autocrosser said:**
> ...the project has gone a fair ways in a short time...as for inclusion in Karmic-----I don't think so. My guess it will land square in our next LTS release--so I'm betting we really don't see it until 10.10 :(

There is "going" to be a "choice" in gnome to run 2 or 3---I'm going with 3 as soon as I can.

There's been some talk delaying LTS release to 10.10, makes me think that it's due to Gnome3, If landing during 10.04 would make sense to sort out the issues before releasing LTS
[http://www.markshuttleworth.com/archives/288](http://www.markshuttleworth.com/archives/288)


As for autocrosser, have you noticed any serious improvements, other than visual.

---

### Post by autocrosser on 2009-05-06
There have been some usability improvements--I just built tonight with the commits from the last 24 hrs & ran into a large crasher bug---I'm running the newest nVidia driver 185.18.08 & with tonights build I get a fast Xserver crash back to GDM--this did not happen with 185.18.04

Was bugreport time for me ;(

As soon as its runnable again, I'll post the new stuff---I really wanted to test this build--tabbing was coming in.....

I'm going to see if it will run on my laptop--will post in a bit.....will take longer to build it ---1.2GHZ Thinkpad :(

---

### Post by gnomeuser on 2009-05-06
I have to admit I am still not sold on the idea of the GNOME shell, I am fundamentally not sure that workspace management is the primary concern on the desktop today. This however is one of the top level problems handled by GNOME Shell.

I am skeptical of the sanity involved in selecting Javascript as the language to do development for GNOME 3.

The more I think about it, the less I believe that the GNOME shell is the right way ahead. On the whole I wonder why the ideas brewed upon in the Online Desktop were dropped wholesale.

I don't think it is fundamentally improving our computing experience, there were so many more interesting ideas being bandied about and this is the target.

Additionally I am concerned that for cycle after cycle we put limits on accepting things like webkit, yet javascript bridges, a new windowing manager (mutter - not entirely new granted) and a whole new desktop concept is accepted hardly without debate. 

Under the helmet though I am very excited about GNOME 3.0. Many needed cleanups and a set of clear guidelines for moving forward. Getting geolocation and communications solidly integrated really makes for exciting prospects.

---

### Post by taavikko on 2009-05-06
Tried to run a quick test, but my HD3450 radeon didn't like it.
Xephyr froze and --replace consisted with artifacts and tearing, so not a pleasent first run...

Screencast reminds me little too much of UNR, which in larger scale isn't too usable, IMO. but I'll wait for the release before forming opinion of it.
Not much worth speculating on current state.

---

### Post by adredz on 2009-05-06
Built succesfully... I thought there would be no bottom panel anymore. I was disgusted when I saw it. I don't like the menu too-- too big and space consuming. But I really like the very smooth animation when adding worskpaces and managing windows...

---

### Post by Merk42 on 2009-05-06
It'd be nice if this early on GNOME asked people **completely unfamiliar with GNOME and/or Linux** what would be an intuitive interface.  What sort of usability features **they** would want.  Linux needs to get out of the *by* programmers *for* programmers stigma.

---

### Post by gnomeuser on 2009-05-06
> **Merk42 said:**
> It'd be nice if this early on GNOME asked people **completely unfamiliar with GNOME and/or Linux** what would be an intuitive interface.  What sort of usability features **they** would want.  Linux needs to get out of the *by* programmers *for* programmers stigma.

BetterDesktop.org :) Aside that Sun has invested millions of hours teaching the existing GNOME developer base about usability and accessability during the development of the 2.x series.

It is not as if we don't know how to do the work, it just seems that this gnome-shell thing was designed at a hackfest where only developers attended, the design was not sufficiently exposed to the real world. There are some good ideas but also some really bad ones.

---

### Post by autocrosser on 2009-05-06
Yes---but at the same time I (a experienced Gnome user) have had contact with the developers & it was a (shock!!) good interchange of thoughts/ideas....I would say that this is the first time I have talked to a Gnome Dev & came away feeling good about it....

They "seem" more open than I am use to...so I am hopeful that this can be made into something workable.


On another note: I tried to build it on my old faithful 1.2GHZ Thinkpad--was a grinding, drawn out experience to watch it...I promptly removed & wait til I hear that the bug I uncovered last night gets resolved......

There is discussion in the list about "really" running a 3D desktop--will be interesting to see how that plays out...............

---

### Post by Starks on 2009-05-06
How do I build Gnome 3?

---

### Post by taavikko on 2009-05-06
> **Starks said:**
> How do I build Gnome 3?

[http://live.gnome.org/GnomeShell#building](http://live.gnome.org/GnomeShell#building)

You need to install few packages in the process also but you'll get it ;)

---

### Post by Starks on 2009-05-06
What are the build dependencies?

---

### Post by ronacc on 2009-05-06
the script on that page will pull in most  of the build deps and as you go through the process it will ask for what it needs .

---

### Post by Starks on 2009-05-06
I just got gnome-shell to compile, and I must say this: It's quite sexy.

---

### Post by gjoellee on 2009-05-06
Fail building clutter:

```
0.9.o']' returned non-zero exit status 1
make[6]: *** [Cogl-0.9.gir] Error 1
make[5]: *** [all-recursive] Error 1
make[4]: *** [all] Error 2
make[3]: *** [all-recursive] Error 1
make[2]: *** [all] Error 2
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** error during stage build of clutter: ########## Error running make   *** [3/6]


  [1] rerun stage build
  [2] ignore error and continue to install
  [3] give up on module
  [4] start shell
  [5] go to stage force_checkout
  [6] go to stage configure
choice:
```

which option or potential fix

---

### Post by Starks on 2009-05-06
I ran into that problem about an hour ago. I solved it by compiling clutter separately and using /usr as the installation prefix.

```
git clone git://[git.clutter-project.org/clutter]("http://git.clutter-project.org/clutter")
cd clutter
./autogen.sh --prefix=/usr
make
sudo make install

```Be sure to run "jhbuild build -f -a -c" after compiling clutter from wherever you are running jhbuild from in order to reset the installation of gnome-shell.

---

### Post by gjoellee on 2009-05-06
> **Starks said:**
> I ran into that problem about an hour ago. I solved it by compiling clutter separately and using /usr as the installation prefix.

```
git clone git://[git.clutter-project.org/clutter]("http://git.clutter-project.org/clutter")
cd clutter
./autogen.sh --prefix=/usr
make
sudo make install

```Be sure to run "jhbuild build -f -a -c" after compiling clutter from wherever you are running jhbuild from in order to reset the installation of gnome-shell.

Thanks...Oh, GNOME 3 already looks good....and sooo smooth effects!

---

### Post by autocrosser on 2009-05-06
Yes--looking better than it did about a month ago---the wallpaper background in the menu mode was very new.......

---

### Post by super.rad on 2009-05-06
Just tried building but it's completely unusable for me, tried running it nested and replacing the panel. When replacing the panel the whole desktop turned black, eventually the top panel loaded but when I click activities everything freezes up until the side bar opens (when it opens the top panel goes weird with white bits everywhere) and then it pretty much freezes, pressing Ctrl+C does nothing and I had to hit the reset button.
When I tried it nested clicking activities opened the side bar about 2cm and then all froze up again.

---

### Post by autocrosser on 2009-05-06
Ya--nested never worked for me--it would normally bomb out---the note for running it nested states: "This requires a relatively recent version of Xephyr with GLX support to be installed on your system"   So, if you don't have xepher installed it will bomb very quickly....It runs very nice as a replacement---just remember to keep the term you started the shell with open or minimized---you need to be in that term to shut the shell down gracefully....

---

### Post by ronacc on 2009-05-06
I've got it up and running , just 2 questions , how do I reduce the size of the top bar and how do I get rid of the bottom pannel ?

---

### Post by adredz on 2009-05-06
> **ronacc said:**
> I've got it up and running , just 2 questions , how do I reduce the size of the top bar and how do I get rid of the bottom pannel ?

Where would the tasks be placed if there would be no bottom panel? I've been asking this until I built gnome 3 myself. I guessed it right, there's still a bottom panel since applets are not allowed in the top panel. Well, I don't like it so far... The only thing I like is the smooth animation. :) but I know it's too early to tell...

---

### Post by autocrosser on 2009-05-06
> **ronacc said:**
> I've got it up and running , just 2 questions , how do I reduce the size of the top bar and how do I get rid of the bottom pannel ?


Greetings!!!

there are pref files in /gnome-shell/install/share/gnome-shell/js/ui--you need to modify appDisplay.js & panel.js---both are in plain language, so are easy to edit---just follow the syntax & you will do fine...take a look at the ones I have changed.....mod_info.tar

You also will need to change your start path---I use:

```
cd '/home/dean/gnome-shell/install/bin' 
./gnome-shell --replace

```

Beware---sometimes the devs break this path--I do a bug report when this happens---you can look at the current commits (the newest was in response to my last bug report)---I also would bookmark the commits page (the link is on the main Gnome-Shell page)--you will need it to see if things will break on a build that day.........

---

### Post by BGFG on 2009-05-06
> **gnomeuser said:**
> 

I am skeptical of the sanity involved in selecting Javascript as the language to do development for GNOME 3.


After reading a bit and coming across the fact that Sun has actually training sessions with the Gnome dev team in terms of usability and desktop experience and the fact Gnome seems to be the flagship DE for Opensolaris it isn't not a shock to me that Gnome has gone javascript. With the hard push that Sun is making into the OS environment when i heard that javascript was going to be the language used involvement with Sun immediately came to mind, nothing shady mind you!:) this is not some 'conspiracy theory' post. It just made sense to me.

Edit: mistakenly thought java and javascript were both sun products.

---

### Post by ronacc on 2009-05-06
@ autocrosser thanks for the info .

---

### Post by adult swim on 2009-05-06
has anyone else crashed it yet by pressing the big + in the bottom right corner trying to see how many desktops you can add?  im excited to see where this is going to go, there seems to be some nice features in the works.

---

### Post by autocrosser on 2009-05-06
> **ronacc said:**
> @ autocrosser thanks for the info .

No sweat---have fun changing it---just don't push it too far--it will blow-up on you....


THIS MESSAGE WILL SELF_DESTRUCT IN 10 SECONDS....9.....8.....7

---

### Post by Merk42 on 2009-05-06
Is it possible to test this in a VM? I'd like to poke around with it but afraid of the ramifications.

I'm in KDE 4.2 right now checking that out.

I wish stuff like freedesktop.org or other inputs were publicized better.  GNOME (and KDE, and xcfe, etc) needs the input of Joe User.  Of course by the time GNOME 3 comes out, Joe User will be using Windows 7 anyway. :(

---

### Post by frustphil on 2009-05-07
[quote=autocrosser;7229048]

```
cd '/home/dean/gnome-shell/install/bin' 
./gnome-shell --replace

```

It doesn't work for me. It fails when it tries to switch to gnome-shell...

---

### Post by autocrosser on 2009-05-07
Problem would be accelerated desktop in a VM....It runs like a sloth in a non-accelerated desktop...real fluid otherwise....

---

### Post by autocrosser on 2009-05-07
Sorry---you need to put in your home address instead of mine.....

```
cd '/home/*your_name*/gnome-shell/install/bin' 

```

or you can nav to the location & click/run it.....Only use this way if you are modding the .js files---if you are just demo-ing the shell, use the info on the page I linked earlier.....

---

### Post by frustphil on 2009-05-07
> **autocrosser said:**
> Sorry---you need to put in your home address instead of mine.....

```
cd '/home/*your_name*/gnome-shell/install/bin' 

```or you can nav to the location & click/run it.....Only use this way if you are modding the .js files---if you are just demo-ing the shell, use the info on the page I linked earlier.....

Yup, I changed the home address to mine.
I downloaded your mod files, removed the .bak part, and replaced the original files in the said location. Then cd '/home/my_name/gnome-shell/install/bin' and ./gnome-shell --replace... But it failed...

---

### Post by autocrosser on 2009-05-07
The mod files are for example only---you need to look at them as a guideline to mod yours how you want....If you want, I'll set-up a current file set--those ones I use for reference--reason is that all the files in your install will be over-written each time you do a new build...that's why the ones you got have .bak at the end---they won't be over-written & you can re-mod the current files---they are constantly changing & the one you use one day may not be usable the next :)

At this stage of development--everything can be up in the air---wait a minute--it'll change;)

---

### Post by plun on 2009-05-07
The "damned" bottom panel.....:)

Where do I block it ????

panel.js
[http://paste.ubuntu.com/165909/](http://paste.ubuntu.com/165909/)


My lazy start-script....

```
#!/bin/bash

cd ~/gnome-shell/source/gnome-shell/src

./gnome-shell --replace


```

---

### Post by autocrosser on 2009-05-07
Sorry my friend---as I have heard it--right now the lower panel is hard-coded--I'm not sure you can get rid of it........I'll really look at the panel.js this weekend to verify that...

---

### Post by plun on 2009-05-07
> **autocrosser said:**
> Sorry my friend---as I have heard it--right now the lower panel is hard-coded--I'm not sure you can get rid of it........I'll really look at the panel.js this weekend to verify that...

OK, thanks ... the same as for a month ago...

Nevertheless I upgraded Gnome-shell this morning and it seg faults with a hard logout...:---)

It maybe has something todo with compiz because its really unstable for the moment,   Compiz to Metacity switch.

---

### Post by Incognito-Here on 2009-05-07
> After reading a bit and coming across the fact that Sun has actually training sessions with the Gnome dev team in terms of usability and desktop experience and the fact Gnome seems to be the flagship DE for Opensolaris it isn't not a shock to me that Gnome has gone javascript. With the hard push that Sun is making into the OS environment when i heard that javascript was going to be the language used involvement with Sun immediately came to mind, nothing shady mind you! this is not some 'conspiracy theory' post. It just made sense to me.

I think that the gnome shell will be an amazing experience on OpenSolaris running their flagship code.
Fool, javascript is not java.

---

### Post by frustphil on 2009-05-07
Someone pls enlighten me whether or not the bottom panel is temporary? If it is, where would the tasks be placed if it will be removed? Hmmmm... Docky? It would be nice but GNOME 3 would sound bad...

---

### Post by super.rad on 2009-05-07
> **autocrosser said:**
> Problem would be accelerated desktop in a VM....It runs like a sloth in a non-accelerated desktop...real fluid otherwise....

ah that must be my problem. I'm using the opensource ATI drivers an have no 3D for my card

---

### Post by plun on 2009-05-07
> **frustphil said:**
> Someone pls enlighten me whether or not the bottom panel is temporary? If it is, where would the tasks be placed if it will be removed? Hmmmm... Docky? It would be nice but GNOME 3 would sound bad...

I am using Avant-Window-Navigator (AWN), much more functions then Docky.

Another choice is maybe Dockbar
[https://code.launchpad.net/~dockbar-main](https://code.launchpad.net/~dockbar-main)

edit, more about dockbar

[http://www.gnome-look.org/content/show.php/DockbarX?content=101604](http://www.gnome-look.org/content/show.php/DockbarX?content=101604)

The standard panel is just terrible....

---

### Post by Merk42 on 2009-05-07
> **super.rad said:**
> ah that must be my problem. I'm using the opensource ATI drivers an have no 3D for my card

But the latest version of Virtualbox supports virtual 3d acceleration.

---

### Post by autocrosser on 2009-05-07
> **frustphil said:**
> Someone pls enlighten me whether or not the bottom panel is temporary? If it is, where would the tasks be placed if it will be removed? Hmmmm... Docky? It would be nice but GNOME 3 would sound bad...


Yes--there has been talk about Docky or Gnome-Do---I would be happy with anything but what is there--or at least allow us the option to really mod the lower panel. AWN would be a good choice or.......   I'm keeping my eye on the dev list & will notify if anything looks good.

---

### Post by autocrosser on 2009-05-07
> **plun said:**
> OK, thanks ... the same as for a month ago...

Nevertheless I upgraded Gnome-shell this morning and it seg faults with a hard logout...:---)

It maybe has something todo with compiz because its really unstable for the moment,   Compiz to Metacity switch.

Hey plun---what version of nVidia driver are you using?  I had a hard crash back to GDM with the new beta 185 drivers (bug reported)--works well with the 180.53 driver....I don't see anything in the commits that would be a problem---last was the fix for one of my bug reports.....link: [http://git.gnome.org/cgit/gnome-shell](http://git.gnome.org/cgit/gnome-shell)

Take a look at my report: [http://bugzilla.gnome.org/show_bug.cgi?id=581556](http://bugzilla.gnome.org/show_bug.cgi?id=581556)  & check your logs to see if you had the same errors....If you did & you have a bugzilla account--could you confirm the bug?

---

### Post by plun on 2009-05-07
> **autocrosser said:**
> Hey plun---what version of nVidia driver are you using?  I had a hard crash back to GDM with the new beta 185 drivers (bug reported)--works well with the 180.53 driver....I don't see anything in the commits that would be a problem---last was the fix for one of my bug reports.....link: [http://git.gnome.org/cgit/gnome-shell](http://git.gnome.org/cgit/gnome-shell)

Hi again, I am using the beta driver 185.18.08
[http://www.nvnews.net/vbulletin/showthread.php?p=1997862](http://www.nvnews.net/vbulletin/showthread.php?p=1997862)

Crash,boom,bang with Gnome-shell .....:)

Maybe I should take some time and use SSH for a check. Nevertheless X crashes and restarts with a Logout.

---

### Post by autocrosser on 2009-05-07
> **plun said:**
> Hi again, I am using the beta driver 185.18.08
[http://www.nvnews.net/vbulletin/showthread.php?p=1997862](http://www.nvnews.net/vbulletin/showthread.php?p=1997862)

Crash,boom,bang with Gnome-shell .....:)

Maybe I should take some time and use SSH for a check. Nevertheless X crashes and restarts with a Logout.

Ya--that's what I thought!!!! I added info to my last post---dig thru your logs & please add to my bug report--the dev that looked at it (Milan) wants me to shuffel off to a X-org bug...It is interesting that it was a commit from the last day or so?  that is at the heart of the "problem"---If you revert to 180.53 (Jaunty-proposed), the shell works as expected....

When was the last time you did a build?

---

### Post by autocrosser on 2009-05-07
Just as a side note: It was not doing it with the 185.18.04 driver.....

---

### Post by plun on 2009-05-07
> **autocrosser said:**
> 
If you revert to 180.53 (Jaunty-proposed), the shell works as expected....

When was the last time you did a build?

Okidok... revert is done and it.... works..:)

Last time was maybe a week ago. So we have a bug with latest
nVidia driver.

---

### Post by BGFG on 2009-05-07
> **Incognito-Here said:**
> Fool, javascript is not java.

SunMicrosystems , Netscape. My mistake. You were wonderfully helpful though. keep up the great work.

---

### Post by autocrosser on 2009-05-07
> **plun said:**
> Okidok... revert is done and it.... works..:)

Last time was maybe a week ago. So we have a bug with latest
nVidia driver.


Ya---I thought it was a bug in the.08 driver---best we can do is keep a eye on the nVidia releases & test/verify as they come out........

---

### Post by afv on 2009-05-07
Running fine for me with NVIDIA drivers version *185.19.1~really185.18.04-0ubuntu0* from [Michael Marley's PPA](https://launchpad.net/~thefirstm/+archive/ppa). :)

---

### Post by autocrosser on 2009-05-08
Just do not update to the .08 from that PPA---you will break the shell---plun & I both were running it.

---

### Post by Incognito-Here on 2009-05-08
> **BGFG said:**
> SunMicrosystems , Netscape. My mistake. You were wonderfully helpful though. keep up the great work.
They use adobe spidermonkey (tracemonkey in the near future) engine, not mozilla/netscape ;)

---

### Post by frustphil on 2009-05-08
> **autocrosser said:**
> Yes--there has been talk about Docky or Gnome-Do---I would be happy with anything but what is there--or at least allow us the option to really mod the lower panel. AWN would be a good choice or.......   I'm keeping my eye on the dev list & will notify if anything looks good.

That's wonderful to hear... I hope it would be Docky... and global-menu. :)

---

### Post by Starks on 2009-05-08
> **frustphil said:**
> That's wonderful to hear... I hope it would be Docky... and global-menu. :)
All I want is a healthy focus.

---

### Post by skierkyles on 2009-05-08
So will there be any major changes to the desktop in 3, or is it mostly the gnome shell?

---

### Post by Starks on 2009-05-08
> **skierkyles said:**
> So will there be any major changes to the desktop in 3, or is it mostly the gnome shell?

[http://live.gnome.org/ThreePointZero/Plan](http://live.gnome.org/ThreePointZero/Plan)

Doesn't sound too encouraging.

---

### Post by Merk42 on 2009-05-08
> **skierkyles said:**
> So will there be any major changes to the desktop in 3, or is it mostly the gnome shell?

**Change**? in **GNOME**? hahaahaha

---

### Post by flipmatthew on 2009-05-08
it will not let me build clutter with git clone git://git.clutter-project.org/clutter
cd clutter
./autogen.sh --prefix=/usr
make
sudo make install
also, gnome 3 warns me it needs /root/bin and when i try to configure gnome 3, one of the errors is Python headers not found
*** error during stage configure of gobject-introspection: ########## Error running ./autogen.sh --prefix /root/gnome-shell/install --libdir '${exec_prefix}/lib64'  --disable-static --disable-gtk-doc *** [1

---

### Post by flipmatthew on 2009-05-08
also it gives some errors about go object

---

### Post by Sand Lee on 2009-05-08
> **autocrosser said:**
> Yes--there has been talk about Docky or Gnome-Do---I would be happy with anything but what is there--or at least allow us the option to really mod the lower panel. AWN would be a good choice or.......   I'm keeping my eye on the dev list & will notify if anything looks good.

wait a sec, honestly speaking and i'm not trying to flame bait,
won't this almost make gnome 3's desktop look just like OSX's?

---

### Post by olskar on 2009-05-08
Kde 4.3:
[http://3.bp.blogspot.com/__JNFVYfijS4/SZdFclarlKI/AAAAAAAAAYI/jQfZsz1VdGw/s1600-h/image601.png](http://3.bp.blogspot.com/__JNFVYfijS4/SZdFclarlKI/AAAAAAAAAYI/jQfZsz1VdGw/s1600-h/image601.png)


Gnome 3:
[http://live.gnome.org/GnomeShell/Screenshots?action=AttachFile&do=get&target=GnomeShell.png](http://live.gnome.org/GnomeShell/Screenshots?action=AttachFile&do=get&target=GnomeShell.png)


:neutral:

---

### Post by frustphil on 2009-05-08
> **Sand Lee said:**
> wait a sec, honestly speaking and i'm not trying to flame bait,
won't this almost make gnome 3's desktop look just like OSX's?
  Certainly... But what could else be the other way to manage tasks? The bottom panel is very ancient IMHO and it doesn't improve Gnome 3 visually. And I am pretty sure someone said during the boston hackfest that there would be no bottom panel...

---

### Post by Nullack on 2009-05-08
Numerous useability experts are critical of the idea for a GUI involving a dock - including one of the founders of the Mac interface.

---

### Post by autocrosser on 2009-05-08
> **flipmatthew said:**
> also it gives some errors about go object


I am having the go-object error right now--if it is still there after tonights commits---I would ask anyone that is having the build problem to add to my bug report...  [http://bugzilla.gnome.org/show_bug.cgi?id=581828](http://bugzilla.gnome.org/show_bug.cgi?id=581828)

Thanks!!!

---

### Post by Longinus00 on 2009-05-09
I'm not exactly sure what I think about this move towards interfaces that require 3d acceleration considering how often 3d acceleration gets broken (see jaunty ATI and Intel drivers). Some drivers also have problems with doing XV acceleration while compositing is enabled.

---

### Post by gnomeuser on 2009-05-09
> **Nullack said:**
> Numerous useability experts are critical of the idea for a GUI involving a dock - including one of the founders of the Mac interface.
[citation neeeded]

---

### Post by plun on 2009-05-09
> **autocrosser said:**
> I am having the go-object error right now--if it is still there after tonights commits---I would ask anyone that is having the build problem to add to my bug report...  [http://bugzilla.gnome.org/show_bug.cgi?id=581828](http://bugzilla.gnome.org/show_bug.cgi?id=581828)

Thanks!!!

It works for me with latest updates.... nothing in the log

```
 JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
```

:confused:

EDIT

What gives a complete new build ?

```
jhbuild build -f -a -c
```

---

### Post by autocrosser on 2009-05-09
Interesting...........I deleted (almost) everything for the shell & had tried to build it with no luck yesterday---I tried again this morning & deleted everything including the gnome-shell-build-setup.sh on my desktop---built without a error.   I guess I need to "really" remove all parts of the build if there is a problem with any part of it :(:(.....

Closed my bug & hang my head in shame......................

---

### Post by flipmatthew on 2009-05-09
no matter what I do, i still get the go-object error. i also get an error Installing jhbuild...
In file included from /usr/include/bits/errno.h:25,
                 from /usr/include/errno.h:36,
                 from install-check.c:23:
/usr/include/linux/errno.h:4:23: error: asm/errno.h: No such file or directory


in the go-object error, it says cannot find python headers.
i ignored that and got another error during stage configure of gir-repository: ########## Error running ./autogen.sh --prefix /root/gnome-shell/install --libdir '${exec_prefix}/lib64'  --disable-static --disable-gtk-doc *** [2/6]
also *** error during stage build of gir-repository: ########## Error running make   *** [2/6]

---

### Post by flipmatthew on 2009-05-09
no matter what I do, i still get the go-object error. i also get an error Installing jhbuild...
In file included from /usr/include/bits/errno.h:25,
from /usr/include/errno.h:36,
from install-check.c:23:
/usr/include/linux/errno.h:4:23: error: asm/errno.h: No such file or directory


in the go-object error, it says cannot find python headers.
i ignored that and got another error during stage configure of gir-repository: ########## Error running ./autogen.sh --prefix /root/gnome-shell/install --libdir '${exec_prefix}/lib64' --disable-static --disable-gtk-doc *** [2/6]
also *** error during stage build of gir-repository: ########## Error running make *** [2/6]
also error running ./configure for clutter...
also *** error during stage install of clutter: ########## Error running make *** [3/6]
also *** error during stage install of clutter: ########## Error running make install *** [3/6]
*** error during stage configure of mutter: ########## Error running ./autogen.sh --prefix /root/gnome-shell/install --libdir '${exec_prefix}/lib64' --with-clutter --disable-static --disable-gtk-doc *** [4/6]
also *** error during stage install of mutter: ########## Error running make *** [4/6]
also *** error during stage install of mutter: ########## Error running make install *** [4/6]
also *** error during stage configure of gjs: ########## Error running ./autogen.sh --prefix /root/gnome-shell/install --libdir '${exec_prefix}/lib64'  --disable-static --disable-gtk-doc *** [5/6]
error building gjs *** error during stage build of gjs: ########## Error running make
*** error during stage build of gjs: ########## Error running make install
*** error during stage configure of gnome-shell: ########## Error running ./autogen.sh --prefix /root/gnome-shell/install --libdir '${exec_prefix}/lib64'  --disable-static --disable-gtk-doc *** [6/6]
make  
make: *** No targets specified and no makefile found.  Stop.
*** error during stage build of gnome-shell: ########## Error running make   *** [6/6]
make   install
make: *** No rule to make target `install'.  Stop.
*** error during stage install of gnome-shell: ########## Error running make   install *** [6/6]

---

### Post by Naddiseo on 2009-05-09
> **flipmatthew said:**
> no matter what I do, i still get the go-object error. i also get an error Installing jhbuild...
In file included from /usr/include/bits/errno.h:25,
from /usr/include/errno.h:36,
from install-check.c:23:
/usr/include/linux/errno.h:4:23: error: asm/errno.h: No such file or directory


You need to update linux-libc-dev

---

### Post by autocrosser on 2009-05-09
I reinstall everything python last night--Go-object needs python-dev-headers to build...All I can figure is that after I rebooted all of it got seen & worked-----I also deleted EVERYTHING for gnome-shell--the script on the desktop, .jhbuildrc & .jhbuildrc-custom in my user folder & the main gnome-shell folder.....then reinstalled it all...now it works again....go figure :(

---

### Post by flipmatthew on 2009-05-09
do i need python 2 or 3?

---

### Post by Starks on 2009-05-09
> **flipmatthew said:**
> do i need python 2 or 3?
If you need to ask that question, you probably didn't install all of the requested build-deps.

---

### Post by Wolki on 2009-05-10
> **gnomeuser said:**
> [citation neeeded]

[http://www.asktog.com/columns/044top10docksucks.html](http://www.asktog.com/columns/044top10docksucks.html)

---

### Post by plun on 2009-05-10
It looks like this for the moment with AWN running....  :-\"

[[img]http://ubuntu-pics.de/thumb/13811/snapshot42_15i5od.png[/img]](http://ubuntu-pics.de/bild/13811/snapshot42_15i5od.png)


I cannot see any reason for going to "Activities" every time I want to launch my favourite application.

Also saw this mockup for task-handling:

[http://live.gnome.org/GnomeShell/DesignerPlayground/TaskListDropDown](http://live.gnome.org/GnomeShell/DesignerPlayground/TaskListDropDown)



More fuel for the debate  8-), "The Compiz challenge"

[http://smspillaz.wordpress.com/2009/04/30/misinformation-and-miscommunication/](http://smspillaz.wordpress.com/2009/04/30/misinformation-and-miscommunication/)

---

### Post by davideotape on 2009-05-10
Just installed gnome 3, but I'm getting this message when trying to start it:

```
david@ExternalHarddrive:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x0000000002b3bf10 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f9383eaacc8]
/lib/libc.so.6(cfree+0x76)[0x7f9383ead286]
/usr/lib/libGL.so.1[0x7f9385ccd12a]
======= Memory map: ========
00400000-0043c000 r-xp 00000000 08:35 13421984                           /usr/bin/compiz.real
0063b000-0063c000 r--p 0003b000 08:35 13421984                           /usr/bin/compiz.real
0063c000-0063d000 rw-p 0003c000 08:35 13421984                           /usr/bin/compiz.real
012b0000-03a79000 rw-p 012b0000 00:00 0                                  [heap]
7f937dcf3000-7f937dcff000 r-xp 00000000 08:35 8897166                    /lib/libnss_files-2.9.so
7f937dcff000-7f937defe000 ---p 0000c000 08:35 8897166                    /lib/libnss_files-2.9.so
7f937defe000-7f937deff000 r--p 0000b000 08:35 8897166                    /lib/libnss_files-2.9.so
7f937deff000-7f937df00000 rw-p 0000c000 08:35 8897166                    /lib/libnss_files-2.9.so
7f937df00000-7f937df0a000 r-xp 00000000 08:35 8897168                    /lib/libnss_nis-2.9.so
7f937df0a000-7f937e109000 ---p 0000a000 08:35 8897168                    /lib/libnss_nis-2.9.so
7f937e109000-7f937e10a000 r--p 00009000 08:35 8897168                    /lib/libnss_nis-2.9.so
7f937e10a000-7f937e10b000 rw-p 0000a000 08:35 8897168                    /lib/libnss_nis-2.9.so
7f937e10b000-7f937e121000 r-xp 00000000 08:35 8897163                    /lib/libnsl-2.9.so
7f937e121000-7f937e321000 ---p 00016000 08:35 8897163                    /lib/libnsl-2.9.so
7f937e321000-7f937e322000 r--p 00016000 08:35 8897163                    /lib/libnsl-2.9.so
7f937e322000-7f937e323000 rw-p 00017000 08:35 8897163                    /lib/libnsl-2.9.so
7f937e323000-7f937e325000 rw-p 7f937e323000 00:00 0 
7f937e325000-7f937e32d000 r-xp 00000000 08:35 8897164                    /lib/libnss_compat-2.9.so
7f937e32d000-7f937e52c000 ---p 00008000 08:35 8897164                    /lib/libnss_compat-2.9.so
7f937e52c000-7f937e52d000 r--p 00007000 08:35 8897164                    /lib/libnss_compat-2.9.so
7f937e52d000-7f937e52e000 rw-p 00008000 08:35 8897164                    /lib/libnss_compat-2.9.so
7f937e52e000-7f937e55d000 r-xp 00000000 08:35 8896632                    /lib/libpcre.so.3.12.1
7f937e55d000-7f937e75c000 ---p 0002f000 08:35 8896632                    /lib/libpcre.so.3.12.1
7f937e75c000-7f937e75d000 r--p 0002e000 08:35 8896632                    /lib/libpcre.so.3.12.1
7f937e75d000-7f937e75e000 rw-p 0002f000 08:35 8896632                    /lib/libpcre.so.3.12.1
7f937e75e000-7f937e7a2000 r-xp 00000000 08:35 13420276                   /usr/lib/libgobject-2.0.so.0.2000.1
7f937e7a2000-7f937e9a2000 ---p 00044000 08:35 13420276                   /usr/lib/libgobject-2.0.so.0.2000.1
7f937e9a2000-7f937e9a3000 r--p 00044000 08:35 13420276                   /usr/lib/libgobject-2.0.so.0.2000.1
7f937e9a3000-7f937e9a4000 rw-p 00045000 08:35 13420276                   /usr/lib/libgobject-2.0.so.0.2000.1
7f937e9a4000-7f937e9a5000 rw-p 7f937e9a4000 00:00 0 
7f937e9a5000-7f937e9e1000 r-xp 00000000 08:35 8896567                    /lib/libdbus-1.so.3.4.0
7f937e9e1000-7f937ebe0000 ---p 0003c000 08:35 8896567                    /lib/libdbus-1.so.3.4.0
7f937ebe0000-7f937ebe1000 r--p 0003b000 08:35 8896567                    /lib/libdbus-1.so.3.4.0
7f937ebe1000-7f937ebe2000 rw-p 0003c000 08:35 8896567                    /lib/libdbus-1.so.3.4.0
7f937ebe2000-7f937ec02000 r-xp 00000000 08:35 13418746                   /usr/lib/libdbus-glib-1.so.2.1.0
7f937ec02000-7f937ee02000 ---p 00020000 08:35 13418746                   /usr/lib/libdbus-glib-1.so.2.1.0
7f937ee02000-7f937ee03000 r--p 00020000 08:35 13418746                   /usr/lib/libdbus-glib-1.so.2.1.0
7f937ee03000-7f937ee04000 rw-p 00021000 08:35 13418746                   /usr/lib/libdbus-glib-1.so.2.1.0
7f937ee04000-7f937ee0b000 r-xp 00000000 08:35 8897173                    /lib/librt-2.9.so
7f937ee0b000-7f937f00a000 ---p 00007000 08:35 88Aborted
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
Checking for Xgl: david@ExternalHarddrive:~/gnome-shell/source/gnome-shell/src$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: ** (gnome-panel:19752): DEBUG: Adding applet 0.
** (gnome-panel:19752): DEBUG: Initialized Panel Applet Signaler.
present. 
Checking for Composite extension: present. 
Checking screen 1** (gnome-panel:19752): DEBUG: Adding applet 1.
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: ** (gnome-panel:19752): DEBUG: Adding applet 2.
Not present. 
Checking for nVidia: present. 
Checking for FBConfig: ** (gnome-panel:19752): DEBUG: Adding applet 3.

(gnome-panel:19752): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: ** (gnome-panel:19752): DEBUG: Adding applet 4.
not present. 
** (gnome-panel:19752): DEBUG: Adding applet 5.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
david@ExternalHarddrive:~/gnome-shell/source/gnome-shell/src$ 

```

Anyone know what's happening and how I can fix it?

---

### Post by autocrosser on 2009-05-10
Yes---stop Compiz first---Gnome-shell uses composite also--you "can't" have two composite managers running at the same time......

---

### Post by olskar on 2009-05-10
> **plun said:**
> 
Also saw this mockup for task-handling:

[http://live.gnome.org/GnomeShell/DesignerPlayground/TaskListDropDown](http://live.gnome.org/GnomeShell/DesignerPlayground/TaskListDropDown)

Terrible idea IMO, this way you have to stop what you are doing and hover your mouse over the taskbar to see what application wants attention. 

You should be able to see what application is demanding attention before you stop what you are doing so you can decide if it is something you want to check now or wait with.

They sure aren't usability experts at Gnome :(

---

### Post by davideotape on 2009-05-10
> **autocrosser said:**
> Yes---stop Compiz first---Gnome-shell uses composite also--you "can't" have two composite managers running at the same time......

Thanks, that worked for me. Does the shell thingymabob install updates to gnome 3.0 for you in synaptic or not?

---

### Post by frustphil on 2009-05-10
> **plun said:**
> 

Also saw this mockup for task-handling:

[http://live.gnome.org/GnomeShell/DesignerPlayground/TaskListDropDown](http://live.gnome.org/GnomeShell/DesignerPlayground/TaskListDropDown)



More fuel for the debate  8-), "The Compiz challenge"

[http://smspillaz.wordpress.com/2009/04/30/misinformation-and-miscommunication/](http://smspillaz.wordpress.com/2009/04/30/misinformation-and-miscommunication/)

Is it official???

---

### Post by autocrosser on 2009-05-10
> **frustphil said:**
> Is it official???

I really hope so..it's needed for task handling.....

---

### Post by autocrosser on 2009-05-10
> **davideotape said:**
> Thanks, that worked for me. Does the shell thingymabob install updates to gnome 3.0 for you in synaptic or not?

If there are depends that the script sees are not on your system you "should" get a prompt to do a "sudo apt-get whatever it is"---

As far as updating the shell it self--that is just a manual thing...it's installed in your user folder so it will not muck up your main system---it is under very heavy development right now & changes almost daily...

Look for the links I've posted in this thread & keep up on the commits.

---

### Post by Merk42 on 2009-05-10
> **autocrosser said:**
> I really hope so..it's needed for task handling.....

Neat idea, but it requires a click to see what programs you have open.
Every other OS in use I can think of (Windows, OSX, and Linux with KDE and GNOME DEs) show at a glance what programs you have running without requiring any action from the user.

I also thought the top bar was going to be the title of the window when it was fully maximized.

---

### Post by olskar on 2009-05-10
> **Merk42 said:**
> Neat idea, but it requires a click to see what programs you have open.
Every other OS in use I can think of (Windows, OSX, and Linux with KDE and GNOME DEs) show at a glance what programs you have running without requiring any action from the user.

I also thought the top bar was going to be the title of the window when it was fully maximized.

As I understand it you only how to hover over to see what programs are running, however it is still a really bad idea usabilitywise.

---

### Post by ronacc on 2009-05-10
is there a way to install it ? I'm willing to give it a try ,I'd rather have that than the bottom bar .

---

### Post by davideotape on 2009-05-10
> **autocrosser said:**
> If there are depends that the script sees are not on your system you "should" get a prompt to do a "sudo apt-get whatever it is"---

As far as updating the shell it self--that is just a manual thing...it's installed in your user folder so it will not muck up your main system---it is under very heavy development right now & changes almost daily...

Look for the links I've posted in this thread & keep up on the commits.

Sorry about all the questions, but I'm very new to this testing business. Is there an easy way to update to the newest commits?

---

### Post by olskar on 2009-05-10
> **davideotape said:**
> Sorry about all the questions, but I'm very new to this testing business. Is there an easy way to update to the newest commits?

Try jhbuild build -f -a -c

---

### Post by ronacc on 2009-05-10
in your .jhbuild dir  do   ```
jhbuild build -f -a -c 
``` . that should do it .

---

### Post by davideotape on 2009-05-10
> **olskar said:**
> Try jhbuild build -f -a -c

> **ronacc said:**
> in your .jhbuild dir do
Code:

```
jhbuild build -f -a -c
```



Thanks guys :D

---

### Post by flipmatthew on 2009-05-10
ok so I built it without any errors, but when I try to replace it it will take away the bottom and top task bars and exit buttons, and won't replace them, all i end uo with is a non working OS and I have to restart.

---

### Post by davideotape on 2009-05-10
> **flipmatthew said:**
> ok so I built it without any errors, but when I try to replace it it will take away the bottom and top task bars and exit buttons, and won't replace them, all i end uo with is a non working OS and I have to restart.

Can you not use control-c to exit and go back to your origional desktop environment?

---

### Post by super.rad on 2009-05-10
I have similar problems, it loads the panels but the desktop just stays black, when I click activities it takes about 2 minutes to open it and if i try click an application it takes ages to open but I can't see it as the desktop is black. Ctrl+C does nothing for me either, I have to restart. I'm using the radeon drivers if that makes any difference

---

### Post by davideotape on 2009-05-10
> **super.rad said:**
>   I'm using the radeon drivers if that makes any difference

I think it does make a difference. Some others have posted about problems with the radeon drivers previously I'm this thread. Personally I'm using the nvidia drivers and all seems to be working fine.

---

### Post by autocrosser on 2009-05-10
Well--you need a 3D enabled driver to use Gnome-Shell---just like you would need with Compiz.....

There has been quite a bit about hardware requirements on the dev-list--rather spirited stuff......:)

---

### Post by flipmatthew on 2009-05-10
No, Control + c won't work, and yes I have 3D acceleration with nvidia 180.42 graphics ( used envy-ng ). i don't get why it won't work.

---

### Post by olskar on 2009-05-10
> **flipmatthew said:**
> No, Control + c won't work, and yes I have 3D acceleration with nvidia 180.42 graphics ( used envy-ng ). i don't get why it won't work.

Do you turn off compiz before turning on gnomeshell?

---

### Post by flipmatthew on 2009-05-10
yes i used sudo metacity --replace.

---

### Post by super.rad on 2009-05-10
> **autocrosser said:**
> Well--you need a 3D enabled driver to use Gnome-Shell---just like you would need with Compiz.....

There has been quite a bit about hardware requirements on the dev-list--rather spirited stuff......:)

ah that explains it, i have no 3D for my card....yet

---

### Post by flipmatthew on 2009-05-10
It just will not work, can anyone help me!

---

### Post by flipmatthew on 2009-05-10
could the 2.6.30 rc4 kernel have anything to do with it. if anyone can help me that would be greatly appreciated!

---

### Post by MacUntu on 2009-05-10
Will it be possible to mimic current behavior? If this is the future of Gnome, KDE is the future for my systems. :(

---

### Post by autocrosser on 2009-05-10
> **flipmatthew said:**
> could the 2.6.30 rc4 kernel have anything to do with it. if anyone can help me that would be greatly appreciated!

Not sure what is going on with your system---
1. How are you starting the shell? (using the info on the webpage, via my method or using plun's script?)
2. When was the last time you built it?
3. Are you trying to save any files forward (appDisplay.js or panel.js?) & if so, are you just replacing the new files with the old ones or just copying the important bits into the new files?

---

### Post by flipmatthew on 2009-05-10
1. i used the info on the webpage
2. just a second ago
3. i don't know what u mean.

---

### Post by autocrosser on 2009-05-10
As to #3---If you start the shell via my or plun's way, you can change the default apps & other factors that make up the shell....

OK---the first thing I would do is remove EVERYTHING that the shell uses & redo it....that includes the gnome-shell user folder, the desktop build script & both the .jhbuildrc & .jhbuildrc-custom in your users folder(hidden files). After you do a clean build, then try doing a shell start---make sure that you DO NOT close the terminal until you want to close the shell---you can minimize the term......

Post back with the term output if it is not working so we can see what is going on.......

---

### Post by flipmatthew on 2009-05-10
ok, im rebuilding after deleting everything.

---

### Post by flipmatthew on 2009-05-10
building worked, running failed, yes i did metaccity --replace. here is the log
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
x

---

### Post by olskar on 2009-05-10
> **MacUntu said:**
> Will it be possible to mimic current behavior? If this is the future of Gnome, KDE is the future for my systems. :(

As it looks now, I agree. But let's see what happens, it's not even alpha :)

---

### Post by frustphil on 2009-05-10
> **olskar said:**
> As I understand it you only how to hover over to see what programs are running, however it is still a really bad idea usabilitywise.

For me it's ingenious. It doesn't matter if only the active task is visible IMHO. It gives me a clear view as to which window I am using especially with multiple tasks running. Really you don't have to see all the other tasks but the one you are actively using. And if I want to see all the tasks, it's just a hover away...

---

### Post by autocrosser on 2009-05-10
> **flipmatthew said:**
> building worked, running failed, yes i did metaccity --replace. here is the log
Window manager warning: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
x


Hmmmm---what stands out in that is: "the message bus security policy blocked the reply"---Have you had permission problems in the past with your system?

You might check in Users & Groups to see if you are an Admin or just a Desktop user...I would also (if you are an Admin), create another user (while you are in U&G--make sure the new user is an Admin) & build the shell there...that will tell you if there is a problem with your user....

Also--go into Apperance & under the "Visual Effects" tab---select "none" (then log out/in--you might try this before creating another user.....)--then try the shell that way.


I got to admit that one is a bit odd........Tell me a bit more about your system.

---

### Post by ronacc on 2009-05-10
have you udated recently , there were problems with users and groups (among other things) early on , see this thread [http://ubuntuforums.org/showthread.php?t=1145045](http://ubuntuforums.org/showthread.php?t=1145045)  .

---

### Post by frustphil on 2009-05-10
How do I update gnome-shell?:)

---

### Post by autocrosser on 2009-05-10
First---take a look at the commits page---link is in the main Gnome-Shell page that is linked earlier in this thread....if there are no commits dated after you built last, there won't be any need to do it again.

If there are commits, then you just build the shell again..the script will look at what you already have & update only the elements that have changed...Use the standard:

```
curl -O http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh
jhbuild build

```that you did before---if you run into problems with the build, try:

```
jhbuild build -f -a -c
```Instead of just build to re-do all of it for a clean build.

If that still causes a problem--follow my info from the last page or so & delete EVERYTHING related to Gnome-Shell & then do a fresh build....

I think that about covers it :):)

---

### Post by frustphil on 2009-05-10
> **autocrosser said:**
> First---take a look at the commits page---link is in the main Gnome-Shell page that is linked earlier in this thread....if there are no commits dated after you built last, there won't be any need to do it again.

If there are commits, then you just build the shell again..the script will look at what you already have & update only the elements that have changed...Use the standard:

```
curl -O http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh
jhbuild build

```that you did before---if you run into problems with the build, try:

```
jhbuild build -f -a -c
```Instead of just build to re-do all of it for a clean build.

If that still causes a problem--follow my info from the last page or so & delete EVERYTHING related to Gnome-Shell & then do a fresh build....

I think that about covers it :):)

Thanks!:)

---

### Post by MacUntu on 2009-05-11
> **olskar said:**
> As it looks now, I agree. But let's see what happens, it's not even alpha :)

I'm not against such experiments, it's just that I don't see how those concepts would raise my efficiency - pre-alpha or not.

Windows 7's taskbar as an example: I can achieve my goals much faster with the old implementation. What's a "pro" for others is just overhead for me.

So for me the possibility to "go back" is crucial. With KDE 4 you can have activities, but you don't need to. Not using them doesn't influence your desktop experience - that's what I'm expecting.

---

### Post by ronacc on 2009-05-11
it's a given that any change especially a major one will not make everyone happy. The ability to revert would be welcome but I'm not sure how long that can be maintained without a large "cost " in overhead . I'm willing to play with this as it developes in hopes that by the time it becomes "the desktop" I am adjusted to it . I too have some misgivings about whether this " improvement " will help my daily operations .

---

### Post by Merk42 on 2009-05-11
Seems like the same argument I see in the Windows 7 forums demanding the classic Start Menu. (and to a lesser extent the tab change in Safari 4)

People argue the new way is less efficient.
The other side argues they only feel it's less efficient because it's not that they're used to and if they actually tried the new way they'd find it better.

Given GNOME3 is pre-alpha they haven't even figured out what they're doing for all aspects of navigation, such as minimized windows.  Frankly I would think that a mock-up should have been done that addressed all these issues first, and **then** work on making the code.

---

### Post by ronacc on 2009-05-11
> **Merk42 said:**
> 
Given GNOME3 is pre-alpha they haven't even figured out what they're doing for all aspects of navigation, such as minimized windows.  Frankly I would think that a mock-up should have been done that addressed all these issues first, and **then** work on making the code.

I think that putting this out early in the process gives us a chance to have some input as to how it develops rather than be presented with an almost finished version that would be hard to get changed .

---

### Post by 23meg on 2009-05-11
This thread seems to have turned into being about the GNOME Shell project rather than GNOME 3 in whole, so I've retitled it appropriately to avoid false impressions.

---

### Post by autocrosser on 2009-05-11
Thanks 23meg---how are you doing??

---

### Post by 23meg on 2009-05-11
Buried in work, preparing the stickies, preparing for UDS :)

---

### Post by flipmatthew on 2009-05-11
ok hold on, i disabled the visual affects i will try it again soon. yes im admin. 64bit 2.6.30 rc4 ( about to be rc5 ) with nvidia drivers.

---

### Post by frustphil on 2009-05-11
One of the two bugs I hate about compiz is with clutter as well.. The shadow effects of the top panel is not turned off when you drag a window against it. It looks like the window slides under the top panel.

---

### Post by autocrosser on 2009-05-11
> **23meg said:**
> Buried in work, preparing the stickies, preparing for UDS :)


Great to see you're still around---Have fun at UDS---I wish I could have gone to the last one---I live only 5 hrs away from the Bay area...:(

No chance I can make this one :(:(:(


Cheers!!!!!

---

### Post by Gourgi on 2009-05-11
i'd like this features for Gnome 3:
Nautilus split view filebrowsing : [http://www.youtube.com/watch?v=yqBDEi17l2A](http://www.youtube.com/watch?v=yqBDEi17l2A)
individual Workspace Wallpapers [http://www.youtube.com/watch?v=e1QHs-STcHs](http://www.youtube.com/watch?v=e1QHs-STcHs)

---

### Post by autocrosser on 2009-05-11
> **Gourgi said:**
> i'd like this features for Gnome 3:
Nautilus split view filebrowsing : [http://www.youtube.com/watch?v=yqBDEi17l2A](http://www.youtube.com/watch?v=yqBDEi17l2A)
individual Workspace Wallpapers [http://www.youtube.com/watch?v=e1QHs-STcHs](http://www.youtube.com/watch?v=e1QHs-STcHs)


I'm not sure about the split-view (as far as being done for the Shell---would be nice) & there has been quite a bit of talk about different wallpaper for different desktops---So I'm sure that one "should" be a go-------

---

### Post by frustphil on 2009-05-12
Gnome-shell development seems a bit slow. 12th of May has 2 commits only...

---

### Post by autocrosser on 2009-05-12
> **frustphil said:**
> Gnome-shell development seems a bit slow. 12th of May has 2 commits only...


You ought to see the bug reports---I think the devs are a bit busy----

---

### Post by cykotiktek on 2009-05-13
I am sure i am just missing something simple but this is what i am getting when i try to build 

hansen@ghansen-desktop:~$ jhbuild build
Traceback (most recent call last):
  File "/usr/share/jhbuild/jhbuild/config.py", line 92, in __init__
    execfile(filename, config)
IOError: [Errno 2] No such file or directory: '/home/ghansen/.jhbuildrc'
jhbuild: could not load config file

---

### Post by ronacc on 2009-05-13
If you followed the steps on [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)  , it should have created the .jhbuild  dir in your /home/<you>/ dir .

---

### Post by cykotiktek on 2009-05-13
this is what i did which i am pretty sure is exactly what the instructions say.  i am not exactly a command line junky so i could be messing something up i am just not sure what.

ghansen@ghansen-desktop:~$ curl -O [http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh](http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  5619  100  5619    0     0  12602      0 --:--:-- --:--:-- --:--:-- 12655
ghansen@ghansen-desktop:~$ /bin/bash gnome-shell-build-setup.sh
Checking out jhbuild into /home/ghansen/Source/jhbuild ... git.gnome.org[0: 209.132.176.202]: errno=Connection refused
fatal: unable to connect a socket (Connection refused)

---

### Post by ronacc on 2009-05-13
did the first cmd download gnome-shell-build-setup.sh ? if it did open a terminal in the dir where it is and run the cmd this way .
```
/bin/bash ./gnome-shell-build-setup.sh
```
and see what happens .

---

### Post by vaibhav on 2009-05-13
> **gnomeuser said:**
> I have to admit I am still not sold on the idea of the GNOME shell, I am fundamentally not sure that workspace management is the primary concern on the desktop today. This however is one of the top level problems handled by GNOME Shell.

I am skeptical of the sanity involved in selecting Javascript as the language to do development for GNOME 3.

The more I think about it, the less I believe that the GNOME shell is the right way ahead. On the whole I wonder why the ideas brewed upon in the Online Desktop were dropped wholesale.

I don't think it is fundamentally improving our computing experience, there were so many more interesting ideas being bandied about and this is the target.

Additionally I am concerned that for cycle after cycle we put limits on accepting things like webkit, yet javascript bridges, a new windowing manager (mutter - not entirely new granted) and a whole new desktop concept is accepted hardly without debate. 

Under the helmet though I am very excited about GNOME 3.0. Many needed cleanups and a set of clear guidelines for moving forward. Getting geolocation and communications solidly integrated really makes for exciting prospects.
Exactly my feeling.

---

### Post by lithorus on 2009-05-13
> **flipmatthew said:**
> yes i used sudo metacity --replace.
Don't use sudo for metacity. It's supposed to run as current logged in user...

---

### Post by coolen on 2009-05-14
I'm having troubles building at the moment. When I attempt the instructions given, I wind up failing on Clutter with this:

```
  File "/usr/lib/python2.6/subprocess.py", line 462, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['../../doltlibtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/tmp/tmp-introspectvndhSt/Cogl-0.9', '-L.', '-lclutter-cogl', '-pthread', '-Wl,--export-dynamic', '-L/home/benji/gnome-shell/install/lib64', '-lgio-2.0', '-lgirepository-1.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/tmp/tmp-introspectvndhSt/Cogl-0.9.o']' returned non-zero exit status 1
make[6]: *** [Cogl-0.9.gir] Error 1
make[5]: *** [all-recursive] Error 1
make[4]: *** [all] Error 2
make[3]: *** [all-recursive] Error 1
make[2]: *** [all] Error 2
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** error during stage build of clutter: ########## Error running make  *** [3/6]

  [1] rerun stage build
  [2] ignore error and continue to install
  [3] give up on module
  [4] start shell
  [5] reload configuration
  [6] go to stage force_checkout
  [7] go to stage configure
  [8] go to stage force_clean
  [9] go to stage force_distclean
choice: 
```

I saw that some had success building clutter separately. Following the advice of post #17 in this thread, I attempted to build Clutter, and wound up at this when I run make:

```
make[4]: *** No rule to make target `../clutter/cogl/libclutter-cogl.la', needed by `libclutter-glx-0.9.la'.  Stop.
make[3]: *** [all-recursive] Error 1
make[2]: *** [all] Error 2
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
```

Has anyone run into this, and perhaps solved it?

---

### Post by frustphil on 2009-05-14
Now I can't run it anymore. It reverts back when I try to ./gnome-shell --replace :(

---

### Post by autocrosser on 2009-05-14
There is a b0rk in the current build---wait until this evening & try again---I'm going on a short trip---will be back Friday or Saturday-----

---

### Post by plun on 2009-05-16
Build OK today....also running with latest nVidia driver ver 180.60

A new smart function...:D

[IMG]http://ubuntu-pics.de/bild/14424/snapshot44_b35H6R.png[/IMG]

:popcorn:

---

### Post by autocrosser on 2009-05-16
Ya--I just did a rebuild last night---looks very cool--there should be several fun things coming in in the next couple of weeks.

---

### Post by Merk42 on 2009-05-16
> **plun said:**
> Build OK today....also running with latest nVidia driver ver 180.60

A new smart function...:D

[IMG]http://ubuntu-pics.de/bild/14424/snapshot44_b35H6R.png[/IMG]

:popcorn:

What is that?
Is there any good place with up to date videos on what the shell is like?

---

### Post by autocrosser on 2009-05-16
It's a pop-out side menu---you are seeing it in the "hidden" position--I'll post a shot in a while on the "open" position...


There are no up-to-date videos--things are really in flux right now--they are breaking it as often as making it work---great fun!!!!!!

---

### Post by MacUntu on 2009-05-16
Does it affect the current Gnome installation or can I just deactivate it if I want the old desktop back (I feel this terrible "must install"-itching... :D)?

**Edit:** Well, it's already answered:

> Having this JHBuild setup will not affect your main system, so there is no need to run the GNOME Shell inside a virtual machine. 

---

### Post by autocrosser on 2009-05-16
OK--I've screen-shot both "hidden" & "open" with my default apps loaded in the appDisplay.js file---also, composite is starting to work better--the windows are dragging faster than they were a week ago.....

As for affecting the "current" gnome install---No, you sandbox it in your user folder & run it from there--no displacement of currently installed Gnome installed....Remember, this is still pre-alpha, so it breaks with regularity--it's also great fun---currently it builds, but I would build it before the next commits.....

Just read thru my comments about build/running it & have some fun!!!!

---

### Post by MacUntu on 2009-05-16
Unusable with VESA... need to get a new (working) laptop. :D

---

### Post by lamalex on 2009-05-16
> **gnomeuser said:**
> I have to admit I am still not sold on the idea of the GNOME shell, I am fundamentally not sure that workspace management is the primary concern on the desktop today. This however is one of the top level problems handled by GNOME Shell.

I am skeptical of the sanity involved in selecting Javascript as the language to do development for GNOME 3.

The more I think about it, the less I believe that the GNOME shell is the right way ahead. On the whole I wonder why the ideas brewed upon in the Online Desktop were dropped wholesale.

I don't think it is fundamentally improving our computing experience, there were so many more interesting ideas being bandied about and this is the target.

Additionally I am concerned that for cycle after cycle we put limits on accepting things like webkit, yet javascript bridges, a new windowing manager (mutter - not entirely new granted) and a whole new desktop concept is accepted hardly without debate. 

Under the helmet though I am very excited about GNOME 3.0. Many needed cleanups and a set of clear guidelines for moving forward. Getting geolocation and communications solidly integrated really makes for exciting prospects.

Spot on. I was at GDS when GNOME Shell was revealed, and have been following the progression since day 1, it's an entirely broken metaphor. Some of the comments from the developers really make me scratch my head, like this one:
> 
Nathan Lo is going to work on Multiple monitor support for workspaces. The combination of multiple monitors and multiple workspaces has always been uncomfortable in GNOME. Switching all your monitors at once just isn’t what you normally want. It’s more likely that you want to keep one monitor fixed and switch another. This problem becomes more pressing in GNOME Shell where we’ve tried to make workspaces easy to use and intuitive. So the project will explore how it works to have separate workspaces on the different monitors and what the appropriate way is to present that to the user. I’ll mentor this one.
 - [Owen Taylor]("http://blog.fishsoup.net/2009/04/20/gnome-shell-soc-projects/")

Has anyone ever really had the thought that they only wanted to switch one monitor? I know I haven't, most people I know use two monitors to have one giant desktop, not an electronic Rubik's cube.

---

### Post by oomingmak on 2009-05-16
> **lamalex said:**
> Spot on. I was at GDS when GNOME Shell was revealed, and have been following the progression since day 1,** it's an entirely broken metaphor**.
I absolutely agree with you.

---

### Post by ronacc on 2009-05-16
I have grave dougts about any scripting or interpeted language as the basic developement language .
 As to the monitor thing , independently switchable monitors is exactly what I want , I always want my desktop firmly anchored on my monitor with my lcd tv as a place to drag things to but with things always reverting to the monitor if the tv is off or not selected .

---

### Post by Nullack on 2009-05-16
gnome is loosing its way

---

### Post by Reiger on 2009-05-16
> **ronacc said:**
> I have grave dougts about any scripting or interpeted language as the basic developement language .

Granted I have not gotten my hands dirty with its code, but -if as I think it is- this gnome panel is basically a way of combining lots of meta info in JavaScript objects with some hardwired relations into them and functions to retrieve various objects (and display icons/stuff for the corresponding activities where appropriate) pushing all the real stuff down as much as possible to rather more heavy-duty-oriented libraries... Why not? Think of it as a widget, a quick launch or a dock but with a twist... It is not [should not] ever going to experience much of an application load, by virtue of the fact that but very few humans can actually do more than two or three things at a time and this Gnome Shell doesn't really involve much of the "doing" side of things. It just provides a way of beginning your "things". 

Having great doubts about any scripting or interpreted language as the basic development language means you really shouldn't be looking at the boot *scripts* or erhm... basically half the OS. :)

That said: I am not sold on its actual usability. I mean the only reason why I have my setup configured for more than 1 workspace is that I can accidentally loose focus of my current workspace by mis-scrolling or see the cube. ;)

---

### Post by ronacc on 2009-05-16
point taken . I do think the boot scripts can be justified , the rest I would prefer to see done in a compiled language ( whichever is appropriate to the app ) . The (relatively ) recent rage for scripting languages is a large part of the reason we need multi gigahertz , multi core processors and gb's of ram to manage more than a slow crawl. If JS is restricted to launchers etc ok but as the favored paradigm I fear "mission creep ".

---

### Post by Merk42 on 2009-05-17
> **autocrosser said:**
> OK--I've screen-shot both "hidden" & "open" with my default apps loaded in the appDisplay.js file---also, composite is starting to work better--the windows are dragging faster than they were a week ago.....

Did GNOME figure out where to put hidden windows yet?
With the exception of the thing you posted, all I've seen of GNOME3 is "woo look multiple desktops" and that's IT.

---

### Post by Regenweald on 2009-05-17
What is under the Gnome Shell hood ? I am a one workspace person, so outside of clutter and workspaces, what am I looking forward to ?
Zeitgeist is quite exciting though.

---

### Post by coolen on 2009-05-18
I've recently gotten into multiple workspaces. They are fantastic, but they can be difficult to work with (Expo and the cube are good for this).

I imagine a lot of people will find Gnome Shell helps them make use of multiple workspaces. Also makes it easy to add and remove them to suit your needs, which I like.

Other than that...umm...funkier application launching?

---

### Post by davideotape on 2009-05-18
Anyone else having problems with screencasting? Apparently the keycode is control-shift-alt-R, but pressing that gives me this:

```
    JS ERROR: !!!     message = 'Expected type array for Argument 'argv' but got type 'object' (nil)'
    JS ERROR: !!!   Exception was: Error: Expected type array for Argument 'argv' but got type 'object' (nil)
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Expected type array for Argument 'argv' but got type 'object' (nil)")@:0
("Expected type array for Argument 'argv' but got type 'object' (nil)")@gjs_throw:0
@:0
([object _private_Meta_Screen])@/home/david/gnome-shell/source/gnome-shell/js/ui/main.js:80
'
    JS ERROR: !!!     message = 'Expected type array for Argument 'argv' but got type 'object' (nil)'


```

---

### Post by Regenweald on 2009-05-18
> **coolen said:**
> I've recently gotten into multiple workspaces. They are fantastic, but they can be difficult to work with (Expo and the cube are good for this).

I imagine a lot of people will find Gnome Shell helps them make use of multiple workspaces. Also makes it easy to add and remove them to suit your needs, which I like.

Other than that...umm...funkier application launching?

It just feels like the Gnome team has let all the 'stagnant' criticism get to them. I get Zeitgeist, I get cleaning up of the 2.0 Libraries, but I'm a one workspace person, so other that launching apps like Gnome-do currently does, what is under that hood ?

From the mailing lists, even some Gnome-devs don't seem too impressed with this re-invention of the wheel. So basically: 'We've decided you can manage 'activities' better, and don't need as much customization, thusly, a new look and new number' 

Please don't get me wrong, All i have ever used is Gnome and i love it. I'm just trying to understand what the shell is all about.

---

### Post by coolen on 2009-05-18
Yeah, I understand where you're coming from. The first criticism that springs to mind when considering Gnome is rarely "workspaces are so hard to work with!".

It seems like they went for the bling that changes the way you work with the desktop, without really considering what's wrong with the way people currently work with their desktops.

Being a bling-whore and a multi-workspace person, Gnome Shell will be rather welcome (although I wish it were WM-agnostic).

My main hope is that it marks the beginning of a trend. Gnome needs some new ways of doing things. Now we just need to get Gloobus and Gnome-Do an official part of Gnome :D

---

### Post by autocrosser on 2009-05-18
> **Regenweald said:**
> What is under the Gnome Shell hood ? I am a one workspace person, so outside of clutter and workspaces, what am I looking forward to ?
Zeitgeist is quite exciting though.


Well, at this point its just playing with a concept---I'm not sure if it will work or not in the long run---but its different enough & like I said the devs have been at least thinking about the comments I have sent to them---So I'm hopeful that something good can be made with the bits that are being worked on.......After years of having made comments that seem to fall on deaf ears--it is a breath of fresh air to have someone on the other end at least listen.......;)

---

### Post by ronacc on 2009-05-18
If they actualy pay some heed to the input they get during developement it may turn out OK but if they just shove a bunch of ill thought out shinies at us things may not end well .

---

### Post by Merk42 on 2009-05-18
> **ronacc said:**
> If they actualy pay some heed to the input they get during developement it may turn out OK but if they just shove a bunch of ill thought out shinies at us things may not end well .

Yea, they need to pay attention to the input of GNOME **users**, not just GNOME **developers**

---

### Post by Regenweald on 2009-05-18
From a real world point of view, most of us have one workspace, our desk, and we manage activities using our little elevated trays. Engineers/ Artists etc. may have separate desks dedicated to entirely different tasks, but walking around a room to each desk may not be the most efficient way to get work done.

Rather than launching apps, and finding an efficient way to manage the apps we have now added another layer of multiple workspaces. 

Why not treat an application as a workspace ? Apply the same tabbing functionality that we love in our file managers to management of applications. need two, three apps at once ? key command, separate them into panels....

:)

---

### Post by coolen on 2009-05-19
Why would you need to walk around a room to get to a different workspace? Try hitting Ctrl+Alt+Right.

---

### Post by Keith Hedger on 2009-05-20
I just installed gnome-shell no problems compiling or running it I just don't see the point of it! It jumps about pushing icons off the desktop, cluttering my screen and does nothing that can't be done with a program like docky (I don't use it) or just a top gnome-panel and one of the many docks out there ( I use AWN ), this is a bit of unnecessary programming and in my opinion the time would have been better spent by the developers in creating an 'official' gnome dock as it seems more and more people are using docks, I have now un-installed it.

---

### Post by matthewbpt on 2009-05-20
Ok I built the gnome shell and while it was building the most bizare thing happened to all my fonts! see attached picture. All the gnome fonts seemed to have been corrupted and made diagonal! ... what do I do?!

---

### Post by loneowais on 2009-05-20
After working my way out of the dependency hell, I got Gnome Shell to build successfully. But to my disappointment it is running too slow. Like 1 frame in 5 secs. I'm on Intel x3100. I know this card has issues in jaunty but i've fixed them by using latest intel drivers from some PPA and Kernel 2.6.30 rc6.

My intel driver also has dri2 enabled. I can switch between 3d games and desktop by alt+tab. Also glx-gears works fine when rotating the cube.

Therefore this is not a gfx driver issue.

Any ideas?

---

### Post by 23meg on 2009-05-20
> **Merk42 said:**
> Yea, they need to pay attention to the input of GNOME **users**, not just GNOME **developers**

There are [various ways]("http://live.gnome.org/GnomeShell#head-b4b79cb03cd5682020839b4826100238bcf26430") for users to get involved. Reporting your experience and the bugs you've found in the ways described in the link will be better use of your time than bashing a project in its infancy with weasel words in a forum disconnected from its development.

---

### Post by tad1073 on 2009-05-20
got these errors whne I tried to run gnome shell

```

:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Checking for Xgl: thomas@ubuntu:~/gnome-shell/source/gnome-shell/src$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: ** (gnome-panel:31496): DEBUG: Adding applet 0.
** (gnome-panel:31496): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:31496): DEBUG: Adding applet 1.
present. 
Checking for non power of two support: 
(gnome-panel:31496): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
present. 
Checking for Composite extension: present. 
Checking screen 1** (gnome-panel:31496): DEBUG: Adding applet 2.
** (gnome-panel:31496): DEBUG: Adding applet 3.
** (gnome-panel:31496): DEBUG: Adding applet 4.
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```

---

### Post by Merk42 on 2009-05-20
> **23meg said:**
> There are [various ways]("http://live.gnome.org/GnomeShell#head-b4b79cb03cd5682020839b4826100238bcf26430") for users to get involved. Reporting your experience and the bugs you've found in the ways described in the link will be better use of your time than bashing a project in its infancy with weasel words in a forum disconnected from its development.

Well I plan to do that, but I mean a bigger sample.
GNOME needs to get something together where they just pull people off of the street to get their impressions.  They need to get a wider pool of people, not just existing GNOME users.

Right now it'll only be tested by those running GNOME (or at best those with another DE that don't mind a larger install).  If GNOME wants to improve itself, make it more attractive to new users, then it needs to be advertised to Joe User... but then again Linux as a whole has always had a problem with advertising.

---

### Post by tad1073 on 2009-05-20
> **tad1073 said:**
> got these errors whne I tried to run gnome shell

```

:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
Checking for Xgl: thomas@ubuntu:~/gnome-shell/source/gnome-shell/src$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: ** (gnome-panel:31496): DEBUG: Adding applet 0.
** (gnome-panel:31496): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:31496): DEBUG: Adding applet 1.
present. 
Checking for non power of two support: 
(gnome-panel:31496): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
present. 
Checking for Composite extension: present. 
Checking screen 1** (gnome-panel:31496): DEBUG: Adding applet 2.
** (gnome-panel:31496): DEBUG: Adding applet 3.
** (gnome-panel:31496): DEBUG: Adding applet 4.
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```


I figured it out. gnome-shell is pretty sweet IMO. 

It has a lot of bugs though.

searched for firefox, called it up and my system froze. ctrl+c brought me back to regular gnome.

The first time my sys. froze I had to do a hard reboot.

I expanded and colapsed the gnome-shell side-bar

---

### Post by autocrosser on 2009-05-20
If you have problems like that again---please create a bugzilla account & report the bug--at this stage of the shell anything that you report will most likely help in making it a better product........I know that bugzilla is a bit harder to nav than launchpad, but good reporting is critical...I posted the basic info in this thread about where to report--If anyone wants--I'll post it again..

---

### Post by autocrosser on 2009-05-21
> **Merk42 said:**
> Well I plan to do that, but I mean a bigger sample.
GNOME needs to get something together where they just pull people off of the street to get their impressions.  They need to get a wider pool of people, not just existing GNOME users.

Right now it'll only be tested by those running GNOME (or at best those with another DE that don't mind a larger install).  If GNOME wants to improve itself, make it more attractive to new users, then it needs to be advertised to Joe User... but then again Linux as a whole has always had a problem with advertising.

Yes--that is true, but there has been one study already:  [http://live.gnome.org/UsabilityProject/UsabilityTests/GnomeGeneralResearch](http://live.gnome.org/UsabilityProject/UsabilityTests/GnomeGeneralResearch)

It is also very interesting how many Ubuntu users are in the grouping.......

I was in the study as a early-adopter with the shell project...I think it was a good use of my time & hope the devs take a long look at the findings.

---

### Post by autocrosser on 2009-05-21
> **matthewbpt said:**
> Ok I built the gnome shell and while it was building the most bizare thing happened to all my fonts! see attached picture. All the gnome fonts seemed to have been corrupted and made diagonal! ... what do I do?!

Not sure what happened there---I would try another font & then logout/in to see if the problem goes away...

---

### Post by TrueTom on 2009-05-21
> **autocrosser said:**
> Yes--that is true, but there has been one study already:  [http://live.gnome.org/UsabilityProject/UsabilityTests/GnomeGeneralResearch](http://live.gnome.org/UsabilityProject/UsabilityTests/GnomeGeneralResearch)

It is also very interesting how many Ubuntu users are in the grouping.......

I was in the study as a early-adopter with the shell project...I think it was a good use of my time & hope the devs take a long look at the findings.

They are pretty creative when it comes to drawing conclusions. Basically this is just marketing.

---

### Post by tawmas on 2009-05-21
> **gnomeuser said:**
> [citation neeeded]

Sorry about chiming in late, I've just read through the whole thread...

I think Nullack was referring to Bruce Tognazzini's "Top Ten Reasons the Apple Dock Still Sucks" [1]. The article was written in 2001 and last updated in 2004, and at some point it was retitled as "Top Nine Reasons..."

When I read it I found it quite compelling (and applicable cross-platform). I'd need to reread it to see if it's still current, but I'd expect it to still be an interesting read at least for not repeating the same old errors.

In the article, Tognazzini self-describes himself this way:

> Bruce Tognazzini was hired at Apple by Steve Jobs and Jef Raskin in 1978, where he remained for 14 years, founding the Apple Human Interface Group and writing the first five editions of the Apple Human Interface Guidelines.

[1] [http://www.asktog.com/columns/044top10docksucks.html](http://www.asktog.com/columns/044top10docksucks.html)

---

### Post by Merk42 on 2009-05-21
> **TrueTom said:**
> They are pretty creative when it comes to drawing conclusions. Basically this is just marketing.

Yea, tell me about it
> # Top panel and menus need redesign because they are cluttered and hard to navigate through. 

So hey here's an idea, let's introduce a **third** panel on the left that pretty much does what the Activities button already does!

Not sure when that study was, but they should do another (maybe with the same people?) and show them what they have so far and get input from that.

And yes, 23meg, I installed it last night.

---

### Post by celticbhoy on 2009-05-21
I get this when I try to build 

```
WARNING: Skipping unknown interface GtkFileChooserEmbed
warning: Interface 'Activatable' virtual function 'update' has no known invoker
warning: Interface 'TreeSortable' virtual function 'set_sort_func' has no known invoker
warning: Interface 'TreeSortable' virtual function 'set_default_sort_func' has no known invoker
warning: Interface 'Editable' virtual function 'do_insert_text' has no known invoker
warning: Interface 'Editable' virtual function 'do_delete_text' has no known invoker
warning: Interface 'Editable' virtual function 'set_selection_bounds' has no known invoker
warning: Interface 'RecentChooser' virtual function 'get_recent_manager' has no known invoker
warning: Interface 'RecentChooser' virtual function 'set_sort_func' has no known invoker
make[2]: *** No rule to make target `Soup-2.4.gir', needed by `WebKit-1.0.gir'. Stop.
make[2]: Leaving directory `/home/gary/gnome-shell/source/gir-repository/gir'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gary/gnome-shell/source/gir-repository'
make: *** [all] Error 2
*** error during stage build of gir-repository: ########## Error running make   *** [2/6]

```

Any help.....

---

### Post by LittleKoy on 2009-05-23
It's extremely slow to me, moving a window around eats all my cpu and animations are laggy, as if hw accell wasn't enabled. 
Ok, my pc is not a monster (duron 1,6ghz, radeon 9200se + open drivers), but when using regular gnome everything is fast and smooth, with compiz effect activated, and moving around a window very fast doesn't suck more than 10-15% of cpu.

Am I the only one experiencing this?

PS: I heard JScript is used. I had the misfortune to develop in js only a couple of times, but I still find it a terrible language, especially if not used carefully. Why this choice? Also, isn't it gonna be slow? Or is compiled?

PPS: looks ingenious! :O

---

### Post by jimmyxx on 2009-06-15
I've just watched the screen cast for gnome-shell and seen the screenshots for Zeitgeist and I must admit I'm rather concerned. 

Personally I don't like the the look of Gnome-Shell as it's stands in the screen cast. I think it needs a lot more work on both the UI and the functionality if it's going to be a success. Maybe they should modularize the gnome shell so you can install you're own widgets to it instead of just recent documents & applications (recently used files in eclipse, bookamrks etc). I think the UI needs a *lot* of work, it looks very amateur at the moment. 

Zeitgeist looks quite promising but I think it should be integrated in to nautilus. Having another separate program purely for file exploring would just be totally annoying. Perhaps they could take a leaf out of gnome-do's book and have a key combination that opens a dialog to explore your files or perhaps this could be built into gnome-shell somehow? 

I've been really excited about the idea of gnome 3.0 for a couple of years, but now i've seen the ideas for it I'm more worried than anything else. It's probably a very good thing that kde 4.x is finally getting more stable.

---

### Post by jimmyxx on 2009-06-15
Using gnome-shell has only confirmed my suspicions, I really, *really* don't like it! I seriously hope there is a way to use the conventional panels and turn the shell off completely. 

As for usability i think it's bloody awful. It's a real step backward from where we are today. Also the fact it's taking more of my screen real estate by having a a sidebar is insane. The usability designers need to take a leaf out of google chrome's book, less is more, screen real-estate is very important!!!

I hope gnome 3.0 is a long way off because if it goes live with GnomeShell similar to this then it's going to be an absolute disaster imho.

---

### Post by olskar on 2009-06-15
> **jimmyxx said:**
> Using gnome-shell has only confirmed my suspicions, I really, *really* don't like it! I seriously hope there is a way to use the conventional panels and turn the shell off completely. 

As for usability i think it's bloody awful. It's a real step backward from where we are today. Also the fact it's taking more of my screen real estate by having a a sidebar is insane. The usability designers need to take a leaf out of google chrome's book, less is more, screen real-estate is very important!!!

I hope gnome 3.0 is a long way off because if it goes live with GnomeShell similar to this then it's going to be an absolute disaster imho.

Do they have usability designers? ;) I fully agree with you.

---

### Post by Legace on 2009-06-15
What the **** have the devs of GNOME Shell been thinking? It's absolutely hideous!

---

### Post by amano on 2009-06-15
I really hope that GNOME Shell will not make it into the default GNOME. There was nothing wrong with the old interface and it is the reason that I use GNOME. Clean and simple.

At least the old "way" should be left in as an option.

---

### Post by celticbhoy on 2009-06-15
It almost looks like they have got caught up in the whole netbook interface type of thing.

---

### Post by super.rad on 2009-06-16
Any info on when there will be an ubuntu package for this?
Also last time I used this it was painfully slow (turned out to be a driver problem, using the opensource ati drivers with no 3d/compositing) is this now fixed?

---

### Post by adult swim on 2009-06-16
can anyone get gnome-shell to build right now?

---

### Post by autocrosser on 2009-06-17
I'll try it--there have been 3 commits that could "barf" the build in the last 12 hours....

---

### Post by autocrosser on 2009-06-17
OK--I just ran a clean build with no errors---Make sure you do:```
curl -O http://git.gnome.org/cgit/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
/bin/bash gnome-shell-build-setup.sh
jhbuild build -f -a -c
```To build without using anything from past builds.....


Well--for the first time I have my customized lower panel--pity that the shell lower panel is still there, but at least I can "really" get to all my normal stuff..Now we need a way to not use the "official" lower--that would be much nicer.....

---

### Post by adult swim on 2009-06-17
for some reason every time i build, i get the error
*** Error during phase build of gjs: ########## Error running make   *** [5/6]

---

### Post by MacUntu on 2009-06-17
---

---

### Post by autocrosser on 2009-06-17
> **adult swim said:**
> for some reason every time i build, i get the error
*** Error during phase build of gjs: ########## Error running make   *** [5/6]

Hmmm---try deleting everything gnome-shell & then build it as per my last post....sometimes if you have something old in the build source you will have problems....

---

### Post by MacUntu on 2009-06-17
After a total cleanup it builds without errors here (but still runs VERY slow with the vesa driver).

---

### Post by Mazza558 on 2009-06-17
I say we scrap GNOME-shell, and instead keep the current base. However, don't try and reinvent what doesn't need fixing. I propose:

- Build gnome-do into future versions of GNOME and merge its features into the UI. Maybe a bar that decends from the top panel?

- A new menu which is less reliant on submenus and has a universal search function linked to gnome-do's database (this means more relevant options would pop up first)

- Build notify-osd into gnome default and make it interactive and customisable -  and also link it to gnome-do's database to retrieve twitter, facebook, and other social networking information, as well as news updates (which could be customisable for when you need to really work)

- Separate the notification area so that critical system functions, like volume, brightness, networking and power options stay easy to access.
 
- Combine gnome-do docky's features with the traditional program list - including pinning applications on the bar and context menus? Alternatively, just allow context menus. For example, right-clicking Pidgin in the program list should show my contacts and allow me to quickly change my status in a small menu.

- Increase drag-and-drop options. Dragging selected text onto programs in the window list should produce a response different for each program. If I drag text onto pidgin/empathy conversations, it should paste the contents into the message box.

---

### Post by Changturkey on 2009-06-17
> **Mazza558 said:**
> I say we scrap GNOME-shell, and instead keep the current base. However, don't try and reinvent what doesn't need fixing. I propose:

- Build gnome-do into future versions of GNOME and merge its features into the UI. Maybe a bar that decends from the top panel?

- A new menu which is less reliant on submenus and has a universal search function linked to gnome-do's database (this means more relevant options would pop up first)

- Build notify-osd into gnome default and make it interactive and customisable -  and also link it to gnome-do's database to retrieve twitter, facebook, and other social networking information, as well as news updates (which could be customisable for when you need to really work)

- Separate the notification area so that critical system functions, like volume, brightness, networking and power options stay easy to access.
 
- Combine gnome-do docky's features with the traditional program list - including pinning applications on the bar and context menus? Alternatively, just allow context menus. For example, right-clicking Pidgin in the program list should show my contacts and allow me to quickly change my status in a small menu.

- Increase drag-and-drop options. Dragging selected text onto programs in the window list should produce a response different for each program. If I drag text onto pidgin/empathy conversations, it should paste the contents into the message box.

One problem: Mono.

---

### Post by Mazza558 on 2009-06-17
> **Changturkey said:**
> One problem: Mono.

We already have F-spot using mono though...

---

### Post by Neon Lights on 2009-06-17
> **Mazza558 said:**
> We already have F-spot using mono though...
And Tomboy too.

---

### Post by zekopeko on 2009-06-17
> **Changturkey said:**
> One problem: Mono.

where is the problem exactly?

---

### Post by meeples on 2009-06-17
gnome-shell is pretty cool, but its not for a distobution like ubuntu.

its not user friendly and thats the whole point in ubuntu. i doubt very much ubuntu will use gnome 3.

---

### Post by super.rad on 2009-06-17
> **meeples said:**
> gnome-shell is pretty cool, but its not for a distobution like ubuntu.

its not user friendly and thats the whole point in ubuntu. i doubt very much ubuntu will use gnome 3.

It probably won't use it as default in 10.04 as thats going to be a LTS release but after that they'll start using it. Eventually it will be the only option

---

### Post by jimmyxx on 2009-06-18
> **Mazza558 said:**
> I say we scrap GNOME-shell, and instead keep the current base. However, don't try and reinvent what doesn't need fixing. I propose:

- Build gnome-do into future versions of GNOME and merge its features into the UI. Maybe a bar that decends from the top panel?

- A new menu which is less reliant on submenus and has a universal search function linked to gnome-do's database (this means more relevant options would pop up first)

- Build notify-osd into gnome default and make it interactive and customisable -  and also link it to gnome-do's database to retrieve twitter, facebook, and other social networking information, as well as news updates (which could be customisable for when you need to really work)

- Separate the notification area so that critical system functions, like volume, brightness, networking and power options stay easy to access.
 
- Combine gnome-do docky's features with the traditional program list - including pinning applications on the bar and context menus? Alternatively, just allow context menus. For example, right-clicking Pidgin in the program list should show my contacts and allow me to quickly change my status in a small menu.

- Increase drag-and-drop options. Dragging selected text onto programs in the window list should produce a response different for each program. If I drag text onto pidgin/empathy conversations, it should paste the contents into the message box.


I love your suggestions! :KS

I think if gnome shell goes ahead a couple of things needs to happen:

[LIST=1]
[*]The panels must stay along with shortcuts & panel widgets
[*]The gnome-shell gets a /hell/ of a lot more work done to it
[/LIST]

I think the gnome-shell team needs to look to the compiz-fusion developers, try the 'Expo' feature [Super+E], it works and looks a hundreds times better than gnome shell. They could shrink it down and add the functionality to find programs, documents etc. 

I would like gnome-shell more if it were modular so you can add/develop plugins for it such as google could release google-desktop search functionality, eclipse could show recent modified files / svn recent commits etc. I think it needs a more sophistiacted UI that would allow people to make it actually useful and something that would increase productivity.

If we keep panels then you could optionally choose to replace the "Main Menu" option with the gnome shell "Activities" button so people who really didn't want to use it didn't have to?

---

### Post by drkages on 2009-06-30
I have been doing a good bit of reading about the gnome shell, however I am unable to build it.
I get a series of errors which I think may be related to the ability of my git istallation from receiving the files from gnome's server.

Using the build instruction from gnome website i get the following error after running the command bash command

"Checking out jhbuild into /home/kyle/Source/jhbuild ... git.gnome.org[0: 209.132.176.202]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)"

I found another installation method at [link]("http://anotherubuntu.blogspot.com/2008/11/installing-gnome-shell-in-ubuntu.html") though older i realised they are mostly the same except it uses svn rather than git in the gnome-shell-build-setup.sh file.

at this point i get the error:
when running the command jhbuild build 

*** Checking out gobject-introspection *** [1/7]
git clone git://git.gnome.org/gobject-introspection
Initialized empty Git repository in /home/kyle/gnome-shell/source/gobject-introspection/.git/
git.gnome.org[0: 209.132.176.202]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)
*** error during stage checkout of gobject-introspection: ########## Error running git clone git://git.gnome.org/gobject-introspection *** [1/7]


Any help would be most appreciated

thanks

---

### Post by autocrosser on 2009-07-01
There was a fairly large amount of comits within the last 24 hours & a separate branch was folded into the shell, so expect problems with building it for the next couple of days--my build failed this evening & I'm going to wait a day or two for things to settle down.....

---

### Post by Joe_Bishop on 2009-07-01
Are you joking? Do you think gnome/gtk team spending so much time with optimization and startup to get things worse again with C# stuff?

---

### Post by | MM | on 2009-07-01
> **Mazza558 said:**
> I say we scrap GNOME-shell, and instead keep the current base. However, don't try and reinvent what doesn't need fixing...

I only read your opening paragraph... but i agree!  I like the GNOME foundation, usability wise.  

Henceforth i probably deviate from Mazza's points.

IMO where efforts should be focused is to provide a toolkit, graphically focused, that empowers people to be artistic.  By that i mean, if i want to (as a developer), graphically customise elements of the default widget-set, I caN  with relative ease.  I want to be able to draw on a VBoxes gtk.gdk.window and not have to worry about dealing with crazy artifacts (although im probably missing something)... .  I want to be able to provide some vector data to a gtk.Button and have it render as a 12 pointed star, so i can have 'Super Special that wont last' type buttons that still inherit all the gtk.state_xxxxx theme appearances... I want a toolkit that allows me to apply dropshadow or inner glow affects with ease, etc...

I know many will recoil at the thought of enhancing the ability of people to deviate from the default widget-set or such like, but this is open source -- file a bug if you think a deviation is ugly!!!

I think Gnome-Shell is admirable, but they don't realise that Opera exists and they could just ape that **** and be stellar!

What i want is a toolkit that allows for a greater degree of free form experimentation in a graphical sense ... no doubt a scene graph is a great leap in that direction.  IMHO let the great unwashed design the next Gnome shell ontop of a super uber flexible _graphical_ toolkit full of animations, shader and 3d/2d graphics capabilities. Amen.

---

### Post by davideotape on 2009-07-01
> **autocrosser said:**
> There was a fairly large amount of comits within the last 24 hours & a separate branch was folded into the shell, so expect problems with building it for the next couple of days--my build failed this evening & I'm going to wait a day or two for things to settle down.....

That looks like more commits in the last 24 hours than the last month :P And surprisingly, my build only failed on 1 stage.

---

### Post by Merk42 on 2009-07-01
Hopefully there are some improvements to the UI in this more recent build. The mini sidebar I thought was a horrible idea, I'd also like one of the many bottom panel ideas to have been implemented. 

[Speaking of UIs....](http://ubuntuforums.org/showthread.php?t=1172233)

---

### Post by davideotape on 2009-07-01
> **Merk42 said:**
> Hopefully there are some improvements to the UI in this more recent build. The mini sidebar I thought was a horrible idea 



Agreed on the sidebar. I brought it up on the mailing list, but there seemed to be a general idea that the more sidebars the better :(

---

### Post by drkages on 2009-07-01
> **autocrosser said:**
> There was a fairly large amount of comits within the last 24 hours & a separate branch was folded into the shell, so expect problems with building it for the next couple of days--my build failed this evening & I'm going to wait a day or two for things to settle down.....
Thanks for that indication, I was beginning to feel like I was alone.

Could you give us an inidication when you are able to rebuild 

most appreciated

---

### Post by frustphil on 2009-07-01
looks like gnome-shell development is gaining speed...:)

---

### Post by Merk42 on 2009-07-01
> **frustphil said:**
> looks like gnome-shell development is gaining speed...:)

Good it's accelerating, I'm just worried about where it's going.

---

### Post by nhasian on 2009-07-01
I would like to report that I was able to build gnome-shell today.  i just followed the instructions on their website and it compiled and ran just fine.  i played around it with it and its pretty neat.  not yet ready for prime time, but coming along nicely.

---

### Post by autocrosser on 2009-07-02
> **nhasian said:**
> I would like to report that I was able to build gnome-shell today.  i just followed the instructions on their website and it compiled and ran just fine.  i played around it with it and its pretty neat.  not yet ready for prime time, but coming along nicely.

The overlay has had the branch merged--now it works much more like I would like it to--no longer are the desktops pushed off the screen when you ask for "more" in overlay....very nice...

Anyone that can't build right now--save your custom mods & delete everything about the shell--the build-setup.sh & gnome-shell folder--do a clean build & it will come up fine.....

I also see a noticeable speed improvement dragging windows around--delay has been cut in half on my system...

Also look at the information icon during overlay.......

---

### Post by Bou on 2009-07-02
Could you guys please post a working deb?

---

### Post by autocrosser on 2009-07-02
> **Bou said:**
> Could you guys please post a working deb?

Its a bit much for a .deb & you'd not want it installed anywhere but in your home folder or in /opt at this time anyway....it is a easy build--not sure how long its taking the other guys, but my system builds it in 6~8 minutes--i7-920 system. 

There are a fair amount of depends that it needs, but the build script prompts for them--if your system is a bit tight for space you might not want to, but if you dont mind the extra dev stuff I really recommend giving it a go....

---

### Post by jimmyxx on 2009-07-02
oops wrong thread

---

### Post by Merk42 on 2009-07-02
> **autocrosser said:**
> Anyone that can't build right now--save your custom mods & delete everything about the shell--the build-setup.sh & gnome-shell folder--do a clean build & it will come up fine.....

Exactly what folders do I delete? This is my first time doing anything this technical (well second as I built it a first time).  Is there a special way I have to delete them?

---

### Post by Jay_Bee on 2009-07-02
Just delete the entire gnome-shell folder in your home folder and repeat the whole procedure from the wiki, I tried it and it worked fine, no errors.

---

### Post by davideotape on 2009-07-02
Hmm, did a completely clean install and it doesn't start for me. I made sure that desktop effects were disabled, so I'm not sure what's the problem. Any ideas on what could be wrong?

---

### Post by Merk42 on 2009-07-02
> **davideotape said:**
> Hmm, did a completely clean install and it doesn't start for me. I made sure that desktop effects were disabled, so I'm not sure what's the problem. Any ideas on what could be wrong?

You did run ```
cd ~/gnome-shell/source/gnome-shell/src
./gnome-shell --replace
``` right?

Mine took a few seconds to convert when I ran that script.

Also, while I do notice speed improvement, the sidebar is still there :(

---

### Post by afv on 2009-07-02
There's a package at Ubuntu Desktop's PPA, uploaded 1 hour ago.

[https://launchpad.net/~ubuntu-desktop/+archive/ppa](https://launchpad.net/~ubuntu-desktop/+archive/ppa)

> 
Package: gnome-shell
New: yes
State: installed
Automatically installed: no
Version: 0.0.1~git20090702-0ubuntu0.1
Priority: extra
Section: gnome
Maintainer: Sebastien Bacher <seb128@ubuntu.com>
Uncompressed Size: 729k
Depends: gjs, libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libclutter-0.9-0,
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.23.2), libgirepository1 (>= 0.5.0),
         libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.16.0), libgnome-menu2 (>= 2.15.4), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.22.0),
         libgnomevfs2-0 (>= 1:2.17.90), libgstreamer0.10-0 (>= 0.10.20), libgtk2.0-0 (>= 2.17.0), libice6 (>= 1:1.0.0), libnspr4-0d (>= 4.7.0~1.9b1), liborbit2 (>= 1:2.14.10),
         libpango1.0-0 (>= 1.14.0), libpopt0 (>= 1.14), librsvg2-2 (>= 2.26.0), libsm6, libwnck22 (>= 2.22.0), libx11-6, libxcomposite1 (>= 1:0.3-1), libxdamage1 (>= 1:1.1),
         libxext6, libxfixes3 (>= 1:4.0.1), libxml2 (>= 2.6.27), libxss1, zlib1g (>= 1:1.1.4), gconf2 (>= 2.10.1-2), mutter, gobject-introspection-glib-2.0,
         gobject-introspection-repository
Description: redefines user interactions with the GNOME desktop
 The GNOME Shell redefines user interactions with the GNOME desktop. In particular, it offers new paradigms for launching applications, accessing documents, and organizing open
 windows in GNOME. Later, it will introduce a new applets eco-system and offer new solutions for other desktop features, such as notifications and contacts management. The GNOME
 Shell is intended to replace functions handled by the GNOME Panel and by the window manager in previous versions of GNOME. The GNOME Shell has rich visual effects enabled by
 new graphical technologies.


---

### Post by Merk42 on 2009-07-02
Ugh, where is the mailing list for this?
The window performance is better, but the UI is even worse (yes I realize still early)

[list][*]No idea how to subtract desktops
[*] Don't know how to add applications to the sidebar
[*] I don't like the sidebar anyway, GNOME is supposed to be simple, why introduce a **third** area?
[*]It seems the only way to find an application is by typing it in[/list]

---

### Post by davideotape on 2009-07-02
Wo, I'm using the usual commands to replace with gnome-shell. It just flickers about, then seems to abort and flickers back to my origional desktop. And the mailing list is here:  mailto:gnome-shell-list@gnome.org

---

### Post by MacUntu on 2009-07-02
> **davideotape said:**
> Wo, I'm using the usual commands to replace with gnome-shell. It just flickers about, then seems to abort and flickers back to my origional desktop.

Same here. Starting it nested (without '--replace') works, though.

---

### Post by superfoor on 2009-07-02
Do you have Compiz off?

Mine failed just like that when i was running desktop effects

---

### Post by davideotape on 2009-07-02
did put appearance effects to zero, but next time I'll try sudo killall compiz before trying to replace.

---

### Post by autocrosser on 2009-07-02
That sounds 'bout right---I do not run a composite manager other than Gnome Shell & I do not "seem" to have any problems with starting (other than getting it to build ;)  )--If you really want to play it safe--run it as another user.....

---

### Post by 23meg on 2009-07-02
> **Merk42 said:**
> Ugh, where is the mailing list for this?

[http://mail.gnome.org/mailman/listinfo/gnome-shell-list](http://mail.gnome.org/mailman/listinfo/gnome-shell-list)

You may want to read [http://live.gnome.org/GnomeShell/NotesAboutDesktopUsage](http://live.gnome.org/GnomeShell/NotesAboutDesktopUsage) and [http://live.gnome.org/GnomeShell/UserResearch](http://live.gnome.org/GnomeShell/UserResearch) first.

---

### Post by Bou on 2009-07-03
> **Merk42 said:**
> Ugh, where is the mailing list for this?
The window performance is better, but the UI is even worse (yes I realize still early)

[list][*]No idea how to subtract desktops
[*] Don't know how to add applications to the sidebar
[*] I don't like the sidebar anyway, GNOME is supposed to be simple, why introduce a **third** area?
[*]It seems the only way to find an application is by typing it in[/list]

I agree with all of the points above.

---

### Post by autocrosser on 2009-07-03
> **Bou said:**
> I agree with all of the points above.

You must remember that the Shell is under constant development right now--if anyone is not liking parts of it--get in & involved with the process--that is what I'M DOING..that way I CAN have a say in the direction it goes. I also can remember that there was the same amount of "discussion" surrounding the move from Gnome1 to Gnome2--And--Gee, it seems that people have got use to Gnome2 just fine---I am sure once Gnome3 is stable there will no end of mods to make it almost anyway one wishes it to look.....

By-the-by--looks like Sebastien heard your want-------> Date: Fri, 03 Jul 2009 18:20:54 -0000
From: Sebastien Bacher [EMAIL="seb128@ubuntu.com"]<seb128@ubuntu.com>[/EMAIL]
Subject: [ubuntu/karmic] gnome-shell 0.0.1~git20090702-0ubuntu0.2
    (Accepted)
To: [EMAIL="karmic-changes@lists.ubuntu.com"]karmic-changes@lists.ubuntu.com[/EMAIL]
Message-ID:
    [EMAIL="20090703182054.6285.62515.launchpad@cocoplum.canonical.com"]<20090703182054.6285.62515.launchpad@cocoplum.canonical.com>[/EMAIL]
Content-Type: text/plain; charset="utf-8"

gnome-shell (0.0.1~git20090702-0ubuntu0.2) karmic; urgency=low

  * debian/control:
    - recommends xserver-xephyr

Date: Thu, 02 Jul 2009 19:48:06 +0200
Changed-By: Sebastien Bacher [EMAIL="seb128@ubuntu.com"]<seb128@ubuntu.com>[/EMAIL]
[https://launchpad.net/ubuntu/karmic/+source/gnome-shell/0.0.1~git20090702-0ubuntu0.2]("https://launchpad.net/ubuntu/karmic/+source/gnome-shell/0.0.1%7Egit20090702-0ubuntu0.2")


---

### Post by Merk42 on 2009-07-03
> **autocrosser said:**
> --if anyone is not liking parts of [GNOME Shell]--get in & involved with the process--

I know you were responding to Bou and not myself, but is there a better way to get involved other than the mailinglist?

---

### Post by autocrosser on 2009-07-03
Well--the list is the "best" way--I got involved very early & emailed several of the developers with polite questions & gentle suggestions--that was taken very well & I have seen several of my "thoughts" worked on---maybe not to the degree I want, but just applying a bit of pressure on the wheel steers things to a better outcome....

As with anything Gnome--one "feels" like man vs mountain--but I have found if one talks quietly & with positive reinforcement--mountains can be moved.

---

### Post by autocrosser on 2009-07-04
Several commits within the last 24hrs--biggest change is in the way the recent apps are displayed in the sidebar & Activities list...nothing earth-shaking, but steady progress....I noted on the list that talk is going forward about replacing the lower panel--I say about time!!!!!

---

### Post by Jay_Bee on 2009-07-05
"Jeremy helped me put together a nice animated mockup of what [Message Tray] may look like.  [Check it out!]("http://www.gnome.org/~mccann/shell/mockups/20090630-demo/")
You can read more about this and the rest of the GNOME Shell design concepts in a document I&#8217;ve put together to try to explain it to myself and others.  I should emphasize that this is a living document that we&#8217;ll try to keep up-to-date as things evolve.  [Check it out]("http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf") and let me know what you think."

From: [http://blogs.gnome.org/mccann/2009/07/05/getting-the-message](http://blogs.gnome.org/mccann/2009/07/05/getting-the-message)

Flame away guys! ;-)

---

### Post by tgpraveen on 2009-07-05
i wonder what this means for messaging indicator from canonical and also from what i can tell all they have done is that the current windows list they have transfered to top and the tray icons and applets transfered to bottom bar and made it on auto hide or something.

---

### Post by volanin on 2009-07-05
> **tgpraveen said:**
> i wonder what this means for messaging indicator from canonical and also from what i can tell all they have done is that the current windows list they have transfered to top and the tray icons and applets transfered to bottom bar and made it on auto hide or something.

From the PDF they explain that only the CURRENTLY ACTIVE window is listed in the top panel, so you don't have to depend on hints from the window border. Also, there is no tray defined yet. The bottom panel only hosts notifications and notification queues (the icons on the right side), so that you can refer to the messages you ignored at a later time.

It's an interesting read:
[http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf](http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf)

---

### Post by 89c51 on 2009-07-05
Gnome shell seems to complicate things more :-?

first of all it adds more clicks in order to perform a task (ie start an app)

Do-ification should have been one of the top priorities 


what also should be included -and i dont thing anyone is working on that in order to be ready for gnome 3- is a global address book (mail IM Voip etc) available on the desktop (click->scroll->contact) 

the tray thing seems like duplication :? :sad:

---

### Post by Merk42 on 2009-07-05
Anyone in this thread with strong opinions should subscribe to [the mailing list](http://mail.gnome.org/mailman/listinfo/gnome-shell-list) and make it known.

---

### Post by CarpKing on 2009-07-06
> **89c51 said:**
> what also should be included -and i dont thing anyone is working on that in order to be ready for gnome 3- is a global address book (mail IM Voip etc) available on the desktop (click->scroll->contact) 

There is talk of a "People" menu, but I don't know what they have in mind.  Gnome has an integrated contacts list through Evolution Data Server, and there is talk of tying it to IM through Telepathy, but the only thing that currently uses it is the clunker/Outlook clone Evolution.  None of this is directly related to the shell, though, and that seems to be the focus of Gnome 3 along with cleanup work to make implementing new stuff easier.

---

### Post by 89c51 on 2009-07-06
> **Merk42 said:**
> Anyone in this thread with strong opinions should subscribe to [the mailing list](http://mail.gnome.org/mailman/listinfo/gnome-shell-list) and make it known.


sadly if someone is not a developer -that can implement features by himself- has zero chances of getting his voice heard or his ideas materialized

---

### Post by Merk42 on 2009-07-19
Bumping this thread since I made the [wiki](https://wiki.ubuntu.com/gnomeshell) zekopeko and 23meg suggested in the [Gran Canaria Desktop Summit thread](http://ubuntuforums.org/showthread.php?t=1205594)
It's pretty barren and probably 'wrong', but that's because I've never done one before.  While I'm inexperienced in making a wiki like this, I felt I had to do *something*.

---

### Post by shafin on 2009-07-23
I am not getting a semi transparent panel, instead a black one. Anyone know how to change color of Gnome Shell?

---

### Post by ricsi-pontaz on 2009-08-05
Edit: Problem solved! It is works!

---

### Post by Vaun on 2009-08-11
Just uploaded to Karmic.

gnome-shell (2.27.0-0ubuntu1) karmic; urgency=low

  * New upstream version

---

### Post by TrueTom on 2009-08-11
If you believe that Gnome Shell is a wrong step in the wrong direction, you can chip in here:

[http://blogs.gnome.org/aklapper/2009/08/11/gnome-3-update-module-proposals-welcome-now/]("http://blogs.gnome.org/aklapper/2009/08/11/gnome-3-update-module-proposals-welcome-now/")

---

### Post by Joe_Bishop on 2009-08-11
And how this article can change their (and mine too) opinion?

---

### Post by MaX on 2009-08-11
It can't.... so could someone make a .deb of the tarball they released of gnome-shell?

---

### Post by TrueTom on 2009-08-11
It probably can't which is part of the problem. I actually have given up on that topic already and accepted my fate that I have to switch to a Mac eventually. At least the day Ubuntu ships with gnome-shell as default and there is no easy way to restore gnome-panel.

It' still fun to mess with people, though... :)

---

### Post by Merk42 on 2009-08-11
> **TrueTom said:**
> It probably can't which is part of the problem. I actually have given up on that topic already and accepted my fate that I have to switch to a Mac eventually. At least the day Ubuntu ships with gnome-shell as default and there is no easy way to restore gnome-panel.

It' still fun to mess with people, though... :)

Why would you switch to Mac?
Wouldn't it be far easier to just switch to KDE or XFCE?

---

### Post by wayne_cat on 2009-08-11
> **MaX said:**
> It can't.... so could someone make a .deb of the tarball they released of gnome-shell?

Just wait for an hour or two ... it is already in the queue:

[https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=](https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=)

---

### Post by Merk42 on 2009-08-11
> **wayne_cat said:**
> Just wait for an hour or two ... it is already in the queue:

[https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=](https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=)

Is that why I get an error trying to build it (albeit in a VM running Jaunty)
```
*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/merk/gnome-shell/install --libdir '/home/merk/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [7/7]

```

---

### Post by wayne_cat on 2009-08-11
> **Merk42 said:**
> Is that why I get an error trying to build it (albeit in a VM running Jaunty)
```
*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/merk/gnome-shell/install --libdir '/home/merk/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [7/7]

```

do you try to build the deb with dpkg-buildpackage?

(no problems on my Karmic system)

---

### Post by Merk42 on 2009-08-11
> **wayne_cat said:**
> do you try to build the deb with dpkg-buildpackage?

(no problems on my Karmic system)

I tried building the same way I successfully have in the past on my actual (read not VM) install of Jaunty.  The jhbuild instructions [on GNOME's site](http://live.gnome.org/GnomeShell)

---

### Post by Jay_Bee on 2009-08-11
you need to install libgnome-desktop-dev package

---

### Post by wayne_cat on 2009-08-11
Tried to compile it via jhbuild on Jaunty ... result:

```
*** success *** [7/7]
```I have to agree ...  one or more missing dependencies

---

### Post by Merk42 on 2009-08-11
> **wayne_cat said:**
> Tried to compile it via jhbuild on Jaunty ... result:

```
*** success *** [7/7]
```I have to agree ...  one or more missing dependencies

Got it to build after adding the libgnome-desktop-dev package.  Unfortunately it doesn't render correctly in the VM. Also, still nothing for the bottom area?

I hope they don't expect the user to constantly click on Activities just to see what they currently have running.

---

### Post by wayne_cat on 2009-08-11
> **Merk42 said:**
> Got it to build after adding the libgnome-desktop-dev package.  Unfortunately it doesn't render correctly in the VM. Also, still nothing for the bottom area?

I hope they don't expect the user to constantly click on Activities just to see what they currently have running.

The whole screen is quite blurry if I start gnome-shell ... I can stand it only for a view minutes ... the whole thing is a bad joke ... no usability ... freaking huge fonts and icons.

---

### Post by frustphil on 2009-08-16
I noticed there's no task manager yet. Any idea when it will be implemented? And which one is likely to succeed?
a. [Clever Windows]("http://www.youtube.com/watch?v=lsZvwyxJ9vk")
b. [Breadcrumbs on the panel]("http://live.gnome.org/GnomeShell/DesignerPlayground/BreadcrumbsEtc")
c. [Task list as a drop down list]("http://live.gnome.org/GnomeShell/DesignerPlayground/TaskListDropDown")
d. [Shelf]("http://farm4.static.flickr.com/3577/3443594832_dac308e054_o.png")

My thoughts...
a. Is too animated I guess and not very intuitive.
b. Is really great, but where can I find other active windows when the current window is maximized? And contradicts the aim on removing bottom panel.
c. Is the cleanest and the most efficient in terms of screen estate. But, adds one more step (that is hovering) in locating/finding a task. But I guess this method is more efficient when there are many tasks running than the current one.
d. Works like a dock. But I don't like the idea of it being hidden and can only be accessed by hovering against hot corners. And it also takes a lot of screen estate.

Note: there are several other proposed methods but IMHO, they're not as viable as the ones I mentioned above.

---

### Post by Regenweald on 2009-08-16
> **wayne_cat said:**
> The whole screen is quite blurry if I start gnome-shell ... I can stand it only for a view minutes ... the whole thing is a bad joke ... no usability ... freaking huge fonts and icons.

Because of all the OTHER improvements in Gnome 3.0 and the fact that I will probably not need the 'add workspace' and can thus bypass it, I do support the project, but I am at a loss as to how the existing framework can be turned into anything stable and functional in 8 months. Short of magic. That is my biggest concern.

maybe drop the cool way to add a workspace, leave the Desktop+panel infrastructure(for now)and concentrate on integrating new tech like clutter, zeitgiest and sabayon into one of the already most stable and functional DE's around.

---

### Post by coolen on 2009-08-16
I imagine the initial release of Gnome 3.0 will be something like that of KDE 4.0: not really stable, to be polished on the next release.

---

### Post by meborc on 2009-08-16
> **coolen said:**
> I imagine the initial release of Gnome 3.0 will be something like that of KDE 4.0: not really stable, to be polished on the next release.

fortunately we have kde 4.4 by the time... and i'm already migrating :). i love gnome, but this is way too shaky for me to start acclimating... lets see what the devs can come up with

---

### Post by coolen on 2009-08-16
I tried moving to Kubuntu a while back, but for some reason plasma was holding back kernel updates in KPackageKit. I did a dist-upgrade, and plasma would never run again.

4.3 does look pretty fantastic, I must say. I think I'll give it another go for Karmic.

---

### Post by Merk42 on 2009-08-16
> **frustphil said:**
> I noticed there's no task manager yet. Any idea when it will be implemented? And which one is likely to succeed?
a. [Clever Windows]("http://www.youtube.com/watch?v=lsZvwyxJ9vk")
b. [Breadcrumbs on the panel]("http://live.gnome.org/GnomeShell/DesignerPlayground/BreadcrumbsEtc")
c. [Task list as a drop down list]("http://live.gnome.org/GnomeShell/DesignerPlayground/TaskListDropDown")
d. [Shelf]("http://farm4.static.flickr.com/3577/3443594832_dac308e054_o.png")

My thoughts...
a. Is too animated I guess and not very intuitive.
b. Is really great, but where can I find other active windows when the current window is maximized? And contradicts the aim on removing bottom panel.
c. Is the cleanest and the most efficient in terms of screen estate. But, adds one more step (that is hovering) in locating/finding a task. But I guess this method is more efficient when there are many tasks running than the current one.
d. Works like a dock. But I don't like the idea of it being hidden and can only be accessed by hovering against hot corners. And it also takes a lot of screen estate.

Note: there are several other proposed methods but IMHO, they're not as viable as the ones I mentioned above.

I [just asked about](http://mail.gnome.org/archives/gnome-shell-list/2009-August/msg00039.html) that yesterday in the GNOME shell mailinglist.
[The answer](http://mail.gnome.org/archives/gnome-shell-list/2009-August/msg00040.html)? There won't be any **at all**
That's right! If you want to see what is running/change applications you either have to use the overlay or alt-tab.

Source:
[GNOME Design Document](http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf)

---

### Post by TrueTom on 2009-08-16
Something I read on planet.ubuntu today:

> Im quite the opposite I really like Gnome-Shell I think that it is the right way to do things and that innovation is what make Free and Open source software great. We put our heads together and come up with useful ways to do things. Gnome-Panel is basic and does the job at the moment but compared to our rivals microsoft and mac we are lagging behind. We need something special and Gnome-Shell love it or hate it is special and unique.

So, basically it doesn't matter if it's crap or not. As long as it new it's per definition good.

---

### Post by coolen on 2009-08-16
I must say, that is what the Gnome Shell is sounding like.

Too eager to get into shifting paradigms, not spending enough time considering what's wrong (or perhaps more importantly, right) with the existing one.

I think Gnome 3.0 may be very good news for KDE, or, if done improperly, Apple (I don't imagine a lot of people flocking back to Windows over this. After all, that's where most have flocked from).

---

### Post by frustphil on 2009-08-16
> **Merk42 said:**
> I [just asked about]("http://mail.gnome.org/archives/gnome-shell-list/2009-August/msg00039.html") that yesterday in the GNOME shell mailinglist.
[The answer]("http://mail.gnome.org/archives/gnome-shell-list/2009-August/msg00040.html")? There won't be any **at all**
That's right! If you want to see what is running/change applications you either have to use the overlay or alt-tab.

Source:
[GNOME Design Document]("http://www.gnome.org/%7Emccann/shell/design/GNOME_Shell-20090705.pdf")

I see. It surprised me a little bit to know there won't be any. But from what I observed about the shift to overlay, I think it makes sense. It gives you the ability to launch and choose running apps at the same time. Plus, the apps on the workspace preview are presented as thumbnails (windows 7 like) which is a good improvement. I am worried though about adding too many workspaces (say you have over 6) may make thumbnails too small to identify.

BTW, GNOME Design Document is very well thought IMO.

---

### Post by Merk42 on 2009-08-16
> **frustphil said:**
> BTW, GNOME Design Document is very well thought IMO.

I'm going to have to disagree.  A desktop environment that doesn't show what applications I'm currently running (without any interaction from the user) doesn't seem very well thought out.

Regardless, I'll be interesting to see the reaction once GNOME Shell is released and used by more people. I'm eager to see the thoughts from an average GNOME user, not the testers/coders that have been using it so far.

---

### Post by qamelian on 2009-08-16
> **TrueTom said:**
> Something I read on planet.ubuntu today:

So, basically it doesn't matter if it's crap or not. As long as it new it's per definition good.
Whether it is crap or not is very much a matter of opinion. Although I don't like everything that is being done with gnome-shell, I do like most of it. I also find that the latest build has taken a noticeable leap forward in performance. It now feels substantially faster than the current Gnome desktop on my aging laptop. 

Frankly, I'm looking forward to following the continued development of gnome-shell, as well as other aspects of Gnome 3.

---

### Post by frustphil on 2009-08-16
> **Merk42 said:**
> I'm going to have to disagree.  A desktop environment that doesn't show what applications I'm currently running (without any interaction from the user) doesn't seem very well thought out.

For me, I don't mind swaying my mouse against the top-left corner to view them. Yes it would have been nice to instantly see them, but how?

---

### Post by Merk42 on 2009-08-16
> **frustphil said:**
> For me, I don't mind swaying my mouse against the top-left corner to view them. Yes it would have been nice to instantly see them, but how?

As I suggested in the mailing list, why not take the idea on page 22 & 23 of the design document and put it in the lower left? That area as of right now is unused.

---

### Post by autocrosser on 2009-08-16
I'm very sure once a larger group starts using the Shell there will be lots of hacks & add-ons--what we are seeing is the core development only......After it is "really" out for a couple of months will tell where it goes. 

Projects like Gnome-Do, AWN Dock & others will just find other ways around the coding--so a Shell for everyone's needs will be quite soon.

---

### Post by frustphil on 2009-08-16
> **Merk42 said:**
> As I suggested in the mailing list, why not take the idea on page 22 & 23 of the design document and put it in the lower left? That area as of right now is unused.

Then it would be like Dock if I understood you correctly. They probably won't allow that.

---

### Post by wayne_cat on 2009-08-16
> **frustphil said:**
> Then it would be like Dock if I understood you correctly. They probably won't allow that.

you can still start things like cairo-dock or awn

---

### Post by Merk42 on 2009-08-16
> **wayne_cat said:**
> you can still start things like cairo-dock or awn

I think frustphil means the GNOME devs wouldn't allow such a thing to be in by default with the GNOME Shell.
Though why they wouldn't allow that, but will allow that awful sidebar is beyond me.

I'm going to have to look into AWN/Docky etc, because I'm have the bizarre notion that I should be able to easily see what different tasks I'm running in a multitasking OS.

---

### Post by zekopeko on 2009-08-16
> **wayne_cat said:**
> you can still start things like cairo-dock or awn

But the point is that such functionality should be provided by the default desktop shell not 3rd party addons.
I can't wait to see people looking for their running applications.
They also put emphasis on Alt-Tab and that is a power users tool. Not to mention that you have to either use the keyboard or have excessive mouse clicks to reach the application you want.

Major fail here is that they aren't testing this on regular users. Anybody who can compile the shell from scratch isn't a regular user. Ubuntu/Canonical has it right: Before deploying UI changes do some usability testing.

---

### Post by Regenweald on 2009-08-16
Initially, the design gave me a very laptop centric, for coders feel. Looking forward to being wrong I hope.

@zekopeko: I think 'regular' user testing will come in once the product can be easily installed and used. currently it does take some doing just to install so the larger user base will encounter it in a bit.

---

### Post by wayne_cat on 2009-08-16
> **Merk42 said:**
> I think frustphil means the GNOME devs wouldn't allow such a thing to be in by default with the GNOME Shell.
Though why they wouldn't allow that, but will allow that awful sidebar is beyond me.

I'm going to have to look into AWN/Docky etc, because I'm have the bizarre notion that I should be able to easily see what different tasks I'm running in a multitasking OS.

here is a screenshot of AWN ... 

- left of the separator: the Launchers (to start an application)
- right of the separator: the running instances (2x Firefox & 2x Nautilus)

if you remove the Launchers you will have a plain "What is running" dock

BTW .. you can hide the sidebar in the latest gnome-shell version

[[IMG]http://ubuntu-pics.de/thumb/22091/screen_X3gVvC.png[/IMG]]("http://ubuntu-pics.de/bild/22091/screen_X3gVvC.png")

---

### Post by zekopeko on 2009-08-16
> **Regenweald said:**
> Initially, the design gave me a very laptop centric, for coders feel. Looking forward to being wrong I hope.

@zekopeko: I think 'regular' user testing will come in once the product can be easily installed and used. currently it does take some doing just to install so the larger user base will encounter it in a bit.

By the time Gnome-Shell is easily installed it's going to be deployed. You are supposed to do user testing before you ship a product.

My other beef with GS is that they used some funky reasoning to make it workspace centric. They actually took the number of workspaces distributions ship as a way of showing that users actually USE them.

Then they ignore Ubuntu's notification work that would fit perfectly with GS goals. Notify-OSD is a perfect example of excellently thought out policies for showing user real-time information. And I'm not just talking about the "bubble" but the whole spec with morphing windows and messaging menu.

---

### Post by zekopeko on 2009-08-16
> **wayne_cat said:**
> here is a screenshot of AWN ... 

- left of the separator: the Launchers (to start an application)
- right of the separator: the running instances (2x Firefox & 2x Nautilus)

if you remove the Launchers you will have a plain "What is running" dock

BTW .. you can hide the sidebar in the latest gnome-shell version

[[IMG]http://ubuntu-pics.de/thumb/22091/screen_X3gVvC.png[/IMG]]("http://ubuntu-pics.de/bild/22091/screen_X3gVvC.png")

A good thing would be to have Dockey married with Windows 7's task bar way of showing multiple running instances of the same application. Mouse over and shiny window previews pop out. The little dot(s) show if there is only a single instance of the application or multiple one's.
Add basic search for application and folder that Dockey can do and you are full of win.

---

### Post by wayne_cat on 2009-08-16
> **zekopeko said:**
> A good thing would be to have Dockey married with Windows 7's
task bar way of showing multiple running instances of the same application. Mouse over and shiny window previews pop out. The little dot(s) show if there is only single instance of the application or multiple one's.
Add basic search for application and folder that Dockey can do and you are full of win.

You can add the "preview function" with compiz. I works at least with AWN and the standard Gnome panel .. I don't have Docky on my system ... so I can not test it.

Windows7 is really not bad .. the first Windows version since Win95 that I like ;)

---

### Post by zekopeko on 2009-08-16
> **wayne_cat said:**
> You can add the "preview function" with compiz. I works at least with AWN and the standard Gnome panel .. I don't have Docky on my system ... so I can not test it.

Windows7 is really not bad .. the first Windows version since Win95 that I like ;)

Dockey/Compiz needs to fix a bug where the previews are way above the icon. Also Win7 windows previews have some other nice features such as being able to select and close windows from it and showing tabs for app such as IE8 or FF.

And Win7 is a good operating system.

---

### Post by frustphil on 2009-08-16
> **zekopeko said:**
> A good thing would be to have Dockey married with Windows 7's task bar way of showing multiple running instances of the same application. Mouse over and shiny window previews pop out. The little dot(s) show if there is only a single instance of the application or multiple one's.
Add basic search for application and folder that Dockey can do and you are full of win.

You mean something like [this]("http://www.kdedevelopers.org/node/4038")? Plus notification applet and notify-osd it would be awesome.

Given this would be implemented, I would remove the overlay and bring back the old menu bar or make a unified menu.

---

### Post by frustphil on 2009-08-16
> **zekopeko said:**
> 
Then they ignore Ubuntu's notification work that would fit perfectly with GS goals. Notify-OSD is a perfect example of excellently thought out policies for showing user real-time information. And I'm not just talking about the "bubble" but the whole spec with morphing windows and messaging menu.

That's why I am thrilled of what Canonical will do with the shell.

---

### Post by Merk42 on 2009-08-16
> **wayne_cat said:**
> 
BTW .. you can hide the sidebar in the latest gnome-shell version
I know I can hide it. My point is you say they wouldn't allow a dock for what is running, yet allow a dock (called sidebar) for launching?

> **frustphil said:**
> That's why I am thrilled of what Canonical will do with the shell.
Is Canonical going to do anything? I made [a wiki](https://wiki.ubuntu.com/gnomeshell) a while ago as far as Ubuntu's GNOME Shell and it hasn't seen any activity. Maybe I just didn't set it up correctly, I've never done that sort of thing before.

---

### Post by frustphil on 2009-08-16
> **Merk42 said:**
> 
Is Canonical going to do anything? I made [a wiki]("https://wiki.ubuntu.com/gnomeshell") a while ago as far as Ubuntu's GNOME Shell and it hasn't seen any activity. Maybe I just didn't set it up correctly, I've never done that sort of thing before.

I'm sorry.. That should be "would do" not "will do". 
I hope they will...:)

---

### Post by Bastanteroma on 2009-08-16
Anyone know how to use the packaged version of Gnome Shell? I've tried running "gnome-shell" form within old Gnome with Compiz running, but all I get is a black xephyr window with xeyes and an xterm.

---

### Post by wayne_cat on 2009-08-16
> **Bastanteroma said:**
> Anyone know how to use the packaged version of Gnome Shell? I've tried running "gnome-shell" form within old Gnome with Compiz running, but all I get is a black xephyr window with xeyes and an xterm.

try this:

```
gnome-shell --replace
```

---

### Post by autocrosser on 2009-08-16
You will also need to turn Compiz off--Gnome-shell starts it's own composted session.

---

### Post by rgbrown on 2009-08-17
> **autocrosser said:**
> You will also need to turn Compiz off--Gnome-shell starts it's own composted session.

:) Was that an intentional typo?

---

### Post by Merk42 on 2009-08-17
> **autocrosser said:**
> You will also need to turn Compiz off--Gnome-shell starts it's own composted session.

I never need to turn it off, but if GNOME Shell doesn't work, then turn it off.

---

### Post by Bastanteroma on 2009-08-17
"gnome-shell --replace" worked fine, in the sense that it started Gnome Shell, even with Compiz running. Sadly, I can't say that Gnome Shell itself worked fine. I'll be waiting, fingers crossed, for the approach to make sense to me.

---

### Post by Merk42 on 2009-08-17
> **Bastanteroma said:**
> "gnome-shell --replace" worked fine, in the sense that it started Gnome Shell, even with Compiz running. Sadly, I can't say that Gnome Shell itself worked fine. I'll be waiting, fingers crossed, for the approach to make sense to me.

If it doesn't now, it never will.  That's not a dig against you though, I feel the same way.

Someone tell me how I can easily view/empty the trash in GNOME Shell?

---

### Post by shafin on 2009-08-17
This guy has implementedsome very nice features on gnome-shell. Check his blog out:
[http://linux4kix.blogspot.com/](http://linux4kix.blogspot.com/)


[IMG]http://lh4.ggpht.com/_mlDCGSyb6_w/Smg4mB6jJuI/AAAAAAAAAeI/AogK78w-brA/s640/gnome-shell-netbook2.png[/IMG]


Video: [http://www.youtube.com/watch?v=KL8472OXtAg](http://www.youtube.com/watch?v=KL8472OXtAg)

---

### Post by Rackstar on 2009-08-17
That's pretty cool!

I'll still change desktops using shortcuts. But I'm a shortcut guy. 90% (guess) of the people are point & click. I like the fact that you can "preview" the workspace, but that is probably the whole point.

---

### Post by celticbhoy on 2009-08-17
gary@Testing:~$ gnome-shell --replace
    JS ERROR: !!!   REPORTED: 'reserved slot index out of range'
    JS ERROR: !!!   REPORTED: file '(null)' line 0 exception 0 number 166
Failed to init standard javascript classes

gary@Testing:~$ Cannot register the panel shell: there is already one running.


Getting the above, any help guys.

Using PPA version.

---

### Post by Darkshade on 2009-08-17
Same problem here.

---

### Post by qamelian on 2009-08-17
I got the same errors using the version in the PPA, so I built it myself using the instructions at [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell). This seems to work fine. In its current state, I find the performance of gnome-shell to be greatly improved. It's still missing some stuff and it's different enough from 'old Gnome' to take some getting used to, but it's starting to grow on me. :)

---

### Post by rudenko_ruslan on 2009-08-17
Why using GNOME Shell from PPA? There is a package "gnome-shell" in Ubuntu's repos.

---

### Post by ricsi-pontaz on 2009-08-17
> **celticbhoy said:**
> gary@Testing:~$ gnome-shell --replace
    JS ERROR: !!!   REPORTED: 'reserved slot index out of range'
    JS ERROR: !!!   REPORTED: file '(null)' line 0 exception 0 number 166
Failed to init standard javascript classes

gary@Testing:~$ Cannot register the panel shell: there is already one running.


Getting the above, any help guys.

Using PPA version.

Remove xulrunner 1.9, because an other version (1.9.1) is installed too!

---

### Post by autocrosser on 2009-08-17
> **rgbrown said:**
> :) Was that an intentional typo?

Late evening brain-death :)

---

### Post by vlearner on 2009-08-20
omg, i could compile it but when i tried to run it, got this error msg :( :(
```

(mutter:4431): Clutter-CRITICAL **: clutter_texture_set_cogl_texture: assertion `cogl_is_texture (cogl_tex)' failed

(mutter:4431): Cogl-Common-CRITICAL **: cogl_handle_unref: assertion `handle != COGL_INVALID_HANDLE' failed

(mutter:4431): Clutter-CRITICAL **: clutter_texture_set_cogl_texture: assertion `cogl_is_texture (cogl_tex)' failed

(mutter:4431): Cogl-Common-CRITICAL **: cogl_handle_unref: assertion `handle != COGL_INVALID_HANDLE' failed

(mutter:4431): Clutter-CRITICAL **: clutter_texture_set_cogl_texture: assertion `cogl_is_texture (cogl_tex)' failed

(mutter:4431): Cogl-Common-CRITICAL **: cogl_handle_unref: assertion `handle != COGL_INVALID_HANDLE' failed
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js

(mutter:4431): Clutter-CRITICAL **: clutter_texture_set_cogl_texture: assertion `cogl_is_texture (cogl_tex)' failed

(mutter:4431): Cogl-Common-CRITICAL **: cogl_handle_unref: assertion `handle != COGL_INVALID_HANDLE' failed

(mutter:4431): Clutter-CRITICAL **: clutter_texture_set_cogl_texture: assertion `cogl_is_texture (cogl_tex)' failed

(mutter:4431): Cogl-Common-CRITICAL **: cogl_handle_unref: assertion `handle != COGL_INVALID_HANDLE' failed

(mutter:4431): Clutter-CRITICAL **: clutter_texture_set_cogl_texture: assertion `cogl_is_texture (cogl_tex)' failed

(mutter:4431): Cogl-Common-CRITICAL **: cogl_handle_unref: assertion `handle != COGL_INVALID_HANDLE' failed

(mutter:4431): Clutter-CRITICAL **: clutter_texture_set_cogl_texture: assertion `cogl_is_texture (cogl_tex)' failed

(mutter:4431): Cogl-Common-CRITICAL **: cogl_handle_unref: assertion `handle != COGL_INVALID_HANDLE' failed

(mutter:4431): Clutter-CRITICAL **: clutter_texture_set_cogl_texture: assertion `cogl_is_texture (cogl_tex)' failed

```

---

### Post by vlearner on 2009-08-20
for some reasons, I git clutter-gtk and installed it and now gnome-shell works only with Xephyr, it s somehow freaking slow tho and seems like i cannot change desktop wallpaper
----> back to Xmonad

---

### Post by jfernyhough on 2009-08-20
Wow, just got it running (had to remove xulrunner-1.9, symlink libclutter-glx-1.so.0 to -1.so and run it as gnome-shell --replace, won't work in xephyr).

This is going to be seriously immense. I love the expo/workspace switching (though I'm not fussed with the recent docs/quicklaunch bar as it is, hanging on the side of my screen).

---

### Post by Merk42 on 2009-08-21
> **jfernyhough said:**
> (though I'm not fussed with the recent docs/quicklaunch bar as it is, hanging on the side of my screen).

Thankfully you can turn it off, just click on your user switcher in the upper right.

---

### Post by x1um1n on 2009-08-23
Hi All,
I've been following Gnome-Shell since Gnome announced the plans for 3.0, I finally succumbed to temptation and installed Karmic last night.

Overall, I'm quite happy and I reckon it's going to remain my primary UI on my laptop.  There are a few niggles, mainly around customization:


[LIST]
[*]How do I remove apps from the top of the Activities pane?  I can add them easy enough with a lil drag n drop, but how do I remove the default Evo & OOo? I don't want either of them there.
[*]Also, why can't I re-order what's there by drag n drop?
[*]Does the time really have to be in 12hr format?
[*]Why does right-click do the same as left-click? If I wanted 1 mouse button, I'd be using a mac..
[/LIST]
It combines very well with Gnome-do/Docky, pity the same can't be said for Screenlets..

Is there a config tool for Shell? or even a config file?

Thanks

---

### Post by jmmL on 2009-08-23
Just had a very quick play around with gnome-shell. I liked what I saw, and I'm cautiously optimistic about where the project is heading.

Did encounter one very annoying bug though. I started gnome-shell in a gnome-terminal instance and when I tried to move the terminal around the screen from the activities view, the terminal "popped" out of gnome-shell. I didn't have the foresight to take a screenshot, but it essentially floated on top of everything contained within gnome-shell. Here's the relevant output from said terminal:```
jmmL@karmic-laptop:~$ gnome-shell --replace
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
Fatal Python error: PyEval_SaveThread: NULL tstate

(mutter:3401): Clutter-WARNING **: Actor of type ClutterClone is not in the same container of actor of type ClutterClone

(mutter:3401): Clutter-WARNING **: Actor of type ClutterClone is not in the same container of actor of type ClutterClone

(mutter:3401): Clutter-WARNING **: Actor of type ClutterClone is not in the same container of actor of type ClutterClone

(mutter:3401): Clutter-WARNING **: Actor of type ClutterClone is not in the same container of actor of type ClutterClone

(mutter:3401): Clutter-WARNING **: Actor of type BigBox is not inside a container

(mutter:3401): Clutter-WARNING **: Actor of type ClutterClone is not in the same container of actor of type ClutterClone

(mutter:3401): Clutter-WARNING **: Actor of type BigBox is not inside a container

(mutter:3401): Clutter-WARNING **: Actor of type ClutterClone is not in the same container of actor of type ClutterClone
```

Thanks to jfernyhough for the symlink tip.

---

### Post by cyberkilla on 2009-08-24
I had it working yesterday. I had the xulrunner issue too.

From what I've seen, they have the right idea. I'm not entirely bought on the sidebars, but just replacing gnome-panel gives them +500 bonus points from me. :P

It isn't really up to the reliability/usefulness of Compiz, when it comes to workspace switching, but it's well on its way.

It would be nice if they made the fonts, icons and UI elements more consistent with the GTK UI you see in the actual applications.

For instance, the behaviour of scrolling, highlighting menu items, etc.
I'm sure they already realise this though. I just enjoy stating the obvious. :P

---

### Post by portis on 2009-08-28
I always have a narrow sidebar on left.
Can someone tell me how to disable sidebar please? Thanks in advance.

---

### Post by portis on 2009-08-28
Ok, I found a key in gconf.

---

### Post by Merk42 on 2009-08-28
> **portis said:**
> Ok, I found a key in gconf.

I think you went about a more complicated way than you needed to.
Look at my post which was 4 posts before your question.

---

### Post by portis on 2009-08-28
Thanks, it works. 

> **Merk42 said:**
> I think you went about a more complicated way than you needed to.
Look at my post which was 4 posts before your question.

---

### Post by Bastanteroma on 2009-08-30
Is it possible to put breadcrumbs in the panel using the packaged Gnome Shell?

---

### Post by mahsom on 2009-08-30
Hello everyone

I resiving this error after runing ./jhbuild build -f -a -c

what is this problem !

```
checking for TEST_SHELL_RECORDER... yes
checking for MUTTER_PLUGIN... configure: error: Package requirements (gio-unix-2.0 gtk+-2.0 dbus-glib-1 mutter-plugins
                                 gjs-gi-1.0 libgnome-menu gstreamer-0.10 gstreamer-base-0.10 xfixes gconf-2.0
                                 gdk-x11-2.0 clutter-x11-1.0 clutter-glx-1.0
                                 gnome-desktop-2.0 >= 2.26 libstartup-notification-1.0
                                 gobject-introspection-1.0 >= 0.6.4) were not met:

No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MUTTER_PLUGIN_CFLAGS
and MUTTER_PLUGIN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

*** error during stage configure of gnome-shell: ########## Error running ./autogen.sh --prefix /root/gnome-shell/install --libdir '${exec_prefix}/lib'  --disable-static --disable-gtk-doc  *** [7/7]
```

I working with Ubuntu 9.04 .
Please hellp me !

---

### Post by qamelian on 2009-08-30
You don't have all the necessary dependencies installed. Install the '-dev' packages for each of the failures listed in the error.

---

### Post by taavikko on 2009-08-31
> **qamelian said:**
> You don't have all the necessary dependencies installed. Install the '-dev' packages for each of the failures listed in the error.

Wouldn't it be easier to just install gnome-shell via apt
```
sudo aptitude install gnome-shell
```

---

### Post by autocrosser on 2009-08-31
The build version is MUCH newer that what's available via APT.....I'm running into a build problem with the current stuff though.....had to do a bug report on Clutter due to a GLX error..

---

### Post by Tompalaz on 2009-08-31
the build went fine. however when I try to start gnome-shell it just breaks, nothing happens except gnome-panel disappears.

from ~/gnome-shell/source/gnome-shell/src i run ./gnome-shell --replace

I have gnome-shell installed from apt, can this cause the crash?

testing on Karmic 64bit

> tomas@MacintoshLinux:~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
tomas@MacintoshLinux:~/gnome-shell/source/gnome-s

---

### Post by go7Ul1ai on 2009-08-31
Okay, so I installed the Gnome-Shell packages using Synaptic on Karmic, nothing has changed. I try using sudo gnome-shell or gnome-shell through the terminal to no avail. I try using alt+f2 but strangely no run type command pops up when I press that keyboard combination :S I've even tried running it using the command the GNOME website has provided.

Any advice?

Lee

---

### Post by qamelian on 2009-08-31
The build from source I did yesterday seems to have some problems, although the build went from start to finish with no apparent errors. I have had both the build from the repos and my own build installed side by side since the repo version was released without any apparent conflict, so I doubt that is the problem. I haven't had time to poke around and try to troubleshoot the build from source, but I think I'll wait a day or two and do a fresh build to see what happens. This isn't the first time I've seen breakage in builds of gnome-shell, but it usually only lasts a day or two before a fresh build gets it working again.

---

### Post by autocrosser on 2009-08-31
Yes--I've been building it for about 6 months now & have had 3 "major" non-builds--talking to the guys about why it broke on my system--Dan is looking at the config log & I'm waiting to hear from Owen.

---

### Post by qamelian on 2009-08-31
> **autocrosser said:**
> Yes--I've been building it for about 6 months now & have had 3 "major" non-builds--talking to the guys about why it broke on my system--Dan is looking at the config log & I'm waiting to hear from Owen.
This is half the fun, I guess.:lolflag:

I can't wait to see the final product. Except for a few minor quibbles, I'm really enjoying using Gnome Shell.

---

### Post by Schendje on 2009-08-31
> **qamelian said:**
> 
I can't wait to see the final product. Except for a few minor quibbles, I'm really enjoying using Gnome Shell.
Me too! I'm not an expert by any means, but I installed it a few hours ago and I think it's great.

Looking forward to GNOME 3.:)

---

### Post by Regenweald on 2009-08-31
I have seen a turnaround in the responses to the shell at least in the forums, whatever the developers are doing, they must be doing it right ;) I'll build it again soon...

---

### Post by TrueTom on 2009-08-31
> **Regenweald said:**
> I have seen a turnaround in the responses to the shell at least in the forums, whatever the developers are doing, they must be doing it right ;) I'll build it again soon...

Just because five people like it doesn't mean it's good. I can find you five people who believe playing Russian Roulette is a fun and worthwhile past time activity. I for one still believe it's complete crap but don't see the point in mentioning it every second since it won't change a thing.

---

### Post by qamelian on 2009-08-31
> **TrueTom said:**
> Just because five people like it doesn't mean it's good. I can find you five people who believe playing Russian Roulette is a fun and worthwhile past time activity. I for one still believe it's complete crap but don't see the point in mentioning it every second since it won't change a thing.
You're entitled to your opinion. I like Gnome Shell for a number of reasons. It performs better for me than the existing Gnome environment. I find it more friendly for me from a usability standpoint. I like the new workspace approach. I don't like the almost complete lack of configuration options, but I expect them to appear as the shell matures. This is the first time I have genuinely enjoyed using Gnome since before the switch from Gnome 1.4 to Gnome 2. When that switch took place, I considered Gnome 2 to be crap compared to 1.4. I still prefer 1.4 to Gnome 2, in fact! To each his own. :)

---

### Post by Regenweald on 2009-08-31
> **TrueTom said:**
> Just because five people like it doesn't mean it's good. I can find you five people who believe playing Russian Roulette is a fun and worthwhile past time activity. I for one still believe it's complete crap but don't see the point in mentioning it every second since it won't change a thing.

I missed the beginning of our argument so you'll have to refresh my memory.
At the beginning of testing basically all the feedback was negative, it seems that the devs have been listening to some of the feedback and now we have persons complimenting it and using it fulltime. As i said, i have seen a turnaround in the response in the forums.

---

### Post by Schendje on 2009-08-31
> **qamelian said:**
> I don't like the almost complete lack of configuration options, but I expect them to appear as the shell matures. 
Yeah, I was searching for the configuration options, but then I realized there weren't any. :D

I'm sure they're on their way though.

---

### Post by qamelian on 2009-08-31
> **Schendje said:**
> Yeah, I was searching for the configuration options, but then I realized there weren't any. :D

I'm sure they're on their way though.
I might be off base, but it seems to me they would want to get everything working at least approximately the way they planned before turning us loose with hammers to break it! :)

---

### Post by Fnyx on 2009-08-31
> **autocrosser said:**
> The build version is MUCH newer that what's available via APT.....I'm running into a build problem with the current stuff though.....had to do a bug report on Clutter due to a GLX error..
Had the same thing (Jaunty though) and I'm guessing you too have nvidia drivers version 190.25 which seems to be bugged. Downgrade to 190.18 or older and it should be fine (some changing in the linking of libGL.so* might work aswell but I haven't tried).

---

### Post by qamelian on 2009-08-31
> **Fnyx said:**
> Had the same thing (Jaunty though) and I'm guessing you too have nvidia drivers version 190.25 which seems to be bugged. Downgrade to 190.18 or older and it should be fine (some changing in the linking of libGL.so* might work aswell but I haven't tried).
I don't think that is necessarily the problem. I'm having the same issue with the open source Radeon drivers on my laptop.

---

### Post by Fnyx on 2009-08-31
> **qamelian said:**
> I don't think that is necessarily the problem. I'm having the same issue with the open source Radeon drivers on my laptop.

The exact error was:
```
checking for glXCreateContext in -lGL... no
configure: error: Required GLX library not found

```
If you have that and Radeon I guess it might be a bug in the shell afterall :-)

---

### Post by psyke83 on 2009-08-31
> **Fnyx said:**
> The exact error was:
```
checking for glXCreateContext in -lGL... no
configure: error: Required GLX library not found

```
If you have that and Radeon I guess it might be a bug in the shell afterall :-)

That only means that you don't have the development files installed (probably libgl-dev).

---

### Post by gnomeuser on 2009-08-31
it's is better than before however my whole problem with this is still the fundamental design, to believe that generic workspaces of all things is the one thing we need to spend a load of time fixing is simply not making sense to me. It's a solution looking for a problem.

Regardless it is still dead slow in all aspects, painfully so in many cases. I don't want to sit and wait for something to happen if I click the activities context. The trade off here should be that the added complexity and additional click be offset by the speed and convenience in design of this new solution.

There are bugs, but I will forgive that. 

I am utterly unconvinced this is the right direction for the GNOME desktop, building everything in javascript of all thing e.g. makes no sense to me. Putting out something this sluggish doesn't either, the design makes no sense.. really the whole thing just makes me wonder.

---

### Post by qamelian on 2009-08-31
> **gnomeuser said:**
> it's is better than before however my whole problem with this is still the fundamental design, to believe that generic workspaces of all things is the one thing we need to spend a load of time fixing is simply not making sense to me. It's a solution looking for a problem.
We'll need to agree to disagree. I love the way they are handling workspaces myself. I can't really say why, but it just feels comfortable to me.

> Regardless it is still dead slow in all aspects, painfully so in many cases. I don't want to sit and wait for something to happen if I click the activities context. The trade off here should be that the added complexity and additional click be offset by the speed and convenience in design of this new solution.
I don't see this on my gear. On my laptop, it feels noticeably faster than the gnome desktop that shipped with any of the last three Ubuntu releases. I find it very responsive and smooth.

 > I am utterly unconvinced this is the right direction for the GNOME desktop, building everything in javascript of all thing e.g. makes no sense to me. Putting out something this sluggish doesn't either, the design makes no sense.. really the whole thing just makes me wonder.
Maybe you're right and it is the wrong direction, but it sure feels right to me. I'm genuinely liking the Gnome desktop for the first time since Gnome 1.4. And as I said above, I don't see the sluggishness you describe. It's quite perky running on my Compaq Presario R3000T.

---

### Post by autocrosser on 2009-08-31
> **psyke83 said:**
> That only means that you don't have the development files installed (probably libgl-dev).

The bummer is that I have all the -dev files installed & ran into this problem--as I said Dan & Owen are looking into it--I just responded back to Dan with more info a few minutes ago...

Here is the bug report if anyone can add info to it: [http://bugzilla.gnome.org/show_bug.cgi?id=593603](http://bugzilla.gnome.org/show_bug.cgi?id=593603)

---

### Post by Yes_It's_Me on 2009-08-31
> **gnomeuser said:**
> I am utterly unconvinced this is the right direction for the GNOME desktop, building everything in javascript of all thing e.g. makes no sense to me. Putting out something this sluggish doesn't either, the design makes no sense.. really the whole thing just makes me wonder.

I agree, it's the worst possible language to base everything off.

It's like Linus waking up tomorrow and going "I want to rewrite the kernel in python!"

---

### Post by frustphil on 2009-09-01
> **qamelian said:**
> 
i don't see this on my gear. On my laptop, it feels noticeably faster than the gnome desktop that shipped with any of the last three ubuntu releases. I find it very responsive and smooth.
+1

---

### Post by frustphil on 2009-09-01
> **Yes_It's_Me said:**
> I agree, it's the worst possible language to base everything off.

It's like Linus waking up tomorrow and going "I want to rewrite the kernel in python!"

JavaScript = Easy = Widely used = More developers.

---

### Post by TrueTom on 2009-09-01
> **frustphil said:**
> JavaScript = Easy = Widely used = More developers.

You don't want the kind of developers who use JavaScript working on an OS.

---

### Post by Fnyx on 2009-09-01
> **autocrosser said:**
> The bummer is that I have all the -dev files installed & ran into this problem--as I said Dan & Owen are looking into it--I just responded back to Dan with more info a few minutes ago...

Here is the bug report if anyone can add info to it: [http://bugzilla.gnome.org/show_bug.cgi?id=593603](http://bugzilla.gnome.org/show_bug.cgi?id=593603)

Found something related on the nVidia forum:
[http://www.nvnews.net/vbulletin/showthread.php?t=138016]("http://www.nvnews.net/vbulletin/showthread.php?t=138016")

---

### Post by Reiger on 2009-09-01
> **frustphil said:**
> JavaScript = Easy = Widely used = More developers.
== Ignorant & Unfair.

It is Ignorant because:

JavaScript != Easy != Widely Used != More developers. Actually.

JavaScript, or should we say ECMAScript, in the browser is purposefully made easy by browser developers, but that is no merit of the language itself. (Although it can be argued JavaScript/ECMAScript brings a lot to the table when it comes to inherent expressiveness that many other languages lack: courtesy of the prototype object/concept & closures.) I would actually argue that a language like Python is a lot easier than JavaScript but also much more limited. (Prototype magic is awesome, and by awesome I mean totally sweet.) In any case we are outside the browser, so the language is for the most part as easy as the bindings to other API's which is also not really telling anything about how easy the language actually is.... 

Widely used? On the Internet perhaps, but bear in mind that we are talking about something quite different here. JavaScript on the desktop is not a new phenomenon per se: there have been bidings/engines for JavaScript apps on a desktop and Microsoft Windows has had support for (and probably existing apps written in) JScript/ActionScript on the desktop for years. Even so the number of JavaScript/ECMAScript apps for a desktop isn't exactly huge compared to the number of desktop apps (in general), and this is further underlined by the fact that the GnomeShell is a new (kind of) project building on top of a new (kind of) stack. So the question really is: is JavaScript used widely enough there exists prior art & expertise on this (new) kind of thing?

The argument is unfair because it implicitly "accuses" the GnomeShell people of going with a language that is "easy" to "gain more developers", rather than one that is technically superior for the job. Also it calls, implicitly, the into question the competence of individual developers because we (whomever reading your statement, I mean) are made to believe that had the GnomeShell project chosen a "less easy" language there would be "less developers" because of that.

Personally I also doubt that the GnomeShell team saw a very large increase in the number of team members because of whatever the language they use: simply because that is not really how projects work. Not everyone can join up any project: you are asked for some credentials/work-to-show first.

---

### Post by Joe_Bishop on 2009-09-01
> **frustphil said:**
> +1
You are uniq. Which video card do you use? My expirience on nVidia ones (8800gtx, 8800gts 512, 8600gt) is horrible, gtkperf slow down in about 5(!) times with gnome-shell in the comparison to both metacity and compiz.

---

### Post by Joe_Bishop on 2009-09-01
> **Reiger said:**
> == Ignorant & Unfair.

It is Ignorant because:

JavaScript != Easy != Widely Used != More developers. Actually.

JavaScript, or should we say ECMAScript, in the browser is purposefully made easy by browser developers, but that is no merit of the language itself. (Although it can be argued JavaScript/ECMAScript brings a lot to the table when it comes to inherent expressiveness that many other languages lack: courtesy of the prototype object/concept & closures.) I would actually argue that a language like Python is a lot easier than JavaScript but also much more limited. (Prototype magic is awesome, and by awesome I mean totally sweet.) In any case we are outside the browser, so the language is for the most part as easy as the bindings to other API's which is also not really telling anything about how easy the language actually is.... 

Widely used? On the Internet perhaps, but bear in mind that we are talking about something quite different here. JavaScript on the desktop is not a new phenomenon per se: there have been bidings/engines for JavaScript apps on a desktop and Microsoft Windows has had support for (and probably existing apps written in) JScript/ActionScript on the desktop for years. Even so the number of JavaScript/ECMAScript apps for a desktop isn't exactly huge compared to the number of desktop apps (in general), and this is further underlined by the fact that the GnomeShell is a new (kind of) project building on top of a new (kind of) stack. So the question really is: is JavaScript used widely enough there exists prior art & expertise on this (new) kind of thing?

The argument is unfair because it implicitly "accuses" the GnomeShell people of going with a language that is "easy" to "gain more developers", rather than one that is technically superior for the job. Also it calls, implicitly, the into question the competence of individual developers because we (whomever reading your statement, I mean) are made to believe that had the GnomeShell project chosen a "less easy" language there would be "less developers" because of that.

Personally I also doubt that the GnomeShell team saw a very large increase in the number of team members because of whatever the language they use: simply because that is not really how projects work. Not everyone can join up any project: you are asked for some credentials/work-to-show first.

I'm not fully agree with you, but subscribe to your opinion in most of you've told. Language is not a universal panacea, especially when they are about equal in expressiveness, such as Python, C#, JavaScript, etc. In this case libraries make all the sence, but javascript sucks here. Another weakness of gnome-shell is they are using mozilla jit infrastructure, which only works well on 32bit platforms, not 64 - so, it's horribly slow now on 64bit machines, taking ages even for opening application submenu.

---

### Post by frustphil on 2009-09-01
> **Reiger said:**
> == Ignorant & Unfair.

It is Ignorant because:

JavaScript != Easy != Widely Used != More developers. Actually.

JavaScript, or should we say ECMAScript, in the browser is purposefully made easy by browser developers, but that is no merit of the language itself. (Although it can be argued JavaScript/ECMAScript brings a lot to the table when it comes to inherent expressiveness that many other languages lack: courtesy of the prototype object/concept & closures.) I would actually argue that a language like Python is a lot easier than JavaScript but also much more limited. (Prototype magic is awesome, and by awesome I mean totally sweet.) In any case we are outside the browser, so the language is for the most part as easy as the bindings to other API's which is also not really telling anything about how easy the language actually is.... 

Widely used? On the Internet perhaps, but bear in mind that we are talking about something quite different here. JavaScript on the desktop is not a new phenomenon per se: there have been bidings/engines for JavaScript apps on a desktop and Microsoft Windows has had support for (and probably existing apps written in) JScript/ActionScript on the desktop for years. Even so the number of JavaScript/ECMAScript apps for a desktop isn't exactly huge compared to the number of desktop apps (in general), and this is further underlined by the fact that the GnomeShell is a new (kind of) project building on top of a new (kind of) stack. So the question really is: is JavaScript used widely enough there exists prior art & expertise on this (new) kind of thing?

The argument is unfair because it implicitly "accuses" the GnomeShell people of going with a language that is "easy" to "gain more developers", rather than one that is technically superior for the job. Also it calls, implicitly, the into question the competence of individual developers because we (whomever reading your statement, I mean) are made to believe that had the GnomeShell project chosen a "less easy" language there would be "less developers" because of that.

Personally I also doubt that the GnomeShell team saw a very large increase in the number of team members because of whatever the language they use: simply because that is not really how projects work. Not everyone can join up any project: you are asked for some credentials/work-to-show first.

Oops that was too long for me to bother reading. Anyway my statement was based on the many articles I read about GNOME Shell from the time it was announced to replace gnome. I don't know how they stated it exactly but what I understood was they chose JavaScript to attract more developers. 

Or maybe I was reading too much :guitar:

---

### Post by frustphil on 2009-09-01
> **Joe_Bishop said:**
> You are uniq. Which video card do you use? My expirience on nVidia ones (8800gtx, 8800gts 512, 8600gt) is horrible, gtkperf slow down in about 5(!) times with gnome-shell in the comparison to both metacity and compiz.

Intel 82945G/GZ

---

### Post by Joe_Bishop on 2009-09-01
> **frustphil said:**
> Oops that was too long for me to bother reading. Anyway my statement was based on the many articles I read about GNOME Shell from the time it was announced to replace gnome. I don't know how they stated it exactly but what I understood was they chose JavaScript to attract more developers. 

Or maybe I was reading too much :guitar:
How web development expirience with javascript can help in gnome-shell development? It's very specific thing to code for web browsers, I don't think it can help with gnome-shell much. I also think Python is better known among linux users, most of javascript coders are using windows.

---

### Post by coolen on 2009-09-01
Yeah, I'm not quite sold on the whole "more developers" thing.

Sure, a lot of people know JS. Those people, very likely, have little interest in developing applications, particularly for Gnome.

If you're motivated and talented enough to make a serious contribution, you won't have too much trouble learning to use one of the other supported languages.

You know what other language a lot of people know? C. If that many C developers, developers who do have an interest in writing good code for applications, aren't interested in writing them for Gnome, why do you imagine that a lot fewer people who know a language that's thus far been largely confined to the web will come flocking over with new, shiny toys?

---

### Post by qamelian on 2009-09-01
> **Joe_Bishop said:**
> You are uniq. Which video card do you use? My expirience on nVidia ones (8800gtx, 8800gts 512, 8600gt) is horrible, gtkperf slow down in about 5(!) times with gnome-shell in the comparison to both metacity and compiz.
I'm using it on two different machines at home. One is an older Compaq Presario R3000T, with an ATI Mobility Radeon 9000 IGP. Gnome-shell absolutely flies on it compared to the nautilus-managed desktop in Gnome 2.26 in Jaunty or 2.27.Xvin Karmic. The second system is an Acer desktop with an  ATI Radeon 2450HD card. Again, gnome-shell flies. The laptop is running the open-source radeon drivers on Karmic right now, while the desktop is running proprietary drivers on Jaunty.

---

### Post by Merk42 on 2009-09-01
> **qamelian said:**
> [QUOTE=gnomeuser;7877432]it's is better than before however my whole problem with this is still the fundamental design, to believe that generic workspaces of all things is the one thing we need to spend a load of time fixing is simply not making sense to me. It's a solution looking for a problem.
We'll need to agree to disagree. I love the way they are handling workspaces myself. I can't really say why, but it just feels comfortable to me.
[/QUOTE]
I don't want to speak for gnomeuser, but my take is that while the treatment of workspaces isn't necessarily bad, it seems like they focused on just that and every other aspect of the UI was an afterthough.

Have the new builds yet implemented a way I can see running applications at a glance(ie no interaction needed), or switch between them without Alt-Tab?

---

### Post by Joe_Bishop on 2009-09-01
> **qamelian said:**
> I'm using it on two different machines at home. One is an older Compaq Presario R3000T, with an ATI Mobility Radeon 9000 IGP. Gnome-shell absolutely flies on it compared to the nautilus-managed desktop in Gnome 2.26 in Jaunty or 2.27.Xvin Karmic. The second system is an Acer desktop with an  ATI Radeon 2450HD card. Again, gnome-shell flies. The laptop is running the open-source radeon drivers on Karmic right now, while the desktop is running proprietary drivers on Jaunty.
Now try to bench in gtkperf with metacity/compiz/gnome-shell.

---

### Post by simius on 2009-09-01
There’s not really a point in arguing over this, but personally the use of JavaScript helped me get started developing patches for gnome-shell. Being able to change a script file and running alt-f2 ‘replace’ to see the results makes it very easy to learn how it works. (Another big factor was the small size of the project 10 months ago.)

The new shell is probably even less focused on using multiple workspaces than GNOME 2. The feature is more or less hidden, initially only displaying a (+) button in a corner of the screen, while GNOME 2 creates two or four workspaces by default and shows a confusing switcher in the panel. The shell and its Activities overview really shine when you use only one workspace.

Of course the new UI hasn't proven itself better than gnome-panel + metacity yet. Chances are that distributors will continue to provide the well-known and tested GNOME 2 UI for years or develop something entirely different (a new Moonlight-based panel?).

Another good thing of the gnome-shell infrastructure and a lot of work behind it (on the Mutter window manager, GObject introspection and JavaScript bindings) is that new interface ideas can be much more easily experimented with. Even if the current design doesn't work out well in practice, new prototypes can be written and distributed quickly.

---

### Post by qamelian on 2009-09-01
> **Joe_Bishop said:**
> Now try to bench in gtkperf with metacity/compiz/gnome-shell.
I don't need to. Moving a window in Gnome 2.26 is jerky with visible tearing. In Gnome-shell, move is smooth with no tearing. In Gnome 2.26, minimizing or maximizing a window results in a slight delay before anything happens. In Gnome-shell, no delay. Performance in Gnome 2.26 gets noticably worse when I activate the Metacity compositing manager. 

I don't care about benchmarks. I care about real-world performance and experience. On my hardware, Gnome-shell is much more pleasant to use that the standard Gnome desktop. That's really all there is to it.

---

### Post by pulpo69 on 2009-09-01
why gnomeshell don't work here (karmic 64 bit, amd phenom)?

---

### Post by qamelian on 2009-09-01
> **Merk42 said:**
>  Have the new builds yet implemented a way I can see running applications at a glance(ie no interaction needed), or switch between them without Alt-Tab?
Not yet, unfortunately. Currently, it seems to require moving the mouse pointer to the upper-left corner, which gives you essentially the same view as clicking on the Activities menu.

---

### Post by qamelian on 2009-09-01
> **autocrosser said:**
> The bummer is that I have all the -dev files installed & ran into this problem--as I said Dan & Owen are looking into it--I just responded back to Dan with more info a few minutes ago...

Here is the bug report if anyone can add info to it: [http://bugzilla.gnome.org/show_bug.cgi?id=593603](http://bugzilla.gnome.org/show_bug.cgi?id=593603)
Looks like the problem is resolved, whatever it was. It builds just fine now.

---

### Post by go7Ul1ai on 2009-09-01
Okay, so I installed the Gnome-Shell packages using Synaptic on Karmic, nothing has changed. I try using sudo gnome-shell or gnome-shell through the terminal to no avail. I try using alt+f2 but strangely no run type command pops up when I press that keyboard combination :S I've even tried running it using the command the GNOME website has provided.

Any advice?

Lee

---

### Post by taavikko on 2009-09-01
> **lee.jarratt said:**
> Okay, so I installed the Gnome-Shell packages using Synaptic on Karmic, nothing has changed. I try using sudo gnome-shell or gnome-shell through the terminal to no avail. I try using alt+f2 but strangely no run type command pops up when I press that keyboard combination :S I've even tried running it using the command the GNOME website has provided.

Any advice?

Lee

Have none for gnome-shell, except, don't try to run it with sudo
Also, test with new user if the gnome-shell works.

For the launcher, if using custom or solid color for gnome-panel background, switch it off.

---

### Post by Merk42 on 2009-09-01
> **qamelian said:**
> Not yet, unfortunately. Currently, it seems to require moving the mouse pointer to the upper-left corner, which gives you essentially the same view as clicking on the Activities menu.

I HOPE that officially changes. I hear about breadcrumbs, which only half solves it, but is good.

How about any way of accessing/emptying trash? Is that possible?

---

### Post by Darkshade on 2009-09-02
> **lee.jarratt said:**
> Okay, so I installed the Gnome-Shell packages using Synaptic on Karmic, nothing has changed. I try using sudo gnome-shell or gnome-shell through the terminal to no avail. I try using alt+f2 but strangely no run type command pops up when I press that keyboard combination :S I've even tried running it using the command the GNOME website has provided.

Any advice?

Lee

The gnome-shell package didn't work for me at all on both my PC and laptop.
Try following the instructions here to build it yourself - [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

---

### Post by qamelian on 2009-09-02
> **Merk42 said:**
> I HOPE that officially changes. I hear about breadcrumbs, which only half solves it, but is good.

How about any way of accessing/emptying trash? Is that possible?
I still don't see any easy way of doing that either. It's not an issue for me, as when I delete something I just want it gone and by-pass the trash anyway, but I no it will be a big issue for many users whose habits differ from mine.

---

### Post by Merk42 on 2009-09-02
> **qamelian said:**
> I still don't see any easy way of doing that either. It's not an issue for me, as when I delete something I just want it gone and by-pass the trash anyway, but I no it will be a big issue for many users whose habits differ from mine.

And it's those two things (the other being the aforementioned open application view/switcher) that make me feel GNOME 3 was: "Hey let's completely focus on multiple desktops with an overlay and not even think about anything else until its coded"

---

### Post by gnomeuser on 2009-09-02
> **pulpo69 said:**
> why gnomeshell don't work here (karmic 64 bit, amd phenom)?

What is the specific error?

---

### Post by qamelian on 2009-09-02
> **Merk42 said:**
> And it's those two things (the other being the aforementioned open application view/switcher) that make me feel GNOME 3 was: "Hey let's completely focus on multiple desktops with an overlay and not even think about anything else until its coded"
I can appreciate that. Neither one of those items impacts my current work habits, but I can certainly see why other users would be concerned. Since my work habits tend to evolve over time, I'd like to see them dealt with as well, in case they become an issue to me! :)

---

### Post by Mr. Picklesworth on 2009-09-02
As a GNOME Shell fan, let me say that I would love to see this (maybe the whole GNOME 3 thing) postponed for at least one more release. It may be "finished" by 2.30, but by the time the dust settles there won't be any time for other applications to make use of it.

---

### Post by Merk42 on 2009-09-02
> **Mr. Picklesworth said:**
> As a GNOME Shell fan, let me say that I would love to see this (maybe the whole GNOME 3 thing) postponed for at least one more release. It may be "finished" by 2.30, but by the time the dust settles there won't be any time for other applications to make use of it.

Well shouldn't the programmers of said apps be following GNOME Shell now and updating?
Some third party applications already take advantage of Windows 7's new features before it went RTM.

That aside, I feel GNOME 3 is going to be like KDE 4 (and I guess a lesser extent Mac OS X).  Where the first good release will be the .1 release.

---

### Post by qamelian on 2009-09-02
> **Merk42 said:**
>  That aside, I feel GNOME 3 is going to be like KDE 4 (and I guess a lesser extent Mac OS X).  Where the first good release will be the .1 release.
You're probably right, but then again, I remember the transition from Gnome 1.4 to Gnome 2 being a bit unpleasant too, at least for me. I think it's just a normal part of any major change to an environment like Gnome, KDE, etc. At least with Linux, if a major upgrade of a DE breaks your experrience badly, you have the option of shifting to another DE until the glitches are ironed out...or permanently if you desire. Not every OS is flexible enough to offer such freedom.

---

### Post by ttoms on 2009-09-03
I appear to have just 'lost' gnome-shell. Installed it from the ubuntu repositories a while ago. Able to run it with "gnome-shell --replace" until updates today. Strange.

Still it was (as expected) pretty buggy, and took some getting used to. I was just getting to like it though!

---

### Post by seeker5528 on 2009-09-03
> **Mr. Picklesworth said:**
> As a GNOME Shell fan, let me say that I would love to see this (maybe the whole GNOME 3 thing) postponed for at least one more release. It may be "finished" by 2.30, but by the time the dust settles there won't be any time for other applications to make use of it.

Don't know how the developers of the Gnome Shell see the situation but to my way of thinking.....

For every rule there are exceptions, but as a general rule of thumb, it should not be up to the application developers to have to take advantage of Gnome Shell, to the extent possible it should be up to the Gnome Shell developers to make the Gnome Shell experience advantageous for the running of *all* the users applications.

For example if the default when you click on an application launcher for an application that is already open is to switch you to that application and something has to be done to specify there should be an option to open the application again instead of switching to the running instance of the application. That sounds like something that should be set in a .desktop file so it can be set by the distribution vendors or the end users independently of whether the application developers choose to support the option or not.

Later, Seeker

---

### Post by cdEWoozy on 2009-09-04
> **seeker5528 said:**
> For example if the default when you click on an application launcher for an application that is already open is to switch you to that application and something has to be done to specify there should be an option to open the application again instead of switching to the running instance of the application. That sounds like something that should be set in a .desktop file so it can be set by the distribution vendors or the end users independently of whether the application developers choose to support the option or not.

I think that is already planned. Somewhere in the comments of [this article](http://cgwalters.livejournal.com/25818.html) cgwalters states that middle-clicking on the application icon should open a new window or an entirely new instance of the application (depending on what the application supports).

Left-clicking however should always either take you to the open window or start the application, if it is not yet running. Being able to specify in the .desktop-file that the default action for a left-click is to open another instance (or window) should be a no-go, as it would introduce inconsistency (sometimes left-clicking opens the active window, sometimes it starts another window/instance). I'm not sure if that is what you meant.

---

### Post by Starks on 2009-09-04
There's no way in hell Gnome 3 will be ready for Liger, if it is, it'll just barely make the cutoff and be crap.

---

### Post by coolen on 2009-09-04
It probably won't show up until the Manic Mongoose, possibly ever the Nefarious Newt.

---

### Post by Kazade on 2009-09-04
OK, so I just tried Gnome-shell for the first time in a few months. Generally I like the idea, it makes working with multiple desktops really nice, I've got questions though (dunno if any of you can answer them):

1. Will the top panel be configurable at all? I have dual monitors and the clocks falls right bang in the middle, which is really annoying.
2. Will the colour scheme be configurable? I don't mind the dark top bar, but I'm finding the overlay view difficult to see (too dark).
3. Will gnome-shell work with Compiz?
4. Gnome-shell doesn't seem to pay attention to font settings (font is too large compared to everything else), is this something that will change?

Basically, my view is, if they make it slightly configurable (not madly configurable, just theme, fonts, applet positions) then I like, if not, then come Gnome 3 I'll be jumping ship to KDE most likely.

---

### Post by simius on 2009-09-04
> **Kazade said:**
> 1. Will the top panel be configurable at all? I have dual monitors and the clocks falls right bang in the middle, which is really annoying.
2. Will the colour scheme be configurable? I don't mind the dark top bar, but I'm finding the overlay view difficult to see (too dark).
3. Will gnome-shell work with Compiz?
4. Gnome-shell doesn't seem to pay attention to font settings (font is too large compared to everything else), is this something that will change?
1. Probably not, but the the plan is to display the top panel only on the main monitor. Which one that is, should probably be configurable.
2. I don't think it will be configurable, though a GTK+ theme color could be picked to replace the blue on selections. If you can describe your problems using the overview with the current black background, please file a bug.
3. No, GNOME Shell is a window manager itself (based on Mutter, based on Metacity). Compiz is another one, so they are mutually exclusive.

---

### Post by autocrosser on 2009-09-04
I am "fairly" sure that people will find many ways to hack/change/mod it as soon as the code stabilizes--it is mostly java after all......So I am hopeful that no matter what is released--we can mod it to something we like...

---

### Post by Mr. Picklesworth on 2009-09-04
> **autocrosser said:**
> I am "fairly" sure that people will find many ways to hack/change/mod it as soon as the code stabilizes--it is mostly java after all......So I am hopeful that no matter what is released--we can mod it to something we like...

Java*script*. Big difference. And yes, one of the reasons for using Javascript (or any scripting language) here is that it is really extensible :)
Details forthcoming.

About applets: you can consider them dead in their current form, but I wouldn't be surprised to see applications drawing directly to the panel at some point. (And maybe some helper functions to that end). The problem with today's applets is easily explained by some examples:

 * I want a handy timer! So, instead of launching an application, I right click on the panel, head to Add Applet, add the Timer applet and then set it. When it is finished, I must remove the timer applet because my panel really doesn't have the space for it. These examples are *frequent*.
 * It shouldn't be possible to lose pieces of UI such as the system tray and menu. Right now, it is, because the panels are somewhat feeble, the applets can be deleted or moved to weird places.
 * When everyone has a different shell, solid documentation is a mammoth task for everyone, including the end user.

---

### Post by Copernicus1234 on 2009-09-04
> **Mr. Picklesworth said:**
> Java*script*; big difference. And yes, one of the reasons for using Javascript (or any scripting language) here is that it is really extensible :)
Details forthcoming.

I recently started using Javascript for "serious" work and its actually pretty powerful. It has a complicated syntax to get used to when doing inheritance, but it becomes second nature after a while.

Thank god for Firebug though. I cant imagine doing javascript without it. Nothing ive tried is as good, including Eclipse JS plugins etc.

---

### Post by Kazade on 2009-09-04
> **Mr. Picklesworth said:**
> 
About applets: you can consider them dead in their current form, but I wouldn't be surprised to see applications drawing directly to the panel at some point. (And maybe some helper functions to that end). 

I had this idea earlier about this, what if there was some kind of spinning wheel in the bottom right hand corner of the desktop that you could drag applications that support a particular "applet-style" API to. You could then spin the wheel to spin through the docked applications you have open, and you could make some of them on load on start, but the default is to disappear when the session ends. I think that would be kinda cool :)

---

### Post by britjm on 2009-09-15
Ah. G-S looks and feels great... until I decide to watch a video. Then it drops a large majority of the frames. I wonder what the solution is to the issue, aside from not using G-S.

---

### Post by Eestlane on 2009-09-15
Gnome Shell seems to be like an anticipated feature. There are some minor annoyances in the current one though, can't see the administration menu and... well it's raw. But I like it!

EDIT: Oh, nice. Administration is in top right username->System preferences

---

### Post by Joe_Bishop on 2009-09-16
> **Copernicus1234 said:**
> I recently started using Javascript for "serious" work and its actually pretty powerful. It has a complicated syntax to get used to when doing inheritance, but it becomes second nature after a while.

Thank god for Firebug though. I cant imagine doing javascript without it. Nothing ive tried is as good, including Eclipse JS plugins etc.
firebug won't any help you when coding for gnome-shell ;)

---

### Post by simius on 2009-09-16
> **Joe_Bishop said:**
> firebug won't any help you when coding for gnome-shell ;)
But since a few weeks there is [Looking Glass]("http://live.gnome.org/GnomeShell/LookingGlass"). It doesn't have all features from Firebug, but makes it easy to experiment with the JS code.

---

### Post by Joe_Bishop on 2009-09-22
Many languages has similar tools. JavaScript itself is knows as bad language, because of the lack of libraries.

---

### Post by [h2o] on 2009-09-22
> **Joe_Bishop said:**
> Many languages has similar tools. JavaScript itself is knows as bad language, because of the lack of libraries.
Which is where [http://live.gnome.org/GObjectIntrospection](http://live.gnome.org/GObjectIntrospection) comes handy.

Javascript is known as a bad language since it is mostly used only inside web browsers and their implementations are kind of sucky at times.
Sure, JS is not my favourite language to use, but compared to a lot of other languages it is really nice and I think it will fit well as the application language of Gnome Shell.

---

### Post by TrueTom on 2009-09-22
While JavaScript isn't a bad language there are better alternatives like Lua which is twice as fast and therefore more battery friendly (which is probably no concern for the developers since GNOME 3 won't run on a lot of netbooks anyway).

---

### Post by gnomeuser on 2009-09-22
> **TrueTom said:**
> While JavaScript isn't a bad language there are better alternatives like Lua which is twice as fast and therefore more battery friendly (which is probably no concern for the developers since GNOME 3 won't run on a lot of netbooks anyway).

And yet the primary developers are Red Hat people, who has been banging on about good power management for years and made it a focus for their RHEL6 release.

Regardless I simply loath the choice of Javascript. It's a language without a standard people actually follow which means we are bound to our compiler in much the same way as a guy with cement shoes is, with much the same result. It's notoriously insecure and under performant, it encourages more of the internets shittasticly bad coders to invade the desktop (and this is actually seen as a good thing by the gs developers). Now I am not in fact against encouraging more developers to join Linux or even inexperienced developers but for the love of the flying spaghetti monster give them some tools that help them code properly, safely and with performance. Additionally you should provide them with choice, no language fits all but the underlying technology should allow for this to not be a problem.

I would much rather have seen Mono and Moonlight tapped for the next generation desktop, it has excellent development tools and environments. There are good examples to pick from. It allows for all the swanky bling we might desire and it still performs very acceptably. It allows for choice for the developer and it lets us upgrade one runtime that benefits the performance of everyones code. It is managed, sexy and comes with a lot of help. It is perfect for job.

Nothing good can come of this, nothing at all.

---

### Post by Merk42 on 2009-09-22
> **gnomeuser said:**
> Nothing good can come of this, nothing at all.

Sure there can be good....



A lot more development/users of KDE....

---

### Post by [h2o] on 2009-09-22
> **TrueTom said:**
> While JavaScript isn't a bad language there are better alternatives like Lua which is twice as fast and therefore more battery friendly (which is probably no concern for the developers since GNOME 3 won't run on a lot of netbooks anyway).
I fail to see how a language can be faster. Implementations can be faster or slower than others sure, but the language itself? As for JavaScript, there are obviously huge performance differences between the engines shipped with our browsers.

As for standards... is that a problem? I thought that the javascripting was for apps within the shell ("plugins" of some kind) and parts of the shell itself, and not for regular desktop applications. Then what is the problem? If I write a plugin for application A then it will most certainly not work with application B even if both are implemented in language X and has the same purpose.

---

### Post by GeneralZod on 2009-09-22
> **Merk42 said:**
> 
A lot more development/users of KDE....

The preferred scripting language for Plasmoids is (or rather, will be) [drumroll] - Javascript! Of course, others are allowed, but this will be the one that people are encouraged to use.

---

### Post by TrueTom on 2009-09-22
> **'[h2o] said:**
> I fail to see how a language can be faster.

Unfortunately this true. For example: statically typed languages are usually faster than dynamically typed ones. JIT compilation can help but it is always an uphill battle.

---

### Post by Regenweald on 2009-09-22
Now that Gnome 2.28 is basically out the door, have all efforts already shifted to 3.0 ? The shell seems remarkably usable currently, Six months now looks like good time.

---

### Post by [h2o] on 2009-09-22
> **TrueTom said:**
> Unfortunately this true. For example: statically typed languages are usually faster than dynamically typed ones. JIT compilation can help but it is always an uphill battle.
That I can agree on. But statically typed languages are not the issue now. I'd bet there are usable JS implementations that are at least as fast as other scripting languages.

---

### Post by Joe_Bishop on 2009-09-22
> The shell seems remarkably usable currently
Is it a joke? The concept seems to be invalid -- sh1tload of clicks on basic actions.

---

### Post by [h2o] on 2009-09-22
> **Joe_Bishop said:**
> Is it a joke? The concept seems to be invalid -- sh1tload of clicks on basic actions.
Which actions? Opening frequently used apps should be faster than what current Gnome has. Opening less frequent apps is the same.

---

### Post by Longinus00 on 2009-09-22
My complaints are that it takes focus away from your desktop every time you want to start a new program. And if, god help you, you want to start a program that's not one of the 5 recently used ones because then it completely hides your desktop. If I wanted to launch a program with typing, gnome-do lets me do that WITHOUT losing context of the desktop.

Considering how few people actually leverage workspaces, especially people coming from windows or mac where such things don't have good implementations, that seems like it would put off lots of new and old users alike. I understand that they're trying to get people to leverage workspaces, but many people have a hard enough time trying to remember where they files they download go, even if it always downloads to the same directory! If many people lose files on their desktop how can you expect them to remember which workspace their program is on?

A problem with the examples on youtube that I've seen is that after a point, there is no point to having such a huge number of workspaces. If you're going to have a workspace for every single different application you open, you might as well keep them all on one or two workspaces and use expose (i.e. scale in compiz) to switch between them.

Maybe I'm just cynical but I'm pretty sure that if they actually sat some non-developers/non-linux people in front of gnome shell, they would NEVER use the workspace functionality while bemoaning how annoying it is to launch a new program.

---

### Post by 23meg on 2009-09-22
I don't get the "too much focus on workspaces" point.

As long as you don't click that plus icon on the bottom right, you don't even have to know or care about workspaces *at all*. Every new application launches in the current workspace, which, by default, is the only workspace that exists, and that you have to care about. 

Compared to the current workspace setup of most popular distributions shipping GNOME 2.2x, where you get multiple workspaces and a workspace switcher by default, it's simpler, and since you get a clear spatial overview of which window is in which workspace, it's harder for a user who doesn't have prior grasp of the paradigm of workspaces to get disoriented or lost in.

---

### Post by Longinus00 on 2009-09-22
> **23meg said:**
> I don't get the "too much focus on workspaces" point.

As long as you don't click that plus icon on the bottom right, you don't even have to know or care about workspaces *at all*. Every new application launches in the current workspace, which, by default, is the only workspace that exists, and that you have to care about. 

Compared to the workspace setup of most popular distributions, where you get multiple workspaces and a workspace switcher by default, it's simpler, and since you get a clear spatial overview of which window is in which workspace, it's harder for a user who doesn't have prior grasp of the paradigm of workspaces to get disoriented or lost in.

The fact that they separate the application launcher from your current desktop shows, to me anyway, that they're pushing the workspace concept. Why decouple them if you're going to not push workspaces? Why does launching a program that's not in the 5 ones listed require hiding the whole desktop? 

My main gripe about gnome shell is really the loss of context every time you're switching from the desktop to the desktop manager. Judging by the directly gnome-shell is going, they seem to expect you switch contexts regularly.

I should add that I don't have a current system running gnome-shell and am basing my observations off of this.

[http://www.youtube.com/watch?v=Bp1fWp6wino](http://www.youtube.com/watch?v=Bp1fWp6wino)

---

### Post by Joe_Bishop on 2009-09-22
> **'[h2o] said:**
> Which actions? Opening frequently used apps should be faster than what current Gnome has. Opening less frequent apps is the same.
I can drop "frequently used apps" on the panel, so current one will be faster. In addition, these overlay switch in gnome-shell is hard to eye. Simple menu is much more neutral in this field. E.g., opening bookmarks (gnome devs spoiled the whole idea though, with their tiny 5-bookmark limit, so I need to recompile all the time when new gnome-panel comes) in current gnome is easy to eye: open Places, choose destination. In gnome-shell you need to suffer from switching into ugly blacky overlay, which takes ages, then choose your location and switch again. It's stupid, these basic actions shouldn't switch context as gnome-shell does.

---

### Post by meborc on 2009-09-22
> **Longinus00 said:**
> The fact that they separate the application launcher from your current desktop shows, to me anyway, that they're pushing the workspace concept. Why decouple them if you're going to not push workspaces? Why does launching a program that's not in the 5 ones listed require hiding the whole desktop? 

My main gripe about gnome shell is really the loss of context every time you're switching from the desktop to the desktop manager. Judging by the directly gnome-shell is going, they seem to expect you switch contexts regularly.

I should add that I don't have a current system running gnome-shell and am basing my observations off of this.

[http://www.youtube.com/watch?v=Bp1fWp6wino](http://www.youtube.com/watch?v=Bp1fWp6wino)

you should try the latest gnome-shell with karmic... you would get a better idea on how snappy and usable it is (i'm still getting used to it, but i like what i see)

and i have used only 1 workspace while using gnome-shell... so i don't see your point

---

### Post by Longinus00 on 2009-09-22
> **Joe_Bishop said:**
> I can drop "frequently used apps" on the panel, so current one will be faster. In addition, these overlay switch in gnome-shell is hard to eye. Simple menu is much more neutral in this field. E.g., opening bookmarks (gnome devs spoiled the whole idea though, with their tiny 5-bookmark limit, so I need to recompile all the time when new gnome-panel comes) in current gnome is easy to eye: open Places, choose destination. In gnome-shell you need to suffer from switching into ugly blacky overlay, which takes ages, then choose your location and switch again. It's stupid, these basic actions shouldn't switch context as gnome-shell does.

Seeing as how you run gnome-shell, I hope you don't mind a few questions about it since I am currently not using it. Everyone else feel free to answer these if you can.

1. What is with that auto-expose thing when you launch gnome shell? To me this just breaks context with you workspaces even more because now, when you change to a different workspace, it won't even look like the preview. Also, to me this seems like it would be even harder to tell what windows you have open because it will further reduce their size thus making text illegible.

2. Is there any other view besides list view when selecting applications or recently used documents? It seems like icon view would be the natural fit here since they're already taking over the whole viewing area anyway. Only using a single column of space to select things seems wholly impractical as people are moving towards 16:10 and 16:9 resolutions, especially with those small tiny buttons to switch pages.

3. Are there keyboard shortcuts for switching between workspaces and moving windows between workspaces? I find that I use workspaces most efficiently if I don't have to fumble with the gui.

4. Is there a panel workspace switcher or are you stuck with using gnome shell to preview your workspaces?

5. How does this thing work with dual/multiple monitor setups?

> **meborc said:**
> you should try the latest gnome-shell with karmic... you would get a better idea on how snappy and usable it is (i'm still getting used to it, but i like what i see)

and i have used only 1 workspace while using gnome-shell... so i don't see your point

What advantages have you noticed in gnome-shell on a single workspace vs. the previous gnome panel?

---

### Post by bela42 on 2009-09-22
Well, I actually gave gnome shell a try lately and found it very pleasant to use.

I do completely disagree with all the yada yada about "context switching" all the time, since if I open a menu - what I do is a context switch. Using gs the menu is just looking a little different, so what all the fuss about?

So, what is actually the usability problem with "switching from the desktop context"???

---

### Post by VMC on 2009-09-22
> **Longinus00 said:**
> What advantages have you noticed in gnome-shell on a single workspace vs. the previous gnome panel?
This would be my question, as I don't have enough programs open to warrant having multiple Desktops available. I don't even use the switch Desks. Or rarely. I would question the Gnome Shell overhead.

I watched that video and its impressive but maybe not for me, unless programs were more responsive.

---

### Post by bela42 on 2009-09-22
> **VMC said:**
> This would be my question, as I don't have enough programs open to warrant having multiple Desktops available. I don't even use the switch Desks. Or rarely. I would question the Gnome Shell overhead.

I watched that video and its impressive but maybe not for me, unless programs were more responsive.

As for advantage: better. organization. of. information.

I use to have many programs open at the same time.

I did not notice any overhead.

I did not notice any degradation in programs resposiveness.

---

### Post by Longinus00 on 2009-09-22
> **bela42 said:**
> As for advantage: better. organization. of. information.

How exactly does it better organise information?

---

### Post by Joe_Bishop on 2009-09-22
> **Longinus00 said:**
> Seeing as how you run gnome-shell, I hope you don't mind a few questions about it since I am currently not using it. Everyone else feel free to answer these if you can.

1. What is with that auto-expose thing when you launch gnome shell? To me this just breaks context with you workspaces even more because now, when you change to a different workspace, it won't even look like the preview. Also, to me this seems like it would be even harder to tell what windows you have open because it will further reduce their size thus making text illegible.

2. Is there any other view besides list view when selecting applications or recently used documents? It seems like icon view would be the natural fit here since they're already taking over the whole viewing area anyway. Only using a single column of space to select things seems wholly impractical as people are moving towards 16:10 and 16:9 resolutions, especially with those small tiny buttons to switch pages.

3. Are there keyboard shortcuts for switching between workspaces and moving windows between workspaces? I find that I use workspaces most efficiently if I don't have to fumble with the gui.

4. Is there a panel workspace switcher or are you stuck with using gnome shell to preview your workspaces?

5. How does this thing work with dual/multiple monitor setups?



What advantages have you noticed in gnome-shell on a single workspace vs. the previous gnome panel?

1. Yes, it really breakes it. I feel this. Some guys under the "wow" effect, but I'm not, these thing is not smooth, breake everything.

2. Currently only list view. They've realized users need application menu, so they've put it into the right panel. But the submenu items appearance is horrible: ugly blacky giant panel which hides everything else, including exposed workspaces.

3. Switching between workspaces is worse than in current gnome, because now we have constant workspaces and used to switching between them, know where we should to switch now. In gnome-shell workspace configuration is dynamic, so you can't make any habits, it reduces workspace usability very much. Old Ctrl+Alt+<Arrow> shortcuts work though.

4. Yes, you only can preview in overlay, no workspace switcher configuration in the panel (it's impossible by their design)

5. Didn't try it, because I have the only monitor at home. Don't have time at workplace to try it.

---

### Post by Merk42 on 2009-09-22
Hmm why do I think GNOME Shell is the wrong direction?

[list][*]I don't like the icons in the overlay with the text.  The text always gets truncated, and it obscures the dots that are there to give a hint to how many windows.
I've brought that up to the mailing-list at GNOME, but since my post wasn't followed by "oh and here's some code that changes it" they didn't care.

[*]Giant black wasted space at top in overlay mode.  Why not have the open/frequent applications there horizontally?

[*]+ for open workspace is easy to click, yet - to erase you have to hunt around to whatever workspace it is.  This is silly since the last workspace will always be removed.  As a test go click the + Rapidly as see how many workspaces you can add, now see how long it takes you to remove them all.

[*]No way of seeing what applications are open without interaction from the user.

[*]Most comically, someone here tell me how to do something as basic and **emptying my trash**[/list]

---

### Post by cyberkilla on 2009-09-22
> **Merk42 said:**
> Hmm why do I think GNOME Shell is the wrong direction?

[list][*]I don't like the icons in the overlay with the text.  The text always gets truncated, and it obscures the dots that are there to give a hint to how many windows.
I've brought that up to the mailing-list at GNOME, but since my post wasn't followed by "oh and here's some code that changes it" they didn't care.

[*]Giant black wasted space at top in overlay mode.  Why not have the open/frequent applications there horizontally?

[*]+ for open workspace is easy to click, yet - to erase you have to hunt around to whatever workspace it is.  This is silly since the last workspace will always be removed.  As a test go click the + Rapidly as see how many workspaces you can add, now see how long it takes you to remove them all.

[*]No way of seeing what applications are open without interaction from the user.

[*]Most comically, someone here tell me how to do something as basic and **emptying my trash**[/list]

Whenever I use it, I feel like my workspaces are trapped in a padded cell. I feel like I have less space; the walls are closing in on me!!!
:lolflag:

---

### Post by zombiepig on 2009-09-22
Random question... but does anyone know if there's any official stance about wobbly windows making it into gnome shell/mutter? I can't stand desktops without wobbly now, it makes everything so static and lifeless :P

---

### Post by NCLI on 2009-09-22
I can't even get it working :(

```
seph@NCLI-MAINFRAME:~$ gnome-shell --replace
Window manager warning: Failed to read saved session file /home/seph/.config/mutter/sessions/1038426ac9711a0cdc125364753310059400000029600024.ms: Failed to open file '/home/seph/.config/mutter/sessions/1038426ac9711a0cdc125364753310059400000029600024.ms': No such file or directory                                   
      JS LOG: Loading tweener.js                                               
      JS LOG: Loading tweenlist.js                                             
      JS LOG: Done loading tweenlist.js                                        
      JS LOG: Done loading tweener.js                                          

** (process:14469): WARNING **: Couldn't change nice value of process.

** (process:14473): WARNING **: Couldn't change nice value of process.

** (process:14474): WARNING **: Couldn't change nice value of process.

** (process:14476): WARNING **: Couldn't change nice value of process.

** (process:14475): WARNING **: Couldn't change nice value of process.

** (process:14477): WARNING **: Couldn't change nice value of process.
    JS ERROR: !!!   Exception was: Error: Failed to convert UTF-8 string to JS string: Invalid byte sequence in conversion input                              
    JS ERROR: !!!     lineNumber = '0'                                         
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Failed to convert UTF-8 string to JS string: Invalid byte sequence in conversion input")@:0
("Failed to convert UTF-8 string to JS string: Invalid byte sequence in conversion input")@gjs_throw:0
@:0
([object _private_Shell_AppInfo])@/usr/share/gnome-shell/js/ui/appDisplay.js:322
()@/usr/share/gnome-shell/js/ui/appDisplay.js:350
()@/usr/share/gnome-shell/js/ui/appDisplay.js:205
AppDisplay()@/usr/share/gnome-shell/js/ui/appDisplay.js:170
(AppDisplay,false)@/usr/share/gnome-shell/js/ui/dash.js:163
ResultArea(AppDisplay,false)@/usr/share/gnome-shell/js/ui/dash.js:150
()@/usr/share/gnome-shell/js/ui/dash.js:767
Dash()@/usr/share/gnome-shell/js/ui/dash.js:555
()@/usr/share/gnome-shell/js/ui/overview.js:112
Overview()@/usr/share/gnome-shell/js/ui/overview.js:78
start()@/usr/share/gnome-shell/js/ui/main.js:73
@<main>:1
'
    JS ERROR: !!!     message = 'Failed to convert UTF-8 string to JS string: Invalid byte sequence in conversion input'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Failed to convert UTF-8 string to JS string: Invalid byte sequence in conversion input
seph@NCLI-MAINFRAME:~$ Window manager warning: Failed to read saved session file /home/seph/.config/metacity/sessions/1038426ac9711a0cdc125364753310059400000029600024.ms: Failed to open file '/home/seph/.config/metacity/sessions/1038426ac9711a0cdc125364753310059400000029600024.ms': No such file or directory
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
seph@NCLI-MAINFRAME:~$ ** (gnome-panel:14487): DEBUG: Adding applet 0.
** (gnome-panel:14487): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:14487): DEBUG: Adding applet 1.
** (gnome-panel:14487): DEBUG: Adding applet 2.
** (gnome-panel:14487): DEBUG: Adding applet 3.

(gnome-panel:14487): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 24
** (gnome-panel:14487): DEBUG: Adding applet 4.
** (gnome-panel:14487): DEBUG: Adding applet 5.
Unable to open desktop file /usr/share/applications/firefox-3.1.desktop for panel launcher: No such file or directory
Unable to open desktop file /usr/share/applications/VirtualBox.desktop for panel launcher: No such file or directory
Unable to open desktop file  for panel launcher: Not a regular file
** (gnome-panel:14487): DEBUG: Adding applet 6.
** (gnome-panel:14487): DEBUG: Adding applet 7.
** (gnome-panel:14487): DEBUG: Adding applet 8.
** (gnome-panel:14487): DEBUG: Adding applet 9.
** (gnome-panel:14487): DEBUG: Adding applet 10.
** (gnome-panel:14487): DEBUG: Adding applet 11.

(gnome-panel:14487): Gdk-WARNING **: /build/buildd/gtk+2.0-2.17.11/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window
** (gnome-panel:14487): DEBUG: Adding applet 12.
** (gnome-panel:14487): DEBUG: Adding applet 13.
** (gnome-panel:14487): DEBUG: Adding applet 14.
** (gnome-panel:14487): DEBUG: Adding applet 15.
** (gnome-panel:14487): DEBUG: Adding applet 16.
```

---

### Post by ukblacknight on 2009-09-22
> **NCLI said:**
> I can't even get it working :(


I can't either!  Different message to you though.  I am trying it in a VM (with Guest Additions installed).

Error message is attached.

---

### Post by damnick on 2009-09-23
I run gnome-shell without any problem with 1 monitor or with 2 monitors in tween view.
But the i try to run it with 2 monitors (2 seperate screens) i get the following errors:

~/gnome-shell/source/gnome-shell/src$ ./gnome-shell --replace
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 16: Another compositing manager is running on screen 0
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: add_win: assertion `info != NULL' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: meta_compositor_sync_window_geometry: assertion `info' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: add_win: assertion `info != NULL' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: meta_compositor_sync_window_geometry: assertion `info' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: add_win: assertion `info != NULL' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: meta_compositor_sync_window_geometry: assertion `info' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: add_win: assertion `info != NULL' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: meta_compositor_sync_window_geometry: assertion `info' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: add_win: assertion `info != NULL' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: meta_compositor_sync_window_geometry: assertion `info' failed
&#928;&#961;&#959;&#949;&#953;&#948;&#959;&#960;&#959;&#943;&#951;&#963;&#951; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957;: Log level 8: add_win: assertion `info != NULL' failed
Shell killed with signal 11
e-genius@e-genius-server:~/gnome-shell/source/gnome-shell/src$ ** (gnome-panel:8116): DEBUG: Adding applet 0.
** (gnome-panel:8116): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:8116): DEBUG: Adding applet 1.
** (gnome-panel:8116): DEBUG: Adding applet 2.
** (gnome-panel:8116): DEBUG: Adding applet 3.
** (gnome-panel:8116): DEBUG: Adding applet 4.
** (gnome-panel:8116): DEBUG: Adding applet 5.
** (gnome-panel:8116): DEBUG: Adding applet 6.
** (gnome-panel:8116): DEBUG: Adding applet 7.
** (gnome-panel:8116): DEBUG: Adding applet 8.
** (gnome-panel:8116): DEBUG: Adding applet 9.
** (gnome-panel:8116): DEBUG: Adding applet 10.
** (gnome-panel:8116): DEBUG: Adding applet 11.
** (gnome-panel:8116): DEBUG: Adding applet 12.
** (gnome-panel:8116): DEBUG: Adding applet 13.
** (gnome-panel:8116): DEBUG: Adding applet 14.
** (gnome-panel:8116): DEBUG: Adding applet 15.
** (gnome-panel:8116): DEBUG: Adding applet 16.
** (gnome-panel:8116): DEBUG: Adding applet 17.
** (gnome-panel:8116): DEBUG: Adding applet 18.
** (gnome-panel:8116): DEBUG: Adding applet 19.
** (gnome-panel:8116): DEBUG: Adding applet 20.
** (gnome-panel:8116): DEBUG: Adding applet 21.
** (gnome-panel:8116): DEBUG: Adding applet 22.
** (gnome-panel:8116): DEBUG: Adding applet 23.
** (gnome-panel:8116): DEBUG: Adding applet 24.
** (gnome-panel:8116): DEBUG: Adding applet 25.
** (gnome-panel:8116): DEBUG: Adding applet 26.
** (gnome-panel:8116): DEBUG: Adding applet 27.

(gnome-panel:8116): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

(gnome-panel:8116): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:8116): DEBUG: Adding applet 28.
** (gnome-panel:8116): DEBUG: Adding applet 29.
** (gnome-panel:8116): DEBUG: Adding applet 30.
** (gnome-panel:8116): DEBUG: Adding applet 31.
** (gnome-panel:8116): DEBUG: Adding applet 32.

(gnome-panel:8116): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 24
** (gnome-panel:8116): DEBUG: Adding applet 33.
** (gnome-panel:8116): DEBUG: Adding applet 34.
** (gnome-panel:8116): DEBUG: Adding applet 35.
** (gnome-panel:8116): DEBUG: Adding applet 36.
** (gnome-panel:8116): DEBUG: Adding applet 37.

(gnome-panel:8116): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:8116): DEBUG: Adding applet 38.
** (gnome-panel:8116): DEBUG: Adding applet 39.
** (gnome-panel:8116): DEBUG: Adding applet 40.
** (gnome-panel:8116): DEBUG: Adding applet 41.

---

### Post by 23meg on 2009-09-23
[QUOTE=Longinus00]My complaints are that it takes focus away from your desktop every time you want to start a new program.[/QUOTE]

[QUOTE=Longinus00]My main gripe about gnome shell is really the loss of context every time you're switching from the desktop to the desktop manager.[/QUOTE]

Why exactly do you need to know about the state of your desktop at the time of launching a new application? 

[QUOTE=Joe_Bishop]In gnome-shell you need to suffer from switching into ugly blacky overlay,[/quote]

You shove your mouse to the upper left corner,

[QUOTE=Joe_Bishop]which takes ages,[/QUOTE]

and the overlay opens immediately, without requiring a click,

[QUOTE=Joe_Bishop]then choose your location [/QUOTE]

then choose your location,

[QUOTE=Joe_Bishop]and switch again.[/QUOTE]

and click the left mouse button, and the application / place opens and the overlay goes away.

---

### Post by Longinus00 on 2009-09-23
> **damnick said:**
> I run gnome-shell without any problem with 1 monitor or with 2 monitors in tween view.
But the i try to run it with 2 monitors (2 seperate screens) i get the following errors:

I was researching this earlier and I'm almost completely certain gnome-shell doesn't support multiple monitors yet (at the very least, not well anyway).

> **23meg said:**
> Why exactly do you need to know about the state of your desktop at the time of launching a new application?

Considering that gnome-shell is trying to change the status quo (no other mainstream desktop that I can think of does this) I believe there should be a better reason for this behaviour besides, "why not". 

Imagine this scenario:
1. I decide to start an application in response to something I see on my screen (perhaps I want to start gimp because I start downloading an image).
2. My internet goes down so my download fails.
3. I decide I don't want to start gimp any more and would rather spend my time figuring out why my internet dropped.

If I couldn't see my desktop while hunting around for gimp (imagine it's not one of the 5 applications I use often), when I come back from gnome-shell I'll see that I'm loading gimp for nothing and have to go back into gnome shell to start some *other* program. If the application launcher didn't hide the whole screen I can respond to the new situation immediately.

---

### Post by 23meg on 2009-09-23
> **Longinus00 said:**
> 
Considering that gnome-shell is trying to change the status quo (no other mainstream desktop that I can think of does this) I believe there should be a better reason for this behaviour besides, "why not". 

There is. Mine wasn't a general "why not" argument though; it was a genuine question directed to you specifically.

> **Longinus00 said:**
> Imagine this scenario:
1. I decide to start an application in response to something I see on my screen (perhaps I want to start gimp because I start downloading an image).
2. My internet goes down so my download fails.
3. I decide I don't want to start gimp any more and would rather spend my time figuring out why my internet dropped. 

If I couldn't see my desktop while hunting around for gimp (imagine it's not one of the 5 applications I use often), when I come back from gnome-shell I'll see that I'm loading gimp for nothing and have to go back into gnome shell to start some *other* program. If the application launcher didn't hide the whole screen I can respond to the new situation immediately.

I concur that the application launching method can be improved ([and so do others]("http://live.gnome.org/GnomeShell/DesignerPlayground/ApplicationBrowsing")), but that doesn't necessarily have to do with context switching. You're switching contexts when navigating the GNOME 2.x panel menus with clicks and hovers, too. Since [you can't and don't have to multitask]("http://www.azarask.in/blog/post/you-cant-multitask/") when navigating a menu, the parts of the screen not covered by the menus as they unfold are equally irrelevant to the task you're performing. The only difference is that your whole screen isn't being repainted, as is the case with the current GNOME Shell.

---

### Post by TrueTom on 2009-09-23
> **23meg said:**
> Since [you can't and don't have to multitask]("http://www.azarask.in/blog/post/you-cant-multitask/") when navigating a menu, the parts of the screen not covered by the menus as they unfold are equally irrelevant to the task you're performing.

Quoting some random and crappy blog post by some random guy makes a pretty weak argument. Almost all people are quite capable to multitask, otherwise you couldn't smoke, drive and having a phone conversation at the same time.

---

### Post by Merk42 on 2009-09-23
I see you didn't break down my issues with GNOME Shell, 23meg, does that mean we're in agreement with those?

---

### Post by Jaybugg13 on 2009-09-23
I like the general concpet, but I would like to retain some of my options.  So if Compiz will not work in GNOME shell that's fine, but the feel of the cube vs Overlay mode with workspaces is completly different and to some this will be a welcome change as they didn't like the cube and to others (such as myself) I prefer the open feeling of the cube.  The overlay mode itself is nice, in fact if I could view the cube when window/workspace switching and open apps in Overlay with the current workspace format I would be in heaven.  Granted as many have pointed out there is a little waster space above the Overlay window, perhaps recent docs could occupy the horizontal space above the overlay and app icons could use the vertical space to the left?

---

### Post by 23meg on 2009-09-23
> **Merk42 said:**
> I see you didn't break down my issues with GNOME Shell, 23meg, does that mean we're in agreement with those?

No. I just think you (any many others in this thread) are focusing too much on the *current* status of GNOME Shell and too little on the long term, and I don't find the particular short term concerns you've listed  worth discussing here.

---

### Post by Longinus00 on 2009-09-23
> **23meg said:**
> There is. Mine wasn't a general "why not" argument though; it was a genuine question directed to you specifically.



I concur that the application launching method can be improved ([and so do others]("http://live.gnome.org/GnomeShell/DesignerPlayground/ApplicationBrowsing")), but that doesn't necessarily have to do with context switching. You're switching contexts when navigating the GNOME 2.x panel menus with clicks and hovers, too. Since [you can't and don't have to multitask]("http://www.azarask.in/blog/post/you-cant-multitask/") when navigating a menu, the parts of the screen not covered by the menus as they unfold are equally irrelevant to the task you're performing. The only difference is that your whole screen isn't being repainted, as is the case with the current GNOME Shell.

Perhaps context switching wasn't the best wordage on my part but my point still stands. Allow me to try to explain it a little more clearly.

Looking through that link it looks like they are dead set on hiding the whole desktop whenever you launch a program. Lets try a new thought experiment to show where this may be less than ideal.

Imagine that I'm giving help to someone online via chat of some sort and I want them to start a program. I could tell them something like "applications->internet->firefox" and they could do that, all the while looking back at my message for reference. Using gnome-shell this becomes much harder because you can't reference typed out instructions for two main reasons:
1. Gnome-shell automatically expose the windows when you go into gnome-shell so if they have several windows open the text becomes impossible to read.
2. Any time you want to launch a program, either by going through the menu or typing the application name it hides the whole screen.

---

### Post by Jaybugg13 on 2009-09-23
> **TrueTom said:**
> Quoting some random and crappy blog post by some random guy makes a pretty weak argument.
 
Sorry but I have to agree with 23meg. While the human brain is very adept at creating task constructs in truth what we feel is multitasking is really just switching between these constructs very quickly leading to the perception that we can do it all at once. 
[http://www.npr.org/templates/story/story.php?storyId=95256794](http://www.npr.org/templates/story/story.php?storyId=95256794)

---

### Post by MadMan2k on 2009-09-23
> **TrueTom said:**
> Quoting some random and crappy blog post by some random guy makes a pretty weak argument. Almost all people are quite capable to multitask, otherwise you couldn't smoke, drive and having a phone conversation at the same time.
well its not a random crappy blogpost by a random guy. ;)
google for him and be enlightened...

---

### Post by 23meg on 2009-09-23
> **TrueTom said:**
> Quoting some random and crappy blog post by some random guy makes a pretty weak argument. Almost all people are quite capable to multitask, otherwise you couldn't smoke, drive and having a phone conversation at the same time.

Except that [Aza Raskin]("http://en.wikipedia.org/wiki/Aza_Raskin") is not exactly "some random guy", and you obviously didn't take time to read even the first few sentences before calling the post "crappy" and my argument "weak":

> We can talk on a cell phone while driving to work, and we can compose complex sentences while typing. But, if you stop to reflect on it, you can only do those things at the same time because at least one of them is automatic. In the first case driving is automatic, and in the second case typing is automatic. You&#8217;ve done them so often that you&#8217;ve habituated to them: doing them doesn&#8217;t require any thinking. Can you still talk on your cell phone while driving through a rainstorm on unfamiliar roads? Would you still be able to concentrate on writing if you had just switched to a Dvorak keyboard? I didn&#8217;t think so.

There's a lot of mental friction involved in finding an application in the GNOME 2.x panel menus (click a small area of the screen, hover over some menu item that you think is relevant, read through the list that pops up on the side, move your cursor over the item you figured is the one you want, click it); it's by no means automatic, even if you've habituated the behavior. You can't really look at a picture, read a piece of text, or perform any other task requiring significant intellectual activity *while* launching an application.

---

### Post by Merk42 on 2009-09-23
> **23meg said:**
> No. I just think you (any many others in this thread) are focusing too much on the *current* status of GNOME Shell and too little on the long term, and I don't find the particular short term concerns you've listed  worth discussing here.

How are any of those 'short term'?
I hope you don't mean because GNOME Shell isn't finalized yet, in which case **any** issue is short term.

Let's take the beef I have wiht application switching/see what's open. I read the design document and they're actually advocating the advanced use of Alt-Tab as the only non-overlay way to do it!

---

### Post by zekopeko on 2009-09-23
> **Merk42 said:**
> How are any of those 'short term'?
I hope you don't mean because GNOME Shell isn't finalized yet, in which case **any** issue is short term.

Let's take the beef I have wiht application switching/see what's open. I read the design document and they're actually advocating the advanced use of Alt-Tab as the only non-overlay way to do it!

Agreed.
What irks me is that the Ayatana project is offering them a great way to display notifications and yet they are ignoring them.
For the most part I have the feeling that Gnome-Shell is Gnome's rushed job at trying to compete with KDE4. A weekend experiment that people took seriously without exploring any other venue for improving Gnome.

@23meg
What Merk42 said stands. I don't see any long term goals of it beyond what is now in it. They insist on this overlay mode, which is nothing but a glorified widget layer. Have they conducted user testing? Examined the workflow of your average user?

---

### Post by 23meg on 2009-09-23
> **Merk42 said:**
> How are any of those 'short term'?
I hope you don't mean because GNOME Shell isn't finalized yet, in which case **any** issue is short term.

Any issue that is being discussed or will obviously be addressed through a redesign of the respective component or further development is short term. It's obvious to me that whatever ends up as the panel and window manager replacement for GNOME 3.x will let you switch tasks effortlessly and empty your trash; it's just that those components haven't seen enough design and development effort *yet*.

---

### Post by TrueTom on 2009-09-23
> **MadMan2k said:**
> well its not a random crappy blogpost by a random guy. ;)
google for him and be enlightened...

I know who he is. The point is "proof by name dropping" is lame and doesn't really work. And the post is indeed crappy and merely a straw man argument. He probably is still a great guy and all... :)

---

### Post by Merk42 on 2009-09-23
> **23meg said:**
> Any issue that is being discussed or will obviously be addressed through a redesign of the respective component or further development is short term. It's obvious to me that whatever ends up as the panel and window manager replacement for GNOME 3.x will let you switch tasks effortlessly and empty your trash; it's just that those components haven't seen enough design and development effort *yet*.

It's obvious it **should**, but **will** it? As myself and zekopeko pointed out, neither of us see any documentation that there is a plan to do such a thing.

I really hope you're doing more than just assuming it will be fixed.

---

### Post by zekopeko on 2009-09-23
> **23meg said:**
> Any issue that is being discussed or will obviously be addressed through a redesign of the respective component or further development is short term. It's obvious to me that whatever ends up as the panel and window manager replacement for GNOME 3.x will let you switch tasks effortlessly and empty your trash; it's just that those components haven't seen enough design and development effort *yet*.

I think (from the info I've read) that window manager is mutter (metacity+clutter = metacity 3). Windows decoration are going to be fixed with client-side rendering or whatever the name of the tech is. I hope that windows decorations are merged in the main window since there is really no reason to have wasted vertical space for 3/4 buttons and the ability to drag the window.

From the design doc there is not going to be a lower panel but the notification area. So that means that application switching is going to suck. It's interesting that Win and Mac went with the icon/dock paradigm of representing applications. Guess that Gnome really has to try not be Windows. Perhaps at least Gnome-shell will silence those "Linux isn't Windows and shouldn't copy from it" people.

---

### Post by 23meg on 2009-09-23
> **zekopeko]Have they conducted user testing?[/QUOTE]

[It seems so]("http://live.gnome.org/GnomeShell/UserObservationData"), and everyone is invited to conduct more.

[QUOTE=Merk42 said:**
> It's obvious it **should**, but **will** it? As myself and zekopeko pointed out, neither of us see any documentation that there is a plan to do such a thing.

[http://live.gnome.org/GnomeShell/DesignerPlayground/BreadcrumbsEtc](http://live.gnome.org/GnomeShell/DesignerPlayground/BreadcrumbsEtc) , for one.

> **Merk42]I really hope you're doing more than just assuming it will be fixed.[/QUOTE]

Realistically, yes, I'm just assuming the trash and task management stuff will be fixed *by others*, since my shortage of interest in those, coupled with limited time and energy, means I'm not planning to contribute anything into them. But I'm cooking up some wireframes for application launching, workspace management and Zeitgeist integration. 

[QUOTE=TrueTom said:**
>  The point is "proof by name dropping" is lame 

Referencing an article to support your point isn't supposed to be "proof", but citation of supporting evidence. 

[quote=TrueTom]and doesn't really work.[/quote]

It works way better than bare assertion.

---

### Post by Longinus00 on 2009-09-23
> **23meg said:**
> [It seems so]("http://live.gnome.org/GnomeShell/UserObservationData"), and everyone is invited to conduct more.

That is NOT a page about user testing for gnome-shell. It is a page about creating a persona ([http://en.wikipedia.org/wiki/Persona_%28marketing%29](http://en.wikipedia.org/wiki/Persona_%28marketing%29)) for the development of gnome-shell. That is completely different.

I should also add that I still stand by the fact that I believe the whole concept of launching applications in a totally different space from your current workspace is flawed and is not a "short term" issue because it is in the fundamental design documents.

---

### Post by 23meg on 2009-09-23
> **Longinus00 said:**
> That is NOT a page about user testing for gnome-shell. It is a page about creating a persona ([http://en.wikipedia.org/wiki/Persona_%28marketing%29](http://en.wikipedia.org/wiki/Persona_%28marketing%29)) for the development of gnome-shell. That is completely different.

How is it not about user testing (the better term is "usability testing", but anyway), when its title is "UserObservationData", it contains a link to a page with test results, and invites people to do user testing? I guess the sentence "It would also be good to create a set of personas for use in developing the GNOME Shell" led you to interpret "Jessy the Office Manager" as a persona.

It's of course indirectly true that "it's a page about creating a persona", since you can't realistically create useful personas without user observation and interviews.

[QUOTE=Longinus00]I should also add that I still stand by the fact that I believe the whole concept of launching applications in a totally different space from your current workspace is flawed and is not a "short term" issue because it is in the fundamental design documents.[/QUOTE]

I didn't say that it was a "short term" issue; I said that it needed improvement and cited some proposals by others on improving it.

---

### Post by Longinus00 on 2009-09-23
> **23meg said:**
> How is it not about user testing (the better term is "usability testing", but anyway), when its title is "UserObservationData", it contains a link to a page with test results, and invites people to do user testing? I guess the sentence "It would also be good to create a set of personas for use in developing the GNOME Shell" led you to interpret "Jessy the Office Manager" as a persona.

It's of course indirectly true that "it's a page about creating a persona", since you can't realistically create useful personas without user observation and interviews.



I didn't say that it was a "short term" issue; I said that it needed improvement and cited some proposals by others on improving it.

> Take some time, grab a friend, and watch them interact with their desktop - Windows, GNOME, KDE, or OS X, whatever is their desktop of choice.

How is it testing the usability of gnome-shell exactly (which was what zekopeko was asking for)?

There are also no proposals for launching an application without taking up the whole screen.

---

### Post by zekopeko on 2009-09-23
> **Longinus00 said:**
> How is it testing the usability of gnome-shell exactly (which was what zekopeko was asking for)?

There are also no proposals for launching an application without taking up the whole screen.

Well using my layman skills:

This is user testing. You are observing users and their interaction.
The problem is that Gnome-shell wasn't tested nor planned. It just sprung up during a hacker sprint and continued going.

Ideally you would observe how people interact with the computer (23meg's link) and then you would design a prototype. Then you would test the prototype and fix any flaws (if they aren't fundamental) and test again.

The problem with Gnome-shell is that they just started coding without any spec. They actually composed the spec around the code, not the other way around. 

Ubuntu Software Store is a great example of a good spec. mpt conducted user testing and create the user interface in high detail BEFORE there was any code written. After that, code was written, minor issues fixed and the spec updated.

---

### Post by 23meg on 2009-09-23
> **Longinus00 said:**
> How is it testing the usability of gnome-shell exactly (which was what zekopeko was asking for)?

It's not.

[quote=Longinus00]There are also no proposals for launching an application without taking up the whole screen.[/QUOTE]

Did you think of proposing one?

---

### Post by Longinus00 on 2009-09-23
> **23meg said:**
> Did you think of proposing one?

My proposal of "don't have that overlay" isn't really going to get much traction I'm afraid as it conflicts with the raison d'etre of gnome-shell.

---

### Post by 23meg on 2009-09-24
> **Longinus00 said:**
> My proposal of "don't have that overlay" isn't really going to get much traction I'm afraid as it conflicts with the raison d'etre of gnome-shell.

Indeed. Similarly, my proposal of "Don't expect all people, including people new to computing, and those with orthopedic disorders, to be so dexterous and persistent as to fluently navigate the GNOME 2.x panel menus with hovers, unfolding hierarchical lists, scrolling and the like", hadn't found much popularity back in the day. 

But as a plan B, you *may* be able to come up with an application launcher design that keeps more of the screen readable. (Hints: More transparency? Smaller icons? Less padding? Not "expose"ing windows and just scaling the active window?  Doing that if and only if you have one workspace?)

---

### Post by coolen on 2009-09-24
My thoughts on the Shell:

First, I like the overlay for working with workspaces. The concept is very nice. I like being able to see what's open on each in the expose-like mode, and rearrange them there. The present implementation is not helpful. It takes too long for an application to appear on the new workspace, but I'm assuming that's not a design defect.

Of course, if you need that, Compiz can almost do this. The difference is that expo does not do any scale-like arranging of windows. In this regard, GS > Compiz in design.

Of course, having to add my usual four workspeces really sucks. I hope that I get the option to save my configuration in the future, and I also hope that switching will better reflect their layout in overlay.

Application launching in the Shell currently sucks. What if I want to open a few applications in quick succession? I often do this when I first log in: Firefox, Spicebord, Emesene, Pidgin, VirtualBox. With Gnome Do, that's a total of fifteen keystrokes. Sounds like a lot, except that in typing "Sounds like a lot" I actually exceeded that.

In GS, launching an application gets rid of the overlay, so I have to go back in there each time seperately (find-as-you-type in the Shell also sucks at the moment, especially when compared with Do, but again, that's not by design). It's a pain. Also, I have the overlay. Why not keep it up? I'll usually throw that selection of five applications over three workspaces. You've got the perfect system there for me to do it in. Just launch them in the first workspace and let me rearrange them before I return to the desktop: I know when I'm done with the overlay. You do not.

While I do personally like the workspace treatment, I know that most will not appreciate it. It seems like such a strange place to throw your development effort, and I feel it's currently all that the Shell has going for it. As it is, a new plugin for Compiz could easily render the Shell useless for me, and I suspect a lot of users.

---

### Post by gnomeuser on 2009-09-24
I found one thing in prolonged use. The gnome-shell necessitates workspace use which I normally loath since there is no good indication of where I put my work without me designing a workflow already, e.g. all communications goes on WS1, webbrowser on WS2 and so on.

With gs this is not needed since for everything you do, you have to call up the activities menu and then all your windows and workspaces are neatly arranged with big visuals. This is nice.. at least for a while, I imagine once I start needing more than 4 workspaces the visuals will one again be small and the workspace workflow equally painful. 

The primary reason I dislike workspaces is that I tend to lose work that way I forget where I put things, or I pick up a second task and when I am done with that shutdown the desktop having forgot the original half written article.. and puff.

I feel that the approach gs has taken makes workspaces tolerable up to a certain number on a given screen size after which you once again tend to get work going MIA. For my laptop the number seems to be 4, for my netbook I fear it is more like 1 or 2.

I like that when I let my cursor flow to the activities menu I need not click on it making navigation with a trackball effortless. You toss the ball upwards and voila there is all your work. On a physically resistive touchpad like that on my netbook however it's terrible and involves far to much moving my finger. Sadly the real world contains more of the latter and not enough trackballs, making the design optimized for the wrong case. 

It's sadly also very buggy, little things like the labels and buttons being places on top of text makes it look unprofessional and act plain weird in use. When you drag an application onto the big + to put on it's own new workspace it doesn't become transparent making it hard to know if you are hitting the icon or not.. little things that just add to the weight and immaturity of the interface, sadly there are boatloads of them in there. 

Performance is better now than it used to be but it is still remarkably slow, especially the animations are putting a real slowdown into the whole thing.

---

### Post by [h2o] on 2009-09-25
> **gnomeuser said:**
> I like that when I let my cursor flow to the activities menu I need not click on it making navigation with a trackball effortless. You toss the ball upwards and voila there is all your work. On a physically resistive touchpad like that on my netbook however it's terrible and involves far to much moving my finger. Sadly the real world contains more of the latter and not enough trackballs, making the design optimized for the wrong case. That is a problem, but is it a new problem? The menus are in the top left corner now as well, so you still move the mouse to the same screen space. Or am  I missing something? I don't use laptops a lot these days.

Also, there is the possibility to open the overlay using a keyboard shortcut (or at least it used to, haven't been able to compile and test for a few weeks).

---

### Post by Longinus00 on 2009-09-25
> **23meg said:**
> Indeed. Similarly, my proposal of "Don't expect all people, including people new to computing, and those with orthopedic disorders, to be so dexterous and persistent as to fluently navigate the GNOME 2.x panel menus with hovers, unfolding hierarchical lists, scrolling and the like", hadn't found much popularity back in the day. 

But as a plan B, you *may* be able to come up with an application launcher design that keeps more of the screen readable. (Hints: More transparency? Smaller icons? Less padding? Not "expose"ing windows and just scaling the active window?  Doing that if and only if you have one workspace?)

Those people who you've listed as being unable to navigate gnome 2.x seem to get along fine in windows with its menus and hierarchical lists.

I'm not quite sure why application launching needs the overlay. If you're going to start a program and it's going to come up on the current workspace, why do you need to leave the workspace in the first place? They could just fancy up the panel launcher and it would give the same functionality without confusing people coming from other operating systems. If they leave overlay for workspaces only and it becomes very popular with people, then maybe they can think about putting other functionality in there as well.

When I heard Shuttleworth's quote from LinuxCon I thought immediately of gnome-shell.

> During his keynote, he extended an invitation to any open source application to submit their software for testing by user-experience experts. The sessions would be recorded for posterity, and the developer would not be able to interact with the user.

"If the developer is in the room, they have to say nothing. It's the shut the f--- up protocol," Shuttleworth said. "You sit and watch someone struggle with the software that you've so lovingly produced."

Shuttleworth noted that there traditionally has been some tension in software development between user interface (UI) people and developers, which is a big problem. 

[http://www.internetnews.com/dev-news/article.php/3840826/Shuttleworth+Dont+Give+Up+the+Linux+Desktop.htm](http://www.internetnews.com/dev-news/article.php/3840826/Shuttleworth+Dont+Give+Up+the+Linux+Desktop.htm)

*edit*

I've been meaning to ask, what happens in gnome-shell if you don't have 3d acceleration? It can't possibly have the overlay right? Does nothing work yet without 3d acceleration?

---

### Post by TrueTom on 2009-09-25
> **Longinus00 said:**
> I've been meaning to ask, what happens in gnome-shell if you don't have 3d acceleration? It can't possibly have the overlay right? Does nothing work yet without 3d acceleration?

The official position is that every computer in the last 5 years has OpenGl capable hardware and therefore it's OK to require it. If you don't have a working 3D driver, tough luck. Feel free to use something else.

---

### Post by Longinus00 on 2009-09-25
> **TrueTom said:**
> The official position is that every computer in the last 5 years has OpenGl capable hardware and therefore it's OK to require it. If you don't have a working 3D driver, tough luck. Feel free to use something else.

Is there a fallback or are people just going to be unable to use gnome 3.0 unless they have 3d acceleration working?

---

### Post by TrueTom on 2009-09-25
> **Longinus00 said:**
> Is there a fallback or are people just going to be unable to use gnome 3.0 unless they have 3d acceleration working?

Yes, the proposed solutions are you can fork Metacity or use something else (and I'm not making this up). The Solaris people aren't very happy about this either.

---

### Post by 23meg on 2009-09-25
> **Longinus00]Those people who you've listed as being unable to navigate gnome 2.x seem to get along fine in windows with its menus and hierarchical lists.[/QUOTE]

If by "get along fine" you mean "have to tolerate and adapt to and suffer through, due to lack of an alternative", that's right. It's not that they're unable to said:**
> decreasing the efficiency of use, increasing the number of errors, and lessening the satisfaction they get from using the software[/URL].

[QUOTE=Longinus00]I'm not quite sure why application launching needs the overlay. If you're going to start a program and it's going to come up on the current workspace, why do you need to leave the workspace in the first place? They could just fancy up the panel launcher and it would give the same functionality without confusing people coming from other operating systems. If they leave overlay for workspaces only and it becomes very popular with people, then maybe they can think about putting other functionality in there as well.

While placing the trigger for launching an application somewhere outside the context of "Activities" sounds out of place at first, it's perhaps worth a mockup.

The primary point where we disagree seems to be that you perceive triggering the overlay as "leaving the workspace", whereas I do not. That perception is probably rooted in the fact that triggering the overlay, in that it repaints the whole screen, is disruptive enough to trigger a sense of location / context shift, even though it may not be meant to convey one.

---

### Post by Longinus00 on 2009-09-25
> **23meg said:**
> If by "get along fine" you mean "have to tolerate and adapt to and suffer through, due to lack of an alternative", that's right. It's not that they're unable to; they're mostly able, but the interface involves too much motor skill friction, [decreasing the efficiency of use, increasing the number of errors, and lessening the satisfaction they get from using the software]("http://www.useit.com/alertbox/20030825.html").



While placing the trigger for launching an application somewhere outside the context of "Activities" sounds out of place at first, it's perhaps worth a mockup.

The primary point where we disagree seems to be that you perceive triggering the overlay as "leaving the workspace", whereas I do not. That perception is probably rooted in the fact that triggering the overlay, in that it repaints the whole screen, is obstrusive enough to trigger a sense of location / context shift, even though it may not be meant to convey one.

If you have more than one workspace open then gnome-shell will show all the other workspaces open. If you happen to have several workspaces open (this number probably depends on the resolution of your monitor) each with a few windows open, you might not be able to identify which workspace you just came from if it weren't highlighted. In my mind this should be considered "leaving the workspace".

> Yes, the proposed solutions are you can fork Metacity or use something else (and I'm not making this up). The Solaris people aren't very happy about this either.

When you say "you can fork metacity", I take it they mean somebody besides the gnome developers? This seems dangerous considering the state of linux drivers for many video cards. (my computers run ATI and intel for graphics cards so I've experienced a whole gamut of unfortunate regressions)

---

### Post by coolen on 2009-09-25
Regarding the whole overlay/leaving the workspace thing...

I think it'd be less jarring a change if the background didn't scale down with the workspaces.

Imagine if you moused over to the corner, and then the activities menu appeared on the left, the workspaces all came into view, scaled and all, while the background didn't move (not sure what you'd do for the background of the workspaces...this is just something I thought of in the shower).

It would feel less like a change of environment and more like an augmentation, I think.

---

### Post by Longinus00 on 2009-09-25
> **coolen said:**
> Regarding the whole overlay/leaving the workspace thing...

I think it'd be less jarring a change if the background didn't scale down with the workspaces.

Imagine if you moused over to the corner, and then the activities menu appeared on the left, the workspaces all came into view, scaled and all, while the background didn't move (not sure what you'd do for the background of the workspaces...this is just something I thought of in the shower).

It would feel less like a change of environment and more like an augmentation, I think.

My point of contention is why do you have to show all the workspaces when you open the activities menu? Is there some functionality that ties them together? Why can't that just come up on the current workspace?

---

### Post by Merk42 on 2009-09-25
> **coolen said:**
> Regarding the whole overlay/leaving the workspace thing...

I think it'd be less jarring a change if the background didn't scale down with the workspaces.

Imagine if you moused over to the corner, and then the activities menu appeared on the left, the workspaces all came into view, scaled and all, while the background didn't move (not sure what you'd do for the background of the workspaces...this is just something I thought of in the shower).

It would feel less like a change of environment and more like an augmentation, I think.

Well think about it when there are multiple desktops, would you see the same background spread across all of them? Wouldn't that make the user think the applications were running in sections of the one screen instead of wholly different screens?

---

### Post by coolen on 2009-09-25
I'm not suggesting just throw them up on the one background. There'd be something to differentiate them (borders of some kind).

I'd just feel less like I'm leaving the desktop if the background stayed put. Makes it feel more like the same environment, just different functionality.

Longinus00, I agree. It seems like a silly thing to do, but the devs seem pretty set. Just thought it might help allay one (not all) of your criticisms.

Also, a note: you can drag applications over to workspaces, or onto the + to give it its own new workspace, so for those who use workspaces heavily, it does make sense. This brings it back to the age old question: why put so much effort into a feature that so few people make use of?

---

### Post by Sophont on 2009-09-25
The problem I have with the Gnome Shell is that it makes a bonus feature (workspaces) into a central feature and then goes ahead and enforces one single way to handle it - killing off Compiz use in the process.

What I like about Gnome 3 is getting rid of old cruft and offering a script language for easy manipulation (I prefer Python over JS - but I get why JS was choen for this and t's not a bad language either).

I also like the new default that you get to the running app in the typical case and need to explicitly open a new window for the exceptional case.

I'm trying to keep an open mind and I follow the progress on Gnome Shell with interest and I occasionally give it a try. But to me the whole focus on workspaces and implementing 1 policy is the wrong direction.

Workspaces are a geek feature. Most users start a browser and a couple other apps and don't have a need to spread them over several workspaces. So it looks to me that a lot focus of GS design is wasted on a feature that's not relevant to most users while at the same time limits the minority who do use it.

The incompatibility with Compiz is a big problem IMHO. You can find a lot of comments on Youtube by windows users who saw a Cube or other cool Compiz feature that made them try Linux for the first time.

The effects the Gnome Shell offers are nicely done so far - but won't lead to as many popular youtube videos as Compiz does.

Perhaps I underestimate the adaptability of the Gnome Shell - so far it looks like users will be forced into 1 particular vision of how a desktop should look and work (while we currently have a lot of variety with Gnome-Do Docky, Widgets, Compiz Effects, etc...).

I hope I'm wrong but atm it looks to me as if Gnome will fork between 2.x and 3. With that I mean 2.x will continue for a long time parallel to 3.x while 3.x might never be the dominant gnome branch and eventually fully replacing 2.x.

---

### Post by Longinus00 on 2009-09-25
I wanted to come back to a few points because I don't believe gnome-shell solves what you mentioned before.

> **23meg said:**
> Indeed. Similarly, my proposal of "Don't expect all people, including people new to computing, and those with orthopedic disorders, to be so dexterous and persistent as to fluently navigate the GNOME 2.x panel menus with hovers, unfolding hierarchical lists, scrolling and the like", hadn't found much popularity back in the day. 
...


Gnome-shell currently has an a hierarchical application launcher[1] just like you mention in the first post as a downside of gnome 2.x. I've not seen any mock-up of gnome-shell that didn't include some sort of hierarchical application launcher. While gnome-shell may not have "scrolling" in a sense, you have to navigate "pages" of applications and I'm not sure that is an improvement (in some mockups[2] the scrolling returns). 

1. [http://live.gnome.org/GnomeShell/DesignerPlayground/ApplicationBrowsing](http://live.gnome.org/GnomeShell/DesignerPlayground/ApplicationBrowsing)
2. [http://live.gnome.org/GnomeShell/DesignerPlayground/AppBrowsingAlternative](http://live.gnome.org/GnomeShell/DesignerPlayground/AppBrowsingAlternative)

> **23meg said:**
> If by "get along fine" you mean "have to tolerate and adapt to and suffer through, due to lack of an alternative", that's right. It's not that they're unable to; they're mostly able, but the interface involves too much motor skill friction, [decreasing the efficiency of use, increasing the number of errors, and lessening the satisfaction they get from using the software]("http://www.useit.com/alertbox/20030825.html").
...


Linking to a page describing usability doesn't really prove that windows users "have to tolerate and adapt to and suffer through, due to lack of an alternative". Coincidently Jakob Nielsen, the person you linked to, recently wrote a post discussing our current topic "Fresh vs. Familiar: How Aggressively to Redesign"[3]. I'll just quote his conclusion here for convenience's sake.

> Generally, it's best to evolve a UI with gentle changes rather than offer a totally fresh design. I thus strongly recommend getting the basic design right in the first place, before you launch, so that it can live for several years with minor updates. Before you release anything to customers, use techniques such as rapid iterative design and paper prototypes to thoroughly explore the design space and polish the usability.

This approach contrasts with that of simply "throwing something at the wall" to see what sticks. Indeed, some people advocate just releasing your best guess, because the beauty of the Web is that you can always change it if you're wrong. This is true, but you'll be unpopular, because

    * you'll be mistreating users by subjecting them to a flawed design that you could have fixed with just a few days of pre-release user testing; and
    * you'll antagonize users by making them suffer the very changes that we know they hate. 

In general, get it right, and then change slowly. Still, there are two cases in which a more radical approach is appropriate:

    * If you have almost no current users and expect a major design improvement to dramatically expand the user base. In this case, the business loss from punishing your current customers is small enough to be worth taking. Of course, it's still a gamble that you'll actually be able to attract a vastly bigger audience. Remember the old adage: a bird in the hand is better than two in the bush. Unless you're sure that there are millions of users in that bush, you might not want to go there.
    * If your old design has incrementally evolved for so many years that the overall user experience has become overly convoluted and lost any sense of a unified conceptual structure. 

I am of the opinion that gnome-shell's development is in the "throwing something at the wall" camp. I turn to the lack of a tasklist so far into development as evidence for this. I also present the the sidebar as another example.

As per the design document's description[4], it acts as a replacement storage area for all the applets that were once in the panel (e.g. stocks, sticky notes, etc.) and seems to mimic  windows vista sidebar's functionality. If they moved the favorites and applications onto this sidebar, it would effectively a gnome panel on the side of the screen. So far they've taken functionality that is commonly in the top panel and spread it across three different places. In gnome 2.x this behavior is already possible, albeit without the flashyness of gnome-shell.

Looking at his point of when it is appropriate for radical user changes, I fail to see how gnome 2.x's UI paradigm satisfies either of his statements. This first statement is obviously not true but the second one deserves some consideration. Gnome has worked rather hard at not being convoluted by reducing the number of items users can normally adjust.

I guess what I'm trying to say is, I've yet to hear a compelling reason for how gnome-shell is changing how to get to the same functionality. Windows ribbon groups like commands so they are presented with each other in a more visual way without sacrificing functionality (i.e. anything you wanted to do in office2003, you can do in office2007). Gnome-shell has relocated various functionality without, to my knowledge, any specific gain.

3. [http://www.useit.com/alertbox/familiar-design.html](http://www.useit.com/alertbox/familiar-design.html)
4. [http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf](http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf)

---

### Post by gnomeuser on 2009-09-25
> **'[h2o] said:**
> That is a problem, but is it a new problem? The menus are in the top left corner now as well, so you still move the mouse to the same screen space. Or am  I missing something? I don't use laptops a lot these days.

Also, there is the possibility to open the overlay using a keyboard shortcut (or at least it used to, haven't been able to compile and test for a few weeks).

To do anything in the new activities menu you really have to move the mouse, in the current scheme I can keep my cursor in the "work area" and navigate the menu with shortcut keys. I realise it is not what most people would do but it works well to not rub my fingertips bloody.

---

### Post by cgroza on 2009-09-25
It better be something cool.I am not waiting so long for another gnome clone....

---

### Post by Merk42 on 2009-09-25
> **cgroza said:**
> It better be something cool.I am not waiting so long for another gnome clone....

You can see videos or, if you feel like it, try out the early version right now.

Also, I don't see how it could be a GNOME clone when it's made by GNOME :confused:

---

### Post by dadedo123 on 2009-09-25
What is Gnome Shell? :s

---

### Post by NCLI on 2009-09-25
The new interface for GNOME 3.

---

### Post by Merk42 on 2009-09-25
> **dadedo123 said:**
> What is Gnome Shell? :s

Ha, well yes, I suppose the first post doesn't do a job of explaining it.

GNOME Shell is a part of GNOME 3.  GNOME 3 is actually GNOME 2.30, Karmic will have 2.28 so the next round version of Ubuntu after Karmic will tentatively use GNOME 3 and therefore GNOME Shell.


GNOME Shell is the overall interface, the desktop environment.  A different way of managing / launching applications.  In much the same way that KDE does it differently than GNOME, GNOME Shell will do it differently than those two.

It is still early in development and arguably has a focus on workspaces.  If you want to try it, you can build it using the instructions [here](http://live.gnome.org/GnomeShell#building) (you may also have to install other dependencies, but the terminal will tell you what ones).  For testing purposes it is easy to turn it on/off and since everything in installed to a folder called gnome-shell in your home folder, you don't have to worry about it messing up your system.

---

### Post by dadedo123 on 2009-09-25
> **Merk42 said:**
> Ha, well yes, I suppose the first post doesn't do a job of explaining it.

GNOME Shell is a part of GNOME 3.  GNOME 3 is actually GNOME 2.30, Karmic will have 2.28 so the next round version of Ubuntu after Karmic will tentatively use GNOME 3 and therefore GNOME Shell.


GNOME Shell is the overall interface, the desktop environment.  A different way of managing / launching applications.  In much the same way that KDE does it differently than GNOME, GNOME Shell will do it differently than those two.

It is still early in development and arguably has a focus on workspaces.  If you want to try it, you can build it using the instructions [here](http://live.gnome.org/GnomeShell#building) (you may also have to install other dependencies, but the terminal will tell you what ones).  For testing purposes it is easy to turn it on/off and since everything in installed to a folder called gnome-shell in your home folder, you don't have to worry about it messing up your system.
Errghhh! What the hell is this? Just watched a video in youtube, and it's messed up. It doesn't even look like an everyday OS, the GUI is V*I*L*E. So Ubuntu Lynx LTS will be based on Gnome Shell by default? Will we still be able to use Gnome?

---

### Post by Merk42 on 2009-09-25
> **dadedo123 said:**
> Errghhh! What the hell is this? Just watched a video in youtube, and it's messed up. It doesn't even look like an everyday OS, the GUI is V*I*L*E.
Keep in mind it is unfinished.

If you do feel strongly about it, let the developers know on the [mailing list](http://mail.gnome.org/mailman/listinfo/gnome-shell-list).

**DO NOT** say such things as "...the GUI is V*I*L*E" and/or not provide an alternative idea.  When you do provide an alternative, **DO NOT** have it be "just like it was in the old GNOME".  If you do any of those **DO NOT** things, I'm sure you'll just be considered whining and be ignored.


> **dadedo123 said:**
>  So Ubuntu Lynx LTS will be based on Gnome Shell by default? Will we still be able to use Gnome?
Don't know yet as that's too far into the future.

---

### Post by dadedo123 on 2009-09-25
> **Merk42 said:**
> 
Don't know yet as that's too far into the future.

Not really. It's less than a year away. :p

---

### Post by Eclipse. on 2009-09-25
> **dadedo123 said:**
> Not really. It's less than a year away. :p

Gnome 3 (2.30) wont be everything done, infact it will be far from it.Dont expect to see gnome-shell by default until Karmic+3 possibly +2.

---

### Post by rubinstein on 2009-09-26
> **dadedo123 said:**
> So Ubuntu Lynx LTS will be based on Gnome Shell by default?
No. The release after Lynx may be based on Gnome Shell.

---

### Post by Joe_Bishop on 2009-09-26
I hope no one of gnome releases will be based on gnome-shell.

---

### Post by n3had on 2009-09-26
> **dadedo123 said:**
> What is Gnome Shell? :s

[http://www.youtube.com/watch?v=32zkq1wHk6Q](http://www.youtube.com/watch?v=32zkq1wHk6Q)

Check the video for a preview and How to install it..

---

### Post by ajr901 on 2009-09-26
i was able to fix the error that a lot of people are getting about jhbuild. all i did was run sudo apt-get install python-dev and selected option number 1. it worked fine

---

### Post by ukblacknight on 2009-09-26
One thing I don't understand about Gnome-Shell so far, is how do you switch applications?  For example, by default, the window selector is on the bottom panel in traditional gnome - how do you change applications?  The only way I see to do it is by clicking activities and messing with the work spaces, but that seems far too long winded.

Also, I think it's a bit unobvious as to where to browse all the applications.  There is a small browse button to show the application categories, surely this should be emphasised more, maybe have the categories directly in the Activities window.

---

### Post by Merk42 on 2009-09-26
> **ukblacknight said:**
> One thing I don't understand about Gnome-Shell so far, is how do you switch applications?  For example, by default, the window selector is on the bottom panel in traditional gnome - how do you change applications?  The only way I see to do it is by clicking activities and messing with the work spaces, but that seems far too long winded.

**Optimisic thought:** It hasn't been implemented yet
**Pessimsitc Thought:** According to the [design document](http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf), they want you to use Alt-Tab

---

### Post by PRGUY85 on 2009-09-26
> **Merk42 said:**
> **Optimisic thought:** It hasn't been implemented yet
**Pessimsitc Thought:** According to the [design document](http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf), they want you to use Alt-Tab

I have been doing that by grouping common apps by workspace and switching to that workspace by moving mouse toward Left Upper border to pick workspaces.

---

### Post by 23meg on 2009-09-26
> **Merk42 said:**
> **Optimisic thought:** It hasn't been implemented yet
**Pessimsitc Thought:** According to the [design document](http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf), they want you to use Alt-Tab

*Where* in design document do "they want you to use Alt-Tab"? 

And, are you actually testing GNOME Shell? Did you ever notice the highlights under the application names in the overlay (page 17 of the design document)?

---

### Post by 23meg on 2009-09-26
> **Merk42 said:**
> GNOME 3 is actually GNOME 2.30, 

It's not set in stone yet; it may be 2.32 as well.

[QUOTE=Merk42]Karmic will have 2.28 so the next round version of Ubuntu after Karmic will tentatively use GNOME 3 and therefore GNOME Shell.[/QUOTE]

Most likely, almost certainly not.

---

### Post by tretle on 2009-09-26
> **23meg said:**
> *Where* in design document do "they want you to use Alt-Tab"? 

And, are you actually testing GNOME Shell? Did you ever notice the highlights under the application names in the overlay (page 17 of the design document)?

My opinion is this is not being coordinated properly. 
That feature which the gnome-shell guys came up with of not allowing the user to open multiple instances of the same app conflicts with the work which is being done to try and move tabs into Metacity to ensure that any tab in a Gnome3.0 app would be process independent.

---

### Post by 23meg on 2009-09-26
> **Longinus00 said:**
> 
Gnome-shell currently has an a hierarchical application launcher[1] just like you mention in the first post as a downside of gnome 2.x. I've not seen any mock-up of gnome-shell that didn't include some sort of hierarchical application launcher. While gnome-shell may not have "scrolling" in a sense, you have to navigate "pages" of applications and I'm not sure that is an improvement (in some mockups[2] the scrolling returns). 

1. [http://live.gnome.org/GnomeShell/DesignerPlayground/ApplicationBrowsing](http://live.gnome.org/GnomeShell/DesignerPlayground/ApplicationBrowsing)
2. [http://live.gnome.org/GnomeShell/DesignerPlayground/AppBrowsingAlternative](http://live.gnome.org/GnomeShell/DesignerPlayground/AppBrowsingAlternative)

I didn't **ever** say that GNOME Shell's *current* application launching model is any good. Let me repeat, for the [third]("http://ubuntuforums.org/showpost.php?p=7995613&postcount=411") [time]("http://ubuntuforums.org/showpost.php?p=7996326&postcount=428"): it needs improvement, and I too am cooking up some wireframes in order to propose a new method. 

My intention in citing the GNOME 2.x application launching paradigm was to put forward that different "eras" of software design have their different paradigms where certain approaches are favored over others, and it's kind of hard to swim right against conjuncture, in support of your point that "Don't have that overlay" is not going to be an immediately plausible suggestion for improving GNOME Shell. I didn't mean that application launching sucked in GNOME 2.x and is all good in GNOME Shell.

> **Longinus00 said:**
> Linking to a page describing usability doesn't really prove that windows users "have to tolerate and adapt to and suffer through, due to lack of an alternative". 

Of course it doesn't. And as I said before, it [isn't meant to]("http://ubuntuforums.org/showpost.php?p=7996217&postcount=426"). It's meant to *support* my point by taking a shortcut to explain that usability has multiple components (instead of me typing paragraph after paragraph in my limited time only to do it worse than Jakob Nielsen or [mpt]("http://mpt.net.nz/archive/2008/08/11/usability")), and that for new computer users and people with certain disabilities using complicated hierarchical menu structures that involve a lot of motor skill friction (as opposed to simply "Windows users", which is a misquotation of what I said), three of those components go down. 

[QUOTE=Longinus00]Coincidently Jakob Nielsen, the person you linked to, recently wrote a post discussing our current topic "Fresh vs. Familiar: How Aggressively to Redesign"[3]. I'll just quote his conclusion here for convenience's sake.

...

I am of the opinion that gnome-shell's development is in the "throwing something at the wall" camp. I turn to the lack of a tasklist so far into development as evidence for this. I also present the the sidebar as another example.[/QUOTE]

There's no "lack of a task list". Names of the active applications are highlighted. But I agree that the so far GNOME Shell seems closer to the "throwing something at the wall" camp, but due to mysterious forces I cannot quite deduce from its history, it's somehow looking like a good throw in many ways.

[QUOTE=Longinus00]Looking at his point of when it is appropriate for radical user changes, I fail to see how gnome 2.x's UI paradigm satisfies either of his statements. [/QUOTE]

And I don't see why it has to, since Nielsen is thinking mainly on web design, and [it's a clearly stated goal in GNOME 3 to "break" the user experience]("http://live.gnome.org/ThreePointZero/Plan") that's been refined with small moves over the years.

[QUOTE=Longinus00]I guess what I'm trying to say is, I've yet to hear a compelling reason for how gnome-shell is changing how to get to the same functionality. [/QUOTE]

Especially given that we may not see GNOME Shell deemed ready to replace the existing components altogether until GNOME 2.32, I find it a bit early to talk about feature parity.

---

### Post by Merk42 on 2009-09-26
> **23meg said:**
> *Where* in design document do "they want you to use Alt-Tab"?
Page 22.


> **23meg said:**
> And, are you actually testing GNOME Shell? Did you ever notice the highlights under the application names in the overlay (page 17 of the design document)?
Yes I am, and I have noticed that. In fact I've brought up here (and on the GNOME Shell mailing list) my issue with it.  The issue being that the names of the applications obscure the visibility of said highlights, and given how the names are almost always truncated they should removed completely.

---

### Post by 23meg on 2009-09-26
> **tretle said:**
> the work which is being done to try and move tabs into Metacity to ensure that any tab in a Gnome3.0 app would be process independent.

Could you cite a link for this?

---

### Post by 23meg on 2009-09-26
> **Merk42 said:**
> Page 22.

So? Alt+Tab is one way, the overlay is another, and the workspace view is another. 

(Hint: Try opening six windows, and switching between them by pressing and holding Alt+Tab, moving your cursor over the icon for app you want to switch to, and releasing. That's fast.)

> **Merk42 said:**
> The issue being that the names of the applications obscure the visibility of said highlights

If by "obscure the visibility" you mean "may make it hard to notice at all", that sounds right; especially in low contrast, and for people with poor sight. That's probably going to be resolved in the future (of GTK+ 3, probably) by highlighting the whole icon instead of just the name. Still sounds worth a bug report.

---

### Post by tretle on 2009-09-26
> **23meg said:**
> Could you cite a link for this?

NP, [http://blogs.gnome.org/metacity/2009/07/19/recent-happenings-in-metacity-and-mutter/](http://blogs.gnome.org/metacity/2009/07/19/recent-happenings-in-metacity-and-mutter/) <- thats the news from the Metacity Blog.

There is also a previous post on having custom applications options in Metacity on an app by app basis(rhythmbox would have play, pause etc) that I don't think can be taken advantage of with the gnome shell window management.
The reason why the app specific options are being put in is that applications have a bad habit of taking over the notification area and one of the reasons they do is to get those custom options the task bar does not provide. Meaning it should be an important priority to expose these features so app developers don't feel the need to keep on abusing the notification area.

---

### Post by Merk42 on 2009-09-26
> **23meg said:**
> So? Alt+Tab is one way, the overlay is another, and the workspace view is another. 

(Hint: Try opening six windows, and switching between them with by pressing and holding Alt+Tab, moving your cursor over the icon for app you want to switch to, and releasing. That's fast.)

I wasn't really questioning if it was fast or not.  Just saying the Alt-Tab switcher seems to be the way they'd want you to switch.  First line on "Application Switcher" says "Keyboard Activated" then later specifying Alt-Tab

That's all my point was.  The bigger issue is that there is nothing that shows running applications (to just see or switch to) without user interaction.


> **23meg said:**
> If by "obscure the visibility" you mean "may make it hard to notice at all", that sounds right; especially in low contrast, and for people with poor sight. That's probably going to be resolved in the future (of GTK+ 3, probably) by highlighting the whole icon instead of just the name. Still sounds worth a bug report.
It is what I meant yes.  I don't see how highlighting the whole icon would help though. How would it be able to show "Name backlight with 2 or 3 light sources"?

---

### Post by Starks on 2009-09-26
These bugs needs more attention.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/413497](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/413497)
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/426755](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/426755)

---

### Post by 23meg on 2009-09-26
> **Merk42 said:**
> I wasn't really questioning if it was fast or not. 

I know; mine was a side point. I've just discovered it and really like it.

> **Merk42]Just saying the Alt-Tab switcher seems to be the way they'd want you to switch.  First line on "Application Switcher" says "Keyboard Activated" then later specifying Alt-Tab[/QUOTE]

That's how the draft design document "*sounds*", *right now*. What counts is how the model will have evolved and how official documentation will describe it, in the course of a year or so. Hence "short term".

[QUOTE=Merk42]That's all my point was.  The bigger issue is that there is nothing that shows running applications (to just see or switch to) without user interaction.[/QUOTE]

Right, but that may change said:**
> How would it be able to show "Name backlight with 2 or 3 light sources"?

It wouldn't; perhaps then it would be "Whole icon backlight with 2 or 3 light sources", or some other way. Remember that the design document is a draft.

---

### Post by 23meg on 2009-09-26
> **tretle said:**
> NP, [http://blogs.gnome.org/metacity/2009/07/19/recent-happenings-in-metacity-and-mutter/](http://blogs.gnome.org/metacity/2009/07/19/recent-happenings-in-metacity-and-mutter/) <- thats the news from the Metacity Blog.

Right, that sounds out of place, at least for Mutter. 

[QUOTE=tretle]There is also a previous post on having custom applications options in Metacity on an app by app basis(rhythmbox would have play, pause etc) that I don't think can be taken advantage of with the gnome shell window management.[/QUOTE]

It looks like [the plan]("http://blogs.gnome.org/mccann/2009/07/05/getting-the-message/") is to cover that under the "Detail mode" of the message tray. It can also be integrated into the existing click and hold pop-ups (just thinking out loud).

---

### Post by Merk42 on 2009-09-26
> **23meg said:**
> That's how the draft design document "*sounds*", *right now*. What counts is how the model will have evolved and how official documentation will describe it, in the course of a year or so. Hence "short term".
Are we back on the long term/short term thing again? If so, by your definition **every** critique of GNOME Shell is "short term"

> **23meg said:**
> Right, but that may change; there are some mockups sugge... OK, even if I cite that link another time now, someone else will come shouting "There's no task list!!1 That's Krazy I'm switching to KDEE!!!1" within the next few posts and it will be worthless.
I've seen the ideas in the designer playground if that's what you're referring to.  I don't know what the likely hood of any of them being implemented are though. It just seems like a LOT of ideas, but no information on if it would get implemented or not.[/QUOTE]

The only one I can think of that I've seen might have a chance is breadcrumbs. Every time I build GNOME Shell I hope to see it.

---

### Post by 23meg on 2009-09-26
> **Merk42 said:**
> Are we back on the long term/short term thing again? If so, by your definition **every** critique of GNOME Shell is "short term"

No. How the wording of an incomplete draft design document that's meant to be read by a small group of developers and testers in the development phase *sounds* is *short term*. What kind of application switching GNOME Shell will have evolved to encourage in its final design and official documentation is *long term*. If you focus too much on the former, you tend to lose sight of the latter, and it's the latter that actually matters. Is this clear enough?

---

### Post by tretle on 2009-09-26
> **23meg said:**
> Right, that sounds out of place, at least for Mutter. 



It looks like [the plan]("http://blogs.gnome.org/mccann/2009/07/05/getting-the-message/") is to cover that under the "Detail mode" of the message tray. It can also be integrated into the existing click and hold pop-ups (just thinking out loud).

It doesn't seem out of place to simplify something which is becoming common practice. Independent processes in tabs are seen in chrome and are coming to Firefox and gtk apps too.  
One of the highlights include one tab not taking the other 15 down with it if it crashes.
The window manager should be handling this, it would make development so much simpler and organized. Rather than needing to reinvent the wheal every time an app wants independent processes in tabs.
It wouldn't even need any application specific code to implement.

---

### Post by ajr901 on 2009-09-26
Hey guys i keep getting the error:

*** error during stage configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/aj/gnome-shell/install --libdir '${exec_prefix}/lib64'  --disable-static --disable-gtk-doc  *** [7/7]


...any help?

---

### Post by buzzmandt on 2009-09-26
Ok, I built and test drove gs for the first time in many months and it has come a very long way.  I was actually shocked to see how much more complete it looked and felt.  I do kind of like it, but....

I tried opentennis just to give it something to do.  The game was laggy while in gs.  Makes me think it is kinda resource piggish.  Is this the case or will it eventually get snappier when it nears completion?

---

### Post by 23meg on 2009-09-26
> **tretle said:**
> It doesn't seem out of place to simplify something which is becoming common practice. Independent processes in tabs are seen in chrome and are coming to Firefox and gtk apps too.  
One of the highlights include one tab not taking the other 15 down with it if it crashes.
The window manager should be handling this, it would make development so much simpler and organized. Rather than needing to reinvent the wheal every time an app wants independent processes in tabs.
It wouldn't even need any application specific code to implement.

What I meant was that it sounded out of place to be going in both directions at once, as you said in post #468. But that was without reading at length to understand the intention in implementing that functionality in detail. It looks like reaching consensus is going to take time, as well as some application-specific thinking.

---

### Post by dadedo123 on 2009-09-27
If I install it right now will it be like a whole new environment, or will it just give the current gnome installation a skin?

---

### Post by Sophont on 2009-09-27
It's much more than just a new skin. The way workspaces are handled is very different, main menu and panels are replaced, it has a different window manager and Compiz doesn't work with it.

In short - yes - it's a different environment. That's the point actually. :-)

But the way it's currently offered the environment is temporary. You start it by executing
"gnome-shell --replace"
in a terminal and it will temporarily replace your current environment until you reboot (or explicitly return to metacity).

---

### Post by Regenweald on 2009-09-28
A bit away from the 'Love it, Hate it' back and forth, does anyone have any Idea or info on how Mutter will behave with Nouveau ?

---

### Post by krazyd on 2009-09-28
> **Regenweald said:**
> A bit away from the 'Love it, Hate it' back and forth, does anyone have any Idea or info on how Mutter will behave with Nouveau ?

Judging by [the official page]("http://nouveau.freedesktop.org/wiki/"), it won't work at all:
> Any 3-D functionality that might exist is still unsupported. Do not ask for instructions to try it.

IMHO, this is a _huge_ issue. Will Mutter really force all nvidia owners to use the proprietary driver? Does anyone know if this is the case?

Edit: [it seems that this is by design]("http://markmail.org/message/r2qudmoywdvujtum"):
> Nouveau is coming along nicely. As is 3D support for the latest AMD cards. I have every expectation that in a year (which is when we are really talking about GNOME Shell starting to be widely deployed) we will be able to support it with open source 3D drivers on the vast majority of what people are running. Including netbooks and other low-end devices. 
is nouveau really coming along that fast?

---

### Post by TrueTom on 2009-09-28
> **krazyd said:**
> is nouveau really coming along that fast?

Yes and no. It still is a huge gamble because the moment you run into a bug your computer is dead since you can't fallback to VESA. Lucid+1 should be a fun release cycle for some people.

But this is the price you have to pay for a modern desktop. Trust the Gnome Shell developers. There smarter than you and the rest of the world. It's not like Windows 7 or MacOS X would fallback gracefully to non-compositing if necessary. Oh, wait, they actually do. Hmm. They are obviously legacy systems.

---

### Post by seeker5528 on 2009-09-28
> **tretle said:**
> NP, [http://blogs.gnome.org/metacity/2009/07/19/recent-happenings-in-metacity-and-mutter/](http://blogs.gnome.org/metacity/2009/07/19/recent-happenings-in-metacity-and-mutter/) <- thats the news from the Metacity Blog.

Sounds like something is wrong to me. either the idea or the description of the idea.

Either the tabs are application centric and don't belong in the Window manager or they are an application agnostic function controlled by the window manager allowing any windows from any open applications could be combined into a tabbed window.

But I only read the first post that the blog linked to, maybe this was fleshed out in the follow ups?

I don't know about the rest of this either:

> That feature which the gnome-shell guys came up with of not allowing the user to open multiple instances of the same app conflicts with the work which is being done to try and move tabs into Metacity to ensure that any tab in a Gnome3.0 app would be process independent.

The only thing I have read about this aspect of gnome-shell indicated you would be allowed to open multiple instances, it just wouldn't be the default action when clicking a launcher for an application that is already open.

If the tabs were implemented as a function of the window manager with the intention that applications should use that instead of implementing their own tab functions, application developers would still have to choose to use that instead of their own, I could possibly see that being done for some small amount of apps that are officially part of Gnome, but I can't really see how a lot of developers would want to do that if they have to build in tab support anyway so that you don't have to be running a certain window manager for tabs to work.

Any way you look at it, I don't see how there is a conflict, you will not be running more than a single window manager in a single X session.

Later, Seeker

---

### Post by Regenweald on 2009-09-29
> **krazyd said:**
> Judging by [the official page]("http://nouveau.freedesktop.org/wiki/"), it won't work at all:


IMHO, this is a _huge_ issue. Will Mutter really force all nvidia owners to use the proprietary driver? Does anyone know if this is the case?

Edit: [it seems that this is by design]("http://markmail.org/message/r2qudmoywdvujtum"):

is nouveau really coming along that fast?

Thanks for the talkback, looks like this ride will be by the seat of the pants. nouveau is currently compositing nicely with metacity, A little drag when i move my transparent terminal but nothing to bother me. I guess I'll wait and see. I don't have anything against the blob, just wanted to support nouveau.

---

### Post by screaminj3sus on 2009-09-29
Just installed this and I LOVE IT. perfectly stable and smooth on my ati card (unlike compiz)

How to I make gnome shell default (start up automatically?)

---

### Post by mariner09 on 2009-09-29
How about modifying the overlay?

Mine is black and I've seen screenshots of different colors.

Also the applications category in the sidebar of the overlay?  I'd rather select some commonly used apps instead of what's shown.

---

### Post by ricsi-pontaz on 2009-09-29
Previous day I tried Gnome-Shell again. It is better than before, I love it! :popcorn:

---

### Post by Tompalaz on 2009-09-29
> **screaminj3sus said:**
> 

How to I make gnome shell default (start up automatically?)
Please share if you come up with anything. It won't take the syntax --replace if I put it in startup applications

---

### Post by shafin on 2009-09-29
> **Tompalaz said:**
> Please share if you come up with anything. It won't take the syntax --replace if I put it in startup applications
[http://www.mail-archive.com/gnome-shell-list@gnome.org/msg00023.html](http://www.mail-archive.com/gnome-shell-list@gnome.org/msg00023.html)

---

### Post by screaminj3sus on 2009-09-29
> **Tompalaz said:**
> Please share if you come up with anything. It won't take the syntax --replace if I put it in startup applications

I made a script I use to start it with one click, but when I set toe script to start up at boot it just freezes at login.

and @ last post that link is dead.

This is the command I used in the script:> 
~/gnome-shell/source/gnome-shell/src/./gnome-shell --replace

---

### Post by meborc on 2009-09-29
> **screaminj3sus said:**
> I made a script I use to start it with one click, but when I set toe script to start up at boot it just freezes at login.

and @ last post that link is dead.

that link is not dead for me... quoting from the link:> Hi,

On Sat, Aug 1, 2009 at 2:38 PM, Dean Loros<ubuntu1u...@gmail.com> wrote:
> Thanks for the respond Jon...Seems that it won't work that way on my
> system...Ubuntu Karmic testing. It is a interesting idea--but I guess
> that I was not clear enough--What I would like to do is create a other
> session to login to at GDM start...I've created the correct links & the
> Gnome-Shell shows on my list, but the session bombs out almost as soon
> as I go to it....

What I do is:

1) create a file called /usr/share/applications/gnome-shell.desktop
that looks like this:

[Desktop Entry]
Type=Application
Name=GNOME Shell
Exec=sh -c "jhbuild -f ~/gnome-shell.jhbuild run gnome-shell --replace"
NoDisplay=true
X-GNOME-Provides=panel;windowmanager;
X-GNOME-Autostart-Phase=Panel

(gnome-shell.jhbuild is the .jhbuildrc I use for building gnome-shell)

2) create a file called /usr/share/xsessions/gnome-shell.desktop that
looks like this:
[Desktop Entry]
Type=Application
Name=GNOME Shell
Comment=This session logs you into the GNOME shell.
Exec=gnome-session --default-session-key /desktop/gnome/session/shell_session
TryExec=gnome-session

3) create the shell_session gconf key:

gconftool-2 --set /desktop/gnome/session/shell_session --type list
--list-type string '[gnome-shell,gnome-settings-daemon]'

This key parallels /desktop/gnome/session/default_session but adds the
gnome-shell override.  Since the gnome-shell desktop file provides
panel and windowmanager it won't start the default panel and
windowmanager.

--Ray


---

### Post by meborc on 2009-09-29
> **screaminj3sus said:**
> This is the command I used in the script:

the "/./" is the problem part :D your system thinks you are referring to a "." folder

---

### Post by Milos_SD on 2009-09-29
I tryed to compile it on Jaunty, but I'm geting an error that there is no package "firefox-js" found. What is that, and how can I make it work? :)

---

### Post by Merk42 on 2009-09-29
> **Milos_SD said:**
> I tryed to compile it on Jaunty, but I'm geting an error that there is no package "firefox-js" found. What is that, and how can I make it work? :)
Did you try installing that package?
What instructions are you following?

---

### Post by Milos_SD on 2009-09-29
There is no firefox-js package in repos. I'm following instructions from gnome live as I always did.
[http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

---

### Post by Merk42 on 2009-09-29
> **Milos_SD said:**
> There is no firefox-js package in repos. I'm following instructions from gnome live as I always did.
[http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

So you've done it before?
Did you try deleting the gnome-shell folder and rebuilding?

---

### Post by Milos_SD on 2009-09-29
Yes I did deleted all folders, and started from begining.

---

### Post by danboy on 2009-09-30
I'm having the same issue with firefox-js, could it have anything to due with the fact I'm running shirotoku (firefox 3.5)??

---

### Post by Merk42 on 2009-09-30
> **danboy said:**
> I'm having the same issue with firefox-js, could it have anything to due with the fact I'm running shirotoku (firefox 3.5)??

I'm running Jaunty and have shiretoko installed from the Ubuntu repos.  I was still able to build GNOME Shell, though I do also have the firefox 3.0 version installed.

---

### Post by Merk42 on 2009-10-07
Sorry for the doublepost


**[GNOME Shell 2.28 released [a preview]](http://mail.gnome.org/archives/gnome-shell-list/2009-October/msg00003.html)**
**[Mutter 2.28 released [a preview]](http://mail.gnome.org/archives/gnome-shell-list/2009-October/msg00002.html)**

---

### Post by kaicrr77 on 2009-10-08
I got around the no firefox-js by installing xulrunner-1.9-dev which won't uninstall firefox 3.5.......now i'm stuck on the last part will let you know what I do to get past it.

---

### Post by kaicrr77 on 2009-10-08
K then I deleted the directory (gnome shell) rebuilt it again and... it worked.... I think this is probably the only post that will get you around firefox-js issue. I searched and searched.

---

### Post by Merk42 on 2009-10-08
Well now I can't build
```
*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/merk/gnome-shell/install --libdir '/home/merk/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [7/7]

```

---

### Post by kaicrr77 on 2009-10-08
> **Merk42 said:**
> Well now I can't build
```
*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/merk/gnome-shell/install --libdir '/home/merk/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [7/7]

```

what comes before that? It will tell you what you need.

---

### Post by Merk42 on 2009-10-08
> **kaicrr77 said:**
> what comes before that? It will tell you what you need.

```
checking for ST... configure: error: Package requirements (clutter-1.0 gtk+-2.0 libcroco-0.6) were not met:

No package 'libcroco-0.6' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ST_CFLAGS
and ST_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

So I need libcroco-0.6 which doesn't exist?

---

### Post by kaicrr77 on 2009-10-08
> **Merk42 said:**
> ```
checking for ST... configure: error: Package requirements (clutter-1.0 gtk+-2.0 libcroco-0.6) were not met:

No package 'libcroco-0.6' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ST_CFLAGS
and ST_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

So I need libcroco-0.6 which doesn't exist?

Try libcroco3 libcroco3-dev

---

### Post by Merk42 on 2009-10-08
> **kaicrr77 said:**
> Try libcroco3 libcroco3-dev

Ah that works thanks.

---

### Post by 23meg on 2009-10-11
Some recent GNOME Shell reportage:

[http://blog.fishsoup.net/2009/10/07/gnome-shell-2-28-0-a-preview/](http://blog.fishsoup.net/2009/10/07/gnome-shell-2-28-0-a-preview/)
[http://jasondclinton.livejournal.com/76065.html](http://jasondclinton.livejournal.com/76065.html)

---

### Post by DPic on 2009-10-14
What's the PPA for Gnome 3?

---

### Post by godhika on 2009-10-14
There is no such thing as a PPA for gnome 3. gnome 3 consist of a lot of different components wich are in different stadiums of development. A lot of things in the background like getting rid of old libraries and such are allready, at least partially, in gnome 2.28. other things, like the zeitgeist user interface are still behind closed curtains. people often mistake gnome 3 with the gnome shell only, but it ist just a part. gnome-shell is in the repositories, but is an outdated version. If you want to check out the current status of gnome-shell try this instructions [http://live.gnome.org/GnomeShell#head-3f60626bad6c0dbb60ecdbde36865c01a1dc1e98]("http://live.gnome.org/GnomeShell#head-3f60626bad6c0dbb60ecdbde36865c01a1dc1e98")

---

### Post by DPic on 2009-10-14
> **godhika said:**
> There is no such thing as a PPA for gnome 3. gnome 3 consist of a lot of different components wich are in different stadiums of development. A lot of things in the background like getting rid of old libraries and such are allready, at least partially, in gnome 2.28. other things, like the zeitgeist user interface are still behind closed curtains. people often mistake gnome 3 with the gnome shell only, but it ist just a part. gnome-shell is in the repositories, but is an outdated version. If you want to check out the current status of gnome-shell try this instructions [http://live.gnome.org/GnomeShell#head-3f60626bad6c0dbb60ecdbde36865c01a1dc1e98]("http://live.gnome.org/GnomeShell#head-3f60626bad6c0dbb60ecdbde36865c01a1dc1e98")

IIRC, there was a lot of excitement around the fact that Karmic users would be able to try Gnome 3 using a PPA. In this thread a bunch of people claimed to be testing gnome-shell using the PPA [http://ubuntuforums.org/showthread.php?t=1150357&page=30](http://ubuntuforums.org/showthread.php?t=1150357&page=30)

---

### Post by shafin on 2009-10-18
Is there any way to change the top bar color yet?

---

### Post by autocrosser on 2009-10-18
> **godhika said:**
> There is no such thing as a PPA for gnome 3. gnome 3 consist of a lot of different components wich are in different stadiums of development. A lot of things in the background like getting rid of old libraries and such are allready, at least partially, in gnome 2.28. other things, like the zeitgeist user interface are still behind closed curtains. people often mistake gnome 3 with the gnome shell only, but it ist just a part. gnome-shell is in the repositories, but is an outdated version. If you want to check out the current status of gnome-shell try this instructions [http://live.gnome.org/GnomeShell#head-3f60626bad6c0dbb60ecdbde36865c01a1dc1e98](http://live.gnome.org/GnomeShell#head-3f60626bad6c0dbb60ecdbde36865c01a1dc1e98)

More correctly--you can install Gnome3 via "gnome-shell" in Synaptic, but it is rather out-dated--there was a PPA--but it was dropped...and Gnome3 development happens at such a pace that the best way is to do a build with source files--I sure would not want to keep a PPA up to date--I'd be rebuilding the .debs every day or so......

So, goto  [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)  and start building--on a fast system it only takes 10 minutes or so after the depends are installed. :):):)

---

### Post by autocrosser on 2009-10-18
> **shafin said:**
> Is there any way to change the top bar color yet?


No, its hard-coded for now--I want to make it transparent........

---

### Post by graaant on 2009-10-18
How out of date is gnome-shell in the karmic repos?

---

### Post by 23meg on 2009-10-18
> **graaant said:**
> How out of date is gnome-shell in the karmic repos?

Not much. It's 2.28, which was released 12 days ago.

---

### Post by 23meg on 2009-10-18
> **autocrosser said:**
> More correctly--you can install Gnome3 via "gnome-shell" in Synaptic, 

> **DPic said:**
> IIRC, there was a lot of excitement around the fact that Karmic users would be able to try Gnome 3 using a PPA. 

[GNOME 3]("http://live.gnome.org/ThreePointZero/Plan") != [GNOME Shell]("http://live.gnome.org/GnomeShell").

---

### Post by DPic on 2009-10-19
> **autocrosser said:**
> More correctly--you can install Gnome3 via "gnome-shell" in Synaptic, but it is rather out-dated--there was a PPA--but it was dropped...and Gnome3 development happens at such a pace that the best way is to do a build with source files--I sure would not want to keep a PPA up to date--I'd be rebuilding the .debs every day or so......

So, goto  [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)  and start building--on a fast system it only takes 10 minutes or so after the depends are installed. :):):)

Alright well, which PPA was used for gnome-shell; was it the Ubuntu Dektop team's PPA? Will the PPA be back in time for the final release of Karmic?

---

### Post by Bou on 2009-10-19
Tried gnome-shell and it really feels much better than a few months ago. Is there a way to run it as a default session?

---

### Post by NCLI on 2009-10-19
Add an entry to Startup Applications. The command should be "gnome-shell --replace", as I'msure you know.

---

### Post by aamukahvi on 2009-10-19
Maybe gconf /desktop/gnome/applications/window_manager ?

---

### Post by autocrosser on 2009-10-19
> **DPic said:**
> Alright well, which PPA was used for gnome-shell; was it the Ubuntu Dektop team's PPA? Will the PPA be back in time for the final release of Karmic?

As I recall it was the Desktop PPA--I don't know if it will be back before Karmic release--I would guess not...23 Meg might know----???

Building from source works very well & I take a look at the commit log before I update to see if anything "interesting" has landed after my last update--seems that I update about every other day or so...It's a bit slow on my nVidia SLI setup--guess that the type of composite "hates" non-free drivers?????  I've not been able to try it with anything else(yet) to compare with--I'll install it on one of my T42's to see.....

---

### Post by Tompalaz on 2009-10-24
Is gnome-shell broken?
Can't get it to start now just blinks and then it goes back to metacity.

> tomas@Mac:~$ gnome-shell --replace
Error: glXCreateContext failed
Failed to start shell
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 265, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 138, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 75, in _get_glx_extensions
    server_glx_extensions = set(re.split("\s*,\s*", glxinfo_map['server glx extensions'].strip()))
KeyError: 'server glx extensions'
tomas@Mac:~$ Cannot register the panel shell: there is already one running.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: 0 stored in GConf key /desktop/gnome/peripherals/mouse/cursor_size is out of range 1 to 128


Edit: Got it to work. Used the nvidia 190 driver but downgraded to 185.

---

### Post by Elfy on 2009-10-25
Does anyone else have a problem opening a .ods from the Recent Document list?

Trying to open a oo file from there just results in a nautilus window opening.

I have gnome-shell installed from the repos, looked for a bug - but my search skills appear to be lacking today.

---

### Post by bluebyt on 2009-10-27
Does someone know how to uninstall Gnome-shell?

I installed it with this method:
[http://webupd8.blogspot.com/2009/09/easy-way-to-install-gnome-shell.html]("http://webupd8.blogspot.com/2009/09/easy-way-to-install-gnome-shell.html")

---

### Post by 23meg on 2009-10-27
> **bluebyt said:**
> Does someone know how to uninstall Gnome-shell?

I installed it with this method:
[http://webupd8.blogspot.com/2009/09/easy-way-to-install-gnome-shell.html]("http://webupd8.blogspot.com/2009/09/easy-way-to-install-gnome-shell.html")

Simply delete the folder(s).

---

### Post by passonno on 2009-10-27
Hope it's ok to post this here:

I kinda dig gnome-shell, with one exception:  when I use the run box(alt+f2)
the box as well as the text are so small as to be unreadable.

I have looked in every place I can think of, adjusted Nvidia settings, font sizes, etc, but no luck.

---

### Post by aymaraceci on 2009-10-28
I've tried to make a different session for gnome-shell with autoload, following this instructions &#8594; [http://www.mail-archive.com/gnome-shell-list@gnome.org/msg00023.html]("http://www.mail-archive.com/gnome-shell-list@gnome.org/msg00023.html")  

no idea what i'm doing wrong: a different session have been created, but i can't make it different one from other... both sessions are just the same: if enable gnome-shell --replace in one, it appears in the other too... any clue???

---

