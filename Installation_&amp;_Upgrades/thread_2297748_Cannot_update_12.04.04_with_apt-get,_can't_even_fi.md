---
title: "Cannot update 12.04.04 with apt-get, can't even finish downloading package lists"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by tra4d on 2015-10-06
I have been trying to update our 12.04.04 server for some time without luck.  I am in Canada, on our headless server using the 'mirrors' in the config file to get the best server/mirror/connection.  Still no luck.

It takes hours and hours just to fail on getting the package lists, doesn't even get to downloading and installing them.  Tried to do 'apt-get clean'.  Still nothing.  

Here is the tail end of 'apt-get update':
```
Get:532 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:533 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:534 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:535 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:536 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:537 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:538 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:539 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:540 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:541 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:542 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:543 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:544 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:545 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:546 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:547 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:548 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:549 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:550 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:551 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:552 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:553 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:554 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:555 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:556 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:557 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:558 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:559 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:560 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:561 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:562 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:563 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:564 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:565 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:566 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:567 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:568 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:569 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:570 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:571 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:572 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:573 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:574 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:575 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:576 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:577 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:578 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:579 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:580 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:581 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:582 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:583 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:584 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:585 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:586 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:587 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:588 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:589 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:590 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:591 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:592 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:593 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:594 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:595 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:596 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:597 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:598 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:599 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:600 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:601 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:602 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:603 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:604 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:605 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:606 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:607 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:608 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:609 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:610 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:611 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:612 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:613 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:614 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:615 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:616 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:617 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:618 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:619 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:620 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:621 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:622 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:623 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:624 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:625 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:626 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:627 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:628 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:629 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:630 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:631 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:632 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:633 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:634 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:635 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:636 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:637 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:638 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:639 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:640 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:641 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:642 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:643 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:644 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:645 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:646 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:647 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:648 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:649 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:650 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:651 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:652 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:653 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:654 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:655 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:656 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:657 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:658 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:659 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:660 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:661 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:662 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:663 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:664 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:665 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:666 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:667 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:668 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:669 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:670 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:671 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:672 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:673 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:674 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:675 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:676 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Err http://ca.archive.ubuntu.com precise-security Release

Hit http://ca.archive.ubuntu.com precise/main amd64 Packages
Hit http://ca.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com precise/main i386 Packages
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex
Get:677 http://ca.archive.ubuntu.com precise-updates/main amd64 Packages [938 kB]
Get:678 http://ca.archive.ubuntu.com precise-updates/restricted amd64 Packages [16.1 k
Get:679 http://ca.archive.ubuntu.com precise-updates/main i386 Packages [986 kB]
Get:680 http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages [16.1 kB
Get:681 http://ca.archive.ubuntu.com precise-updates/main TranslationIndex [10.6 kB]
Get:682 http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex [7,29
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA
Hit http://ca.archive.ubuntu.com precise/main Translation-en
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en
Get:683 http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA [10.4 kB]
Get:684 http://ca.archive.ubuntu.com precise-updates/main Translation-en [406 kB]
Get:685 http://ca.archive.ubuntu.com precise-updates/restricted Translation-en [3,857
Fetched 4,915 kB in 11h 49min 11s (115 B/s)
Reading package lists... Done
W: GPG error: mirror://mirrors.ubuntu.com precise-backports Release: The following sigF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated aused. GPG error: http://ca.archive.ubuntu.com precise-security Release: The following 6EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-security/Release

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_distsackages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_distsckages  Hash Sum mismatch

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/main/binary-aMirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/restricted/biable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/universe/binale [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/main/binary-iirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/restricted/bible [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/universe/binae [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-updates/restrt Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-updates/univeAcceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-updates/main/table [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-updates/restr Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-updates/univecceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/restot Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/univ Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/mainptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/restt Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/univAcceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch copy:/var/lib/apt/lists/partial/mirrors.ubuntu.com_mirrors.txt_distranslation-en  Hash Sum mismatch

W: Some index files failed to download. They have been ignored, or old ones used insted
```

I have tried to comment out sections to try and get it to work, still no.  Tried searching and searching the forumn but could only come up with this [thread]("http://ubuntuforums.org/showthread.php?t=2295044") which didn't help.

