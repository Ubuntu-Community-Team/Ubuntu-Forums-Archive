---
title: "ubuntu 10.04 upgrade problem"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by wasp123 on 2012-10-05
hi, 
i've a ubuntu 10.04 version running on my laptop. however, whenever i try to install newer features/plugins, i often get errors, and not one but a whole gamut of'em !
the internet in my campus runs on proxy servers. maybe, this has something to do with it. i don't know. can someone help ?

to be more specific, i'm quoting the errors i got, when i last tried to install a missing plugin that a online radio website asked to be installed. 
the website was:  [http://www.onlineradios.in/](http://www.onlineradios.in/)
and the error i got on searching for the required plugin were: 

"
[I]W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (91.189.92.183). - connect (111: Connection refused) [IP: 91.189.92.183 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.183 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.183 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.183 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.183 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.183 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.183 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.183 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.183 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.183 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.92.150). - connect (111: Connection refused) [IP: 91.189.92.150 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_IN.bz2)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.150 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.92.190). - connect (111: Connection refused) [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Could not connect to dl.google.com:80 (74.125.236.1). - connect (111: Connection refused) [IP: 74.125.236.1 80]

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_IN.bz2](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_IN.bz2)  Unable to connect to dl.google.com:http: [IP: 74.125.236.1 80]

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Unable to connect to dl.google.com:http: [IP: 74.125.236.1 80]

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en_IN.bz2](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en_IN.bz2)  Unable to connect to dl.google.com:http: [IP: 74.125.236.1 80]

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/lucid/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.95.83). - connect (111: Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  Unable to connect to ppa.launchpad.net:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
"[/I]



i must also mention, as i find this fact of relevance, that i have these servers quoted as software sources in the update manager:

[I][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

deb [http://repo.iitd.ernet.in/ubuntu](http://repo.iitd.ernet.in/ubuntu) lucid main restricted universe multiverse

deb-src [http://repo.iitd.ernet.in/ubuntu](http://repo.iitd.ernet.in/ubuntu) lucid main restricted universe multiverse

deb [http://repo.iitd.ernet.in/ubuntu](http://repo.iitd.ernet.in/ubuntu) lucid-proposed main restricted universe multiverse

deb-src [http://repo.iitd.ernet.in/ubuntu](http://repo.iitd.ernet.in/ubuntu) lucid-proposed main restricted universe multiverse[/I]

---

