---
title: "Services-admin is gone... introducing ServiceManager"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by yota on 2009-11-24
Upgrading to Karmic brought lot of new stuff to our desktop, but unfortunately also left something behind...

One thing that bugged me is that I was missing a mean (like service-admin) to manage services through the GUI and since I wanted to play a bit with glade+gtkpython and, I spent a couple of days to make an upstart graphical front-end "ServiceManager" which can be found at this link:

**NEW!** [servicemanager_0.3.deb]("http://opensystems.ath.cx/blog/download/software/linux/servicemanager_0.3.deb")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=137422&stc=1&d=1259053758[/IMG]

The program lets you list, stop start and restart all the services and (if available) provides a description of them. SysV services can also be enabled/disabled at boot.
After selecting a service possible actions on it will be unlocked on the big buttons on the top bar. The checkbox on the "enabled" column can be used to choose if a service should be autostarted at boot time. 
Since at the present time there's no mean in upstart to control if a service should be enabled or not, and considered that services already migrated to upstart are mostly system-critical I've decided not to implement a way to disable upstart services for now. 

The deb can be installed on all architecture and places an homonym icon under the administration menu. For the curious the program is made of two files which can be found under /opt/servicemanager: "mainwindow.glade" is a glade3 project and "servicemanager.py" is the program itself.

If I'll see some interest I can try to extend functionality (as far as the underlying tools like service, initctl etc. allow). Let me know what you think!

**BIG DISCLAIMER:** It's my first work on python, it's something made just to suite my needs, it's simple and stupid, but if it fills an hole I'm happy to share.

