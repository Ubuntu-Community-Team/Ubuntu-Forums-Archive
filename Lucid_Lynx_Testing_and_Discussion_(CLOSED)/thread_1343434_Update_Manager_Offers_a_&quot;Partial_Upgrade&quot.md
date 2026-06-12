---
title: "Update Manager Offers a &quot;Partial Upgrade&quot;? Read This."
date: 2009-12-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-12-01
During the development cycle of Ubuntu 9.10, we've been flooded with threads asking for assistance related to issues caused by careless usage of the "Partial Upgrade" feature of Update Manager, which hinted to a poor understanding of package management and the way updates happen in the development branch. 

In an effort to help with this situation, this document aims to clarify what a "Partial Upgrade" is, and why, **in most cases, you'll want to avoid it**.


[SIZE="4"]**Summary**[/SIZE]
[SIZE="1"]or **"I don't really care if I keep messing things up and wasting my and others' time with preventable problems, and you have 30 seconds to convince me to care!"**[/SIZE]

If you use Update Manager to upgrade your packages, and it offers to do a "Partial Upgrade", do not accept it without thoroughly checking what packages it offers to remove, upgrade and install. If you do, you will most likely end up removing packages that shouldn't be removed, and waste time and effort repairing your testing installation and asking for assistance. 

Most "Partial Upgrade" situations occur due to package archive inconsistencies, which will typically be resolved within a few hours. If your package manager is confused, and so are you, **simply wait** and hold off the updates until things settle down. 


[SIZE="4"]**Short Version**[/SIZE]
[SIZE="1"]or **"Hmm, so I shouldn't blindly do "Partial Upgrade"s and dist-upgrade? I didn't know that..."**[/SIZE]

Due to the fact that uploads to the repositories of the active development branch are asynchronous and uncoordinated, dependencies of certain packages may arrive later than the dependent package. This causes package management tools such as Update Manager, which are mainly meant to be used with stable releases of Ubuntu where the package archive is always consistent, to interpret the situation as requiring a dist-upgrade to install new packages and/or repair packages in a "reqreinst" (requires reinstallation) state. What Update Manager performs when doing a "Partial Upgrade" is a dist-upgrade.

When testing development releases, most of the time, a "Partial Upgrade" is undesired. The situations where it's needed are limited to new packages obsoleting old ones (as in the case of the software-center package replacing software-store) and package removals from the archive.

Do not assume that since you're running a development release, a "Partial Upgrade" is necessarily warranted.


**[SIZE="4"]Long Version[/SIZE]**
[SIZE="1"]or **"I want to be a better tester! I care! Tell me more!"**[/SIZE]

In its normal operating mode, Update Manager will not offer to remove packages. This is the equivalent of "apt-get upgrade"ing your existing packages. In "Partial Upgrade" mode, it can. Sometimes, the removal is warranted, such as when a package is obsoloted by a new one. Other times, it will not be, and a "Partial Upgrade" can offer to remove important packages due to missing dependencies.

Now, the key question: 

"**How do I know whether a package is actually meant to be replaced or removed?**"

There's more than one way:

[list][*] Check the changelog of the package in question. You can do this via "Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or by going to [packages.ubuntu.com]("http://packages.ubuntu.com") and clicking "Ubuntu changelog" for the package you're curious about, or visiting the URL 

