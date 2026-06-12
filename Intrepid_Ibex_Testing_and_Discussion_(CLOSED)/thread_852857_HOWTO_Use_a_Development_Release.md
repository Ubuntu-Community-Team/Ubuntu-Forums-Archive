---
title: "HOWTO: Use a Development Release"
date: 2008-07-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Raptor45 on 2008-07-08
There are always many new users interested in trying out a developmental release for the first time, and many old users with misconceptions about how things work. This is here to provide a (hopefully) accurate reference and to help people avoid the most common issues. 

If you have any comments, corrections, or suggestions on how this might be improved, feel free to make a post below.

**[SIZE="4"]About the Development Release (and the obligatory warning)[/SIZE]**
The point of a development release is not to provide a stable or even usable desktop. Here the goal is all about finding and fixing bugs before they make it into the final release. If something is broken don't complain, as this should be expected; instead file a bug report, go back to a stable release, and wait for the problem to be fixed. Try to avoid applying workarounds, or manually installing 3rd party "hacks" to solve problems. In many ways this reduces your help as a tester, as it makes it harder to tell whether the problem really lies in Ubuntu, or your customizations.

Keep in mind that even with the best precautions, developmental releases are unstable and you need to be willing to accept that any kind of problem may occur. Updates may cause you to suddenly be unable to log in, start X, lose data, burst into flames, etc. Take precautions, and be willing to accept it if something does go wrong.

**[SIZE="4"]Installation:[/SIZE]**
Both of these methods need to be tested, and may encounter different bugs and issues.

**Fresh Install:**
[LIST][*]Find the latest release on the [Release Schedule]("https://wiki.ubuntu.com/IntrepidReleaseSchedule") and download your desired ISO. These are "milestone" releases, and are tested to be reasonably free of major bugs.
[*]Installation can proceed normally from here.[/LIST]
You can also install from the [Desktop]("http://cdimage.ubuntu.com/daily/current/") or [Alternate]("http://cdimage.ubuntu.com/daily-live/current/") Daily Build. However these are built automatically, have no testing, and may frequently have showstopper bugs. They may also be oversized, as packages are changed continuously and an effort to shrink is only made for milestone releases. In such a case you can burn the image to a DVD, or use a Virtual Machine.

**Upgrading:**
[LIST][*]Run the following command from a fully upgraded version of the stable release:
```
update-manager -d
```
[*]There should be a notice that a new release is available. Clicking that will upgrade you to the development release.[/LIST]
Note that this operation is irreversible, and it is essentially impossible to move back to the stable release.

**Manual Upgrade:**
Manually updating by editing sources.list is NOT recommended after the initial Alpha 1 release has been made. A fresh install, or update via update-manager, are the preferred methods. Update-manager has some special logic to deal with upgrades which apt-get does not account for.

**[SIZE="4"]Updating:[/SIZE]**
Use update-manager normally. If a window pops up asking you to do a partial-upgrade, cancel it, and press Install updates on the main window. NEVER do "partial upgrades" or "dist-upgrades" without checking what is being changed!

If the partial-upgrade window popped up before, that means there is a dependency issue of some kind. Normally this will resolve itself in time, however some upgrades do require things to be added or removed. To check what the problem is, start up Synaptic, and mark the problem upgrades. It will tell you what packages would have to be changed.

Adding packages is generally safe, as is removing an obsolete package when it is replaced by a new one. If it wants to remove a bunch of core packages (such as in [this]("http://ubuntuforums.org/showpost.php?p=5337884&postcount=8") case) just wait; all the necessary packages probably haven't made it into the repository yet. Knowing when it is safe to remove a package can require a certain amount of experience, so if you are unsure of what to do ask on the forums.

Updates can also be done on the command line, with the "apt-get update" and "apt-get upgrade" commands. If packages were held back you can check why in Synaptic as before, or attempt a dist-upgrade. However, make sure to avoid doing dist-upgrades without first checking why the packages were held back, and making sure its safe.

**[SIZE="4"]Reporting Bugs:[/SIZE]**
Everyone can contribute to Ubuntu by reporting bugs, regardless of experience level. The proper place to report bugs is [Launchpad]("https://launchpad.net/"), and suggestions can be made on [Brainstorm]("http://brainstorm.ubuntu.com/"). Those interested in hearing what the developers are up to should sign up for the relevant [mailing lists]("https://lists.ubuntu.com/").

Further information and help with reporting bugs can be found on the [wiki]("https://help.ubuntu.com/community/ReportingBugs"). Keep in mind that if you have applied many workarounds, or manually installed 3rd party software not supplied by Ubuntu, you may want to consider reinstalling before reporting bugs. These "hacks" may be causing the problems you have, not Ubuntu itself.

