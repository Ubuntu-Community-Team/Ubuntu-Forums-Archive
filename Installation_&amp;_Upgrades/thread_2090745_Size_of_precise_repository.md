---
title: "Size of precise repository"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by Xubun on 2012-12-03
Hi!!
I want to download the 12.04 repository to my HDD in order to have an offline Ubuntu repo. I checked at [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)
and the whole precise repository 
[IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG][precise-backports/]("http://archive.ubuntu.com/ubuntu/dists/precise-backports/")30-Nov-2012 05:55    -  [IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG][precise-proposed/]("http://archive.ubuntu.com/ubuntu/dists/precise-proposed/")03-Dec-2012 05:37    -  [IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG][precise-security/]("http://archive.ubuntu.com/ubuntu/dists/precise-security/")30-Nov-2012 05:55    -  [IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG][precise-updates/]("http://archive.ubuntu.com/ubuntu/dists/precise-updates/")30-Nov-2012 05:55    -  [IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG][precise/]("http://archive.ubuntu.com/ubuntu/dists/precise/")is only ~10 GB. Is this correct? A colleague told me that it should be around 50 GB ...
Is this the correct link?
Thanks

---

### Post by ibjsb4 on 2012-12-03
Hi Xubun, welcome to the forums  :)

Take a look here for starters.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=download+entire+complete+repository&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=download+entire+complete+repository&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/ubuntu-1210-software-repository-64bit-pc.html](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/ubuntu-1210-software-repository-64bit-pc.html)

---

### Post by Cheesemill on 2012-12-03
```
root@precise:~# cat /etc/apt/mirror.list 
############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu precise main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

#deb-src http://archive.ubuntu.com/ubuntu precise main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu precise-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

clean http://archive.ubuntu.com/ubuntu
root@precise:~# 
root@precise:~# apt-mirror 
Downloading 80 index files using 20 threads...
Begin time: Mon Dec  3 15:51:09 2012
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Mon Dec  3 15:51:29 2012

Proceed indexes: [PPPPP]

54.7 GiB will be downloaded into archive.
```
So it's 54.7 GiB just for the 64-bit repository without sources.

A good page describing how to set up a local repository:
[http://nwlinux.com/configure-an-ubuntu-repo-mirror/](http://nwlinux.com/configure-an-ubuntu-repo-mirror/)

---

### Post by Xubun on 2012-12-03
Thanks a lot!!!

---

