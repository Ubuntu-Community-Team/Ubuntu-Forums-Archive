---
title: "upgrading from 18.04 to 22.04 without losing applications"
date: 2022-09-10
forum: Installation &amp; Upgrades
---

### Post by brightstargiftss on 2022-09-10
Been using 18.04 since it cam out. I currently have hundreds of applications that have been compiled against older libraries and they have not been upgraded to work with newer libraries. 
Lately, I've been trying several applications that require newer libraries such as glibc, etc. which aren't available for 18.04. 
It seems like the only option I have is to upgrade to 22.04 although I don't need any of the new features of it. I'm very happy with how 18.04 works for me. I found it to be the most stable version. 
I tried 22.04 and didn't like it. Had a lot of problems with it on a laptop.

I know I can run 22.04 in a virtual machine if I had to.

So, my question is can I upgrade without losing all my old applications? If so, how since newer libraries will be installed?

---

### Post by guiverc on 2022-09-10
It'll depend on what applications, libraries & toolkits that you have installed, including what package system they are.

If it's a *snap* package, packages from Ubuntu 16.04 LTS, or Ubuntu Core 16, will run on any release which is a benefit of the *snap* packages; ie. if you upgrade from Ubuntu Core 16 through to Ubuntu Core 22; the user applications will remain untouched as only the base system applies; If using Ubuntu 16.04 or 22.04 (or 18.04 in your case), the same applies to the *snap* packages you have installed.

The system I'm using now is running Ubuntu *kinetic* (the *development* release), and it contains packages I installed when I initially installed the system whilst on *artful* (17.10). There are packages that are *unchanged *(here I'm talking *deb* packages), and others that have been upgraded many many times in my *six monthly* *release-upgrade* cycle. Whether or not they upgrade/stay-the-same is dependent on their *depends* rules and what libraries/toolkits (*if any*) they use - so you'll need to look at what application matter and assess.

**Yes** you can upgrade without loosing applications, but the answer may also be a more complex **maybe**, or **no** - depending on details you did not provide. You also didn't indicate if you're talking about a Server installation, or Desktop installation, if they are third party packages (*more complex to know*) or Ubuntu repository software. I've also ignored *appimage, flatpak, or compiled from source* too.

---

### Post by Paddy Landau on 2022-09-10
In addition to what @guiverc said, which is all correct, bear in mind that every release has an expiry date. Ubuntu 18.04 will cease to be supported in April 2023 (you can opt into security updates after that for another five years, but all apps will grow badly out of date).

You will need to upgrade at some point, and not just because of Ubuntu's release cycle; also because libraries progress and evolve. They, too, will grow badly out of date.

I think that the most important question is this:
> **brightstargiftss said:**
> I tried 22.04 and didn't like it. Had a lot of problems with it on a laptop.
That's what you really need to address. You mentioned, "a laptop". Did that laptop also run Ubuntu 18.04 previously? If not, it might be that the laptop has hardware that Linux doesn't support. It's unlikely that you'll have much problem upgrading from 18.04 to 22.04.

The best idea is to create a Live USB with Ubuntu 22.04, and test it on your computer (without installing) to see how it works. If everything works correctly, you'll be good to upgrade.

Last point: Please back up your data before upgrading. Although the upgrade path has been well tested by many people, there's always a small chance of a fatal error.

---

### Post by Paddy Landau on 2022-09-10
One more thing. It's possible to back up your entire hard drive, so that if the upgrade to Ubuntu 22.04 is a total disaster, you can restore your entire hard drive back to what it was before the upgrade.

Look at Clonezilla; it's not terribly user-friendly, but it's solid. Also consider Rescuezilla, which is a GUI front-end for Clonezilla.

---

### Post by Dennis N on 2022-09-10
I would hang on to the 18.04, not attempt an upgrade, and subscribe to the ESM ([Extended Security Maintainance]("https://ubuntu.com/security/esm")) when the time comes.

---

### Post by joshua123456 on 2022-09-10
> **Dennis N said:**
> I would hang on to the 18.04, not attempt an upgrade, and subscribe to the ESM ([Extended Security Maintainance]("https://ubuntu.com/security/esm")) when the time comes.

