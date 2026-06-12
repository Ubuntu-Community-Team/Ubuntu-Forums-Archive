---
title: "Transmission"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by peakshysteria on 2008-04-29
Did a clean install of Hardy yeasterday. Can someone tell me how to upgrade transmission?

My version is outdated. Why doesn't Transmission automatically get new updates when a new version is available?

---

### Post by iaculallad on 2008-04-29
sudo apt-get upgrade

to upgrade your installed apps

---

### Post by PmDematagoda on 2008-04-29
The version of Transmission on Hardy by default is old since that was the version on the Package Freeze, so Transmission will not be updated unless there is a security update for it that cannot be done successfully without upgrading to a newer version.

---

### Post by peakshysteria on 2008-04-29
Then how do i upgrade to the latest version which now is Transmission 1.11?? Some sites block all version but the latest. sudo apt-get upgrade doesn't work.

I'm used to µtorrent in windows. But now i'm trying to give Ubuntu a try and want to use Transmission in the beginning since it's gotten great reviews and is simple and intuitive.

---

### Post by iaculallad on 2008-04-29
Try googling for the Transmission 1.11?? deb file (latest file version you mentioned). If you could locate one, do a manual install. Maybe, its not in the repo.

---

### Post by FredB on 2008-04-29
[http://www.getdeb.net/search.php?keywords=transmission](http://www.getdeb.net/search.php?keywords=transmission)

Here you have it.

I do prefer deluge anyway ;)

---

### Post by sulemankm on 2008-04-29
Transmission 1.11 is available at he GetDeb.net sit.

Here is the link [http://www.getdeb.net/search.php?keywords=transmission](http://www.getdeb.net/search.php?keywords=transmission)

GetDeb generally has newer versions of the software packages than the ubuntu repositories.

---

### Post by peakshysteria on 2008-04-29
> **sulemankm said:**
> Transmission 1.11 is available at he GetDeb.net sit.

Here is the link [http://www.getdeb.net/search.php?keywords=transmission](http://www.getdeb.net/search.php?keywords=transmission)

GetDeb generally has newer versions of the software packages than the ubuntu repositories.

I'm running Hardy 64 bit. The links gives me:

Selected Ubuntu version no longer supported by Getdeb, this package will not be updated !

But i got transmission-1.11.tar.bz2 from the transmission site. How can i install this? (i probably should ask this question in the beginnners section...)

---

### Post by PmDematagoda on 2008-04-29
It works for me, try this link:-
[http://www.getdeb.net/release.php?id=2447](http://www.getdeb.net/release.php?id=2447)

---

### Post by peakshysteria on 2008-04-29
> **PmDematagoda said:**
> It works for me, try this link:-
[http://www.getdeb.net/release.php?id=2447](http://www.getdeb.net/release.php?id=2447)

Thanks man. A bit back and forth here. But i managed to install the right version (the last one). While swearing over my own incompetence i also installed Deluge (thanks FredB), which seems very nice and reliable. Not sure how i can point my Firefox to make Deluge default client since I'm not sure where to find the installed file!? So a pointer on that would be nice. I'm still not completely on safe ground browsing the file structure of Ubuntu I'm sad to say.

Anyway, I'll give both a try and choose later.

If people have other clients to recommend and why one should use other clients than the above mentioned they are welcome to tell us.

I guess we all want supported/allowed clients, reliable, maintained clients with small memory footprints.

---

### Post by phinn on 2008-05-01
Yea you'll have to goto Getdeb for any new packages unfortunately. Ubuntu's software upgrade policy is the worst. There should be a repository that you can click that will update software for reasons other than security updates. Backports just isn't enough.

The problem with using Getdeb is it causes dependency issues for me all the time.
edit: so use  dpkg -i [packagename]

It makes me wonder if we'll have to stay with Firefox 3 Beta until Ubuntu 8.10 comes out.(Unless we manually install it from the site)

---

### Post by peakshysteria on 2008-05-02
How can I point my Firefox to make Deluge default client since I'm not sure where to find the installed Deluge file (or what it's called!? It would be nice to have a torrent start without having to manually drop the torrent on the Deluge client. A pointer on that would be nice. I'm still not completely on safe ground browsing the file structure of Ubuntu I'm sad to say.

And how do i upgrade Deluge without breaking anything?? sudo apt-get upgrade doesn't work. Downloading the latest version and installing on top fails (it says the installed fail). I tried to [force version in synaptic](https://help.ubuntu.com/community/SynapticHowto). But the force version field in the package menu is grayed out for some strange reason.

[color=#FF0000]Solved the upgrade issue with:[/color] sudo aptitude remove deluge-torrent-common deluge-torrent in terminal. Then installed the downloaded .deb package. All is well :) 

**No i only need to know how to make Firefox open torrents with Deluge as the default client instead of transmission....Any takers?**

---

