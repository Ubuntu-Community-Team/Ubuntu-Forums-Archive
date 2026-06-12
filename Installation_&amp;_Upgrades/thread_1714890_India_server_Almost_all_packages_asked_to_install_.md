---
title: "India server: Almost all packages asked to install without verification"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by prshah on 2011-03-26
Hello,

Recently, I have been facing problems with India's repository servers.

First, I am not able to update the index files properly; I usually get the below messages:```
 
Err http://in.archive.ubuntu.com maverick/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
<..>
Err http://in.archive.ubuntu.com maverick/multiverse amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Fetched 249kB in 2min 13s (1,862B/s)
Reading package lists... Done
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37), connection timed out

<..>
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Further, practically any package I try to install gives me a warning about unverified packages:```
Install these packages without verification [Y/n]?
```

This is happening on two different machines, with two different Internet providers.

I changed from the India server to the "Select best server" (it selected one in Taiwan). Now, apt-get updates complete, and packages install smoothly, without warnings about non-verification.

Is there something wrong with the India servers? Any idea where we can report it?

---

### Post by Dutch70 on 2011-03-26
Well, you're not the only one with the problem. So it looks like the servers are down. 
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?p=10601764[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10601764")

---

