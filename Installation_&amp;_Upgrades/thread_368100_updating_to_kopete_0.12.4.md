---
title: "updating to kopete 0.12.4"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by browneyedgirl65 on 2007-02-22
Hi, all, I have edgy eft installed, with both gnome and KDE.  I'm interested in updating from the 0.12.3 version of kopete bundled with 6.10 and going up to 0.12.4 which is the latest.

Problem is, I can't seem to find the packages anywhere.  Even the official kopete site has only 0.12.2 as the latest release on their download page.  So I'm stumped.  I have KDE 3.5.5; would I need to upgrade to 3.5.6 to accomplish this and if so, how?

This is weird, normally I don't have trouble at least finding a tarball of the latest of some project, but kopete seems to be mysterious in this respect.

Thanks,
BEG :confused:

---

### Post by browneyedgirl65 on 2007-02-22
OK, I have at least part of the answer...I actually need to update to KDE 3.5.6 and that's bundled in it.

But I can't seem to find a good way to update this..I don't want to download the sources, but I can never seem to find complete instructions.

I went here [http://kubuntu.org/announcements/kde-356.php](http://kubuntu.org/announcements/kde-356.php) and added the jriddell keys, but nothign obvious happens...I tried
$   sudo apt-get install kubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

still at 3.5.5

So then I tried upgrading to Fiesty for the hell of it, but THAT didn't work either:
~$ gksu "update-manager -c -d"
warning: could not initiate dbus
extracting '/tmp/tmpXp86QE/feisty.tar.gz'
authenticate '/tmp/tmpXp86QE/feisty.tar.gz' against '/tmp/tmpXp86QE/feisty.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
/usr/lib/python2.4/site-packages/UpdateManager/DistUpgradeFetcher.py:62: GtkWarning: gtk_scrolled_window_add: assertion `bin->child == NULL' failed
  self.parent.scrolled_notes.add(textview_release_notes)
extracting '/tmp/tmpA04LOV/feisty.tar.gz'
authenticate '/tmp/tmpA04LOV/feisty.tar.gz' against '/tmp/tmpA04LOV/feisty.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072


so now I'm all crabby with the work it's taking just to get to freaking Kopete 0.12.4


](*,)

---

### Post by Jucato on 2007-02-23
After adding the repository for KDE 3.5.6 and Jonathan Riddell's key:

```
sudo apt-get update
```

then

```
sudo apt-get dist-upgrade
```

---

### Post by browneyedgirl65 on 2007-02-23
OK, last bits not obvious (to me anyway)
add one of the repositories given via the synaptic package manager (tools repository, i think)
and then refresh
and then on the command line
 sudo apt-get upgrade kubuntu-desktop
will commence the upgrade to KDE 3.5.6

phew...gah
hope this helps someone else...

---

### Post by bapoumba on 2007-02-23
Moved to Installations & Upgrades :-)

---

