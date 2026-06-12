---
title: "Interesting features in Koala?"
date: 2009-04-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Stetzen on 2009-04-27
What are you waiting for?

From my point of view, it'll be a lot of X improvements. Intel drivers will finally reach their normal state (well... Intel people told that new stuff bringing is over, stability and performance are the priority for the next few releases), new mesa should bring gallium3d (no idea what will this mean for normal users, but sounds interesting)

New pulseaudio with lots of improvements. 

Anything else?

---

### Post by ghindo on 2009-04-27
[LIST]
[*]Better Intel X performance.
[*]PackageKit integration (hopefully!).
[*]Plymouth.
[*]New theme.
[*]Even faster boot times.
[*]Firefox 3.5 as default.
[*]VLC 1.0.
[*]Optional btrfs support.
[/LIST]

---

### Post by jmmL on 2009-04-27
[LIST]
[*]New kernel. The current rc3 already seems much "snappier" - and manages to lop about 15% off my boot time
[*]ext4 by default
[*]new nvidia drivers with vdpau and cuda support
[*]vdpau-enabled mplayer and vlc
[/LIST]

Granted, all these are available elsewhere, but karmic will bring them together.

---

### Post by autocrosser on 2009-04-27
1. Plymouth
2. Kernel mode-setting for nvidia (nvidia gets it's s-- in gear)
3. New theme
4. Testing use of Gnome 3

---

### Post by phaed on 2009-04-27
Why are people so concerned with boot time?  How often do you reboot your computer?  I reboot mine once a week, maybe.  So shaving the boot time from 40 to 20 seconds is saving me 20 seconds a week.  Even if you reboot every day, the time is negligible.  Honestly, reducing Firefox start time from 5 to <1 second would save me a lot more time throughout a week.

---

### Post by Darkshade on 2009-04-27
> **phaed said:**
> Why are people so concerned with boot time?  How often do you reboot your computer?  I reboot mine once a week, maybe.  So shaving the boot time from 40 to 20 seconds is saving me 20 seconds a week.  Even if you reboot every day, the time is negligible.  Honestly, reducing Firefox start time from 5 to <1 second would save me a lot more time throughout a week.

I have to agree with that, though I rarely restart my Firefox unless I restart my pc which, unless needed cause of some major update I don't do more than once every 10 days or so. When I used to run stable versions only I had uptimes of 3-4 months.

When you realize that your PC boots 6 times faster than your smartphone, but your smartphone opens applications twice faster - you know that something is not right :P

---

### Post by Slug71 on 2009-04-27
Packagekit
Plymouth
KMS
Firefox 3.5
Btrfs as optional
Flawless Pulseaudio.

---

### Post by ghindo on 2009-04-27
> **phaed said:**
> Why are people so concerned with boot time?  How often do you reboot your computer?  I reboot mine once a week, maybe.  So shaving the boot time from 40 to 20 seconds is saving me 20 seconds a week.  Even if you reboot every day, the time is negligible.  Honestly, reducing Firefox start time from 5 to <1 second would save me a lot more time throughout a week.What about those who use Ubuntu on laptops?  I power my laptop off and on several times a *day*.  And even if every Ubuntu user used a desktop, is it a bad thing that the kernel is being fine-tuned, or that start-up programs are being re-examined?

---

### Post by autocrosser on 2009-04-27
> **Slug71 said:**
> Packagekit
Plymouth
KMS
Firefox 3.5
Btrfs as optional
Flawless Pulseaudio.


GOOD TO See you slug!!!!  :):)

---

### Post by Slug71 on 2009-04-27
> **autocrosser said:**
> GOOD TO See you slug!!!!  :):)

:lolflag: You too man. Karmic should be fun.

---

### Post by VMC on 2009-04-27
> **phaed said:**
> Why are people so concerned with boot time?  How often do you reboot your computer?  I reboot mine once a week, maybe.  So shaving the boot time from 40 to 20 seconds is saving me 20 seconds a week.  Even if you reboot every day, the time is negligible.  Honestly, reducing Firefox start time from 5 to <1 second would save me a lot more time throughout a week.

It least 10 times a day or more! I'm one of those that turn OFF their computer when not in use. Do NOT lecture me on this subject. I've been doing this for over 20 years. I can't remember when the last time I had to replace any faulty equipment.

With that in mind, boot-up and shut-down are very important to me. Jaunty is the fastest of any Ubuntu that I've used so far. I'm expecting great things from Koala. Especially Plymouth.

---

### Post by e-rebus on 2009-04-27
> **ghindo said:**
> What about those who use Ubuntu on laptops?  I power my laptop off and on several times a *day*.  And even if every Ubuntu user used a desktop, is it a bad thing that the kernel is being fine-tuned, or that start-up programs are being re-examined?

I would say that sleep and hibernate is more important for laptop users (as well as desktops). No matter how fast the OS boots you still can't beat the time it takes to resume from sleep and have all your applications already open and in the same state as you left them. Koalas like to sleep anyway :), I'd like some improvement on that side.

---

### Post by ghindo on 2009-04-28
> **e-rebus said:**
> I would say that sleep and hibernate is more important for laptop users (as well as desktops). No matter how fast the OS boots you still can't beat the time it takes to resume from sleep and have all your applications already open and in the same state as you left them. Koalas like to sleep anyway :), I'd like some improvement on that side.I mainly prefer to turn my laptop on/off instead of suspend/hibernate because I move it around a lot, and would prefer it be fully powered off.  Regardless, I see your point and do rather appreciate suspend quite a bit :)

---

### Post by caryb on 2009-04-28
It's all well & good to say sleep/hibernate as a option, that is only ok if you resume in the same network location. I have a laptop that I connect via ethernet at work & wireless at home. Until Linux networking can detect changes on boot up reliably I can't use this functionality & have to shut down everytime I change location.


2c Cary

---

### Post by e-rebus on 2009-04-28
> **caryb said:**
> It's all well & good to say sleep/hibernate as a option, that is only ok if you resume in the same network location. I have a laptop that I connect via ethernet at work & wireless at home. Until Linux networking can detect changes on boot up reliably I can't use this functionality & have to shut down everytime I change location.


2c Cary

Yes, I guess it would be pretty inconvenient to reboot to get networking running after every sleep/hibernate. Although it does work flawlessly for me every time and I do change networks quite frequently - at least several times a day... I guess I am just lucky.

---

### Post by Triggerhapp on 2009-04-28
> **e-rebus said:**
> I would say that sleep and hibernate is more important for laptop users (as well as desktops). No matter how fast the OS boots you still can't beat the time it takes to resume from sleep and have all your applications already open and in the same state as you left them. Koalas like to sleep anyway :), I'd like some improvement on that side.

I actually find this funny, I tend to find *provided* I dont hit a disk check, its faster to boot than resume now :)

---

### Post by e-rebus on 2009-04-28
> **Triggerhapp said:**
> I actually find this funny, I tend to find *provided* I dont hit a disk check, its faster to boot than resume now :)

There's no way it can be faster for me, my laptop resumes from sleep pretty much instantly and right away I can use all the apps that I had open before suspending. Anyway, there's no sense in arguing about it :) Both startup times and improved sleep/hibernate support are important. I do on occasion turn off my laptop and the faster it boots the better. And it would be great if don't have to tweak a bunch of stuff to get suspend to work. I always have problems with bluetooth keyboard and mouse not working after sleep out of the box, so I have to fix it myself.

---

### Post by steeleyuk on 2009-04-28
Nouveau by default...

I suppose it depends on how things go with Fedora 11.

---

### Post by erkiha on 2009-04-28
> **ghindo said:**
> What about those who use Ubuntu on laptops?  I power my laptop off and on several times a *day*.  And even if every Ubuntu user used a desktop, is it a bad thing that the kernel is being fine-tuned, or that start-up programs are being re-examined?

Why do you not use suspend ?? No need to power off. I just close the lid of my laptop and it suspends automatically, wehn I open the lid it resumes in about 5 seconds.

---

### Post by steeleyuk on 2009-04-28
I have a habit of shutting down the laptop rather than suspending. Used to using desktop machines...

---

### Post by ndefontenay on 2009-04-28
> **e-rebus said:**
> There's no way it can be faster for me, my laptop resumes from sleep pretty much instantly and right away I can use all the apps that I had open before suspending.

Same here. It's pretty fast when I open the laptop. Instant I would say.

Booting time pretty fast as well. There's no pain into making booting faster anyway. I'm happy with it.

---

### Post by scheuri on 2009-04-28
I wish to have updated packages of the software with some stability.
I wish a recent kernel to be implemented.
I wish to have software developed by Ubuntu for Ubuntu to be bugfixed (network manager is not bevahing nicely all the time) and stabilised.

