---
title: "python3 problem upgrading 20.04 -&gt; 20.10"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by sremick on 2020-10-22
So I'm trying to upgrade Xubuntu from 20.04 to 20.10, but I get stopped at the beginning with:

```
Checking for a new Ubuntu releaseGet:1 Upgrade tool signature [819 B]                                                                                                                                                     
Get:2 Upgrade tool [1,338 kB]                                                                                                                                                            
Fetched 1,339 kB in 0s (0 B/s)                                                                                                                                                           
authenticate 'groovy.tar.gz' against 'groovy.tar.gz.gpg' 
extracting 'groovy.tar.gz'


Reading cache


Checking package manager


Can not upgrade 


Your python3 install is corrupted. Please fix the '/usr/bin/python3' 
symlink. 

```

I did some searching and saw that this can be caused by not having python3 point to the version of python your release originally came from. But mine does (just about). 
```
$ /usr/bin/python3 --version
Python 3.8.5

```

Granted it's 3.8.5 and not 3.8.2, but does that little difference matter? Do I actually have to downgrade?

I am using update-alternatives, but 3.8.5 is the only 3.8 installed.

```
$ ls -l /usr/bin/python3
lrwxrwxrwx 1 root root 25 Jun  3 21:21 /usr/bin/python3 -> /etc/alternatives/python3


$ sudo update-alternatives --config python3
There is only one alternative in link group python3 (providing /usr/bin/python3): /usr/bin/python3.8
Nothing to configure.

```


Please advise... thanks!

---

### Post by sremick on 2020-11-01
This can be closed.


 It turns out the problem was not that I had python 3.8.5 instead of  3.8.2. Instead, it was the symbolic linking that update-alternatives  does to /usr/bin/python3. Removing the chained symbolic links and  linking directly to /usr/bin/python3.8 like it would be without  update-alternatives resolved the 20.10 upgrade problem, even though  python was still 3.8.5 and ultimately still referring to the same  binary.


 I didn't have to change python versions and am now on Xubuntu 20.10.

---

