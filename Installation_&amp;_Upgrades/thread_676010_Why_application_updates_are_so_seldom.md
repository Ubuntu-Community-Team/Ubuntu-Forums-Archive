---
title: "Why application updates are so seldom?"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by arigram on 2008-01-23
Why indeed, applications in Ubuntu don't get updated when there are major versions releases out for quite some time?
For example, two of the main FOSS applications that come with Ubuntu, Open Office and Rhythmbox, both have released updated versions for quite some time. Both cause minor yet annoying problems and their changlogs list many bug fixes that are well needed.
I tried installing Open Office 2.3.1 from the deb packages from the website but they break other dependencies and libraries and freak out the update manager. I have tried really hard but haven't been able to get Rhythmbox 0.11.4 to compile (stuck in dependency hell).

Do they need further Ubuntu polish? Why updates happen so rarely?

---

### Post by Pandemic187 on 2008-01-23
I could be wrong, but I believe program updates are focused into updates of the operating system itself. So, OpenOffice.org probably won't be updated within the Ubuntu OS until the next version, 8.04. It may seem like these programs are updated infrequently then, but really, the six-month release cycle that Ubuntu has is pretty timely.

---

### Post by depele on 2008-01-23
In my opinion ubuntu may be a little bit faster with software updates. 

Openoffice, pidgin, amsn, .....

cya

---

### Post by Whiffle on 2008-01-23
> **arigram said:**
> 
I tried installing Open Office 2.3.1 from the deb packages from the website but they break other dependencies and libraries and freak out the update manager. I have tried really hard but haven't been able to get Rhythmbox 0.11.4 to compile (stuck in dependency hell).

Do they need further Ubuntu polish? Why updates happen so rarely?

I think you answered your own question, but did not know it.  If ubuntu put the newest version of every new package available out as soon as it became available, they would have a mess on their hands trying to make sure everything works together as it is supposed to.  Ubuntu will upgrade versions of software with each new release, and spend time before hand making sure that it actually works.  If you want the most up to date version of software, you need to use a distro like Arch that is on a rolling release schedule and tends to have more bleeding edge software.  Gentoo is another one in that category.

---