I do not need TONS OF new features. A very few selected are fine , but foremost I need newer packages.

I do not care about boot time, I do not care about theme (really I dont, it can be changed within seconds!), I dont care about shiny new features which might turn out to be incomplete just because they are rushed in.

But that....that is just me.
With that, I hope, regressions (like intel stuff with jaunty) can be a tiny little bit covered.

cheers
scheuri

---

### Post by myusername on 2009-04-28
1. Stability
2. Integrate Plymouth
3. New Look

I really don't like this idea of replacing synaptic with package kit. package kit feels stupid, slow, and poorly made. it's nowhere near the ease of use as synaptic. i can find everything i need in synaptic but not in packagekit

---

### Post by Gina on 2009-04-28
I'm very happy with synaptic :)

Personally, theme doesn't worry me - I'm content with what we have and put on my own wallpaper.  I appreciate though that the default theme and wallpaper may be important to promoting Ubuntu in that first impressions are important.

Apps that are fast and work well, and as expected are my top concern.

---

### Post by Tom Mann on 2009-04-28
I'm looking forward to the development of the new notifications, maybe customization? gradients? :-D

---

### Post by Simian Man on 2009-04-28
> **myusername said:**
> 
I really don't like this idea of replacing synaptic with package kit. package kit feels stupid, slow, and poorly made. it's nowhere near the ease of use as synaptic. i can find everything i need in synaptic but not in packagekit

Where and when have you tried PackageKit?  The version included in Fedora 9 was very flaky, but the version in Fedora 10 is much more usable than Synaptic in my opinion.  With development on PK still progressing quickly, it will be more than ready for KK.  Plus you get added functionality like automatic prompts to install codecs and suggested packages and so on.  It does a lot more than Synaptic does.

---

### Post by ronacc on 2009-04-28
I see packagekit more as a replacement for add/remove than synaptic , no way I can see dumping synaptic for atleast a few dev cycles yet , it may not be as cutting edge and glitzy as packagekit but it is very mature and stable and package handling is too important to trust completely to an unfinished app .

---

### Post by gnomeuser on 2009-04-28
My list of bold and vital improvements:

PackageKit by default (no, this does not mean that synaptic will die - read up on what Packagekit actually is).

Banshee as the default media player.

Plymouth.

Better integration of webmail into the platform.

PulseAudio 0.9.15 (or better), I really love that this version finally lets me configure  my 5.1 surround easily. Instead of PA hate threads I want to see users actually help fix problems by reporting problem areas in ALSA drivers. We are already much better and I plan to dedicate the next cycle to crushing every bit of pointless PA hatred and getting clarity on what the real issue is. I really hope we can make glitchfree a viable target for the majority of setups in Koala.

Webcam/VoIP support for MSN in Telepathy with a reference implemention in Empathy.

Empathy by default.

Mono 2.4 (if 2.6 is on schedule I hope we can get this but 2.4 is a nice upgrade). Ubuntu has the best Mono stack around, I hope to see it continue to improve.

I also dearly hope that in the Koala timeframe upstream will manage to get a decent beta of Moonlight 2 available, even if I have to install it via a PPA. I also hope we can get Monsoon in the repos, I would even volunteer to do the work.

Preview of some of the GNOME 3 technology like the gnome-shell would be fun but very likely more in the scope of a PPA.

BtrFS preview, with sizable warnings naturally. It is not to be expected to be stable yet but having it as a technology preview would be exciting for a sizable portion of knowledgable users.

6 months is a long time in technology, I am sure other very interesting bits of new stuff will pop up but this is my list for now. I pledge my time to making some of it happen in the way I can.

---

### Post by jerrylamos on 2009-04-28
New kernel??

I did the sources.list thing on top of a jaunty fresh install and the kernel is 2.6.28-11.

On jaunty I'm running 2.6.30-rc3 which helps the intel graphics adapter pc's like this one.

What kernel is going to be in the karmic alpha's?

Should we try 2.6.30-rc3 on karmic however is that relevant?

Thanks, Jerry

---

### Post by MacUntu on 2009-04-28
I guess I'm not the "Hooray, new features!" guy:
[LIST][*] Faster session startup.
[*] A matured PA version.
[*] Improved boot message logging: "What was that? What failed?" Maybe Upstart related?
[*] The new theme!!!1111oneelven - I'll change it anyway but I'm very curious about it.
[*] Gnome upstream merge - I'm happy to say "Bye, bye!" to most of my reported bugs. :)[/LIST]
That's it.

---

### Post by jerrylamos on 2009-04-28
> **jerrylamos said:**
> New kernel??

On jaunty I'm running 2.6.30-rc3 which helps the intel graphics adapter pc's like this one.

Should we try 2.6.30-rc3 on karmic however is that relevant?

Thanks, Jerry

Oops, I just did try rc3.  Not for early karmic on this pc.  Karmic is better without 2.6.30-rc3 and in particular "AccelMethod" "uxa" screws up on karmic while on this pc it's O.K. on jaunty.

So it's back to 2.6.28-11 with default xorg.conf.

Jerry

---

### Post by zaomaster on 2009-04-28
I personally think that the biggest area of noticeable improvement for the daily user, apart from the pulseaudio continuing melodrama, would be a streamlined gnome start up.

I'm on an older ThinkPad, and while from grub to gdm only takes 20-25sec depending on the boot, gnome takes nearly twice as long to load and I don't have many programs in my startup queue. Can it really be true that I need 1:45 to boot to a non-hard-drive-churning state when the main boot portion only takes 20sec? Huge area of improvement.

And I know that there are talks of Gnome 3.0 and all that, but I think it would be a disservice to wait for these changes to take place, for the main reason that gnome devs move like molasses. If they do end up speeding 3.0 dev then we can be sure of plenty of areas of breakage. I'm not saying it will be like KDE4.0, but the possibility is quite real.

Anyway, my two cents. First impressions are key and for the first time ubuntu user to get to the finished desktop in under 1min would be a great first impression.

---

### Post by SKLP on 2009-04-28
What I believe might be included:
* Plymouth
* Firefox 3.5
* Banshee (replacing Rhythmbox)
* Empathy (replacing Pidgin)
* Ext4 by default
* Btrfs in installer
* Mono 2.4

