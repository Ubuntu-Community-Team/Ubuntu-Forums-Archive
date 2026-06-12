---
title: "why does do-release-upgrade insist on removing anything and can I override that?"
date: 2022-12-10
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2022-12-10
I'm trying to do a do-release-upgrade (from 18.04 lts) and it says that it wants to remove the following:

```
Remove: audacity blender calibre digikam fwupdate-signed gimp 
  gnome-settings-daemon-schemas libapt-inst2.0 libapt-pkg5.0 
  libavcodec-dev libavformat-dev libcupscgi1 libcupsmime1 
  libcupsppdc1 libebook-1.2-19 libedata-book-1.2-25 
  libedata-cal-1.2-28 libfwup1 libldb1 libodbc1 libpolkit-backend-1-0 
  libsensors4 libsnmp30 libyaz5-dev openshot pyqt4-dev-tools 
  python-pip python3-pyqt4 unetbootin uno-libs3 vlc winehq-stable 

Remove (was auto installed) digikam-private-libs libcdk5 libept1.5.0 
  libfontforge2 libgcc1:i386 libgdal20 libgdraw5 libhdf5-100 
  libhfstospell9 libkf5auth-bin-dev libkf5config-bin-dev 
  libmailutils5 libnetcdf13 libogdi3.2 libopencv-highgui3.2 
  libopencv-imgcodecs3.2 libopencv-objdetect3.2 libopencv-videoio3.2 
  libopenimageio1.7 libpango1.0-0 libpython-dev libpython-stdlib 
  libqbscore1.10 libqbsqtprofilesetup1.10 libqt4-dbus 
  libqt4-declarative libqt4-designer libqt4-help libqt4-network 
  libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql 
  libqt4-sql-mysql libqt4-svg libqt4-test libqt4-xml 
  libqt4-xmlpatterns libqtassistantclient4 libqtcore4 libqtdbus4 
  libqtgui4 libsensors4:i386 libtinyxml2-6 libtirpc1 libvigraimpex6 
  libxine2-ffmpeg libxine2-plugins libxine2-x openshot-qt python 
  python-dev python-keyrings.alt python-ldb python-minimal 
  python-pyqt5 python-pyqt5.qtsvg python-pyqt5.qtwebkit python-qt4 
  python-samba python-tdb python3-openshot qdbus qt-at-spi 
  wine-stable wine-stable-amd64 xine-ui 
```

Why does it want to remove anything at all, but much less something I personally installed such as audacity; blender; calibre; and wine? While all of those are worrisome due to the fact that each one has additional settings, profiles and extensions installed along with all of the associated data... wine is even more troublesome because that would also do away with every program I had installed through wine as well.

Surely there has to be SOME way to override this? I mean, if the programs won't work after the "upgrade" ok fine... but shouldn't tat be MY choice. One of the reasons I've always liked linux over windows is the fact that the user (typically) controls the software. Here, though, the software is wanting to control the user! ... unless I am missing something, in which case I will walk that back...

---

### Post by ian-weisser on 2022-12-10
First, let's talk about "choice:"

Total choice is LFS. When you choose a distro (like Ubuntu), you're adopting a set of assumptions and decisions about how software and packages should behave. If you don't like those behaviors, you are free to choose a different distro.

Lots of people like that Ubuntu's assumptions and decisions have led to a rock solid distro, well-tested, with reasonably transparent governance, a cadre of professional engineers, offering a wide variety of flavors, and has kept a consistent release schedule for 18 years. But that's not for everybody. And that is okay.


Second, let's talk about the most common reason folks encounter what you did: Bad choices.

Most folks who encounter lots of removals during a release-upgrade are encountering a consequence for years of unwise choices. They installed lots of software from non-Ubuntu sources, often bolting it onto older LTS releases. They neglected to uninstall that non-Ubuntu software before a release-upgrade. And now that non-Ubuntu software is incompatible with the newer release of Ubuntu, and the source lacks a compatible version, so it gets marked for removal. Folks who stick to the Ubuntu repositories generally don't encounter this problem much.

