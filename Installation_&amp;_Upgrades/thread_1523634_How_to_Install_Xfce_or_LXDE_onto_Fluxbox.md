---
title: "How to Install Xfce or LXDE onto Fluxbox?"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by Ashocka on 2010-07-03
Hi,

I installed LinuxMint Fluxbox 8 onto my mother's old computer (PIII with 1G RAM). It used to run Xbuntu, but she stopped using it and after 2 years wants to use it again (and the toolbars went missing on Xbuntu. She's in her 80's and needs a computer with a good easy desktop. I didn't read all the specs for Fluxbox and didn't realise I couldn't put app icons on the desktop or resize the toolbar (etc). This makes it a bit too difficult to use. Both my mum and I are on a limited bandwidth package, so without going through all the downloads of isos and new package installs, is it possible to just install either the Xfce or LXDE desktop on top of this install? Or a similar package?

I'd prefer to install whichever is most easy to configure the Appearance/Desktop/Toolbars, etc so that it is usable by an elderly person.

I tried installing LXDE with ```
"sudo apt-get install lxde" (and aptitude)
```, but there seems to be no option to reboot into an alternate desktop, and I'm stuck with LM Fluxbox

I am reasonably familiar/comfortable with Ubuntu editions, CLI, etc.

Thanks in advance
Geoff

---

### Post by SmokeyThePanda on 2010-07-04
Hmm..You could install GDM, then install Xfce or whatever window manager you want..I think this would work. :p

---

