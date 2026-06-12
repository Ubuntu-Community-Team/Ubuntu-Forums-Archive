---
title: "Upgrading from Hoary to Breezy?"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by Rebeca on 2006-03-27
I installed Hoary today, and now, I'd like to upgrade to Breezy, but I'm new at this (see: I know nothing) so I need help. I have not added anything nor have I upgraded any programs. So, I don't think I need to "remove conflicting packages," do I?

Anyway, I changed my repositories to look for Breezy but after reloading sources, I saw this window:

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
**[http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Sub-process bzip2 returned an error code (2)**

[SIZE="1"]*My repositories were set to [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu), and I tried to leave those at that, but I also got errors when doing so. The first repository in the list didn't point to the archive, but to the cd which I used to make the installation for hoary.[/SIZE]

After I closed that window, another one opened: 

> The following problems were found on your system

[b]W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages)[/b]

Do I have to get rid of one of the repository entries? I simply edited the ones that were already there as it appeared here: [https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29)

I really don't want to mess up anything since this computer is the one that has the main connection to the internet. (The other ones depend on it, so I wouldn't be able to check back here if something went wrong.)

I've been reading some threads apart from the wikis, but I'd appreciate it if someone could point out one with detailed instructions for me to do this as perfectly as possible. (Please?)

---

### Post by o_fortuna on 2006-03-27
If you want to upgrade, there are two options:

**Option 1**

First, open a terminal (that's in Applications-->System Tools-->Terminal). In the window that appears, copy and paste this command in:
```
sudo gedit /etc/apt/sources.list
```
Now, when the window appears, press Ctrl+A or just select everything, then delete it all. That's right, everything. You now have a blank document in front of you. Paste the following into the document:
```

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./
```
Now save the document and close the window. You should now have the terminal sitting in front of you. Paste these two commands in:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
If you get errors, post them here so we can try to fix them.

**Option 2**
Download a Breezy install CD ([here]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/5.10/ubuntu-5.10-install-i386.iso")), burn it, and insert it into the drive. At least when I was on hoary, a screen popped up telling me to upgrade. This might be the easiest path.

---

### Post by Rebeca on 2006-03-28
Thank you. I tried option 1, and everything seems fine. I have open office 1 and 2 though. I don't see the Add/Remove Programs option anymore either. Has it been replaced or moved? I suppose I'll figure it out.

---

### Post by Vulpus on 2006-03-30
[QUOTE=Rebeca]Thank you. I tried option 1, and everything seems fine. I have open office 1 and 2 though. I don't see the Add/Remove Programs option anymore either. Has it been replaced or moved? I suppose I'll figure it out.[/QUOTE]

This is a 'weakness' of OpenOffice in that you can't just upgrade, you have to install a complete new version.  It is the same with OOo on Windows.

In theory you should be able to remove version (via synaptic) but my advice is to leave it alone for now.  I had a similar situation as you and when I removed the old version it got Ubuntu all confused.

---

### Post by Rebeca on 2006-03-31
Thank you for the advice. I will leave my old version of OpenOffice there until I'm sure I know how to safely remove it.

---

