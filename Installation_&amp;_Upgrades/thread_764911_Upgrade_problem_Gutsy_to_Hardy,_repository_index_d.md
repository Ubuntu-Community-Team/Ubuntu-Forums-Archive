---
title: "Upgrade problem: Gutsy to Hardy, repository index download"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by timhodkinson on 2008-04-24
I get this "Error During Update" message when trying to upgrade from Gutsy to Hardy:

> Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release) Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

I've changed servers and even tried the main one, but they all give me this message and then the only option is to cancel the upgrade.

I've disabled all 3rd Party repositories and all the regular updates for Gutsy have been installed.

Any thoughts?

---

### Post by depele on 2008-04-24
I believe I have to wait a bit longer because everybody is upgrading now.

The website [www.ubuntu.com](www.ubuntu.com) is also down.

I think the servers can't handle the amount of requests.

grtz.

arne

---

### Post by everythingdaniel on 2008-04-24
NICE, we have the same problem!



[http://ubuntuforums.org/showthread.php?t=764842](http://ubuntuforums.org/showthread.php?t=764842)


:lolflag:

---

### Post by cdawzrd on 2008-04-24
I'm sure it's because the repo servers are getting slammed right now.  I'm getting the same message, and it happens at random points of hitting the repos for package lists.

---

### Post by timhodkinson on 2008-04-24
I suspect it probably is a routine upgrade release issue like server load as you've both suggested, but I've found a couple of mirrors that seem very responsive, but just can't seem to provide that one index file.

Anyhow, I'm sure it'll sort itself out in a day or so.  That's not too long to wait, is it? :)

This is my third upgrade and every time I say to myself, I'm not going to upgrade on the very first day next time when the servers are so busy ...but here I am again.

Upgrading to Gutsy took me 12 hours on the first day.  If I'd waited a couple of days I could have done it in half an hour.

---

### Post by timhodkinson on 2008-04-24
From my Googling research, I'm beginning to think the problem is the repository sources list /etc/apt/sources.list

This seems to be the exact same problem someone had with the last upgrade which was to Gutsy.  Two lines in the sources.list got pushed together.

If you do start editing your sources.list, back up the current copy first...

I've learned that the hard way.

---

### Post by timhodkinson on 2008-04-24
Forgot to  add this link:
[http://lists.gllug.org.uk/pipermail/gllug/2007-November/070646.html]("http://lists.gllug.org.uk/pipermail/gllug/2007-November/070646.html")

It's the same problem I'm having now; the only difference is the person was upgrading from Fiesty to Gutsy.

---

### Post by timhodkinson on 2008-04-24
Yep!  That fixed it.

I chopped off a few lines from /etc/apt/sources.list file and then opened up Synaptic and reloaded the repository and then exited and started up the Update Manager and everything's fine now and it's downloading the update packages.

I've got a download speed of 535kbps using a mirror.  Should all be done in half an hour.

Google is Linux's best friend.

---

### Post by ptcbus on 2008-04-24
To download very quickly use torrents. I used torrents and was very fast. I have listed the steps here: [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by darkazurka on 2008-05-08
I've downloaded through torrent the image that is for upgrading (alternative), and it didn't work. Gave me this error: [http://img145.imageshack.us/my.php?image=upgradeerrortohardygx9.png](http://img145.imageshack.us/my.php?image=upgradeerrortohardygx9.png)

So now I'm upgrading through the Update Manager, and it's currently downloading the updates, estimating it to 1 hour time of download.

---

