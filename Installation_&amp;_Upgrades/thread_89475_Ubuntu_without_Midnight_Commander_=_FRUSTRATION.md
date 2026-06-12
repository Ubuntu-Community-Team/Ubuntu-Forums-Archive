---
title: "Ubuntu without Midnight Commander = FRUSTRATION"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by claudiuc on 2005-11-12
Hi Ubutu packaging guru, I observed that after installing Kubuntu 5.10 there's no trace of Midnight Commander, a *very* usefull tool. Even searching of it with "apt-cache search mc". Are the Ubuntu leaders so elitist that they refute such an utility? Who from the Ubuntu packaging leaders is so eager to install by default bitmap, artsbuilder, diveintopython book, fastjar and so many other marginally usefull tools, but do not install mc? And I'm installing Kubuntu 5.10 from DVD! 3.5GB worth of software. No trace of mc. Are the very Linux-guru so adicted by CLI, that they almost everytime refuse friendliness for beginers? I'm very frustrated with this. No wonder why beginers go in droves with SuSE and Mandriva. Please reshape the Ubuntu package list at install, from the beginers perspective. When I'm choosing at the prompt "install" instead of "server", I think I deserve an Midnight Commander by default and not "bitmap" utility. From this POV Gentoo is way far from Ubuntu.

---

### Post by Lambert on 2005-11-12
[COLOR=Blue][COLOR=Black]

mc is available in the repositories, just not on install. 

I'm just curioius what makes it a good tool over anything that might be compareable out there? I'm still quite new ot linux.

[/COLOR] [/COLOR]

---

### Post by Ptero-4 on 2005-11-12
Have you enabled the universe repository? The first time I installed Ubuntu I got mad b/c I couldn't find some apps but when I learned about the universe repo I enabled it and found that not only the sw I wanted was there but also lots of other sw that I liked and I didn't even thought that existed. By adding that repo to your /etc/apt/sources.list and typing sudo apt-get update and entering your password when prompted you'll add a very extensive sw list to synaptic and surelly you'll find mc in it.

---

### Post by claudiuc on 2005-11-13
Hi Ptero,


