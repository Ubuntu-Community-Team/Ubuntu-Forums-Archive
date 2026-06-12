---
title: "Is the new dpkg broken?"
date: 2009-07-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by camper365 on 2009-07-07
I just ran an update and it looks like it tried to update dpkg before anything else, and the update failed. Is dpkg broken for anyone else?

---

### Post by Ratscallion on 2009-07-07
Try doing >  sudo dpkg --configure
If it isn't sorted after that, try sudo apt-get update. The next step, is to give us more info... Try pasting the error?

---

### Post by camper365 on 2009-07-07
Here's the output of the terminal:
```
aaron@truman:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Resolving dependencies...
The following NEW packages will be installed:
  libcompress-bzip2-perl{a} linux-image-2.6.29.5-2-rt{a} 
The following packages will be upgraded:
  byobu debconf debconf-i18n dpkg dpkg-dev gdm gnome-session-canberra hal 
  initramfs-tools libcanberra-gtk-module libcanberra-gtk0 libcanberra0 
  libglib2.0-0 libglib2.0-data libhal-storage1 libhal1 liblircclient0 
  libpci3 libwww-perl linux-image-rt linux-rt nvidia-180-modaliases 
  pciutils screen-profiles ssl-cert update-manager update-manager-core 
  wireless-crda xserver-xorg-video-intel 
29 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/32.5MB of archives. After unpacking 76.0MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 192991 files and directories currently installed.)
Preparing to replace dpkg 1.14.24ubuntu2 (using .../dpkg_1.15.3ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/dpkg_1.15.3ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.15.3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done


```

---

### Post by Ratscallion on 2009-07-07
You're running the safe upgrade thingy I see... I suggest doing the steps mentioned earlier, then try running that again. Maybe, if that doesn't work, you could try going into Synaptic and marking the packages with errors for reinstallation?

---

### Post by camper365 on 2009-07-07
I just manually installed all the packages that needed to be upgraded. I have no problems installing any packages except for dpkg.
By manually, I mean I did the following:

```

cd /var/cache/apt/archives
dpkg -i *packagename*_*version*.deb

```

and I repeated that for every package. When I tried to install dpkg that way, it errored the same way as in aptitude but the rest of them finished just fine.

---

### Post by Ratscallion on 2009-07-07
So everything's fine? Nice to know. Just try a sudo dpkg --configure then sudo apt-get update to make sure it's OK. Glad I could help :)

---

### Post by camper365 on 2009-07-07
> **Ratscallion said:**
> You're running the safe upgrade thingy I see... I suggest doing the steps mentioned earlier, then try running that again. Maybe, if that doesn't work, you could try going into Synaptic and marking the packages with errors for reinstallation?
the problem occurs in any frontend to apt, not just the safe-upgrade



It's not necessarily "fine," because updating via apt doesn't work, I have to do it manually, and dpkg won't install, but everything else is fine. I just think that some of the updates might not be logged.

---

### Post by Ratscallion on 2009-07-08
I suggest checking your repository list in Software Sources for a start. Some of the lists may be *slightly* off, making dpkg go wrong. Try disabling ALL of your THIRD-party lists, and then updating and slowly bring them back, one at a time, until you encounter an error. Once you get an error, that's where the problem lies. However, if you get an error even if they're ALL disabled, then it must be something else.

---

### Post by ranch hand on 2009-07-08
I have not had any problem with dpkg although I have had to run it to get some other updates settled in right.

I would not panic yet at all.  I would wait for tomorrows update and see if that straightens it out.  I suspect that this is somehow connected to the gdm problem as that was causing a re-loggin before updates were completely finished.  May have to do with what they did to fix that (at least for me on my box).  Today is the first I have heard of your problem and today is the first in 3 that I wasn't kicked into re-log before the updates were completely installed.

If not - file a bug.

---

### Post by dinxter on 2009-07-08
the /var/lib/dpkg/info/dpkg.preinst  script  is failing somewhere, you can get more information on why by running 

dpkg --debug=3773 <package name>

---

### Post by camper365 on 2009-07-08
I just ran a
```
sudo aptitude clean
```
and then a full-upgrade again and it redownloaded everything, and the error came again.

---

