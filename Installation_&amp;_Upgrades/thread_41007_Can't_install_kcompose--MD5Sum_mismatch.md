---
title: "Can't install kcompose--MD5Sum mismatch"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by fastluck on 2005-06-11
I'm getting an MD5Sum mismatch when I try to install kcompose.  I ran apt-get update, I tried --fix-missing and I ran apt-get install kompose several times to no avail.  The failed file is at [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb).


Here's a dump:
```
root@roadrage:/home/fastluck # apt-get install kompose
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libimlib2 libungif4g
The following NEW packages will be installed:
  kompose libimlib2 libungif4g
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 185kB/314kB of archives.
After unpacking 1024kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hoary/main libimlib2 1.1.2-2.1 [185kB]
Fetched 185kB in 25s (7289B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@roadrage:/home/fastluck #

```

Here's output from synaptic:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimlib2_1.1.2-2.1_i386.deb)
  MD5Sum mismatch

---

### Post by scoon on 2005-07-09
Hey there, 

I am getting that as well.  All I can hope is that the servers will get updated in the not to distant future.

regards, 

scoon

---

### Post by incredio on 2005-07-09
You may want to try downloading from:

[http://packages.debian.org/stable/libs/libimlib2](http://packages.debian.org/stable/libs/libimlib2)

then:

# dpkg -i  libimlib2_1.1.2-2.1_i386.deb

(I had  a similar problem with the ubuntu archive recently,
but with a different package.)

---