Here is our sources.list config (there is nothing in /etc/apt/sources.list.d/):
```
deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe #multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe #multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-backports main restricted universe #multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-security main restricted universe #multiverse

deb http://ca.archive.ubuntu.com/ubuntu precise main restricted
#deb-src http://ca.archive.ubuntu.com/ubuntu precise main restricted

deb http://ca.archive.ubuntu.com/ubuntu precise-updates main restricted
#deb-src http://ca.archive.ubuntu.com/ubuntu precise-updates main restricted

deb http://ca.archive.ubuntu.com/ubuntu precise-security main restricted
#deb-src http://ca.archive.ubuntu.com/ubuntu precise-security main restricted
deb http://ca.archive.ubuntu.com/ubuntu precise-security universe
#deb-src http://ca.archive.ubuntu.com/ubuntu precise-security universe
#deb http://ca.archive.ubuntu.com/ubuntu precise-security multiverse
#deb-src http://ca.archive.ubuntu.com/ubuntu precise-security multiverse

```

More info:

Network speed is fine:[IMG]http://www.speedtest.net/result/4722590686.png[/IMG]

---

### Post by Bashing-om on 2015-10-06
tra4d; Hello;

Though I am not familiar with your mirroring system .. I can see 2 problems that the package manager advises of.

1) GPG error:
Re-install the signing key(s):
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6EAF437D05B5

```

2) Hash Sum Mismatch :
Often caused by corrupted control files:
Try:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
Where the data bases are removed and in the 'update' process these files are rebuilt.

Could be that 
[INDENT][INDENT]all is good now 
[/INDENT][/INDENT]

---

### Post by tra4d on 2015-10-06
Bashing-om

Thanks for the reply, tried to reinstall the signing key:
```
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.TfKYgndF0G --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6EAF437D05B5
gpg: "6EAF437D05B5" not a key ID: skipping
```

Also, for the mirrors:
[https://mvogt.wordpress.com/2011/03/21/the-apt-mirror-method/](https://mvogt.wordpress.com/2011/03/21/the-apt-mirror-method/)

Update:  after looking at the list of installed keys using '# apt-key list' I was able to see that there were some extra characters in front of the actual key.  Took them off and this command worked.  Trying the update again (after removing files as suggested).

---

### Post by Bashing-om on 2015-10-06
tra4d; K

:)

[INDENT][INDENT][INDENT]making progress
[/INDENT][/INDENT][/INDENT]

---

### Post by tra4d on 2015-10-06
Seems to be stuck as before:
```
ilserv:~# apt-get clean
root@mailserv:~# apt-get update
Get:1 http://ca.archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://ca.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:3 http://ca.archive.ubuntu.com precise-security Release.gpg [198 B]
Hit http://ca.archive.ubuntu.com precise Release
Ign http://ca.archive.ubuntu.com precise Release
Get:4 http://ca.archive.ubuntu.com precise-updates Release [196 kB]
Get:5 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Ign http://ca.archive.ubuntu.com precise-updates Release
Get:6 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:7 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:8 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:9 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:10 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:11 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:12 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:13 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:14 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:15 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:16 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:17 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:18 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:19 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:20 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:21 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:22 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:23 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:24 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:25 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:26 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:27 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:28 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:29 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:30 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:31 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:32 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:33 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:34 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]

```

will let it go and see what happens.

---

### Post by Bashing-om on 2015-10-06
tra4d; so far

So good. It is getting, updating (hit) and ignoring (ign).
Just doing it's thing

---

### Post by tra4d on 2015-10-07
Same results:
```
Get:83 http://archive.ubuntu.com/ubuntu/ precise/universe Translation-en [3,341 kB]
Get:84 http://archive.ubuntu.com/ubuntu/ precise-updates/main Translation-en_CA [10.4 kB]
Get:85 http://archive.ubuntu.com/ubuntu/ precise-updates/main Translation-en [406 kB]
Ign http://archive.ubuntu.com/ubuntu/ precise-updates/restricted Translation-en_CA
Fetched 12.7 MB in 18min 32s (11.4 kB/s)
W: GPG error: mirror://mirrors.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/main/binary-amd64/Packages  406  Not Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/restricted/binary-amd64/Packages  406  Not Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/universe/binary-amd64/Packages  406  Not Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/main/binary-i386/Packages  406  Not Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/restricted/binary-i386/Packages  406  Not Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise/universe/binary-i386/Packages  406  Not Acceptable [Mirror: http://mirror.its.sfu.ca/mirror/ubuntu/]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Here is what I did with respect to the keys:
```
~# apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.Rh1ZJUl44O --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

```