### Post by Ratscallion on 2009-07-08
Just noticed that you're using Karmic... Seeing as it's still in testing, maybe that could be it all along... Though I wouldn't have thought so... Just a thought.

---

### Post by camper365 on 2009-07-08
> **Ratscallion said:**
> Just noticed that you're using Karmic... Seeing as it's still in testing, maybe that could be it all along... Though I wouldn't have thought so... Just a thought.
I was almost certain that Karmic was the cause, but I was just posting to see if anyone else was having those problems.

---

### Post by ranch hand on 2009-07-08
> **Ratscallion said:**
> Just noticed that you're using Karmic... Seeing as it's still in testing, maybe that could be it all along... Though I wouldn't have thought so... Just a thought.
At the top of the page you will see this is the " Karmic Koala Testing and Discussion" forum.

It is a lot of FUN.  But there is some breakage that the devs seem to be on top of pretty well if you give them a day.  After that it may be due to the system on your box and only a few more and a Bug needs filed so they know about it.

---

### Post by dinxter on 2009-07-08
dpkg scripts can fail for any number of reasons, if you do run it in debug mode though it will give you a lot more information on the problem, by default installation is quiet and not much use in identifying whats gone wrong. 

dpkg --debug=3773 /var/cache/apt/archives/dpkg_1.15.3ubuntu1_i386.deb

---

### Post by xebian on 2009-07-08
> **camper365 said:**
> I was almost certain that Karmic was the cause, but I was just posting to see if anyone else was having those problems.

Just had 2 dpkg upgrade today and no problem both times.

[CODE]

Preparing to replace dpkg 1.15.3ubuntu1 (using .../dpkg_1.15.3.1ubuntu1_amd64.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
Setting up dpkg (1.15.3.1ubuntu1) ...

/[CODE]

---

### Post by phoogkamer on 2009-07-09
I have the same problem with dpkg. Al updates went fine, even dpkg-dev. Did a apt-get clean and apt-get autoclean. After that a update and upgrade, but still errors with dpkg.

Tux

---

### Post by camper365 on 2009-07-09
> **phoogkamer said:**
> I have the same problem with dpkg. Al updates went fine, even dpkg-dev. Did a apt-get clean and apt-get autoclean. After that a update and upgrade, but still errors with dpkg.

Tux

Well, dpkg-dev is just the text files that you include in your code (useful when you compile your programs from source) so it should update properly. Your problem is exactly the same as mine. What kind of computer are you running?

I filed a bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/397498](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/397498)

---

### Post by phoogkamer on 2009-07-10
I am running an Acer Aspire 5051.

---

### Post by camper365 on 2009-07-10
64 bit?

---

### Post by Starks on 2009-07-10
I find it insulting that people aren't owning up to this error and repackaging to fix it and are instead suggesting alternative strategies.

If you still care, here's a log.

