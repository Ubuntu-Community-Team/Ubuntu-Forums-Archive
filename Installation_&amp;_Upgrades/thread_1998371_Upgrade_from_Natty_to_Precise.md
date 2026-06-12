---
title: "Upgrade from Natty to Precise"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by andyho on 2012-06-06
Hi y'all...
           I've been reading conflicting info on upgrading so I thought I'd get your opinions real quick. I honestly haven't added too much into my current version 11.04, so I wouldn't be heartbroken to have to start from scratch. I am installing it as a dual boot with Windows 7, so just thought I would see if it makes more sense to maybe try and upgrade it from the manager and see if all goes well and if not then start from scratch, or just start from scratch in the first place?! Thanks for letting me know!!!

Andy

---

### Post by dromichaetes on 2012-06-06
well, I just did the upgrade from the manager and the graphics are messed up. Now I'm looking into a solution myself to fix. I can't do anything really. The good news is that my Natty was configured to boot into console mode, only after I start from the cs the lightdm service I get the problem, so maybe there's a fix to it somehow. 
 
I was running the 11.04 on a Dell laptop with nvidia graphics card. Just to let you know.

---

### Post by Enigmapond on 2012-06-06
You will probably save your sanity and medical bills if you just do a fresh install. Just my opinion....

---

### Post by dromichaetes on 2012-06-06
well, I tried from chroot to run this:
 
```
apt-get autoclean
apt-get clean
apt-get update
```
 
but I get these errors:
 
```

W: Failed to fetch [http://mirrors.adnettelecom.ro/ubuntu/dists/precise/inRelease](http://mirrors.adnettelecom.ro/ubuntu/dists/precise/inRelease)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/inRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/inRelease)
W: Failed to fetch [http://mirrors.adnettelecom.ro/ubuntu/dists/precise-updates/inRelease](http://mirrors.adnettelecom.ro/ubuntu/dists/precise-updates/inRelease)
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/inRelease](http://archive.canonical.com/ubuntu/dists/precise/inRelease)

```

---

### Post by dromichaetes on 2012-06-07
I thought it would be useful to let you know my status. I solved the problem by simply going into the grub menu and choosing the kernel on recovery mode. I then first enabled networking, since my problem appeared to be connectivity-related which made it impossible to access the repositories. 

After doing that I simply run dkpg. It made everything run again, my Precise is spotless now.

---

