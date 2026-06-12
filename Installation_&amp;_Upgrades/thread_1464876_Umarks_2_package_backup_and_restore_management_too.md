---
title: "Umarks 2: package backup and restore management tool"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by lovinglinux on 2010-04-28
Umarks is no longer under development.

---

### Post by wojox on 2010-04-28
Alright I got the beta version downloaded. I'll play around with it tonight. I've already installed Lucid on my laptop. I just need to upgrade my desktop tomorrow.

---

### Post by lovinglinux on 2010-04-28
> **wojox said:**
> Alright I got the beta version downloaded. I'll play around with it tonight. I've already installed Lucid on my laptop. I just need to upgrade my desktop tomorrow.

Thanks. Looking forward to reading your thoughts about it and overall experience.

You can submit bugs at [http://lovinglinux.megabyet.net/?page_id=728](http://lovinglinux.megabyet.net/?page_id=728)

---

### Post by wojox on 2010-04-28
> **lovinglinux said:**
> Thanks. Looking forward to reading your thoughts about it and overall experience.

You can submit bugs at [http://lovinglinux.megabyet.net/?page_id=728](http://lovinglinux.megabyet.net/?page_id=728)

That's pretty cool. You thought of everything. I got it bookmarked. :)

---

### Post by lovinglinux on 2010-04-28
> **wojox said:**
> That's pretty cool. You thought of everything. I got it bookmarked. :)

Thanks. I have been working round-the-clock to make it available before Lucid release. The worst part was making the video tutorials in Lucid, since ogv encoding is totally messed up. There is even a video tutorial with 4 extra minutes containing a static image of my desktop ](*,)

Making the tutorial captions on YouTube takes a lot of time, so I'm not going to replace that video, but I have added a caption with a warning that the user can move on. Not very professional I suppose :)

---

### Post by Bob63 on 2010-04-28
lovinglinux,

Please clarify for me if this tool is supposed to catch ***all*** the repos and ppas users (I) have.

I realize that "my milage may vary" as I am using LinuxMint, so I didn't expect it to catch their repos. However, it only picked up the medibuntu repo, but none of the following repo/ppa:

glx-dock
opera
get-deb
Geza Kovacs (a launchpad ppa)

I'm not trying to be a whiner, and realize that this tool is for Ubuntu and is a beta version. However, discounting the Mint-distro issue, these are customization package and application package sources that some users might like to have available on their fresh install.

Am I jumping the gun?:eek:
Bob63

---

### Post by lovinglinux on 2010-04-29
> **Bob63 said:**
> lovinglinux,

Please clarify for me if this tool is supposed to catch ***all*** the repos and ppas users (I) have.

I realize that "my milage may vary" as I am using LinuxMint, so I didn't expect it to catch their repos. However, it only picked up the medibuntu repo, but none of the following repo/ppa:

glx-dock
opera
get-deb
Geza Kovacs (a launchpad ppa)

I'm not trying to be a whiner, and realize that this tool is for Ubuntu and is a beta version. However, discounting the Mint-distro issue, these are customization package and application package sources that some users might like to have available on their fresh install.

Am I jumping the gun?:eek:
Bob63

First of all, I would like to thank you for suggesting support for repositories sources in the old thread. As you can see, I have changed several things when trying to accommodate the repository support and I'm really excited about this new version. It has the biggest changes since I started to develop Umarks.

The method used to retrieve the repositories is not very elegant. But the underlying structure is already in place now, so I can focus on making this feature better on future versions, without rewriting too much code.

The extension is supposed to catch all launchpad ppa repositories and medibuntu. Nevertheless, bugs are expected, since I have only tested this on my system.

Opera and glx-dock repositories are not supported yet. They can be added and I guess they are very popular. I will include in the next version.

GetDeb.net is not supported, but I should have added it with this release. Thanks for remembering me again about important things to add :)

Geza Kovacs wasn't picked up because you are running Linux Mint. The thing is that I'm using the **add-apt-repository** command to install them, which is supported only on Karmic and Lucid Lynx. The extensions checks for the release codename, in order to decide if the the repositories can be installed by this method or not. Since Linux Mint uses different codenames, is very likely that the extension is skipping the ppa importing/exporting step.

