---
title: "Spotify repository error on update"
date: 2014-07-04
forum: Installation &amp; Upgrades
---

### Post by Thomas_Jrvstrand on 2014-07-04
Hi,

when running apt-get update I get the following error:
```

...
Fetched 29.2 MB in 8s (3,314 kB/s)                                             
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.

```

I've tried [this]("http://ubuntuforums.org/archive/index.php/t-863742.html"), but no luck.

Any tips? :)

T

---

### Post by Thomas_Jrvstrand on 2014-07-04
Nevermind I just realized I'm running Spotify in Wine and not even using the Linux preview anymore :)

---

### Post by miguel25 on 2014-07-04
How could you solve the problem? Did you have to remove spotify? I am having the same trouble and the advice in the link you posted (and many similar to that) is not working at all.

---

### Post by karsta62 on 2014-07-04
I did this:
sudo rm /var/lib/apt/lists/repository.spotify*
removed spotify repo from /etc/apt/sources.list

Now sudo apt-get update runs without errors.
spotify will not be updated anymore, but current version works.

---

### Post by Bucky Ball on 2014-07-04
Rather than remove it completely, it might have been better to simply comment out the spotify repo in /etc/apt/sources.list by placing a hash in front of it (#). That way, you can uncomment in a few days and see if it works. The spotify server may simply be down for maintenence. You can also do Software Updater>Settings>Other Software and untick the spotify repos for now. 

Unless there's been some official announcement that this particular repo is being closed, it is probably just down for whatever reason ...

---

### Post by karsta62 on 2014-07-04
You're right and that is what I actually did.

---

