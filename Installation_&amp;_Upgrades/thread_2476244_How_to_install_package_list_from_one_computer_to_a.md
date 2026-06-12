---
title: "How to install package list from one computer to another (22.04)"
date: 2022-06-20
forum: Installation &amp; Upgrades
---

### Post by NTL2009 on 2022-06-20
I did a fresh install of Xubuntu 22.04 on my older laptop (was 18.04), wiping all the old stuff, and I took quite a bit of time getting the programs I use installed and the desktop configured.

I just installed (fresh) 22.04 on my newer laptop (was 20.04), and I want to use the package list from the first on the second. Following instructions here (and other places),

[https://askubuntu.com/questions/1092567/how-to-get-package-list-from-one-pc-and-install-that-on-another-pc](https://askubuntu.com/questions/1092567/how-to-get-package-list-from-one-pc-and-install-that-on-another-pc)

 I was able to create the list. But when I try to install it, I just get a long list of  "E: Unable to locate package install".

I think those instructions are outdated? I found something recent (lost the link?) but that was similar and didn't work for me.

I'm also concerned, that list has ~ 2300 packages. I really don't want to reinstall everything, just the stuff I did manually (maybe I can get that from Synaptics, I did almost every install through that so it would capture the history). I'm afraid some of those packages were for the hardware for the older laptop, and will mess up my newer one.

Thoughts?

---

### Post by deadflowr on 2022-06-21
You can use the command posted here: [https://ubuntuforums.org/showthread.php?t=2470869&p=14075616#post14075616]("https://ubuntuforums.org/showthread.php?t=2470869&p=14075616#post14075616")
to get a list which should show only what you have installed, mostly.
Then probably use Ubuntu's online package search page here: [https://packages.ubuntu.com/]("https://packages.ubuntu.com/")
to check if they have versions for the new release.
(Sometimes packages are removed or renamed between releases.
It's unfortunate but it happens)

---

### Post by NTL2009 on 2022-06-21
**THANK YOU!**  This worked for me (NOTE - I'm going from the same version, Xubuntu 22.04 to 22.04, just different laptops). The only 'tweak' I needed was to remove any already installed packages from the file that was generated from the "source" laptop. This was mostly some language packs that were installed after boot, and/or after starting an app (libreoffice?), and a few I installed to check some things, so no big deal.

That command from the 1st link was:
```
comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc  /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort  -u) >> ~/manually_installed.txt
```

And yes, it gave me that much shorter list of just the manually installed apps. And when I went to install, I found this command at this link:
[https://www.hostinger.com/tutorials/how-to-list-installed-packages-on-ubuntu/](https://www.hostinger.com/tutorials/how-to-list-installed-packages-on-ubuntu/)
```
sudo xargs -a <your_filename.txt> apt install
```

That's where I got the "already installed" response, and I didn't know if there is a way to just skip them, but I just deleted them from the 'source' file instead, which was easy. That got me from 39 packages to 26 (which is still time consuming to do manually) - the original method I read about gave ~ 2300 packages! Of course, the list from the command was much, much longer than the 26, as that pulls in all the dependencies, but it still took just ~ 4 minutes to complete the download and install. And everything I tried shows up in Whisker-Menu and ran. Awesome! Now I just have to see if I can get some of the specific config files that I've tweaked on the source moved OK. 

**Separately - Now here is something I don't understand -** I hope this doesn't come across as a rant, I'm really trying to be constructive. I love using Xubuntu have been using it as my daily machine since 2015, 14.04, 18.04, 20.04. 22.04 on several machines: But why does there seem to be so many little things I need to search for, find conflicting/old info, then come to a forum to ask? **I really, really appreciate the help that you and many others give,** but isn't there some good central tutorial space for these things that get asked time and time again? I'm not really a coder, I don't understand a lot of the 'under the hood' stuff, but I'd be more than willing to help with documenting these things when I get solutions. 

I've run into a number of these - the Xubuntu installer has a long standing bug, if you try to install on an external drive, and tell it to use the external drive as the boot device (so it can be moved to another computer), it just installs the boot on the internal drive anyhow. I found a work-around that worked for me (clear the boot, efi flags on the internal drive), but if this is a difficult fix, can't they at least document it, preferably with a warning dialog in the installer itself, and a link to workarounds. Setting up samba to share a Public folder has changed, but I keep finding the old info that doesn't apply, over and over again.

Am I missing something? Is there a way I can help, where this stuff would get into some centralized place that would be easy for people to check?

---

### Post by #&amp;thj^% on 2022-06-21
> **NTL2009 said:**
> **THANK YOU!** 
but isn't there some good central tutorial space for these things that get asked time and time again? I'm not really a coder, I don't understand a lot of the 'under the hood' stuff, but I'd be more than willing to help with documenting these things when I get solutions. 

happy you found a solution for your thread, and there is a dying sub forum found here: [https://ubuntuforums.org/forumdisplay.php?f=100](https://ubuntuforums.org/forumdisplay.php?f=100)
Seems everyone would rather ask and receive help rather than posting their how to that section. :(

---

### Post by deadflowr on 2022-06-21
> Separately - Now here is something I don't understand - I hope this doesn't come across as a rant, I'm really trying to be constructive. I love using Xubuntu have been using it as my daily machine since 2015, 14.04, 18.04, 20.04. 22.04 on several machines: But why does there seem to be so many little things I need to search for, find conflicting/old info, then come to a forum to ask? I really, really appreciate the help that you and many others give, but isn't there some good central tutorial space for these things that get asked time and time again? I'm not really a coder, I don't understand a lot of the 'under the hood' stuff, but I'd be more than willing to help with documenting these things when I get solutions.
Yeah, it's unfortunate.
Sometimes things change faster than the ability to document them coherently.
Especially for teams such as the Xubuntu developers which are relatively small to begin with.
Teams like it are already stretch very very thin and perhaps do not have the proper resources to fully vet everything they have to.
I'm sure they would love for you to get involved with help keeping documentation or tutorials reliably up to date.
I'd look at their help page here: [https://xubuntu.org/help/]("https://xubuntu.org/help/") as a starting point.

---

### Post by TheFu on 2022-06-21
The problem is that there are many "solutions" which only work for 1 person, but nobody else. So the real answer is, "tell us more about your hardware, software, skills, and other situational stuff, so we can tailor the answer.

Many blog articles are written by people with very little actual knowledge, but they can't say that because they don't know how little they know.

There is help.ubuntu.com ... and there are the wiki.ubuntu.com sites which are sorta like an useless manual and the too-many-details answers, respectively.  I'm not really being fair.  The Desktop Guides are searchable and when you know the correct term, it is nice to find where some setting is buried deep in the menus.  Of course, the menus for the main Ubuntu seem to change every 4 yrs because "new", but this is a problem with most DEs.  Change for the sake of change is proof they are trying new things (not necessarily better).  

There are usually "desktop guides" for the LTS releases of the major flavors.  "Kubuntu Desktop Guide", is an example.

Because we all have slightly different machines, software installed, different configuration choices and hardware connected, that's why a complete 'very detailed' answer can become unwieldy.   For DE answers, we need to know the exact release, the exact DE and version, and if any default settings have been modified.  With those other, paid, OSes, those details aren't needed since there's only 1 DE and changing the defaults for any of those settings is nearly impossible for 90% of users.  The flexibility we enjoy is also a huge problem for people new to Linux desktops.  When someone used to X is confronted with non-X that has been forced on them, if they are a normal person, they wouldn't be so happy unless the specific change solved a personal issue.
Imagine if our cars removed the doors, changed the steering wheel into a joystick, removed the peddles, and swapped all the radio/navigation knobs around every 2-4 yrs?  That's what happened when The Unity DE was introduced and again when Gnome3 was forced onto people.  But I just wanted to watch a local video, why do I need to learn a new DE?

And because Ubuntu changed from release to release, current information may not be accurate for the next release.  At the time it was written, it may have been a perfect guide and much of it can be used in the next release, but not everything.  People creating blogs online want page views to make money, so they really don't want to limit their answer to 1 specific release.  And 2 yrs later, we have "Do X on Ubuntu" that is out of date. Nobody makes money updating an old article.  How-to article writers are paid by the word.

This is part of the reason why there are 20 new articles when a new Ubuntu is released.  They are basically copying the old article, following it on the latest release, capturing new screen shots, and making updates as they go.  Then they publish.  They are cautious not to say anything negative ... which I'm terrible at ... 

My how-to move files and settings, from 1 system to another is basically to use my backup and recovery methods.  It works for system upgrades too, BTW, but there are assumptions about the things and ways the backups are created.

I use the apt-mark method, btw.  I don't remember who I stole that from ... think it was a debian developer after the dpkg --get-selections and --set-selections wasn't working as well.  Plus, with apt-mark, we can ask for "manual"ly installed packages which should drastically reduce the list.

And ... I haven't seen anyone deal with snap packages, appimages or flatpaks in their backups yet.  I deal with appimages by placing them in /usr/local/ and I always backup /usr/local on all my systems.  About 80% of my systems don't have any snaps and I purge the snap stuff completely, so it isn't too important.  On the few systems with snaps, only 1 is used at start up, lxd, so that would definitely be missed.  I backup lxd containers just like I backup full systems, so my restore process would be similar ... but I haven't actually tested it.  Hummmm.  Getting a list of installed snaps is trivial and since there are so few on my systems, reinstalling them would be trivial. Right now, the full list is:
```
$ snap list
Name                               Version                     Rev    Tracking       Publisher   Notes
bare                               1.0                         5      latest/stable  canonical&#10003;  base
core                               16-2.56                     13308  latest/stable  canonical&#10003;  core
core18                             20220428                    2409   latest/stable  canonical&#10003;  base
core20                             20220527                    1518   latest/stable  canonical&#10003;  base
gnome-3-28-1804                    3.28.0-19-g98f9e67.98f9e67  161    latest/stable  canonical&#10003;  -
gtk-common-themes                  0.1-79-ga83e90c             1534   latest/stable  canonical&#10003;  -
kde-frameworks-5-core18            5.61.0                      32     latest/stable  kde&#10003;        -
kde-frameworks-5-qt-5-15-3-core20  5.87.0                      8      latest/stable  kde&#10003;        -
kdiskmark                          2.3.0                       59     latest/stable  jonmagon    -
lxd                                5.2-79c3c3b                 23155  latest/stable  canonical&#10003;  -
scrcpy                             v1.24                       386    latest/stable  sisco311    -
snapd                              2.56                        16010  latest/stable  canonical&#10003;  snapd
```
If those, only 2 are manually installed, scrcpy and kdiskmark.  lxd is automatically installed on all new systems that I've setup.  I haven't used 
kdiskmark or scrcpy in perhaps 6-12 months. I actually don't recall.  Time to purge them. And now:
```
$ snap list
Name    Version      Rev    Tracking       Publisher   Notes
bare    1.0          5      latest/stable  canonical&#10003;  base
core    16-2.56      13308  latest/stable  canonical&#10003;  core
core20  20220527     1518   latest/stable  canonical&#10003;  base
lxd     5.2-79c3c3b  23155  latest/stable  canonical&#10003;  -
snapd   2.56         16010  latest/stable  canonical&#10003;  snapd
```
Much better. I did have to remove the GTK, Gnome, KDE .... and other unused packages manually. I guessed which weren't needed and expected a complaint by snap if I removed something important.  May not need bare and core anymore either. IDK.
LXD has methods to replicate a container to a different system. I've not gotten that working, but haven't spent too much time trying either.  It uses ZFS capabilities.  The system where I wanted to test is completely incompatible with snaps and since lxd is only available as a snap package, it doesn't work.

---

### Post by MAFoElffen on 2022-06-22
I was the person, which came up with the linked post... The command line I came up with there, does use 'apt-mark'... Though, I tweaked that to use it in the UbuntuForums 'system-info' script, linked in my signature line. That "User Installed" packages is is part of the 'system-info.txt' file report...

I edited that section of the report especially to a single column format list, for the purpose of migration/recovery re-installation lists. These lists are, well, unabridged. Meaning some of the packages were installed as dependencies of other packages. I do not worry about those, because if something is already installed, and you install it again, 'apt' just reurns a message saying it didn't need to do that, skips it, and goes on... 

My experience with a general bash script to use that list is that I just use a 'for' loop that reads the packages names and installs them.

But... I created that just for 'apt' packages... That does not deal with any 'Snap' packages... I am adding that to the script (as we speak). That is more like:
```

snap list | awk '{print $1}' | grep -v 'Name' > ~/SnapPackage.list

```
Then use a script to read the file and install the Snap Packages from that list.

I do 'On-Site' migrations with everything saved on (lists and the scripts), and transported between machines on a portable drive, or adhoc/network the two machines together. On doing 'In-House', I use admin network shares for the storage and access of.

---

