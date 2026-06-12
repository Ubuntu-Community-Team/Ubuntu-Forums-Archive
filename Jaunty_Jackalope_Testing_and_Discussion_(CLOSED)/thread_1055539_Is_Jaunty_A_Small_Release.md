---
title: "Is Jaunty A Small Release?"
date: 2009-01-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-01-30
Looking at upstream, I don't see what's truly compelling changes. GNOME 2.25 / 2.26 is not a significant step forward, the 2.6.29 kernel series is largely some new drivers.......The boot time stuff is being done by GNOME and RedHat/Fedora, and while its nice a few seconds isnt going to compete with Windows 7 boot times on my hardware.

Im not sure what features Ubuntu people are actually working on for Jaunty, beyond bug fixes here and there.

We still have broken gstreamer DVD playback, no gstreamer GPU acceleration, an increasingly outdated default theme and so on. We lack the security that comes from selinux in Fedora and a security audit tool like Fedora.

Seems to me this cycle is shaping up to be some bug fixes and new hardware support from upstream, and not much more.

---

### Post by MaX on 2009-01-30
Yepp... I'm looking at a faster moving target, but I won't go the rpm way... so what should I choose instead of Ubuntu?

---

### Post by jerrylamos on 2009-01-30
On this Compaq Presario boot and shutdown times are much much faster than s-l-o-w intrepid.

Do note I use Ubuntu & Xubuntu as an "ordinary user", AOL & Yahoo & Gmail email, internet news, internet news videos, YouTube videos, Office write & spreadsheet, home network file sharing, digital picture storage & editing & printing, internet health articles, internet information searching, internet shopping, on and on.

Which is to say, Compiz, get out of my hair.  No games either.  

From my standpoint Ubuntu is getting better & better but of course early Alpha bugs are a pain.  Maybe I'm a masochist.  Some of the bugs I find do get fixed, some don't, and a lot of them are worked around or solved from other people's forum entries.

Jerry

---

### Post by Nullack on 2009-01-30
Max I dont see myself leaving Ubuntu :) Blasphemy!

Jerry Im quite happy to be engaged in Alpha bugs and the testing process. My point is more about this specific release being pretty small in the overall sense from both upstream and Ubuntu.

Especially with Snow Leopard and Windows 7 on the near horizon, the competition Linux has is mounting up heavily.

---

### Post by inportb on 2009-01-30
Ah, but KDE 4.2 *is* a significant step forward.

The competition against Snow Leopard and Windows 7 is with KDE ;)

---

### Post by syko21 on 2009-01-30
The new features with snow leopard are the 64 bit architecture and the GPGPU implementation with OpenCL. Snow leopard comparison with windows 7 and KDE 4.2 are rather ridiculous.

---

### Post by Lightstar on 2009-01-31
I just want a good sound system that works
I have a bit of trouble with pulseaudio, switching to oss only takes away a few bugs to give me new ones.

I'd rather have pulseaudio, oss and alsa merge to make one good audio system instead of having to mess with everything and do some bypassing for some programs/games and etc.  it's annoying.

---

### Post by Neural oD on 2009-01-31
well hopefully the pulse audio issues will be more ironed out in jaunty

---

### Post by taavikko on 2009-01-31
> **Nullack said:**
> 

Seems to me this cycle is shaping up to be some bug fixes and new hardware support from upstream, and not much more.

AFAIK, these *.04 releases have always been mainly bugfixes.
*.10 is for introducing goodness, and then we have to stabilize them.

---

### Post by Merk42 on 2009-01-31
> **taavikko said:**
> AFAIK, these *.04 releases have always been mainly bugfixes.
*.10 is for introducing goodness, and then we have to stabilize them.

That's weird if that's the case.  You'd think the version with the higher first number would introduce things.

---

### Post by amano on 2009-01-31
> **taavikko said:**
> AFAIK, these *.04 releases have always been mainly bugfixes.
*.10 is for introducing goodness, and then we have to stabilize them.

You think wrong. Jaunty is a normal update. It happens from time to time that kernel or GNOME changes are NOT visible to the user because there is massive restructuring work done under the hood.

The new gnome version tries to drop all dependencies on outdated technologies (Project Ridley) and to replace them with more current stuff (libgnome, libgnomeui, libgnomeprint, libbonobo, gnome-vfs, liblade will be replaced). And the new linux kernel offers a rewrite of big parts of the graphics stack. The benefits of those rewrtes will be visible on the long run.

Replacing the underlying structure will make a more fine grained transition to GNOME 3 (avoiding to ship a bug-ridden monster like KDE 4).

---

### Post by plun on 2009-01-31
> **Nullack said:**
> Looking at upstream, I don't see what's truly compelling changes. GNOME 2.25 / 2.26 is not a significant step forward, the 2.6.29 kernel series is largely some new drivers.......The boot time stuff is being done by GNOME and RedHat/Fedora, and while its nice a few seconds isnt going to compete with Windows 7 boot times on my hardware.

