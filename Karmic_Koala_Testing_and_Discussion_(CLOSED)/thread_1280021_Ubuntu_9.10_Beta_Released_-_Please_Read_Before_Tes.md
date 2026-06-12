---
title: "Ubuntu 9.10 Beta Released - Please Read Before Testing"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-10-01
Ubuntu 9.10 Beta, the last milestone release before the Release Candidate for Ubuntu 9.10, [has been released]("https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000125.html").

You can find the technical overview and download links at the URL below:

[http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta)

Since we expect many new testers to pick up testing with this milestone, this is a good time to remember some basics regarding testing:

[list][*] The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their predecided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the beta**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. 


[*] If you're just starting to test Karmic, please take a look at [this wiki page]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") for information on various testing methods and good practices.


[*] Once you've started testing, do not upgrade your installation blindly - **especially, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade**. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, always check the list of packages to be removed, upgraded and installed before each upgrade. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at [packages.ubuntu.com]("http://packages.ubuntu.com")) to see why a package may be being removed.


[*] When you install the beta, and just keep upgrading your packages until the final release, you'll have the final release; you don't have to reinstall it. But you may want to, in the case that you may be affected by potential unforeseen corner cases that may require a fresh install to fix.


[*] If you run into problems, you're most likely not alone; please do a bug search at [the bug tracker]("https://bugs.launchpad.net/ubuntu") and/or a forum search in this forum (note the "Search this Forum" item on the upper right corner in the thread index) before starting new threads.


[*] [To report a bug]("https://help.ubuntu.com/community/ReportingBugs") in the default desktop applications, use the "Help > Report a Problem" menu item. Where this is not applicable, use the "ubuntu-bug" command line bug reporting tool. You can invoke it by pressing Alt+F2 to open the "Run Application" window, or starting a terminal emulator, and typing ```
ubuntu-bug package_name
``` and pressing "Enter", where *package_name* is the name of the package you want to report a bug in.

If you have trouble finding the right package to report the bug in, take a look at the [Bugs/FindRightPackage]("https://wiki.ubuntu.com/Bugs/FindRightPackage") page on the wiki. If that doesn't help, feel free to start a thread to ask for assistance.

[/list]

---

### Post by ViRMiN on 2009-10-01
Cool!

Can I rename my live-daily image to the new filename for the official beta release and then zsync it for differences do you know?

---

### Post by tjeremiah on 2009-10-01
doesnt seem all to exciting because im an alpha tester..

---

### Post by lachild on 2009-10-01
FYI - ubuntu-9.10-beta-desktop-amd64.iso.torrent seems to be broken.  Gives the following error "Requested Download is not authorized for use with this tracker"

---

### Post by 23meg on 2009-10-01
> **ViRMiN said:**
> Cool!

Can I rename my live-daily image to the new filename for the official beta release and then zsync it for differences do you know?

