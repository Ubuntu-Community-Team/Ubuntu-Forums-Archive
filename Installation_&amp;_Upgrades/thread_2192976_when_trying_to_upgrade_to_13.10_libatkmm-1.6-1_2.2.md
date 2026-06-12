---
title: "when trying to upgrade to 13.10: libatkmm-1.6-1_2.22.7-2_i386.deb 403  Forbidden"
date: 2013-12-10
forum: Installation &amp; Upgrades
---

### Post by dovidbleier on 2013-12-10
When I tried to upgrade from 13.04 to 13.10, it almost downloads all the new packages and then just towards the end I get
"[B]Failed to fetch [http://releases.ubuntu.spd.co.il/pool/main/a/atkmm1.6/libatkmm-1.6-1_2.22.7-2_i386.deb](http://releases.ubuntu.spd.co.il/pool/main/a/atkmm1.6/libatkmm-1.6-1_2.22.7-2_i386.deb) 403  Forbidden"
[/B]

I have tried 3 times.

---

### Post by Bashing-om on 2013-12-11
dovidbleier; Hi !

Perhaps the package in the PPA is not available for version 13.10 (??).
Show us your sources list file :
```

cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

``` to confirm that suspicion.
[INDENT][INDENT]hey, its a thought
[/INDENT][/INDENT]

---

