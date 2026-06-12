---
title: "failed to fetch update"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by thurstonxander on 2011-04-21
when I check for updates in the update manager on ubuntu 10.10 I get this error message

W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-desktop/gnome3-builds/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-desktop/gnome3-builds/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found 
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-desktop/gnome3-builds/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-desktop/gnome3-builds/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found 
, E:Some index files failed to download, they have been ignored, or old ones used instead.

 what have I done, and how can I repair it?

---

### Post by Hedgehog1 on 2011-04-21
Your version of Ubuntu is no longer supported:

[**intrepid-ibex-to-lose-support-in-april**]("http://www.zdnet.co.uk/news/application-development/2010/03/30/intrepid-ibex-to-lose-support-in-april-40088481/")

The PPAs have been taken down to be resued.

It is time to move to a newer version of Ubuntu.

May I suggest the very nice 10.04.02 LTS version?

***The Hedge***

:KS

---

### Post by thurstonxander on 2011-04-22
I'm using maverick meerkat 10.10. Besides Natty, (which is not officially released yet) I have the most recent version of Ubuntu.

---

### Post by dino99 on 2011-04-22
look at your sources.list, you should only have maverick or natty repo, nothing else

sudo gedit /etc/apt/sources.list

---

### Post by plucky on 2011-04-22
> **thurstonxander said:**
> I'm using maverick meerkat 10.10. Besides Natty, (which is not officially released yet) I have the most recent version of Ubuntu.

Open Software Sources and remove any source that has "Intrepid" in it.

Also your PPA is incorrect as you are getting the "404 not found" error.

[http://ppa.launchpad.net/ubuntu-desktop/gnome3-builds/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-desktop/gnome3-builds/ubuntu/dists/maverick/main/source/Sources.gz)

Should be

[http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-desktop/ppa/ubuntu/dists/maverick/main/source/Sources.gz)

Again can be corrected in Software Sources.

i.e substitute ppa for gnome3-builds


Good Luck

---

### Post by MrSpike16 on 2011-04-22
The word in the OP's original message is an adjective and not referring to a Ubuntu Release.

The PPA repositories were for installing Gnome 3 on Ubuntu 10.10 (Maverick) so you could experiment and test it while in development.

Now that Gnome 3 has been released these repositories have probably been removed.

Unclick the boxes or remove the entries for these PPAs in Software Sources.  Once the source lists have been rebuilt the errors should be gone.

It doesn't look like there will be a release of Gnome 3 for 10.10 so if you installed Gnome 3 there won't be anymore updates for it.

---

### Post by thurstonxander on 2011-04-22
Thanks guys! System works fine now. I love the forum!

---