Wishlist( not realistic I guess... more like a long-term wishlist for Ubuntu):
* Replacing locate/find/updatedb et al with a system-wide indexer daemon that is always on ( think Apple's Spotlight). Doing this probably requires something like this:
[http://jamiemcc.livejournal.com/10814.html](http://jamiemcc.livejournal.com/10814.html)
I don't care if it happens to be Tracker, Beagle, Strigi or whatever that becomes the system-wide indexer, just make sure it works ;)
(although I like mono so I may have a slight preference for beagle... )

* Defaulting to using a swap file instead of a swap partition (dynamically resized of course) 
What would be nice as well is a separated "hiberfile" for hibernation data.

* Some changes in the default application set:
Rhythmbox -> Banshee
Firefox -> Epiphany(webkit)
Pidgin&Ekiga -> Empathy
Removal of compiz( switch to what gnome includes, possibly metacity with compositing)
Removal of gnome-games (they are clogging up my menu :P)

* The "_" on all the menu items etc in Gtk, needs to be non visible by default FOR THEY ARE UGLY.
I believe they are called "accelerators" or something.

* Switch to spatial nautilus or something better ;-) Nautilus in browser mode is not that nice :P

* Good integration with cellphones (syncing contacts etc) out of the box

* Good integration with web services (Gmail et al)

* Add a new window that will pop up when you press CTRL_ALT_DELETE. It should work anywhere when X is running ( including GDM, full screen games, you name it)
When this is accomplished, VTs can finally be disabled by default.

I'm probably missing some of the ideas I've had, but whatever

---

### Post by gnomeuser on 2009-04-28
> **steeleyuk said:**
> Nouveau by default...

I suppose it depends on how things go with Fedora 11.

I have been using nouveau on Fedora 11 since it became the default and it is really a solid driver, Ben Skeggs has done a lot of work to make it suitable to replace the nv driver along with making sure some of the attractive features like XV video playback and KMS are in good shape.

I would definitely view switching as a given feature for Koala. It is not yet ready to replace the proprietary nvidia driver for features like 3D acceleration it is a much better 2D driver than nv with wider support in both cards and features.

---

### Post by Merk42 on 2009-04-28
I understand replacing Rhythmbox with Banshee, there were a few threads about.  Why replace Pidgin with Empathy though?

---

### Post by Nerd_bloke on 2009-04-28
I'd echo a lot of the ideas mentioned already: KMS, Empathy etc.

Also, how about some more copying-the-last-Fedora-release with an implementation of delta based patches? 
Great for people running the test version with so many daily updates.

And how about the humble logoff sound? 
With new themes promised it would nice to actually hear it... been missing these past few releases, audio server is always killed before it plays.

---

### Post by go7Ul1ai on 2009-04-28
> **Merk42 said:**
> I understand replacing Rhythmbox with Banshee, there were a few threads about.  Why replace Pidgin with Empathy though?

Yeah, I love Pidgin.. and Empathy doesn't seem to let me log in to my MSN account for some reason -_- :(

---

### Post by markbuntu on 2009-04-28
Is PA 0.9.15 actually going to work glitch-free?
Is the kernel scheduling and preempt fixed for this to happen?

---

### Post by olskar on 2009-04-28
> **markbuntu said:**
> Is PA 0.9.15 actually going to work glitch-free?
Is the kernel scheduling and preempt fixed for this to happen?

[http://webapps.ubuntu.com/employment/canonical_DASE/](http://webapps.ubuntu.com/employment/canonical_DASE/) 

Looks promising ;)

---

### Post by markbuntu on 2009-04-28
> **olskar said:**
> [http://webapps.ubuntu.com/employment/canonical_DASE/](http://webapps.ubuntu.com/employment/canonical_DASE/) 

Looks promising ;)

Promising????
There are maybe 10 people who could fill that job the way they spec it. I don't think they really need someone who can do all that, just someone who understands what needs to be done and can talk with everyone else, a facilitator.

But at least they are trying, I will give them that.

---

### Post by olskar on 2009-04-28
> **markbuntu said:**
> Promising????
There are maybe 10 people who could fill that job the way they spec it. I don't think they really need someone who can do all that, just someone who understands what needs to be done and can talk with everyone else, a facilitator.

But at least they are trying, I will give them that.

Oh, I did only read the summary, that is indeed a long list of required skills :o

---

### Post by directhex on 2009-04-28
> **gnomeuser said:**
> Mono 2.4 (if 2.6 is on schedule I hope we can get this but 2.4 is a nice upgrade). Ubuntu has the best Mono stack around, I hope to see it continue to improve.

2.4 is a dead cert, and you can quote me on that

However, I hadn't seen that upstream have dropped their ridiculous 3-month release schedule - 2.6 isn't due until September. And deep into freeze is not the time to prepare, package, and test a core framework. So short version: 2.6 not happening.

It takes us at least 3 months to prepare and adequately test a new release - there's a reason 2.2 never happened (too many glaring issues early in the cycle made it seem more trouble than it was worth). And, believe it nor not, I'm STILL discovering packaging bugs in Jaunty's Mono, even though it's been tested to death for months. (can't uninstall cleanly, for example, or use monodoc-browser on a dark GTK+ theme)

---

### Post by gnomeuser on 2009-04-28
> **directhex said:**
> 2.4 is a dead cert, and you can quote me on that

However, I hadn't seen that upstream have dropped their ridiculous 3-month release schedule - 2.6 isn't due until September. And deep into freeze is not the time to prepare, package, and test a core framework. So short version: 2.6 not happening.

It takes us at least 3 months to prepare and adequately test a new release - there's a reason 2.2 never happened (too many glaring issues early in the cycle made it seem more trouble than it was worth). And, believe it nor not, I'm STILL discovering packaging bugs in Jaunty's Mono, even though it's been tested to death for months. (can't uninstall cleanly, for example, or use monodoc-browser on a dark GTK+ theme)

2.4 is plenty good for me, I am very thankful for the hard work you and the pkg-mono group do. Give me a little bit of time to get used to dpkgs syntax and I will join up to give my, ample, sparetime to the cause.

---

### Post by directhex on 2009-04-28
> **gnomeuser said:**
> 2.4 is plenty good for me, I am very thankful for the hard work you and the pkg-mono group do. Give me a little bit of time to get used to dpkgs syntax and I will join up to give my, ample, sparetime to the cause.

Status as of now (i.e. bedtime):
```
directhex@desire:~/Projects/pkg-mono$ head -1 */trunk/debian/changelog | grep urg
cli-common (0.6.2) unstable; urgency=low
gluezilla (2.2-1) UNRELEASED; urgency=low
libgdiplus (2.0-2) unstable; urgency=low
mod-mono (2.0-2) unstable; urgency=low
mono-basic (2.4-1) UNRELEASED; urgency=low
mono-debugger (2.4-1) UNRELEASED; urgency=low
monodoc (2.0-4) UNRELEASED; urgency=low
mono-tools (2.0-3) UNRELEASED; urgency=low
moon (1.0.1-3) unstable; urgency=low
xsp (2.0-3) UNRELEASED; urgency=low
```

---

### Post by myusername on 2009-04-29
> **Simian Man said:**
> Where and when have you tried PackageKit?  The version included in Fedora 9 was very flaky, but the version in Fedora 10 is much more usable than Synaptic in my opinion.  With development on PK still progressing quickly, it will be more than ready for KK.  Plus you get added functionality like automatic prompts to install codecs and suggested packages and so on.  It does a lot more than Synaptic does.

fedora 10/11. i used it. i dont like it

---

### Post by Simian Man on 2009-04-29
> **myusername said:**
> fedora 10/11. i used it. i dont like it

OK which looks more usable to you:
[[IMG]https://help.ubuntu.com/community/SynapticHowto?action=AttachFile&do=get&target=Synaptic-Package-Manager.png[/IMG]]("https://help.ubuntu.com/community/SynapticHowto?action=AttachFile&do=get&target=Synaptic-Package-Manager.png")

Or:
[[IMG]http://www.freewebs.com/simianstudios/images/pk.png[/IMG]]("http://www.freewebs.com/simianstudios/images/pk.png")

Look at the categories in Synaptic.  Amateur radio, communications?  WTF is that supposed to be?  Also why separate the categories based on the repositories (restricted, universe and multiverse)?  99% of users don't give a rat's *** what repo there packages come from and those who do can configure that in software sources.  Packagekit's categories (at least on Fedora) make a whole hell of a lot more sense.

Also PackageKit runs as a normal user application whereas Synaptic runs as root.  It is much better to run GUI apps as default user and only launch authenticated processes when it's actually needed.  For one this prevents a bug from damaging your system accidentally, secondly it makes it so the GUI uses your personal GTK theme and settings, not those of the root user - making the package manager look good for each user.  Most importantly, however, it allows all users to browse packages whether they have root access or not.

PackageKit is a huge step over Synaptic/Add-Remove in terms of usability.  It is as user-friendly as Add-Remove but is more powerful than both applications.  Here I'm only discussing usability issues.  This is in addition to the technical advantages gnomeuser has already discussed in great detail.

Also there's no reason why people can't install synaptic and use that instead of PK if they want to.  Many Fedora users still use yumex which is very similar to Synaptic.

---

### Post by Ubuntu Terrier on 2009-04-29
Personally I'm waiting for more gui tools to configurate built-in functionalities, devices and system settings, like desktop gamma (rgb), graphic tablet settings, pwm fan settings, etc which at the moment are only command-line based or require to install additional software for a gui.

---

### Post by panaut0lordv on 2009-04-29
> **Simian Man said:**
> OK which looks more usable to you:
[Removed]
Or:
[Removed]
Look at the categories in Synaptic.  Amateur radio, communications?  WTF is that supposed to be?  Also why separate the categories based on the repositories (restricted, universe and multiverse)?  99% of users don't give a rat's *** what repo there packages come from and those who do can configure that in software sources.  Packagekit's categories (at least on Fedora) make a whole hell of a lot more sense.

Also PackageKit runs as a normal user application whereas Synaptic runs as root.  It is much better to run GUI apps as default user and only launch authenticated processes when it's actually needed.  For one this prevents a bug from damaging your system accidentally, secondly it makes it so the GUI uses your personal GTK theme and settings, not those of the root user - making the package manager look good for each user.  Most importantly, however, it allows all users to browse packages whether they have root access or not.

PackageKit is a huge step over Synaptic/Add-Remove in terms of usability.  It is as user-friendly as Add-Remove but is more powerful than both applications.  Here I'm only discussing usability issues.  This is in addition to the technical advantages gnomeuser has already discussed in great detail.

Also there's no reason why people can't install synaptic and use that instead of PK if they want to.  Many Fedora users still use yumex which is very similar to Synaptic.

Lol, and what icon is libace-dev supposed to have?
I think that division for Desktop User Apps / Geek Packages Manager is PERFECT.

---

### Post by Simian Man on 2009-04-29
[QUOTE=panaut0lordv]Lol, and what icon is libace-dev supposed to have?[/quote]
It doesn't have an icon, just a generic package box like the package you can see at the bottom.  I just included ones with icons for the screenshot so you can see that many applications do have nice icons.

[QUOTE=panaut0lordv]I think that division for Desktop User Apps / Geek Packages Manager is PERFECT.[/QUOTE]

I disagree.  When I first tried Ubuntu I only found the Add/Remove Applications program.  It didn't occur to me that there would be two applications for the same thing, so I just assumed that Ubuntu's package frontend sucked and managed all of the software from the command line.

IMHO Packagekit is easy enough to use that no users should have trouble with it.

---

### Post by Nullack on 2009-04-29
Im looking forward to the Totem svn changes and gstreamer plugin changes to get DVD navigation working better.

---

### Post by coolen on 2009-04-30
> **myusername said:**
> I really don't like this idea of replacing synaptic with package kit. package kit feels stupid, slow, and poorly made. it's nowhere near the ease of use as synaptic. i can find everything i need in synaptic but not in packagekit

Who said it would be?

PackageKit cannot, and will not, replace Synaptic. Synaptic is very closely tied to APT, and reveals much of its specific functionality that PK, as a general interface for many package managers, cannot possibly implement.

It is not the goal of the project to replace tools like Synaptic, but to replace tools like Update Manager and Add/Remove, which use only the most basic functions of package management.

Remember that PackageKit is, essentially, a wrapper around APT. It does no harm for either to use PK all the time or use APT directly when needed.

---

### Post by coolen on 2009-04-30
> **lee.jarratt said:**
> Yeah, I love Pidgin.. and Empathy doesn't seem to let me log in to my MSN account for some reason -_- :(

This is why it's not included by default.

Once it is ready and usable for everyone, it will make a fine addition to the desktop.

Although personally, I'll probably replace it with eMeSeNe in the long run. Speaking of which, if eMeSeNe picked up Telepathy and, therefore, multi-protocol support (yes, it is that easy...) I'd buy everyone involved in the project a lifetime supply of beer.

---

### Post by oomingmak on 2009-04-30
> **Simian Man said:**
> When I first tried Ubuntu I only found the Add/Remove Applications program.  It didn't occur to me that there would be two applications for the same thing
Same here when I first started.

---

### Post by Jeffery Mewtamer on 2009-04-30
I have one question regarding Package Kit: is it Gnome specific or desktop agnostic? I usually do updates via Konsole, but I find a graphic package manager useful for finding new packages.

Anyways, here is a list of things  I would like to see in Karmic Koala:

- A version of VLC that does not freeze when I try to open a directory.
- for Gwenview to regain the plug-ins it lost in the transition from KDE3 to KDE4, especially 'find duplicate images'.
- Ripping to FLAC being supported in a default install of K3B
- Ark gaining support for lzh archives and being integrated with Dolphin.
- A obvious method of editing, adding, and deleting items in the K Menu.

That's about it.

---

### Post by coolen on 2009-05-01
The PackageKit graphical utilities, I believe, are written in GTK, simply because they've more experience with it. That's not to say they won't run on Gnome, but they're more at home in Gnome.

PK itself is desktop agnostic. It doesn't rely on the GUIs, they rely on it. It can be used for the command line, or new interfaces can be written for it using other toolkits.

---

### Post by steeleyuk on 2009-05-01
Theres a GUI written in Qt as well for the KDE users.

---

### Post by irrdev on 2009-05-01
I'm quite happy if we finally get a new theme. I think its an encouraging sign that Mark specifically mentioned a new look for Koala on the message boards. I particularly am optimistic about his mention of moving away from brown; let's have something more professional, brighter and modern. 

I also hope that Packagekit gets bundled along with Koala. For those who don't **really** know what Packagekit is, please understand that Synaptic can still co-exist just fine. I installed Kubuntu Jaunty on one of my computers, and am really impressed by the extra features and codec notifications. I also really appreciate the "service pack" feature; its really useful for mass package installations, and would greatly appeal to those installing software for schools, businesses, and offline computers.

---

### Post by rockin_goliath on 2009-05-01
My wishlist, in order:
[LIST]
[*]Finished Pulseaudio integration (using the new PA gui)
[*]Useable replacement for Skype (Empathy)
[*]Better and automatic power management/savings (Ubuntu's battery life on laptops should kick Windows' a**)
[*]Flawless DVD playback in Totem/Gstreamer
[*]Packagekit
[*]Integration of web apps (no, I don't consider Prism to be the answer)
[*]Tighter integration of the Ubuntu-made tools with the Gnome desktop (Policykit, Packagekit, etc)
[*]New look
[/LIST]

---

### Post by steeleyuk on 2009-05-01
> Flawless DVD playback in Totem/Gstreamer

Its half way there but still needs some work to catch up to Xine. I'd add to that and say I'd like to be able to skip PUO's... again, like Xine.

---

### Post by eluminx on 2009-05-02
With the new theme/look in mind it would be nice if they actually made a very unified look.  The thing i like about Mac OS X is the way they have a very unified GUI.  Things just flow very nicely, windows is not great at this either.  Of course there are alot of themes out there for OS's that have a unified look, but getting something as the default would be great, and it can even be brown or whatever color they choose.

Can't really mention anything else that wasn't already mentioned, it seems like Ubuntu and Linux in general is just getting better and better.  I am really glad i haven been using it for the past 7 years and have seem the changes that have been made and the ones that are soon to come.

---

### Post by Gina on 2009-05-02
> **eluminx said:**
> Can't really mention anything else that wasn't already mentioned, it seems like Ubuntu and Linux in general is just getting better and better.  I am really glad i haven been using it for the past 7 years and have seem the changes that have been made and the ones that are soon to come.I agree :)  I have looked at Linux over the years but it is only in the last 3 or 4 years that it has been easy enough to use that I stopped using Windows virtually altogether.  Linux has always appealed to me - seems to fit my mindset - I was never really happy with Windows.  Now Ubuntu is easier to use than Windows (XP) and generally so much nicer, I find.  We all know all the other benefits :lol:

Yes, Linux and Ubuntu has really improved in usability in the last few years - it just gets better and better :) :)

---

### Post by | MM | on 2009-05-02
I am just keen to see the multimedia experience get even better:

Better DVD support, widespread vdapu support, widespread upnp support in banshee, nautilus et al.

Improve the file sharing nautilus plugin.

I wuld love if Banshee gets visualisations and can support projectm stuff!

And i guess any infrustructure stuff is welcome; PA, PK, Kernel improvements won't be sniffed at by me!

---

### Post by gnomeuser on 2009-05-02
> **| MM | said:**
> I am just keen to see the multimedia experience get even better:

Better DVD support, widespread vdapu support, widespread upnp support in banshee, nautilus et al.


work is being done but certain areas should not be expected to improve. Codecs will still have problems with patents and so on, we can fix bugs but that is largely it.

> 
Improve the file sharing nautilus plugin.


what would you like to see of improvements?

> 
I wuld love if Banshee gets visualisations and can support projectm stuff!


It has already (called openVP I believe, check the banshee git there is a branch for it), awaiting integration as soon as the Now Playing window can be overloaded, aside that git master has some work to use clutter for the now playing view. You will enjoy this I promise.

> 
And i guess any infrustructure stuff is welcome; PA, PK, Kernel improvements won't be sniffed at by me!

Lots of things to get cracking at.

---

### Post by BCurtisWX on 2009-05-02
I just hope the user base doesn't flood a bug about update-manager in Koala... Man that's getting repetitive.

---

### Post by Slug71 on 2009-05-02
I wonder if LSB 4.0 will be done in time for Karmic?

---

### Post by rajeev1204 on 2009-05-03
Guys, can i install itrepid on new partition and then change sources list from itrepid to karmic to upgrade , or i need to install jaunty for the upgrade?




regards

rajeev

---

### Post by the_one(2) on 2009-05-03
Support for the ATA TRIM command for SSDs would be awesome. Really hope that will be in karmic.

---

### Post by Merk42 on 2009-05-03
> **rajeev1204 said:**
> Guys, can i install itrepid on new partition and then change sources list from itrepid to karmic to upgrade , or i need to install jaunty for the upgrade?




regards

rajeev

If you plan on doing a fresh install, why wouldn't you use Jaunty?

---

### Post by rajeev1204 on 2009-05-03
> **Merk42 said:**
> If you plan on doing a fresh install, why wouldn't you use Jaunty?

I dont have the jaunty iso.

---

### Post by Phreaker on 2009-05-03
I would like to see an improved pulseaudio &  plymouth
EDIT: possibly even grub2
Edit2: devicekit

---

### Post by Locke_99GS on 2009-05-03
I speak from the point of view of an average PC user, and I'd only hope to see a couple things (though I expect they will never happen):

_Stability_, especially for the things an average user uses, for example, gphoto2 *and* it's implementation. In Intrepid, gphoto2 was pretty much useless, requiring root to access my Kodak, which then gave file ownership to root when transfering images. Implementation is far better in Jaunty, but gphoto2 itself crashes Nautilus (as desktop) when making thumbnails. These stability issues are not limited to gphoto2, but to me is the most annoying. We must stop releasing broken software.

_Usability_. who decided BlueZ 4 was to replace 3? Not all new things are better. My bluetooth worked great in Hardy, (or Gutsy, I can't remember) then on one dist-upgrade we switched to BlueZ 4 and half of my devices no longer connect to it. There seems to be less connectivity and less functionality with the new bluetooth stack, what exactly did we gain from this switch? Again, this is not limited to bluetooth, general regressions seem to happen everywhere, and often more is lost than gained.


It seems to me that the devs put too much on their plates; with such relatively short amounts of time between releases, it's foolish to to add more; slow it down, keep it simple, and DO IT RIGHT. (I still can't believe that Intrepid was actually released with the ALSA-Network conflict at shutdown issue, which was well known during beta, and lets not forget the boondoggle of a half-assed initial implementation of PA, both caused simply by haste) I'd rather have less new features that work right, than more that fall on their face. 

Would you put a fancy new stereo in your car, if your brakes only worked half of the time?

---

### Post by billyShears on 2009-05-03
[LIST]
[*]stability: jaunty was freezing quite often here, luckily kernel 2.6.30 seems stable
[*]better pulseaudio integration: with 2.6.30 it's very unstable here and it was not perfect in jaunty
[*]hopefully new version of tracker with better integration into the desktop
[*]firefox 3.5
[*]new version of anjuta with autocompletion of class members
[*]of course speed improvements are always welcome, especially improvements of login speed.
[*]kms support in nouveau would be nice
[/LIST]

---

### Post by olskar on 2009-05-03
> **billyShears said:**
> [LIST]
[*]stability: jaunty was freezing quite often here, luckily kernel 2.6.30 seems stable
[/LIST]

Glad to hear that, IMO it was really bad to release Jaunty when it hard freezes on LOTS of compuers...

---

### Post by smbm on 2009-05-04
This looks pretty interesting:

[http://blog.fubar.dk/?p=105](http://blog.fubar.dk/?p=105)

---

### Post by olskar on 2009-05-04
> **smbm said:**
> This looks pretty interesting:

[http://blog.fubar.dk/?p=105](http://blog.fubar.dk/?p=105)

Indeed, it looks really nice

---

### Post by olskar on 2009-05-04
> **Locke_99GS said:**
> We must stop releasing broken software.


Yes, it feels like they think it's more important to release on time than it is to release something that will not crash

---

### Post by TomaszD on 2009-05-05
Personally I'm waiting for two things:

- Stable, functioning Bluetooth/PulseAudio SCO/A2DP with simple GUI to configure this. This is really irritating. Jaunty is broken, not to mention there is no GUI to set this up. It works well in Vista and Windows 7 out of the box with very intuitive GUI.

- PackageKit integration. It's high time for this technology. I think that gnome-app-install people are reluctant to drop their work and move on for the better good, but that's just me being a conspiratorial thinker ;]

Bonus grudge: I'm waiting for some actual real world use for Upstart. 9.10 will mark 3 years after the first implementation of Upstart (in 6.10), but it seems it's of absolutely no use, because it's still using SysV compatibility mode. This, my fellow Ubuntu users, should no longer be the case, but I'm becoming more and more jaded...

Of course, in fairytale land I would also be waiting for support of my TM6010-based Hybrid TV tuner (LifeView LV5H), a useful GUI OCR application and for all the Windows games to work flawlessly in Wine.

---

### Post by olskar on 2009-05-13
> **smbm said:**
> This looks pretty interesting:

[http://blog.fubar.dk/?p=105](http://blog.fubar.dk/?p=105)


Anyone knows if this has a chance to be in Karmic? It's in Fedora 11 that should be released soon so it is probably quite stable when it's time for Karmic release.

---

### Post by 23meg on 2009-05-13
> **olskar said:**
> Yes, it feels like they think it's more important to release on time than it is to release something that will not crash

[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)
[http://mdzlog.alcor.net/2008/10/29/ubuntu-quality/](http://mdzlog.alcor.net/2008/10/29/ubuntu-quality/)

---

### Post by Locke_99GS on 2009-05-13
I think everybody has a pretty good understanding of how and why the devs do things but I still stand firmly by what I mentioned in post #71 of this thread. 

While I agree that the distro must move forward with new features if it wants to continue to attract new users, (which it has seemingly been doing very well at, I might add) but it also must become more stable. I can no longer tell people that it "just works" anymore, because it doesn't.

My suggestions for the next few releases: make fewer feature advancements, and invest more time in improving stability and useability. Bug #1 will never be fixed if we continue to ignore serious useability problems with features that should be taken for granted. We need a solid release.

---

### Post by coolen on 2009-05-14
> **Locke_99GS said:**
> My suggestions for the next few releases: make fewer feature advancements, and invest more time in improving stability and useability. Bug #1 will never be fixed if we continue to ignore serious useability problems with features that should be taken for granted. We need a solid release.

Good thing we're not expecting any drastic UI and architecture shifts in the next year, then.

---

### Post by Gina on 2009-05-14
I have to agree - we need things to "just work" and OOTB! New features are no good when we keep hearing things like "my wireless isn't supported", "my graphics card isn't supported", "the sound doesn't work".  "I've tried but have given up!"

---

### Post by mixmaster on 2009-05-14
I'll go with that.  As soon as a new release comes out massive threads develop to argue about the default theme.  Themes are there to be changed - if you don't like the default then choose something you do.  The big scream this time seems to be to replace usplash with plymouth.  Given that I only reboot when the kernel changes this is of absolutely no interest or importance to me.  To be honest, I'd rather stay in text mode so I can see the install messages!

Lets fix the things which are difficult or unreliable like wireless networking and X support for more unusual configurations (dual screen and dual graphics card stuff can be a nightmare to set up).  It should work acceptably out of the box on all current and most legacy hardware.

---

### Post by taavikko on 2009-05-14
I'll wait for plymouth for flicker free login
Now if they could only snip few seconds from login to desktop...

networking should see some love, 3G modems/phones, wireless
multimedia (audio/video) improvements.

Above are just my wishes for what should be focused on.
there are tons of more, but not enough time :)

---

### Post by coolen on 2009-05-14
> **mixmaster said:**
> Lets fix the things which are difficult or unreliable like wireless networking and X support for more unusual configurations (dual screen and dual graphics card stuff can be a nightmare to set up).  It should work acceptably out of the box on all current and most legacy hardware.

You do realise that most of that work will not be done by anyone involved with Ubuntu, right?

No one's suggesting we integrate Plymouth to the exclusion of all else. X.org will continue to improve, as will Network Manager, and we'll get it all in the end. It has nothing to do with which splash we use.

Even within Ubuntu, we have different teams working on different problems. We can have people working on integrating Plymouth and other people working on getting the X server ready with still more people looking for bugs in NM.

These are all good things which will (hopefully) improve the system and make it a more attractive option. If everyone threw the bulk of their development efforts behind one problem at a time, we'd never get anywhere. If everyone worked on squashing bugs in the existing desktop, do you think we'd have Compiz enabled by default?

---

### Post by mixmaster on 2009-05-15
> **coolen said:**
> You do realise that most of that work will not be done by anyone involved with Ubuntu, right?

No one's suggesting we integrate Plymouth to the exclusion of all else. X.org will continue to improve, as will Network Manager, and we'll get it all in the end. It has nothing to do with which splash we use.

Even within Ubuntu, we have different teams working on different problems. We can have people working on integrating Plymouth and other people working on getting the X server ready with still more people looking for bugs in NM.

These are all good things which will (hopefully) improve the system and make it a more attractive option. If everyone threw the bulk of their development efforts behind one problem at a time, we'd never get anywhere. If everyone worked on squashing bugs in the existing desktop, do you think we'd have Compiz enabled by default?

Yes, I do understand that.  I was more making the point that as soon as a new release is announced it is the fluff which generates the excitement.  There are a lot of bugs which are within the control of the ubuntu team which seem to sit around forever because they are not "sexy".

As for compiz, if it is enabled by default it is just one more thing I'll have to turn off when I next re-install/upgrade.

---

### Post by coolen on 2009-05-15
Sex sells. I agree it sucks, but they have to keep people interested.

---

### Post by Merk42 on 2009-05-15
> **coolen said:**
> Sex sells. I agree it sucks, but they have to keep people interested.

This.
Hopefully Ubuntu/Linux are slowly learning that in order to succeed you have to do things that Joe User cares about more than the coder.

---

### Post by MacUntu on 2009-05-15
Can I haz boot time logging, plz?

---

### Post by fifth on 2009-05-15
> **Locke_99GS said:**
> I think everybody has a pretty good understanding of how and why the devs do things but I still stand firmly by what I mentioned in post #71 of this thread. 

While I agree that the distro must move forward with new features if it wants to continue to attract new users, (which it has seemingly been doing very well at, I might add) but it also must become more stable. I can no longer tell people that it "just works" anymore, because it doesn't.

My suggestions for the next few releases: make fewer feature advancements, and invest more time in improving stability and useability. Bug #1 will never be fixed if we continue to ignore serious useability problems with features that should be taken for granted. We need a solid release.

If you are wanting to recommend people in the Ubuntu direction why not recommend an Intrepid (or earlier LTS) release? Do you need to recommend the latest? Do the people your recommending need the latest?

If you need stable and reliable then recommend accordingly, imho.

---

### Post by Geekkit on 2009-05-15
Stability, that's all I ask.

---

### Post by shanefagan on 2009-05-15
> **Geekkit said:**
> Stability, that's all I ask.

Ah if they improve the nvidia drivers and pulse audio it should fix a lot of problems.

---

### Post by coolen on 2009-05-15
> **shanefagan said:**
> Ah if they improve the nvidia drivers and pulse audio it should fix a lot of problems.

Nvidia drivers are out of their hands (binary ones, at least. I'd love to see Nouveau get good enough to replace it ^_^).

PA is, generally, woeful in Ubuntu. I'm hoping they can fill [this](http://webapps.ubuntu.com/employment/canonical_DASE/) position, and maybe make it what it should be.

---

### Post by Gourgi on 2009-05-15
> **shanefagan said:**
> Ah if **they** improve the nvidia drivers and pulse audio it should fix a lot of problems.

if by saying **they** you mean the ubuntu developers then don't hold your breath, they can't ! it is closed source ):P

---

### Post by Locke_99GS on 2009-05-16
> **fifth said:**
> If you are wanting to recommend people in the Ubuntu direction why not recommend an Intrepid (or earlier LTS) release? Do you need to recommend the latest? Do the people your recommending need the latest?

If you need stable and reliable then recommend accordingly, imho.

Really? You really just said that? 



Me: "Hey Joe Blow, you mentioned you were sick of the viruses, malware,  constant rebooting, and incompatibilities, and that you were interested in Linux. Try Ubuntu, it's great! Just be sure you are prepared to patch, kludge, work-around, and alter the default configuration. It's as easy as that!"

Joe: "But you told me last year that Ubuntu was 'Linux for human beings', and that it 'Just works.' I'm about as Human as they come, and that doesn't sound like it will *just work* for me."

Me: "Yeah, sorry. They haven't gotten around to officially changing their mottos and slogans. If you want 'Linux for human beings' and 'Just works' you'll have to use an older version that won't be officially supprted for much longer, such as Hardy."



I don't see how that conversation would conclude to Ubuntu's benefit.

---

### Post by Merk42 on 2009-05-16
> **Locke_99GS said:**
> Really? You really just said that? 



Me: "Hey Joe Blow, you mentioned you were sick of the viruses, malware,  constant rebooting, and incompatibilities, and that you were interested in Linux. Try Ubuntu, it's great! Just be sure you are prepared to patch, kludge, work-around, and alter the default configuration. It's as easy as that!"

Joe: "But you told me last year that Ubuntu was 'Linux for human beings', and that it 'Just works.' I'm about as Human as they come, and that doesn't sound like it will *just work* for me."

Me: "Yeah, sorry. They haven't gotten around to officially changing their mottos and slogans. If you want 'Linux for human beings' and 'Just works' you'll have to use an older version that won't be officially supprted for much longer, such as Hardy."



I don't see how that conversation would conclude to Ubuntu's benefit.

Um, Ubuntu 8.04 is supported for another **two years** as of this post, which is longer than XP is supported (which is what they're most likely using).  By the time the two years is up, then they'd upgrade to the next LTS.

Otherwise you're recommending they get Jaunty? Which then you'd encourage them to upgrade in less than six months.

---

### Post by bashphoenux on 2009-05-16
> **Slug71 said:**
> Packagekit
Plymouth
KMS
Firefox 3.5
Btrfs as optional
Flawless Pulseaudio.
sounds nice :D

---

### Post by jmmL on 2009-05-16
> **MacUntu said:**
> Can I haz boot time logging, plz?

I may be missing something here; but what about bootchart? If you want to log the whole boot and log-in process you can do this with putting bootchart=nostop in the kernel options. Once you've logged in, it's then just a case of running```
sudo /etc/init.d/stop-bootchart start
```

---

### Post by markbuntu on 2009-05-16
It seems to me that Jaunty is a sort of alpha-placeholder for the next LTS and Koala will be the beta. 10.4 will be the rc and 10.4.1 will be the next actual stable LTS release. This is not such a bad thing as it will give Hardy users a very stable LTS to upgrade to and plenty of time to do so. 

A six month release cycle geared towards a 2 year LTS cycle could certainly improve things immensly. The first release after LTS, fix all LTS bugs and replace items that just missed the LTS but add minor functionality and hardware support without drastic changes and have proven stable. Second release after LTS, add new major changes introduce new/upgraded major apps. Third release after LTS, add minor changes, fix bugs, minor apps. LTS, total focus on bug fixes and stability.

The 6 month release cycle, while admirable, is certainly leaving something to be desired stability wise. The Debian people may be onto something after all...

---

### Post by MacUntu on 2009-05-16
> **jmmL said:**
> I may be missing something here; but what about bootchart? If you want to log the whole boot and log-in process you can do this with putting bootchart=nostop in the kernel options. 

Nah, I was talking about the logging of boot messages (like all the output of the init scripts that doesn't end up in syslog). I don't want to edit init scripts or use my cam to record the boot process for problem solving.

Bootlogd once worked, now doesn't or does it? I don't know... Would be nice to have a simple "dumb" logger (compared to logd) for those messages.

---

### Post by olskar on 2009-05-16
> **markbuntu said:**
> It seems to me that Jaunty is a sort of alpha-placeholder for the next LTS and Koala will be the beta. 10.4 will be the rc and 10.4.1 will be the next actual stable LTS release. This is not such a bad thing as it will give Hardy users a very stable LTS to upgrade to and plenty of time to do so. 

A six month release cycle geared towards a 2 year LTS cycle could certainly improve things immensly. The first release after LTS, fix all LTS bugs and replace items that just missed the LTS but add minor functionality and hardware support without drastic changes and have proven stable. Second release after LTS, add new major changes introduce new/upgraded major apps. Third release after LTS, add minor changes, fix bugs, minor apps. LTS, total focus on bug fixes and stability.

The 6 month release cycle, while admirable, is certainly leaving something to be desired stability wise. The Debian people may be onto something after all...

I get the same feeling. For example, they introduce notification-osd and messaging-menu in Jaunty (alpha), shape it up in Karmic (beta) and it will probably be very polished in Karmic+1 (final).

---

### Post by MacUntu on 2009-05-16
The power of evolution! :D

---

### Post by turezky on 2009-06-16
Yeah, right, a new theme! :)
This has been lingering for some time...
Hope they won't just add a new button there, and change background color there and call it "a major user experience breakthrough" again :)
Fingers crossed!

---

### Post by super.rad on 2009-06-16
> **turezky said:**
> Yeah, right, a new theme! :)
This has been lingering for some time...
Hope they won't just add a new button there, and change background color there and call it "a major user experience breakthrough" again :)
Fingers crossed!
Sorry to dissapoint but have a search through this forum, loads of posts about it already but long story short no new theme for 9.10 :p

---

### Post by zekopeko on 2009-06-16
> **olskar said:**
> I get the same feeling. For example, they introduce notification-osd and messaging-menu in Jaunty (alpha), shape it up in Karmic (beta) and it will probably be very polished in Karmic+1 (final).

Mark Shuttleworth said it best: [http://www.markshuttleworth.com/archives/288](http://www.markshuttleworth.com/archives/288)

---

### Post by kayosiii on 2009-06-17
My wishlist:

1) MOVE JACKD OUT OF UNIVERSE AND INTO UBUNTU PROPER!!! I have a firewire based soundcard that only has jackd drivers and I am sick of having to recompile packages in the main archive just so I can have sound.

2) make network manager not be such a resource hog.

3) better tested pro audio packages

---

### Post by Simian Man on 2009-06-17
> **Slug71 said:**
> Packagekit
Plymouth
KMS
Firefox 3.5
Btrfs as optional
Flawless Pulseaudio.

Sounds like Fedora 11 :).

---

### Post by Swarms on 2009-06-17
> **Simian Man said:**
> Sounds like Fedora 11 :).

Every part (maybe except Packagekit, not knowledgeable enough about that) should be in Karmic.

---

### Post by super.rad on 2009-06-17
> **Swarms said:**
> Every part (maybe except Packagekit, not knowledgeable enough about that) should be in Karmic.
Plymouth isn't going to be, not sure about optional btrfs either

---

### Post by Swarms on 2009-06-18
> **super.rad said:**
> Plymouth isn't going to be, not sure about optional btrfs either

I know, it was my personal opinion.

---

### Post by super.rad on 2009-06-18
> **Swarms said:**
> I know, it was my personal opinion.
Ah right thought you were saying that all of those are likely to be in karmic. would be nice to have them all

---

### Post by Swarms on 2009-06-18
> **super.rad said:**
> Ah right thought you were saying that all of those are likely to be in karmic. would be nice to have them all

It sure would.

---

### Post by ubudog on 2009-08-01
Faster 
Firefox 3.5 
New Human Theme
A lot of new cool stuff probably.  Can't wait:D

---

### Post by juancarlospaco on 2009-08-01
*Im using it on my netbook so...*

-Intel Graphics acceleration is nice, higher resolutions supported.
-Fast
-Better WIFI support out-of-the-box
-More 3G USB thingy support
-Cutting Edge programs on repos
-More packages on repos *(we get reaching +/-30.000 enabling all repos)*

---

### Post by arranmc182 on 2009-08-11
> **phaed said:**
> Why are people so concerned with boot time?  How often do you reboot your computer?  I reboot mine once a week, maybe.  So shaving the boot time from 40 to 20 seconds is saving me 20 seconds a week.  Even if you reboot every day, the time is negligible.  Honestly, reducing Firefox start time from 5 to <1 second would save me a lot more time throughout a week.

People are concerned with boot time for things like there note/netbooks as they dont want them on 24/7 and i would say there are people that like to shut there systems down at night like people who are switching from Windows cus we all no how slow Windows gets if it dont have a good shut down

---

### Post by markbuntu on 2009-08-11
I have a netbook and I put it in suspend where it will stay for a week at a time. I unsuspend and everything is there and working instantly.  The only time I reboot is after updates. If the effort put into reducing boot time would be put into getting suspend to work on more machines ......

Boot times are irrelevant with a working suspend mode.

---

### Post by kestal on 2009-08-11
> **markbuntu said:**
> I have a netbook and I put it in suspend where it will stay for a week at a time. I unsuspend and everything is there and working instantly.  The only time I reboot is after updates. If the effort put into reducing boot time would be put into getting suspend to work on more machines ......

Boot times are irrelevant with a working suspend mode.

A Working suspend mode would be nice, as on my laptop it basically means a restart anyway. However boot times are nice too from a marketable point of view. I mean, within the next bit we have Windows 7 coming and although I know some people here flame Windows often but it has made improvements. 

I know flocks of people who went to Ubuntu and tried it, then went back (They arent exactly a general user either, though thats a different story all together.

A quick boot time would be a concrete and solidifying improvement that Windows 7 will never be able to obtain (9.10 Alpha 3 is already quicker on boot times). Just because there are people who want better boot times and a graphically pleasing experience does not mean you have to flame them for it, or belittle it.

Part of Ubuntu's purpose (in my eyes) is to show the average joe that there is an alternative that may be equally pleasing. Seemingly so, Ubuntu is on its way. Quick boot is just one of those perks you can throw in.

Just because Ubuntu is free does not mean it should have the UI, reaction time, and backend of something that should not belong in this decade. Show some pride.

---

### Post by Locke_99GS on 2009-08-12
I have several PC's, all runing Ubuntu primarily. (or an Ubuntu derivative) I only tend to leave one of them on all the tmie, while they all get used throughout the day. Boot time is important to me.

---

### Post by joey-elijah on 2009-08-13
Boot time is important from an battery point of view. If my netbook battery dies during suspend on the way into town, i suddenly have the most awesome thing to tweet about.. i don't want to have to wait 2mins for the thing to start so, like others, boot time is important to me.

My desktop is on all the time, however for the rare times i do need to reboot - i'm not gonna turn down a super fast boot time! it means i can get back to what i was doing in quicker time. 

The gripes about quicker boot time are moot - if you need quicker boot times they're coming, if you don't - well you don't reboot anyway so what does it matter!

With the oncoming 'instant on' OSes and the 5sec boot Moblin (which is where most of this quick boot work is coming from) - Ubuntu needs to compete as well.

---

### Post by psyke83 on 2009-08-13
> **markbuntu said:**
> I have a netbook and I put it in suspend where it will stay for a week at a time. I unsuspend and everything is there and working instantly.  The only time I reboot is after updates. If the effort put into reducing boot time would be put into getting suspend to work on more machines ......

Boot times are irrelevant with a working suspend mode.

A working suspend mode is irrelevant with a dual-booting laptop.

What I don't understand is how people **don't** appreciate when optimizations and improvements are made in any area. 

P.S. Getting suspend to work for more users is more work than you would imagine. Most issues are due to buggy BIOS and ACPI implementations in many PCs and laptops, most of which are tested and certified only for Windows systems. Fixing suspend means adding quirks for buggy hardware and workarounds for obfuscated code in certain proprietary drivers.

---

### Post by dext on 2009-08-13
> **steeleyuk said:**
> Nouveau by default...

I suppose it depends on how things go with Fedora 11.

that driver has improved in Fedora12 Pre-Alpha.i still think its a release or 2 away from getting 3D on it though. i think it only supports 2D currently

ok just foundout the Nouveau driver probably wont be 3D capable till atleast Fedora14 but KMS is enabled by default in F12 now

---

### Post by coolen on 2009-08-13
Whenever boot times are discussed, I see a problem crop up that is common, but never so evident.

That is, "I do not need".

Ubuntu is aiming at a quicker boot time. Awesome! This is very good news. I turn my computer off all the time, and I'd like to be able to get back to my desktop as quick as possible.

Many dual-boot. They may boot several times a day. Reducing the boot process is a godsend for this, let's face it, majority of users.

Okay, so you don't turn off your machine. You are blessed with functional suspend capabilities. Good for you, but you must recognise that Ubuntu does not exist to meet your needs. It exists to meet the needs of the many, and the many will benefit from quicker boot times.

In short, get over yourselves.

---

### Post by taavikko on 2009-08-13
> **coolen said:**
> 
In short, get over yourselves.

Yay, many users have improved bootup times, but if the desktop usage is slow, yay. ;)

---

### Post by coolen on 2009-08-13
I'm sorry, I forgot that we can only focus on one thing at a time, and all development effort occurs within the Ubuntu camp.

---

### Post by taavikko on 2009-08-13
> **coolen said:**
> I'm sorry, I forgot that we can only focus on one thing at a time, and all development effort occurs within the Ubuntu camp.

sarcasm, not handled very well by so many.

Improved bootup-times is nice bonus, I agree on that, but that shouldn't be the main course.
Linux lacks in many features* compared to windows/osX. For really offering alternative
to them, they need to be prioritized. See bug #1.

*but offers so many extra things that windows/osX doesn't, so yay for that.

---

### Post by coolen on 2009-08-13
See the second part of that sentence.

Gnome/KDE are in better positions to bring us to feature parity with competitors, if only because those imporvements will then filter down to all the distros (not impossible if Canonical does it, but far less likely).

---

### Post by mrdiego on 2009-08-25
Reading and reading, but still I don't know exactly what's new or improved in Karmic. Boot and Empathy - okay. Improving the usability (hundert papercuts) is the other thing I know. But what more? What exactly?

The asks goes separated!!! So Ubuntu Karmic is one way and Kubuntu Karmic a totally different. So for example Ubuntu gets maybe a new theme it's not meaning the you will have a new theme in Kubuntu, too. If Kubuntu gets finally the KDE4-port for OOo it isn't a interesting "News" for Ubuntu-Users ...

What I want to say is that I really wish a Feature-Threat for KDE (next release) and one for Gnome (Ubuntu - next release) - separated. And if possible not only wishes, but correct statements and decisions about what will coming in the next release. So "I am/we are" well informed and not like always what happens to me: reading and stay in the clouds. ;)

