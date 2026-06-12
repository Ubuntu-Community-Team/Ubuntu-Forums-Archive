---
title: "apt-get upgrade fails"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by jezzab on 2011-12-01
Hi Everyone, 

We have a new install of 11.10 server. We can access it internally and the box can ping out to ubuntu.com.

But the apt-get upgrade fails with:


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en](http://au.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en)  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22: Invalid argument)

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_AU](http://au.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_AU)  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22: Invalid argument)

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en](http://au.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en)  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22: Invalid argument)

I tried this yesterday and the same result. The au.archive seems to be up and running fine. 

Any ideas? Is this a proxy issue?

Kind Regards,
J

---

### Post by drs305 on 2011-12-01
It could be a proxy issue. I've not worked my way around oneiric proxy issues, but click the HOME (upper left) button to open DASH, then type Network. Click on 'Network' and see what you have under the "Network Proxy" setting. See if selecting "None" solves it.

---

### Post by jezzab on 2011-12-01
Hi drs305, thanks for the suggestion. It's a fresh server install so no dash ;) Our network is behind a proxy so I would've assumed it necessary.

Changing the repo to US also fails. Seems to be local issue.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_AU](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_AU)  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22: Invalid argument)


Cheers,
J

---

### Post by drs305 on 2011-12-01
Sorry about that...

I have clicked on the links and they are functioning properly, as you also indicated.

I did an error search and in several posts the proxy was exported incorrectly, with this being the proper format
export http_proxy=http://192.168.1.11:8080
export ftp_proxy=http://192.168.1.11:8080

---

### Post by jezzab on 2011-12-01
> **drs305 said:**
> Sorry about that...

I have clicked on the links and they are functioning properly, as you also indicated.

I did an error search and in several posts the proxy was exported incorrectly, with this being the proper format
export http_proxy=http://192.168.1.11:8080
export ftp_proxy=http://192.168.1.11:8080


Thanks, I tried no proxy and re-exporting it - same result unfortunately.

---

### Post by jezzab on 2011-12-01
> **jezzab said:**
> Thanks, I tried no proxy and re-exporting it - same result unfortunately.


Resolved! 

This thread gave me some clues [http://ubuntuforums.org/showthread.php?t=1787267](http://ubuntuforums.org/showthread.php?t=1787267)

For some reason even re-exporting the proxy didn't affect the 
 /etc/apt/apt.conf file. It had an old setting I'd put in there. 

Clearing it fixed the problem!
Cheers.

---

### Post by drs305 on 2011-12-01
lol.

I'd found a thread about /etc/apt/apt.conf and found I didn't have that file. So I didn't pursue it and looked at other posts.

Glad you figured it out.

You can mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post if you have no further issues.

---

