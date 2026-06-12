---
title: "Problem upgrading from Kinetic (22.10) to Lunar Lobster"
date: 2023-05-29
forum: Installation &amp; Upgrades
---

### Post by mberg2007 on 2023-05-29
Hi,

I run a pretty vanilla Ubuntu desktop which is currently at 22.10. I've been upgrading the machine since I think 16.x with little to no difficulties, but today when I wanted to go to Lunar Lobster I got this:

```
$ sudo do-release-upgrade 
(bunch of upgrade output omitted)
Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This was likely caused by: 
* Unofficial software packages not provided by Ubuntu 
Please use the tool 'ppa-purge' from the ppa-purge 
package to remove software from a Launchpad PPA and 
try the upgrade again. 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 
```

Now this is strange. I don't have any PPA's enabled. And checking the apt.log also seems to suggest some more serious problems:

```
$ grep Broken /var/log/dist-upgrade/apt.log
Broken gnome-shell-extension-ubuntu-dock:amd64 Depends on gnome-shell:amd64 < 43.1-0ubuntu1 -> 44.0-2ubuntu3 @ii umU > (< 44)
Broken pipewire-audio:amd64 Conflicts on pulseaudio:amd64 < 1:16.1+dfsg1-1ubuntu3.1 -> 1:16.1+dfsg1-2ubuntu3 @ii umU >
Broken nautilus:amd64 Depends on libadwaita-1-0:amd64 < 1.2.0-1ubuntu2 | 1.3.2-0ubuntu1 @ii pumH > (>= 1.3~alpha)
Broken gnome-shell-extension-desktop-icons-ng:amd64 Depends on nautilus:amd64 < 1:43.2-0ubuntu1 | 1:44.0-1ubuntu2 @ii umR > (>= 3.38)
Broken libxapp-gtk3-module:amd64 Breaks on xapp:amd64 < 2.2.15-1 @ii mK Ib > (< 2.4.2-1~)
Broken ubuntu-desktop-minimal:amd64 Depends on gnome-shell-extension-desktop-icons-ng:amd64 < 46-3 | 46+really47.0.2-3 @ii umR >
Broken ubuntu-desktop:amd64 Depends on gnome-shell-extension-desktop-icons-ng:amd64 < 46-3 | 46+really47.0.2-3 @ii umR >
Broken pipewire-alsa:amd64 Conflicts on pulseaudio:amd64 < 1:16.1+dfsg1-1ubuntu3.1 -> 1:16.1+dfsg1-2ubuntu3 @ii umU >
Broken nautilus-share:amd64 Depends on nautilus:amd64 < 1:43.2-0ubuntu1 | 1:44.0-1ubuntu2 @ii umR > (>= 43~rc)
Broken libgs9:amd64 Depends on libgs9-common:amd64 < 9.56.1~dfsg1-0ubuntu3.1 -> 10.0.0~dfsg1-0ubuntu1.1 @ii umU > (= 9.56.1~dfsg1-0ubuntu3.1)
Broken gnome-shell-extension-ubuntu-dock:amd64 Depends on gnome-shell:amd64 < 43.1-0ubuntu1 -> 44.0-2ubuntu3 @ii umU > (< 44)
Broken gnome-shell:amd64 Depends on gnome-shell-common:amd64 < 43.1-0ubuntu1 -> 44.0-2ubuntu3 @ii umU > (= 43.1-0ubuntu1)
Broken libmutter-12-0:amd64 Breaks on gnome-shell:amd64 < 43.1-0ubuntu1 | 44.0-2ubuntu3 @ii umH > (< 44~rc)
Broken gir1.2-mutter-12:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (= 44.0-2ubuntu4.23.04.1)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken gnome-remote-desktop:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 44~)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
Broken mutter-common-bin:amd64 Breaks on mutter:amd64 < 43.0-1ubuntu4 | 44.0-2ubuntu4.23.04.1 @ii umH > (< 44~)
Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)
```

Now before you ask, no I have not installed anything like mutter or any of the other packages reported as broken. Apt-get update also doesn't report any problems at all. I don't have any PPA Launchpads installed, they are all disabled at the moment.

Does anyone know what this is caused by and how I can fix the problem? Also how in the world did my system end up in this state?

-Michael

---

### Post by TheFu on 2023-05-29
Doing only upgrades leaves cruft behind that can confuse the system in the future.  Well, seems the future is today and your system is confused.  I have a few unwritten rules:
[LIST]
[*]Only install LTS releases, unless my hardware is so new that it demands the latest non-LTS.  
[*]Get off non-LTS releases ASAP.
[*]Only upgrade from 1 release to the next once. Next upgrade needs to be a fresh install.  This means cruft gets cleared out every other LTS (at the longest). Additionally, the system doesn't get confused by old subsystems being left behind.  Many subsystems have been swapped out since 16.04.
[*]Always have a know-you-can-100%-restore backup before doing any release upgrade.  Always.  This way, if some thing bad happens, you can restore and try again.
[/LIST]

