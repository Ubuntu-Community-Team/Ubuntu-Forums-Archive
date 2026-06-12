---
title: "how to fix broken/missing OpenOffice 3.0"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by zika on 2008-11-27
Yesterday I've been usin OpenOfifice happily.

Today I've found today that my OpenOffice is missing from menu and that it won't open files anymore. I have upgraded openoffice to 3.0 from the one that came with Ibex (2.*) some time ago via:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
sudo apt-get update
sudo apt-get dist-upgrade


i've tried to do sudo apt-get install opennoffice.org but that gave me:
 

sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
E: Broken packages

Is there any help?

I've tried just a minute ago to reinstall it using [ftp://ftp.ussg.iu.edu/pub/openoffice...-US_deb.tar.gz]("ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz") and everything went well except menus could not be installed. But, the situation is the same, I can not start OpenOffice.

Where are the files that start writer etc?

---

### Post by zika on 2008-11-27
I've just checked and the same thing happened on the other machine on my LAN. They are totally independent, this second one was not ON until yesterday whei it was just updated ... maybe the updates are to blame?

---

### Post by Ric_ on 2008-11-27
Hey man I just got this to install correctly.

However be VERY careful with apt-get dist-upgrade

apt-get update and apt-get upgrade are your normal methods.

this is what i did:

sudo vi /etc/apt/sources.list

added

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

then:

apt-get update

apt-get install openoffice.org

If your having problems you may have a corrupted .deb file downlaoded.

try:

apt-cache clean
apt-get update

If your going through a proxy try and flush the cache too as the problem could be there.

Ric

---

### Post by zika on 2008-11-27
I had it installed perfecly and flawlessly a month ago. just the way You say.

I think I know what happened: after update yesterday Cruft Remover suggested to delete uno-libs3 package. So I did. It seems that it is needed for OO3.0.

Any ideas how to undo that operation?

Should I reinstall (before uninstalling all of OO2.* originally from Ibex)?

---

### Post by zika on 2008-12-24
Watch it! Again today, after weeks of empy list, Cruft remover offered to me to erase uno-libs3. That's how the problem described above started. Of course, I refused but beware ... :smile:

---