I am just wondering why would you advise someone to stick with Ubuntu 18.04 and sign up for ESM? This seems quite drastic. In my opinion 18.04 is 4,5 years old and getting out of date really.

If the topic starter really doesn't like ubuntu 22.04, I would advise him to give it another try, and if still 22.04 is been disliked it might be an option to move to another distro.

---

### Post by TheFu on 2022-09-10
> **joshua123456 said:**
> I am just wondering why would you advise someone to stick with Ubuntu 18.04 and sign up for ESM? This seems quite drastic. In my opinion 18.04 is 4,5 years old and getting out of date really.

If the topic starter really doesn't like ubuntu 22.04, I would advise him to give it another try, and if still 22.04 is been disliked it might be an option to move to another distro.

Not at all.  If a system is working how you like and it is available for ESM - like Ubuntu Server and Ubuntu Gnome Desktop are, AND you are willing to only get security updates, why change?

Don't get confused.  Most DEs in the Ubuntu 18.04  family (XFCE, LXDE, Mate, Gnome2, and others) lost support last year (they get 3 yrs, not 5) and are not eligible for ESM.

Old doesn't mean bad.  It means stable and understood, provided security patches are still being created for it.
"New" means unproven and often, unstable.
"New" is the enemy of "stable".  Never forget that.

However, there is a point where keeping really old software that isn't supported is extremely risky.  Kernels lose support. This year, there have been 2 remote attacks against the Linux kernel, so if someone hasn't updated for both of those updates (at least, there are other reasons), then if someone can reach the linux device remotely, they can completely pwn the system.

OTOH, if you compiled the programs and libraries, then you've already been managing the applications and applying security patches. If you haven't, then you've accepted the risks -even if you don't realize it.

When compiling and installing manually compiled stuff, it is smart to keep them in specific directories, not connected to any package managers.  Normally, this is where /usr/local/ stuff happens.  If you did that, backup everything you don't want to lose, then do a fresh install, and restore /usr/local/ - most things should work, unless they are compiled and linked using ordinal positions into libraries, not names or symbols.  libc has definitely changed over these years.

Before doing any upgrade, you should backup anything you cannot lose.  For some people, that is everything. I found clonezilla to be too hard.  ddrescue or fsarchiver is how I'd do it for a full disk image need. I seldom need that.

For others like me, I'll backup the list of manually installed APT packages (apt-mark showmanual). I don't manually install .deb files anymore. Those are known to break APT dependencies.  When I do need to compile specific programs, I'll place those and dependent libraries under /usr/local/ ... which is completely backed up nightly.  Well, since I do versioned backups, only changes are backed up, but the idea is the almost the same.  Using a backup tool that does versioning is the way to have 90-200 days of versioned backups that don't require having 90+ disks.  I'm also selective to backup only the stuff that is needed to recreate the install in 15-45 minutes, should something bad happen.  These backups are able to be installed to different hardware or even for OS migrations. Of course, the restore process needs to be selective for the OS stuff, but for data, they are pretty bonehead.  Just put the data back where it was on the source system.  When I was first creating these backups, using selective areas, I didn't get everything needed the first try.  It took a few tries to get it worked out. That was nearly 14 yrs ago.  I've had to migrate and restore systems multiple times since then.  I don't think there is any faster, more efficient (storage and time), flexible, way to have backups and to be able to restore them onto completely new hardware.

When I was new to Linux, like most other people, I wanted a bit-for-bit clone, because I didn't know where important files were stored or the internals of which files should NOT be restored onto a new system with a fresh OS install.  Just know that the first step in my restore process is to install a minimal system of the OS version I want, then add the data and specific system+user settings backup.  The last step is to feed the list of manually installed applications back into APT to have those re-installed into the new system.  All of this takes about 45 min, worst case.

Also, since newer, but stable applications in a 1 yr old LTS release are probably well tested, I get newer stuff, but it is still stable.

Very few applications need to be the latest to do what I need.  I self-host most services, so when tweeter or face-steal change, I don't care or need new versions of programs to interface with them.

