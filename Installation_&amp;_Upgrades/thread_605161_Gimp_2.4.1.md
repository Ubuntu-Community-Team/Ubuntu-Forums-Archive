---
title: "Gimp 2.4.1"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Liliitha on 2007-11-06
I have tried to install the new GIMP but the directions are a little sketchy and some things are not turning out right.  First I configure the program and then I just type make and it says I need to select something to "make".  Well I have looked in the folder and have tried a number of times.  Just what is it I am supposed to be "make"ing?  I used a .deb file and this critical error comes up saying > Error: Dependency is not satisfiable: gimp-data  Can anyone help me on this?

---

### Post by tubasoldier on 2007-11-06
you have to compile the gimp-data package before you compile the gimp package. 

Why not just use the one in the repositories?
```
sudo apt-get install gimp
```

---

### Post by Liliitha on 2007-11-06
Strangely it doesn't work...

> gaurdian@Box:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gimp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gimp-data
E: Package gimp has no installation candidate
gaurdian@Box:~$ 


---

### Post by Liliitha on 2007-11-06
Does anyone have an idea of what is going on?  Please help.

---

### Post by rsambuca on 2007-11-06
Your repositories are messed up.  Open a terminal and post the output of ```
cat /etc/apt/sources.list
```

EDIT:  and quit bumping your posts so quickly!  If you need immediate help, try the IRC channels!

---

### Post by Liliitha on 2007-11-06
> **rsambuca said:**
> Your repositories are messed up.  Open a terminal and post the output of ```
cat /etc/apt/sources.list
```

EDIT:  and quit bumping your posts so quickly!  If you need immediate help, try the IRC channels!

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse restricted universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse


This is what came out.  The IRC isn't working.  When I try to go to a channel it says "SNAC threw error: BUSTED SNAC PAYLOAD

---

### Post by rsambuca on 2007-11-06
I think you have your repositories messed up a bit.  I would just make a new sources.list using[ this website here]("http://www.ubuntu-nl.org/source-o-matic/").

Also, it appears you are obviously using Feisty, so the gimp version will be 2.2 anyways.  If you really need 2.4, you might be better off just upgrading your ubuntu to the newest version - 7.10 Gutsy Gibbon.  It has gimp 2.4 installed by default.

---

### Post by Liliitha on 2007-11-06
Is there a way to upgrade Ubuntu to 7.10 off 7.4 or do I make another cd to overwrite it?

---

### Post by rsambuca on 2007-11-06
If you have not used any outside repositories or compiled programs from source, then you may be OK just upgrading, rather than a complete re-install.  First backup your sensitive data just in-case, and then follow the[ upgrade instructions here]("https://help.ubuntu.com/community/GutsyUpgrades").

---

### Post by Liliitha on 2007-11-06
The box that is supposedly supposed to appear saying *Upgrade to gusty gibbon* does not appear.   All that appears is an empty chart saying I have upgraded everything.

---

### Post by rsambuca on 2007-11-06
It must be because your sources.list is messed up.  Follow the instructions from the link on post#7 to fix your repositories.  You should be able to upgrade after that.

---

### Post by meho_r on 2007-11-06
> **rsambuca said:**
> I think you have your repositories messed up a bit.  I would just make a new sources.list using[ this website here]("http://www.ubuntu-nl.org/source-o-matic/").

Also, it appears you are obviously using Feisty, so the gimp version will be 2.2 anyways.  If you really need 2.4, you might be better off just upgrading your ubuntu to the newest version - 7.10 Gutsy Gibbon.  It has gimp 2.4 installed by default.