### Post by kerry_s on 2010-07-04
try lubuntu, it's ubuntu+lxde.
[http://lubuntu.net/blog/lubuntu-1004-now-available-download](http://lubuntu.net/blog/lubuntu-1004-now-available-download)

with lxde you can put launchers on the desktop or panel.
there's also netbook mode you might want to try, you can select it at the log in screen.

---

### Post by SmokeyThePanda on 2010-07-04
Notice, he said he just wants to install a window manager on the already existing fluxbox :p

---

### Post by kerry_s on 2010-07-04
> **SmokeyThePanda said:**
> Notice, he said he just wants to install a window manager on the already existing fluxbox :p

i know what he said, but i think he would be better off with a clean install that is already trimmed to be fast. i run lubuntu on 450mhz 256mb ram, with his specs it should be a nice fast system. to insure he gets the best possible setup it's better he start fresh instead of a system that has different wm's, different settings for each wm & what ever else there is.

it doesn't hurt to offer him a better choice.

---

### Post by Ashocka on 2010-07-04
Hi Smoky,

I'll give that a try.  Thanks.

KerryS;

I'll go lbuntu if I can't install another desktop onto of this one.  Just trying to save on bandwidth, but if push come to shove....

Thanks

---

### Post by Ashocka on 2010-07-04
I've done what smoky recommended and everything seemed fine, I set the desktop to autologin, and it did, but then it resolves to a login screen which will not login in.  It's stuck in a loop.  Any suggestions how to get out of it?

---

### Post by kerry_s on 2010-07-04
can you get to a console? (ctrl+alt+f2)
or
the rescue mode (i think you hold the shift key at boot)

---

### Post by fancypiper on 2010-07-04
Fluxbox is a windows manager and I don't think you can run two windows managers at the same time.  I believe the OP wants to turn Fluxbox into a light weight desktop environment.

You could use something like the Avant Window Navigator.  I move the fluxbox panel to the top and use the AWN as a bottom panel for launching, paging, etc.

sudo apt-get install avant-window-navigator

There are apps that will create desktop icons as well, try using the PCMan File Manager to control the desktop.

sudo apt-get install pcmanfm

---

### Post by kerry_s on 2010-07-04
> **fancypiper said:**
> Fluxbox is a windows manager and I don't think you can run two windows managers at the same time.  I believe the OP wants to turn Fluxbox into a light weight desktop environment.

You could use something like the Avant Window Navigator.  I move the fluxbox panel to the top and use the AWN as a bottom panel for launching, paging, etc.

sudo apt-get install avant-window-navigator

There are apps that will create desktop icons as well, try using the PCMan File Manager to control the desktop.

sudo apt-get install pcmanfm


first he needs to get in there, his problem right now is the log in loop.
he installed gdm & set it to auto log in.
so i'm thinking if he can get to console(ctrl+alt+f#), then he can stop gdm(sudo service gdm stop), if not then uninstalling(sudo apt-get remove --purge gdm) it in rescue mode.

any other idea how to get him out of the loop?

---

### Post by Ashocka on 2010-07-04
Thanks kerry_s

Got in there and at least fixed the main problem, which kinda reflects the gist of what fancypiper was saying about mixing distros and environments.  The problem was that I used the standard "login screen" to configure autologin and NOT SLIM login!!

I do need to clean up the startup config as it is now going through a few more things than necessary.  

I never thought of AWN, thought it might be too graphics intensive.  I have moved LXDE toolbar to the top as it would not resize at the bottom.

---

### Post by fancypiper on 2010-07-04
I don't like autologin as that bypasses your choices of the graphical session you want to run.

So you are running LXDE rather than fluxbox now?  LXDE's file manager pcmanfm handles the desktop. As I posted before, you can use this to make Fluxbox into a desktop environment.

I love the Fluxbox tabs with gkrellm running in the slit, so I run Fluxbox with the Avant Window Navigator.  I don't really need stuff cluttering up my desktop, so I end up editing the Fluxbox menu file to minimize the clicks I need to do the jobs I want.

BTW, I am 70 years old and I ditched Windows in 1999.  My oldest son is still a gamer (he just turned 40), so he still runs Windows. When I use his computer, it feels clunky and slow with lots of clicks needed to do anything.

---

### Post by Ashocka on 2010-07-05
> **fancypiper said:**
> I don't like autologin as that bypasses your choices of the graphical session you want to run.
That's what great about anything that has configurable options; you can set it up to suit yourself.  In my mums case, the less choices she has to deal with on a computer, the easier it is.  So it is my job to make her computer interface as simple as possible.

> So you are running LXDE rather than fluxbox now?  LXDE's file manager pcmanfm handles the desktop. As I posted before, you can use this to make Fluxbox into a desktop environment.
Thanks for the info, that will help me make better choices for a more easy interface for my mum.
> I love the Fluxbox tabs with gkrellm running in the slit, so I run Fluxbox with the Avant Window Navigator.  I don't really need stuff cluttering up my desktop, so I end up editing the Fluxbox menu file to minimize the clicks I need to do the jobs I want.
The Fluxbox menu is not ideal for my mum.
> 
BTW, I am 70 years old and I ditched Windows in 1999.  My oldest son is still a gamer (he just turned 40), so he still runs Windows. When I use his computer, it feels clunky and slow with lots of clicks needed to do anything.
My mum is in her 80's, she worked in a government office a long time ago with computers and office software, she used her computer a few years back for following the tennis and playing the interviews online.  These days she is really having trouble with the simplest of task, so the simpler the better.

The local Linux user group is made of geeks in their late 60's and early 70's.  They use everything from ubuntu, mint, mepis, slackware, puppy, suse.... etc, etc.  What I really like about them is you can always have a laugh about HCI.

I'm 55.  Most of my work over the last 15 years has been in web development.  I have usually had one or two linux servers running, but I only every learn enough to get the job done.  I have a long term neck injury which takes it's toll on my cognitive ability these days.

One of the great things about Linux these days is that people can offer a lot of different ways to do things.  I really like the idea of AWN on Fluxbox.  I'm going to try and do that as it may be able to be configured in a way that supplies the most easy to use interface.  My mum basically just wants a web browser, file manager, F-Spot, and Shutdown.

---

### Post by kerry_s on 2010-07-05
when i did my grand ma's computer i went with gnome at the time, cause the icons you put on the desktop can be sized to any size you want, she has bad eyes. 
now a days though i would go with 1 of the netbook launchers, there very easy to navigate, like having a giant menu right on the desktop. you might want to give those a try.

i use the 3d version of netbook-launcher. pic below.

give me a sec & i'll put a pic of the lxlauncher on lubuntu on my other computer.

---

### Post by Ashocka on 2010-07-05
Thanks for that kerry_s.  More ideas on how to customise it for those who need a KISS UI.

---

### Post by kerry_s on 2010-07-05
> **Ashocka said:**
> Thanks for that kerry_s.  More ideas on how to customise it for those who need a KISS UI.

i'm thinking why don't you try the netbook version on your system, see how it feels. if your system can't run the 3d version, then try the 2d version at the login screen. you can run it live with out installing.
[http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso)

your specs are decent. 
that other computer of mine that i'm running lubuntu is 450mhz 256mb ram, is a laptop from 1999, it's maxed hardware wise, anyways i can run the 2d version of the netbook just fine. i was thinking of putting that back on there, i have to do a alternate install then add the launcher cause of my low ram.

i'm downloading the ubuntu unity right now, want to see how thats going. ;)

---

### Post by Ashocka on 2010-07-05
Is there any way to install a package on Fluxbox so that you can customize the size of the mouse pointer?

---

### Post by fancypiper on 2010-07-05
I haven't needed a bigger curser, but I did find these:

[X and Fluxbox :: mouse theme]("http://www.damnsmalllinux.org/f/topic-3-10-9535-0.html")

[Using the Fluxbox Window Manager]("http://www.damnsmalllinux.org/f/topic-3-10-9535-0.html")

HTH

---

### Post by kerry_s on 2010-07-05
> **fancypiper said:**
> I haven't needed a bigger curser, but I did find these:

[X and Fluxbox :: mouse theme]("http://www.damnsmalllinux.org/f/topic-3-10-9535-0.html")

[Using the Fluxbox Window Manager]("http://www.damnsmalllinux.org/f/topic-3-10-9535-0.html")

HTH

+1
create the ".Xdefaults" file & put "Xcursor.size:  32 "

---

### Post by Ashocka on 2010-07-05
> **fancypiper said:**
> I haven't needed a bigger curser, but I did find these:

[X and Fluxbox :: mouse theme]("http://www.damnsmalllinux.org/f/topic-3-10-9535-0.html")

[Using the Fluxbox Window Manager]("http://www.damnsmalllinux.org/f/topic-3-10-9535-0.html")

HTH

Thanks for that:-)  Much appreciated

---

