---
title: "Installing additional software"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by htmlterrier on 2005-04-14
Hi,

I don't know if this is a general problem with [k]ubuntu but I have serious trouble installing software. I tried to install digikam (don't like fetch my photos with konquorer) and kdebluetooth. 

digikam:
I found a bash script on the projects website to install digikam from the CVS. I know the main user of ubuntu shouldn't be bothered with strange abbreviations like CVS, but I couldn't find digikam through apt-cache search. After I started the script nearly everything it needed was missing or outdated. automake as well as autoconf, yada yada yada. OK found a deb package on freshmeet and it worked well.

kdebluetooth:
Today I wanted to connect my mobile via bluetooth. OK big issue under linux ;-). Anyway I found this neat application kdebluetooth but alas, again cpp, gcc, glibc and all the other stuff seems as if they are not on my system.

Now I added different 'regular' debain mirrors and tried to install everything missing, but surprise surprise most of the stuff is just not linked right. Fixed that and still, I can not install any deb package that I find on the net, for example the kdebluetooth thing from [http://dev.kubuntu.org.uk/~motaboy/ubuntu/](http://dev.kubuntu.org.uk/~motaboy/ubuntu/)


I don't know, I thought that kubunt rocks and is fully 'Dad loves his windows' compatible, but now I am a bit disappointed. The dependencies are not solved and if there is always something missing. Anyway I still want to give it a try and would like to ask you if you could help me solve my problems.

---

### Post by erkki70 on 2005-04-14
Hi,
It looks like you should update your /etc/apt/sources.list because digikam 0.7.3 is on the repositories as seen here:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=digikam&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=digikam&searchon=names&subword=1&version=all&release=all)

You'll find a lot of softwares, over 15,000 that you can easily install through apt or Synaptic, Kynaptic as you're using kde. ;-)

a quick "sources.list" keyword search on these forums will lead you to activate correctly all the repositories you need to have easy install for many softwares.

Hope this helps.

Cheers,
Erkki

---

### Post by htmlterrier on 2005-04-14
Hi,

Thanks that did solved some problems. I now find for example kdebluetooth, but still I can not install it because some of the dependencies are not solved. libglib1.2 for example. Somehow I am not able to install this, something with kdebluetooth comes up.

kdebluetooth: Depends libgtk1.2
Depends liblockdev1

and so on

Any idea?

Dave

---