For references on the problem see:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/433701](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/433701) (outdated version posted there)
[http://ubuntuforums.org/showthread.php?t=1294610](http://ubuntuforums.org/showthread.php?t=1294610)
[http://ubuntuforums.org/showthread.php?t=1319122](http://ubuntuforums.org/showthread.php?t=1319122)

I've leeched some ideas from Stebalien's program (ref: [http://gtk-apps.org/content/show.php?content=114727](http://gtk-apps.org/content/show.php?content=114727)) which was complementary to my 0.1 version, my intention is to deliver both start-on-boot and live stop/start/restart control in one tool.

Other than this work and the one from Stebalien I've just mentioned I'm not aware of other efforts to bring such a functionality to Karmic, if you do please tell me.

---

### Post by sandman74 on 2009-11-24
Very nice, Works great!! I appreciate it.

---

### Post by nalimilan on 2009-11-25
Well, I'd rather you helped us making services-admin rock so that we can bring it back in Lucid. It would benefit to all Linux distributions (and FreeBSD), since it's part of GNOME.

services-admin is using PolicyKit, which allows for a much nicer way of managing authorizations than a simple gksudo call, and is now the standard way on Linux. That will require you more work, which could have been spent in improving existing tools.

Good luck, though!

---

### Post by yota on 2009-11-25
Hi nalimilan,

yours are good points, really, but as I said this was something I did just to experiment a bit of python.
It was not something I made with a plan in mind, I just saw that a feature was missing (without even knowing it was part of gnome) and I tried to create something to replace it on my environment.

Once finished it didn't seemed that bad after all and I thought it was worth sharing.
Maybe you can look at it as a quick and dirty replacement for services-admin until a new big-and-better version is ready, which has the non-trivial plus of being available today.

Anyway now that you make me reason a bit on the matter, in effect there are some aspects in which I didn't like services-admin that much.
For instance there was no live start/stop/restart, just the checkbox to select if the service has to be started at boot and moreover the service list and descriptions seemed hard-coded in the program rather that dynamically gathered (so that not all services were listed).

Maybe, better if someone agrees, I'd be glad to forward those observation to the services-admin developers... any pointers?

---

### Post by nalimilan on 2009-11-25
Yeah, I understand your intentions, no problem with that, that can always be useful. I was just replying to your proposal on the services-admin bug report.

I perfectly see the limitations in services-admin you complain about, but we're a pair of developers working on their free time, so we don't lack of ideas to improve it, but of time. That's why I was talking about work duplication.

At least, I'd like to get rid of the static list of services by the next release. But the problem is that services we don't know about beforehand won't have they descriptions translated, and I can't see any solution to this.

---

### Post by yota on 2009-11-26
Mhhh... I was asking pointers to services-admin developers without realizing I was already speaking to one of them! How insigthful am I :-)

Speaking about descriptions translations, aren't they a way to heavy burden to be carried on by the administration tool?
IMHO the descriptions (and their translations) should be contained within the upstart job definitions, like:
```

# mountall - Mount filesystems on boot
#
# This helper mounts filesystems in the correct order as the devices
# and mountpoints become available.

description	"Mount filesystems on boot"
description[it] "Monta i filesystem all'avvio del sistema"
description[es] ...
...

```
This is exactly what happens with .desktop files and insures that also custom programs installed by the user (also if out of official repositories, like skype and acrobat reader) get correcly listed in the menu with their translation (where available).

Since the service administration tool can't possibly be aware of every single service existing in the world and contain within itself all translations probably shouldn't try to handle the problem all on its own.

This is especially true if the development resources are limited: better focus on problems that can be solved easily than on ones which are unsolvable.

Anyway if some help is needed in the development of services-admin for Lucid I'd be glad to contribute (obviously if I'm able), if that's welcome, how can I?

---

### Post by nalimilan on 2009-11-26
Sure, translations would ideally be carried by the scripts themselves, but ATM there's no way to do so. I had already thought of a .desktop file-like translation, but that would make the scripts really hard to read and edit manually. Maybe we could actually ship a .desktop file in some place with all the data needed (even an icon if wanted). That is a request that should be reported to the Upstart developer, e.g. via a bug in Launchpad.

Glad to hear you want to help us! It depends on whether you prefer C or perl coding (I know, it's choosing between two evils :-p). services-admin is in C and you can get it using
git clone git://git.gnome.org/gnome-system-tools
It's in src/services/.
(If you need documentation about git, see [http://live.gnome.org/Git/Developers](http://live.gnome.org/Git/Developers))

But services-admin mostly needs a nice support for Upstart jobs, which is managed on the privileged backend side, the system-tools-backends. Get them using
git clone git://anongit.freedesktop.org/system-tools-backends
the relevant code is in Init/. It's working with "platforms", meaning that they behave completely differently depending on the distribution. For Debian/Ubuntu, we're now using the "upstart" scheme, which currently is only traditional SystemV support plus detection of Upstart jobs so that we don't show them at all (since we don't know how to manage them).

But it may be better to discuss that on our list, to avoid cluttering your thread here. It's at
[http://mail.gnome.org/mailman/listinfo/system-tools-list](http://mail.gnome.org/mailman/listinfo/system-tools-list)

---

### Post by yota on 2009-12-10
Updated to version 0.3, the news are:
[LIST][*]Fixed icon on KDE[*]The program can be launched from CLI for debug (verbose messages on standard output)[*]Nicer, hopefully more readable, code[*]Implemented sort of plugin mechanics to make easier porting to different platform
[/LIST]
There had been more than 100 downloads in 2 weeks, not that much, but still some interest has been shown even if here just one user took some time to thank.

Nonetheless I guess that no complain means that the tool works...

---

### Post by zanglang on 2009-12-26
The link for version 0.3 is incorrect, by the way. ;)
Any chance of packaging it on a PPA so that we could get instantly notified about new releases?

---

### Post by billsdesk on 2009-12-29
The switch to Upstart is one thing, the lack of a management utility is quite another. Your program worked fine, and solved my immediate problem.

---

### Post by yota on 2010-01-11
> **zanglang said:**
> The link for version 0.3 is incorrect, by the way. ;)
Any chance of packaging it on a PPA so that we could get instantly notified about new releases?

Hi zanglang, sorry for the "holidays delay" and thank you, link fixed.

About the PPA I've to say that **ideally** (and time permitting) I'd like more to help fixing the stock gnome services-admin and limit the development of servicemanager to bug fixes.

But if there's enough interest in this specific tool, and specifically if there's the opinion that it delivers some advantage, a PPA can surely be considered: I'd like to hear some opinions on the subject.

---

### Post by ensefik on 2010-02-06
Thank you for the work that you have done here, it is just what I needed so I could stop or start application services like Mysql - where you cannot log into the GUI admin tool if MySQL isn't already started.:D

---

### Post by joelgsf on 2010-05-31
Nice initiative yota! As I switched from 9.04 straight to 10.04, without trying Ubuntu 9.10, only now I was suprised is this fact. Waht is even more surprising is that I couldn't find an official replacement for services-admin. If the intention is to make Ubuntu easier to use with each new release, I can't understand why it has ben left aside such an useful tool.
I will be trying your solution.
Thank you.

Cheers,

   Joel Guilherme

---

### Post by sistematico on 2010-06-25
Thank you yota!!!

---

### Post by MestreLion on 2010-12-30
Absolutely unbelievable that until now theres no GUI for start/stop services and boot autostart enable/disable...

Ubuntu sistematically switches to "new technologies" waaaaay too early. Empathy, Grub2, and now Upstart. I see a pattern here:

- New tool has a "more modern fundation" that has very promising features for the future
- But, nowadays, it still lack all those features
- And lack a decent (or any) GUI
- And theyre no longer compatible with all the tools and guis made for the previous tech
- We, users, end up doing loooong research and editing several config files by hand, like 10 years ago

So whats supposed to be a "new and exciting and promising technology" end up being a painful experience editing text files and doing all sorts of hacking after hours lost researching web and foruns, just the kind of stuff Linux won its fame of "geek-only OS" and Ubuntu has struggled so hard to change.

Come on! Upstart has NO was to easly disable autostart of a service? Not even CLI?
Grub2 has NO way to select/disable a given OS? Or to rename it? Or even to add a damn separator in that ugly menu? So why swtich to them?? Were there ANY improvement at all to the users??

Sorry for the long post, but im really getting annoyed of wasting so much time having to dig in config files for every simple stuff. Im tired, ready to give up and switch back to some other OS...

---

### Post by MestreLion on 2010-12-30
That said, your ServiceManager is simply GREAT!

MUCH better than bum, ebox or Webmin.

1 - Telling wheter a service is SysV or Upstart is awesome! Upstart services are very accurate on their start/stop status, but you cant disable, SysV, on the other hand, your can easily enable/disable, but their running status is not accurate. Knowing which services uses each method give a very nice control and undestanding of whats going on...

2 - Start/Stop/Restart/Enable/Disable all in 1 simple, easy screen. Great!

3 - Much better than the currently officially-provided tool in ubuntu: NONE

Some questions/remarks:

- Were are you getting the descriptions from? is there any standard to read those from conf files?

- How are you handling services that are both Upstart and also (symlinked to) SysV (or vice-versa) ?

- How are you detecting SysV current status? Tomcat6 (from Ubuntu repo) is always said to be "stopped", but sudo service tomcat6 status says its active. (and it is)

- I luved the icon :D

- Isnt sudo (or gksu) required to run this? How come it didnt ask me for a password? How did u manage to do all this without root privileges?

- How does it disable SysV services? Is there any "standard" way for this?

Any chance for a PPA or, evn better, official repo/dist ? It is reliable, simple, lists all services, has no hardcode, and its Upstart compatible. And it doesnt allow you to disable Upstart services simply because Upstart provides no way for it. So, is there any requirement you dont fulfill?

Cheers!

---

### Post by sisco311 on 2010-12-30
> **MestreLion said:**
> 
3 - Much better than the currently officially-provided tool in ubuntu: **jobs-admin (universe repo)**


fixed :)

---

### Post by lazyron on 2011-01-05
Thanks yota :)

---

### Post by yota on 2011-02-03
> **MestreLion said:**
> That said, your ServiceManager is simply GREAT!

MUCH better than bum, ebox or Webmin.


Thank you (and anyone else that cared to write here). It's always heart-warming receiving positive feedback.

> 
SysV, on the other hand, your can easily enable/disable, but their running status is not accurate


Yes, you are right... the sysV running status is not reliable.
I'm using "service --status-all" first and trying even with "/etc/init.d/*servicename* status", but still if a service responds with some cryptic sentence like "I'm doing what you told me, Sir!" instead of "running" or "started" I can't correctly parse the output.
Mostly the problem is coming from the underneath tools: the service command is not reliable on statuses and /etc/init.d scripts are not standardized.

> 
- Were are you getting the descriptions from? is there any standard to read those from conf files?

The program is FOSS so feel free to look at the code in /opt/servicemanager for all details.
In short the upstart .conf files have a "description" line and most init.d script a "# Description:"

> 
- Isnt sudo (or gksu) required to run this? How come it didnt ask me for a password? How did u manage to do all this without root privileges?

I'm indeed using gksudo, which has a (5 minutes I think) grace period between authentications. If you made a successful auth you'll need not re-enter the password for a limited amount of time.
> 
- How does it disable SysV services? Is there any "standard" way for this?

I'm using update-rc.d command, which, I believe, is a Debian standard.

> 
Any chance for a PPA or, evn better, official repo/dist ? 


Considered the few releases, and the limited time I can spend on this work I'm not considering a PPA at this time. Anyway since, as already said, this is FOSS anyone can contribute if finds this tool interesting.

---

