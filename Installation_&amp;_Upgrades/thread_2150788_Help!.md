---
title: "Help!"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by MiamiHF on 2013-06-02
im trying to install TOR and Spotify but when i do apt-get update i get this error 

```

linux@ubuntu:~$ apt-get update
E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
linux@ubuntu:~$ apt-get install deb.torproject.org-keyring
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
linux@ubuntu:~$ 


```

can anyone help me ?

---

### Post by Cheesemill on 2013-06-02
You need to run the commands with root privileges. Try running...
```
sudo apt-get update
sudo apt-get install deb.torproject.org-keyring
```

If you still get an error about line 62 then can you run the following command and post the output here....
```
cat -n /etc/apt/sources.list
```

---

### Post by MiamiHF on 2013-06-02
i fixed the apt-get update on line 62 but now im having another problem the problem that im having now is this. i have all the sources there but there not downloading when i do apt-get update even with SUDO 

```
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise/InRelease  

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-updates/InRelease  

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-backports/InRelease  

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-security/InRelease  

W: Failed to fetch http://repository.spotify.com/dists/stable/InRelease  

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/precise/InRelease  Unable to find expected entry 'main/binary-powerpc/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise/Release.gpg  Could not resolve 'ports.ubuntu.com'

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-updates/Release.gpg  Could not resolve 'ports.ubuntu.com'

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-backports/Release.gpg  Could not resolve 'ports.ubuntu.com'

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-security/Release.gpg  Could not resolve 'ports.ubuntu.com'

W: Failed to fetch http://repository.spotify.com/dists/stable/Release.gpg  Could not resolve 'repository.spotify.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
linux@ubuntu:~$ ^C
linux@ubuntu:~$ sudo apt-get install deb.torproject.org-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package deb.torproject.org-keyring
E: Couldn't find any package by regex 'deb.torproject.org-keyring'
linux@ubuntu:~$ 
[B]W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise/InRelease  

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-updates/InRelease  

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-backports/InRelease  

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-security/InRelease  

W: Failed to fetch http://repository.spotify.com/dists/stable/InRelease  

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/precise/InRelease  Unable to find expected entry 'main/binary-powerpc/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise/Release.gpg  Could not resolve 'ports.ubuntu.com'

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-updates/Release.gpg  Could not resolve 'ports.ubuntu.com'

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-backports/Release.gpg  Could not resolve 'ports.ubuntu.com'

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/precise-security/Release.gpg  Could not resolve 'ports.ubuntu.com'

W: Failed to fetch http://repository.spotify.com/dists/stable/Release.gpg  Could not resolve 'repository.spotify.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
linux@ubuntu:~$ ^C
linux@ubuntu:~$ sudo apt-get install deb.torproject.org-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package deb.torproject.org-keyring
E: Couldn't find any package by regex 'deb.torproject.org-keyring'
linux@ubuntu:~$ 
[/B]

```

---

### Post by Cheesemill on 2013-06-02
Can you post the contents of your sources.list please...
```
cat -n /etc/apt/sources.list
```

---

### Post by MiamiHF on 2013-06-02
Here you go thanks for the help btw 

```
linux@ubuntu:~$ cat -n /etc/apt/sources.list
     1    # 
     2    
     3    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release powerpc (20120423.2)]/ precise main restricted
     4    
     5    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release powerpc (20120423.2)]/ precise main restricted
     6    
     7    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     8    # newer versions of the distribution.
     9    deb http://ports.ubuntu.com/ubuntu-ports/ precise main restricted
    10    deb-src http://archive.ubuntu.com/ubuntu precise main restricted
    11    
    12    ## Major bug fix updates produced after the final release of the
    13    ## distribution.
    14    deb http://ports.ubuntu.com/ubuntu-ports/ precise-updates main restricted
    15    deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    18    ## team. Also, please note that software in universe WILL NOT receive any
    19    ## review or updates from the Ubuntu security team.
    20    deb http://ports.ubuntu.com/ubuntu-ports/ precise universe
    21    deb-src http://archive.ubuntu.com/ubuntu precise universe
    22    deb http://ports.ubuntu.com/ubuntu-ports/ precise-updates universe
    23    deb-src http://archive.ubuntu.com/ubuntu precise-updates universe
    24    
    25    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    26    ## team, and may not be under a free licence. Please satisfy yourself as to 
    27    ## your rights to use the software. Also, please note that software in 
    28    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    29    ## security team.
    30    deb http://ports.ubuntu.com/ubuntu-ports/ precise multiverse
    31    deb-src http://archive.ubuntu.com/ubuntu precise multiverse
    32    deb http://ports.ubuntu.com/ubuntu-ports/ precise-updates multiverse
    33    deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse
    34    
    35    ## N.B. software from this repository may not have been tested as
    36    ## extensively as that contained in the main release, although it includes
    37    ## newer versions of some applications which may provide useful features.
    38    ## Also, please note that software in backports WILL NOT receive any review
    39    ## or updates from the Ubuntu security team.
    40    deb http://ports.ubuntu.com/ubuntu-ports/ precise-backports main restricted universe multiverse
    41    deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    42    
    43    deb http://ports.ubuntu.com/ubuntu-ports/ precise-security main restricted
    44    deb-src http://ports.ubuntu.com/ubuntu-ports/ precise-security main restricted
    45    deb http://ports.ubuntu.com/ubuntu-ports/ precise-security universe
    46    deb-src http://ports.ubuntu.com/ubuntu-ports/ precise-security universe
    47    deb http://ports.ubuntu.com/ubuntu-ports/ precise-security multiverse
    48    deb-src http://ports.ubuntu.com/ubuntu-ports/ precise-security multiverse
    49    
    50    ## Uncomment the following two lines to add software from Canonical's
    51    ## 'partner' repository.
    52    ## This software is not part of Ubuntu, but is offered by Canonical and the
    53    ## respective vendors as a service to Ubuntu users.
    54    # deb http://archive.canonical.com/ubuntu precise partner
    55    # deb-src http://archive.canonical.com/ubuntu precise partner
    56    
    57    ## This software is not part of Ubuntu, but is offered by third-party
    58    ## developers who want to ship their latest software.
    59    deb http://extras.ubuntu.com/ubuntu precise main
    60    deb http://repository.spotify.com stable non-free
    61    deb-src http://repository.spotify.com stable non-free
    62    deb http://deb.torproject.org/torproject.org precise main
    63    deb-src http://deb.torproject.org/torproject.org precise main
    64    deb-src http://extras.ubuntu.com/ubuntu precise main
linux@ubuntu:~$ 


```

---