The forums are meant for discussion, not bug reporting; the developers generally don't read the forums, so complaints and reports will not be of much use here. If you would like to make a post in the hope of discussing the problem and checking that your issue really is a bug, please first search both the forums and launchpad; someone may have already encountered your problem. Repeat posts and "testimonials" add to the clutter, making it harder for others to find the information they need.

**[SIZE="4"]Common Issues & FAQs:[/SIZE]**
**Upgrading Between Alphas/Betas/RC/Final Release:**
If you keep up with upgrades, you will always have the latest version. There is no need to install from scratch or do a special upgrade to move to the next one.

The reason for this is that a given release of Ubuntu is not fixed, as a typical "static" program may be with specific version numbers. It is instead more fluid, with new and updated packages hitting the repositories all the time. An alpha or beta release is simply a "snapshot" of the repositories at that given point, nothing more.

With that said, when testing, it can often be beneficial to reinstall from scratch each time a new version comes out. This will clear up any bugs from the previous installation which may be causing issues, and will get rid of any lingering hacks or tweaks which may have been applied. It also allows you to test the installer again, with is always helpful.

**Testing in a Virtual Machine**
Testing a real install is preferred, however Virtual Machines can still be useful if that is your only option. For testing kernels, X, and anything that interacts directly or at a low level with hardware, it's hard to produce useful bug reports. If filing showstopper bugs from VM installs, don't forget that they will be reports about Ubuntu failing to work on that particular VM, and don't forget to indicate that you're testing on a VM in your bug report. While VMs are a valid use case, bugs from real hardware are much more useful. If, however, you're only looking to test high-level stuff such as userspace apps, user interfaces and so on, VMs are fine.

**A note on "dist-upgrade"s and "partial upgrade"s:**
Essentially, never do them. While that is not necessarily true in all cases, it is a safe rule to follow. The commands are very likely to cause harm if you don't first check that what they are doing is safe.

At certain times, dependencies of certain packages can't be satisfied, simply because they haven't been built and placed in the archive at the time. This is normal. Developers work only on source packages locally; once a source package is uploaded, it takes a certain amount of time for it to be picked up by the build daemons, built, and placed into the archive.

A normal upgrade will "hold back" these packages until all dependencies are available; this is the safe solution, and will leave you with a "stable" system. A dist-upgrade will attempt to install these incomplete packages, doing whatever is necessary to resolve these dependencies. Often this means removing vital packages or entire chunks of the system. All that must be done is to wait for the rest of the packages to hit the repository, where they will be automatically installed by a normal upgrade.

Sometimes it IS necessary and correct for packages to be added or removed; such as when an obsolete program is replaced by a new one. In such cases a dist-upgrade would be safe; however this operation can also be done in synaptic or aptitude. Telling whether an upgrade is safe or not is generally based off experience, so if you are unsure feel free to ask on the forums. For more information check the Updating section.

---

### Post by autocrosser on 2008-07-08
Several thumbs up---well said.

I tend to "jump in" as soon as the repos open & just change my sources to reflect the new testing branch. I also "generally" keep two installs of the testing software--a "fresh" install (reinstall at  least 4 or 5 of the alpha/beta releases)  that is as up-to-date as normal installs will allow & a upgraded install that I sync weekly when I "think" things are at a "safe" place. I also have a stable install of the last version that I keep updated also.

I use the freshest install as my daily OS & only boot the others for updates & when something goes "away".  At this stage of the game, I expect "blow-ups"--normal running is abnormal ;)   It goes without asking that each install has a separate /home & I DON"T share them.

The only thing I can really add is---ALWAYS have a alternate--backups, other installs--just don't fly with the testing branch as your only install.

---

### Post by philinux on 2008-07-08
Nicely done Raptor. Just what I needed to see in black and white.

---

### Post by ikt on 2008-07-08
Did not know about the whole dist-upgrade thing, thank you for the information :)

---

### Post by psyke83 on 2008-07-08
Raptor45,

A word about "dist-upgrade" - unfortunately your information is not quite correct. During the development process it *is* necessary to perform the "dist-upgrade" command, so that new packages will be installed (such as a new kernel release), or new dependencies are added to fulfill a package upgrade. Beginners need to know when it is safe to perform a "dist-upgrade", not to be forbidden to do so. 

The simplest rule of thumb* is: if a "dist-upgrade" elects to install new packages, then the upgrade is safe. If a "dist-upgrade elects to remove packages, then the upgrade is not safe.

Ok, here's a good example:

```
conn@inspiron:~/work$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libcairo2 libquicktime1
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Packages are being held back. There could be unfulfilled dependencies, so let's try a dist-upgrade to see:

```
conn@inspiron:~/work$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libswscale0 libxcb-render-util0 libxcb-render0
The following packages will be upgraded:
  libcairo2 libquicktime1