Or maybe you have some different problem entirely. Check "apt-cache policy <packagename>" for each of those packages to find out where it's from (Ubuntu vs. Non-Ubuntu). Use rmadison or packages.ubuntu.com to learn what the 20.04 requirements for those packages are.

---

### Post by rebeltaz on 2022-12-10
> **ian-weisser said:**
> First, let's talk about "choice:"

Total choice is LFS. When you choose a distro (like Ubuntu), you're adopting a set of assumptions and decisions about how software and packages should behave. If you don't like those behaviors, you are free to choose a different distro.

Lots of people like that Ubuntu's assumptions and decisions have led to a rock solid distro, well-tested, with reasonably transparent governance, a cadre of professional engineers, offering a wide variety of flavors, and has kept a consistent release schedule for 18 years. But that's not for everybody. And that is okay.


Second, let's talk about the most common reason folks encounter what you did: Bad choices.

Most folks who encounter lots of removals during a release-upgrade are encountering a consequence for years of unwise choices. They installed lots of software from non-Ubuntu sources, often bolting it onto older LTS releases. They neglected to uninstall that non-Ubuntu software before a release-upgrade. And now that non-Ubuntu software is incompatible with the newer release of Ubuntu, and the source lacks a compatible version, so it gets marked for removal. Folks who stick to the Ubuntu repositories generally don't encounter this problem much.

Or maybe you have some different problem entirely. Check "apt-cache policy <packagename>" for each of those packages to find out where it's from (Ubuntu vs. Non-Ubuntu). Use rmadison or packages.ubuntu.com to learn what the 20.04 requirements for those packages are.

So.. I have no idea what LFS means. 

As for installing non-Ubuntu software, maybe if Ubuntu would have up to date software in their repositories, we wouldn't HAVE to install non-Ubuntu software. Each of those programs was installed outside of the Ubuntu universe because Ubuntu does not have the latest - or in some cases, even a CURRENT - version in their official repository.

---

### Post by QIII on 2022-12-10
In which case you will have accept the removal of the non-official packages, uprade your release, and then, if the apps are still out of date, re-install them from outside sources.

Once a release of Ubuntu hits the street, applications are frozen unless there is a security issue or a really important update.  Ubuntu is not a rolling release.  

If you don't like that, you might want to chose a rolling release ... and deal with a bit of instability from time to time.

LFS = Linux From Scratch.

---

### Post by QIII on 2022-12-10
Just for the record, my Ubuntu 22.04 is running the Linux 5.15.0 (and change) kernel, while my Fedora machine is running 6.0.11 (and change).

All distros are different and have different goals/assumptions.

---

### Post by rebeltaz on 2022-12-10
> **QIII said:**
> In which case you will have accept the removal of the non-official packages, uprade your release, and then, if the apps are still out of date, re-install them from outside sources.

Once a release of Ubuntu hits the street, applications are frozen unless there is a security issue or a really important update.  Ubuntu is not a rolling release.  

If you don't like that, you might want to chose a rolling release ... and deal with a bit of instability from time to time.

LFS = Linux From Scratch.

So I'm guessing the answer to my question is that there is no way to NOT remove the packages. Thanks.

---

### Post by Impavidus on 2022-12-10
> **rebeltaz said:**
> 
As for installing non-Ubuntu software, maybe if Ubuntu would have up to date software in their repositories, we wouldn't HAVE to install non-Ubuntu software. Each of those programs was installed outside of the Ubuntu universe because Ubuntu does not have the latest - or in some cases, even a CURRENT - version in their official repository.Ubuntu has up to date software in its repositories, provided you use a recent Ubuntu. Instead of forcing recent software into your 18.04 system, you could have moved to a more recent Ubuntu release years ago. If you go from one LTS release to the next as soon as the release upgrade is available, your software won't be more than 2.5 years out of date. If you use the interim releases, no more than 1 year.

