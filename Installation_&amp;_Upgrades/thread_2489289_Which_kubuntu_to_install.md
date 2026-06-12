---
title: "Which kubuntu to install"
date: 2023-07-25
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2023-07-25
Old kubuntu's are great. New ones are full of junk, and
has less function (in  my opinion, you may not agree). 

Old ones have Kaffeine, Audacity, Avidemux, Gimp, Kile, Kate editors, 
K3B CD-writer
or you can install them from repository. 

There are panels, and I can add stuff to panels (terminal, firefox,..)
I click left bottom corner, where I can easily locate, shut-down, logout, change user, manage user, system settings,
search for anything.
..
In new ones, I'm forced to see icons which I will never use, or who knows,
I will activate chat without realizing it, and my computer will be public property, just because I don't have the last update.
.............................
After this introduction Questions:

-Can I have new kubuntu, but old everything, 
I mean old interface, old familiar programs, no junk icons, only difference will be LTS.

-What if there is no LTS. What will go wrong?
I only care about security updates.
Also wondering, who can possibly attack, just because I don;t have the last update. 
Only connection I make with internet is, firefox, and ubuntu's site via sudo terminal commands.
Can any of these be a source of attack, and what kind of attack can it be. I mean,
can a site see that I'm using an old kubuntu, and they know know how to attack it, and they just do.
Is this how it works? 
Or a download a .pdf, or ,mp3, and open them, will there be a risk?

-Can I get kaffeine, audacity, avidemux, firefox, kile, kate, office equivalent (to view some files) 
from reliable places with or without sudo command?

-Can I freely uninstall any program without affecting the rest?

-Should I use lubuntu instead?

.................
The last kubuntu I used crashed, for unknown reasons, but it was usually slow for no reason,
and there were 50 programs running by kubuntu itself.  Why would so many processes needed.
Older ones needed about 10 processes only. 

.....................
K3B is important. I'm not sure if new *ubuntu's  have k3b or allow CD-writing. 
I have two dead kubuntu computers which have CD writes.
One has grub error, for the other one I don't see the reason, because
its own monitor is dead, and external monitor not showing anything either, but 
I suspect there are minor issues I'm not aware of.
SO ONCE I RECOVER or format  those computers, I want to be able to use K3B to write to CDs.
Is there no such k3B anymore?

..........
Why are good programs being removed from repository one by one.
Hard to understand. And we are shown options, and neither works, and not sure which can be trusted.

................
ALSO WONDERING if there is a difference between old and new *ubuntu's in terms of
creating live-usb FLASH disk. 
For example in old versions, I would download ISO file, and just click on it, to start burning (after choosing the target).
Can I still do it (is I choose an old version)?
.................

