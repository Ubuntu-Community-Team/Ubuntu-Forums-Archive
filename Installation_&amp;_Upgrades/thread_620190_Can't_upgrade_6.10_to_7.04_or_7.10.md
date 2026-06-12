---
title: "Can't upgrade 6.10 to 7.04 or 7.10"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by qwert231 on 2007-11-22
I get this message:
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz) 404 Not Found

When I try to do the standard GUI from 6.10 to 7.04.

I thought I'd go to 7.04 then 7.10.

Thoughts, suggestions? What should I look for?

---

### Post by MJN on 2007-11-22
It looks like the medibuntu URLs have changed - see [https://answers.launchpad.net/ubuntu/+question/15530](https://answers.launchpad.net/ubuntu/+question/15530) and following the resolution steps.

Edit: Scratch that - I've just noticed you were getting 404 errors, i.e. *page/file* not found (and not that the site was not found) hence the solution I proposed may not be applicable to you.

Mathew

---

### Post by qwert231 on 2007-11-27
Still having this issue, can anybody help?

---

### Post by MJN on 2007-11-27
Have you tried changing the relevent entries in /etc/sources.list to the following?
 
deb [_[COLOR=#606420]http://packages.medibuntu.org/[/COLOR]_]("http://packages.medibuntu.org/") edgy free non-free
deb-src [_[COLOR=#606420]http://packages.medibuntu.org/[/COLOR]_]("http://packages.medibuntu.org/") edgy free non-free
 
Mathew

---

### Post by PmDematagoda on 2007-11-27
Why don't you simply disable the offending repository addresses?

Open the sources.list file for editing using:-

```
sudo gedit /etc/apt/sources.list
```

Then uncomment(Type # infront of them) the Medibuntu repository addresses and any other 3rd party addresses, you can re-enable them after the upgrade. After the sources.list file has been edited, do:-

```
sudo apt-get update
```

After that is complete try upgrading the OS again.

---

### Post by MJN on 2007-11-27
The risk with disabling repositories is that those packages will obviously be frozen yet they may be dependencies of other packages undergoing an upgrade. The real danger comes from ending up in a state where half the installation has been upgraded yet the other half stalls due to the unmet dependencies - the resulting hybrid release state will be unstable at best and more likely entirely borked.
 
Mathew

---

### Post by PmDematagoda on 2007-11-28
Since the Medibuntu repositories are third party and are not supported by Ubuntu officially, the Medibuntu repositories do not take any part in the upgrade process which means that it is very safe(In some cases necessary) to disable such third party repositories before an upgrade.

---

### Post by MJN on 2007-11-28
Ah, okay. I'm not familiar with Medibuntu and just assumed it was inter-related.
 
Apologies for the misinformation.
 
Mathew

---

### Post by qwert231 on 2007-12-07
So, for your information, I'm up to 7.04 now. Can't get to 7.10 but I think it's a simliar issue, bad data in the sources list.

I burnt an ISO of 7.10, so will try to upgrade off of that.

---

### Post by MJN on 2007-12-07
What's the error? And what does your /etc/apt/sources.list look like now?

Mathew

---

