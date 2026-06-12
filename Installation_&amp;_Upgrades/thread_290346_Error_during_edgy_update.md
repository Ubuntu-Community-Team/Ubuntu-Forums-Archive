---
title: "Error during edgy update"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by themijs on 2006-11-01
Hi,

It seems there are lots of problems whit updating to edgy. (sorry for my english)
I have also a problem whit upgrading.
So I searched on the forum for a solution but none of them works.

This is my problem during the upgrade.
```
themijs@TheMijs:~$ gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpGp_Q8-/edgy.tar.gz'
authenticate '/tmp/tmpGp_Q8-/edgy.tar.gz' against '/tmp/tmpGp_Q8-/edgy.tar.gz.gpg'

```

And I get a "pop-up" whit this text in

Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg) Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg) Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.23 80]
Failed to fetch...

What can be the problem?
My network works fine.
And how to solve it?


Thanks

---

### Post by themijs on 2006-11-01
Any ideas?

---

### Post by newagelink on 2006-11-20
[I got a similar error message]("http://ubuntuforums.org/showpost.php?p=1785256&postcount=96"). I'm gonna read threads and try to solve my problem. If I (a newbie) figure anything out, and it seems related to your problem, I'll post it ...

---

