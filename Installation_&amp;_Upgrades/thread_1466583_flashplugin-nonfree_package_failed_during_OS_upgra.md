---
title: "flashplugin-nonfree package failed during OS upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by LongFist on 2010-04-30
- and now the installer (Applications->Ubuntu Software Center) is *obsessed* with it!  No matter what I select for install, I get the following message back:

> E:I wasn't able to locate file for the flashplugin-nonfree package. This might mean you need to manually fix this package.:


I decided to see if I could fix this myself, trying Synaptics Package Manager "Broken Package" Filter:

> 
You have 1 broken package on your system!

Use the "Broken" filter to locate it.

flashplugin-nonfree
Adobe Flash Player plugin installer (transitional package)

This package is a transitional package that can safely be removed after you installed
flashplugin-installer.


...Hm.  Apparently not.  It failed, leaving me pretty much where I started.  Moving on, I decided to try

> sudo apt-get clean

...which apparently didn't do anything.  Anything visible, anyway.  It was said that
> sudo apt-get update
might resolve the issue, so I ran it.  I turned hopeful when I saw this:

> Fetched 3,645B in 3s (935B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


...so I ran it again, and it appeared to resolve something.  At least it didn't come back with any errors.  But it didn't fix the problem, either.

> 
longfist@Ono-Sendai-Seven:~$ sudo apt-get clean
sudo: unable to resolve host Ono-Sendai-Seven
longfist@Ono-Sendai-Seven:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
longfist@Ono-Sendai-Seven:~$ sudo apt-get -f install
sudo: unable to resolve host Ono-Sendai-Seven
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopencdk10-dev libstrigiqtdbusclient0 liborbit2-dev libfreebob0
  python-gtk2-doc libarts1c2a libgnomeui-dev libartsc0 libglitz-glx1
  libgnutlsxx13 lsb-languages libtasn1-3-dev libdc1394-13
  kdebase-runtime-data-common libgpg-error-dev libcvaux1 mplayer-skins
  libstdc++5-3.3-dev libaudclient1 libbeecrypt6 libgfortran2 g++-3.3
  nethack-common g++-4.2 libgcrypt11-dev lsb-graphics lsb-desktop
  libjack0.100.0-0 boson-data gnustep-back0.12-art
  openoffice.org-hyphenation-en-us ncurses-term libchm1 libpostproc1d
  python-chm gnustep-back0.12 libgnome-keyring-dev libswt3.2-gtk-java
  libservlet2.4-java libgnustep-gui0.12 libavahi-client-dev
  libfile-basedir-perl librasqal0 libgail-dev libawn0 libavformat1d
  binutils-static libmysqlclient15off libx264-57 samdump2 libbonoboui2-dev
  xulrunner-1.9-dom-inspector ri-li-data nvidia-kernel-common kdm-kde4
  libbonobo2-dev kdebase-runtime-bin-kde4 libfile-mimeinfo-perl gfortran-4.2
  libkonq4 libggi2 libgnutls-dev libkrosspython0 atomix-data python-sip4
  libgii1 libgnustep-base1.14 krosspython ksysguardd-kde4 libaudid3tag1 lsb
  libglitz1 pax libfile-desktopentry-perl libidl-dev libart-2.0-dev
  libkrossruby0 libgii1-target-x libcv1 libgnomecanvas2-dev xlibmesa-gl-dev
  lsb-multimedia libdvdread3 libzip1 libstdc++6-4.2-dev tcl8.3
  libgnomevfs2-dev libhighgui1 liblzo2-dev libffcall1 lsb-printing tk8.3
  khelpcenter4 libavcodec1d libgconf2-dev libncurses5-dev libselinux1-dev
  bkhive libgmyth0 odt2txt libadns1 libgnome2-dev libswt3.2-gtk-jni ladcca2
  libavahi-glib-dev libimlib2 libavahi-common-dev lsb-core libaudit0
  libsepol1-dev xconq-common libmpeg3-1 lsb-cxx libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse flashplugin-installer 10.0.45.2ubuntu1 [19.7kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse flashplugin-nonfree 10.0.45.2ubuntu1 [1,764B]
Fetched 21.4kB in 0s (63.0kB/s)               
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)


tl/dr: I can't install it, I can't un-install it, and the Ubuntu Software Center won't let me do anything else.  [Aaarrgh!]

So.  Here I am, a brand-spanking-new install of 10.04 LTS (up from 8.04 LTS), and I cannot install anything via the Ubuntu Software Center because it can't get past the flashplugin-nonfree package.  What can I do - and manual removal is an option, I'm not the least bit intimidated by the Terminal.  You could say that's where I live, really.  But I'd like to free up that functionality, if I could. [-o<

Thanks in advance,

---

### Post by mac9416 on 2010-04-30
Hi, LongFist,

For whatever reason, flashplugin-nonfree wants to "locate file for the flashplugin-nonfree package" in the repositories. If there isn't a repository enabled that holds flashplugin-nonfree, you'll get this error.
So you need to go to System > Administration > Software Sources and enable the source ending with "partner". That should stop the error messages.

---

### Post by LongFist on 2010-04-30
Interestingly enough, the source ending with "partner" showed up twice, both selected (checked) already.

[CENTER][IMG]http://i41.tinypic.com/2evz47b.jpg[/IMG][/CENTER]

I looked (Edit) at each one, and they're identical.  So I un-checked one, and got the following message:

> You have 1 broken package on your system!

Use the "Broken" filter to locate it.

Clicked OK, then immediately got the next message:

> Could not apply changes.  Fix broken packages first!

Frustrating.  If I ever get this thing stabilized...

---

### Post by firebug2 on 2010-04-30
Here is what helped me (after some research):

Manually remove flashplugin-nonfree from /var/lib/dpkg/status.  Look for 
"Package: flashplugin-nonfree"
line and remove everything after it till the next "Package:" record.

Run update-manager to get all the latest updates.

If you want flashplugin-nonfree installed after all, do it via synaptic.

HTH

---

### Post by j-gar on 2010-04-30
Hi All,

Try here:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841)

look at item 8, thats how it worked for me.

take care

j

---

### Post by LongFist on 2010-04-30
:KS  Firebug2, j-gar --- thank you both *VERY* much!

This is exactly what I needed to get my machine stable again!  What can I say?  Thanks millions!!!   :P

---

### Post by Blind Tiger on 2010-05-02
j-gar -- much thanks, item #8 solved the upgrade/removal failure.  relief!

---

### Post by fmgill on 2010-05-02
Thank you. Thank you! Thank you!!! Not only did this fix flash for me, but somewhere/somehow in there if took care of another problem I had.

---

### Post by Padyn on 2010-05-03
firebug, j-gar solution worked for me as well.

> This removed the package for me:

rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
dpkg --remove --force-remove-reinstreq flashplugin-nonfree
dpkg --purge --force-remove-reinstreq flashplugin-nonfree


---

### Post by cotcot on 2010-05-03
Thanks firebug2. Your solution solved my problem.

---

### Post by markthys on 2010-05-06
I had the similar problem.
I did just a copy-paste of the 3 command's with sudo.

Thx to Emanuel Greisen (#8)

---

### Post by bayouoldguy on 2010-06-11
Same problem as above...could not get the "/var/lib/dpkg/status" to run.
maybe I did not use a "space" in the "rm /" prefix. Did run several time the
: dpkg --remove --force-remove-reinstreq flashplugin-nonfree
dpkg --purge --force-remove-reinstreq flashplugin-nonfree   commands, continuing to get the "not removed" result. Finally ran the "purge" command by itself with "sudo" twice, & it completed the task. The error notice is gone & I was able to run a software update with no problems......"G"

---

