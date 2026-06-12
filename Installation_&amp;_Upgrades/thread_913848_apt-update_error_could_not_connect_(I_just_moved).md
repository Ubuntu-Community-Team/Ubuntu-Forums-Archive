---
title: "apt-update error could not connect (I just moved)"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by CodeNosher on 2008-09-08
I recently moved from the US to Nairobi, Kenya.  I say that because I wonder if this is at the root of it.

When I run aptitude, apt-get, or any update manager I get the same errors.  Here's a few:

Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg                            
  Could not connect to packages.medibuntu.org:80 (88.191.82.11). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg                             
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.45). - connect (111 Connection refused) [IP: 91.189.88.45 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                      
  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111 Connection refused)


Why would my connection be refused?  Does living in Africa mean I need to change sources?

I'm now behind a proxy, would that have something to do with it?

Thanks.

---

### Post by Muflon on 2008-09-08
Within Synaptic Package Manager you need to set the proxy settings in Settings \ Preferences \ Network.

These will then work for Update Manager.  These are in addition to the Proxy settings that you need in Firefox.

Muflon

---

### Post by CodeNosher on 2008-09-09
Thanks for the tip, it pushed me in the right path.

I checked on proxy settings for apt and found this:

[http://ubuntuforums.org/showthread.php?t=177926]("http://ubuntuforums.org/showthread.php?t=177926")

That fixed apt, so if it ever finished downloading (:popcorn:) I'll see if it fixed aptitude, too.

---