Im not sure what features Ubuntu people are actually working on for Jaunty, beyond bug fixes here and there.

We still have broken gstreamer DVD playback, no gstreamer GPU acceleration, an increasingly outdated default theme and so on. We lack the security that comes from selinux in Fedora and a security audit tool like Fedora.

Seems to me this cycle is shaping up to be some bug fixes and new hardware support from upstream, and not much more.


Well... this is the **most important release** in Ubuntus history and a lot of work are done against non-issues, Debian-"doing nothing" because of endless discussions about religious non-important issues.

Just tragic !

Or Fedoras tragic "forbidden" list.....


Kill this thread instead with a smart GUI....;)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


And of course Gnomes "doing nothing" and a just tragic desktop....

---

### Post by taavikko on 2009-01-31
> **amano said:**
> You think wrong. Jaunty is a normal update. It happens from time to time that kernel or GNOME changes are NOT visible to the user because there is massive restructuring work done under the hood.



Yes, I'm aware of that since release cycle is linked in GNOME.
Hardy introduced gfvs, and so on...

*.10 versions are for testing more fancy stuff, 
*.04 trying to stabilize them, leading to LTS releases. every two years.

btw, I started the message with AFAIK ;)
And now finish it with same acronym, AFAIK...

---

### Post by amano on 2009-01-31
And I started my message with the clue that you are wrong. *.10 versions just package the September Gnome (Ubunto gets released on month 10=October) and *.04 versions package the GNOME from March (Ubuntu is released on month 4=April). And there is no rule that the GNOME from March is more stable and the GNOME from September is more experimental/fancier. Even with LTS releases there is no rule that they are actually more stable than normal releases. They are just supported longer than other releases which is a marketing decision and not a quality decision.

Thus AFAICT you know wrong.

---

### Post by plun on 2009-01-31
> **taavikko said:**
> 
*.10 versions are for testing more fancy stuff, 
*.04 trying to stabilize them, leading to LTS releases. every two years.


Well, I have not seeen any fancy stuff for years from Gnome.

One developer promised such a easy thing as different wallpapers on different workspaces but that probably gone with the Metacity-doctrine

This can just end in a disaster.....

Users from dists without any users dictacte Ubuntu.....;)

Well, well...     I can see Baghdad Bobs everywhere...:D

---

### Post by taavikko on 2009-01-31
> **amano said:**
> And I started my message with the clue that you are 
Thus AFAICT you know wrong.

Please stop using fancy words, my head starts to hurt :lol:

I meant more than just GNOME, in general, everything under the hood.
Every release needs to be as stable as possible..


I think were arguing about different things?

---

### Post by Eclipse. on 2009-01-31
> **taavikko said:**
> AFAIK, these *.04 releases have always been mainly bugfixes.
*.10 is for introducing goodness, and then we have to stabilize them.

I can ensure you thats not true at all.

---

### Post by Nullack on 2009-01-31
Amano while I understand the importance of GEM for example, I'll still be waiting for NVIDIA's drivers to adopt it and for compiz too and all the other parties. Which means this release wont provide a user apparent difference :) Same for flicker free boot and other examples.

Given the ecosystem seems to have all shaped up for a bug fix type release for Jaunty, my biggest user desire is to see Linux's broken audio fixed. I raised a bug on it in tests of alpha 1. Then maybe by the next release gstreamer might have working dvd playback.

---

### Post by Hobbsee on 2009-02-01
> **plun said:**
> Well, I have not seeen any fancy stuff for years from Gnome.

One developer promised such a easy thing as different wallpapers on different workspaces but that probably gone with the Metacity-doctrine

Well, gnome may not have any particularly new and shiny additions - but I expect that promise was made for KDE - and KDE 4.2 has this.  Looks nice!

---

### Post by Slug71 on 2009-02-01
Well it was pretty much stated from the beginning that Jaunty will be a 'bug fix and boot performance' release.
9.10-KK will get lots of cool new stuff though and then i'm guessing the dev cycle for 10.04 will be like Jaunty again since its gonna be an LTS release.

---

### Post by Starks on 2009-02-01
> **Merk42 said:**
> That's weird if that's the case.  You'd think the version with the higher first number would introduce things.

Yeah. That's pretty messed up.

---

### Post by Slug71 on 2009-02-01
> **Starks said:**
> Yeah. That's pretty messed up.

> **taavikko said:**
> AFAIK, these *.04 releases have always been mainly bugfixes.
*.10 is for introducing goodness, and then we have to stabilize them.

> **Merk42 said:**
> That's weird if that's the case.  You'd think the version with the higher first number would introduce things.

I dont think the version numbers determine anything.

8.04 had Pulseaudio among other new things.

I think it was just decided that Jaunty was gonna be a bug fix release because of the problems that plagued 8.04 and 8.10.
We also have another LTS coming up 2 releases from now so it really needed to be done.

Jaunty has got Ext4 which is pretty big and will have that nicely tested and solidified for 10.04-LTS.

We would have also had Plymouth had the drivers been done in time but at least there should be a PPA for it.

---