[https://launchpad.net/ubuntu/+source/](https://launchpad.net/ubuntu/+source/)[COLOR="DarkRed"]package_name[/COLOR]/+changelog

where [COLOR="DarkRed"]package_name[/COLOR] is the name of the source package you're curious about. The most recent changelog entry will indicate the reason for the removal or replacement, if there is one.


[*] Keep an eye on the changes mailing list or RSS feed for the active development release. The current ones are the [lucid-changes mailing list]("https://lists.ubuntu.com/mailman/listinfo/Lucid-changes"), and [its RSS counterpart]("http://feeds.ubuntu-nl.org/LucidChanges").

For an example scenario of using the list of recent changes to determine whether a package removal and "Partial Upgrade" is safe, refer to [the next post]("http://ubuntuforums.org/showpost.php?p=8423549&postcount=2").


[*] Check the [build status information page]("https://launchpad.net/ubuntu/+builds") for Ubuntu and the [queue of new uploads to Lucid]("https://launchpad.net/ubuntu/lucid/+queue") on Launchpad to see if those mysterious missing dependencies are coming down the pipes, or there are problems preventing them from being built.


[*] Do a forum search, or [join the #ubuntu+1 channel on irc.freenode.net]("https://help.ubuntu.com/community/InternetRelayChat") and ask around to see whether other people are having problems with the same package(s).


[*] If you're still confused, simply **wait** and see if things are magically fixed within a few hours. If not, start a new thread or post to an existing one on the same issue to check with others.[/list]

A typical interaction with a package manager involves the following three steps:

[list] [*] You select some packages to be installed / removed / upgraded


[*] The package manager resolves your intention according to its package management logic, the available software sources, and the priorities you've indicated (as in APT pinning), if any, to a set of actions it has to perform, and outputs a list of those actions


[*] You check this list, confirm it if you're happy with it, or cancel it and refine your selection until you're happy with it.[/list]

If you skip the third step, assuming that simply updating your package information and hitting "Apply" or pressing "Enter" when the prompt comes up will give you the latest changes, and/or that since you're running a development release, any kind of package conflict / removal / replacement, even those that seem to intentionally remove lots of packages, are to be expected, you'll keep breaking your installation unnecessarily. Don't do that. Review that list of changes.

While asking for and providing assistance regarding testing is one of the main functions of this forum, learning [the basics of using development releases]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") is a prerequisite for doing useful testing, and if lots of people keep messing up their testing installations due to being unfamiliar with those basics, the forum will get flooded with duplicate threads and quicky become much less useful to everyone. 

Please take some time to learn the basics, and if you need help with that, don't hesitate to ask!

---

### Post by 23meg on 2009-12-01
Here's a typical scenario in which I figured out whether it was fine to let Synaptic remove *gstreamer0.10-schroedinger*, a package I knew nothing about previously, using one of the methods I suggested in the first post. This could have been any other package manager, such as Update Manager offering a "Partial Upgrade" to remove that package.

[list=1][*] Synaptic offered to remove the package *gstreamer0.10-schroedinger*. At this point I did not know whether Synaptic was offering to remove it due to temporary archive flux, or it was actually meant to be removed.

[[IMG]http://img16.imageshack.us/img16/2705/67492748.png[/IMG]](http://img16.imageshack.us/my.php?image=67492748.png)


[*] To figure out, I decided to check the karmic-changes mailing list (the current one is [Lucid-changes]("https://lists.ubuntu.com/mailman/listinfo/Lucid-changes")). Since I'm subscribed to it, I actually did this **much faster** in my mail client, but for the sake of illustrating how it could have been done without being subscribed (by the way: **subscribing is very beneficial if you're serious about testing** - there's also [an RSS feed]("http://feeds.ubuntu-nl.org/LucidChanges") if you don't want mail), and even only vaguely remembering the location of it, I'll pretend I browsed it at the web archives.


[*] At [https://lists.ubuntu.com/mailman/listinfo/Karmic-changes](https://lists.ubuntu.com/mailman/listinfo/Karmic-changes) (at which I may have arrived with a web search, or through [https://lists.ubuntu.com](https://lists.ubuntu.com)), I clicked the link leading to the archives.

[IMG]http://img140.imageshack.us/img140/9418/65689993.png[/IMG]


[*] I then clicked the "Date" link for the current month, since I was looking for what's probably a recent change, and I wanted the changes ordered by date.

[[IMG]http://img8.imageshack.us/img8/4152/74695720.png[/IMG]](http://img8.imageshack.us/my.php?image=74695720.png)


[*] I hit "Ctrl + F" in Firefox to search for the word "schroedinger", which is part of the package name, among the list of recent changes. I only typed the first few letters.

[[IMG]http://img12.imageshack.us/img12/2108/48677299.png[/IMG]](http://img12.imageshack.us/my.php?image=48677299.png)


[*] That highlighted what looked like a relevant change! I clicked on it to see the changelog.

[[IMG]http://img14.imageshack.us/img14/4971/85014317.png[/IMG]](http://img14.imageshack.us/my.php?image=85014317.png)


[*] I scanned through [the changelog]("https://lists.ubuntu.com/archives/karmic-changes/2009-October/010163.html") for a hint of whether this package is actually being removed. Searching the page for the words "remove", "drop" or "deprecate" was practical at this point, since I was looking to see if one of those things had happened to the suspected package.


[*] And there it was!
> debian/gstreamer0.10-schroedinger.install:
      - Dropped GStreamer plugin, it's now in gstreamer0.10-plugins-bad.


[[IMG]http://img8.imageshack.us/img8/4224/48655391.png[/IMG]](http://img8.imageshack.us/my.php?image=48655391.png)



[*] OK, it seems the GStreamer plugin for Schroedinger is being merged into the  *gstreamer0.10-plugins-bad* package, and the old package *gstreamer0.10-schroedinger* is being deprecated. So it should be fine to remove it.


[*] Just to make sure, and to satisfy my detective urge, I went back to archive page, and this time, searched for "plugins-bad", which led me to [a change entry for *gstreamer0.10-plugins-bad*]("https://lists.ubuntu.com/archives/karmic-changes/2009-October/011527.html").


[*] I looked for "schro..", and there we go:

>      + debian/gstreamer-plugins-bad.install:
       - Add new asfmux, frei0r, kate and schroedinger plugins.

[/list]

Now I know what's going on, and can comfortably let *any* package manager remove the suspected package. It's fine to accept a "Partial Upgrade" that wants to remove it.

---

### Post by Merk42 on 2009-12-01
Nice pun about being unsure of the status of a package called [schroedinger](http://en.wikipedia.org/wiki/Schr%C3%B6dinger%27s_cat)

Seriously though, when will this be stickied?

---

### Post by 23meg on 2009-12-01
> **Merk42 said:**
> Nice pun about being unsure of the status of a package called [schroedinger](http://en.wikipedia.org/wiki/Schr%C3%B6dinger%27s_cat)

Nice to see it received.

[quote=Merk42]Seriously though, when will this be stickied?[/QUOTE]

Right now.

---

### Post by VMC on 2009-12-01
If this doesn't answer all questions pertaining to Partial Upgrade,  nothing will. 

Good job.

---

### Post by philinux on 2009-12-02
+1 good job 23meg.

---

### Post by Sophont on 2009-12-03
Best sticky ever. :-)

---

### Post by woodnymph on 2009-12-13
i'm probably violating the spirit of this post, but one more question .. 

i would like to try the #3 approach and learn some, but i'm still new here and that all is still well over me.  this is the first time i've run a devel release .. 

so i use the update mngr .. it offers me a partial upgrade so i just closed out and have checked back a couple times over several days to run the update again.  still only a partial is offered.  should i keep waiting until it offers a normal update, or do something from a command line?  i seem to have a stable intall of the lucid alpha1 running.  any simple advice for a newby still in the middle ground .. much appreciated.

---

### Post by Rallg on 2009-12-14
Let me second woodnymph's above post. I can do "some" testing, but I'm not good enough to do "real" testing. For days, Update Manager has been offering a partial upgrade, and the problem files seem to be rather critical (including some Compiz support). So I won't do a partial upgrade to my otherwise-stable pre-alpha installation. I simply don't know enough to hand-pick files from the many that have changed.

Could I use apt-get in Terminal to do a lower-risk update?

---

### Post by Gina on 2009-12-14
sudo aptitude update && sudo aptitude safe-upgrade

if I remember correctly.

---

### Post by VMC on 2009-12-14
> **Gina said:**
> sudo aptitude update && sudo aptitude safe-upgrade

if I remember correctly.

That's exactly it. And if things are held back, there done that way for a reason. Just be patient. Most likely some supporting files are not ready yet.

---

### Post by woodnymph on 2009-12-16
> **Gina said:**
> sudo aptitude update && sudo aptitude safe-upgrade

if I remember correctly.

yup. the '&&' means basically that iff the first command runs successfully, then run the second.

---

### Post by 23meg on 2009-12-16
> **woodnymph said:**
> 
so i use the update mngr .. it offers me a partial upgrade so i just closed out and have checked back a couple times over several days to run the update again.  still only a partial is offered.  should i keep waiting until it offers a normal update, or do something from a command line?  i seem to have a stable intall of the lucid alpha1 running.  any simple advice for a newby still in the middle ground .. much appreciated.

You may want to check [whether your mirror is lagging behind]("launchpad.net/ubuntu/+archivemirrors"), and [whether there are new uploads or ongoing builds of packages that are held back, or their dependencies]("https://launchpad.net/ubuntu/+builds"). 

> **Gina said:**
> sudo aptitude update && sudo aptitude safe-upgrade

Aptitude can try to be overly "smart" when resolving dependency problems, especially with an unstable archive as in the development branch, and using it along with a different package manager and/or without caution can lead to trainwrecks that will be hard to fix. I'd recommend inexperienced testers to stick to apt-get as the command line option. The equivalent command would be: ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Gina on 2009-12-16
Thanks for that ***23meg*** :)  Something I wasn't aware of.

---

### Post by VMC on 2009-12-16
> **Gina said:**
> Thanks for that ***23meg*** :)  Something I wasn't aware of.

This is the first time I've heard this too. I will do both and see if aptitude is any different or what the difference is. Very simply answer "n" to either ones questions then weight the options.

---

### Post by Gtklocker on 2009-12-20
> **Gina said:**
> sudo aptitude update && sudo aptitude safe-upgrade

if I remember correctly.

That's the best. :)

---

### Post by phillw on 2009-12-20
I usually use synaptic's GUI and not allow partial updates. So having done that I followed 23meg's ```

sudo apt-get update && sudo apt-get upgrade
```And now have ....

```
The following packages have been kept back:
  evolution evolution-common evolution-indicator evolution-plugins gdm
  indicator-applet indicator-applet-session indicator-messages
  indicator-session initramfs-tools linux-generic linux-headers-generic
  linux-image-generic rhythmbox tomboy
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.

```Which is the same as is 'lurking' in my GUI as awaiting.
Just wondering if others have a similarly long queue ?
Do I need to alter my repositries ?
> #deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Alpha i386 (20091209)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
As you can see - I'm using the gb mirror, is this one upto date ?

Thanks,

Phill.

---

### Post by Gina on 2009-12-20
I forget now where you find out but as I recall the GB one is a fair bit behind.  For the most up-to-date use Main Server.

---

### Post by phillw on 2009-12-20
Hmm.. odd ?  I switched over to main server & it still says all the above listed are only partitial updates.

Phill.

---

### Post by lukjad on 2009-12-20
Interesting read, thanks for that.

---

### Post by Gina on 2009-12-20
> **phillw said:**
> Hmm.. odd ?  I switched over to main server & it still says all the above listed are only partitial updates.

Phill. Yes, still work in hand.

---

### Post by phillw on 2009-12-20
> **Gina said:**
> Yes, still work in hand.

I will continue as I am, then. I'd hate to bork A1 - it's running really well :-)

Phill.

---

### Post by 23meg on 2009-12-22
> **phillw said:**
> I usually use synaptic's GUI and not allow partial updates. So having done that I followed 23meg's ```

sudo apt-get update && sudo apt-get upgrade
```And now have ....

```
The following packages have been kept back:
  evolution evolution-common evolution-indicator evolution-plugins gdm
  indicator-applet indicator-applet-session indicator-messages
  indicator-session initramfs-tools linux-generic linux-headers-generic
  linux-image-generic rhythmbox tomboy
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.

```Which is the same as is 'lurking' in my GUI as awaiting.
Just wondering if others have a similarly long queue ?
Do I need to alter my repositries ?

As you can see - I'm using the gb mirror, is this one upto date ?

Thanks,

Phill.

Well, the whole point of having this thread is to provide you with the information with which *you* can figure out what to do in such a situation. I posted information on how to check whether your mirror is up to date just three posts above yours, as well as in the original post. Please take a little time to read or search through the existing information before posting.

Whether others are experiencing the same symptoms in their package managers is not a reliable indication of what's going on; others may have different sets of packages installed, may have activated testing PPAs, may have broken their testing installations, or may be using different mirrors, all of which will potentially lead to different sets of packages being or not being held back, thus mislead you in your judgement on what's going on.

[QUOTE=Gina]I forget now where you find out [/QUOTE]

Just a few posts above.

[QUOTE=Gina]For the most up-to-date use Main Server.[/QUOTE]

I would not recommend using it in testing except as a last resort, since it's going to be slow for you, and expensive for Canonical.

---

### Post by phillw on 2009-12-22
> "**How do I know whether a package is actually meant to be replaced or removed?**"

There's more than one way:
 Check the changelog of the package in question. .......by going to [packages.ubuntu.com]("http://packages.ubuntu.com/") and clicking "Ubuntu changelog" for the package you're curious about

So, I did & typed in Rythmbox, asked it to look in Lucid and got nothing returned

>    You have searched for *Rythmbox* in packages names and descriptions in suite(s) *lucid*, all sections, and all architectures (including subword matching).       
Sorry, your search gave no results
       
         

>     You have searched for files named *Rythmbox* in suite *lucid*, all sections, and all architectures.    
Sorry, your search gave no results
   
         

I guess that I'm doing something really dumb here :confused:

Phill.

---

### Post by 23meg on 2009-12-22
> **phillw said:**
> 
I guess that I'm doing something really dumb here :confused:

You seem to have misspelled "rhythmbox" when doing a search; it's missing the first "h". 

```
aptitude changelog rhythmbox
``` is faster.

---

### Post by brookie on 2009-12-22
Hi, 

Thanks for posting this. I recently added a launchpad ppa for an awesome [equalizer]("http://ubuntuforums.org/showthread.php?t=1308838&highlight=audio+ppa") posted on this forum and got the Partial Dist. Upgrade on three machines. 

Specifically I added [Ubuntu Audio Dev ppa]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa") to my sources. 

I did it! Luckliy everything is working okay on all 3 boxes but I have no idea how to back track and see what if anything was removed. 

So were these newer packages I installed incompatible with some older dependencies or something? I don't recall having packages removed but I do recall a lot of things being installed other than pavucontrol and pulseadio. 

Synaptic shows that these newer items are indeed installed and in use. 

Okay thanks. Gotta run.
Cheers, 
brook

---

### Post by phillw on 2009-12-22
Yup, that'd be it ....  I guess I'll have to learn to spell !!!

Now, I've just got try and make some sense of it all --

I've reverted back to UK server ... but can't seem to find which I'm using ?

> United Kingdom         8 Gbps                             11                      mirrors                                           [University Of Kent UK Mirror Service]("https://launchpad.net/ubuntu/+mirror/uk-mirror-service")                             [http]("http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/")           [ftp]("ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/")           [rsync]("rsync://rsync.mirrorservice.org/archive.ubuntu.com/ubuntu/")                  2 Gbps                             Six hours behind                                           [Bytemark Hosting]("https://launchpad.net/ubuntu/+mirror/bytemark-archive")                             [http]("http://mirror.bytemark.co.uk/ubuntu/")           [ftp]("ftp://mirror.bytemark.co.uk/ubuntu/")           [rsync]("rsync://mirror.bytemark.co.uk/ubuntu/")                  1 Gbps                             Up to date                                           [Ticklers.org]("https://launchpad.net/ubuntu/+mirror/ftp.ticklers.org-archive")                             [http]("http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/")           [ftp]("ftp://ftp.ticklers.org/archive.ubuntu.org/ubuntu/")           [rsync]("rsync://ftp.ticklers.org/archive.ubuntu.org/ubuntu/")                  1 Gbps                             Two days behind                                           [XILO Communications Ltd.]("https://launchpad.net/ubuntu/+mirror/mirror.as29550.net-archive")                             [http]("http://mirror.as29550.net/archive.ubuntu.com/")           [ftp]("ftp://mirror.as29550.net/archive.ubuntu.com/")                             1 Gbps                             Two days behind                                           [Oxford University Computing Services]("https://launchpad.net/ubuntu/+mirror/mirror.ox.ac.uk-archive")                             [http]("http://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/")           [ftp]("ftp://mirror.ox.ac.uk/sites/archive.ubuntu.com/ubuntu/")           [rsync]("rsync://mirror.ox.ac.uk/sites/archive.ubuntu.com/")                  1 Gbps                             Two days behind                                           [Goscomb Technologies Limited]("https://launchpad.net/ubuntu/+mirror/mirror.sov.uk.goscomb.net-archive")                             [http]("http://mirror.sov.uk.goscomb.net/ubuntu/")           [ftp]("ftp://mirror.sov.uk.goscomb.net/ubuntu/")                             1 Gbps                             One day behind                                           [Datahop Ltd.]("https://launchpad.net/ubuntu/+mirror/ubuntu.datahop.net-archive")                             [http]("http://ubuntu.datahop.net/ubuntu/")           [ftp]("ftp://ubuntu.datahop.net/ubuntu/")           [rsync]("rsync://ubuntu.datahop.net/ubuntu/")                  1 Gbps                             Up to date                                           [Canonical Ltd.]("https://launchpad.net/ubuntu/+mirror/archive.ubuntu.com")                             [http]("http://archive.ubuntu.com/ubuntu/")           [ftp]("ftp://archive.ubuntu.com/ubuntu/")           [rsync]("rsync://archive.ubuntu.com/ubuntu/")                  100 Mbps                             Up to date                                           [The Positive Internet Company]("https://launchpad.net/ubuntu/+mirror/ubuntu.positive-internet.com-archive")                             [http]("http://ubuntu.positive-internet.com/ubuntu/")                                        100 Mbps                             One week behind                                           [Retrosnub Internet Services]("https://launchpad.net/ubuntu/+mirror/ubuntu.retrosnub.co.uk-archive")                             [http]("http://ubuntu.retrosnub.co.uk/ubuntu/")           [ftp]("ftp://ubuntu.retrosnub.co.uk/ubuntu/")           [rsync]("rsync://ubuntu.retrosnub.co.uk/ubuntu/")                  100 Mbps                             Two hours behind                                           [Virgin Media]("https://launchpad.net/ubuntu/+mirror/ubuntu.virginmedia.com-archive")                             [http]("http://ubuntu.virginmedia.com/archive/")           [ftp]("ftp://mirrors.virginmedia.com/mirrors/ubuntu/archive")                             100 Mbps                             One day behindAll i have in Synaptic is >  **rhythmbox **music playerand organiser for GNOME (Size 1.0Mb)So, It's not really telling me anything about version numbers etc.
[http://packages.ubuntu.com/lucid/remuco-rhythmbox](http://packages.ubuntu.com/lucid/remuco-rhythmbox)

just says > **Package: remuco-rhythmbox (0.9.1.1+dfsg-1)  [[B]universe**] [/B]

Synaptic says I have 0.12.6-1ubuntu1

I'm sorry for appearing incredibly stupid, but I AM trying to get my head round this, as between rhythmbox and evolution my system is going trotting off to get 4MB of downloads every time I check for updates (about twice a day).

/edit -- okies, what I did was that both Rhythmbox and Evolution showed in Synaptic Package Manager as having newer versions than I had installed. I checked the 'mark for upgrade' and let it get on with it. Everything is working well. Now, if someone could confirm wether that is the 'safe' way for me deal with applications such as the two mentioned - or should I have done further checking ?  Thanks, Phill.

Phill.

---

### Post by Jordanwb on 2009-12-23
For the past week or two my laptop has been wanting me to do a partial upgrade. I read the OP but I don't want to mess up my A1 install. It's running very well.

---

### Post by phillw on 2009-12-23
> **Jordanwb said:**
> For the past week or two my laptop has been wanting me to do a partial upgrade. I read the OP but I don't want to mess up my A1 install. It's running very well.

I used package manager within synaptic to update Rhythmbox and Evolution - I don't use Evolutuion, so have no idea if it is/was working - But Rythmbox is still fine.
The listing of things for partial update has dropped to about 6 items. So far, so good :P

Phill.

---

### Post by Jordanwb on 2009-12-30
Rhythmbox and Evolution and its dependencies are one of the first packages that I remove when I install Ubuntu. One of the packages that is held back is GDM. If I force Synaptic to install GDM it wants to remove usplash, which I suppose is the start of using plymouth in place of usplash.

*Edit*

I installed plymouth, removed usplash, which upgraded GDM, which lets me upgrade everything else. Plymouth fails to start but that's another thread.

---

### Post by nanog on 2010-01-07
> If you do, you will most likely end up removing packages that shouldn't be removed, and waste time and effort repairing your testing installation and asking for assistance.

```
dpkg --purge badnewpackage; dpkg -i /var/cache/apt/oldpackage.deb; sudo apt-get --reinstall xorg xterm ubuntu-desktop
```

:o

---

### Post by kevpan815 on 2010-01-09
> **23meg said:**
> During the development cycle of Ubuntu 9.10, we've been flooded with threads asking for assistance related to issues caused by careless usage of the "Partial Upgrade" feature of Update Manager, which hinted to a poor understanding of package management and the way updates happen in the development branch. 

In an effort to help with this situation, this document aims to clarify what a "Partial Upgrade" is, and why, **in most cases, you'll want to avoid it**.


[SIZE="4"]**Summary**[/SIZE]
[SIZE="1"]or **"I don't really care if I keep messing things up and wasting my and others' time with preventable problems, and you have 30 seconds to convince me to care!"**[/SIZE]

If you use Update Manager to upgrade your packages, and it offers to do a "Partial Upgrade", do not accept it without thoroughly checking what packages it offers to remove, upgrade and install. If you do, you will most likely end up removing packages that shouldn't be removed, and waste time and effort repairing your testing installation and asking for assistance. 

Most "Partial Upgrade" situations occur due to package archive inconsistencies, which will typically be resolved within a few hours. If your package manager is confused, and so are you, **simply wait** and hold off the updates until things settle down. 


[SIZE="4"]**Short Version**[/SIZE]
[SIZE="1"]or **"Hmm, so I shouldn't blindly do "Partial Upgrade"s and dist-upgrade? I didn't know that..."**[/SIZE]

Due to the fact that uploads to the repositories of the active development branch are asynchronous and uncoordinated, dependencies of certain packages may arrive later than the dependent package. This causes package management tools such as Update Manager, which are mainly meant to be used with stable releases of Ubuntu where the package archive is always consistent, to interpret the situation as requiring a dist-upgrade to install new packages and/or repair packages in a "reqreinst" (requires reinstallation) state. What Update Manager performs when doing a "Partial Upgrade" is a dist-upgrade.

When testing development releases, most of the time, a "Partial Upgrade" is undesired. The situations where it's needed are limited to new packages obsoleting old ones (as in the case of the software-center package replacing software-store) and package removals from the archive.

Do not assume that since you're running a development release, a "Partial Upgrade" is necessarily warranted.


**[SIZE="4"]Long Version[/SIZE]**
[SIZE="1"]or **"I want to be a better tester! I care! Tell me more!"**[/SIZE]

In its normal operating mode, Update Manager will not offer to remove packages. This is the equivalent of "apt-get upgrade"ing your existing packages. In "Partial Upgrade" mode, it can. Sometimes, the removal is warranted, such as when a package is obsoloted by a new one. Other times, it will not be, and a "Partial Upgrade" can offer to remove important packages due to missing dependencies.

Now, the key question: 

"**How do I know whether a package is actually meant to be replaced or removed?**"

There's more than one way:

[list][*] Check the changelog of the package in question. You can do this via "Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or by going to [packages.ubuntu.com]("http://packages.ubuntu.com") and clicking "Ubuntu changelog" for the package you're curious about, or visiting the URL 

[https://launchpad.net/ubuntu/+source/](https://launchpad.net/ubuntu/+source/)[COLOR="DarkRed"]package_name[/COLOR]/+changelog

where [COLOR="DarkRed"]package_name[/COLOR] is the name of the source package you're curious about. The most recent changelog entry will indicate the reason for the removal or replacement, if there is one.


[*] Keep an eye on the changes mailing list or RSS feed for the active development release. The current ones are the [lucid-changes mailing list]("https://lists.ubuntu.com/mailman/listinfo/Lucid-changes"), and [its RSS counterpart]("http://feeds.ubuntu-nl.org/LucidChanges").

For an example scenario of using the list of recent changes to determine whether a package removal and "Partial Upgrade" is safe, refer to [the next post]("http://ubuntuforums.org/showpost.php?p=8423549&postcount=2").


[*] Check the [build status information page]("https://launchpad.net/ubuntu/+builds") for Ubuntu and the [queue of new uploads to Lucid]("https://launchpad.net/ubuntu/lucid/+queue") on Launchpad to see if those mysterious missing dependencies are coming down the pipes, or there are problems preventing them from being built.


[*] Do a forum search, or [join the #ubuntu+1 channel on irc.freenode.net]("https://help.ubuntu.com/community/InternetRelayChat") and ask around to see whether other people are having problems with the same package(s).


[*] If you're still confused, simply **wait** and see if things are magically fixed within a few hours. If not, start a new thread or post to an existing one on the same issue to check with others.[/list]

A typical interaction with a package manager involves the following three steps:

[list] [*] You select some packages to be installed / removed / upgraded


[*] The package manager resolves your intention according to its package management logic, the available software sources, and the priorities you've indicated (as in APT pinning), if any, to a set of actions it has to perform, and outputs a list of those actions


[*] You check this list, confirm it if you're happy with it, or cancel it and refine your selection until you're happy with it.[/list]

If you skip the third step, assuming that simply updating your package information and hitting "Apply" or pressing "Enter" when the prompt comes up will give you the latest changes, and/or that since you're running a development release, any kind of package conflict / removal / replacement, even those that seem to intentionally remove lots of packages, are to be expected, you'll keep breaking your installation unnecessarily. Don't do that. Review that list of changes.

While asking for and providing assistance regarding testing is one of the main functions of this forum, learning [the basics of using development releases]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") is a prerequisite for doing useful testing, and if lots of people keep messing up their testing installations due to being unfamiliar with those basics, the forum will get flooded with duplicate threads and quicky become much less useful to everyone. 

Please take some time to learn the basics, and if you need help with that, don't hesitate to ask!

Great advice 23meg! Yesterday, Update-Manager offered me a Partial Upgrade and Today Update-Manager fixed the problem just as you described automatically!

---

### Post by amsterdamharu on 2010-02-22
I just read this after the partial upgrade, took 3 hours to download. I think all the packages are re-installed and 2 are removed (obsolete).

Computer seems to be working fine but it gave me an extra package "Disk Utility 2.29.0" by red hat. I know this tool with fedora it gives me warnings about bad sectors on the harddisk but there is nothing wrong with the harddisk.

I will remove this package since I don't remember ever asking for it to be installed. If everything brakes down I have a copy of the system I can put back anyway.

[update]
Can't find disk utility in the synaptic package manager. Thoughtful of the programmers to make a program that doesn't work with a title that isn't used used in software package maintenance software. It's called gnome-disk-utility. Searching for disk utility in title and description just gives too many results
[/update]

---

### Post by grubdude on 2010-02-24
Sure wish that I had read this before accepting one or two partial upgrades. Everything seems to be working fine but for now on I will wait and not accept partials. What is the best way to make sure that something that should be there (is) and something that shouldn't is not? 

Thanks......

---

### Post by ranch hand on 2010-02-24
Use "apt-get update" and "apt-get upgrade".

Go to "Software Sources" and uncheck "check for updates daily".  That will shut Update Mangler up.

If you do not like apt (which I think is safest - you will here from the aptitude folks) use synaptic.

---

### Post by Slug71 on 2010-02-27
Does anybody else have 69 updates being held back?

---

### Post by Uncle Spellbinder on 2010-02-27
I just ran the update manager and was offered 7 updates. Same in Synaptic and *apt-get upgrade*. Nothing being held back here.

---

### Post by Slug71 on 2010-02-27
> **Uncle Spellbinder said:**
> I just ran the update manager and was offered 7 updates. Same in Synaptic and *apt-get upgrade*. Nothing being held back here.

Thanks, yeh theyve been held back for a while.

---

### Post by VMC on 2010-02-27
> **Slug71 said:**
> Thanks, yeh theyve been held back for a while.

run this and see what's held back. You can quit it at the end:

```
sudo aptitude update && sudo aptitude safe-upgrade

```

Then look at the held back.

---

### Post by Otaconda on 2010-03-11
Update manager has been asking me to do a partial upgrade for 24 hours or so - it wants to remove brasero f-spot gnome-applets gnome-disk-utility gnome-session gvfs-backends gvfs-bin gvfs-fuse nautilus nautilus-share ubuntu-desktop update-notifier usb-creator-common usb-creator-gtk

That seems a bit much to me. Cant seem to pinpoint why it's come to this conclusion (in the package changelogs) - any pointers?

---

### Post by ranch hand on 2010-03-11
> **Otaconda said:**
> Update manager has been asking me to do a partial upgrade for 24 hours or so - it wants to remove brasero f-spot gnome-applets gnome-disk-utility gnome-session gvfs-backends gvfs-bin gvfs-fuse nautilus nautilus-share ubuntu-desktop update-notifier usb-creator-common usb-creator-gtk

That seems a bit much to me. Cant seem to pinpoint why it's come to this conclusion (in the package changelogs) - any pointers?
Quit using Update Mangler and use some thing that will give you some information.

I like a combination of apt-get and synaptic.  I use apt for updating and upgrading and synaptic to tell me what the held back packages are going to do.

If it wants to remove a lot of stuff leave it a lone.  Remember to breath.  The world will not end if those packages sit there for a month.

---

### Post by Otaconda on 2010-03-11
I'm not posting out of impatience, I'm posting because I've never known the archive to be confused for this long. apt-get doesn't give me enough information, and I find synaptic horrible, but fair point in that there is more to find out.

aptitude does list the conflicts more explicitly:

The following packages are BROKEN:
  libparted1.8-12 update-notifier 
The following packages will be REMOVED:
  devicekit-disks{a} dmraid{u} kpartx{u} libdmraid1.0.0.rc16{u} 
---
The following packages have unmet dependencies:
  update-notifier: Depends: update-notifier-common (= 0.96) but 0.98 is to be installed.
  libparted1.8-12: Conflicts: libparted0 but 2.2-1ubuntu2 is to be installed.

If this kind of archive inconsistency is more common than I've experienced then that's fine, just looking for some advice is all.

---

### Post by ranch hand on 2010-03-11
Ah, I see said the blind man as he picked up his hammer and saw.

Welcome to testing pre-release OS'.

This is not really inconsistency.  It is more that there are a lot of packages to get into the repo and some are ready before others.  Change is rapid and these things are going to happen regularly.

This does not happen on stable releases basically because they are stable.  We are unstable here and no I don't just mean the OS.

---

### Post by shafin on 2010-03-11
> **Otaconda said:**
> I'm not posting out of impatience, I'm posting because I've never known the archive to be confused for this long. apt-get doesn't give me enough information, and I find synaptic horrible, but fair point in that there is more to find out.

aptitude does list the conflicts more explicitly:

The following packages are BROKEN:
  libparted1.8-12 update-notifier 
The following packages will be REMOVED:
  devicekit-disks{a} dmraid{u} kpartx{u} libdmraid1.0.0.rc16{u} 
---
The following packages have unmet dependencies:
  update-notifier: Depends: update-notifier-common (= 0.96) but 0.98 is to be installed.
  libparted1.8-12: Conflicts: libparted0 but 2.2-1ubuntu2 is to be installed.

If this kind of archive inconsistency is more common than I've experienced then that's fine, just looking for some advice is all.
There is a problem with libparted1.8-12, its been replaced with libparted0. You should go to synaptic and install libparted0, this will remove libparted1.8.

---

### Post by Otaconda on 2010-03-12
Just the job, thanks :)

---

### Post by Slug71 on 2010-03-12
I currently have these packages held back:
 > couchdb-bin, gdm, gnome-power-manager, gnome-session, gnome-session-bin, gparted,
  libdevkit-power-gobject1, parted, udisks, update-notifier,
  update-notifier-common, upower, yelp

---

### Post by plun on 2010-03-12
```
sudo apt-get install libparted0 
```

;)

---

### Post by teh603 on 2010-03-12
> **shafin said:**
> There is a problem with libparted1.8-12, its been replaced with libparted0. You should go to synaptic and install libparted0, this will remove libparted1.8.So will the Beta 1 installer have libparted0 or libparted1.8 ?

---

### Post by geoffp on 2010-03-15
> **shafin said:**
> There is a problem with libparted1.8-12, its been replaced with libparted0. You should go to synaptic and install libparted0, this will remove libparted1.8.

Thanks!  Once I did this, synaptic was able to upgrade the rest of my system normally.  I was a bit freaked out by the removal of devicekit-disks, but I gather that's being replaced by udisks, is that right?

---

### Post by Orographic on 2010-03-23
I'm trying to follow this. So, once I've installed Lucid Beta 1, is it okay to go to update manager in system>admin>update manager and download software updates there?

---

### Post by 23meg on 2010-03-23
> **Orographic said:**
> I'm trying to follow this. So, once I've installed Lucid Beta 1, is it okay to go to update manager in system>admin>update manager and download software updates there?

Yes, and you should do that (or use another package manager) if you want to keep up to date with testing.

---

### Post by Orographic on 2010-03-23
Thanks, am downloading all updates now for Beta 1.

---

### Post by enceladus47 on 2010-03-24
I now just update through apt-get update and apt-get upgrade, but a few days back when I didn't know I did the partial upgrade which only removed f-spot and gvfs-bin.
Now when I try to install f-spot I get ' Depends: gvfs-bin but it is not going to be installed', and when I try to install gvfs-bin I get '  Depends: gvfs (=1.5.5-0ubuntu2) but 1.4.1-0ubuntu1 is to be installed'.

Any idea what I should do? I don't need f-spot urgently so I can wait if I can install them after some upgrade.

---

### Post by enceladus47 on 2010-03-25
all sorted by installing libparted0, don't even get the option to partial upgrade anymore

---

### Post by Cavsfan on 2010-04-01
(I am a real noob when it comes to testing this stuff, so please bear with me. I am 
giving this my best shot though and can hopefully contribute as I have seen many other 
generous people on here do.)

Today I seen my first "partial upgrade" in Update Manager. I didn't let it install anything. 
I happen to see a post by Ranch Hand and asked about it. Good thing I did and didn't let it upgrade. 
He told me to use "_sudo apt-get update_ and then _sudo apt-get upgrade_" instead of Update Manager. 
So, I entered the 2 commands and got a whole bunch of updates.
Immediately afterwards I brought up Update Manager and I think (but am not 100% certain) that 
it was still wanting to do a "Partial Upgrade". I just left it alone.

Now, several hours have gone by and I brought up Update Manager and it does not mention anything 
about "Partial Upgrade".

So, my question is this: should I stay away from Update Manager altogether or is it OK to use when it is 
not saying it wants to do a "Partial Upgrade"? Can I still use the above 2 underlined commands and get all 
of the upgrades I need?

I am sorry, but I cannot read through all of the stuff I should be to keep up with this, but I have a neurological 
disorder that slows me down to about 50% of what I once was.
I am trying though and by trying I feel like I am contributing to something good.
I can do a lot of things, but researching things and reading a lot of stuff are not one of my strong suits.

So, should I use Update Manager when it doesn't say "Partial Upgrades" or can I just get by with a terminal and 
the two commands above or what else do I need to do.
Thanks for your patience!

---

### Post by cariboo on 2010-04-01
I would suggest if you want to continue using a gui app to upgrade, use synaptic package manager, as it essentially does the same as aptitude safe-upgrade. It will let you know what it is going to remove before allowing you to continue with the update.

---

### Post by Cavsfan on 2010-04-01
> **cariboo907 said:**
> I would suggest if you want to continue using a gui app to upgrade, use synaptic package manager, as it essentially does the same as aptitude safe-upgrade. It will let you know what it is going to remove before allowing you to continue with the update.

Thanks a lot for your prompt response.
I'll do that, but when it says "partial upgrade" I use the 2 commands right?
When Update Manager does not say "partial upgrade", I can safely use it right?
I just have a hard time reading through and deciphering what all it will remove.
And then what to do with it once I have read it.
Thanks again!

---

### Post by haddog on 2010-04-01
You really can learn something just by **READING** these forums. For all the years I have been using Ubuntu, I did not know what the heck a "Partial Upgrade" was. Most of the time I use the apt-get command from a terminal so maybe that is why I wasn't really concerned. Great post, Thnx!

---

### Post by Cavsfan on 2010-04-01
I think I have it now.
I entered "apt-get dist-upgrade" and it held back 7 packages.

I then brought up Update Manager and it installed 3 things and there were 7 things
grayed out, which I guess were "held back".

So they both matched. So, [U]only when Upgrade Manager says "partial upgrade" do I need 
to worry about anything right? [/U]That's when I use "sudo apt-get update" and then "sudo apt-get upgrade".

(Taking notes, so I learn something from this)

Thanks!

---

### Post by ranch hand on 2010-04-01
I would quit using Update Mangler at all.  It is a pain.

---

### Post by arpanaut on 2010-04-01
> **ranch hand said:**
> I would quit using Update Mangler at all.  It is a pain.

Pardon Me!  but Update Manager works perfectly fine 99% of the time.

IF one avoids "Partial Upgrades"...  When things do go wrong, yes, the CLI, Apt, Aptitude, and Synaptic are great tools for recovery.  MOST users do not need to resort to using those tools.

No offense meant towards you Mr. Ranch Hand, you do great work around here, and I understand where you are coming from.  I've been riding this wild mustang since Warty Warthog... over 5 years and the more that I use this OS the more I have come to appreciate what Mr. Shuttleworth and the crew is trying to do!  Offer a "Human" usable GUI orientated system that the average user is comfortable with. 

I love the CLI, it's functionality, it's expediency, and simplicity.  It's saved my bacon many times and "testers" should be competent in it's use!  

It is not the be all, end all for the Common User.

Just this "Old Cowboy's" opinion in contrast with that of a competent "Ranch Hand"

Best Wishes to All

---

### Post by ranch hand on 2010-04-01
Yup, we have a disagreement there.  I bet we can live with it.

I am not too sure about the competent part though.

And I am not too sure about there being a "common user" on any Linux OS.  There I think the common perception by non users is probably correct.

We really are a strange bunch.

---

### Post by arpanaut on 2010-04-01
> **ranch hand said:**
> 

We really are a strange bunch.

Yup... You got that right!

And... Yes we can deal with difference of opinion 'round here!

---

### Post by Cavsfan on 2010-04-02
You guys are cracking me up! :D

I just got on this band wagon last year with Jaunty, so I am pretty noobish and like I mentioned in a previous post 
I have a neurological disorder that slows me down a lot, but don't worry I am not going to croak anytime soon or anything like that. 
I just have to struggle a bit more than most folks do to get things done. 
I may ask a lot of questions, but I try to take notes so that I only have to ask once.

(sorry about all of the I's above; it's like me. me, me!)

I really do like this Ubuntu though!

_One question: What is the CLI?_

Thanks!

---

### Post by iClouseau88 on 2010-04-02
C=command
L=Line
I=Interface

e.g C:\Windows>

ha ha!

---

### Post by ranch hand on 2010-04-02
Command Line Interface.  Your terminal.

---

### Post by andrewabc on 2010-04-02
Applications->Accessories->Terminal

---

### Post by Cavsfan on 2010-04-02
Well, you can bet I won't forget what CLI stands for! LOL!

---

### Post by Owen.C93 on 2010-04-05
I've been having the for a while now. The latest headers are greyed out.

---

### Post by vivekspanicker on 2010-04-06
hi,. today I have installed lucid beta in my msi netbook. But accidently syatem got off at the final stage. Lucid got installed in my system but seems some bugs are arising. I am not able to see lucid in my boot menu. Instead, older 9.10 version is showing. But selecting this option will lead to lucid. I am not able to use update manager. It is getting closed while choosing partial upgrade. How can I install this fully? Please help with this. Thanks in advance for your support.

---

### Post by ranch hand on 2010-04-06
You should be happy that you can't choose a partial upgrade.  It is a bad idea.

Use apt-get, aptitude, or synaptic.

---

### Post by Cavsfan on 2010-04-06
Yes, like Ranch Hand said use these commands:
"sudo apt-get update" and then "sudo apt-get upgrade".
Also "sudo apt-get dist-upgrade" for kernels, etc.

That way, you only get what you should be getting and nothing more.

Can anyone tell me if ALT-TAB will work to switch between applications?
Didn't it use to work or am I losing my mind? (which is a definite possibility).

I keep pressing ALT-TAB and mess up whatever I have open with the TAB.
I could have sworn I used ALT-TAB at one time to move between apps. ](*,)

---

### Post by ranch hand on 2010-04-06
It is working for me on any workspace here.

---

### Post by VMC on 2010-04-06
> **Cavsfan said:**
> 
Can anyone tell me if ALT-TAB will work to switch between applications?


Open *System>Preferences>Keyboard Shortcuts*, then find ALT+TAB under shortcut. It should state on the left ..to move between windows.

---

### Post by Cavsfan on 2010-04-07
> **VMC said:**
> Open *System>Preferences>Keyboard Shortcuts*, then find ALT+TAB under shortcut. It should state on the left ..to move between windows.

Thanks! It was disabled, I just had to put ALT+TAB back in there and it is good to go now.
I am used to having that work and now it does. 

Not a day goes by that I don't learn something on here.

Thanks again! :D

---

### Post by Owen.C93 on 2010-04-07
I can't get the -19 headers :(, I get offered a partial upgrade I click no and just have 3kb kernel updates greyed out. Why would this be? I've tried synaptic but I dont think it worked.

---

### Post by ranch hand on 2010-04-07
If you mark it for upgrade in synaptic and it is not going to upgrade it you should get a box explaining why not.

If you mark it for upgrade and it marks it and you hit apply you should get a box saying what it is going to do.  Look at the details.

Synaptic is working fine on all my installs.

If it is not working you could always go to terminal and;
```

sudo apt-get upgrade

```
This should show what is held back and what is going to be upgraded.

If the only thing held back is kernel related;
```

sudo apt-get dist-upgrade

```
should get it.

---

### Post by Owen.C93 on 2010-04-07
> **ranch hand said:**
> If you mark it for upgrade in synaptic and it is not going to upgrade it you should get a box explaining why not.

If you mark it for upgrade and it marks it and you hit apply you should get a box saying what it is going to do.  Look at the details.

Synaptic is working fine on all my installs.

If it is not working you could always go to terminal and;
```

sudo apt-get upgrade

```This should show what is held back and what is going to be upgraded.

If the only thing held back is kernel related;
```

sudo apt-get dist-upgrade

```should get it.
Hmm there's a few others being held back to.  I'll leave it a bit longer and force an upgrade eventually.

---

### Post by AndThenWhat on 2010-04-09
I would not recommend doing the partial upgrade.  I did it last night to upgrade to the Lucid Beta 2 and it essentially broke Compiz and semi-broke metacity.

---

### Post by Cavsfan on 2010-04-09
I now only use Update Manager to check to see if there are any updates. I seen this morning that there were a lot of updates. I closed Update Mangler.
Then I used these commands (thanks Ranch Hand) to get the updates:
1) "sudo apt-get update" 
2) "sudo apt-get upgrade" 
3) "sudo apt-get dist-upgrade" to check for kernels and some other things.

There were a lot of updates this morning and it didn't say re-boot, but I did it anyway.

Then after getting some emails about Lucid-changes. I checked Update Mangler and it said it wanted to do a "partial upgrade". 
I promptly closed that and executed the 3 commands listed previously. It got a whole lot more updates and even the 3rd command pulled in something. 

Then I went back to Update Manager and it said there were no updates.
So, these 3 commands can alleviate the need to contemplate partial upgrades and can keep your system up to date as well.

It has been a busy day with the updates...

---

### Post by Cavsfan on 2010-04-09
My bad!

---

### Post by Cavsfan on 2010-04-10
I wish I could delete that last post, but I couldn't figure out a way.

I got so many updates today and yesterday that my screen saver started to kick on!

Wonder how it knows I have an HP Photosmart all-in-one.
I haven't even had it on (that I know of) and it has installed the latest HPLIP
and a lot of other HP stuff. Although I haven't installed the drivers yet. I think
I better do that...

Off to install HP drivers and test the printer...

---

### Post by 23meg on 2010-04-13
> **Cavsfan said:**
> 
Then I went back to Update Manager and it said there were no updates.
So, these 3 commands can alleviate the need to contemplate partial upgrades and can keep your system up to date as well.

What Update Manager does when you accept a partial upgrade is actually dist-upgrade, so that situation is not surprising. But it isn't generally advisable either: **dist-upgrading is not a way of getting rid of an unstable archive / package conflict situation, since it's the same thing as accepting a partial upgrade**. It shouldn't be resorted to without studying the changelogs for the packages involved and establishing that the situation involves an intended package removal.

---

### Post by ranch hand on 2010-04-13
+1

It does give you a nice list of things to be removed or added that you can see before hitting enter.

That of coarse is the problem.  You do need to read.

---

### Post by Cavsfan on 2010-04-14
+1

So, I guess it's 1/2 dozen of one or 6 of the other...

I do like being able to read what's happening though. However, being able to read does not mean that one understands everything one reads.
So, either way would make no difference. I like the 3 commands though.

Thanks for the clarification.

---

### Post by ranch hand on 2010-04-14
You are usually safe if the upgrade is adding packages.

It is when it is removing packages where you generally run into trouble.  This comes about when there is no package replacing the one being removed.

Of coarse the best thing to do if you do not want this problem is to not run development OS' in the first place.  No matter how careful you are there is a good chance that some update, someday will whack your OS.

That is what we are here for, to get whacked.  File bugs.  Let the devs sort it out so that folks think the new release on release day is just great.

---

### Post by UpSignal on 2010-04-14
Oh man... i didn't know about this... and actualy i just clicked to install the partial upgrade. i saw some things getting removed, but didn't care because i always trusted the update manager. then, at the end, i came here to the forum because the word "partial upgrade" reminded me some topic. then i found out this topic...and now the question is: What i'm gonna do now? is there a way to see the history of the things removed/installed? synaptic didn't show me, where do i get the update manager history? so far my system doesn't show signs of a near break down.
god damn it, why did i clicked the damn button :s
i'm using luci lynx

---

### Post by ranch hand on 2010-04-14
Hey you get away with it sometimes.  As we near release the incidence of partials should decrease some.

Just keep updating and the packages will catch up.

If you use synaptic instead of UM it will be safer and give you better information on what is going to happen.

---

### Post by Cavsfan on 2010-04-14
As long as you can still boot up, you will always get the updates at a later point even if you have done a partial. 
Am I right? At least that is what my experience appears to be.

And the partials do not come once it's been finally released right? This is just because this is a development release.

I am very happy to be a part of this! I think this is gonna be an awesome OS!\\:D/

---

### Post by ranch hand on 2010-04-14
If you think about the number of updates per day, you will realize that they are being loaded on the repos very fast.

Sometimes packages that need each other just don't get on at the same time.   This is when apt, aptitude, and synaptic will hold packages back an wait for the rest.  It is also an example of when you get the offer of a partial upgrade.

This kind of thing just does not happen with a stable release.   I mean, geeze, you could go months (on Hardy right now) and not get the kind of updates we are getting on some days.

---

### Post by UpSignal on 2010-04-14
well, i've rebooted my laptoo. so far, no problems :D
Oh man..i hope these 15 days go fast. lucid owns

---

### Post by 23meg on 2010-04-14
> **Cavsfan said:**
>  However, being able to read does not mean that one understands everything one reads.
So, either way would make no difference. 

If you don't understand what you read, you can ask for assistance in this forum. If you still don't understand how to interpret package manager output, how to find and read changelogs etc. after a while (assuming people help you in an appropriate manner) , your testing will likely not be very useful.

> **Cavsfan said:**
> I like the 3 commands though.

Applying those three commands blindly in the development branch is a recipe for needlessly breaking your system and keeping people busy with redundant support requests.

---

### Post by 23meg on 2010-04-14
> **Cavsfan said:**
> As long as you can still boot up, you will always get the updates at a later point even if you have done a partial. 
Am I right? At least that is what my experience appears to be.

If the partial ugrade / dist-upgrade removed packages that shouldn't be removed, you'll have to find out what those are and reinstall them. If you fail to, that may affect the health of your system, and the accuracy of your testing negatively in various ways.

[QUOTE=Cavsfan]And the partials do not come once it's been finally released right? This is just because this is a development release.[/QUOTE]

That's right.

---

### Post by cheapsaket on 2010-04-14
I have been doing apt-get update and apt-get upgrade and noticed something strange yesterday.
apt-get upgrade showed me the -20 kernel and a few other updates that it said were being held back and did not give me an option to install them.

I went to update manager and it showed me the same updates and allowed me to install them, there were no mentions of packages being held back etc.

This experience was sort of opposite to the one this thread discusses!

Any thing to be concerned about?

---

### Post by ranch hand on 2010-04-14
That was because apt is conservative.  You were shown 3 packages to be upgraded.  There were also 3 packages being installed.

If you had used "dist-upgrade" it would have shown you the 3 to be upgraded and the 3 to be installed and asked if you wanted to do that.

If you had gone to synaptic and done your upgrading there is would have offered the mto you the first time around but you would have a chance to see everything to be done in the acceptance box that would have come up when you hit "apply".

---

### Post by Cavsfan on 2010-04-14
23meg, don't worry, I am not as dumb as I apparently led you to believe.
By saying I can read, but don't always understand, I only meant that some of the names of the programs being updated I don't have a clue what they are: gwibber, bindwood, wesnoth, heartbeat, cluster-glue for example. 
I have no idea what these are but I can see them and if they bomb I do know how to file a bug report.

Besides I see them way before hand as I am subscribed to the Lucid-Changes email list.
For this development release, I let the emails pile up for a while and then get some updates.

I have been familiar with raw Linux commands for about 10 years, but only got involved with Ubuntu about a year ago. 
This is my first contribution as a tester on a development release (if that is what you call me playing around with it as much as I can). 
I only got into Lucid because Karmic would never put my PC to sleep like I wanted it to. Jaunty did perfectly and that was my first flavor of Ubuntu, you could say.

I have not and will never ask for any "redundant support requests".
When I have an issue, I research it on Google and try to find the answer myself and if I cannot, I submit a thread on here. But, I always take careful notes and will not ask the same question twice. 

I worked in computer electronics for 8 years and about 20 years as a senior main frame programmer/analyst. Then I came down with this dastardly neurological disorder which put a big hurt on my ability to do a lot of things. 
But, I am not brain damaged (at least I don't think I am :P). I could be wrong, it's happened before.
I do feel like my knowledge of Ubuntu and Linux has come a long way.
At the risk of blowing my own horn, I was always one of those people who never needed to take notes in computer classes. I had a pad, but it went unused. I just absorb everything I hear and never, ever forget it.
So, I do a lot of playing around on the computer and somehow it makes me feel like I am contributing to something.

Sorry for going on and on, but I feel one of us is misunderstood.

And even if I broke it, I still have the installation disk and am used to doing clean installs. It just takes me a little bit longer than it might take your average Joe.

And most of all, I hope I am not offending you as that is not my intent. My intent is just to clarify the situation.
Now, I have received about 15 lucid-changes email and I am going to go get some updates.

---

### Post by ranch hand on 2010-04-14
Synaptic is a great source of information.  If you wonder what in flinderation does that oacjage do just look it up there and it will tell you.

---

### Post by Cavsfan on 2010-04-15
Running on the new kernel 21! Had some trouble with ttf-indic-fonts-core, so I completely removed it and then installed it and then it was good.
There are currently 3 packages held back - evolution-data-server-common initramfs-tools python-speechd

Don't let that previous post fool you, I am still dumb as a rock about this stuff, but I am trying my best and what more can you ask of someone?

---

### Post by Payteer on 2010-04-15
Well said,  anyway, I have found this post very interesting and I am not a IT person, but I do like to know what is going on with my system.  Anyway, this post has been very informative about Partial Upgrades.  One that has been held back however is Wine 1.2 and also the Kernal upgrades.  I am not going to do the Kernal upgrades until all are finished, but, I can not understand why Wine 1.2.

---

### Post by ranch hand on 2010-04-15
If you would go to synaptic and click to mark the upgrades one at a time you would find why they were held back.

You need to click on the "status" option in the bottom left of the screen to see the listing for "installed upgradable".

---

### Post by arpanaut on 2010-04-15
> **Payteer said:**
> One that has been held back however is Wine 1.2 and also the Kernal upgrades.  I am not going to do the Kernal upgrades until all are finished, but, I can not understand why Wine 1.2.

Probably some dependency issue, which could be determined if you dig for it.

BUT:

Ours is not to question WHY, 
but to DO and DIE  <in the case of doing a partial>
or LIVE and FLY <in the case of choosing NOT>

Patience is a Virtue... :biggrin:

---

### Post by Cavsfan on 2010-04-15
OK, as of this second I am completely up to date! Nothing held back, etc. etc.

Everything looks good so far. Lucid owns![COLOR=Red]
[/COLOR]

---

### Post by ranch hand on 2010-04-15
Always check the stickies;

[http://ubuntuforums.org/showthread.php?t=1455097](http://ubuntuforums.org/showthread.php?t=1455097)

---

### Post by tokyobadger on 2010-04-16
> **Cavsfan said:**
> OK, as of this second I am completely up to date! Nothing held back, etc. etc.

Everything looks good so far. Lucid owns![COLOR=Red]
[/COLOR]
really - I still have (since yesterday) 14 packages that are 'greyed out' including the kernel-related ones, wine-1.2 as mentioned above, as well as a bunch of open-office packages - I'm on amd64 - maybe this is the difference?

---

### Post by ELD on 2010-04-16
> **tokyobadger said:**
> really - I still have (since yesterday) 14 packages that are 'greyed out' including the kernel-related ones, wine-1.2 as mentioned above, as well as a bunch of open-office packages - I'm on amd64 - maybe this is the difference?

Exactly same for me, been like it since i checked yesterday i have the same packages greyed out as you mate, i'm sure in a day or two it will be sorted though.

---

### Post by tokyobadger on 2010-04-16
@ELD: I'm fine with waiting, I was just curious as to how Cavsfan managed to be completely updated, but appreciate the confirmation

---

### Post by Cavsfan on 2010-04-16
> **ranch hand said:**
> Always check the stickies;

[http://ubuntuforums.org/showthread.php?t=1455097](http://ubuntuforums.org/showthread.php?t=1455097)


Thanks a lot! I thought I was off topic and looked in Lucid Lynx Testing and Discussion and found it. 
Must have been about the same time you posted this! 
I was getting off for the day. I just got on and got it fixed.

tokyobadger and ELD,
I don't have a clue as to why my system is up to date and your's is not.
I posted that last night and this morning I seen more emails from Lucid Changes and just got the latest updates.

I just checked Update Manager and it lists initramfs-tools and it's grayed out.

But, if you have been following this thread, you'd know that I don't use Update Manager except to see if there are any updates.
I use these three commands provided to me by Ranch Hand:
"sudo apt-get update" 
"sudo apt-get upgrade"
"sudo apt-get dist-upgrade"

If Update Manager mentions "Partial Update" or the output of the 2nd command says 
it is going to remove something and nothing is going to replace it I leave it alone.
I come back later and check again.

Other than that I don't know what to tell you.

---

### Post by Cavsfan on 2010-04-16
I don't use wine and I am on 64 bit also as you can see from my sig.

---

### Post by tokyobadger on 2010-04-16
@Cavsfan: thanks for clarifying, I was just curious; this is the first time I stuck with any version of ubuntu more than 3 days and I've committed to a 'vanilla' experience especially during the testing cycle and I'm just trying to understand what's going on

---

### Post by Cavsfan on 2010-04-16
> **tokyobadger said:**
> @Cavsfan: thanks for clarifying, I was just curious; this is the first time I stuck with any version of ubuntu more than 3 days and I've committed to a 'vanilla' experience especially during the testing cycle and I'm just trying to understand what's going on

You are most welcome! :) I just went to Update Manager and still the single update I mentioned above is grayed out.

I could not begin to tell you why mine is different, but I know Lucid is definitely going to rock!

---

### Post by Cavsfan on 2010-04-16
You should be able to get all of the updates now. I just did and for some reason I got the kernel 21 again.
So, I can understand why it was being questioned that I was on 21.
I looked in Update Manager and there was a gray exclamation mark on the 21 kernel parts.
When I entered "sudo uname -a" it said I was using 21, but anyway everything should go smooth with the updates now. 

I guess leave it alone if it says "partial" though; mine did not.

Best of luck to you!

---

### Post by 23meg on 2010-04-16
> **Cavsfan said:**
> 23meg, don't worry, I am not as dumb as I apparently led you to believe.

I wasn't implying that you're dumb, or anything of the sort; I'm sorry if it came across that way. I wasn't even referring to *you* in person, but anyone who follows the practice, even though my phrasing and the fact that I quoted you rightly led you to interpret my reply that way.

It's good to know that *you're* on top of things and know your way around package managers, changelogs and Lucid-changes, but as you'll note from many replies to this thread, and the many redundant threads started by people who don't seem to have read this thread, not everybody is. I believe we need to get much better at having people follow good testing practices, hence my ending up being a bit verbose about this matter at times.

---

### Post by ranch hand on 2010-04-16
> **23meg said:**
> I wasn't implying that you're dumb, or anything of the sort; I'm sorry if it came across that way. I wasn't even referring to *you* in person, but anyone who follows the practice, even though my phrasing and the fact that I quoted you rightly led you to interpret my reply that way.

It's good to know that *you're* on top of things and know your way around package managers, changelogs and Lucid-changes, but as you'll note from many replies to this thread, and the many redundant threads started by people who don't seem to have read this thread, not everybody is. I believe we need to get much better at having people follow good testing practices, hence my ending up being a bit verbose about this matter at times.
And taking quite a bit of abuse if I remember last testing round.

---

### Post by ELD on 2010-04-17
Well mine happily still offering only a partial upgrade with the kernel updates greyed out, guess i will wait another few days :)

---

### Post by Cavsfan on 2010-04-17
> **23meg said:**
> I wasn't implying that you're dumb, or anything of the sort; I'm sorry if it came across that way. I wasn't even referring to *you* in person, but anyone who follows the practice, even though my phrasing and the fact that I quoted you rightly led you to interpret my reply that way.

It's good to know that *you're* on top of things and know your way around package managers, changelogs and Lucid-changes, but as you'll note from many replies to this thread, and the many redundant threads started by people who don't seem to have read this thread, not everybody is. I believe we need to get much better at having people follow good testing practices, hence my ending up being a bit verbose about this matter at times.

I can really understand what you are saying though. If one doesn't watch, they could really mess their system up.  
I have been carefully about what is being installed, upgraded, removed, etc. during this time.
Thanks for the reply!  :)

---

### Post by Khakilang on 2010-04-18
Oops! I did a partial upgrade and the line broke I install update again. Now I don't know what I miss. But I can always re install when the stable version is available. Lucky for me this is just a test machine. Thanks for the info.

---

### Post by Cavsfan on 2010-04-18
Anyone getting an error in Update Manager when it gets to file 43 of 45 loading?
Mine has gotten a timeout error all day on [http://packages.medibuntu.org/dists/lucid](http://packages.medibuntu.org/dists/lucid)

I am holding off on updates until I can get them all.

---

### Post by ranch hand on 2010-04-18
Seems to be a problem with the medibuntu repo.  I ran my upgrades from apt and had the same problem.  Does not adversely effect the OS, just won't upgrade any restricted stuff you may have on board.

---

### Post by Cavsfan on 2010-04-18
> **ranch hand said:**
> Seems to be a problem with the medibuntu repo.  I ran my upgrades from apt and had the same problem.  Does not adversely effect the OS, just won't upgrade any restricted stuff you may have on board.

Thanks Ranch Hand! 
I guess I'll go ahead and update and just wait for the rest as I am sure it will be fine tomorrow!

---

### Post by Stason on 2010-04-19
I am stuck at Beta 1 at the moment, since aptitude safe-upgrade gives me unbootable system for now. Given that the final is pretty soon, what would be the proper way for me to upgrade to final? Do I just wait until 29th April, make sure that there is no "partial upgrade" warning and just hit upgrade in upgrade manager?

---

### Post by popat007 on 2010-04-19
For some legal reason Medibuntu repository is down so that error may appear.you can change the source of medibuntu repo. to 
> deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) lucid free non-free
hope that solves the prob.

---

### Post by ranch hand on 2010-04-19
> **popat007 said:**
> For some legal reason Medibuntu repository is down so that error may appear.you can change the source of medibuntu repo. to 

hope that solves the prob.
Thanks, I'll do just that.

---

### Post by ELD on 2010-04-20
Can anyone shed light as to why i am still getting only partial upgrade, some open office and kernel updates are holding it back as well as python-uno.

Been like it for me since last week now.

---

### Post by ranch hand on 2010-04-20
If you go to synaptic, a real package manager, and click on status (lower left on left pane) you will get in the upper left pane a list.  That list will include "Installed (upgradable)".  Click on that.

The upper main pane will now display all upgradable packages.  Click on "Mark All Upgrades".  Hit Apply.  This will give you a box that will actually tell you what is going to be done as far as updates, removals, installations.  You have the opportunity to cancel.

This may leave some still held back.  Click on them individually and mark to update.  This will probably tell you why it is held back and this is generally that things are not all there.

The reason that your kernels are held back, as has been explained many times, is that you are upgrading 3 packages and installing 3 more.  The three more cause the call for a partial upgrade just as removals do.

Only in synaptic do you get a listing of installs and removals so that you can tell if a removal is balanced with the installation of a replacement.

Basically Update Mangler is for people who will not or can not read and do not want to be bothered by thought.  If you are burdened by thought and can and will read but want a gui to update with, use synaptic.

---

### Post by ELD on 2010-04-20
Okay well as per your adviced i used synaptic, it only wanted to remove ttf-tahoma-replacement which is just a font the rest was normal, upgrade/install new so i am going ahead with it.

---

### Post by Cavsfan on 2010-04-21
Is any one else not getting any updates for the past 2 days? I have seen emails about Lucid Changes and software that was approved, but nothing is ever available.

Also, the change for the  Medibuntu repository went in Software Sources on the Other Software tab correct?

Thanks! :smile:

---

### Post by ranch hand on 2010-04-21
Final freeze.  We will see some after the RC probably but we really should not have many more before the final release.

[http://ubuntuforums.org/showthread.php?t=1304172](http://ubuntuforums.org/showthread.php?t=1304172)

Read the stickies.  It is what they are there for.

I like this one better;

[https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule)

---

### Post by Cavsfan on 2010-04-21
> **ranch hand said:**
> Final freeze.  We will see some after the RC probably but we really should not have many more before the final release.

[http://ubuntuforums.org/showthread.php?t=1304172](http://ubuntuforums.org/showthread.php?t=1304172)

Read the stickies.  It is what they are there for.

I like this one better;

[https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule)

Yes, I had seen where April 15th was the final freeze, but I still got updates for a couple of days later. And since I kept getting the Lucid-changes Digest emails just like before, I figured there would be updates.

I have been reading the stickies though and looking at a lot of other stuff too.
Thanks!

---

### Post by ranch hand on 2010-04-21
The wiki schedule has links for things like the final freeze that give a little more info on them.  I fine it very handy.

---

### Post by Cavsfan on 2010-04-21
> **ranch hand said:**
> The wiki schedule has links for things like the final freeze that give a little more info on them.  I fine it very handy.

I agree. Looks good. So, I guess now we just wait right?

---

### Post by Cavsfan on 2010-04-22
What happened to those temporary Medibuntu repositories?
I am getting error while updating with "sudo apt-get update"

(Never mind - I see these went back to normal)

---