You could do a fresh install of 22.04 LTS (or even 22.10) now, keeping your home directory. That will keep all your personal settings, for as far as they still apply. I think your wine applications are also in your home directory, but you may get a new release of wine and I don't know the consequences of that. I've never used wine. At the very least, a fresh install will clean up the cruft that has accumulated on your system.

---

### Post by ian-weisser on 2022-12-10
> **rebeltaz said:**
> As for installing non-Ubuntu software, maybe if Ubuntu would have up to date software in their repositories, we wouldn't HAVE to install non-Ubuntu software.

Your current situation seems a direct consequence of your choices. You can throw rocks at Ubuntu, but you were the decision-maker.

Best practice for folks who want newer software is to use the 6-month releases of Ubuntu. 
Ubuntu has lots of newer software in the 6-month releases. You chose to not follow best practice.

Best practice is to uninstall non-Ubuntu deb-packaged software before a release-upgrade precisely to avoid the problem you encountered. You chose to not follow best practice.

You can choose to override apt and keep those packages. Many probably won't work anymore. But you cannot do so from within the do-release-upgrade script. You can choose to manually update your sources and dist-upgrade your system. There are several additional steps. But then your journey to the dark side will be complete -- you will choose to be running some awful Frankensystem that's likely to crash a lot and will be very difficult to maintain and repair. An unwise choice, perhaps.

Advice: There's an easy way out. Let do-release-upgrade remove those application. Let the release-upgrade complete. After you have a stable and supported Ubuntu system again, you can install whatever you choose. You can reinstall those applications from another source. It's not difficult and takes only a minute.

---

### Post by rebeltaz on 2022-12-10
> **ian-weisser said:**
> Your current situation seems a direct consequence of your choices. You can throw rocks at Ubuntu, but you were the decision-maker.

Best practice for folks who want newer software is to use the 6-month releases of Ubuntu. 
Ubuntu has lots of newer software in the 6-month releases. You chose to not follow best practice.

Best practice is to uninstall non-Ubuntu deb-packaged software before a release-upgrade precisely to avoid the problem you encountered. You chose to not follow best practice.

You can choose to override apt and keep those packages. Many probably won't work anymore. But you cannot do so from within the do-release-upgrade script. You can choose to manually update your sources and dist-upgrade your system. There are several additional steps. But then your journey to the dark side will be complete -- you will choose to be running some awful Frankensystem that's likely to crash a lot and will be very difficult to maintain and repair. An unwise choice, perhaps.

Advice: There's an easy way out. Let do-release-upgrade remove those application. Let the release-upgrade complete. After you have a stable and supported Ubuntu system again, you can install whatever you choose. You can reinstall those applications from another source. It's not difficult and takes only a minute.

I know that reinstalling the programs isn't too hard. That's not my real concern. One concern is that all of the customizations and extensions that I've done to those programs will be lost. Right? **THAT** is what **IS** difficult to redo. Even that concern notwithstanding, though, my **REAL** concern is wine. If **THAT** program is removed and all of the associated programs that were installed under that are lost, **THAT** would be a **MAJOR** headache! 

I will most likely just have to do the do-release-update if I want to use this resin printer, but.. you mentioned an ability to override apt. Where would I find the steps to take if I decided to try that route? 

You all keep insisting that what I'm saying is so out there. I've been working with computers since the Atari 400 and never have I updated an operating system and the system take it upon itself to delete programs that the user installed because they weren't "approved." The programs might not work, but at least the data was still there.

Everyone keeps saying I should update every time a new release is out. I guess I'm not wired that way. When something works, I don't see a need to grab hold of the newest shiniest thing. Almost every single time I DO "upgrade" software, either a feature I use is lost; graphical interfaces are changed to (what I find) less user intuitive; or something breaks. I guess in this modern age, "if it ain't broke, don't fix it" doesn't hold water anymore.

