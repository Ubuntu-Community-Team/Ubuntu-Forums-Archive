---
title: "Openoffice Update broken"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by Jvaldezjr on 2007-10-11
I am trying to update openoffice.org from the package openoffice.org-comon_2.2.0-1ubuntu4_all.deb to openoffice.org-common_2.2.0-1ubuntu5_all.deb through adept.  I'm using Kubuntu 7.04

Here is the error message I get when I perform the upgrade:
```
Preparing to replace openoffice.org-common 2.2.0-1ubuntu4 (using .../openoffice.org-common_2.2.0-1ubuntu5_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu5_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/share/registry/data/org/openoffice/Office/WebWizard.xcu')
I/O warning : failed to load external entity "/usr/share/mime/packages/AdobeReader.xml"
Failed to parse '/usr/share/mime/packages/AdobeReader.xml'

Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu5_all.deb

```

And I can't perform the upgrade.

---

### Post by Arcturus691 on 2007-10-19
You are not the only one with problems updating openoffice.  Here are some related threads:
[http://ubuntuforums.org/showthread.php?p=3571274]("http://ubuntuforums.org/showthread.php?p=3571274")
[http://ubuntuforums.org/showthread.php?t=567803]("http://ubuntuforums.org/showthread.php?t=567803")

---

### Post by mike2357 on 2007-10-19
Here's a patch that is allowing openoffice to work for me until a fixed package can be readied.  Open up a terminal screen and type the following:

cd /usr/local/bin
sudo sh -c "cat > ooffice"
#!/bin/sh
soffice $*
<CTRL-D>
sudo chmod 755 ooffice

Note:  the reference to <CTRL-D> above means to hold down the CTRL key and while doing do, type a D.

openoffice is generally invoked with the ooffice command, but it is not working.  By placing a file in /usr/local/bin by this name that calls soffice instead, openoffice can be started.  I have no idea why, but this worked for me.

Remember to remove /usr/local/bin/ooffice when a fixed package is released, or if this solution doesn't work for you.

Good luck.

---

### Post by mike2357 on 2007-10-19
I came across a better solution:
Using Synaptic, do a complete removal of the following packages:
language-support-en
openoffice.org-base
openoffice.org-calc
openoffice.org-core
openoffice.org-draw
openoffice.org-impress
openoffice.org-math
openoffice.org-thesaurus-en-us
openoffice.org-writer


Then, install 
openoffice.org

Problem solved.

---

### Post by Jvaldezjr on 2007-10-27
Mike's way worked better, thanks for the update.

---

### Post by jaromrnelson on 2007-12-05
I have the same problem and I couldn't get it to work, even with a complete removal and reinstallation of all openoffice packages.  I posted my comments to a bug filed with openoffice on lightpad.

sudo apt-get -f install

didn't work either.  It kept getting the same error messages.

I ended up uninstalling openoffice altogether, so I could still use apt-get.  apt-get wouldn't install anything else until the dependencies were fixed, which wouldn't work.

---

### Post by shadowhywind on 2007-12-05
So i just took the advice of the uninstall and then try to install it and now i am getting the same error message when updating any ideas?

---

### Post by dan_linder on 2007-12-07
My OOWriter was not broken completely, rather the menu icons and other visual pieces were missing after the last OpenOffice update.  I noticed that "openoffice.org-kde" was not installed (I run Kubuntu).  Installing that (and the required "openoffice.org-style-crystal") fixed the menus and I have the menu icons back.

---