I don't touch non-LTS releases.  Having to reinstall an OS every 6 months isn't worth my time.  I did my time compiling "new" stuff constantly in the 1990s. I won't be doing that very often anymore.   Whatever versions are provided by the Canonical LTS repos is almost always fine. Perhaps 1:1000 times, I'll need a specific version of some program.  Across my 20-ish systems, I've compiled/ported perhaps 4 things.  Maintaining systems like this is pretty easy ... but things do fail from time to time.

If you are compiling your own versions, I'd strongly recommend creating self-contained runtime directories like we do for non-published programs.  What does that mean?```

program_a
&#9500;&#9472;&#9472; bin
&#9500;&#9472;&#9472; doc
&#9500;&#9472;&#9472; etc
&#9500;&#9472;&#9472; log
&#9492;&#9472;&#9472; lib
program_b
&#9500;&#9472;&#9472; bin
&#9500;&#9472;&#9472; doc
&#9500;&#9472;&#9472; etc
&#9500;&#9472;&#9472; log
&#9492;&#9472;&#9472; lib
...

```
Create startup scripts in the bin/ directory for each that sets the LD_LIBRARY_PATH as needed to find ../lib/ first and ../etc/ for config files.  The way distros put binaries in /usr/bin and settings in /etc/ and logs in /var/logs/ was decided by the packaging teams. It isn't historically how Unix did things. The directory examples above are how we did it.  Then we'd setup some variables in the bin/program_a_start script:
```

#!/bin/bash 

PROG_HOME=/usr/local/program_a
PROG_BIN="$PROG_HOME"/bin
PROG_LIB="$PROG_HOME"/lib
PROG_ETC="$PROG_HOME"/etc
export LD_LIBRARY_PATH="$PROG_LIB":"$LD_LIBRARY_PATH"
"$PROG_BIN"/program_a   -C "$PROG_ETC"/.progarc   "$@"

