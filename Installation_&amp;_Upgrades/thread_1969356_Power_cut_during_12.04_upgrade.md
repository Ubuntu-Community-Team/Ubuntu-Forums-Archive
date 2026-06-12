---
title: "Power cut during 12.04 upgrade"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by aschlosberg on 2012-04-30
I was upgrading to 12.04 when my power was cut. All new packages had been downloaded and about 50% had been installed.

I restarted and everything seems to be running OK. I ran the following to try and complete the upgrade:

```

dpkg --configure -a (apparently did nothing)
apt-get dist-upgrade (did nothing)
apt-get update (ran as expected for precise)
apt-get upgrade (installed 1 package only)
apt-get autoremove (removed a number of libraries)

```

I'm concerned that the upgrade hasn't completed properly. Is there anything that I should check / do?

---

### Post by josephmills on 2012-04-30
yeah you can make sure let us see some things 

```
cat /etc/apt/sources.list 
```
and 
```
dpkg-query -l 
```
and 
```
apt-cache policy dump linux-image*
```


paste here

---

### Post by aschlosberg on 2012-04-30
Thanks mate... attached

---

### Post by josephmills on 2012-04-30
you are looking real good but run 
```
sudo do-release-upgrade
```
just in-case

---

### Post by aschlosberg on 2012-04-30
Thanks, that's what I thought when I looked at them.

"No new release found"

What would have happened to the second half of the packages that hadn't installed yet?

---

