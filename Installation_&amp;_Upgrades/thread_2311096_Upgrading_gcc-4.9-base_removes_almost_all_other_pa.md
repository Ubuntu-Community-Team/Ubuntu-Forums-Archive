---
title: "Upgrading gcc-4.9-base removes almost all other packages"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by alecz20 on 2016-01-24
I am running Ubuntu Mate 14.04.1 x64.

I was trying to install wine but I Synaptic mentioned that this would remove a lot of packages. I think the issue is with **gcc-4.9-base**. The currently installed version is 4.9.1-16, and the available version is 4.9.3-0.
If I try to upgrade **gcc-4.9-base**, I get a huge amount of packages removed including **libapt-pkg4.12**, **libstdc++6**, **apt**, **apt-utils**, **grub**, **firefox**, and many others:
Full output on pastebin: [http://pastebin.ca/3348510](http://pastebin.ca/3348510)

As some point I attempted to install **TeamViewer** but apparently that is no longer possible with Ubuntu 14.04 (works just fine on the old 10.04)
I also installed the **gThumb** version from Ubuntu 15.04 as it has some fixed bugs.
I don't know why I get this behaviour or how to fix it.

Any ideas on how to get to the bottom of this?

I already tried apt-get update, apt-get upgrade, apt-get autoremove, apt-get clean, and apt-get autoclean among other things.

---

### Post by ian-weisser on 2016-01-24
> **alecz20 said:**
> Any ideas on how to get to the bottom of this?

Look through your /var/log/apt/* logs to determine which set of packages created the problem.
Uninstall those packages.
Disable the repository those packages came from...it is no longer your friend.

---

### Post by alecz20 on 2016-01-24
Thanks Ian for the quick reply.
How would I go about "determining which set of packages created the problem". Teamviewer for example has been long removed, and gThumb was installed from utopic repositore long ago.

Can I run apt-get with some kind of verbosity to see WHY it wants to remove half my system on a package upgrade?
How does it even make sense that **apt-get install gcc-4.9-base** needs to remove half the system?

---

### Post by ian-weisser on 2016-01-24
I think you misunderstand the apt error - the error is telling you that all those packages are *already* orphaned and eligible for autoremoval...which, if you removed the gcc base, is completely understandable. The gcc base is an important element of your system. Usually, you get an upgraded version of gcc when you upgrade to the next release of Ubuntu (or Mint).

The specific apt issue that prevents installing your new version of gcc is shown at the bottom of your output - the system is warning you that installing the version of gcc that you have specified will irrevocably break apt. Apt and other key system elements depend upon a specific version of gcc, and apt believes the newer version you are trying to install to be incompatible.

My advice: Disable all your non-Ubuntu, non-Mint sources and reinstall the original version of gcc. Don't try to update gcc. Run a newer release of Ubuntu or Mint instead.

Since you seem to like to experiment: You can force the installation of gcc on your system, too, but the results are unpredictable - it may work, or it may totally break your system. It takes you well outside what we can support: You will be entirely on your own. Our only useful advise if it breaks will be to reinstall. Backup your data before trying it.

---

### Post by alecz20 on 2016-01-25
Thanks for the tips, I managed to get further and I found what caused all this mess.
After I installed Ubuntu-mate, I was disappointed to see that caja does not have the Video Properties tab, and I found that when it was built, they did not include the plugin for the properties, so I had to build gnome-mplayer myself.

I found the command where I installed the dependencies:
**apt-get build-dep gnome-mplayer**

However, it seems I had the Ubuntu 14.10 Utopic repository added (Utopic was supposed to have the gnome-mplayer version with the extension, but it turns out it didn't have it).
When I ran the command, gcc-4.9-base was upgraded from 4.9.1-0ubuntu1 to 4.9.1-16ubuntu6 (which is from utopic). Now Trusty has 4.9.1-20, andTrusty-updates has a newer version: 4.9.3, but I am unable to upgrade to either since, as you say apt thinks it is incompatible with what I have.

Have I totally screwed my system or is there any chance I can fix it now?

To add to this the Utopic repository is no longer available, gives 404 since its EOL.

---

### Post by ian-weisser on 2016-01-25
The hard part is that downgrading is possible (it's a dpkg option), but it's unsupported (no dependency checking).
So, sure, you can downgrade the gcc-4.9-base package...but backup your data first. The results may be unexpected.

Have you any idea what other packages may have updated from 14.10 repos? If it was enabled, you may have upgraded most of your system.

---

### Post by alecz20 on 2016-01-25
Since it is possible that I might have upgraded a bunch of packages from 14.10, I decided to simply upgrade to 15.04. I figured that this should upgrade everything or at least leave it the same version.

There were a few small glitches such as init not getting installed, but I managed to resolve them all before rebooting. Now I am in 15.04 and everything seems mostly fine.
The only thing is that the theme is a bit messed up... for example checkboxes no longer show, only the check marks (you need to guess where the boxes are).

Once I assess more of the system I'll mark this thread as solved.

---

### Post by ian-weisser on 2016-01-25
Upgrading to 15.04 was a wise choice. A smart way to sidestep the dependency problems by upgrading *everything*.
FYI, 15.04 will EOL in 10 days on Feb 4, 2016. Plan to upgrade again very soon to 15.10.

---

### Post by alecz20 on 2016-01-27
Just to confirm. Upgrading to 15.04 did solve all the issues. Thanks for the heads up on the EOL. I am looking forward to go to the next LTS so I will keep upgrading.

---

