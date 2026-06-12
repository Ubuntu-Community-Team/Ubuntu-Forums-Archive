---
title: "Try to install one package, everything goes haywire"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by solinent on 2007-07-08
I want to build amarok-svn, and I also want music-brainz support.

Anyways, this is what I get when I try to install.  It probably is totally unrelated (probably aptitude related).

I get this:

> adrian@adrian-desktop:~$ sudo aptitude install libmusicbrainz4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  libmusicbrainz4-dev [b]
The following packages are unused and will be REMOVED:
  audacity gdk-imlib11 gnome-bin gnome-libs-data gtick imlib-base libart2 
  libdb3 libgnome32 libgnomesupport0 libgnomeui32 libgnorba27 libgnorbagtk0 
  liborbit0 [/b]
0 packages upgraded, 1 newly installed, 14 to remove and 0 not upgraded.
Need to get 128kB of archives. After unpacking 12.9MB will be freed.
The following packages have unmet dependencies:
  libmusicbrainz4-dev: Depends: libmusicbrainz4c2a (= 2.1.4-1ubuntu2) but 2.1.4-2 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libmusicbrainz4c2a [2.1.4-2 (now) -> 2.1.4-1ubuntu2 (feisty)]

Score is -40

Accept this solution? [Y/n/q/?]

Now, I've built audacity locally.  These problems started to occur after I installed the package:
ubuntustudio-audio
Then I un-installed it because ardour wasn't working with Jack (it turns out Jack wasn't setup right, and I was using ardour-gtk not ardour2!)

Thanks.

EDIT:
Not sure if double posting is allowed, but here's what I did:

> 
OK. I went looking around, and found bug 64814 with a similar symptom, but with apt.

In there there was a suggestion to delete /var/lib/apt/extended_states. I then decided to to the same with the aptitude equivalent -- /var/lib/aptitude/pkgstates. Deleted it, run aptidude update && aptitude dist-upgrade and...

nothing to be removed anymore.

So. For me, this is solved. I am not going to reject it myself, since I do not know what you would want to do -- perhaps document something?

Since this laptop has suffered Edgy -> Feisty -> Gutsy (and a move from KDE to Gnome in early Feisty), it might very well have gotten a not-so-perfect version of something, and it just happened that I seldom use aptitude.

This guy had a much severe problem, but I did what he said and it "fixed" it.
Now, I get this (I figured out that I should be installing libtunepimp-dev)
> adrian@adrian-desktop:~$ sudo aptitude install libtunepimp-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libmusicbrainz4-dev libraptor1-dev libtunepimp-dev 
The following NEW packages will be automatically installed:
  libcurl3-gnutls-dev libofa0-dev 
The following packages will be automatically REMOVED:
  libcurl3-openssl-dev 
The following NEW packages will be installed:
  libcurl3-gnutls-dev libofa0-dev 
The following packages will be REMOVED:
  libcurl3-openssl-dev 
0 packages upgraded, 4 newly installed, 1 to remove and 0 not upgraded.
Need to get 1198kB of archives. After unpacking 1847kB will be used.
The following packages have unmet dependencies:
  libtunepimp-dev: Depends: libtunepimp5 (= 0.5.2-1ubuntu3) but 0.5.2-1.luks2 is installed.
  libmusicbrainz4-dev: Depends: libmusicbrainz4c2a (= 2.1.4-1ubuntu2) but 2.1.4-2 is installed.
  libraptor1-dev: Depends: libcurl3-openssl-dev but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
liblrdf0-dev
libraptor1-dev
librasqal0-dev
librdf0-dev

Downgrade the following packages:
libmusicbrainz4c2a [2.1.4-2 (now) -> 2.1.4-1ubuntu2 (feisty)]
libtunepimp5 [0.5.2-1.luks2 (now) -> 0.5.2-1ubuntu3 (feisty)]

Score is -1534

Accept this solution? [Y/n/q/?] 

I accepted, and it will see if anything changed now....

---