Take these rules for whatever you like.  Many things have changed over the years.  Unity is gone.  Gnome 2.x has been replaced by 3.x and now 4.x.  Those are huge changes that ripple throughout the entire GUI, including the login manager.

Time for a fresh install.  Backup your data and create a list of packages installed on the box, so you can quickly reinstall them.  **apt-mark showmanual** and **apt-mark showauto** will help with the list.  OTOH, most of those packages don't need to be manually installed, some are deprecated (gone) and a few have changed their config files and data formats to be incompatible with newer releases (bad programmers!).

---

### Post by Impavidus on 2023-05-30
I've had one system that I've upgraded 6.06&#8594;8.04&#8594;10.04&#8594;12.04. It worked, mostly, but there was cruft accumulating. So I made it a fresh install when going to 14.04. That really improved things.

---

### Post by MAFoElffen on 2023-05-31
I have to do a lot of "testing"... And I do this mostly on KVM guests. Some of these include interim releases.

The last time I saw a mess like that, with the default installed packages (like I see there) on a 'do-release-upgrade'... It was because I took a VM guest that I hadn't upgraded to the latest updates before doing (or rather ended up as trying to do) the 'do-release-upgrade' process.

Try 
```

sudo apt update && sudo apt upgrade -y

```
And just ensure that all the upgrades are applied. If it was not up to date and did apply some newer, then, after it finishes, try to do a 'do-release-upgrade' again.

---

### Post by mberg2007 on 2023-05-31
Hello,

Thanks for your feedback. However, I'm obviously not interested in doing a complete reinstall. This defeatist mentality might be common among Windows users, but this is Linux. We can do better.

I have gone through the Gnome upgrades and from X11 to Wayland. My system is not broken because of any of that, it's broken because of something that apt has done to it. This might have happened at any time, be it a dist release, an upgrade or a dist-upgrade.

What I'm looking for is someone who can explain to me in simple terms what this actually means:

Broken mutter:amd64 Depends on libmutter-12-0:amd64 < none | 44.0-2ubuntu4.23.04.1 @un uH > (>= 43.0)

What I'm reading here is that the package "mutter" is broken because it depends on libmutter-12-0. Does that mean I have that installed? Does it mean that the release upgrade intends to install a newer version of libmutter-12-0? What does " < none" mean? Does that mean the upgrade intends to remove libmutter-12-0 which would break mutter? Why the heck would the upgrade want to remove libmutter-12-0 and not replace mutter with a version compatible with whatever it intends to install in stead of libmutter-12-0?

Frankly that log line is so terrible and hopelessly useless it might as well just have read "Hey buddy, something's broken, good luck to you!" except without the good luck part.

I have a different laptop which I have successfully upgraded in precisely the same way. No problems whatsoever. Do you or anyone have any helpful suggestions at all for commands that might be useful in getting to the root cause of this problem?

-Michael

---

### Post by mberg2007 on 2023-05-31
Thanks for your response. I do the apt-update thing regularly and also before do-release-upgrade - in fact that command won't run at all if it determines all updates have not already been applied.

Just did an apt-update and got a new version of tzdata which is nice, but I'm not especially hopeful that this will help resolve my mutter problems.

According to wikipedia, mutter is:

*Mutter is **a portmanteau of Metacity and Clutter**. Mutter can function as a standalone window manager for GNOME-like desktops, and serves as the primary window manager for the GNOME Shell, which is an integral part of GNOME 3. Mutter is extensible with plug-ins, and supports numerous visual effects.*

So I don't think I can just remove it to resolve this problem.

-Michael

---

### Post by helicase on 2023-05-31
You could try
```
apt --fix-broken install
```

---

### Post by TheFu on 2023-05-31
> **mberg2007 said:**
>  
Thanks for your feedback. However, I'm obviously not interested in doing a complete reinstall. This defeatist mentality might be common among Windows users, but this is Linux. We can do better.


As an admin, my job is to avoid surprises.  When I post, I'm trying to provide wisdom, not just type XYZ.  IME, OS release upgrades are often more pain than they are worth.  I did an upgrade from 18.04 to 20.04 and it took 3 hrs.  For the next few weeks, the system was slow, so I ended up doing a reinstall.  It isn't defeatist.  It is a viable option and likely to save time in the long run because of all the issues that will be avoided.

The fresh install for that 20.04 system was 15 minutes. Add in another 15 minutes to restore the data for the system and configs that had been customized previously, then 15 more minutes to reinstall the packages that were really important on the system before the upgrade.  I use **apt-mark showmanual** and **apt-mark showauto** to create lists of applications to be installed after any restore.  Those lists can be trimmed (no need to have any libraries, for example), then feed the remaining list back into APT on the newly installed system.  Prior settings will be picked up.  Any config file differences will prompt for Keep/Replace/View changes so you can decide if retaining the older settings is needed or not.  Basically, 45 minutes to make a fresh install "my" OS with my settings, data and applications.