### Post by mivo on 2008-01-23
There are two types of Linux distros: "timed release distros" like Ubuntu, Fedora, etc, and "rolling release distros" like ArchLinux. The difference between the two is that timed releases come out every x months with a completely new version, and inbetween only put out security and crucial maintenance updates, but not generally new feature versions of applications. The definition of what is and is not a crucial update can differ, though (for exampe, I am unclear why Pidgin isn't getting updated to the latest version). 

Rolling release distros don't really have cyclical releases. They may offer snapshots every so often, but software (both system and application) is updated when new versions are available, so you always have the latest version and never really have to upgrade from one distro version to another distro version.

Both approaches have up and downsides.

In case of Ubuntu, you can often find DEB files of newer versions of apps at [http://www.getdeb.net/](http://www.getdeb.net/) which is really a great resource for those who prefer the "bleeding edge" for some applications. There is also the development version of Hardy, if you are really brave (not recommended). :)

---

### Post by aysiu on 2008-01-23
Updates happen every six months.

---

### Post by arigram on 2008-01-23
I am aware of the six month schedule of Ubuntu, but I am not talking about new and unstable experimental components but about bug fix releases.
Like I mentioned, I have some problems with the main applications of Ubuntu which seem to have been fixed in newer versions already out some time.
Does that mean I have to put up with buggy and crash prone major applications for six months?
Other components and applications do get updated though, often ones that are not essential or even commonly used.
I am aware of GetDeb but being a small project, it doesn't offer timely updates and often focuses more on games and obscure tools than in major applications.

Again, I am talking about bug fixes that make the applications more stable, not revolutionary unstable new features.

---

### Post by aysiu on 2008-01-23
Ubuntu's bug fixing policy is controversial:
[http://ubuntuforums.org/showthread.php?t=671086](http://ubuntuforums.org/showthread.php?t=671086)

---

### Post by Pandemic187 on 2008-01-23
> **mivo said:**
> Both approaches have up and downsides.
For the sake of discussion and perhaps some enlightenment, what could be a downside to a rolling release system? I know this is straying from the purpose of the thread, but I'm curious because I've always been somewhat interested in Arch. I tried installing Arch once though, and I was more or less dumbfounded by the installer.

---

### Post by mivo on 2008-01-23
> **Pandemic187 said:**
> For the sake of discussion and perhaps some enlightenment, what could be a downside to a rolling release system? I know this is straying from the purpose of the thread, but I'm curious because I've always been somewhat interested in Arch. I tried installing Arch once though, and I was more or less dumbfounded by the installer.

Well, the downside of rolling releases is how "bleeding edge" the software and the OS is. It is always the latest stuff, the newest kernel, the most recent drivers, etc, though i.e. Arch also does have a testing repository, but  the chance of something breaking is much higher than with a timed release like Ubuntu that is tested before release (as a whole package, not only its individual parts). Once you have Ubuntu running, you can be relatively sure that no major changes are going to occur until the next version comes out. With a rolling release, updates to the core system happen on a constant basis, so something may break whenever you update. For professional users, or conservative home users (who don't want to tinker), a rolling release is potentially troublesome and undesirable.

Arch is great, though. I use it on my other Linux machine and I haven't had any breakages. Still, I prefer Ubuntu for my production box because I need it for work, so I play it safe (in addition, it's much easier to get help here, since Ubuntu's community is unmatched). Arch is great for learning, though, and if you have time and interest, it's certainly worth a look and can be a rewarding adventure. There is a good [Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") for it.

---

### Post by arigram on 2008-01-24
Since there is an Update Manager, which it does bring updates often, which are system-wide and application-wide, why then, its not used to the fullest?
I mean, part of the attraction of a Linux distro is that it includes all those applications inside and one can add to them and update at will using such fine GUI tools.
If those applications exhibit bugs and they are patched, why don't they get updated in Ubuntu?

Don't get me wrong. I like the set Ubuntu releases. I like to mess with my computer and its great to know there is a stable base to fall back to and to look forwards to when I will format everything and install cleanly,

But some main applications that come with Ubuntu need to be updated because of bugs not new features.

---

### Post by Eck on 2008-01-28
Funny that no one mentioned Debian.  Well, I guess it's time someone did.

You know that Ubuntu is a bug fixed, customized, gui tools added version of Debian Sid (Debian Unstable)?

If you install Debian Testing (Lenny right now until it becomes the next Stable sometime next fall), you will get most of what you are asking for without the worry of having the upgraded packages causing breakage and adding bugs because of being "bleeding edge."  This, because the upstream releases are first used in Sid for a time before being accepted into Lenny when no new bugs are reported, the packages don't break anything else in Lenny, and all install and upgrade properly.  Quite nice!

Debian Testing is sort of a running Release Candidate quality version of Debian.  And, if you're wondering, you can make the Gnome or KDE gui's look like Ubuntu or Kubuntu through themes if that is what you wish.

The adventurous can run a mixed system with both testing and unstable repos active, but with a default release specified in /etc/apt/apt.conf, which sets testing to a 990 apt pin ensuring that only packages a user specifies with an aptitude install -t unstable switch (metapackages don't work, you must specify each dependency of them and so for all intents you accomplish the same thing) and its dependencies get installed and upgraded.  Upgrades for those packages will then come from Unstable, but no others, and when they get accepted into Testing they will from then on come from Testing again.

So even though Lenny has OpenOffice.org 2.1, many install it from the 2.3.1 in Unstable if they really want it.

The safest bet for installing testing is to use an Etch (Stable) DVD1 to install, which gives you the proper specific Kernel for your architecture, choosing just the Standard task and unchecking the Desktop Environment task.  The cd's and net-install only give you a 486 Kernel metapackage and you must then install the K7 or 686 metapackage after installation, then remove the 486 metapackage once you boot into the specific arch's new Kernel.  I just like the DVD because it has all the specific ones and there's no need to bother with it.  

Once up, you login as your user, su - to root, editor /etc/apt/sources.list, change the lines from etch to lenny, add contrib and non-free to the ends of the lines, and add the debian-multimedia.org repo, aptitude update, aptitude dist-upgrade, reboot to your new lenny kernel (without needing to bother to install it as the Etch DVD's linux-image-2.6-k7 automatically installs the latest one from lenny when dist-upgrading), I aptitude purge the older Etch Kernel then, reboot, and run aptitude.  Scroll to the tasks and pick desktop, kde-desktop, and gnome-desktop, (hit plus next to each), hit g, adjust if advised of any dependency issues as needed, and hit g again.  Grab a beer and watch the magic.  Install mesa-utils (stupid that it doesn't do that in the tasks).  Choose which Display Manager you want when it asks (GDM if you want to use Gnome mostly or KDM if you want to use KDE mostly), run dpkg-reconfigure xserver-xorg to be sure you'll get the driver and resolutions you want, shutdown -a -r now, and boot into your fully setup KDE or Gnome Lenny desktop.

For most things it'll be difficult to tell you aren't using Ubuntu, which after all is Debian, but you will have the running distro that is still VERY stable that you desire.  Everyday, you aptitude update, aptitude full-upgrade (full-upgrade replaced dist-upgrade in Lenny).  Be amazed at all the new stuff you get that works great.

If you're in love with Synaptec, those tasks I told you about install that.  Use it once you have your desktop installed with the tasks.  These days apt and Synaptec work about as well as aptitude since they include Recommends by default and track them for uninstalls (at least I think they track them for uninstalls, and if not you can still remove useless junk yourself if you want).

---

### Post by Achetar on 2008-01-28
> **mivo said:**
> ...There is also the development version of Hardy, if you are really brave (not recommended). :)

Actually, I just installed Hardy last night, aside from an easy-to-fix xorg.conf error, everything is working great! I was even able to uninstall KDE4 (I never use it, but Gutsy wouldn't let me uninstall it, something about dependencies). It seems like you would have to be more brave to use something like getdebs.com, since you would have to download a whole mess of .deb files.

---