In fact, 2.4rc3, not 2.4 final. GIMP 2.4.1 is out, but still no updates in repos, even not to 2.4 :(

---

### Post by rsambuca on 2007-11-06
> **meho_r said:**
> In fact, 2.4rc3, not 2.4 final. GIMP 2.4.1 is out, but still no updates in repos, even not to 2.4 :(

Yeah I know, but I bet you can't tell the difference.

---

### Post by meho_r on 2007-11-06
Most likely cannot, but it'll be nice to have final version though...

---

### Post by rsambuca on 2007-11-06
> **meho_r said:**
> Most likely cannot, but it'll be nice to have final version though...

I don't understand why people get hung up on version numbers.

---

### Post by meho_r on 2007-11-07
What do you think why do version numbers exist?

---

### Post by rsambuca on 2007-11-07
Tell me this then, what exactly is it in 2.4.1 that you need? My point is that most people just want the latest version number eventhough the features they use could be done with a 3 year old program.

---

### Post by meho_r on 2007-11-07
If I can choose between GIMP rc3 and 2.4.1 (and I can), I'll pick 2.4.1. Simple :) 

Sorry for this discussion.

---

### Post by rsambuca on 2007-11-07
> **meho_r said:**
> If I can choose between GIMP rc3 and 2.4.1 (and I can), I'll pick 2.4.1. Simple :) 

Sorry for this discussion.

Well of course - so would anyone!  That is not what I asked.  I asked you what is in 2.4.1 that you do not have in 2.4rc3?  I am guessing that like the majority, there is no new feature in 2.4.1 that you would personally use, so why make a fuss?

---

### Post by julian67 on 2007-11-07
> **rsambuca said:**
> ....... what is in 2.4.1 that you do not have in 2.4rc3?

bugfixes ;-)

[QUOTE=gimp.org]GIMP 2.4.1 is a bug-fix release in the stable 2.4 series. It fixes problems that were discovered after the 2.4.0 release. Please see the NEWS file for details...........................

...........

Changes in GIMP 2.4.1
=====================

- fixed a minor display rendering problem
- improved the workaround for broken graphics card drivers (bug #421466)
- fixed a crash with broken scripts and plug-ins (bug #490055)
- fixed potential syntax error in configure script (bug #490068)
- fixed parsing of floating point numbers in Script-Fu (bug #490198)
- fixed potential crash when converting an indexed image to RGB (bug #490048)
- update the histogram while doing color corrections (bug #490182)
- fixed another crash with broken plug-ins (bug #490617)
- fixed problems on Win32 when GIMP is installed into a non-ASCII path
- fixed handling of truncated ASCII PNM files (bug #490827)
- make sure that there's always a cursor, even for small brushes (bug #491272)
- fixed line-drawing with a tablet and the Shift key (bug #164240)
- added code to use the system monitor profile on OS X (bug #488170)
- show changes to the rounded corners in the Rectangle Select tool (bug #418284)
- reduced rounding errors in the display render routines (bug #490785)
- translation updates (ca, de, et, lt, mk, pa, sv)
[/QUOTE]

---

### Post by rsambuca on 2007-11-07
Yeah, I can read, but you guys obviously just aren't getting my point.

---

### Post by roderick on 2007-11-07
I think the main question is "what is supported". If you need support from the GIMP dev's and they are not willing to support 2.4.0RC3, then, yes it makes sense that you need 2.4.1 as they will likely say "upgrade" to fix the issue.

However, if there is support, and the app works well, then I agree, no reason to have an immediate upgrade just because a new release was put out.

I do believe, that if a release is put out, and it is strictly a bug fix, it should be added to the repos for users to update. If new features were added, then, maybe it needs time to settle first.

Under Gentoo, this philosophy is quite easy, as you have stable, unstable and masked package, which the user can control. Not sure if a similar functionality could exist here in Ubuntu, without causing additional pain :)

---

### Post by rsambuca on 2007-11-07
Gentoo is a rolling release distro.  Ubuntu is not.

---

### Post by yabbadabbadont on 2007-11-07
> **roderick said:**
> Under Gentoo, this philosophy is quite easy, as you have stable, unstable and masked package, which the user can control.

You left out the "local portage overlay" option for the level beyond "hard masked".  :twisted:

It is also useful for when the devs are slow to bump the version in the official portage tree.

---

### Post by meho_r on 2007-11-08
> **rsambuca said:**
> Well of course - so would anyone!  That is not what I asked.  I asked you what is in 2.4.1 that you do not have in 2.4rc3?  I am guessing that like the majority, there is no new feature in 2.4.1 that you would personally use, so why make a fuss?

Well, I notice slight difference in splash screen ;) Seriously -- there's no need for new feature (and maybe there are some, I don't know, think that I should try 2.4.1. first to say), I'd just like to see repos updated so I don't need to hunt .debs. GIMP is one of the most important Linux apps (in my opinion) and it should be regularly updated in repos. OK?

---

### Post by julian67 on 2007-11-08
I have 2.4rc3 on Xubuntu 7.04 and it has some real problems. 2.4 is massively improved over 2.2. with improved tools, new tools, *extremely important new capability* like cmyk and icc profile so there are plenty of things you can do that were either not possible or very difficult in earlier versions. The bug fix release is not just some trivial tidying up, it addresses some BIG bugs.  So neither the change from 2.2 to 2.4 or from 2.4 to 2.4.1 can really be considered trivial. One is a major version change (**after several years!!!**) and the other fixes real and important problems.

---

### Post by measekite on 2007-11-09
> **rsambuca said:**
> Your repositories are messed up.  Open a terminal and post the output of ```
cat /etc/apt/sources.list
```EDIT:  and quit bumping your posts so quickly!  If you need immediate help, try the IRC channels!

I too am interested in the new features of Gimp 2.4. I am using Feisty and do not want to upgrade for the next few months since I am new to Linux and have just spent considerable time finding my way around and getting all of my printers and scanner to work as well as Linux wireless as well.

I have read that many Feisty users have a desire to go to Gimp 2.4 due to the new features.  It seems that Canonical has decided not to update the repositories for Feisty.  It is not just Gimp but Open Office, Thunderbird, Firefox and others.

Do you think that this policy will change.  If you take Firefox the Help>CheckforUpdates is even grayed out.  I would think that will all of the Ubuntu support Canonical would see fit to keep their repositories current.

Any idea what happens with Suse, Red Hat or Mandriva (non commercial versions)?

---

### Post by rsambuca on 2007-11-09
> **measekite said:**
> I have read that many Feisty users have a desire to go to Gimp 2.4 due to the new features.  It seems that Canonical has decided not to update the repositories for Feisty.  It is not just Gimp but Open Office, Thunderbird, Firefox and others.

Do you think that this policy will change.  If you take Firefox the Help>CheckforUpdates is even grayed out.  I would think that will all of the Ubuntu support Canonical would see fit to keep their repositories current.

Any idea what happens with Suse, Red Hat or Mandriva (non commercial versions)?

I think you don't really understand how Ubuntu works.  The developers create a snapshot of the Debian unstable repositories every six months.  The Ubuntu developers then work for six months fixing bugs, integrating their own packages, integrate the newest Gnome desktop, and then release it as one big package, the lastest being 7.10, Gutsy Gibbon.

After this, the process starts over.  ie a new snapshot of the Debian unstable repos is taken...
In the meantime, the Ubuntu developers are also integrating bug fixes and security patches into the packages of the older versions of ubuntu.  Therefore, right now they continue to submit updates for Dapper, Edgy, Feisty, and Gutsy.  For the most part, the updates are security patches and bug fixes.  They are not full upgrades to new versions of software.

Simply put, if you insist on having the newest versions of software and can not wait for a maximum of 6 months, then you will either have to compile the programs from source, or find a .deb package.

Basically, if you really want the latest and greatest immediately, then Ubuntu probably isn't the best distro for you to be using.  You would be much happier with a "Rolling Release" Distro, where all the packages are upgraded on a continuous basis.  You get the newer versions quicker, but sometimes you also have to deal with the associated bugs that come with it.  Some rolling release distros that you might like are:  Debian Sid (this is what Ubuntu is derived from), Foresight Linux, Gentoo, or Arch linux, to name a few.  Please do not criticize Ubuntu for doing what it was intended to do.  The developers have chosen to strike a balance between cutting edge and stability.  If you don't like their choice, there are a myriad of others.

---

### Post by cmost on 2007-11-09
> **rsambuca said:**
> I think you have your repositories messed up a bit.  I would just make a new sources.list using[ this website here]("http://www.ubuntu-nl.org/source-o-matic/").

Also, it appears you are obviously using Feisty, so the gimp version will be 2.2 anyways.  If you really need 2.4, you might be better off just upgrading your ubuntu to the newest version - 7.10 Gutsy Gibbon.  It has gimp 2.4 installed by default.

Why is it that the answer to someone requesting a new version of a package is to "upgrade to the  new version of Ubuntu..."  It seems utterly ridiculous to me that I have to upgrade my entire OS, reinstall all my custom programs and settings just to get a single package.  This is where Ubuntu fails, in my opinion.  Sure, you might retort that Ubuntu offers an "easy upgrade" path from one version to the next.  In all honesty, this process isn't bulletproof and many, many users hose their systems attempting this.

I'm an experienced Linux user and I know how to compile programs.  With pure Debian, adding missing libraries, etc. that some programs are dependent on for compilation is easy.  Not so with Ubuntu because each version's repositories are frozen (unless by some miracle an updated package winds up in Backports, which is rare.)

This guy wants to compile the latest Gimp on Feisty and he shouldn't hvae to jump through myriad of hoops to do so.  Ubuntu might be touted as the "Linux for Human Beings" but that's only if those humans are happy with the stock installation and the specific set of packages present in a particular versions' repository.  Advanced users should seek another distribution.

:confused:

---

### Post by rsambuca on 2007-11-09
> **cmost said:**
> This guy wants to compile the latest Gimp on Feisty and he shouldn't hvae to jump through myriad of hoops to do so.  Ubuntu might be touted as the "Linux for Human Beings" but that's only if those humans are happy with the stock installation and the specific set of packages present in a particular versions' repository.  Advanced users should seek another distribution.

:confused:

I basically agree with your thoughts on stock installations, but I don't think a user's level of expertise has anything to do with it.  In fact, "advanced users" are more able to find workarounds, so Ubuntu is somewhat easier for them if they want something outside the "stock installation".

---

### Post by cmost on 2007-11-09
According to my research, here's what's required to get Gimp 2.4.x to compile on Ubuntu 7.04 (which is only six months old.)  By comparison, the Windows port will work on Windows 98, 2000, XP, or Vista.  Windows 98 has been out since the Fall of 1997.

Note:  Details on the following instructions are available here:  [https://help.ubuntu.com/community/GIMP2.4-on-Feisty](https://help.ubuntu.com/community/GIMP2.4-on-Feisty)  (This guy is just as frustrated as the rest of us of the lack of Feisty support now that precious Gutsy has been released.)

1.  You have to download the source tarball from Gimp's home page.  Got it. (so far so good.)
2.  Untar it somewhere in your home folder.  Check.
3.  Next, grab the dependencies (which are helpfully provided after a simple Google search.

$sudo apt-get install build-essential subversion make gcc libglib2.0-dev libgtk2.0-dev intltool automake1.9 libtool gtk-doc-tools g++-3.3 libart-2.0-dev libtiff4-dev libexif-dev libxmu-dev libjpeg62-dev libmng-dev libpng12-dev librsvg2-dev libgutenprintui2-dev libaa1-dev python2.5-dev python-gtk2-dev libaa1-dev libxpm-dev libwmf-bin libwmf-dev libgtkhtml2-dev

4.  Once the dependencies and required build packages are installed, it should be a simple ./configure followed by 'make' and then 'sudo make install'.  But not this time.  Since Gimp has a hard coded dependency on GTK+ version >=2.10.13; which Feisty doesn't have in its repositories, nor in the backports (what a shock) you have to compile your own.

5.  Download the source package for GTK+ 2.10.13.  Oops, another problem.  Now you need the updated Pango and Glib libraries or GTK+ 2.10.13 won't compile.  So, you get those too (from here [ftp://ftp.gtk.org/pub/](ftp://ftp.gtk.org/pub/)) and go through the laborious process of compiling them.

6.  After a lot of wasted time tracking down and Jerry-rigging libraries and dependencies, we're finally ready for the standard:
./configure
make
sudo make install

Is this worth it?  I think not!  I doubt even advanced users are willing to go through this nonsense just to install an updated package (and probably screw up other packages that depended on the older versions of files.)

Advanced users are going to go running to Debian Sid, or Arch Linux, or even Gentoo (i.e., rolling distributions.)  Which is where my next stop will be if Ubuntu can't get it together and recognize that they need to stop cramming every new feature they can into a release and start fixing bugs, adjustting the repositories so they're more flexible and start catering to their entire user base.  Oh, and getting rid of the hideous brown wouldn't hurt either.

---

### Post by rsambuca on 2007-11-09
> **cmost said:**
> According to my research, here's what's required to get Gimp 2.4.x to compile on Ubuntu 7.04 (which is only six months old.)  By comparison, the Windows port will work on Windows 98, 2000, XP, or Vista.  Windows 98 has been out since the Fall of 1997.

Note:  Details on the following instructions are available here:  [https://help.ubuntu.com/community/GIMP2.4-on-Feisty](https://help.ubuntu.com/community/GIMP2.4-on-Feisty)  (This guy is just as frustrated as the rest of us of the lack of Feisty support now that precious Gutsy has been released.)

1.  You have to download the source tarball from Gimp's home page.  Got it. (so far so good.)
2.  Untar it somewhere in your home folder.  Check.
3.  Next, grab the dependencies (which are helpfully provided after a simple Google search.

$sudo apt-get install build-essential subversion make gcc libglib2.0-dev libgtk2.0-dev intltool automake1.9 libtool gtk-doc-tools g++-3.3 libart-2.0-dev libtiff4-dev libexif-dev libxmu-dev libjpeg62-dev libmng-dev libpng12-dev librsvg2-dev libgutenprintui2-dev libaa1-dev python2.5-dev python-gtk2-dev libaa1-dev libxpm-dev libwmf-bin libwmf-dev libgtkhtml2-dev

4.  Once the dependencies and required build packages are installed, it should be a simple ./configure followed by 'make' and then 'sudo make install'.  But not this time.  Since Gimp has a hard coded dependency on GTK+ version >=2.10.13; which Feisty doesn't have in its repositories, nor in the backports (what a shock) you have to compile your own.

5.  Download the source package for GTK+ 2.10.13.  Oops, another problem.  Now you need the updated Pango and Glib libraries or GTK+ 2.10.13 won't compile.  So, you get those too (from here [ftp://ftp.gtk.org/pub/](ftp://ftp.gtk.org/pub/)) and go through the laborious process of compiling them.

6.  After a lot of wasted time tracking down and Jerry-rigging libraries and dependencies, we're finally ready for the standard:
./configure
make
sudo make install

Is this worth it?  I think not!  I doubt even advanced users are willing to go through this nonsense just to install an updated package (and probably screw up other packages that depended on the older versions of files.)

Advanced users are going to go running to Debian Sid, or Arch Linux, or even Gentoo (i.e., rolling distributions.)  Which is where my next stop will be if Ubuntu can't get it together and recognize that they need to stop cramming every new feature they can into a release and start fixing bugs, adjustting the repositories so they're more flexible and start catering to their entire user base.  Oh, and getting rid of the hideous brown wouldn't hurt either.


To be completely honest, I don't think that Ubuntu is the best distro for you.  I don't say that to be mean or to put you down in any way.  I just think that with your expectations, you will be much happier with another distro.  

The beauty of linux is that there is a linux flavour for everyone.  There is no shame in trying others and moving on if you find one you like.  I strongly encourage you to test other distros as I am sure you will be happier!

Good luck.

---

### Post by yabbadabbadont on 2007-11-09
If you have an extra partition that you can spare, you should really consider installing Gentoo, Arch, or Sabayon onto it.  That way you could dual-boot until you find a distribution that meets your needs.  Plus, at least with Gentoo, you can do the installation in a chroot while booted in Ubuntu.  That way you will have a full system to use while the installation is proceeding.

---

### Post by eeried on 2007-11-11
hello,

Ive read the whole thread , and I'm well aware of the Ubuntu policy (similar to Debian stable) to stick to a version. For instance we have Firefox 2 on Gutsy and Gutsy won't upgrade from FF2 to Firefox3.

This version of the GIMP, however, is a bit different as it it a Release Candidate. Of course Gutsy won't upgrade to GIMP 2.5 or GIMP3 or whatever but I would expect GIMP2.4 to upgrade inside the 2.4 series, that is  to 2.4.1, etc., even if it doesn't immediately.

Won't it be the case??

---

### Post by julian67 on 2007-11-11
There are updated versions of certain packages available via backports and such a unique and powerful program as Gimp would be an obvious candidate.  There is a deb of 2.4rc3 for 7.04 from getdeb but it has plenty of problems (no complaints, it's rc) so it certainly is possible for a backported version of 2.4 or 2.4.1 to be made available to Feisty users.

---

### Post by eeried on 2007-11-12
> There is a deb of 2.4rc3 for 7.04 

So let's hope those who have upgraded to Gutsy will eventually get GIMP 2.4.1 and the  2.4.x later on.

GIMP 2.4 even in its rc version is great. For instance, the crop tool is fantastic now. GIMP is easier both for power users and beginners, which is good news for libre software.

---

### Post by julian67 on 2007-11-12
> **eeried said:**
> So let's hope those who have upgraded to Gutsy will eventually get GIMP 2.4.1 and the  2.4.x later on.

GIMP 2.4 even in its rc version is great. For instance, the crop tool is fantastic now. GIMP is easier both for power users and beginners, which is good news for libre software.

Yes it's a huge improvement but the rc deb (from gimpusers) has problems, such as it loses all exif data on 7.04 and it doesn't work well with dcraw so opening my RAWs has to be done in ufraw.

---

### Post by eeried on 2007-11-12
So Feisty users are happy with their stable GIMP and  Gutsy users have to wait for  2.4.1.deb with bated breath -- until they choke for a breath of fresh air and install the 2.2 version.

I'm not sure how to make a DEB file from the file available on the GIMP web site but I would imagine someone will make one: howto: 
[http://www.davehayes.org/2007/11/01/howto-install-the-gimp-241-on-ubuntu-710-gutsy/](http://www.davehayes.org/2007/11/01/howto-install-the-gimp-241-on-ubuntu-710-gutsy/)
> The [Gutsy] Ubuntu package contains a patch that fixes a bug, says davehayes :-)

PS: if you don't upgrade to Debian Sid you won't get GIMP 2.4.1 either. Ubuntu is like Debian Etch: it doesn't move from one version of a software to the next. Some people may choose to go over to Sid but  you may end up with a rather unstable system and with unmet dependencies. Ubuntu is supposedly stable, though Gutsy is rather raw -- it is becoming a tradition that October releases are rather edgy.

---

### Post by trig on 2008-02-16
what is the update command for gimp...sudo apt-get update gimp

---

### Post by trig on 2008-02-16
sudo apt-get upgrade gimp
to get the latest version of gimp that i can find out

---

### Post by eeried on 2008-02-18
Hello,

You shouldn't have to do anything if you're on Gusty, apart from clikcing on the notification icon toi get the latest updates/upgrades

---

### Post by julian67 on 2008-02-18
I just uninstalled the repo's gimp and installed the latest version from getdeb. It's 2.4.4

---