I'm sorry for that. I was looking into making Mint compatible after we "spoke" for the last time, but since then I changed so many things and I saw that the next version of Mint will have a backup tool that can do dpkg selections. So it went to the bottom of my priorities. Anyway, now I can focus on that again. Please don't give up just yet ;)

What version of Mint you are using?

Please post the output of these commands:

```
ls /etc/apt/sources.list.d
```

```
cat /etc/lsb-release
```

```
dpkg --get-selections
```

Don't need to post the entire output of the last command, just report if it does work.

Also, create a new backup, select it and click the info button. Then look into your Firefox profile folder (~/.mozilla/firefox/profile), locate the file umarks.sqlite and attach it (if you don't mind letting me see your user name and installed packages). So I can take a look if anything is missing from the database. That will give some clues about where the code is failing.

I could test Mint on a VM, but Umarks is not playing well on the VM environment here. I'm not sure why yet. So if you provide that information would help a lot.

Additionally, before running the extension, click "Tools >> Error Console" in Firefox, click the "all" button, then type umarks in the code field. Test the extension features and post any errors from the console.

---

### Post by Bob63 on 2010-04-29
lovinglinux,

No problem!  I'm glad to help. I'm not the most knowledgeable person in the world, but with a bit of hand-holding over the rough terrain, I think we can get through this.

Oh, and I am using LinuxMint 8 Helena, based on Ubuntu 9.10. Also, it is the Main release, meaning it is 32-bit.

Here is the first few things you requested.

The output of **ls /etc/apt/sources.list.d**[FONT=Lucida Console]**:**
[/FONT]```
gezakovacs-ppa-helena.list
medibuntu.list
opera.list.save
gezakovacs-ppa-helena.list.save
opera.list
```[I put each one on a separate line for clarity rather than the tab-separated list the ls command outputs.]

I don't know why this is but I discovered that while the sources.list.d file for Geza Kovacs' ppa is named gezakovacs-ppa-helena.list, the contents of the file is:
***"deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) karmic main"*** (without quotes). I haven't been to his page in a month, perhaps, but I recall that he had packages prepared for multiple releases of the OS, i.e. karmic, jaunty, etc. Although you didn't specifically ask for this, here is the contents of apt's **sources.list**
```
deb http://packages.linuxmint.com/ helena main upstream import backport universe multiverse
deb-src http://packages.linuxmint.com/ helena main upstream import backport #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ karmic partner
deb http://packages.medibuntu.org/ karmic free non-free
deb http://repository.glx-dock.org/ubuntu karmic cairo-dock
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```The sources.list is correctly identifying the distro code name for all the repos.

Then, the output of **cat /etc/lsb-release:**
```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=8
RELEASE_NOTES_URL=http://www.linuxmint.com/rel_helena.php
DISTRIB_CODENAME=helena
DISTRIB_DESCRIPTION="Linux Mint 8 Helena - Main Edition"

```As for the Firefox Error Console output, there are some issues I am having, but before I post these I have a couple of add-ons that I want to disable before re-running to ensure they are not coming from or caused by AdBlock or NoScript. I'll get back to you on this after some experimentation.

Other comments:
1) I ran the previous version of the tool after our last "conversation", and it seemed to catch all the packages in line with what we had discussed about Ubuntu vs. Mint. What I didn't consider until after I ran the install side on a fresh Mint 8 installation was the customizations I had done above and beyond the distinction between Mint and Ubuntu. There are certain apps I have installed which were locally compiled and installed using tools like auto-apt and checkinstall. In particular, auto-apt has to be properly set up so it can pull dependencies correctly. Otherwise, future compilations with the tool will fail. You might want to consider adding an informational warning to prospective users who may have similar situations.

2) The tool pulled the nVidia driver package and installed it, but I had to activate it. Until activation, you'll get the "restricted driver available" notification. I had forgot about this point. I watched the tool pull the driver and went "good!", then got the notification and went "huh?" There is probably nothing your tool can do about this as it involves kernel recompilation.