---

### Post by GodLikeCreature on 2009-08-26
I am interested about the XORG server version Koala will use...  Does anybody know?  I think there already was quite a jump from Intrepid to Jaunty, and I hope they make it look even better this time around.

Regardless of specific features, I think these are exciting times for Ubuntu.  Incorporating GRUB2, Plymouth, ext4, faster boot times, new themes and the soon to come GNOME3, as well as other important releases...  Can´t wait!

---

### Post by cdEWoozy on 2009-08-26
> **GodLikeCreature said:**
> I am interested about the XORG server version Koala will use...  Does anybody know?  I think there already was quite a jump from Intrepid to Jaunty, and I hope they make it look even better this time around.
[https://lists.ubuntu.com/archives/ubuntu-x/2009-August/000602.html](https://lists.ubuntu.com/archives/ubuntu-x/2009-August/000602.html):
> Quick note that after discussing this with a bunch of people, the decision was finalized today that due to the lateness of xserver 1.7 we will instead be targetting 1.6.3 in Karmic.  Timo has done the merge for this already today.  Going forward we anticipate pulling patches in from the 1.7 tree as makes most sense.

---

### Post by aamukahvi on 2009-08-26
> **GodLikeCreature said:**
> I am interested about the XORG server version Koala will use...  Does anybody know?
I think it's the same version as in Jaunty because X.Org didn't meet its release schedule.

---

### Post by coolen on 2009-08-26
Karmic will be sticking with the 1.6 series of X.Org, although we'll undoubtedly be treated to a new minor release.

Also, Plymouth's been dumped. We're going to have XSplash instead, which runs atop the X server (which will be started within three seconds). It requires KMS, so I'm not sure what's happening with Nvidia cards. I'm not sure if we're planning on using Nouveau by default, or if they'll just be left behind.

It should be a good release, though. GDM's also getting an upgrade, so there's a much better list (I think it's find-as-you-type, but it's not the project MacSlow had going) and the option for compositing. As I understand it, GDM will now run in a minimal Gnome session as user gdm.

So, getting to the desktop, for those who have the right hardware and stick with the right drivers, will be pretty damn slick in Karmic at the very least.

---

### Post by GodLikeCreature on 2009-08-26
> **aamukahvi said:**
> I think it's the same version as in Jaunty because X.Org didn't meet its release schedule.

Thanks for the quick reply, guys...

Well, a bit of a longer wait for the next release, I suppose.  Nothing dramatic, tho, as Jaunty already looks terrific.

Karmic is already pointing high, but the next release (hopefully LTS) is shooting for the stars!

---

### Post by coolen on 2009-08-26
If I recall correctly, the next LTS has been put off to 10.10 due to the release of Gnome 3.0 coinciding with 10.04. At least, there was talk about it.

Whatever happens, Karmic+1 should feature MPX. Although for those wanting it sooner, there'll undoubtedly be builds in the PPAs.

---

### Post by taavikko on 2009-08-26
> **coolen said:**
> If I recall correctly, the next LTS has been put off to 10.10 due to the release of Gnome 3.0 coinciding with 10.04. At least, there was talk about it.


Yep, there's talk about of this, nothing has been decided for sure, so let's wait and see :)