```
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
(Reading database ... 411242 files and directories currently installed.)
Preparing to replace dpkg 1.14.24ubuntu2 (using .../dpkg_1.15.3ubuntu1_i386.deb) ...
D000200: process_archive conffile `/etc/dpkg/dpkg.cfg' in package dpkg - conff ?
D000020: process_archive conffile `/etc/dpkg/dpkg.cfg' package=dpkg same hash=f4413ffb515f8f753624ae3bb365b81b
D000200: process_archive conffile `/etc/alternatives/README' in package dpkg - conff ?
D000200: process_archive conffile `/etc/alternatives/README' in package dpkg - conff ? not `/etc/dpkg/dpkg.cfg'
D000200: process_archive conffile `/etc/alternatives/README' in package dpkg - conff ? not `/etc/dpkg/origins/debian'
D000020: process_archive conffile `/etc/alternatives/README' package=dpkg same hash=69c4ba7f08363e998e0f2e244a04f881
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ?
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ? not `/etc/dpkg/dpkg.cfg'
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ? not `/etc/dpkg/origins/debian'
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ? not `/etc/alternatives/README'
D000020: process_archive conffile `/etc/logrotate.d/dpkg' package=dpkg same hash=501f8c90b83c7ea180868ca82e1e82d1
D000200: oldconffsetflags `/etc/dpkg/dpkg.cfg' namenode 0xb37cc40 flags 5
D000200: oldconffsetflags `/etc/dpkg/origins/debian' namenode 0xa1679d4 flags 4
D000200: oldconffsetflags `/etc/alternatives/README' namenode 0xb37cca0 flags 5
D000200: oldconffsetflags `/etc/logrotate.d/dpkg' namenode 0xb37ccd4 flags 5
D000001: process_archive oldversionstatus=installed
D000002: maintainer_script_alternative nonexistent prerm `/var/lib/dpkg/info/dpkg.prerm'
D000002: fork/exec /var/lib/dpkg/[tmp.ci/preinst]("http://tmp.ci/preinst") ( upgrade 1.14.24ubuntu2 )
dpkg: error processing /var/cache/apt/archives/dpkg_1.15.3ubuntu1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
D000002: fork/exec /var/lib/dpkg/[tmp.ci/postrm]("http://tmp.ci/postrm") ( abort-upgrade 1.14.24ubuntu2 )
D000002: fork/exec /var/lib/dpkg/info/dpkg.postinst ( abort-upgrade 1.15.3ubuntu1 )
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
D000010: ensure_pathname_nonexisting running rm -rf
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/reassemble.deb'
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.15.3ubuntu1_i386.deb
```

---

### Post by phoogkamer on 2009-07-12
@camper365

Yes, 64bit. Is there an issue with 64 bit dpkg??
Here is my output:
sudo dpkg --debug=3773 -i dpkg_1.15.3.1ubuntu1_amd64.deb 
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
(Database inlezen ... 139897 bestanden en mappen geïnstalleerd.)
Voorbereiden om dpkg 1.14.24ubuntu2 te vervangen (door dpkg_1.15.3.1ubuntu1_amd64.deb) ...
D000200: process_archive conffile `/etc/dpkg/dpkg.cfg' in package dpkg - conff ?
D000020: process_archive conffile `/etc/dpkg/dpkg.cfg' package=dpkg same hash=f4413ffb515f8f753624ae3bb365b81b
D000200: process_archive conffile `/etc/alternatives/README' in package dpkg - conff ?
D000200: process_archive conffile `/etc/alternatives/README' in package dpkg - conff ? not `/etc/dpkg/dpkg.cfg'
D000200: process_archive conffile `/etc/alternatives/README' in package dpkg - conff ? not `/etc/dpkg/origins/debian'
D000020: process_archive conffile `/etc/alternatives/README' package=dpkg same hash=69c4ba7f08363e998e0f2e244a04f881
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ?
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ? not `/etc/dpkg/dpkg.cfg'
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ? not `/etc/dpkg/origins/debian'
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ? not `/etc/alternatives/README'
D000020: process_archive conffile `/etc/logrotate.d/dpkg' package=dpkg same hash=501f8c90b83c7ea180868ca82e1e82d1
D000200: oldconffsetflags `/etc/dpkg/dpkg.cfg' namenode 0x383b380 flags 5
D000200: oldconffsetflags `/etc/dpkg/origins/debian' namenode 0x2e08ce0 flags 4
D000200: oldconffsetflags `/etc/alternatives/README' namenode 0x383b470 flags 5
D000200: oldconffsetflags `/etc/logrotate.d/dpkg' namenode 0x383b4e0 flags 5
D000001: process_archive oldversionstatus=installed
D000002: maintainer_script_alternative nonexistent prerm `/var/lib/dpkg/info/dpkg.prerm'
D000002: fork/exec /var/lib/dpkg/tmp.ci/preinst ( upgrade 1.14.24ubuntu2 )
dpkg: fout bij afhandelen van dpkg_1.15.3.1ubuntu1_amd64.deb (--install):
 subproces pre-installation script gaf een foutwaarde 1 terug
D000002: fork/exec /var/lib/dpkg/tmp.ci/postrm ( abort-upgrade 1.14.24ubuntu2 )
D000002: fork/exec /var/lib/dpkg/info/dpkg.postinst ( abort-upgrade 1.15.3.1ubuntu1 )
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
D000010: ensure_pathname_nonexisting running rm -rf
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/reassemble.deb'
Fouten gevonden tijdens behandelen van:
 dpkg_1.15.3.1ubuntu1_amd64.deb