Case in point - audacity: [https://fosspost.org/audacity-developers-apologize-revise-controversial-privacy-policy/](https://fosspost.org/audacity-developers-apologize-revise-controversial-privacy-policy/)

I know I will get hate for this (I usually do) but for the most part what I have gotten has been "bad user. bad, bad user." :roll:

---

### Post by QIII on 2022-12-10
My response contained no "hate".  Just a simple matter of fact.  Ubuntu is not a rolling release and Canonical freezes features/software at release time.  That is simply how it is.  If you step outside of the repos for your software, it is likely that it will be removed (or you will have to remove it) at release upgrade.  Each release has been tested with the software versions available in the repos and having other versions installed is problematic.

There are rolling releases that update software and components of the OS itself as things become available.  You are not stuck with Ubuntu.  What distro you use *is your choice*.  Whether or not you keep with the best practices of a release based on its purveyor's vision *is your choice.*

Choice is what this is all about.  Choice is a *good* thing.

Just be aware that Ubuntu is premised on stability (To paraphrase TheFu:  New is the enemy of stable.)  Roiling releases are less stable, but are more likely to have the newest bells and whistles.  Between the two is a spectrum of releases.  Fedora is stable, but the community supporting it is more willing to press forward with the new than Canonical is willing with Ubuntu.  Fedora is a test-bed for Red Hat, so it gets new things to test out.  I use Fedora every bit as often as Ubuntu.

That this or that or the other OS does things one way does not place any requirement on any other OS to do the same.

Canonical values stability, and that requires a methodical and measured process for moving forward.  It also often requires that applications be installed from a repo that contains things that have been thoroughly tested with Ubuntu to ensure stability.

Canonical is unlikely to change its approach, so getting yourself wrapped around the axle over this is not constructive.

---

### Post by oldfred on 2022-12-10
See this, if you do not purge, your configurations should remain.
man apt

And you should have good backups of /home, your data, and all installed apps.
But if not using standard repositories, they may not even be available for a new version.

You can also check all default software versions in the manifest of a version. Some may now be in default install.
[http://releases.ubuntu.com/jammy/](http://releases.ubuntu.com/jammy/)
[http://releases.ubuntu.com/jammy/ubuntu-22.04.1-desktop-amd64.manifest](http://releases.ubuntu.com/jammy/ubuntu-22.04.1-desktop-amd64.manifest)

---

### Post by rebeltaz on 2022-12-10
I'm sorry. That wasn't aimed at you. 

> (To paraphrase TheFu: New is the enemy of stable.)
My sentiments exactly!

---

### Post by rebeltaz on 2022-12-10
> **oldfred said:**
> See this, if you do not purge, your configurations should remain.
man apt

And you should have good backups of /home, your data, and all installed apps.
But if not using standard repositories, they may not even be available for a new version.

You can also check all default software versions in the manifest of a version. Some may now be in default install.
[http://releases.ubuntu.com/jammy/](http://releases.ubuntu.com/jammy/)
[http://releases.ubuntu.com/jammy/ubuntu-22.04.1-desktop-amd64.manifest](http://releases.ubuntu.com/jammy/ubuntu-22.04.1-desktop-amd64.manifest)

Thank you. I made TWO clones of this hard drive last night, so I'm good on backups. :) I appreciate it.

---

### Post by ian-weisser on 2022-12-10
> **rebeltaz said:**
> You all keep insisting that what I'm saying is so out there. I've been working with computers since the Atari 400 and never have I updated an operating system and the system take it upon itself to delete programs that the user installed because they weren't "approved." The programs might not work, but at least the data was still there.

We hear you. Seems like we're roughly similarly-aged. I've seen OSX updates remove frequently-used features without warning. And I've seen Windows updates make terrible unwanted changes without warning. In this case, seems like Ubuntu *warned* you first, gave you a chance to abort, and would not have deleted your data.

The feature you are complaining about is inherent in the way Debian-based packaging systems work. Removal of incompatible packages was a huge advance that apt was doing before Ubuntu existed.

---

### Post by rebeltaz on 2022-12-10
I just finished doing the upgrade. It wasn't as painful as that warning would have had me believe. I did have to reinstall a couple of programs (still need to find an old version of blender) but at least the data was still there when I did. 

If I may ask, though... 18.04 was an LTS, right? According to the Ubuntu Releases page, 'Each Ubuntu LTS is maintained for 10 years total." I would think that that would include the repositories as well. If not, what is the purpose of maintaining the OS itself? 

Anyway... I got it done and I still have some hair left, so... thank you!

oh... and don't get me started on windows. When they decided that you couldn't disable automatic updates and took it upon themselves to update your entire OS whether you wanted it or not... nah.

---

### Post by ian-weisser on 2022-12-10
> **rebeltaz said:**
> According to the Ubuntu Releases page, 'Each Ubuntu LTS is maintained for 10 years total." I would think that that would include the repositories as well. If not, what is the purpose of maintaining the OS itself? 

The entire sentence reads:

"*Each Ubuntu LTS is maintained for 10 years total: 5 years of standard support + 5 years of ESM*"

That's a big difference. ESM is security updates only. No community support (that's us). No other repositories. No bugfixes. ESM is a bare shadow of support, originally intended for enterprise slowcoaches. ESM is *not* intended for systems that need to be maintained or changed.

---

### Post by rebeltaz on 2022-12-10
> **ian-weisser said:**
> Read the entire sentence:

"*Each Ubuntu LTS is maintained for 10 years total: 5 years of standard support + 5 years of ESM*"

That's a big difference. ESM is security updates only. No community support (that's us). No other repositories. No bugfixes. ESM is a bare shadow of support, originally intended for enterprise slowcoaches.

OK... I'll admit that I read that wrong. I didn't realize that the 5 and 5 where the 10 total. But...

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

Doesn't this show that the 5 year support for 18.04 ends 2023? 

[ATTACH=CONFIG]291406[/ATTACH]

as does this - [https://computing.cs.cmu.edu/news/2022/eol-ubuntu-1804](https://computing.cs.cmu.edu/news/2022/eol-ubuntu-1804)

It's a moot point now, but my point about the repositories in a LTS sill stands. Maybe I'm wrong. It's happened before. But that's the way it looks to me.

---

### Post by Impavidus on 2022-12-11
> **rebeltaz said:**
> 
Doesn't this show that the 5 year support for 18.04 ends 2023?

Yes, 18.04 has 5 months of standard support left. It will end in April next year. This standard support means that the software in the main repository will get security fixes and (some) other bugfixes, which typically get backported into the versions of the software in the repositories. There are, with a few exceptions, no new releases with new features, which protects you from new bugs.

---

### Post by Tadaen_Sylvermane on 2022-12-11
I just wanted to directly respond here for future reference, didn't see this touched on.

> I know that reinstalling the programs isn't too hard. That's not my real  concern. One concern is that all of the customizations and extensions  that I've done to those programs will be lost. Right? **THAT** is what **IS** difficult to redo. Even that concern notwithstanding, though, my **REAL** concern is wine. If **THAT** program is removed and all of the associated programs that were installed under that are lost, **THAT** would be a **MAJOR** headache!

Unless you've messed with the code and by extension changed how the system works any changes you've made in settings for stuff is in your /home/"$USER" directory. Nothing should be outside of that so it should stay just the way it is on upgrades.

---

### Post by rebeltaz on 2022-12-11
> **Tadaen_Sylvermane said:**
> I just wanted to directly respond here for future reference, didn't see this touched on.



Unless you've messed with the code and by extension changed how the system works any changes you've made in settings for stuff is in your /home/"$USER" directory. Nothing should be outside of that so it should stay just the way it is on upgrades.

And it was. The warning about deleting stuff, though, was a little worrisome. It all turned out relatively ok, though. More so than it usually does for me :)

---

