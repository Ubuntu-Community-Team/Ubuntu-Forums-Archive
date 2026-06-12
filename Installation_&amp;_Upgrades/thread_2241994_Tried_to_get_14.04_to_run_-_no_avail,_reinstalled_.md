---
title: "Tried to get 14.04 to run - no avail, reinstalled 13.04 and Software Center deosn't w"
date: 2014-08-29
forum: Installation &amp; Upgrades
---

### Post by hugo.k.becker on 2014-08-29
So I tired to get 14.04 to run - it failed big time, and the attmepts to resolve the no display issue didn't work - so I scraped odds and ends off the partition my /home was on - and reinstalled a 13.04 image. It runs but I cannot install anything from Software Center, the Plug-In Finder Service 2 for Firefox is in a loop - and when I try the odds and ends already mentioned about this problem I get nowhere. 

I've gone into Systems & Settings > Software & Updates and tried the US server and the main server for updates. I get the following error(s) when I run '$sudo apt-get upgrade && 
sudo apt-get update'

**W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]**

An attempt to ping the IP works:

[B]PING 91.189.91.14 (91.189.91.14) 56(84) bytes of data.
64 bytes from 91.189.91.14: icmp_req=1 ttl=49 time=58.1 ms
64 bytes from 91.189.91.14: icmp_req=2 ttl=49 time=56.1 ms
64 bytes from 91.189.91.14: icmp_req=3 ttl=49 time=55.8 ms
64 bytes from 91.189.91.14: icmp_req=4 ttl=49 time=55.8 ms[/B]

But yes the 404 is there at the site. So how do I get anything updated?

I'm clueless (most of the time ; -). Any ideas?

---

### Post by QIII on 2014-08-29
13.04 is past its EOL and the repos have been moved.  That is why you are getting the 404s.

As we no longer support EOL versions on the Forums, the staff recommends clean installs of a supported version -- currently 12.04 and 14.04.  So we won't support help with questions about 13.04.

If you were having problems with 14.04, did you ask for assistance?

---

### Post by hugo.k.becker on 2014-08-29
12.04 it is then!

---

### Post by hugo.k.becker on 2014-08-29
12.04 went in perfectly - updates are active - now to reassemble the multitude of usb connected hard drives - I need to build slightly more coherent work spaces

---

