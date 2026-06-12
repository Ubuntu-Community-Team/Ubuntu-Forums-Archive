---
title: "libstdc++5 help"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-09-28
Im trying to narrow this down to my machine or if this is something in the latest updates of karmic hence the new topic after a day or so of searching by myself and having no answer after searching for hours :) 

I cant run any version of thunderbird since last week..it wont start...Ive had a few topics started and no one seems to understand why, but the package needed is libstdc++5. Doing a sudo apt-get install libstdc 5 refers to no installation candiate, and trying to pull the package from the jaunty repos is a no go, I get a bad file descriptor. So until this gets fixed Im having to use evolution, which is hard to get around..Anyone else experience this, or am i the only one?

Edit: I have  libstdc++6, but it looks like I need 5 as well.  Sorry for the confusion , guys :)

---

### Post by Tomy on 2009-09-28
I don't know the answer

but libstdc++5 is also needed for the gstreamer fluendo-plugins that Canonical sells -- so this package cannot be installed on karmic.

---

### Post by sports fan Matt on 2009-09-28
Maybe It will be fixed in an update..I have libstdc++6

---

### Post by mariner09 on 2009-09-28
I don't know why you would have that requirement for Thunderbird.  I have Thunderbird 2.0.0.23 running and it lists libstdc++6 as a dependency.  This is however on Karmic A6, so I'm not sure if the same would hold true on Jaunty or other versions.

---

### Post by sports fan Matt on 2009-09-28
I dunno but I do know Tbird running from terminal yields: /opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by mariner09 on 2009-09-28
What version do you have installed?  dpkg -l thunderbird or look through synaptic...

---

### Post by sports fan Matt on 2009-09-28
I have the version through synaptic..

Also, id also like to get Opera 10 installed

---

### Post by mariner09 on 2009-09-28
So, go to thunderbird in synaptic, click on properties and then look at the dependencies.

It should show libstdc++6 and not 5.

---

### Post by sports fan Matt on 2009-09-28
It does show that but it refuses to start...even after a complete purge of the folder.  Its installed, but it wont start..Sorry if I want clear :)

---

### Post by kansasnoob on 2009-09-30
I've been googling a lot and this seems to be a repetitious problem in development as far back as 2006:

