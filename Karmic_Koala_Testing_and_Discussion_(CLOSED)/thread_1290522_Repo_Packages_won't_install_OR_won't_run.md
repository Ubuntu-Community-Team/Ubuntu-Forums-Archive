---
title: "Repo Packages won't install OR won't run"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-10-13
I'm having an issue whereby I can't install packages even though they are showing in the repos.

Examples:

FFmpeg
DeVeDe (installs but won't run because it need mplayer).
Installing mplayer removes DeVeDe
Installing DeVeDe removes mplayer

There are others too but I don't remember the all.

Will these be fixed on or about release time, or will it be fixed at all?

---

### Post by taavikko on 2009-10-13
Nothing about removing mplayer (though I have mplayer-nogui installed)
```
devil@core7:~$ sudo aptitude install devede
[sudo] password for devil:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  devede dvdauthor{a} libavformat-extra-52{a} libcdio7{a} libglade2-0{a} libiso9660-5{a}
  libpostproc-extra-51{a} libswscale-extra-0{a} libvcdinfo0{a} mencoder{a} python-cairo{a}
  python-glade2{a} python-gtk2{a} vcdimager{a}
The following packages will be REMOVED:
  libavformat52{a} libpostproc51{a} libswscale0{a}
0 packages upgraded, 14 newly installed, 3 to remove and 0 not upgraded.
Need to get 6,785kB of archives. After unpacking 17.1MB will be used.
Do you want to continue? [Y/n/?]

```

If you're experiencing dependency problems, check the launchpad if they're reported, if not, then report them yourself, only way to get them sorted out.

---

### Post by crjackson on 2009-10-13
> **taavikko said:**
> Nothing about removing mplayer (though I have mplayer-nogui installed)
```
devil@core7:~$ sudo aptitude install devede
[sudo] password for devil:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  devede dvdauthor{a} libavformat-extra-52{a} libcdio7{a} libglade2-0{a} libiso9660-5{a}
  libpostproc-extra-51{a} libswscale-extra-0{a} libvcdinfo0{a} mencoder{a} python-cairo{a}
  python-glade2{a} python-gtk2{a} vcdimager{a}
The following packages will be REMOVED:
  libavformat52{a} libpostproc51{a} libswscale0{a}
0 packages upgraded, 14 newly installed, 3 to remove and 0 not upgraded.
Need to get 6,785kB of archives. After unpacking 17.1MB will be used.
Do you want to continue? [Y/n/?]

```

If you're experiencing dependency problems, check the launchpad if they're reported, if not, then report them yourself, only way to get them sorted out.

I wasn't asking anyone to REPORT IT FOR ME!

I was asking if anyone knew if the packages would be fixed.  Sometimes packages are depreciated and HELPFUL people are nice enough to let you know you're wasting your time.

It makes no sense to file a bug report if I'm somehow causing the problem.  I could be my setup as opposed to a bug so I figured I ask before I started pointing fingers at a particular package.  I'd like to know if anyone else has issues installing ffmpeg as well.

Here's what I get when I install:
```
charles@charles-m6809:~$ sudo apt-get install devede
[sudo] password for charles: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dvgrab lives-data libweed0 icedax
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mplayer-nogui
Suggested packages:
  mplayer-doc netselect fping nvidia-libvdpau1 nvidia-libvdpau
The following packages will be REMOVED:
  mplayer mplayer-fonts
The following NEW packages will be installed:
  devede mplayer-nogui
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 3,645kB of archives.
After this operation, 11.3MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/multiverse mplayer-nogui 2:1.0~rc3+svn20090426-1ubuntu9 [2,090kB]
Get:2 http://us.archive.ubuntu.com karmic/multiverse devede 3.14.0-0ubuntu5 [1,555kB]
Fetched 3,645kB in 4s (911kB/s)          
(Reading database ... 188027 files and directories currently installed.)
Removing mplayer-fonts ...
dpkg: mplayer: dependency problems, but removing anyway as you requested:
 mozilla-mplayer depends on mplayer (>= 1.0~rc2) | mplayer-nogui (>= 1.0~rc2); however:
  Package mplayer is to be removed.
  Package mplayer-nogui is not installed.
 gnome-mplayer depends on mplayer (>= 1.0~) | mplayer-nogui (>= 1.0~); however:
  Package mplayer is to be removed.
  Package mplayer-nogui is not installed.
 smplayer depends on mplayer | mplayer-nogui; however:
  Package mplayer is to be removed.
  Package mplayer-nogui is not installed.
 ogmrip depends on mplayer-nogui | mplayer; however:
  Package mplayer-nogui is not installed.
  Package mplayer is to be removed.
Removing mplayer ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Selecting previously deselected package mplayer-nogui.
(Reading database ... 187822 files and directories currently installed.)
Unpacking mplayer-nogui (from .../mplayer-nogui_2%3a1.0~rc3+svn20090426-1ubuntu9_i386.deb) ...
Selecting previously deselected package devede.
Unpacking devede (from .../devede_3.14.0-0ubuntu5_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for menu ...
Setting up mplayer-nogui (2:1.0~rc3+svn20090426-1ubuntu9) ...
Installing new version of config file /etc/mplayer/mplayer.conf ...
Installing new version of config file /etc/mplayer/input.conf ...
Installing new version of config file /etc/mplayer/menu.conf ...

Setting up devede (3.14.0-0ubuntu5) ...

Processing triggers for menu ...
charles@charles-m6809:~$ 

```

The screen shot in below shows the result of launching DeVeDe.

So then I install mplayer and get:

```
charles@charles-m6809:~$ sudo apt-get install mplayer
[sudo] password for charles: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dvgrab lives-data vcdimager libweed0 icedax
Use 'apt-get autoremove' to remove them.
Suggested packages:
  mplayer-doc
The following packages will be REMOVED:
  devede mplayer-nogui
The following NEW packages will be installed:
  mplayer
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 5,223kB of archives.
After this operation, 3,936kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net karmic/main mplayer 2:1.0~rc3+svn20090904-0karmic1 [5,223kB]
Fetched 5,223kB in 5s (1,026kB/s)  
(Reading database ... 187974 files and directories currently installed.)
Removing devede ...
dpkg: mplayer-nogui: dependency problems, but removing anyway as you requested:
 mozilla-mplayer depends on mplayer (>= 1.0~rc2) | mplayer-nogui (>= 1.0~rc2); however:
  Package mplayer is not installed.
  Package mplayer-nogui is to be removed.
 gnome-mplayer depends on mplayer (>= 1.0~) | mplayer-nogui (>= 1.0~); however:
  Package mplayer is not installed.
  Package mplayer-nogui is to be removed.
 smplayer depends on mplayer | mplayer-nogui; however:
  Package mplayer is not installed.
  Package mplayer-nogui is to be removed.
 ogmrip depends on mplayer-nogui | mplayer; however:
  Package mplayer-nogui is to be removed.
  Package mplayer is not installed.
Removing mplayer-nogui ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for desktop-file-utils ...
Selecting previously deselected package mplayer.
(Reading database ... 187822 files and directories currently installed.)
Unpacking mplayer (from .../mplayer_2%3a1.0~rc3+svn20090904-0karmic1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up mplayer (2:1.0~rc3+svn20090904-0karmic1) ...
Installing new version of config file /etc/mplayer/menu.conf ...
Installing new version of config file /etc/mplayer/mplayer.conf ...
Installing new version of config file /etc/mplayer/input.conf ...

charles@charles-m6809:~$ 

```

---

### Post by tymanthius on 2009-10-13
I'm having devede/mplayer issues as well, but it will let me install everything just fine.  mplayer just gives codec_wav_tags errors, which causes devede to fail.

---

### Post by tekstr1der on 2009-10-13
> **crjackson said:**
> Sometimes packages are depreciated...

I'm not so sure packages ever depreciate.

---

### Post by mc4man on 2009-10-13
> knew if the packages would be fixed.

need to ck. something

---

### Post by diesch on 2009-10-13
edit: ignore this, I didn't read carefully enough

You can't have both mplayer and mplayer-nogui installed, so if you install one of them the other one gets removed.  That causes a temporary dependency problem when no mplayer version is installed, but that gets fixed when the new mplayer package gets installed, so in the end everything is fine.

---

### Post by crjackson on 2009-10-13
> **mc4man said:**
> I think that will depend on if devede can work with the mplayer package vs the  mplayer-nogui that it has as a dependency.

For whatever reason mplayer has been split into 2 package versions that conflict with each other.

Shouldn't be to hard too test to see if devede will work with the mplayer version. (couple of ways to install with the mplayer version installed: if desired will post a couple of them

If so then it's depends could be changed to mplayer | mplayer-nogui

If not then then you'd need to use the nogui mplayer and if a gui was desired install one such as smplayer.

I do a lot of tinkering with video/DVDs. I don't doing whatever it takes to make DeVeDe work, I just don't KNOW what to do personally.

I was kind of hoping it would be some kind of a repos issue that would be corrected by release.  I want to upgrade all my machines, but NOT having DeVeDe would be a deal breaker.

---

### Post by mc4man on 2009-10-13
Sorry for last post, was on my 'real' karmic install that I've modified a bit.

On a straight up. **fully updated **tester I don't see any problem as far as installing

mplayer depends on mplayer-nogui so they both can be installed at the same time. Installing devede doesn't remove the mplayer package, see screen

If having an issue maybe remove whatever mplayer you have in synaptic, then mark mplayer and then devede for install and install all 3 at the same time


(are you using a ppa for mplayer?

some ppa mplayer packages have mplayer-nogui marked as a conflict so installing them will uninstall the repo mplayer-nogui package

---

### Post by diesch on 2009-10-13
I don't get this error when starting devede. What does ```
which mplayer
``` say? What does ~/.devede contain?

```

devede:
  Installed: 3.14.0-0ubuntu5
  Candidate: 3.14.0-0ubuntu5
  Version table:
 *** 3.14.0-0ubuntu5 0
        500 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Packages
        100 /var/lib/dpkg/status
mplayer-nogui:
  Installed: 2:1.0~rc3+svn20090426-1ubuntu9
  Candidate: 2:1.0~rc3+svn20090426-1ubuntu9
  Version table:
 *** 2:1.0~rc3+svn20090426-1ubuntu9 0
        500 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/multiverse Packages
        100 /var/lib/dpkg/status

```

---

### Post by crjackson on 2009-10-13
> **mc4man said:**
> Sorry for last post, was on my 'real' karmic install that I've modified a bit.

On a staight up. **fully updated **tester I son't see any problem as far as installing

mplayer depends on mplayer-nogui so they both can be installed at the same time. Installing devede doesn't remove the mplayer package, see screen

If having an issue maybe remove whatever mplayer you have in synaptic, then mark mplayer and then devede for install and install all 3 at the same time


(are you using a ppa for mplayer?

Maybe a clean install after the release will do the trick. What about ffmpeg.  Will that install for you.

---

### Post by mc4man on 2009-10-13
What you've reported about trying to install devede is consistent with what would happen if you have a mplayer ppa enabled in your sources (like the rvm mplayer ppa (smplayer

Plus a closer look shows that you have smplayer, so did you also add the rvm mplayer repo?


What I quickly did is edit the control file in the repo  devede to allow using mplayer or mplayer-nogui and also added the rvm ppa and upgraded mplayer and mencoder

The modified devede installed fine with the ppa mplayer installed, though I've never used devede before so don't now how to test but it opens fine. See screen


Edit:
so maybe for some clarity
Your mplayer (or mplayer-nogui) and mencoder versions must match.

So if using the karmic repo packages of both then there will be no issue installing and running devede.

If using a ppa like the rvm mplayer ppa then again you need both mplayer and mencoder from that ppa installed and you then need a devede package that's either modified to allow mplayer as a dep or they update devede to add mplayer as a dep choice.
( you also can use a dpkg command to remove mplayer-nogui as an install dep

If you build your own mplayer then probably the best way would be to build as a debian package set that would include a mencoder package.

If you build your own mplayer as a checkinstall package  then I'm not sure, you'd probably need a checkinstall mencoder as well
(or possibly mod an available mencoder package to same version as the ckinstall one

---

### Post by crjackson on 2009-10-13
> **mc4man said:**
> What you've reported about trying to install devede is onsistent with what would happen if you have a mplayer ppa enabled in your sources (like the rvm mplayer ppa (smplayer

Plus a closer look shows that you have smplayer, so did you also add the rvm mplayer repo?


What I quickly did is edit the control file in the repo  devede to allow using mplayer or mplayer-nogui and also added the rvm ppa and upgraded mplayer.

the modified devede installed fine with the ppa mplayer installed, though I've never used devede before so don't now how to test. See screen




Edit:
so maybe for some clarity
Your mplayer (or mplayer-nogui) and mencoder versions must match.

So if using the karmic repo packages of both then there will be no issue installing and running devede.

If using a ppa like the rvm mplayer ppa then again you need both mplayer and mencoder from that ppa installed and you then need a devede package that's either modified to allow mplayer as a dep or they update devede to add mplayer as a dep choice.
( you also can use a dpkg command to remove mplayer-nogui as an install dep

If you build your own mplayer then probably the best way would be to build as a debian package set that would include a mencoder package.

If you build your own mplayer as a checkinstall package  then I'm not sure, you'd probably need a checkinstall mencoder as well
(or possibly mod an available mencoder package to same version as the ckinstall one

Okay, that makes sense.  I do have Ubuntu-Tweak installed and enabled some third party repos they have pre-selected.  I'll turn that off, remove all the mplayer stuff and reinstall with out the ppa selected.

I'd love to be able to use the upgraded versions but I don't anything about editing control files.  I'll be fine to just have it working.

Are you able to install ffmpeg?  Perhaps it's borked on my system for the same reason.  I'm glad I asked here and got your advice.  Thanks..

---

### Post by mc4man on 2009-10-13
> Are you able to install ffmpeg? 

Yes, no problem, Again this is in regard to a testing install that is using the karmic repos (with exception of  just adding the rvm ppa for mplayer and mencoder

If you're having an issues with ffmpeg and it's libs (whether the default versions or the 'extra' versions), then again it may be due to some other ppa

I think at this point (beta) using something like ubuntu tweak may prove  problematic.

screen one shows my current installed ffmpeg libs on the testing install, using the 'extra' versions.


As far as the devede thing with a ppa mplayer, this *may be something a bug* could be filed against, there doesn't seem to be any reason I see that mplayer can't be added as a dep choice.

screen 2 shows it opening on the tester with only the rvm ppa mplayer and mencoder installed, seems ok ...?

Maybe let things shake out, otherwise it really isn't that hard to mod the .deb, could describe fairly easily.

---

### Post by rwood on 2009-10-13
> **crjackson said:**
> I'm having an issue whereby I can't install packages even though they are showing in the repos.

Examples:

FFmpeg
DeVeDe (installs but won't run because it need mplayer).
Installing mplayer removes DeVeDe
Installing DeVeDe removes mplayer

There are others too but I don't remember the all.

Will these be fixed on or about release time, or will it be fixed at all?

 same problem with devede  "solved" by removing version 3.14.0 with synaptic
then installing older deb version.installed and asked if i wanted to upgrade to the latest devede i did and it works fine.
i think the problem was something missing in karmic devede that older version picked up.

---

### Post by crjackson on 2009-10-13
> **mc4man said:**
> Yes, no problem, Again this is in regard to a testing install that is using the karmic repos (with exception of  just adding the rvm ppa for mplayer and mencoder

If you're having an issues with ffmpeg and it's libs (whether the default versions or the 'extra' versions), then again it may be due to some other ppa

I think at this point (beta) using something like ubuntu tweak may prove  problematic.

screen one shows my current installed ffmpeg libs on the testing install, using the 'extra' versions.


As far as the devede thing with a ppa mplayer, this *may be something a bug* could be filed against, there doesn't seem to be any reason I see that mplayer can't be added as a dep choice.

screen 2 shows it opening on the tester with only the rvm ppa mplayer and mencoder installed, seems ok ...?

Maybe let things shake out, otherwise it really isn't that hard to mod the .deb, could describe fairly easily.


Okay, I give up.  I removed the ppas, removed / purged all mplayer and devede stuff. Reinstalled and I still get the same error.

I'll wait a few days and download the release version to do a fresh install.  I've been using this install since A3 so it's bound to have other issues under the hood.

Thanks for your help.  As long as I know these packages DO work in Karmic, I'm good.  I'll proceed with my upgrades in a few days.

---

### Post by crjackson on 2009-10-13
> **rwood said:**
> same problem with devede  "solved" by removing version 3.14.0 with synaptic
then installing older deb version.installed and asked if i wanted to upgrade to the latest devede i did and it works fine.
i think the problem was something missing in karmic devede that older version picked up.

Where did you get the older deb file?

---

### Post by tymanthius on 2009-10-13
> **crjackson said:**
> Where did you get the older deb file?

I got one from [http://www.filestube.com/8c3069bcb09bfe6f03e9/details.html](http://www.filestube.com/8c3069bcb09bfe6f03e9/details.html)

But it didn't do any good b/c it's mplayer that's borked, not devede.


:confused:

---

### Post by mc4man on 2009-10-13
Not really understanding where you guys are having an issue.

Went ahead and removed the rvm ppa. After that, in synaptic, removed mplayer, mencoder and devede.

Then from the terminal installed the repo devede (which also installed the repo mplayer-nogui and mencoder

> doug@doug-desktop:~$ sudo apt-get install devede
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcc-4.3-base mplayer-skins libggi-target-x libx264-75 libx264-76 libggi2
  libgii1 mplayer-skin-blue libgii1-target-x cpp-4.3 libopencore-amrnb0
  libopencore-amrwb0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mencoder mplayer-nogui
Suggested packages:
  mplayer-doc netselect fping
The following NEW packages will be installed:
  devede mencoder mplayer-nogui
0 upgraded, 3 newly installed, 0 to remove and 39 not upgraded.
Need to get 0B/5,302kB of archives.
After this operation, 12.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package mplayer-nogui.
(Reading database ... 182317 files and directories currently installed.)
Unpacking mplayer-nogui (from .../mplayer-nogui_2%3a1.0~rc3+svn20090426-1ubuntu9_i386.deb) ...
Selecting previously deselected package mencoder.
Unpacking mencoder (from .../mencoder_2%3a1.0~rc3+svn20090426-1ubuntu9_i386.deb) ...
Selecting previously deselected package devede.
Unpacking devede (from .../devede_3.14.0-0ubuntu5_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up mplayer-nogui [COLOR="Blue"](2:1.0~rc3+svn20090426-1ubuntu9)[/COLOR] ...
Installing new version of config file /etc/mplayer/mplayer.conf ...
Installing new version of config file /etc/mplayer/input.conf ...
Installing new version of config file /etc/mplayer/menu.conf ...

Setting up mencoder [COLOR="Blue"](2:1.0~rc3+svn20090426-1ubuntu9)[/COLOR] ...
Setting up devede [COLOR="Blue"](3.14.0-0ubuntu5)[/COLOR] ...

doug@doug-desktop:~$ 


I'd make sure that prior to installing devede that the various ffmpeg libs installed are like what I showed in previous screen ( plus a few lower down in the list

Mark all the 'extra' and install



You'll notice that installing devede only installed mplayer-nogui, if wanted, mplayer (the repo gui), could then also be installed ( done right after the above

> doug@doug-desktop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcc-4.3-base mplayer-skins libggi-target-x libx264-75 libx264-76 libggi2
  libgii1 libgii1-target-x cpp-4.3 libopencore-amrnb0 libopencore-amrwb0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  mplayer-doc netselect fping
The following NEW packages will be installed:
  mplayer
0 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.
Need to get 0B/2,268kB of archives.
After this operation, 5,022kB of additional disk space will be used.
Selecting previously deselected package mplayer.
(Reading database ... 182482 files and directories currently installed.)
Unpacking mplayer (from .../mplayer_2%3a1.0~rc3+svn20090426-1ubuntu9_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up mplayer [COLOR="Blue"](2:1.0~rc3+svn20090426-1ubuntu9)[/COLOR] ...



---

### Post by crjackson on 2009-10-15
Well, my install is obviously broken.  I'm not concerned since I've been milking this since an early Alpha.  I plan to do a clean install in a couple of days and that should fix it.

---

### Post by mc4man on 2009-10-15
> .......and that should fix it. 

Shouldn't be any reason it doesn't work out with the repo versions

Maybe just start off installing devede and it should pull in the dep's it needs
> Package: devede
Version: 3.14.0-0ubuntu5
Architecture: all
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Installed-Size: 3560
Depends: python, python-support (>= 0.90.0), python-glade2, mencoder, dvdauthor, genisoimage, vcdimager, imagemagick, mplayer-nogui, libavcodec-extra-52, libavformat-extra-52, libavutil-extra-49, libpostproc-extra-51, libswscale-extra-0

If by release it still only allows the mplayer-nogui let me know. a simple script will allow you to edit the devede .deb to allow an mplayer package to also satisfy. 
( the other possible thing is that rvm changes his mplayer builds to mplayer-nogui, though there may be reasons behing using mlayer as package name

---

### Post by crjackson on 2009-10-16
> **mc4man said:**
> Shouldn't be any reason it doesn't work out with the repo versions

Maybe just start off installing devede and it should pull in the dep's it needs


If by release it still only allows the mplayer-nogui let me know. a simple script will allow you to edit the devede .deb to allow an mplayer package to also satisfy. 
( the other possible thing is that rvm changes his mplayer builds to mplayer-nogui, though there may be reasons behing using mlayer as package name

Okay thanks, I'll do just that.

---

### Post by crjackson on 2009-10-18
> **mc4man said:**
> Shouldn't be any reason it doesn't work out with the repo versions

Maybe just start off installing devede and it should pull in the dep's it needs


If by release it still only allows the mplayer-nogui let me know. a simple script will allow you to edit the devede .deb to allow an mplayer package to also satisfy. 
( the other possible thing is that rvm changes his mplayer builds to mplayer-nogui, though there may be reasons behing using mlayer as package name

wow, even after a fresh install I'm getting the same errors.  I can't install mencoder either this time, and still ffmpeg won't install.  WTF is going on here?

---

### Post by mc4man on 2009-10-18
> WTF is going on here?

Not sure where you're going wrong.

Just to see took the daily from friday and did fresh install on tester. Only installed the nvidia drivers so I could see (this machine defaults to 1600/1200 on install

Then this ( clipped to show what was to be installed
> doug@doug-desktop:~$ sudo apt-get install devede
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dvdauthor imagemagick libaudio2 libavcodec-extra-52 libavformat-extra-52
  libavutil-extra-49 libcelt0 libdirac0c2a libdvdnav4 libdvdread4 libfaac0
  libfaad0 libffado1 libfreebob0 libgsm1 libiso9660-5 libjack0 liblzo2-2
  libmp3lame0 libopenal1 libopenjpeg2 libpostproc-extra-51
  libschroedinger-1.0-0 libsvga1 libswscale-extra-0 libvcdinfo0 libx264-67
  libxml++2.6-2 libxvidcore4 mencoder mplayer-nogui vcdimager
Suggested packages:
  transfig imagemagick-doc nas libdvdcss2 debhelper build-essential jackd
  mplayer-doc netselect fping
The following NEW packages will be installed:
  devede dvdauthor imagemagick libaudio2 libavcodec-extra-52
  libavformat-extra-52 libavutil-extra-49 libcelt0 libdirac0c2a libdvdnav4
  libdvdread4 libfaac0 libfaad0 libffado1 libfreebob0 libgsm1 libiso9660-5
  libjack0 liblzo2-2 libmp3lame0 libopenal1 libopenjpeg2 libpostproc-extra-51
  libschroedinger-1.0-0 libsvga1 libswscale-extra-0 libvcdinfo0 libx264-67
  libxml++2.6-2 libxvidcore4 mencoder mplayer-nogui vcdimager
0 upgraded, 33 newly installed, 0 to remove and 73 not upgraded.
Need to get 15.0MB of archives.
After this operation, 38.1MB of additional disk space will be used.
Do you want to continue [Y/n]?

And 
> ................................
Registering documents with scrollkeeper...
Setting up libaudio2 (1.9.2-1) ...

Setting up libavutil-extra-49 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libdirac0c2a (1.0.2-0ubuntu1) ...

Setting up libfaad0 (2.6.1-3.1) ...

Setting up libgsm1 (1.0.13-1) ...

Setting up libmp3lame0 (3.98.2+debian-0ubuntu1) ...

Setting up libopenjpeg2 (1.3+dfsg-4) ...

Setting up libschroedinger-1.0-0 (1.0.8-2) ...

Setting up libx264-67 (1:0.svn20090621+git364d7d-0ubuntu2) ...

Setting up libxvidcore4 (2:1.1.2-0.1ubuntu4) ...

Setting up libavcodec-extra-52 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libavformat-extra-52 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libfaac0 (1.26-0.1ubuntu2) ...
Registering documents with scrollkeeper...
Setting up libaudio2 (1.9.2-1) ...

Setting up libavutil-extra-49 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libdirac0c2a (1.0.2-0ubuntu1) ...

Setting up libfaad0 (2.6.1-3.1) ...

Setting up libgsm1 (1.0.13-1) ...

Setting up libmp3lame0 (3.98.2+debian-0ubuntu1) ...

Setting up libopenjpeg2 (1.3+dfsg-4) ...

Setting up libschroedinger-1.0-0 (1.0.8-2) ...

Setting up libx264-67 (1:0.svn20090621+git364d7d-0ubuntu2) ...

Setting up libxvidcore4 (2:1.1.2-0.1ubuntu4) ...

Setting up libavcodec-extra-52 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libavformat-extra-52 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libfaac0 (1.26-0.1ubuntu2) ...

Setting up libcelt0 (0.6.1-1) ...

Setting up libxml++2.6-2 (2.26.0-2) ...

Setting up libffado1 (2.0~rc2+svn1569-2ubuntu1) ...

Setting up libfreebob0 (1.0.11-1build1) ...

Setting up libjack0 (0.116.1-4ubuntu2) ...

Setting up liblzo2-2 (2.03-1) ...

Setting up libopenal1 (1:1.8.466-2) ...

Setting up libpostproc-extra-51 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libsvga1 (1:1.4.3-27ubuntu1) ...

Setting up libswscale-extra-0 (4:0.5+svn20090706-2ubuntu3) ...

Setting up mplayer-nogui (2:1.0~rc3+svn20090426-1ubuntu10) ...

Setting up mencoder (2:1.0~rc3+svn20090426-1ubuntu10) ...
Setting up libdvdread4 (4.1.3-5ubuntu2) ...

Setting up dvdauthor (0.6.14-3ubuntu4) ...
Setting up libiso9660-5 (0.78.2+dfsg1-3) ...

Setting up libvcdinfo0 (0.7.23-4ubuntu1) ...

Setting up vcdimager (0.7.23-4ubuntu1) ...
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support

Setting up imagemagick (7:6.5.1.0-1.1ubuntu3) ...

Setting up devede (3.14.0-0ubuntu5) ...

Setting up libdvdnav4 (4.1.3-3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
doug@doug-desktop:~$ 

Setting up libcelt0 (0.6.1-1) ...

Setting up libxml++2.6-2 (2.26.0-2) ...

Setting up libffado1 (2.0~rc2+svn1569-2ubuntu1) ...

Setting up libfreebob0 (1.0.11-1build1) ...

Setting up libjack0 (0.116.1-4ubuntu2) ...

Setting up liblzo2-2 (2.03-1) ...

Setting up libopenal1 (1:1.8.466-2) ...

Setting up libpostproc-extra-51 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libsvga1 (1:1.4.3-27ubuntu1) ...

Setting up libswscale-extra-0 (4:0.5+svn20090706-2ubuntu3) ...

Setting up mplayer-nogui (2:1.0~rc3+svn20090426-1ubuntu10) ...

Setting up mencoder (2:1.0~rc3+svn20090426-1ubuntu10) ...
Setting up libdvdread4 (4.1.3-5ubuntu2) ...

Setting up dvdauthor (0.6.14-3ubuntu4) ...
Setting up libiso9660-5 (0.78.2+dfsg1-3) ...

Setting up libvcdinfo0 (0.7.23-4ubuntu1) ...

Setting up vcdimager (0.7.23-4ubuntu1) ...
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support

Setting up imagemagick (7:6.5.1.0-1.1ubuntu3) ...

Setting up devede (3.14.0-0ubuntu5) ...

Setting up libdvdnav4 (4.1.3-3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
doug@doug-desktop:~$ 



Edit
Do you have all the ubuntu repos enabled?  (restricted and multiverse

---

### Post by crjackson on 2009-10-18
> **mc4man said:**
> Not sure where you're going wrong.

Just to see took the daily from friday and did fresh install on tester. Only installed the nvidia drivers so I could see (this machine defaults to 1600/1200 on install

Then this ( clipped to show what was to be installed


And 



Edit
Do you have all the ubuntu repos enabled?  (restricted and multiverse

I do.  And it's a fresh install with nothing else installed except flash / java plug-in from sun.  I pulled in devede and it looked like it was going well.  Then I try to run it and it tells me it needs mplayer and mencoder.  Now mcoder won't install, and mplayer removes devede.  FFmpeg also still won't install.  I don't get it.

---

### Post by mc4man on 2009-10-18
If you haven't** added a ppa** then this doesn't make sense
> Now mcoder won't install, and mplayer removes devede. FFmpeg also still won't install.


The karmic repo mplayer is just a gui and depends on mplayer-nogui
The karmic repo mencoder also depends on mplayer-nogui as does devede

So there is no reason for the repo mplayer to remove devede and there is nothing to prevent mencoder from being installed

All four depend on the ffmpeg libs (libavcodec52, libavformat52, ect.), only devede requires the 'extra' version though the other three can also use (no conflicts there

maybe try this ( all it's going to do is install mplayer which will require mplayer-nogui, and maybe install the unstripped versions which will require the extra version

In other words
mplayer
mplayer-nogui
libavcodec-unstripped-52, ect.
libavcodec-extra-52, ect.
mencoder

[http://ubuntuforums.org/showthread.php?t=1291624&highlight=devede](http://ubuntuforums.org/showthread.php?t=1291624&highlight=devede)

Anyway on the install from previous post did both a devede conversion mpeg2 to avi and avi to mpeg2 (dvd video

worked fine both ways

---

### Post by crjackson on 2009-10-18
Well, I don't get it, but I installed again a 4th time on this machine and now devede, mplayer, ffmpeg, mencoder and others are working.

I did nothing different.  It's just working....  I really don't get it...

---

### Post by mc4man on 2009-10-18
> I really don't get it...

that makes 2, but at least your back in business ....

---

### Post by crjackson on 2009-10-18
Stragely enough, I was about to install ubuntu-restricted-extras when it showed me that it would remove devede, ffmpeg, and mencoder.  How strange is that?

---

### Post by mc4man on 2009-10-19
> Stragely enough, I was about to install ubuntu-restricted-extras

I've never used that package, prefer to install the plugins from synaptic.

It **may** be because the 'recommends' for ubuntu-restricted-extras include the non extra versions of the ffmpeg libs ( libavcodec52, libavformat52, ect.) which conflict with the 'extra' versions

By default all recommends are now installed in karmic, the exception would be Gdebi.

Will have to ck. on a tester.


Edit: 
> It **may** be because the 'recommends

That appears to be the reason, why u-r-e doesn't have a depend option of the extra lib's is unclear to me

( the treatment of ffmpeg and mplayer in karmic is a bit of a joke, also the vlc build is missing some useful features that could be easily enabled but they choose not to.

---

### Post by rvm4000 on 2009-10-19
> **mc4man said:**
> If you haven't** added a ppa** then this doesn't make sense


The karmic repo mplayer is just a gui and depends on mplayer-nogui

I haven't downloaded the packages of mplayer in karmic, but unless mplayer has changed a lot lately (which I doubt) the gui version (gmplayer) is just mplayer built with gui support, but it can do the same things than the build without gui support.

IMO devede should depend on mplayer-nogui OR mplayer (gui).

---

### Post by mc4man on 2009-10-19
> I haven't downloaded the packages of mplayer in karmic

These are showing up for karmic...? ( with a way to add to karmic sources
(2:1.0~rc3+svn20090904-0karmic1)
[https://launchpad.net/~rvm/+archive/mplayer/+packages](https://launchpad.net/~rvm/+archive/mplayer/+packages)

> the gui version (gmplayer) is just mplayer built with gui support

In karmic the mplayer package is just the gui, mplayer itself is provided with the mplayer-nogui package

[http://packages.ubuntu.com/karmic/mplayer/filelist](http://packages.ubuntu.com/karmic/mplayer/filelist)

> IMO devede should depend on mplayer-nogui OR mplayer (gui). 

I agree there, did so in this post with no issue, which allowed an mplayer package from your ppa above to stay installed

[http://ubuntuforums.org/showthread.php?p=8100285#post8100285](http://ubuntuforums.org/showthread.php?p=8100285#post8100285)

Otherwise is there some reason not to name the karmic package mplayer-nogui..... with a conflict of mplayer ..?

---

### Post by rvm4000 on 2009-10-24
Well, I think the new build of mplayer (mplayer - 2:1.0~rc3+svn20090904-0karmic3) available at [https://launchpad.net/~rvm/+archive/mplayer/](https://launchpad.net/~rvm/+archive/mplayer/) has this problem fixed. Now you can install devede with this version of mplayer.

Note that I have only tested the installation, but I have not tested if devede actually works.

---

### Post by mc4man on 2009-10-24
> but I have not tested if devede actually works. 

Seems to work fine ( don't use devede but it's encoding away on a tester.

The only possible scenario that may prove confusing to some is if devede is already installed before the mplayer ppa is added. (repo mencoder and mplayer-nogui only

Then after adding the ppa and updating, mencoder will be seen with an update available but not the ppa mplayer.

To use the ppa mplayer one would need to do so manually 

sudo apt-get install mplayer

or mark mplayer for install in synaptic

---

### Post by crjackson on 2009-10-26
> **mc4man said:**
> Seems to work fine ( don't use devede but it's encoding away on a tester.

The only possible scenario that may prove confusing to some is if devede is already installed before the mplayer ppa is added. (repo mencoder and mplayer-nogui only

Then after adding the ppa and updating, mencoder will be seen with an update available but not the ppa mplayer.

To use the ppa mplayer one would need to do so manually 

sudo apt-get install mplayer

or mark mplayer for install in synaptic

As a routine process for every new install, I enable medibuntu repos and pull in updated codecs.  I think this was the culprit.  Purging all the packages affected, clearing the cache, turning off the medibuntu repo, and then re=installing the wanted packages seemed to fix things.

---

### Post by mc4man on 2009-10-26
Glad you got it going...

There isn't any great reason to enable medibuntu anymore as a source (really since hardy

Any of the 1 or two packages one may want can be added directly from their package list or gotten elsewhere

current karmic list
> # aacgain
# aacplusenc
# acroread-fonts
# alsa-firmware
# amrnb
# amrwb
# app-install-data-medibuntu
# apport-hooks-medibuntu
# gizmo5
# googleearth-data
# googleearth
# hot-babe
# ices
# libamrnb3
# libamrnb-dev
# libamrwb3
# libamrwb-dev
# libdvdcss2
# libdvdcss-dev
# medibuntu-keyring
# non-free-codecs
# realplayer
# rmconverter
# skype-common
# skype
# skype-static
# w32codecs
# w64codecs

[http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)

---

### Post by crjackson on 2009-10-27
> **mc4man said:**
> Glad you got it going...

There isn't any great reason to enable medibuntu anymore as a source (really since hardy

Any of the 1 or two packages one may want can be added directly from their package list or gotten elsewhere

current karmic list


[http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)

Thanks.  I always have to learn things the hard way I guess ;)

---