In a similar vein, I also have Sun VirtualBox on my machine. The tool pulled the repo version, but I had the more recent version from Sun. Again, maybe a warning that the tool won't hunt down packages outside the available repos.

Now, if there was a way to search my personal collection of debs in my downloads directory, then do a version comparison...:lolflag:

Thanks for taking the time to listen.
Bob63

---

### Post by lovinglinux on 2010-04-29
> **Bob63 said:**
> lovinglinux,

No problem!  I'm glad to help. I'm not the most knowledgeable person in the world, but with a bit of hand-holding over the rough terrain, I think we can get through this.

Oh, and I am using LinuxMint 8 Helena, based on Ubuntu 9.10. Also, it is the Main release, meaning it is 32-bit.

Here is the first few things you requested.

The output of **ls /etc/apt/sources.list.d**[FONT=Lucida Console]**:**
[/FONT]```
gezakovacs-ppa-helena.list
medibuntu.list
opera.list.save
gezakovacs-ppa-helena.list.save
opera.list
```[I put each one on a separate line for clarity rather than the tab-separated list the ls command outputs.]

I don't know why this is but I discovered that while the sources.list.d file for Geza Kovacs' ppa is named gezakovacs-ppa-helena.list, the contents of the file is:
***"deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) karmic main"*** (without quotes). I haven't been to his page in a month, perhaps, but I recall that he had packages prepared for multiple releases of the OS, i.e. karmic, jaunty, etc. Although you didn't specifically ask for this, here is the contents of apt's **sources.list**
```
deb http://packages.linuxmint.com/ helena main upstream import backport universe multiverse
deb-src http://packages.linuxmint.com/ helena main upstream import backport #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ karmic partner
deb http://packages.medibuntu.org/ karmic free non-free
deb http://repository.glx-dock.org/ubuntu karmic cairo-dock
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```The sources.list is correctly identifying the distro code name for all the repos.

Then, the output of **cat /etc/lsb-release:**
```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=8
RELEASE_NOTES_URL=http://www.linuxmint.com/rel_helena.php
DISTRIB_CODENAME=helena
DISTRIB_DESCRIPTION="Linux Mint 8 Helena - Main Edition"

```As for the Firefox Error Console output, there are some issues I am having, but before I post these I have a couple of add-ons that I want to disable before re-running to ensure they are not coming from or caused by AdBlock or NoScript. I'll get back to you on this after some experimentation.

Other comments:
1) I ran the previous version of the tool after our last "conversation", and it seemed to catch all the packages in line with what we had discussed about Ubuntu vs. Mint. What I didn't consider until after I ran the install side on a fresh Mint 8 installation was the customizations I had done above and beyond the distinction between Mint and Ubuntu. There are certain apps I have installed which were locally compiled and installed using tools like auto-apt and checkinstall. In particular, auto-apt has to be properly set up so it can pull dependencies correctly. Otherwise, future compilations with the tool will fail. You might want to consider adding an informational warning to prospective users who may have similar situations.

2) The tool pulled the nVidia driver package and installed it, but I had to activate it. Until activation, you'll get the "restricted driver available" notification. I had forgot about this point. I watched the tool pull the driver and went "good!", then got the notification and went "huh?" There is probably nothing your tool can do about this as it involves kernel recompilation.

In a similar vein, I also have Sun VirtualBox on my machine. The tool pulled the repo version, but I had the more recent version from Sun. Again, maybe a warning that the tool won't hunt down packages outside the available repos.

Now, if there was a way to search my personal collection of debs in my downloads directory, then do a version comparison...:lolflag:

Thanks for taking the time to listen.
Bob63

Thanks for the feedback. Indeed it won't work yet for several reasons. I need to re-write some stuff to make Mint compatible. Please stay tuned. I will post as soon as I have a beta2 version.

---

### Post by Bob63 on 2010-04-29
lovinglinux,

