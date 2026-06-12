---
title: "Edgy upgrade error: Sub-process gzip returned an error code (1)"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by nismoskys on 2006-10-26
i just wanted to upgrade my system to Edgy from Dapper but it's not working, following the guide at [https://help.ubuntu.com/community/EdgyUpgrades#head-bae1bd1cc0751cc10225e7845e18100ae83668ae]("https://help.ubuntu.com/community/EdgyUpgrades#head-bae1bd1cc0751cc10225e7845e18100ae83668ae")

i tried the update manager which kept giving me the error: ```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  Sub-process gzip returned an error code (1)
```

then when i tried using apt-get i got pretty much the same thing.
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
......
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources
Get:6 http://archive.ubuntu.com edgy/multiverse Sources [55.3kB]
99% [6 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/multiverse Sources
  Sub-process gzip returned an error code (1)
Fetched 6B in 27s (0B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

i dont know what to do.

---

### Post by jpeddicord on 2006-10-26
I experienced this exact problem just a few minutes ago. The repositories may be down or are being updated. Try waiting a couple of houurs, and if it still does not work, restart your system.

---

### Post by nismoskys on 2006-10-26
alright then, thanks.

---

### Post by KageKeeper on 2006-11-03
I have been trying for the past two days to upgrade and I continuously get this error.

Waiting does not seem to be helping.

Any suggestions?

---

### Post by nismoskys on 2006-11-04
you know i actually did end up getting it to work, but then i chose not to upgrade after all, i guess thats why i forgot to post the solution i got.

i got from some website that if u change the affected server in the sources.list file to begin with "ftp://" instead of "http://" it'll work.

i actually ended up just downloading the iso for edgy and installed it seperately though.

---

### Post by pzonik on 2006-11-05
I have not upgrade system (pure Edgy installation), and when I use 'sudo apt-get update' I have also problem with:

[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)

Everything works fine, but I hate when I have errors.

---

### Post by cmnorton on 2007-09-22
> **jacobmp92 said:**
> I experienced this exact problem just a few minutes ago. The repositories may be down or are being updated. Try waiting a couple of houurs, and if it still does not work, restart your system.

I am encountering this same error. I have tried this a few times in the last hour. I rebooted my system. If there is some configuration I should fix, would someone give me a pointer to it?

Here is the error:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

If I cannot get this to work, is it possible to use the live CD for 6.10 and request an upgrade? If so, a pointer to those instructions would be appreciated.

I have looked at bug #59353 in launchpad, and issuing the following command was discussed followed by restarting the upgrade.

sudo rm -v /var/lib/apt/lists/partial/*

I tried that with no success. I would be very interested in a workaround, as I would like to avoid a clean install.

Thanks
cmn

---

