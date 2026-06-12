---
title: "apturl - upgrade error"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by miegiel on 2009-09-01
```
user@machine:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apturl
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.3kB of archives.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 198442 files and directories currently installed.)
Preparing to replace apturl 0.3.6ubuntu1 (using .../apturl_0.4.0ubuntu2_all.deb) ...
Unpacking replacement apturl ...
Replaced by files in installed package apturl-common ...
dpkg: error processing /var/cache/apt/archives/apturl_0.4.0ubuntu2_all.deb (--unpack):
 error creating directory `./usr/lib/python2.6/dist-packages/AptUrl/gtk': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/apturl_0.4.0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Should there be a dot leading *./usr/lib/python2.6/dist-packages/AptUrl/gtk* ? (just thinking out loud)

Oh and if you have more updates to be processed, just run
```
sudo dpkg --configure -a
```
(for those who are stuck ;))

---

### Post by mrsurb on 2009-09-01
Same problem here...

I completed the other updates with apt-get install -f

---

### Post by paul_in_london on 2009-09-01
[https://bugs.launchpad.net/ubuntu/+source/apturl/+bug/422825](https://bugs.launchpad.net/ubuntu/+source/apturl/+bug/422825)

"For a workaround, see Comment #8 ([https://bugs.launchpad.net/ubuntu/+source/apturl/+bug/422825/comments/8](https://bugs.launchpad.net/ubuntu/+source/apturl/+bug/422825/comments/8)) (corrects a typo in comment #7)".

---

### Post by exploder on 2009-09-01
Thanks paul_in_london! That took care of that problem.:D

---

### Post by rburkartjo on 2009-09-01
same problem here. paul tried your link for work around couoldnt get it to fix problem

---

### Post by Tibuda on 2009-09-01
Same here using GUI update manager. EDIT: Workaround fixed it.

---

### Post by philinux on 2009-09-02
Cheers for that. Cleared up and no errors.

---

### Post by zika on 2009-09-02
Thank You for a quick fix.

---

### Post by Locke_99GS on 2009-09-02
Using workaround:

```

locke@Pimpshit:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
locke@Pimpshit:~$ sudo apt-get --purge remove apturl-common apturl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-beaker python-mako python-egenix-mxtools python-indicate python-webkit python-utidylib python-egenix-mxdatetime python-feedparser libtidy-0.99-0 libavutil-unstripped-49
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apturl* apturl-common* ubufox*
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
locke@Pimpshit:~$ 

```

This error persists. I have no other package managers running.

---

### Post by taavikko on 2009-09-02
> **Locke_99GS said:**
> Using workaround:

```

locke@Pimpshit:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
locke@Pimpshit:~$ sudo apt-get --purge remove apturl-common apturl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-beaker python-mako python-egenix-mxtools python-indicate python-webkit python-utidylib python-egenix-mxdatetime python-feedparser libtidy-0.99-0 libavutil-unstripped-49
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apturl* apturl-common* ubufox*
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
locke@Pimpshit:~$ 

```

This error persists. I have no other package managers running.

Try removing the lock
"sudo rm /var/cache/apt/archives/lock"

And try again.

---

### Post by Locke_99GS on 2009-09-02
Why was there a left-over lock? Hmmm. Ohh well.

Success. Thank you.

---