---

### Post by mrdiego on 2009-08-26
I hope that the LTS comes into 10.4 - so 10.4 can be quite boring and peoples can rest, easy going and save energy. With the accumulated energy and pre-planings etc. for 10.10 "+" since a time running Gnome3 and the new KDE 4.5 the 10.10-Version will be really explosive!!! :o :p

---

### Post by coolen on 2009-08-26
If 10.04 is an LTS, I think they'll stick with an older version of Gnome.

---

### Post by jrothwell97 on 2009-08-26
> **coolen said:**
> If 10.04 is an LTS, I think they'll stick with an older version of Gnome.
I suspect they'll do what they did with Hardy, and have a GNOME 3.0 "remix" that isn't officially supported. The stable LTS version will use old GNOME.

---

### Post by aamukahvi on 2009-08-26
> **jrothwell97 said:**
> I suspect they'll do what they did with Hardy, and have a GNOME 3.0 "remix" that isn't officially supported. The stable LTS version will use old GNOME.

Why not just ship 2.30 with Metacity? Leave out the cutting edge new stuff and it'll be fine.

---

### Post by Merk42 on 2009-08-26
> **coolen said:**
> If 10.04 is an LTS, I think they'll stick with an older version of Gnome.
> **jrothwell97 said:**
> I suspect they'll do what they did with Hardy, and have a GNOME 3.0 "remix" that isn't officially supported. The stable LTS version will use old GNOME.