Thank you for "universe" thingy. The MC is very nice hidden.
I'm sure a beginner will find it in a snap. But it's still a big mistake
to install a lot of crap from a 3.5GB DVD (!!!!) and not put
a little 2MB Midnight Commander. Are Ubuntu maintainers
listening? Man, I'm really astonished! We have by default:
bicyclerepair (... "helping Pythonistas everywhere glide over
gory details of refactoring their code"),  but we can't
have a decent CLI file manager like "mc".

But the Pythonistas every where need: phyhon-epydoc,
phyton-unit, python2.4-epydoc, python2.4-unit, phython-tk,
python2.4-tk, just to resolve dependecies for kubuntu-destkop.
The "kubuntu-desktop" only contain copyright and changelog.gz.
Come on, the Ubuntu developers are so adicted by phyton (RedHat
guy anyone?) that the disguise that for only 2 text files. I 
"dpkg -r" all of them.

And I still ask: in that default install isn't a place for Midnight Commander, but for a lot of python packages, even these 
are not directly usefull for users? Is "mc" so hated that we're so
eager to put tons of crap on a DVD, but not a such usefull utility?

Here's a statistic:
```

claudiuc@mybox:/usr/share/doc$ ls -1 | grep python | wc -l
114
claudiuc@mybox:/usr/share/doc$ ls -1 | grep python
diveintopython
libpythonize0
python
python2.4
python2.4-adns
python2.4-apt
python2.4-clientcookie
python2.4-crypto
python2.4-dbus
python2.4-dev
python2.4-dictclient
python2.4-egenix-mxdatetime
python2.4-egenix-mxproxy
python2.4-egenix-mxstack
python2.4-egenix-mxtexttools
python2.4-egenix-mxtools
python2.4-eunuchs
python2.4-examples
python2.4-gadfly
python2.4-gd
python2.4-gdbm
python2.4-geoip
python2.4-htmlgen
python2.4-htmltmpl
python2.4-id3lib
python2.4-imaging
python2.4-imaging-sane
python2.4-jabber
python2.4-kde3
python2.4-kjbuckets
python2.4-ldap
python2.4-librdf
python2.4-libxml2
python2.4-libxslt1
python2.4-minimal
python2.4-musicbrainz
python2.4-mysqldb
python2.4-numeric
python2.4-opengl
python2.4-osd
python2.4-pam
python2.4-pexpect
python2.4-pgsql
python2.4-pycurl
python2.4-pylibacl
python2.4-pyopenssl
python2.4-pyorbit
python2.4-pyxattr
python2.4-qt3
python2.4-reportlab
python2.4-simpletal
python2.4-sip4-qt3
python2.4-sqlite
python2.4-syck
python2.4-xml
python2.4-xmpp
python-adns
python-apt
python-cddb
python-clientcookie
python-crypto
python-egenix-mxproxy
python-egenix-mxstack
python-egenix-mxtexttools
python-egenix-mxtools
python-eunuchs
python-examples
python-gadfly
python-gd
python-gdbm
python-gdchart
python-genetic
python-geoip
python-gnupginterface
python-htmlgen
python-htmltmpl
python-id3lib
python-imaging
python-imaging-sane
python-jabber
python-kde3
python-kjbuckets
python-ldap
python-minimal
python-musicbrainz
python-mysqldb
python-netcdf
python-newt
python-numeric
python-opengl
python-osd
python-pam
python-parted
python-pexpect
python-pgsql
python-pisock
python-pqueue
python-pyao
python-pylibacl
python-pyogg
python-pyopenssl
python-pyorbit
python-pyvorbis
python-pyxattr
python-reportlab
python-simpletal
python-soappy
python-sqlite
python-stats
python-syck
python-uno
python-xdg
python-xml
python-xmpp

```

I bet not a 50% of it is immediatelly usefull after a default
install.

---

### Post by claudiuc on 2005-11-13
[QUOTE=Lambert][COLOR=Blue][COLOR=Black]

mc is available in the repositories, just not on install. 

I'm just curioius what makes it a good tool over anything that might be compareable out there? I'm still quite new ot linux.

[/COLOR] [/COLOR][/QUOTE]

Tell me what is "compareable out there" at the CLI and I'll
tell you why the Midnight Commander is the king of the console.
Many so declared "guru" are to shy to not use "mc". They're
not so cool when will use it. They're so adicted for "ls -l, cd ...,
ls, cd, ls, cd, ...." that may be we can still punch cards for 
programming computers. No wonder why Windows and Mac OS X
are still top of the usability, even there are lot of mistakes in them
(I mean Windows).

---

### Post by metoo on 2005-11-13
You are right, mc is the swiss-army-knife of file system operation. I'm always lost if it isn't around.
It should indeed available as default.

One can update it even when running from a live CD, but surely this is nothing for a beginner.

But keeping your tone a bit more diplomatic wouldn't hurt either.  ;-)

---

### Post by az on 2005-11-13
MC rocks.  It is probably something that would fit in well with a lightweight system like Xubuntu.  Perhaps we could ask them to include it on their install cd, if they ever make one.  

The reason that mc is not on the Ubuntu install is because there are already tools which do the same job (Nautilus).  Ubuntu is streamlined.  It is only a small subset of packages which get love from Canonical.  The rest are in the hands of the community.

---

### Post by claudiuc on 2005-11-13
[QUOTE=metoo]You are right, mc is the swiss-army-knife of file system operation. I'm always lost if it isn't around.
It should indeed available as default.

One can update it even when running from a live CD, but surely this is nothing for a beginner.

But keeping your tone a bit more diplomatic wouldn't hurt either.  ;-)[/QUOTE]
Sure, but how you can feel when you're frustrated. I love Debian.
I was thinking Ubuntu is a contemporary Debian. It is, but with
I-wanna-my-own-distro newbie mistakes. I'm very confident 
Ubuntu maintainers are inteligent and knowledgeable people. But
they're emotion and habit driven. When you're one-man-shop,
it's understandable, but when many people poke arround to
build a nice distro (and it is), you can't afford emotion.

Why I say emotion or habit? Because by popular demand and
utility, Midnight Commander, "mc is the swiss-army-knife". 
It's suitable for Linux rescue on pen-drive and CD-ROM.
Needless to say on default install of *any* distro. But hey,
Ubuntu is too "133t" to have Midnight Commander on 3.5GB DVD
worth of good and crappy software. 
To erase users habit of using it, just let hide it on "universe" repo. 

Sorry, I can't hide my angry at this. To be fair, at least in the past
there where many distro arround which missed "mc".

---

### Post by Cashel on 2005-11-15
Agreed with many comments.. I am a long time linux user and just love this little app.. when I want to mess with perms and what have you CLI is the way to go, but for hunting down files who's names I dont know but will when I see them mc is the way to go... we should brow beat linus into merging git into it :) .. That said it seems the default package in the repositories doesnt work right.. both in Hoary and Breezy the menus show up clean in an x term but not in a real term (cli) .. ncurses problems? I'll look into it I guess just wanted to spout some love for mc while I saw the thread :)

peace,
cashel

---

