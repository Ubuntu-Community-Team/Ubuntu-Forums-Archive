---
title: "Problems updating from behind a proxy"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by Cpt.Cheese on 2010-03-08
So, about 2 weeks ago, I decided to update Ubuntu while at school. I launched Aptitude, and to my dismay, it said that It couldn't access the files. I tried a few days later at home, and the same problem happened. So I checked the network proxy settings, making sure that There weren't any while I was at home, and after doing that tried again, same problem. So a few days later I looked up how to update behind a proxy on google so I could update at school, and still nothing.  

So the question is, What can I do to update Ubuntu at school, and how can I change the settings So that when I'm not at school, to update at home?

---

### Post by crlang13 on 2010-03-08
Hey cheese,

have you checked system > preferences > network proxy?

You can configure your schools proxy and apply it system wide and it should work for updates and package downloads.

There may be a problem though in that your schools proxy does not allow certain download types and only allows general surfing.

---

### Post by Cpt.Cheese on 2010-03-08
Yeah, I have and thats the strange thing. I would think that just having the system proxy set to my school would do the trick.

---

### Post by crlang13 on 2010-03-08
Hmm...

Does your school provide an automatic configuration script or do you have to in a different setting for each protocol?  My uni supplies both.

I'm not sure what protocol the update manager uses, but my uni's proxy only supports HTTP and FTP and I've gotten it to work before.

This may sound very "I.T. Crowd," but have you tried setting the proxy to system wide and turning it the computer off and on again?  The reason I ask is that I've gotten the updates to work before, but I don't think the system settings change unless you close the package and update managers.  The update manager runs in the background so rebooting should do the trick.  Unless you're confident enough to kill all of its processes and reopen it, but a reboot should do the trick.

---

### Post by Cpt.Cheese on 2010-03-09
I don't know the answer to that first question, I can ask my Digital media teacher today though. 

I have tried turning it off and on after applying the proxy settings, and that still hasn't helped. 
(And dispite the bit of off topic-ness, I do love myself some I.T. crowd)

EDIT: Just to be safe I restarted again, and it still didn't help. For more information I copied the Thing that it gives me when I try to update

> W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic/Release.gpg](http://ubuntu.media.mit.edu/ubuntu/dists/karmic/Release.gpg)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/Release.gpg](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/Release.gpg)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/Release.gpg](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/Release.gpg)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://ubuntu.media.mit.edu/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 192.168.0.1:800 (192.168.0.1). - connect (111: Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead**.**

---

### Post by crlang13 on 2010-03-09
I'm stumped then mate. I don't know enough... I'll keep my eyes open to see if something pops up.  Goodluck

---

### Post by Cpt.Cheese on 2010-03-10
Ah, Well apparently my Digital media teacher said that the Repository mirrors are blocked by the school firewall, so I guess that solves this question. However before i give it the solved status, I'm going to see If I can update at home so We can get that fixed too.

---

### Post by crlang13 on 2010-03-10
That's annoying that it's blocked...

I looked into the error message a bit (I was curious).  As your teacher said, the error seems to suggest a problem with the proxy, not your computer or the settings... 

Basically I guess that means you can't update at school :(

---