---

### Post by Kow on 2009-07-12
Bug report submitted as I am seeing the same and numerous others are. After investigating I see why some get the problem and others do not.

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/398592](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/398592)

Someone else should confirm. :)

---

### Post by camper365 on 2009-07-12
I don't think it's an issue with the 64-bit version, since mine is only 32-bit. Here's a debug output of mine:
```
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
(Reading database ... 198688 files and directories currently installed.)
Preparing to replace dpkg 1.14.24ubuntu2 (using .../dpkg_1.15.3.1ubuntu1_i386.deb) ...
D000200: process_archive conffile `/etc/dpkg/dpkg.cfg' in package dpkg - conff ?
D000020: process_archive conffile `/etc/dpkg/dpkg.cfg' package=dpkg same hash=f4413ffb515f8f753624ae3bb365b81b
D000200: process_archive conffile `/etc/alternatives/README' in package dpkg - conff ?
D000200: process_archive conffile `/etc/alternatives/README' in package dpkg - conff ? not `/etc/dpkg/dpkg.cfg'
D000200: process_archive conffile `/etc/alternatives/README' in package dpkg - conff ? not `/etc/dpkg/origins/debian'
D000020: process_archive conffile `/etc/alternatives/README' package=dpkg same hash=69c4ba7f08363e998e0f2e244a04f881
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ?
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ? not `/etc/dpkg/dpkg.cfg'
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ? not `/etc/dpkg/origins/debian'
D000200: process_archive conffile `/etc/logrotate.d/dpkg' in package dpkg - conff ? not `/etc/alternatives/README'
D000020: process_archive conffile `/etc/logrotate.d/dpkg' package=dpkg same hash=501f8c90b83c7ea180868ca82e1e82d1
D000200: oldconffsetflags `/etc/dpkg/dpkg.cfg' namenode 0xa38ae58 flags 5
D000200: oldconffsetflags `/etc/dpkg/origins/debian' namenode 0x9d325d0 flags 4
D000200: oldconffsetflags `/etc/alternatives/README' namenode 0xa38aeb8 flags 5
D000200: oldconffsetflags `/etc/logrotate.d/dpkg' namenode 0xa38aeec flags 5
D000001: process_archive oldversionstatus=installed
D000002: maintainer_script_alternative nonexistent prerm `/var/lib/dpkg/info/dpkg.prerm'
D000002: fork/exec /var/lib/dpkg/tmp.ci/preinst ( upgrade 1.14.24ubuntu2 )
dpkg: error processing /var/cache/apt/archives/dpkg_1.15.3.1ubuntu1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
D000002: fork/exec /var/lib/dpkg/tmp.ci/postrm ( abort-upgrade 1.14.24ubuntu2 )
D000002: fork/exec /var/lib/dpkg/info/dpkg.postinst ( abort-upgrade 1.15.3.1ubuntu1 )
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
D000010: ensure_pathname_nonexisting running rm -rf
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/reassemble.deb'
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.15.3.1ubuntu1_i386.deb

```

---

### Post by Kow on 2009-07-13
Someone really needs to confirm my bug report or this thread is going to go nowhere and a major bug (for some... nonexistent for others) will go unfixed.

---

### Post by phoogkamer on 2009-07-15
@Kow

You have a duplicate bug report which has the same conclusion, maybe you should subsribe on that bug report and solve the issue.

You already did am I noticing now.

---

### Post by monti on 2009-07-19
I was able to find a workaround, it's posted at [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/397498/comments/19](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/397498/comments/19)

---

### Post by camper365 on 2009-07-23
> **monti said:**
> I was able to find a workaround, it's posted at [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/397498/comments/19](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/397498/comments/19)

It works for me

---

### Post by JDex on 2009-08-26
Hmm.  Just picked up this bug, on 8.04 (32bit) Server, by running aptitude safe-upgrade.

I think this is a bigger issue than Karmic.

The workaround above doesn't apply for me, everything in the /dpkg/alternatives directory has bits.

:confused:

---

### Post by monti on 2009-08-27
> **JDex said:**
> The workaround above doesn't apply for me, everything in the /dpkg/alternatives directory has bits.
That sentence just doesn't make any sense.  Rephrase please?

---

