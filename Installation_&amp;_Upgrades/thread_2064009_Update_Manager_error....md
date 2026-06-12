---
title: "Update Manager error..."
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by cjohns30 on 2012-09-28
I am receiving an error when running sudo apt-get update

any ideas?



Fetched 2,154 kB in 2min 12s (16.3 kB/s)
Reading package lists... Error!
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by kc1di on 2012-09-28
Hi cjohns30 & Welcome to Ubuntu forums,

I've run into this before and here's how I fixed it on my machine.
your mileage may vary.

in a terminal execute the following commands one at a time.

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

you can copy the command and paste it into your terminal.

Good Luck!

---

### Post by cjohns30 on 2012-09-28
That worked beautifully! Thank you!

---

### Post by kc1di on 2012-09-28
> **cjohns30 said:**
> That worked beautifully! Thank you!

your Welcome - enjoy :)

when  you have a chance please mark thread as Solved -Thanks.

---