```
Easy.  Set any other environment variables needed - JAVA_HOME, ORACLE_HOME, whatever too, just before the last line.  The .../BIN and ../ETC aren't used by the program, but could be.  I'm showing the -C option to specify a config file, but it would be common for a default file to be "found" in the expected locations.

If you look at thunderbird or firefox or most big programs, we don't actually run the program, but a script that sets some environment variables first.

For example: 
```
$ file /usr/bin/firefox
/usr/bin/firefox: symbolic link to ../lib/firefox/firefox.sh
```
See?

---

### Post by mIk3_08 on 2022-09-11
> **brightstargiftss said:**
> It seems like the only option I have is  to upgrade to 22.04 although I don't need any of the new features of  it. I'm very happy with how 18.04 works for me. I found it to be the  most stable version. 
I tried 22.04 and didn't like it. Had a lot of problems with it on a laptop.
I know I can run 22.04 in a virtual machine if I had to.
So, my question is can I upgrade without losing all my old applications?  If so, how since newer libraries will be installed?

I am  sure your applications won't be lose but I am sure it wont be running  the same things as normal because 18.04 uses python2.7 as default and  22.04 uses python3.10  as default. In this way, application that depends  on python2.7 won't easily work on  python3.10. you must also have to  upgrade those applications so it will work to python3.10. Not only  application will be lose also your drivers too. In my case, FingerPrints  which is so very important to me. And also I manage to upgrade my  kernel from 5.4 to 5.15 everything is alright during the process but  some of my attach device wont run successfully and Glad I manage it  already. As everyone says that Linux is not MS Windows. That is a fact!  :-D Things here in Linux World is not the same as MS Windows. It is the  FACT that Linux is a ROCK SOLID Operating System. Desktop, Server,  Cloud.
My advise if you decide to upgrade your Operating System to a  higher release back up your system. There are a lot of application that  is very secure to use. Mine, I uses clonezilla  "expert mode" but as  what TheFu says, ...
[QUOTE=TheFu]Before doing any upgrade, you should backup anything you cannot lose.   For some people, that is everything. I found clonezilla to be too hard.   ddrescue or fsarchiver is how I'd do it for a full disk image need. I  seldom need that.[/QUOTE]
I better follow what TheFu says. because  you might accidentally erase the important files/system that you plan to  back up for some reasons. Regards and cheers.

---

### Post by Paddy Landau on 2022-09-11
> **TheFu said:**
> Not at all. If a system is working how you like and it is available for ESM - like Ubuntu Server and Ubuntu Gnome Desktop are, AND you are willing to only get security updates, why change?
You make tremendous sense, @TheFu. There is one small but important point that I think needs answering, which is your question, "Why change?"

The reason why is that eventually you will be forced to change, and if you've waited a long time, the change will be wrenching. Too much would have changed from "then" to "now", and the problems could be overwhelming.

For this reason, it's better to keep upgrading regularly in order to keep important changes gradual, done in phases, rather than a massive change in one fell swoop. It keeps you in control, and creates fewer problems at a time. Ubuntu's two-yearly LTS cycle, in my experience, is a good compromise.

**To the OP:** When I upgraded from Ubuntu 20.04 to 22.04, I created a virtual machine (VM) to test everything first. That way, I knew in advance what would work, what wouldn't work, and what to do about it. If you have sufficient RAM, I recommend this route, because a VM allows you to take a snapshot before doing anything. This allows you to roll back in an instant and try again differently. It saved me a lot of hassle when I upgraded for real!
> **mIk3_08 said:**
> I manage to upgrade my kernel from 5.4 to 5.15
[s]As 5.4 is far into the future, I imagine that you meant something else :)[/s] Oops, that was wrong :redface:

---

### Post by mIk3_08 on 2022-09-11
> **Paddy Landau said:**
> As 5.4 is far into the future, I imagine that you meant something else :) Unbelievable right? But I did. The process is not advisable though. But I made it. :-D That's how Linux Ubuntu works. Make the impossible possible. 
> **Paddy Landau said:**
> 
**To the OP:** When I upgraded from Ubuntu 20.04 to 22.04, I created a  virtual machine (VM) to test everything first. That way, I knew in  advance what would work, what wouldn't work, and what to do about it. If  you have sufficient RAM, I recommend this route, because a VM allows  you to take a snapshot before doing anything. This allows you to roll  back in an instant and try again differently. It saved me a lot of  hassle when I upgraded for real! Yes. This is good thing but I think it needs a good hardware specially ssd/hdd, RAM etc. Thanks for the advice.   Regards and cheers

---

### Post by brightstargiftss on 2022-09-11
Thank you everyone for taking the time to answer my question. In the past, I've simply removed my current version disk and put a new disk in  and installed the new OS. Keeping the old disk, I simply copied anything I needed over to the new disk, keeping the old disk for a couple of years, just in case. The laptop that I mentioned, had 18.04 on it and I upgraded to 22.04, when it was just released. Things didn't work very well and I reinstalled 18.04. 

This is for my everyday desktop. It's been extremely stable even though I do a lot of experimenting on it. I started using Linux in 1995. Tried almost every distro out there. Keep coming back to Kubuntu. Been using only Linux since that time. I have a MAC Pro G5 sitting next to it. Haven't touched windows in over 10 years. 

I keep several backup to 2 different 64 TB Nas machines so I'm always covered. I used a lot of old programs that I love. I've tried using newer ones but they always seem to lack features I need. That is one of my biggest complaints with upgrading. They always throw in new programs that don't seem to work as well as the old ones.

I have several appimage programs and no flatpacks or any other container applications. I've compiled most of my applications from source. A lot of the newer applications I want to try don't come in any container and when I try to compile them, they complain about not having the latest libraries. I haven't thought about creating compartments in the filesystem to run certain programs with certain libraries. Just seem like a lot of work when I can upgrade and apt a program  and run it. 

I think I'll put in another disk and dual boot for awhile to see if I can work out the kinks and learn to live with whatever programs they throw in 22.04. 

Thank you, everyone again. You all gave me things to think about.

---

### Post by brightstargiftss on 2022-09-11
Thank you everyone for taking the time to answer my question. In the  past, I've simply removed my current version disk and put a new disk in   and installed the new OS. Keeping the old disk, I simply copied  anything I needed over to the new disk, keeping the old disk for a  couple of years, just in case. The laptop that I mentioned, had 18.04 on  it and I upgraded to 22.04, when it was just released. Things didn't  work very well and I reinstalled 18.04. 

This is for my everyday  desktop. It's been extremely stable even though I do a lot of  experimenting on it. I started using Linux in 1995. Tried almost every  distro out there. Keep coming back to Kubuntu. Been using only Linux  since that time. I have a MAC Pro G5 sitting next to it. Haven't touched  windows in over 10 years. 

I keep several backup to 2 different  64 TB Nas machines so I'm always covered. I used a lot of old programs  that I love. I've tried using newer ones but they always seem to lack  features I need. That is one of my biggest complaints with upgrading.  They always throw in new programs that don't seem to work as well as the  old ones.

I have several appimage programs and no flatpacks or  any other container applications. I've compiled most of my applications  from source. A lot of the newer applications I want to try don't come in  any container and when I try to compile them, they complain about not  having the latest libraries. I haven't thought about creating  compartments in the filesystem to run certain programs with certain  libraries. Just seem like a lot of work when I can upgrade and apt a  program  and run it. 

I think I'll put in another disk and dual  boot for awhile to see if I can work out the kinks and learn to live  with whatever programs they throw in 22.04. 

Thank you, everyone again. You all gave me things to think about.

---

### Post by Paddy Landau on 2022-09-11
> **mIk3_08 said:**
> Unbelievable right? But I did.
I realise that I misread and misunderstood :redface: so sorry about that!
> **brightstargiftss said:**
> I have several appimage programs and no flatpacks or any other container applications. I've compiled most of my applications from source.
Compiling from source will always give you dependency problems eventually. That's one of the two major problems that container apps were meant to solve, and mostly do so successfully.

Appimages are a good choice of container app if you don't want automatic updates and aren't worried about implementing a security model. (It's possible to automate their updates, but I believe that it's a bit of a chore to make it work.)

Flatpaks are a good choice of container app if you want automatic updates (you can turn off automatic updates), and the freedom to tailor the security model for each app.

Snaps are a good choice of container app if you want automatic updates, and are happy to be restricted to the security model that you're presented with.

I would say that if you have the choice between compiling from source, or using one of the container apps (appimage, flatpak, snap) go for the latter. You will eliminate a lot of dependency hell. If you don't have a choice, I think that TheFu made some excellent suggestions for how to handle it.

---

### Post by TheFu on 2022-09-11
I agree with Paddy on the AppImages, Flatpak and Snaps.  22.04 comes with snaps and you'll likely have a few.
I think Kubuntu 18.04 support ended last year, BTW: [https://community.kde.org/Kubuntu/Policies#Long_Term_Support_.28LTS.29](https://community.kde.org/Kubuntu/Policies#Long_Term_Support_.28LTS.29)
and
[https://askubuntu.com/questions/1393895/lts-support-for-kubuntu-vs-ubuntu](https://askubuntu.com/questions/1393895/lts-support-for-kubuntu-vs-ubuntu)
Beware.

Take the (apt-mark showmanual) output, save that to a file, and keep that to feed into the new install.

BTW, /usr/local/{program {a... z}/  directories can be automated using an old tool called epkg.  By now, there are probably 5 other projects using that name, so look for the one around package management/system installs.  I think it works with tgz files for different versions of a program and creates a non-version symbolic link from /usr/local/programA ---> /usr/local/programA-v99.43.4
So the active program is easily selectible (that doesn't seem to be a word?). I've been using symlinks for stuff like this for decades.  Here's an appimage directory on a desktop:
```
/usr/local/appimages$ ls -F
drawio-x86_64-14.6.13.AppImage*
drawio-x86_64-14.6.13.AppImage-get
FreeTube_0.17.0_amd64.AppImage*
FreeTube_0.17.1_amd64.AppImage*
FreeTube.AppImage-get
kdenlive-20.12.1c-x86_64.appimage*
kdenlive-20.12.1c-x86_64.appimage-get
LosslessCut-linux.AppImage-get
LosslessCut-linux-x86_64-3.46.2.AppImage*
roku-remote-tool-linux64.AppImage*
streamlink-3.1.1-1-cp310-cp310-manylinux2014_x86_64.AppImage*
VidCutter-6.0.5.1-x86_64.AppImage*
VidCutter-6.0.5.1-x86_64.AppImage-get

