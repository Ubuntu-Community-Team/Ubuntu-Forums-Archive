---
title: "New Boot Experience in Karmic"
date: 2009-06-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrewsomething on 2009-06-26
As people seem to always want the latest news on theming, ect... I thought I'd share this, a great chance to contribute to the default artwork for Karmic. Join in on the Artwork Team list.

> Discussion on Ubuntu artwork <ubuntu-art@lists.ubuntu.com>

From: Mat Tomaszewski

Hi Everyone,

As some of you may already know, Ubuntu Karmic will get a whole new,
shiny and flicker-free boot experience. Another words, the sequence of
events between switching on your computer and your desktop session will
be largely redeveloped and redesigned.

New stuff includes:
- grub 2, which will be silent, only accessible on-demand (by holding
down Shift during Bootloader initialization),
- KMS-powered experiences for the initial boot splash, password
encrypted filesystem and disk-check,
- Graphical boot splash that will be running on top of X-server, not
Usplash,
- Graphical OS Switcher available by pressing ESC during the startup
sequence, also running on top of X,
- GDM 2.

What's most important is: the boot will be *a lot* faster than in Jaunty
(sorry, no precise figures yet!). In fact, the Platform Team (Scott
James Remnant leading the efforts) aims at making the X-server start in
*no more than 3 seconds* on a reference machine (Dell Mini 9/Mini 10v).
What it means is that the standard boot sequence will not include
Usplash any longer, instead, the X-session will be started right away.
Therefore, the graphical boot splash screen will have the whole X-stack
available, including hardware acceleration...