Why would they do that?
Back in Hardy, the default browser was Firefox 3 *beta*. Because they knew, **in the long run**, it'd be better to have Firefox 3 than 2.
Now with 10.04, wouldn't it be better **in the long run** to have GNOME 3 rather than 2? I figured that's why there was the possibility of the LTS being 10.10. In case GNOME 3 wasn't out in time to make it the default in 10.04.

---

### Post by GodLikeCreature on 2009-08-26
> **Merk42 said:**
> Why would they do that?
Back in Hardy, the default browser was Firefox 3 *beta*. Because they knew, **in the long run**, it'd be better to have Firefox 3 than 2.
Now with 10.04, wouldn't it be better **in the long run** to have GNOME 3 rather than 2? I figured that's why there was the possibility of the LTS being 10.10. In case GNOME 3 wasn't out in time to make it the default in 10.04.

Makes sense to me, but I am sure there are other technical reasons why it may not be as straight forward.  I can see updating Firefox not being as big a deal as maybe GNOME3...  

Don't know, but whatever they decide works for me... :P

---

### Post by coolen on 2009-08-26
The desktop shell is a slightly bigger deal than the web browser. A web browser can be easily replaced, and the general population knows this. They're not quite as knowledgeable about their desktop environment. Many new users probably don't even know what Gnome is.

