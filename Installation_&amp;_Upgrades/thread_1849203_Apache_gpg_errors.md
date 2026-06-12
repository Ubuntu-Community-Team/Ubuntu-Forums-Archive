---
title: "Apache gpg errors"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by OpenJacob on 2011-09-24
Hi
I just updated Apache and now I get this error from Dpkg:
```
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-proposed/InRelease  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-backports/InRelease  

W: Failed to fetch http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/InRelease  

W: Failed to fetch http://ppa.launchpad.net/n-muench/burg/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://deb.opera.com/opera/dists/stable/InRelease  

W: Failed to fetch http://deb.opera.com/opera-beta/dists/stable/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-proposed/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-backports/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/Release.gpg  Could not resolve 'linux.avasys.jp'

W: Failed to fetch http://ppa.launchpad.net/n-muench/burg/ubuntu/dists/natty/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Could not resolve 'deb.opera.com'

W: Failed to fetch http://deb.opera.com/opera-beta/dists/stable/Release.gpg  Could not resolve 'deb.opera.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

``` I didn't install anything after Apache and haven't even used this system in the last two weeks. I am connected to the network and have no trouble downloading with torrents so the issue must be in Dpkg or the Ubuntu main server.
Can anyone give me a hand?

---

### Post by OpenJacob on 2011-09-24
I have tried on another system on the same network without issue so know I can rule out both the network and the repos them selfs.

So what is wrong with my system?

---

### Post by OpenJacob on 2011-09-25
Two more people seem to have similar issues:
[http://osdir.com/ml/digikam-users/2011-07/msg00084.html](http://osdir.com/ml/digikam-users/2011-07/msg00084.html)
[http://www.linux-archive.org/ubuntu-user/535896-apt-get-issues-looks-like-some-corruption.html](http://www.linux-archive.org/ubuntu-user/535896-apt-get-issues-looks-like-some-corruption.html)

---

### Post by OpenJacob on 2011-09-25
Any thoughts?

---

### Post by OpenJacob on 2011-09-27
I did use ping to test my connection immediately after the error. I'm trying to make this system into a Apache server connected to my network. No other computer has this error and I'v run some tests on the server connections and Apache and all looks fine.

Do you know of a way to test Dpkg and its connection to Ubuntu main server to see what is going on? I also installed Apache on my laptop to see if that replicates the incident, it did not, so I must have done something to Dpkg without knowing.

I tried Apt and that to seems dead. I found this:
[http://ubuntuforums.org/showthread.php?t=1787485](http://ubuntuforums.org/showthread.php?t=1787485)
But rm cannot remove `/var/lib/apt/lists/partial' as it Is a directory, I will try to remove the directory by hand.


That yielded another error:
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

And upon reinstating the directory the old error pops up again.

I might try to upgrade from a live-dvd but I don't wont to loos my source code. I tested apt-fast and still have the same issue so it must be something other then apt, dpkg and I am quite sure it's not my network.

[http://www.google.com/search?sourcei...+ppa+inrelease](http://www.google.com/search?sourcei...+ppa+inrelease) turned up even more and a bug report going back to 10.04, I'm on 11.04 so Id assume they are not connected.

I have verified that it is not an issue with opendns.
Can someone rename this post "APT gpg errors"?

---