Certain packages do get removed over time from the repos as their projects die off.  I remember seeing about 20 dying with every LTS-to-LTS release change.  Keeping old software can be great, or it can lead to unstable systems.  No way to know before the choice to keep old versions is made.

But with all answers/suggestions here, you are free to take or leave it.

I prefer to avoid issues, before they happen. YMMV.

---

### Post by MAFoElffen on 2023-06-01
I do Ubuntu +1 Development Release testing, and tested Lunar 23.04 extensively... I've been around far too long and just have been exposed to many things. But I also expect that running interim version is "NOT STABLE CODE." I expect things to break with them. I accept that. But what I use for daily runner's is LTS.

What those errors are telling you is this... Let's break down the error into pieces, so that you can understand what each is saying.

example:
```

Broken gnome-shell-extension-ubuntu-dock:amd64 Depends on gnome-shell:amd64 < 43.1-0ubuntu1 -> 44.0-2ubuntu3 @ii umU > (< 44)

```
Impossible situation = Broken.
Package 'gnome-shell-extension-ubuntu-dock (arch64) depends on a gnome-shell of version less than 43.1-0ubuntu1... but you have a newer version installed... version 44.0-2ubuntu3

[COLOR=#ff0000]***That error is a lie...***[/COLOR] The current depends listed for those packages seem to be different. 

If I go to Ubuntu package search on that package, for kinetic, I see this as depends:
```

    dconf-gsettings-backend
        simple configuration storage system - GSettings back-end 
    or gsettings-backend
        virtual package provided by dconf-gsettings-backend 

    gnome-shell (<< 44)
        graphical shell for the GNOME desktop 

    gnome-shell (>= 40)

```
Remember that is says you have 'gnome-shell 44.0-2ubuntu3' installed... That falls within that range(???) If I go to Lunar for that package, I see this as depends:
```

dconf-gsettings-backend
    simple configuration storage system - GSettings back-end 
or gsettings-backend
    Package not available 

gnome-shell (<< 45~)
    graphical shell for the GNOME desktop 

gnome-shell (>= 40)

```
What you have installed also falls within that range also... So that error is a lie. "Something else" is going on there...

For errors like this, that is how I start to trace through them, reading them like that. I start with the first error and work down. You focused on mutter, which is half-way down the list of errors.

Remember me saying above that your errors seems to be lying??? Your errors do not match what is current, as depends. It seems like it is going off an outdated list of depends. Are you sure you have the current update-manager installed to be able to do a 'do-release-upgrade' installed?

Please do this:
```

apt list update-manager --installed

```
It should be update-manager (1:22.10.4)

---

### Post by Impavidus on 2023-06-01
> **mberg2007 said:**
> Thanks for your feedback. However, I'm obviously not interested in doing a complete reinstall. This defeatist mentality might be common among Windows users, but this is Linux. We can do better.
We're all Linux users here. Some of us may use Windows too. But in my experience, the mentality to avoid complete reinstalls at all cost is more common among Windows users. What's wrong with a fresh install?

---

### Post by HostileJava on 2023-06-15
Did this ever get resolved?  I have the exact same error messages and I confirmed i have update-manager 1:22.10.4.

---

### Post by TheFu on 2023-06-16
> **Impavidus said:**
> We're all Linux users here. Some of us may use Windows too. But in my experience, the mentality to avoid complete reinstalls at all cost is more common among Windows users. What's wrong with a fresh install?

It isn't like there's a license key to location/have/worry about.  Not having to track licenses is 1 key reason why I prefer F/LOSS.

If .deb files are manually installed, often those files don't manage dependencies or get updated. While the program will keep working, it will make normal patching fail, eventually. IME, that is usually in 3-6 months.  If normal patching stops working due to dependency issues, there are 2 answers.  Remove the offending .deb package, do system patching, then try to find a newer version of that manually installed .deb that works with the current system.  Hopefully, this time, a solid, reputable, PPA will be found if it isn't in the standard repos.  If not, you'll have to decide if manually using the .deb file is worth the hassle or not.

Often, people can't remember or figure out which package they manually installed.  There's little that can be done, except to perform a fresh install.  Patching at least every few weeks is very important. For the most part, Linux package managers have made that painless since the late 1990s.  But there are a few rules to prevent "dependency hell."

OTOH, a fresh install is just 15 minutes and if you have good backups, restoring settings and data should be less than 30 minutes more.  Effectively, 45 minutes from a wiped disk to "your system" is very reasonable.  Sometimes, for non-servers, it is just 30 minutes to have "my system".

---