Also in previous versions, I could browse the computer, via dolphin, go to the root, and from there
choose any user, and acces its files if chmod rules are like 700. 
In new versions visiting root via dolphin is not possible.
.................
Any difference in terms of full-disk encryption options?
Old ones would work smoothly.
New ones have lots of bugs (in my opinion):
-asking more than one pw, not clear which one is for encryption, and they just call it things like security key.
-forcing to connect internet during installation: why, it is like giving a new born baby to a stranger for protection.
(windows doing this and a lot more, but linux shouldn't do such things)
-new ones don't say full disk encryption; uses different words, become confusing, and after installation, 99 percent not encrypted.

I suspect, old ones are more secure, because in new ones we don't know what to do, we will easily be misled to do wrong things,
and have false sense of security.


.................

Thanks for partial answers in advance.

You won't like some comments, you can consider them as feedback.
Not everyone is happier with newer things.
Also "new" things are often required, and old ones just don't work.
For example browsers may not open sites, or "antispam" bots may block access, because
we refuse to surrender something, by using an old computer.
"security"means, for them, securing their access to our stuff. 
This is ubuntu's own site .. if it was a third party site, it could be more useful in some ways
(but worse in some ways, everyone would push their own app or plugin or .exe program)

---

### Post by yancek on 2023-07-26
>  Can I have new kubuntu, but old everything, 

Not sure that would be possible and if so, I expect very difficult to do.  The developers make changes 'they' feel people want or will like.  One possibility is to install an older version you want/like and not connect to the internet.  You could use a live  OS with or without persistence to connect to the internet or install it in a virtual machine to access the internet.  Not an ideal solution by any means.

Most attacks on home computer users are accidental, they are not after anyone in particular but are scanning thousand of computers and if they find a weakness, they access the system if they can.  Hacking of this type is mostly done with or through web browsers and it is not firefox itself that would be the problem but the fact that it is a web browser and is a major way to access other computer.  Far less likely to have a problem from the Ubuntu repositories.

Downloading a pdf or other type file is not in itself problematic but can be if it is an unknown site.  Download only from trusted/known sites.

A quick online search shows k3b is available in the latest Kubuntu.  I don't use Kubuntu so I'm not sure about the other software.

Some Ubuntu derivative iso files are too large to fit on a DVD so you may need to use a flash drive and use either the dd command from Linux or some software which was designed for this purpose.

Some Linux systems with Dolphin do not allow access by root user, others do but give you a warning when you open Dolphin as root.  Not sure how one would change this behavior in Kubuntu.  As for encryption, I have no familiarity with it so good luck.

---

### Post by guiverc on 2023-07-26
> **bjngchn said:**
> Old kubuntu's are great. New ones are full of junk

I don't know what you mean by OLD versus NEW, but I loved KDE4 where as it had a bad reputation as being *heavy* [on resources] or *bloated*. Qt4 was *heavier* than prior Qt3 thus some of complaints, thus when the library/toolkit shifted to a newer Qt5 they were somewhat careful at remaining *lean* [on resources].  To me, it lost some of what I loved about KDE Plasma.

As for inclusion of apps, I really don't care what is included by default, as I'll add what I want to the system anyway if its not included by default, so the default apps I don't worry about.

Yes when [Qt4 was removed from Debian/Ubuntu]("https://discourse.ubuntu.com/t/removing-qt-4-from-ubuntu-before-the-20-04-release/12295"), sure some apps were lost as no-one offered to upgrade them so they worked with the newer libraries, but that happens with older & unmaintained software, and I don't blame Ubuntu/Kubuntu etc for that. 

> **bjngchn said:**
> Should I use lubuntu instead?

I'll answer that only because I'm on the Lubuntu team. You're most welcome to use Lubuntu & thus the LXQt desktop if you like.

LXQt is also a Qt5 desktop (like KDE Plasma), and is *lighter* (KDE Plasma requires KF5 or KDE Frameworks 5), but if you're using KDE apps (*which will require KF5 in RAM*) the *lightness* is mostly gone anyway.  In the end it's just a *lighter* desktop that has fewer features (*allowing it to be lighter!*) but uses the same Qt5 as KDE/Kubuntu do anyway; as we share the same toolkit/libraries.

You mention K3B, even [Lubuntu has dropped that]("https://discourse.lubuntu.me/t/dropping-trojita-k3b-fcitx-from-lubuntu-jammy-22-04-seed/3044"), but even if *dropped* as a default app, you can easily install it with a simple command, and as mentioned in the post I provided, if you're *release-upgrading* from a release where it was included and don't want it to be removed; the post I linked tells you how to force it to be kept (*and not need to `apt install` it again*). 

k3b will work in Kubuntu like it does Lubuntu anyway.

> **bjngchn said:**
> 
Why are good programs being removed from repository one by one.


I already mentioned the dropping of Qt4 as it was *deprecated* upstream and thus was a security risk, which meant all apps that relied on Qt4 needed coders to update them to work with the new libraries in the years after 2012 when Qt5 was announced, ideally before 2015 when the EOL of Qt4 was announced, though Qt5 as [stated in the link I provided was **not** removed from Debian/Ubuntu until 2019]("https://discourse.ubuntu.com/t/removing-qt-4-from-ubuntu-before-the-20-04-release/12295")...  That's a decent time in my view for *volunteer *developers to step in and update the app so it can still be offered, but no-one did, thus the apps got removed. Those apps had gone 4 years without security fixes & were deemed somewhat risky.  

No-one volunteered to upgrade the apps, thus dropping them was the *safe* option.

> **bjngchn said:**
> 
Also in previous versions, I could browse the computer, via dolphin, go to the root, and from there
choose any user, and acces its files if chmod rules are like 700. 
In new versions visiting root via dolphin is not possible.


I've heard this before, and I don't know if you can get around messages like 

> Running Dolphin with sudo can cause bugs and expose you to security vulnerabilities. Instead use Dolphin normally and you will be prompted for elevated privileges when performing file operations that require them

but I don't see that as a problem anyway. Dolphin is just one file-manager, so if it won't let you do exactly what you want, just use another for some tasks.  I too have a task I do every few days where I want to use a file-manager with elevated privileges as its saves time, I just use a different file-manager than the default and the issue doesn't exist. I also like doing that, as the file-manager looks different to my default which I find helps remind me I've elevated privileges (*and thus end it asap once I've done my chore*).

---

### Post by SeijiSensei on 2023-07-26
I've moved from Kubuntu 22.04 to Debian 12 with the KDE Plasma interface. Works well so far. No snaps either. By default, software like Firefox comes in debs.

I find the "no root" restriction on Dolphin annoying, too. In those cases you can use something like Midnight Commander from the command line. I usually just use utilities like cp and rsync to move files as root.

---

### Post by DuckHook on 2023-07-26
A bit of a head&#8209;scratcher to me, to be honest.

If you don't like so many of the components of Kubuntu, then you should install the server version of Ubuntu (no GUI) then add only the apps that you like.

Start by adding the plasma desktop and go from there.

Take a look at the link in my sig: The Best 'buntu Flavour

Linux is ultra powerful and ultra flexible. That's one of its primary advantages over proprietary cast&#8209;in&#8209;iron OSes. If you don't like the standard offerings, it is not hard to spin something bespoke.

---

### Post by guiverc on 2023-07-26
> **DuckHook said:**
> 
Take a look at the link in my sig: The Best 'buntu Flavour

Linux is ultra powerful and ultra flexible. That's one of its primary advantages over proprietary cast&#8209;in&#8209;iron OSes. If you don't like the standard offerings, it is not hard to spin something bespoke.

Some great stuff exists in DuckHook's link, but please be aware the Lubuntu detail is *oudated*.

Lubuntu 18.04 LTS was the *last* release that used LXDE; LXDE still exists in Ubuntu repositories, but it's now just upstream Debian packages (*LXDE uses xfwm4 and not openbox in Debian*).

LXQt is mentioned in DuckHook's provided link too, which is  what Lubuntu has used last ten releases (*all releases post-18.04*). Lubuntu still uses openbox (LXQt like LXDE before it is WM *agnostic*, and Lubuntu chooses to ship openbox)

In the end, I really agree with the statement "*ultra powerful and ultra flexible*" and we can create any machine we like.  Today I'm using LXQt and a Lubuntu session on this box, yesterday on the same machine I used a Xfce or Xubuntu session on the same box. My install has multiple DEs installed (*in fact was very close to selecting to use GNOME/Ubuntu Desktop at login today*).

What release; that's your decision.  The *latest stable* will always have the later software, but non-LTS releases mean you need to *release-upgrade* every 6-9 months which many people hate having to do. For those that don't want to *release-upgrade* so often, stick to a LTS release & *release-upgrade* jumps to every 2-3 years (*for full support & security*) or 2-5 years (*partial support where 'universe' packages are used*) with an even longer option if you're willing to use Ubuntu Pro.

On older hardware, I often find an older kernel stack is better; with newer hardware you'll usually do better with the newest kernel stack possible. There are more kernel stack choice with LTS releases, the non-LTS always using the latest available at time of release.

---

### Post by DuckHook on 2023-07-26
> **guiverc said:**
> …the Lubuntu detail is *oudated*…

Indeed it is. You've just lit a fire under my backside to bring that thread up to date, which I've been meaning to do but keep putting off for no good reason. 18.04 is, for all intents and purposes, obsolete.

Not a small project I'm afraid. Please stay tuned…

---

### Post by VMC on 2023-07-27
> **DuckHook said:**
> Indeed it is. You've just lit a fire under my backside to bring that thread up to date, which I've been meaning to do but keep putting off for no good reason. 18.04 is, for all intents and purposes, obsolete.

Not a small project I'm afraid. **Please stay tuned…**

Yes, that'll take some doing won't it. First time I read your link. Very informative.

Regarding the topic. I tried several Kubuntu's and kept booting the desktop and filed on the panel, or it was hit and miss. So trued endeavouros-kde, and it is flawless. Recently though I noticed ist a bit heavy on the processes. I tried neon Developer Edition. That didn't work so well. Then install neon basic. Its fast, far less resources. I have had a few problems that I never experience with endeavouros.

---

### Post by DuckHook on 2023-07-27
> **VMC said:**
> Yes, that'll take some doing won't it&#8230;
I've surprised myself by updating the sticky. It took surprisingly less effort than I feared. Things should be more or less up to date now, though I suspect that the exercise will need to be repeated once 24.04 is released.

---

### Post by bjngchn on 2023-08-16
Thanks for responses.

Ubuntu was strange but Kubuntu was ok.

A few problems.


1-Root can't be browsed with dolphin.
2-Security key asked before encryption key, what is it, looks like I will never use it, who will use it then.
3-Firewall disabled by default, Why? Can't be enabled, and gives and error instead; why?
4-Can't logout. When logging out, because of "Blutooth malformed..." and "TRACEPC"  ... things
computer can't logout, and forces me to shut down by on=off button, 
because otherwise I will never be able to use the computer again.
And then eventually partitions will be damaged enough.
The same happens after typing encryption key, but computer doesn't freeze.
(initially such TRACEPC, BLUTOOTH MALFORMED,.. nonsense didn't exist, it
was created out of nothing after a few logouts and shutdowns)

(the bigger the  number, the bigger the problem , in this post)

Ultra new computer, ultra new kubuntu, still such things happening. 
If things start this way, how can they become normal eventually,..everything will get worse and worse.
And I suspect, since I block many things, some entities become unhappy, because then we are not slaves anymore.
via hardware or software,.. someone wants to watch everything.


BLUTOOTH PREFERENCES (and other settings) MUST HAVE NOTIHING TO DO WITH WHETHER I CAN USE THIS COMPUTER OR NOT.
And of course, when disabled, this must be better for health, and computer security, logically, but
logic doesn't apply in this strange world (run by who?)

---

### Post by SeijiSensei on 2023-08-16
If you want to browse as root, use a terminal. You can install text-only file managers like Midnight Commander, or just use things like cp and rsync to manage files from the command prompt. That's my usual method.

---

### Post by guiverc on 2023-08-16
I have a task I perform about 12 days a month that is just easier with a file-manager with elevated (root) privileges. I just do that task in `caja`  ... regardless of whatever desktop I'm using. Even if I'm using LXQt & its default `pcmanfm-qt` will allow it (*it just gives a red vivid reminder that what you're doing is dangerous*), or if I'm using KDE Plasma where `dolphin` doesn't allow it, I don't care as I'll use `caja`. 

All Ubuntu systems of the same release are all running the same base system, so if it works in Ubuntu 22.04 LTS Desktop, it'll be the same for all *flavors* which include Kubuntu 22.04 LTS. The only differences are the default kernel stack installed (*some flavors have different install defaults set by media used in contrast to Ubuntu Desktop* *which defaults to HWE for 22.04 & later*) & packages installed (*they all differ here as they're all built using unique seeds, ie. files of what to include on the ISO**; eg. [here's Kubuntu's lunar or 23.04 seed]("https://ubuntu-archive-team.ubuntu.com/seeds/kubuntu.lunar/desktop")**; but all packages come from the same repositories for all*).

Having a firewall enabled achieves nothing but a slower machine on a GNU/Linux system, as the default is all network traffic is ignored EXCEPT if you start a program to listen/react to it. Why would you want a *firewall* to *drop* network traffic that is ignored anyway? You can use a firewall if you're opening up loads of network tasks & thus changing the default (*to be more like windows*) and thus will benefit from it; it's your choice, just not needed as only costs resources.

I can't comment on your other details, as they're vague & unclear, at least to me sorry.

---

