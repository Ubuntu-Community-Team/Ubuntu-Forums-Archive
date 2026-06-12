---
title: "Internet access but can't get synaptic or upgrade manager"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by Kouki on 2008-05-22
Just thought I'd get some suggestions, I'm using ubuntu on my pc now and evidently have internet access.  However I can't use SPM or the upgrade manager, both tell me I must have a network error.

I thought the server I used may have gone down so I did the system, admin, software sources and asked it to search for the best server.  It was unable to find any servers :confused:

Any suggestions?  Or has every ubuntu upgrade server in the world just gone down?

---

### Post by lswest on 2008-05-22
what are the results of these commands in the terminal: ```
sudo apt-get update
sudo apt-get upgrade
```

(the servers are fine for me)

---

### Post by Kouki on 2008-05-22
stuart@stuart-desktop:~$ sudo apt-get update
[sudo] password for stuart:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_GB
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/main Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/restricted Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/universe Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/multiverse Translation-en_GB
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

and

stuart@stuart-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


Definitely doesn't look quite right.

---

### Post by Kouki on 2008-05-22
I managed to fix it.  I searched on here but all the threads seemed to think the servers were just too busy and suggested waiting 12 hours.  Cheers for letting me know you could access them, saved the wait.

I googled the problem and Linux forums came to the rescue, someone else had experienced the problem and said he used synaptic package manager to remove anonproxy.  I don't remember installing this but it was in snp as an installed program.  I removed it, but still didn't work so I restarted the computer and this time all is good.

So if anyone gets this problem, give that a go, should sort you out.

---