[https://bugs.edge.launchpad.net/baltix/+bug/31218](https://bugs.edge.launchpad.net/baltix/+bug/31218)

And you can see here it also effected w32codecs in Karmic:

[https://bugs.edge.launchpad.net/medibuntu/+bug/428775](https://bugs.edge.launchpad.net/medibuntu/+bug/428775)

so Medibuntu actually removed the codecs dependent on it.

I noticed this while trying to install the mozilla build of Firefox using Ubuntuzilla, but it appears to effect lots of apps.

Sdaly I haven't found the right bug report to comment on. I'll try to look some more tomorrow - time allowing.

Oh, and this was done upstream in Debian Sid:

[http://www.debianhelp.org/node/15792](http://www.debianhelp.org/node/15792)

I have no idea how to do what's recommended there:

> My first thought is that it may work with libstdc++6 also. After installing that package
just giving a soft link from /usr/lib/libstdc++.so.6 to /usr/lib/libstdc++.so.5 and see if it works for you.

Maybe someone else would be kind enough to teach me (or us). I'm a great guinea pig, if I hose things I don't mind reinstalling:)

---

### Post by mc4man on 2009-09-30
here's a thread discussing  libstdc++5 ect.
A link may or may not work, (in the case of w32codecs it wouldn't, but the loss of rv30 decoding is no big deal

[http://ubuntuforums.org/showthread.php?t=1265204](http://ubuntuforums.org/showthread.php?t=1265204)

(you can freely install libstdc++5 if you choose to

---

### Post by kansasnoob on 2009-09-30
I had tried this:

> lance@lance-desktop:~$ sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
ln: creating symbolic link `/usr/lib/libstdc++.so.5': File exists


Still no go for installing Firefox or Thunderbird either using the tarballs or using Ubuntuzilla.

And if I try to install libstdc++5.deb from Jaunty:

[ATTACH]130227[/ATTACH]

---

### Post by mc4man on 2009-09-30
> And if I try to install libstdc++5.deb from Jaunty:

gdebi is broken, you'd need to use dpkg
dpkg -i /path/to/whatever.deb

Looks like creating a link isn't working with those apps either ( though I've never tried myself.
I'd remove the link before trying to install w/ dpkg

( for my real installs I use a local repo, makes adding and maintaining outside or built .debs very easy.
Was extremely useful for hardy, don't expect quite the use in karmic, (at least for awhile.

Current local repo in *working* karmic
> 
doug@doug-desktop:~/repo$ ls *.deb
amarok14_1.4.10-0ubuntu3~ppa4_i386.deb
amarok14-common_1.4.10-0ubuntu3~ppa4_all.deb
amarok14-engine-xine_1.4.10-0ubuntu3~ppa4_i386.deb
ffmpeg_0.5+svn20090906-0.0_i386.deb
libavcodec52_0.5+svn20090906-0.0_i386.deb
libavcodec-dev_0.5+svn20090906-0.0_i386.deb
libavdevice52_0.5+svn20090906-0.0_i386.deb
libavdevice-dev_0.5+svn20090906-0.0_i386.deb
libavfilter0_0.5+svn20090906-0.0_i386.deb
libavfilter-dev_0.5+svn20090906-0.0_i386.deb
libavformat52_0.5+svn20090906-0.0_i386.deb
libavformat-dev_0.5+svn20090906-0.0_i386.deb
libavutil50_0.5+svn20090906-0.0_i386.deb
libavutil-dev_0.5+svn20090906-0.0_i386.deb
libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
libfaac0_1.28-0.3_i386.deb
libfaac-dev_1.28-0.3_i386.deb
libmediainfo0_0.7.20-1_i386.Ubuntu_9.04.deb
libopencore-amrnb0_0.1.1-0.0_i386.deb
libopencore-amrnb-dev_0.1.1-0.0_i386.deb
libopencore-amrwb0_0.1.1-0.0_i386.deb
libopencore-amrwb-dev_0.1.1-0.0_i386.deb
libpostproc51_0.5+svn20090906-0.0_i386.deb
libpostproc-dev_0.5+svn20090906-0.0_i386.deb
libstdc++5_3.3.6-17ubuntu1_i386.deb
libswscale0_0.5+svn20090906-0.0_i386.deb
libswscale-dev_0.5+svn20090906-0.0_i386.deb
libvlc2_1.0.1-2ubuntu2_i386.deb
libvlccore2_1.0.1-2ubuntu2_i386.deb
libx264-68_0.svn20090730-0.0_i386.deb
libx264-75_0.svn20090921-0.0_i386.deb
libx264-76_0.svn20090924-0.0_i386.deb
libx264-dev_0.svn20090921-0.0_i386.deb
libzen0_0.4.3-1_i386.Ubuntu_9.04.deb
mediainfo-gui_0.7.20-1_i386.Debian_5.deb
mozilla-plugin-vlc_1.0.1-2ubuntu2_i386.deb
mplayer_1.0~rc3svn29720_i386.deb
rhythmbox_0.12.5-0ubuntu1-1_i386.deb
rubyripper_0.5.7-0.0_all.deb
smplayer_0.6.8-1~jaunty2_i386.deb
totem-xine_2.28.0-0ubuntu1-1_i386.deb
vlc_1.0.1-2ubuntu2_i386.deb
vlc-data_1.0.1-2ubuntu2_all.deb
vlc-nox_1.0.1-2ubuntu2_i386.deb
vlc-plugin-pulse_1.0.1-2ubuntu2_i386.deb
vlc-plugin-sdl_1.0.1-2ubuntu2_i386.deb
w32codecs_20071007-0medibuntu4_i386.deb

---

### Post by dinxter on 2009-09-30
> **sox fan Matt said:**
> I dunno but I do know Tbird running from terminal yields: /opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

/opt/thunderbird is not the version of thunderbird you are looking for :) 
looks very much like a non-repository installation or ppa installed. the main ubuntu repository installs the binary to /usr/bin/thunderbird 
try runnning that in a terminal to check 
the repository version is  thunderbird/karmic uptodate 2.0.0.23+build1+nobinonly-0ubuntu1

---

### Post by kansasnoob on 2009-09-30
mc4man,

Thanks. I hadn't used Gdebi lately, using dpkg installed the Jaunty .deb of libstdc++5 with no problem.

Just an FYI: for Ubuntuzilla I also had to install libnotify-bin from the repos.

Too soon to be sure I haven't caused some sort of breakage, but nothing apparent.

---

### Post by kansasnoob on 2009-09-30
I'd like to know more about how to create a local repo if you're so inclined. No idea where to begin.

Or maybe I should not hijack this thread.

---

### Post by mc4man on 2009-09-30
> I'd like to know more about how to create a local repo if you're so inclined. No idea where to begin.
move discussion to here, have my take in last post, method culled from various posts for easy to set up local repo ( vs a remote one

[http://ubuntuforums.org/showthread.php?p=7606998#post7606998](http://ubuntuforums.org/showthread.php?p=7606998#post7606998)

Will be around tommorrow if any ?'s

---