And from apt-key list:
```
# apt-key list
/etc/apt/trusted.gpg
--------------------
pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

```

---

### Post by dino99 on 2015-10-07
check these pathes
**** Not Acceptable [Mirror: [http://mirror.its.sfu.ca/mirror/ubuntu/]](http://mirror.its.sfu.ca/mirror/ubuntu/]) *********

---

### Post by tra4d on 2015-10-07
Is this a result of the earlier key error?  They list of mirrors is provided by ubuntu.   ????

---

### Post by tra4d on 2015-10-08
Is it normal to take this long (been running since yesterday)?
```
Get: 1223 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1224 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1225 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1226 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1227 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1228 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1229 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1230 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1231 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1232 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1233 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1234 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1235 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
5% [1235 Packages 0 B/1,273 kB 0%]
```

---

### Post by tra4d on 2015-10-08
Still going...```
Get: 1572 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1573 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1574 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1575 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1576 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1577 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1578 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1579 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1580 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get: 1581 http://ca.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
5% [1581 Packages 0 B/1,273 kB 0%]
```

---

### Post by Bashing-om on 2015-10-08
tra4d; Uh uhhh ..

Syncing (apt-get update ) the data base should only take a matter of scant minutes.
It may well be above my skill level to isolate the fault. I would at this time terminate the update process:
Key combo ctl+c
And closely examine what the fetch files are:
once more an updated:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
just to make sure there is nothing in the 3rd party directory.

Make sure that we can connect to your respective mirror.

[INDENT][INDENT]i be always open
[INDENT][INDENT][INDENT]to a learning experience
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tra4d on 2015-10-08
```
# cat -n /etc/apt/sources.list
     1  deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe #multiverse
     2  deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe #multiverse
     3  deb mirror://mirrors.ubuntu.com/mirrors.txt precise-backports main restricted universe #multiverse
     4  deb mirror://mirrors.ubuntu.com/mirrors.txt precise-security main restricted universe #multiverse
     5
     6  deb http://ca.archive.ubuntu.com/ubuntu precise main restricted
     7  #deb-src http://ca.archive.ubuntu.com/ubuntu precise main restricted
     8
     9  deb http://ca.archive.ubuntu.com/ubuntu precise-updates main restricted
    10  #deb-src http://ca.archive.ubuntu.com/ubuntu precise-updates main restricted
    11
    12  deb http://ca.archive.ubuntu.com/ubuntu precise-security main restricted
    13  #deb-src http://ca.archive.ubuntu.com/ubuntu precise-security main restricted
    14  deb http://ca.archive.ubuntu.com/ubuntu precise-security universe
    15  #deb-src http://ca.archive.ubuntu.com/ubuntu precise-security universe
    16  #deb http://ca.archive.ubuntu.com/ubuntu precise-security multiverse
    17  #deb-src http://ca.archive.ubuntu.com/ubuntu precise-security multiverse

```

```
t# tail -v -n +1 /etc/apt/sources.list.d/*
tail: cannot open `/etc/apt/sources.list.d/*' for reading: No such file or directory
```

---

### Post by Bashing-om on 2015-10-08
tra4d; K;

I do not recognize - means just that I do not know - :
> 
1  deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe #multiverse
     2  deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe #multiverse
     3  deb mirror://mirrors.ubuntu.com/mirrors.txt precise-backports main restricted universe #multiverse
     4  deb mirror://mirrors.ubuntu.com/mirrors.txt precise-security main restricted universe #multiverse

As I do not know what purpose or HOW this mirror works for you; let's comment these fetchs out, and now what results:
```

sudo apt -get update
sudo apt-get upgrade

```
I do expect that the standard archive " ca.archive.ubuntu.com " will now be in effect. and that the process not only runs but completes.

[INDENT][INDENT]but hey, what do I know 
[/INDENT][/INDENT]

---

### Post by tra4d on 2015-10-09
Ok, commented out the mirrors section, same basic results (after 1.5 hours):
```
# apt-get update
Get:1 http://ca.archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://ca.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:3 http://ca.archive.ubuntu.com precise-security Release.gpg [198 B]
Get:4 http://ca.archive.ubuntu.com precise Release [49.6 kB]
Get:5 http://ca.archive.ubuntu.com precise-updates Release [196 kB]
Get:6 http://ca.archive.ubuntu.com precise-updates Release [196 kB]
Get:7 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:8 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:9 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:10 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:11 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:12 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:13 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:14 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:15 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:16 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:17 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:18 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:19 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:20 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:21 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:22 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:23 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:24 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:25 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:26 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:27 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:28 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:29 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:30 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:31 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:32 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:33 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:34 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:35 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:36 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:37 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:38 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:39 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:40 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:41 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:42 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:43 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:44 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:45 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:46 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:47 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:48 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:49 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:50 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:51 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:52 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:53 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:54 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:55 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:56 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:57 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:58 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:59 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:60 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:61 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:62 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:63 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:64 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:65 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:66 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:67 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:68 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:69 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:70 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:71 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:72 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:73 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:74 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:75 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:76 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:77 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:78 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:79 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:80 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:81 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:82 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:83 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:84 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:85 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:86 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
Get:87 http://ca.archive.ubuntu.com precise-security Release [54.3 kB]
82% [87 Release 196 B/54.3 kB 0%]
```

---

### Post by tra4d on 2015-10-09
Ok, next I tried using a specific mirror from a reputable place, same result (SEEMS TO BE ALWAYS STUCK ON 'precise-security Release' file.   ???
```
# apt-get update
Get:1 http://mirror.csclub.uwaterloo.ca precise Release.gpg [198 B]
Get:2 http://mirror.csclub.uwaterloo.ca precise-updates Release.gpg [198 B]
Get:3 http://mirror.csclub.uwaterloo.ca precise-security Release.gpg [198 B]
Get:4 http://mirror.csclub.uwaterloo.ca precise Release [49.6 kB]
Get:5 http://mirror.csclub.uwaterloo.ca precise-updates Release [196 kB]
Get:6 http://mirror.csclub.uwaterloo.ca precise-updates Release [196 kB]
Get:7 http://mirror.csclub.uwaterloo.ca precise-security Release [54.3 kB]
Get:8 http://mirror.csclub.uwaterloo.ca precise-security Release [54.3 kB]
Get:9 http://mirror.csclub.uwaterloo.ca precise-security Release [54.3 kB]
Get:10 http://mirror.csclub.uwaterloo.ca precise-security Release [54.3 kB]
Get:11 http://mirror.csclub.uwaterloo.ca precise-security Release [54.3 kB]
Get:12 http://mirror.csclub.uwaterloo.ca precise-security Release [54.3 kB]
Get:13 http://mirror.csclub.uwaterloo.ca precise-security Release [54.3 kB]
Get:14 http://mirror.csclub.uwaterloo.ca precise-security Release [54.3 kB]
82% [14 Release 540 B/54.3 kB 1%]
```

Next I tried a solution to find the best mirror via netselect [from this post]("https://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line/141536#141536"), same results, seems to be stuck on 'precise-security Release' file:
```
# apt-get update
Get:1 http://ubuntu.mirror.rafal.ca precise Release.gpg [198 B]
Get:2 http://ubuntu.mirror.rafal.ca precise-updates Release.gpg [198 B]
Get:3 http://ubuntu.mirror.rafal.ca precise-security Release.gpg [198 B]
Get:4 http://ubuntu.mirror.rafal.ca precise Release [49.6 kB]
Get:5 http://ubuntu.mirror.rafal.ca precise-updates Release [196 kB]
Get:6 http://ubuntu.mirror.rafal.ca precise-updates Release [196 kB]
Get:7 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:8 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:9 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:10 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:11 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:12 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:13 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:14 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:15 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:16 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:17 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:18 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
Get:19 http://ubuntu.mirror.rafal.ca precise-security Release [54.3 kB]
82% [19 Release 464 B/54.3 kB 1%]
```

---

### Post by tra4d on 2015-10-09
After letting the last one run (choosing the 'quickest' mirror from the list obtained via the netstat command) it did actually eventually finish!!!

After the apt-get upgrade, I am now at "Ubuntu 12.04.5 LTS" which is great.  Tried apt-get update again, and it went lightning fast (w/ the same mirror that did eventually/slowly finish).  Very strange.

---

### Post by Bashing-om on 2015-10-09
tra4d; Great !

Pleased that the situation is resolved.
Disappointed in that we can not point a finger at the exact causes(s). Networking ? System package install ? Conflicts ?
As the system is now happy will be difficult to triage . If one has the want to know bad enough, the past logs might give a hint on what was not taking place.

Not the 1st time I have encountered where the system healed it's self.

[INDENT][INDENT]one smart system
[/INDENT][/INDENT]

---