```
In my HOME (or /usr/local/bin/, are non-version symlinks to the current version of an appimage I want as default.  The ......appimage-get files are just text notes for where to get an update.  About once every month or two, I'll manually get a new AppImage if one is available.  Some of the programs check at startup for a new release.  Files in my /usr/local/ area are all root:root owned with permissions that make sense for the type of files. Updates don't happen without my knowledge. AppImages that I don't use much don't get updates very often. The list above should show that for apps that are known to people here.  I've heard rumors that someone is/will setup an AppImage update tool and standards. That would be nice. [https://www.omgubuntu.co.uk/2021/12/appimage-pool-for-linux-desktops](https://www.omgubuntu.co.uk/2021/12/appimage-pool-for-linux-desktops) ... GUIs for updates don't work for me. That's a personal issue.

Snaps are broken by design, IMHO. They don't work on most of my systems, though Canonical still installs them and does updates. The lack of local control over the permissions (where they can access storage, mainly) and bloated package+support packages are my main issue.

Flatpaks do allow local control, so they have the best parts of what's lacking in AppImages and the ability to relax some runtime constraints.  I don't mind runtime constraints provide they work for my environment and needs.  I'm just used to setting up those constraints myself using other tools.

---

### Post by Paddy Landau on 2022-09-11
> **TheFu said:**
> … selectible (that doesn't seem to be a word?)
selectable :) English can be confusing.
> **TheFu said:**
> I've heard rumors that someone is/will setup an AppImage update tool and standards. That would be nice. 
Standard non-GUI tools already exist, and you even make appimages self-updateable, according to the [official documentation]("https://docs.appimage.org/packaging-guide/optional/updates.html"). I haven't tried, but you might find it useful.
> **TheFu said:**
> Snaps are broken by design, IMHO.
I used to like snaps a lot, but then their inflexibility with security models became a serious issue. For example, I can't use the snap version of Gedit, because I can't use it to edit or even view system files. Flatpak is far superior, with its ability to tweak every aspect of the security model ([Flatseal]("https://flathub.org/apps/details/com.github.tchx84.Flatseal") is nice for people who prefer the GUI). Its only flaw is that [FONT=courier new]/etc[/FONT] and [FONT=courier new]/usr[/FONT] are internally mapped to [FONT=courier new]/run/host/etc[/FONT] and [FONT=courier new]/run/host/usr[/FONT] respectively, so it's a little inconvenient, but nothing serious.

---

### Post by TheFu on 2022-09-11
> **Paddy Landau said:**
>   For example, I can't use the snap version of Gedit, because I can't use it to edit or even view system files.  

Even using sudoedit?  
```

