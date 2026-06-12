---
title: "Up date manager is not working"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by lesleytitus on 2009-11-17
I have this problem with the internet. It was not working...as in a previous thread they said to disable ipv6 and allocate a definite DNS value, my net is back up and working fine.

Now i cannot update my software library:

-When i try sudo apt-get update
```
0% [connecting to archive.ubuntu.com (1.0.0.0)]
```

When i try sys->admin->update manager it is stuck on the update at 0% for a while and then gives the following error message.


```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2  Unable to connect to archive.canonical.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Have searched google and this forum. no avail...pls help...

---

### Post by siddbjo on 2009-11-19
I found out that it is essential to remove any proxy.
This can be done in control center/network proxy and in System Tools/Configuration Editor.
This gave me a list of updates.
Check also with a System Tools/root terminal the following:
[INDENT]
[LIST]
[*]apt-get clean
[*]apt-get update
[*]apt-get upgrade
[/LIST]
[/INDENT]
Kind regards, J.

---

### Post by siddbjo on 2009-11-19
Forgot something:

Synaptic/Preferences/Network
remove any proxy and select "Direct Network".

Kind regards,

J

---

### Post by pgacv2 on 2009-11-19
Weird. What worked for me is *giving* it a proxy. The udpate manager then said that a lot of the packages I was about to download weren't authenticated, but I'm sure they are. Or hope they are.

---

