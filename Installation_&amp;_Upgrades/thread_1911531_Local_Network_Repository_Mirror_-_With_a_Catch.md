---
title: "Local Network Repository Mirror - With a Catch"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by ryannathans on 2012-01-19
Not sure what to search for as all previous searches don't help much.

Basically I have 5 ubuntu machines on my local network. When there is an update, I must download the update manually and seperately on each one.

Is there a way that I can have these 5 machines download the packages from my server.

I don't want to download the whole repository and host that locally.

When I need a package the clients should ask my server for it, if the server doesn't have it - it should be fetched from the internet and then cached ON THE SERVER for use on the remaining 4 machines.

I can't work out the best way to do this, nor can I find a similar/realistic alturnative.

Anyone got any ideas?

-Much Appreciated
ryannathans

---

### Post by ryannathans on 2012-01-20
bumpity

---

### Post by cortman on 2012-01-20
Hm... Very interesting question!

My guess is you'd need to write a small script that would run apt-get upgrade -d >> upgrades.list. The cp the list to the server and have a script on the server add wget commands to the package script.
I think it could be done but it'd take a little bash wizardry.

---

### Post by maminyana on 2012-02-20
> **ryannathans said:**
> 

I don't want to download the whole repository and host that locally.




You could:
1- download updates in one machine, 
2- Copy the whole dir: /etc/cache/apt/archives/* to the other machines. 
3- run "apt-get update"

In order to do this, just share /etc/cache/apt/archives/ via NFS or samba, and write a simple script.


Another alternative is to use aptOnCD.

---

### Post by Cheesehead on 2012-02-20
The apt-cacher-ng package is designed for this use case.

---

### Post by ryannathans on 2012-02-20
> **Cheesehead said:**
> The apt-cacher-ng package is designed for this use case.

I ended up with the apt-cacher.

First request  Fri Jan 20 23:55:06 2012 
Last request  Sun Feb 19 11:14:15 2012 
Total requests  6203 
Total traffic  3.17 GB 
Transfers 1826.505 MB (56.25%) (Cache hit) 1420.164 MB (43.74%) (Cache Miss)

---