Here's what I've noticed about using the add-on:
The issues which I had thought might be related to AdBlock/NoScript might actually be either an error with the way the Mint configuration is setup or the way your add-on parses the /etc/lsb-release file. Searching for packages at packages.ubuntu.com returns an error in the webpage because the string provided to search is (besides being the Mint code name) the third line of the file. For Ubuntu, this is the code name and would be fine, but the Mint distro has a different file organization. If you look at the output of the lsb-release file I provided above, line 3 is the uri for the release notes. The distro code name is on line 4 for Mint. This means that none of the package search works quite right for me, although Google is forgiving enough that it at least gave me a search page where I could have followed a link to the package I was looking for (I tried with Gimp and Inkscape).

Not through yet...I had some unused space on my 500GB drive, so I put Ubuntu 9.10 64-bit on and updated it. When I get home later I'll try to replicate my Mint install as closely as possible using the Ubuntu repos and let you know how it goes.

Thanks again,
Bob63

---

### Post by lovinglinux on 2010-04-29
> **Bob63 said:**
> The issues which I had thought might be related to AdBlock/NoScript might actually be either an error with the way the Mint configuration is setup or the way your add-on parses the /etc/lsb-release file. Searching for packages at packages.ubuntu.com returns an error in the webpage because the string provided to search is (besides being the Mint code name) the third line of the file. For Ubuntu, this is the code name and would be fine, but the Mint distro has a different file organization. If you look at the output of the lsb-release file I provided above, line 3 is the uri for the release notes. The distro code name is on line 4 for Mint. This means that none of the package search works quite right for me, although Google is forgiving enough that it at least gave me a search page where I could have followed a link to the package I was looking for (I tried with Gimp and Inkscape).

You are correct. I was initially fetching the info by matching the entity, but then just after the release I decided to fetch it by line number. This is fine for Ubuntu family systems, but not for Mint.

---

### Post by dryicebomb on 2010-04-30
Nice Job, This has to be the coolest linux program i've seen in a decade. thank you for making it.

---

### Post by lovinglinux on 2010-04-30
> **dryicebomb said:**
> Nice Job, This has to be the coolest linux program i've seen in a decade. thank you for making it.

:) You are welcome. Please let me know if you find any bugs.

---

### Post by lovinglinux on 2010-05-01
@Bob63

Linux Mint support is almost ready. I'm just having a hard time with the repositories :)

---