The important news is that the look&feel of the new boot experience has
not been defined yet. Otto Greenslade (CC'd) is leading the work there,
but I'm sure he would appreciate any help. Fresh, innovative concepts is
what we're looking for (in-line with Ubuntu branding of course!), in
particular regarding the graphical boot splash (spinners, animations,
artwork, etc.).

The design guidelines can be found here:
[https://wiki.ubuntu.com/DesktopExperienceTeam/KarmicBootExperienceDesignSpec](https://wiki.ubuntu.com/DesktopExperienceTeam/KarmicBootExperienceDesignSpec)

Please poke kwwii or chaotic (that's Otto) on irc if you need any
further info!

Cheers,

Mat

---

### Post by shafin on 2009-06-26
This was posted in the ubuntu-art mailing list today, definitely some good news
> Hi Everyone,
  As some of you may already know, Ubuntu Karmic will get a whole new,  
shiny and flicker-free boot experience. Another words, the sequence of  
events between switching on your computer and your desktop session will  
be largely redeveloped and redesigned.
  New stuff includes: 
- grub 2, which will be silent, only accessible on-demand (by holding  
down Shift during Bootloader initialization), 
- KMS-powered experiences for the initial boot splash, password  
encrypted filesystem and disk-check, 
- Graphical boot splash that will be running on top of X-server, not  
Usplash, 
- Graphical OS Switcher available by pressing ESC during the startup  
sequence, also running on top of X, 
- GDM 2.
  What's most important is: the boot will be *a lot* faster than in Jaunty  
(sorry, no precise figures yet!). In fact, the Platform Team (Scott  
James Remnant leading the efforts) aims at making the X-server start in  
*no more than 3 seconds* on a reference machine (Dell Mini 9/Mini 10v).  
What it means is that the standard boot sequence will not include  
Usplash any longer, instead, the X-session will be started right away.  
Therefore, the graphical boot splash screen will have the whole X-stack  
available, including hardware acceleration...
  The important news is that the look&feel of the new boot experience has  
not been defined yet. Otto Greenslade (CC'd) is leading the work there,  
but I'm sure he would appreciate any help. Fresh, innovative concepts is  
what we're looking for (in-line with Ubuntu branding of course!), in  
particular regarding the graphical boot splash (spinners, animations,  
artwork, etc.).
  The design guidelines can be found here:  
[https://wiki.ubuntu.com/DesktopExperienceTeam/KarmicBootExperienceDesignSpec]("http://my.otherinbox.com/r?url=https%3A%2F%2Fwiki.ubuntu.com%2FDesktopExperienceTeam%2FKarmicBootExperienceDesignSpec")
  Please poke kwwii or chaotic (that's Otto) on irc if you need any  
further info!
  Cheers,
  Mat


The important point to note is that, all the things mentioned here are PROPOSED and being worked on, and there is no guarantee that it'll land in karmic, so I'd rather say we set our expectations low. That'll save us from disappointments.

---

### Post by rudenko_ruslan on 2009-06-26
[http://ubuntuforums.org/showthread.php?t=1197583](http://ubuntuforums.org/showthread.php?t=1197583) #-o

---

### Post by rudenko_ruslan on 2009-06-26
Good luck to those people, who are working on Ubuntu's look and feel, that's all I want to say :)

---

### Post by Phreaker on 2009-06-26
This is great!

---

### Post by shafin on 2009-06-26
Yeah, I guess we were at the post new thread page at the same time. 
Mods should delete this thread.

---

### Post by mc4100 on 2009-06-26
> **shafin said:**
> I'd rather say we set our expectations low. That'll save us from disappointments.

Have you tried the new GDM though, it's installable through the ubuntu-desktop PPA -- that's almost a certainty. Most of us here are already running grub2. And we're getting KMS for sure. In fact the only thing that seems to be uncertain is the graphical overlay, which, to be honest, we're only going to see for about 10 seconds.

---

### Post by artir on 2009-06-26
Awesome^Cool!

If they aim for a 10 secs boot on a Mini9, and that computer boots in 25 seconds with jaunty, my computer may boot in 5 seconds, since now it boots in 15, mwhaahaha

---

### Post by Martje_001 on 2009-06-26
[This](https://wiki.ubuntu.com/DesktopExperienceTeam/KarmicBootExperienceDesignSpec?action=AttachFile&do=get&target=boot-sequence-gdm.svg) looks very promising :).

---

### Post by MacUntu on 2009-06-26
I thought there's a (paid) art team at work? Sounds like they have no idea how things should look. :confused:

> The Bootloader should not have any visible representation

Woohoo... I really hope we'll (not) see that. If it's ugly, I don't wanna see it unless necessary.

---

### Post by froggyswamp on 2009-06-26
> Graphical boot splash that will be running on top of X-server ...I don't understand, why did nobody come up with such an implementation before, was it impossible or is it an "original" idea from Canonical?

Also, in 1st post there's mention of GDM 2 as a feature, are we using GDM1 now? Googled, found nothing that would explain it.

ps: the plans seem fantastic, hope it won't be an over-promise and under-delivery issue like with vista or like with previous theme changes.

---

### Post by pferraro on 2009-06-26
> **froggyswamp said:**
> Also, in 1st post there's mention of GDM 2 as a feature, are we using GDM1 now? Googled, found nothing that would explain it.

"GDM2" refers to the redesign of gdm that took place during the GNOME 2.22 cycle and finally released in GNOME 2.24.  For whatever reason, Ubuntu has opted to stick with the old gdm (2.20.x) for the last 2 releases.  Among other features, the new gdm implementation lets you seamlessly transition from the login screen to the desktop without any of the ugly video flickering or grey screen (w/metacity compositing) we see in jaunty.

---

### Post by froggyswamp on 2009-06-26
"GDM2" well explained, thanks.

---

### Post by chrisccoulson on 2009-06-26
> **pferraro said:**
> "GDM2" refers to the redesign of gdm that took place during the GNOME 2.22 cycle and finally released in GNOME 2.24.  For whatever reason, Ubuntu has opted to stick with the old gdm (2.20.x) for the last 2 releases.

One of the reasons is that the new GDM has no graphical configuration tool to replace the current gdm-setup (I don't know if that is still the case now), and the new GDM hasn't really offered anything useful to users compared to the old GDM (it was a complete rewrite of the old GDM, and I think some features regressed too).

However, with the next release probably being LTS, it needs to get in this cycle really otherwise it probably won't be in Ubuntu until October 2010.

---

### Post by mc4100 on 2009-06-26
> **chrisccoulson said:**
> One of the reasons is that the new GDM has no graphical configuration tool to replace the current gdm-setup (I don't know if that is still the case now)

Still the case.

---

### Post by chrisccoulson on 2009-06-26
> **mc4100 said:**
> Still the case.

Yeah, I thought that might be the case.

---

### Post by inportb on 2009-06-26
Graphical OS switcher in X?

Uh... how would this work? Isn't the OS already booting by the time X is available?

---

### Post by taavikko on 2009-06-26
> **chrisccoulson said:**
> One of the reasons is that the new GDM has no graphical configuration tool to replace the current gdm-setup (I don't know if that is still the case now), and the new GDM hasn't really offered anything useful to users compared to the old GDM (it was a complete rewrite of the old GDM, and I think some features regressed too).

However, with the next release probably being LTS, it needs to get in this cycle really otherwise it probably won't be in Ubuntu until October 2010.

+1
anyone aware that someone packaged GDM2 and throw it in a PPA ?
Tried searching a bit. Couldn't find anything...

---

### Post by salsafyren on 2009-06-26
This looks promising.

Ubuntu is starting to break away from Debian. Hopefully it will keep the stability high.

---

### Post by pferraro on 2009-06-26
> **taavikko said:**
> +1
anyone aware that someone packaged GDM2 and throw it in a PPA ?
Tried searching a bit. Couldn't find anything...

deb [http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu) karmic main

---

### Post by taavikko on 2009-06-26
> **pferraro said:**
> deb [http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu) karmic main

Oh, thanks :) Adding this to my laptop and start testing...

Done, there went "ubuntu-desktop & f-u-s-a" but no biggie :)
Transition from login to desktop is much smoother now, now just a way to implement themes...

---

### Post by autocrosser on 2009-06-26
I was using it for a week or so lately--still no way to config it & it works well enough---but the default leaves one wanting much more.....

---

### Post by pferraro on 2009-06-26
> **autocrosser said:**
> I was using it for a week or so lately--still no way to config it & it works well enough---but the default leaves one wanting much more.....

Not entirely true - look at /apps/gdm/simple-greeter in gconf-editor.

---

### Post by MacUntu on 2009-06-26
I'm sure he meant "no _easy_ way to config". ;)

---

### Post by zika on 2009-06-26
> **autocrosser said:**
> I was using it for a week or so lately--still no way to config it & it works well enough---but the default leaves one wanting much more.....
What about fast-user-switch and ubuntu-desktop that have to be removed in order to try that ppa's gdm?

---

### Post by taavikko on 2009-06-26
> **zika said:**
> What about fast-user-switch and ubuntu-desktop that have to be removed in order to try that ppa's gdm?

Most likely be refreshed when new GDM is more mature, Check for ubuntu-desktop changelogs when this is reality...

Not much harm in removing those, except option to miss out what really is karmic 9.10 like on the finish line...

---

### Post by mpt on 2009-06-26
> **salsafyren said:**
> Ubuntu is starting to break away from Debian.

Not as much as you might think. This week, there was [a joint Debian/Ubuntu sprint]("https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028453.html") discussing ways of working together to make startup faster.

---

### Post by MadsRH on 2009-06-27
This sounds fantastic! I hope some bits will land in time for Alpha 3 :-)

Looking forward to an awesome 9.10 release!!!

---

### Post by Starks on 2009-06-28
How can this be done without Plymouth?

Also, I though the xserver isn't loaded until GDM initializes.

---

### Post by Martje_001 on 2009-06-28
> Also, I though the xserver isn't loaded until GDM initializes
Now it is ;).

Grub --> nothing --> Xserver

If 'nothing' takes longer than 5 seconds it will fall back to usplash. If it doesn't you'll see an Xserver with some art. If everything is loaded the xserver starts GDM.

---

### Post by gnomeuser on 2009-06-28
wait a second.. didn't the developers just reject plymouth saying that bootsplashing interfered with boot time goals (never mind that this claim is false for plymouth).

Then they present this, which looks pretty much to reinvent the horror of rhgb (the old X powered bootsplash in Fedora and RHEL). I really do hope they remember to learn from the people who implemented that and try to avoid the problems they encountered over the years with such a solution.

It smells an awful lot like Not Invented Here syndrome. Abide a not invented here proposal with pretty flowcharts for required functionality.

---

### Post by inportb on 2009-06-28
Well we'll see how it foes, shall we?

---

