---
title: "Problems upgrading warty to hoary with apt-get"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by miksta on 2005-04-19
After updating the source.list, doing sudo apt-get upgrade and sudo apt-get dist-upgrade following error shows up in the upgrade:

Package console-common is not configured yet.

dpkg: error processing console-tools (--configure):

 dependency problems - leaving unconfigured

Errors were encountered while processing:

 locales

 ubuntu-base

 lsb

 console-common

 console-data

 base-config

 console-tools

E: Sub-process /usr/bin/dpkg returned an error code (1)

Any idea what causes it? Any help would be appreaciated.

---

### Post by ubuntu_demon on 2005-04-19
look at these threads :

[http://www.ubuntuforums.org/showthread.php?t=23624](http://www.ubuntuforums.org/showthread.php?t=23624)
[http://www.ubuntuforums.org/showthread.php?t=23489](http://www.ubuntuforums.org/showthread.php?t=23489)

---

### Post by jbharrison on 2005-04-19
Log out to failsafe then stop gdm:

$ /etc/init.d/gdm stop

Run apt-get again with force option:

$ apt-get -f dist-upgrade

---

### Post by miksta on 2005-04-20
Thank you for your replies. This issue was resolved :)

This was on my friends computer and he seems very happy now! I still got problems with getting GLX to work [http://ubuntuforums.org/showthread.php?t=28519](http://ubuntuforums.org/showthread.php?t=28519)  on my own box :?:

---

### Post by shazzam on 2005-05-18
I just installed ubantu and I can not install any programs the sudo apt-get is not working at all it gives me an error like the one below  

when i tried to update i got this

Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

or

root@Shazzam:/home/rastes # sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate

I am lost I can not get XMMS and so i can't play my MP3s and for some reason there is no codec for them in the player that is encluded.

I have an IBM laptop with pentium-m architecture and an ATI vedio card which is a whole other problem I am sure.

But please help me I am in deep doo doo. :-?

---

### Post by ubuntu_demon on 2005-06-04
[QUOTE=shazzam]I just installed ubantu and I can not install any programs the sudo apt-get is not working at all it gives me an error like the one below  

when i tried to update i got this

Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

or

root@Shazzam:/home/rastes # sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate

I am lost I can not get XMMS and so i can't play my MP3s and for some reason there is no codec for them in the player that is encluded.

I have an IBM laptop with pentium-m architecture and an ATI vedio card which is a whole other problem I am sure.

But please help me I am in deep doo doo. :-?[/QUOTE]
 shazzam it's better if you open a new topic in the forum that corresponds with the question :)

Your questions are answered at this page :

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

First you have to replace your sources.list with the one they provide see :

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

After this do a manual upgrade like :

[http://www.ubuntuguide.org/#ubuntuupdates](http://www.ubuntuguide.org/#ubuntuupdates)

For video playbak I recommend gxine or totem-xine (a backend for totem). Also install w32codecs and xmms so you can play mp3's and watch xvid/divx:

$ sudo apt-get install xmms w32codecs gxine totem-xine

I hope this helps. Otherwise please start a new thread here :

[http://www.ubuntuforums.org/forumdisplay.php?f=73](http://www.ubuntuforums.org/forumdisplay.php?f=73)

---