### Post by lovinglinux on 2010-05-01
Cool. Umarks is on [Ubuntu Geek](http://www.ubuntugeek.com/umarks-2backup-and-restore-ubuntu-installed-packages-on-multiple-machines.html).

---

### Post by lovinglinux on 2010-05-02
I have released [version 2.0.0beta2](http://umarks-extension.blogspot.com). There are a lot of improvements, so I recommend anyone using 2.0.0beta1 or previous versions to upgrade using the Beta channel.

Among the changes since 2.0.0beta1 are:

[LIST]
[*]full compatibility with Linux Mint (Isadora, Helena, Gloria, Felicia, Elyssa)
[*]compatibility with "any" third-party repository sources, although only ppa repositories, medibuntu and getdeb will also install authentication keys (still need to work on that)
[*]repositories are no longer installed when restoring the entire backup, so you need to install them before, using the repositories menu. Nevertheless, you can install them all-at-once and the extension will detect which are already installed.
[/LIST]

Please test it and let me know what you think and if you encounter any bugs.

---

### Post by teejcee on 2010-05-11
lovinglinux,

It was last night that I was pondering the existence or otherwise of such an application and what a god-send it would be if it did exist.

Before posting I decided to do the right thing and do a search first and lo-and-behold...this thread.

I am not in need of an upgrade at present but I will try and hook up an old disk somewhere, download and do some testing for you...( I am retired so time isn't really an issue to me...)

Keep up the good work.

TC

---

### Post by lovinglinux on 2010-05-11
> **teejcee said:**
> lovinglinux,

It was last night that I was pondering the existence or otherwise of such an application and what a god-send it would be if it did exist.

Before posting I decided to do the right thing and do a search first and lo-and-behold...this thread.

I am not in need of an upgrade at present but I will try and hook up an old disk somewhere, download and do some testing for you...( I am retired so time isn't really an issue to me...)

Keep up the good work.

TC

Great. Please let me know how it goes.

---

### Post by teejcee on 2010-05-12
> **lovinglinux said:**
> Great. Please let me know how it goes.

It does not go well...

I have installed Umarks 2 but cannot find an icon or anything else to invoke the app.

Ubuntu 9.10 64 bit
Firefox 3.5

Cheers

---

### Post by Bob63 on 2010-05-12
> **teejcee said:**
> It does not go well...

I have installed Umarks 2 but cannot find an icon or anything else to invoke the app.

Ubuntu 9.10 64 bit
Firefox 3.5

Cheers

The icon appears (on my installation) as a large "U" in the lower right on the status bar.

---

### Post by teejcee on 2010-05-12
> **Bob63 said:**
> The icon appears (on my installation) as a large "U" in the lower right on the status bar.

Thanks Bob63....enabling the status bar helped....:oops:

---

### Post by Bob63 on 2010-05-12
> **teejcee said:**
> Thanks Bob63....enabling the status bar helped....:oops:

No prob!

Been in similar myself.:lolflag:

---

### Post by lovinglinux on 2010-05-12
> **teejcee said:**
> Thanks Bob63....enabling the status bar helped....:oops:

I have included instructions about this on all demo videos.

That is something I need to think about. I assume most users will have the status bar enabled. Nevertheless, since this is not an extension that you will use very frequently, I thought would be OK to have only the status bar icon.

---

### Post by Bob63 on 2010-05-13
For me it wasn't an issue because my status bar is always on. Is it easier or harder to have the icon appear at a fixed place? What I'm getting at is perhaps having the icon appear in the Customize box so that the user can put it wherever.

(Personally, I'm such a gadget nut that I'm almost ready to add more toolbars...:-\")

---

### Post by lovinglinux on 2010-05-13
> **Bob63 said:**
> For me it wasn't an issue because my status bar is always on. Is it easier or harder to have the icon appear at a fixed place? What I'm getting at is perhaps having the icon appear in the Customize box so that the user can put it wherever.

(Personally, I'm such a gadget nut that I'm almost ready to add more toolbars...:-\")

It would be simple to add it to the Customize box. I'm going to include on the next version. Nevertheless, several users are not familiar with this feature. 

Making it appear on a fixed place is not a problem, the problem is that users tend to customize their tool bars more than the status bar, so having a fixed tool bar position is not a good option.

---

### Post by lovinglinux on 2010-05-21
Umarks 2.0.0 has been approved by Mozilla and is now available through Firefox add-ons manager updates.

Users that have 2.0.0rc don't need to updated, since they are exactly the same version. Nevertheless, if you want to stop receiving beta releases, then you should install version 2.0.0 from the stable channel.

---

### Post by Muzafsh on 2011-05-15
Hi,

@LovingLinux
Can i have a download link to Umarks 2.0.0, i have tried at many places but with no luck. A sure handy app considering Ubuntu comes up with a new version every six months.

thanks,

---

### Post by Bob63 on 2011-05-15
> **Muzafsh said:**
> Hi,

@LovingLinux
Can i have a download link to Umarks 2.0.0, i have tried at many places but with no luck. A sure handy app considering Ubuntu comes up with a new version every six months.

thanks,
Muzafsh,
I think the reason you can no longer find this is the developer stopped work.
Regards,
Bob

---

### Post by lovinglinux on 2011-05-15
> **Bob63 said:**
> Muzafsh,
I think the reason you can no longer find this is the developer stopped work.
Regards,
Bob

Indeed. I have stopped the development of Umarks, because there was no interest on it.

However, you can generate and restore your package list via command.

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages 
```

Then move the file "my-packages" to the other machine, and there run:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

Sorry for the inconvenience, but the extension was really complicated and the lack of users didn't justified keeping it alive, specially that you can achieve the most important functionality via command or via Synaptic.

---

