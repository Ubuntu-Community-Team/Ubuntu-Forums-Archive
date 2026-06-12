---
title: "feisty upgrade problems with xserver"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by cybersleeper on 2007-04-27
I am using the Ubuntu Gamers Edition.
I tried to upgrade to Feisty but I am having xserver upgrade problems.

I have unmet dependencies for xserver-xorg to run. There is a problem with xserver-xorg-core.

here is the output of the apt-get install -f

Unpacking replacement xserver-xorg-core ...
dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.2.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/scanpci.1.gz', which is also in package gatos
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg-core_2%3a1.2.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help is appreciated.

---

### Post by kupajava on 2007-04-27
same problem here, anyone else with this one?

If if figure it out Ill let you know

---

### Post by kupajava on 2007-04-27
still no luck whatsoever.  Whatever I try I still cannot get xserver-xorg-core to update.  nothing goes on after this, its a dpkg crash error that will not allow the update to continue

hope someone sees this!

---

### Post by kupajava on 2007-04-28
I'm getting that possibly the problem here is that the new xserver-xorg-core will not install because it is trying to overwrite a file called "scanpci.1.gz" that is cross referenced by the app "gatos"

I have tried renaming the file scanpci.1.gz - no luck
I have tried deleting the same file - now the xserver won't start at all
I have tried deleting the downloaded xserver file and in case it was corrupted - no dice
I have tried booting to the alternative cd and updating the file in a shell - still errors out

next:
- possibly deleting gatos?  I don't know if I need it as this machine has only one display

- possibly removing the old xserver-xorg?  I would need to remove xserver without using apt-get as it seems to be stuck with the gatos problem

- possibly removing some service that calls on scanpci.1.gz so I can reinstall xserver and then restore the service?

Any Ideas???

its dead as a doornail until I can get past this... so any help would be nice.

---

### Post by kupajava on 2007-04-28
PROBLEM SOLVED!!!!!!!!!!!

The issue here, probably the same issue anyone who uses the Ubuntu ultimate or Ubuntu Gamers edition will have when trying to upgrade to Feisty is this:

Unpacking replacement xserver-xorg-core ...
dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.2.0-3ubuntu8_i386.deb (--unpack):
trying to overwrite `/usr/share/man/man1/scanpci.1.gz', which is also in package gatos
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/xserver-xorg-core_2%3a1.2.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


The Cause: This is because the ultimate and gamers disks install a package called "Gatos" which is an older version which conflicts with the install of xserver-xorg-core.  The gatos package has been modified in a newer version to not conflict on the file scanpci.1.gz but it was too late for us :(

The Resolution: from the console type

 # dpkg -r gatos

to remove gatos and then:

# apt-get install -f

to fix xserver-xorg-core.  Now you can continue your upgrade!!! :-)

Kupajava

---