[https://help.ubuntu.com/community/RsyncCdImage](https://help.ubuntu.com/community/RsyncCdImage)

---

### Post by ViRMiN on 2009-10-01
> **23meg said:**
> [https://help.ubuntu.com/community/RsyncCdImage](https://help.ubuntu.com/community/RsyncCdImage)

Thanks, I tried it anyway and the .zsync files have the old filename in them, so it's not working just yet.  I'll checksum what I've got and just see whether it matches the official release.

---

### Post by neglesaks on 2009-10-01
> **lachild said:**
> FYI - ubuntu-9.10-beta-desktop-amd64.iso.torrent seems to be broken.  Gives the following error "Requested Download is not authorized for use with this tracker"

Same error given by the i386 torrent, but it's downloading full blast.

---

### Post by ViRMiN on 2009-10-01
> **ViRMiN said:**
> Thanks, I tried it anyway and the .zsync files have the old filename in them, so it's not working just yet.  I'll checksum what I've got and just see whether it matches the official release.

Yep, my ISO's are up-to-date already. :)

---

### Post by madsc89 on 2009-10-01
I cant seem to download with torrent, either. Is there a workaround for the problem already described?

---

### Post by neglesaks on 2009-10-01
Try giving it some more time.

---

### Post by cszikszoy on 2009-10-01
> **madsc89 said:**
> I cant seem to download with torrent, either. Is there a workaround for the problem already described?

The alternate torrent is working, just not the desktop one.

---

### Post by zeroandone on 2009-10-01
If you are in North America, use the local mirror from University of Utah. I downloaded the ISO file directly in less than 15 minutes. Burning it on CD now.

---

### Post by andrewabc on 2009-10-01
From release announcement:
> Some users with Intel video chipsets will experience a black screen on reboot after install because the fbcon module is not being loaded. As a workaround, users can boot with the i915.modeset=0 option. Investigation of this issue is ongoing. (431812) 
Anyone know exactly what intel chipsets are affected? and can you only tell if it is affected after you install it?

I have intel g965 x3000 on new computer.


My old computer has Intel i845. Want to install beta to old computer since wireless works better (and maybe intel video works better etc). I don't care if I have to format several times. Just want a heads up on what chipsets are affected.

I have 2 ubuntu installs and winxp. I'll overwrite hardy partition, and I presume grub will recognize Jaunty and winxp install? If completely fails, no problem full format everything is backed up (nothing important).

EDIT:
A lot of the info on [http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta) is out of date. They havn't updated the "have alpha 5 cd available" suggestion.

---

### Post by neglesaks on 2009-10-01
> **cszikszoy said:**
> The alternate torrent is working, just not the desktop one.

Desktop AMD64 works now.

---

### Post by madsc89 on 2009-10-01
Still not able to download using torrent ( ubuntu-9.10-beta-desktop-i386.iso.torrent  and   ubuntu-9.10-beta-desktop-amd64.iso.torrent ). Ive tried with both transmission and bittorrent.

---

### Post by PiotrekS on 2009-10-01
> **madsc89 said:**
> Still not able to download using torrent ( ubuntu-9.10-beta-desktop-i386.iso.torrent  and   ubuntu-9.10-beta-desktop-amd64.iso.torrent ). Ive tried with both transmission and bittorrent.

I haven't any problems. Downloading by torrent is working ok for me (I have downloaded my copy of ubuntu 9.10 beta few minutes ago from this place: [http://releases.ubuntu.com/releases/9.10/]("http://releases.ubuntu.com/releases/9.10/")). Maybe you are firewalled ?

---

### Post by 23meg on 2009-10-01
> **andrewabc said:**
> 
EDIT:
A lot of the info on [http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta) is out of date.

What exactly is out of date?

[QUOTE=andrewabc] They havn't updated the "have alpha 5 cd available" suggestion.[/QUOTE]

Perhaps because it's still relevant?

---

### Post by madsc89 on 2009-10-01
I don't think Im firewalled... I've used torrents on this line on several ocations. I also downloaded from the site suggested. I guess I'll have to wait for the somewhat slow traditional download to finish. I would have liked to help seeding, though. Im sitting on a 20 Mbit/s upload speed..

---

### Post by neglesaks on 2009-10-01
> **madsc89 said:**
> I don't think Im firewalled... I've used torrents on this line on several ocations. I also downloaded from the site suggested. I guess I'll have to wait for the somewhat slow traditional download to finish. I would have liked to help seeding, though. Im sitting on a 20 Mbit/s upload speed..


Give it some time. Some of the torrens have been slow to start off tonight.

---

### Post by mick222 on 2009-10-01
Upgraded seems i have all the updates from alpha 6

---

### Post by andrewabc on 2009-10-01
> **23meg said:**
> Perhaps because it's still relevant?

So they specifically want people to have alpha 5 livecd instead of alpha 6 or beta? Is that because alpha 5 did not have upstart?

---

### Post by 23meg on 2009-10-01
> **andrewabc said:**
> So they specifically want people to have alpha 5 livecd instead of alpha 6 or beta? Is that because alpha 5 did not have upstart?

Correct.

---

### Post by xfalcox on 2009-10-01
I`m typing "sudo apt-get update" and then "sudo apt-get upgrade" and no packages are upgraded...

I`m at Ubuntu unr alpha6 upgraded last time yesterday...

any ideas?

---

### Post by andrewabc on 2009-10-01
> **xfalcox said:**
> I`m typing "sudo apt-get update" and then "sudo apt-get upgrade" and no packages are upgraded...

I`m at Ubuntu unr alpha6 upgraded last time yesterday...

any ideas?

That is normal. You are already running the latest version.

There is no magical update to transform your alpha 6 to beta. And there will be none for beta to RC. As long as you keep up to date you have latest version.

---

### Post by xfalcox on 2009-10-01
> **andrewabc said:**
> That is normal. You are already running the latest version.

There is no magical update to transform your alpha 6 to beta. And there will be none for beta to RC. As long as you keep up to date you have latest version.

I know, but not even ONE package updated?

---

### Post by andrewabc on 2009-10-01
> **xfalcox said:**
> I know, but not even ONE package updated?

Yes. They are in a freeze couple days before release to make sure everything works. Sometimes you may get couple updates, other times nothing. If you don't get any updates in a couple days after release, then start worrying (if update manager not giving any warnings, it should be fine, or try different mirror).

---

### Post by JoseStefan on 2009-10-01
I'm Super-Seeding:
ubuntu-9.10-beta-desktop-amd64.iso

My upload is not the greatest, but it should get things moving with this one.

---

### Post by FormerSlacker on 2009-10-01
Is it possible to upgrade 9.04 via the iso rather then online. update-manager is sputtering along at 30kbs.

---

### Post by Sand &amp; Mercury on 2009-10-02
Slow iso download is slow :lol:

I think I'll wait a bit till the torrents are working properly.

---

### Post by popejeremy on 2009-10-02
> **andrewabc said:**
> Yes. They are in a freeze couple days before release to make sure everything works. Sometimes you may get couple updates, other times nothing. If you don't get any updates in a couple days after release, then start worrying (if update manager not giving any warnings, it should be fine, or try different mirror).

FWIW, I've been running Alpha and I'm not seeing a full upgrade today either. But I am seeing a partial upgrade which I am not using, because I learned the hard way not to. So maybe the Beta isn't any different from the end of the final Alpha.

---

### Post by andymorton on 2009-10-02
> **xfalcox said:**
> I`m typing "sudo apt-get update" and then "sudo apt-get upgrade" and no packages are upgraded...

I`m at Ubuntu unr alpha6 upgraded last time yesterday...

any ideas?



Same thing here. I've been looking forward to the beta for the last few weeks and now I've realised I've already got it. 
I just ran the update manager and it came up with about 10MBs of new packages. :)

---

### Post by tjeremiah on 2009-10-02
> **popejeremy said:**
> FWIW, I've been running Alpha and I'm not seeing a full upgrade today either. But I am seeing a partial upgrade which I am not using, because I learned the hard way not to. So maybe the Beta isn't any different from the end of the final Alpha.

I did the partial upgrade. It removed Ubuntu Store for the new one.

---

### Post by GARoss on 2009-10-02
deleted

---

### Post by imafatmess on 2009-10-02
[http://ubuntuforums.org/showthread.php?p=8045091#post8045091](http://ubuntuforums.org/showthread.php?p=8045091#post8045091)
I have asked the question here as im more likely to get a reply

---

### Post by shadowlands on 2009-10-08
Pan is working but it is hard for me to locate where the items are unless I use the search feature.

Why when unpacking items the par programs are not working.  The gedit program tries to open the package.

---

### Post by emarkay on 2009-10-08
Hey, let's keep this thread on topic - post ONLY known issues and warnings - Moderator - can you snip these (and this post) - and add a "top level" warning about Partial Upgrades?

---

### Post by andrewabc on 2009-10-08
Simple question:

Can we get rid of 60 second timer for shutdown etc? I don't see the option when I right click on menu like in Jaunty. I figured it is fixed but can't find where the options are.

---