2 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 977kB of archives.
After this operation, 418kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

This is a perfect scenario where a "dist-upgrade" is both safe and necessary (to install new dependencies), as nothing will get removed.

*Unfortunately, even this rule of thumb has exceptions. Sometimes obsolete packages are deliberately marked for uninstallation - and how is a user supposed to know when this is the case? Experience and research.

---

### Post by ikt on 2008-07-08
> **psyke83 said:**
> Packages are being held back. There could be unfulfilled dependencies, so let's try a dist-upgrade to see:

```
conn@inspiron:~/work$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libswscale0 libxcb-render-util0 libxcb-render0
The following packages will be upgraded:
  libcairo2 libquicktime1
2 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 977kB of archives.
After this operation, 418kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

This is a perfect scenario where a "dist-upgrade" is both safe and necessary (to install new dependencies), as nothing will get removed.

Could you give an example of when a dist-upgrade is not safe?

---

### Post by psyke83 on 2008-07-08
> **ikt said:**
> Could you give an example of when a dist-upgrade is not safe?

Here's a recent example of an unsafe "dist-upgrade" that occurred yesterday: [http://ubuntuforums.org/showpost.php?p=5337884&postcount=8](http://ubuntuforums.org/showpost.php?p=5337884&postcount=8)

---

### Post by Raptor45 on 2008-07-08
A dist-upgrade would not be safe when installing causes a lot of packages to be removed which aren't intended to be. Recently this was the case with an xorg upgrade, where some of the packages hit the repositories, but trying to install them led to xserver and ubuntu-desktop and a bunch of other things being removed. Sometimes it just takes experience to tell if a package is supposed to be removed or not, which is why I recommended asking on the forums if you're unsure.

EDIT: psyke83 beat me to it; that's what I was talking about. Its a perfect example.

---

### Post by Raptor45 on 2008-07-08
> A word about "dist-upgrade" - unfortunately your information is not quite correct. During the development process it *is* necessary to perform the "dist-upgrade" command, so that new packages will be installed (such as a new kernel release), or new dependencies are added to fulfill a package upgrade. Beginners need to know when it is safe to perform a "dist-upgrade", not to be forbidden to do so.

I tried to cover these cases in the Updating section. I suggested using Synaptic (or aptitude) to check the dependency issues, instead of doing a dist-upgrade directly. This makes it easier to pick and choose the upgrades, as sometimes one might be safe and another cause problems.

If you think this was unclear, I'll edit the original post to fix this.

EDIT: changed the original post; is this more clear?

---

### Post by ronacc on 2008-07-08
nicely done , I would add this . do not be afraid of the terminal , it can be your friend learn to use it . also perhaps install MC , it is an old msdos style filemanager that runs from terminal to make it a bit easier to navigate around and examine log files , config files etc . also I find a live cd distro like puppy linux or DSL to be handy for the same reasons MC is and to allow you to poke around from the comfort of a gui when things go down the tubes .

---

### Post by pilli on 2008-07-08
Thanks for the guide Raptor.  Just tried "gksudo update-manager -d" and UM reports system is up to date, with no indication of a dist upgrade.  However, I'm running Hardy on my box, not II.

Advice, thoughts from anyone would be most appreciated. (just out of interest I thought I'd try it this way rather than downloading ISO, clean install, etc, being lazy in other words (or changing sources list like I did for HH)

---

### Post by Raptor45 on 2008-07-08
> **pilli said:**
> Thanks for the guide Raptor.  Just tried "gksudo update-manager -d" and UM reports system is up to date, with no indication of a dist upgrade.  However, I'm running Hardy on my box, not II.

Advice, thoughts from anyone would be most appreciated. (just out of interest I thought I'd try it this way rather than downloading ISO, clean install, etc, being lazy in other words (or changing sources list like I did for HH)

Sorry: you need quotes around it as follows:

```
gksudo "update-manager -d"
```

Otherwise gksudo takes the -d, instead of update-manager.

EDIT: Fixed in original post.

---

### Post by pilli on 2008-07-08
Ooops, silly me.:lolflag:  I should have known that!  Thanks for getting back to me.

---

### Post by Raptor45 on 2008-07-16
I merged a bunch of stuff from 23meg's [old post]("http://ubuntuforums.org/showthread.php?t=600644"). I hope that makes things a little more helpful.

---

### Post by Gina on 2008-07-16
> **Raptor45 said:**
> I merged a bunch of stuff from 23meg's [old post]("http://ubuntuforums.org/showthread.php?t=600644"). I hope that makes things a little more helpful.Very good :) Now if this thread could be made Sticky...  It disappears from sight at times.

---

### Post by philinux on 2008-07-16
> **Gina said:**
> Good :) Now if 23meg (or someone) could copy that to this forum... :)  Or maybe this thread should be made Sticky - it disappears from sight at times.

+1 for the Sticky, there'll soon be a ton of newbies having a go when they see how good it is.

---

### Post by dr_kabuto on 2008-07-16
Hi guys,
just tried today upgrading to Intrepid.
As usual, typed "sudo upgrade-manager -d" and after a while a window popped up with this message (sorry the unwanted mixed English/Italian translation):

"An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

Nel caso non rientrasse in nessuno di questi casi, segnalare questo evento come bug del pacchetto «update-manager» e includere nella segnalazione i file in «/var/log/dist-upgrade/»."

Surely I have packaged from external repository, and packages from getdeb.org, but I've never had this problem with previous releases, so before I submit a bug report, is anyone here solved this problem?

Thanks!

---

### Post by BwackNinja on 2008-07-16
I'd actually recomend upgrading through synaptic instead of update-manager. A simple "mark all upgrades" and then "apply" will tell you all that's being removed, upgraded, and newly installed. It also takes a lot of trouble out of upgrading all your xserver stuff (I've done this twice already).

---

### Post by madjr on 2008-07-17
**@Raptor45**

you forgot to add the **Unetbootin** option

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)



not everyone wants to burn CDs for every alpha/beta/rc

---

### Post by psyke83 on 2008-07-17
> **BwackNinja said:**
> I'd actually recomend upgrading through synaptic instead of update-manager. A simple "mark all upgrades" and then "apply" will tell you all that's being removed, upgraded, and newly installed. It also takes a lot of trouble out of upgrading all your xserver stuff (I've done this twice already).

I would counter that it should be done via apt-get or aptitude. If you want to test a development release, you really need to have at least a basic understanding of the terminal, especially when (notice I didn't say "if") things go wrong.

---

### Post by BwackNinja on 2008-07-17
> **psyke83 said:**
> I would counter that it should be done via apt-get or aptitude. If you want to test a development release, you really need to have at least a basic understanding of the terminal, especially when (notice I didn't say "if") things go wrong.

I agree with the need to be able to use a terminal well for those situations that would require it, but any task more easily completed using a gui is probably better done that way. Upgrading through the terminal may seem an adequate prerequisite to dealing with a development release, but regardless, people will follow guides on how to do it anyway, even without knowing what the commands specifically do, though expecting they come from a trustworthy source. The best I think can be done is a word of warning, which will deter everyone who doesn't know what they are doing except the more reckless ones.


Also - another way of installing without a CD - [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093) I've done it, so I know it still works, but make sure you have up to date vmlinuz & initrd.gz downloaded, not the edgy ones linked (just modify the download link to say "intrepid" instead of "edgy").

---

### Post by philinux on 2008-07-17
Regarding burning cd's I've only ever used cdrw's so I don't make any coasters.

---

### Post by arpanaut on 2008-07-20
I don't usually do this, but I think this thread needs to be on the front page of this section...

For the Seekers

So:
TTT

---

### Post by InfinityCircuit on 2008-07-20
> **psyke83 said:**
> Raptor45,

*Unfortunately, even this rule of thumb has exceptions. Sometimes obsolete packages are deliberately marked for uninstallation - and how is a user supposed to know when this is the case? Experience and research.

Just use aptitude.  It will tell you.

---

### Post by jerrylamos on 2008-07-21
> **arpanaut said:**
> I don't usually do this, but I think this thread needs to be on the front page of this section...

For the Seekers

So:
TTT

I'm for that.  A bunch of us are on the early software (punishment addicts) and could use some pointers on how to be useful.

Jerry

---

### Post by Mr. Picklesworth on 2008-07-22
As a nice rule of thumb, any update that breaks ubuntu-desktop (and thus requests the removal of it) is probably unsafe.

---

### Post by jerrylamos on 2008-07-22
> **BwackNinja said:**
> I agree with the need to be able to use a terminal well for those situations that would require it, but any task more easily completed using a gui is probably better done that way.....


GUI's are O.K. when they work!  Lots of times, example I want to delete something, either I don't have permission (!) to do it, or it wants to move the junk to trash, or whatever.  Easier to crank up a terminal.

Or I'll be editing something and the GUI won't save it.  "You don't have permission" to save the file, or to save in that folder, or I don't know what its trouble is.  So I crank up terminal like I've been doing since 1982.

Or to do something you have to go thru GUI window after GUI window after GUI window.... KDE is a good case of this.  Trying to remember what sequence of many windows to get to do what I want to do, example change screen resolution.  Or Vista....

Jerry

---