Additionally, any Firefox beta has a huge audience testing it, filing bugs, having them squashed, etc. Gnome Shell, and other components of Gnome 3.0, have comparitively few. Even at beta (and that version was a late beta) Fx had had a more thorough rundown in the wild.

Kubuntu didn't immediately jump to KDE 4 upon release (although I seem to recall they offered a choice). Perhaps they will choose to go with Gnome 3.0, and just ship metacity/compiz instead of the shell, but it just strikes me as easier, with the removal of the panels and all, to just stick with an older version for a release cycle.

---

### Post by martini1179 on 2009-08-30
Check out [http://d0od.blogspot.com/2009/08/new-features-ubuntu-karmic-910.html](http://d0od.blogspot.com/2009/08/new-features-ubuntu-karmic-910.html) for some interesting additions to Karmic. Its looking like a lot of work is being put into making Ubuntu even easier to use: 

-- Much better Wine integration
-- Better migration assistant
-- More intuitive network manager
-- Social network/email integration with GNOME
-- Wubi migration tool that will transfer Wubi installation to its own partition!! 

All this, combined with the beginnings of an [Ubuntu Software Store]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_software_store&num=1") will make Karmic significantly more noob-friendly than Jaunty and allow me to start recommending that people make the switch to Linux without feeling bad about plopping them down into unfamiliar waters. The Wubi migration tool is especially exciting. 

Now lets just hope that all of these usability improvements are not just someone's Photoshop (or GIMP?) wet dream.

---

### Post by coolen on 2009-08-30
When I saw a reply to this thread, my first thought was "hey, I should totally link them to that post!"

That article has prompted me to upgrade to the alpha. Got a shiny new CD all ready to go, after this assignment's done.

---

### Post by conorsulli on 2009-09-01
> **ghindo said:**
> What about those who use Ubuntu on laptops?  I power my laptop off and on several times a *day*.  And even if every Ubuntu user used a desktop, is it a bad thing that the kernel is being fine-tuned, or that start-up programs are being re-examined?

Thank you.... I really freaked out thinking people were ok with having slow pc's..... Especially Laptops!!! anyone who disagrees should be shot! (kidding).

But seriously, I simply love speed.. especially in boot up. and what about all those eee-pc users! (not being one of them, but its the market where Desktop-Linux is strongest at, Its an obvious area to improve when you look at it in this light.)
:guitar:

---

### Post by Jungleboss on 2009-09-08
Does anyone know if ATA Trim support will make it into Karmic?

---

### Post by lemmyc on 2009-09-08
Boot time is very important for those of us who are trying not to waste energy and spew more CO2 into the atmosphere by leaving computers permanently on. :|

---

### Post by coolen on 2009-09-08
lemmyc, I love you.

Seriously, how could that not have come up in this discussion before? Yes, I do realise that I was among those who failed to recognise that point...

---

### Post by ugkbunb on 2009-09-09
> **phaed said:**
> Why are people so concerned with boot time?  How often do you reboot your computer?  I reboot mine once a week, maybe.  So shaving the boot time from 40 to 20 seconds is saving me 20 seconds a week.  Even if you reboot every day, the time is negligible.  Honestly, reducing Firefox start time from 5 to <1 second would save me a lot more time throughout a week.

laptop users?

---