### Post by dovidbleier on 2013-12-12
Here it is:
:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
     2	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3	# newer versions of the distribution.
     4	
     5	
     6	## Major bug fix updates produced after the final release of the
     7	## distribution.
     8	
     9	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    10	## team. Also, please note that software in universe WILL NOT receive any
    11	## review or updates from the Ubuntu security team.
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    14	## team, and may not be under a free licence. Please satisfy yourself as to 
    15	## your rights to use the software. Also, please note that software in 
    16	## multiverse WILL NOT receive any review or updates from the Ubuntu
    17	## security team.
    18	
    19	## Uncomment the following two lines to add software from the 'backports'
    20	## repository.
    21	## N.B. software from this repository may not have been tested as
    22	## extensively as that contained in the main release, although it includes
    23	## newer versions of some applications which may provide useful features.
    24	## Also, please note that software in backports WILL NOT receive any review
    25	## or updates from the Ubuntu security team.
    26	# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    27	# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    28	
    29	## Uncomment the following two lines to add software from Canonical's
    30	## 'partner' repository.
    31	## This software is not part of Ubuntu, but is offered by Canonical and the
    32	## respective vendors as a service to Ubuntu users.
    33	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
    34	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
    35	
    36	## This software is not part of Ubuntu, but is offered by third-party
    37	## developers who want to ship their latest software.
    38	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
    39	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
    40	# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty non-free # disabled on upgrade to natty
    41	
    42	deb [http://releases.ubuntu.spd.co.il/](http://releases.ubuntu.spd.co.il/) raring main universe multiverse restricted
    43	deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) raring-security universe main multiverse restricted
    44	deb [http://releases.ubuntu.spd.co.il/](http://releases.ubuntu.spd.co.il/) raring-updates universe main multiverse restricted

:~$ ls -la /etc/apt/sources.list.d
total 228
drwxr-xr-x 2 root root 4096 Oct 31 07:35 .
drwxr-xr-x 6 root root 4096 Oct 17 13:41 ..
-rw-r--r-- 1 root root  234 Nov 27 01:47 am-monkeyd-nautilus-elementary-ppa-maverick.list
-rw-r--r-- 1 root root  234 Nov 27 01:24 am-monkeyd-nautilus-elementary-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root  234 Apr 30  2013 am-monkeyd-nautilus-elementary-ppa-maverick.list.save
-rw-r--r-- 1 root root  200 Nov 27 01:47 apt-fast-stable-quantal.list
-rw-r--r-- 1 root root  200 Nov 27 01:24 apt-fast-stable-quantal.list.distUpgrade
-rw-r--r-- 1 root root  200 Apr 30  2013 apt-fast-stable-quantal.list.save
-rw-r--r-- 1 root root  158 Nov 27 01:47 bimsebasse-cinnamonextras-quantal.list
-rw-r--r-- 1 root root  158 Nov 27 01:24 bimsebasse-cinnamonextras-quantal.list.distUpgrade
-rw-r--r-- 1 root root  158 Apr 30  2013 bimsebasse-cinnamonextras-quantal.list.save
-rw-r--r-- 1 root root  200 Nov 27 01:47 elegant-gnome-ppa-maverick.list
-rw-r--r-- 1 root root  200 Nov 27 01:24 elegant-gnome-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root  200 Apr 30  2013 elegant-gnome-ppa-maverick.list.save
-rw-r--r-- 1 root root  200 Nov 27 01:47 gnac-team-ppa-natty.list
-rw-r--r-- 1 root root  200 Nov 27 01:24 gnac-team-ppa-natty.list.distUpgrade
-rw-r--r-- 1 root root  200 Apr 30  2013 gnac-team-ppa-natty.list.save
-rw-r--r-- 1 root root  176 Nov 27 01:47 google-chrome.list
-rw-r--r-- 1 root root  176 Nov 27 01:24 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  176 Apr 30  2013 google-chrome.list.save
-rw-r--r-- 1 root root  209 Nov 27 01:47 gwendal-lebihan-dev-cinnamon-stable-quantal.list
-rw-r--r-- 1 root root  209 Nov 27 01:24 gwendal-lebihan-dev-cinnamon-stable-quantal.list.distUpgrade
-rw-r--r-- 1 root root  209 Apr 30  2013 gwendal-lebihan-dev-cinnamon-stable-quantal.list.save
-rw-r--r-- 1 root root  234 Nov 27 01:47 indicator-multiload-stable-daily-quantal.list
-rw-r--r-- 1 root root  234 Nov 27 01:24 indicator-multiload-stable-daily-quantal.list.distUpgrade
-rw-r--r-- 1 root root  234 Apr 30  2013 indicator-multiload-stable-daily-quantal.list.save
-rw-r--r-- 1 root root  314 Nov 27 01:47 medibuntu.list
-rw-r--r-- 1 root root  314 Nov 27 01:24 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root  314 Apr 30  2013 medibuntu.list.save
-rw-r--r-- 1 root root  234 Nov 27 01:47 mozillateam-thunderbird-stable-natty.list
-rw-r--r-- 1 root root  234 Nov 27 01:24 mozillateam-thunderbird-stable-natty.list.distUpgrade
-rw-r--r-- 1 root root  234 Apr 30  2013 mozillateam-thunderbird-stable-natty.list.save
-rw-r--r-- 1 root root   77 Nov 27 01:47 s3tools.list
-rw-r--r-- 1 root root   77 Nov 27 01:24 s3tools.list.distUpgrade
-rw-r--r-- 1 root root   77 Apr 30  2013 s3tools.list.save
-rw-r--r-- 1 root root  210 Nov 27 01:47 scopes-packagers-ppa-quantal.list
-rw-r--r-- 1 root root  210 Nov 27 01:24 scopes-packagers-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root  210 Apr 30  2013 scopes-packagers-ppa-quantal.list.save
-rw-r--r-- 1 root root  136 Nov 27 01:47 screenlets-ppa-quantal.list
-rw-r--r-- 1 root root  136 Nov 27 01:24 screenlets-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root  136 Apr 30  2013 screenlets-ppa-quantal.list.save
-rw-r--r-- 1 root root  196 Nov 27 01:47 shnatsel-zram-quantal.list
-rw-r--r-- 1 root root  196 Nov 27 01:24 shnatsel-zram-quantal.list.distUpgrade
-rw-r--r-- 1 root root  196 Apr 30  2013 shnatsel-zram-quantal.list.save
-rw-r--r-- 1 root root  138 Nov 27 01:47 tiheum-equinox-maverick.list
-rw-r--r-- 1 root root  138 Nov 27 01:24 tiheum-equinox-maverick.list.distUpgrade
-rw-r--r-- 1 root root  138 Apr 30  2013 tiheum-equinox-maverick.list.save
-rw-r--r-- 1 root root  120 Nov 27 01:47 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root  120 Nov 27 01:24 tualatrix-ppa-maverick.list.distUpgrade
-rw-r--r-- 1 root root  120 Apr 30  2013 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root  196 Nov 27 01:47 tualatrix-ppa-quantal.list
-rw-r--r-- 1 root root  196 Nov 27 01:24 tualatrix-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root  196 Apr 30  2013 tualatrix-ppa-quantal.list.save
-rw-r--r-- 1 root root   92 Apr  1  2011 ubuntu-tweak-stable.list.save
-rw-r--r-- 1 root root  202 Nov 27 01:47 webupd8team-java-quantal.list
-rw-r--r-- 1 root root  202 Nov 27 01:24 webupd8team-java-quantal.list.distUpgrade
-rw-r--r-- 1 root root  202 Apr 30  2013 webupd8team-java-quantal.list.save

---

### Post by mörgæs on 2013-12-12
Whoa, this system has been upgraded all the way from 10.10. 
I would recommend a fresh install of 13.10. After that you can add PPA's as needed.

---

### Post by Bashing-om on 2013-12-12
dovidbleier; Yeah !

What ^ mörgæs advised !

Hey that would be much quicker, and  get a stable result than wading through and fixing ALL those old PPAs and applications.
It would be time consuming to verify that each of those PPAs continue to be supported in the raring release, remove those that are not, not to mention removing the applications that no longer have support (appropriate version libraries !)

But, You are the man, you make the call ... keep in mind all the knowledge and experience mörgæs has in this respect.
That recommendation is not made lightly.

[INDENT]a clean install is a clean slate
[/INDENT]

---

### Post by dovidbleier on 2013-12-12
I hear that. But won't that mean that I'll have to reinstall all software not included with the release, reconfigure, reset up my front end (using cinnamon with that classic gnome2 experience), etc. etc. which could take days to recover from, no?

Or is there a less painful way to make a clean install? Is it really so uncommon to continuously upgrade from older versions? I am using 13.04 now.

btw, thank you both for all the help.

---

### Post by Bashing-om on 2013-12-12
dovidbleier; Well,

I honestly do not comprehend how lucky you are to be at 13.04 making all the upgrades from version 10.10, A huge amount of things have changed in the operating system since version 10.10 and many have not made it over the humps of "unity" and "upstart".
Not withstanding, if your system is solid and stable, not counting the package manager screaming and hollering in respect to the old PPAs, and you want to try - I do stress try - and clean up the old PPAs and convert to what might still be available, there is a good chance that it is doable. It is going to be tedious, one line at a time ! One item at a time .. working through what ever must be done to satisfy the package manager .

Back up your data, not likely, but possible, that in the process your system may get broke taking some time to find a resolution to get it back on-line.

Cinamon - from what I gather - does not play nice when any other DE is involved. Best I can recall Cinamon does have support up to raring - will have to check first thing ! 

Then. yes. IF, you (RE-)install you do indeed start all over building your system back to where it is now ( but not making the same mistakes once more ! ) You now have an opportunity to do better.

Gots to have a stable system, presently it is not, with the package manager bent out of shape.

[INDENT][INDENT]whatever
[INDENT][INDENT][INDENT]you want to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dovidbleier on 2013-12-19
well, I seem to have made it. After some unsuccessful mucking with the package manager, I ran apt-get install -f and that fixed whatever the issues were. I am now on Saucy. I hope to make it to the next LTS and then I think I'll sit there for a while. Truth is I would be just as happy (or more) to have stayed with Maverick. It was great, it was sleek, it was fast, no junk or bloat. I like the gnome2 interface (which is why I am running cinnamon).

---

### Post by dovidbleier on 2013-12-19
anyway thanks for all your help.

---

### Post by mörgæs on 2013-12-19
Good, please mark the thread 'solved'.

---