export EDITOR=gedit
sudoedit /path/to some/system/file

```
I haven't tried it, but sudoedit copies the file to be edited elsewhere, then runs the editor under your normal account.  When completed, it copies the file back and resets the owner/group and permissions like they were.

---

### Post by Paddy Landau on 2022-09-12
> **TheFu said:**
> Even using sudoedit?
Not even with [FONT=courier new]sudoedit[/FONT]!

[FONT=courier new]sudoedit[/FONT] places the temporary file in [FONT=courier new]/var/tmp[/FONT]. The security model for the snap version of Gedit disallows access outside selected directories in your home. Even [FONT=courier new]~/.bashrc[/FONT] or files within [FONT=courier new]~/.config[/FONT] and [FONT=courier new]~/.local[/FONT] are disallowed. (It used to be so bad that I couldn't edit my own scripts in [FONT=courier new]~/bin[/FONT] with the snap version, but the devs at least fixed that.)

There's a "classic" mode that you can use in snap to overcome this, but the devs disabled this option for Gedit. This is an example of a paranoid security level.

I raised a [bug report]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1897562") for this two years ago, but I'm not holding my breath.

Your only choices are to install from the standard repositories or, if you need the latest version, to use the flatpak version and tweak Gedit's security model. I've tested flatpak, and it works, albeit that you need to remember the mapping from [FONT=courier new]/etc[/FONT] and [FONT=courier new]/usr[/FONT] to [FONT=courier new]/run/host/etc[/FONT] and [FONT=courier new]/run/host/usr[/FONT].

---

