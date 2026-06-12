---
title: "apt-get corrupts partial downloads frequently"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by ca261 on 2011-06-04
Hi, I'm using 10.04.2, and I find that whenever I'm trying update (whether using synaptic, or command-line apt-get), the package download starts off fine, but after downloading a few files (usually only 4 or 5), the next partial (ongoing) downloads become corrupt, all the remaining downloads stay in the partial folder and finally apt-get gives a size mismatch error :confused:.

I'm forced to watch the update progress the entire time and wait for the downloads to corrupt (at this point the progress bar stops at say, "Downloading file 4 of 70" but the details show subsequent files *are* being downloaded). I then abort the update process and clean the /var/cache/apt/archives/partial folder (NOT the archives folder, or **all** the packages will have to be downloaded again). Then I restart the update and it picks up after the last successfully downloaded .deb.

Effectively, every such iteration downloads 3-5 .deb files successfully, and corrupts the remaining. Needless to say, if I'm upgrading 50 packages, it gets really frustrating.

I faced this problem even on new installations on my system as well as a friend's. Lucid, Maverik, Natty all have the same problem. By new installations, I mean on the very first boot, I setup the network (I'm behind a proxy server in a university) and that's it. I tried Linux Mint and it had the same problem.

---

### Post by ca261 on 2011-06-04
I forgot to mention, I've been using Ubuntu here for the past 4 years but never faced this problem until recently. Also, not all Ubuntu users in my college seem to encounter this problem.

---

### Post by mörgæs on 2011-06-04
It could be a problem on serverside. Have you tried changing mirror?

---

### Post by ca261 on 2011-06-04
> It could be a problem on serverside. Have you tried changing mirror?

Yup, I'm in India and I've tried the main server, all servers in India, and a couple of others too. Same error.

---

### Post by mörgæs on 2011-06-05
You could try to  boot the computer and run 

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Please post the error messages, if any.

---

### Post by ca261 on 2011-06-05
Well, since I went through the tedious 'workaround' I described previously, my system is finally up-to-date. But to show you the problem, I tried installing g++, gcj and gij (any install/upgrade requiring download of more than 5 or 6 files would face this problem).

I ran

```
sudo apt-get clean
sudo apt-get update
```

These worked. Then

```
sudo apt-get install g++ gcj gij
```

I've attached the output I got. Also, here's the listing of my apt cache.

```
chaitanya@Castle:~$ ls -lh /var/cache/apt/archives/partial/
total 13M
-rw-r--r-- 1 root root 1.6K 2010-03-19 23:35 ecj_3.5.1-1_amd64.deb
-rw-r--r-- 1 root root 1.1K 2010-03-19 23:35 ecj-gcj_3.5.1-1_amd64.deb
-rw-r--r-- 1 root root  89K 2010-06-21 23:36 g++_4%3a4.4.3-1ubuntu1_amd64.deb
-rw-r--r-- 1 root root 751K 2011-03-15 04:34 g++-4.4_4.4.3-4ubuntu5_amd64.deb
-rw-r--r-- 1 root root 6.3K 2010-03-19 23:35 gcj-4.4-jre_4.4.3-1ubuntu4.1_amd64.deb
-rw-r--r-- 1 root root 5.5M 2010-03-27 06:34 gcj-4.4-jre-headless_4.4.3-1ubuntu4.1_amd64.deb
-rw-r--r-- 1 root root 1.5K 2010-03-19 23:35 gcj-4.4-jre-lib_4.4.3-1ubuntu4.1_all.deb
-rw-r--r-- 1 root root  906 2010-03-19 23:35 gcj-jre_4%3a4.4.3-1ubuntu1_amd64.deb
-rw-r--r-- 1 root root 421K 2010-03-19 23:35 gcj-jre-headless_4%3a4.4.3-1ubuntu1_amd64.deb
-rw-r--r-- 1 root root 1.1K 2011-03-15 04:34 libecj-java-gcj_3.5.1-1_amd64.deb
-rw-r--r-- 1 root root 1.5M 2010-03-27 06:34 libgcj10_4.4.3-1ubuntu4.1_amd64.deb
-rw-r--r-- 1 root root 4.0M 2011-03-15 04:34 libgcj10-awt_4.4.3-1ubuntu4.1_amd64.deb
-rw-r--r-- 1 root root  80K 2011-03-15 04:34 libgcj-bc_4.4.3-4ubuntu1_amd64.deb
-rw-r--r-- 1 root root 164K 2009-11-09 21:34 libstdc++6-4.4-dev_4.4.3-4ubuntu5_amd64.deb
-rw-r--r-- 1 root root 1.1K 2010-03-19 23:35 zlib1g-dev_1%3a1.2.3.3.dfsg-15ubuntu1_amd64.deb
chaitanya@Castle:~$ ls -lh /var/cache/apt/archives/
total 6.7M
-rw-r--r-- 1 root root  89K 2010-06-21 23:36 fastjar_2%3a0.98-1ubuntu0.10.04.1_amd64.deb
-rw-r--r-- 1 root root  906 2010-03-19 23:35 gcj_4%3a4.4.3-1ubuntu1_amd64.deb
-rw-r--r-- 1 root root 107K 2011-03-15 04:34 gcj-4.4-base_4.4.3-1ubuntu4.1_amd64.deb
-rw-r--r-- 1 root root 4.0M 2011-03-15 04:34 gcj-4.4-jdk_4.4.3-1ubuntu4.1_amd64.deb
-rw-r--r-- 1 root root 6.3K 2010-03-19 23:35 gcj-jdk_4%3a4.4.3-1ubuntu1_amd64.deb
-rw-r--r-- 1 root root 1.1K 2010-03-19 23:35 gij_4%3a4.4.3-1ubuntu1_amd64.deb
-rw-r--r-- 1 root root 421K 2010-03-19 23:35 libantlr-java_2.7.7-15ubuntu1_all.deb
-rw-r--r-- 1 root root 1.2M 2009-11-24 04:34 libecj-java_3.5.1-1_all.deb
-rw-r--r-- 1 root root 751K 2011-03-15 04:34 libgcj10-dev_4.4.3-1ubuntu4.1_amd64.deb
-rw-r--r-- 1 root root 119K 2010-03-19 23:35 libgcj-common_1%3a4.4.3-1ubuntu1_all.deb
-rw-r----- 1 root root    0 2011-02-11 18:37 lock
drwxr-xr-x 2 root root  12K 2011-06-05 17:11 partial
chaitanya@Castle:~$ 
```

Like I said, the partial folder contains corrupt files. Now if I clean the partial folder (but not the archives folder), then I can try again. A few more files will be downloaded successfully and a size mismatch for the rest. Then clean, try again till I get a size mismatch. Then clean.....

Could this be a problem in my network itself? I mean, I was using 10.10 and it worked fine until maybe 1 or 2 months ago. Only now I face this peculiar problem. Do I need to contact my network administrator?

PS: I downloaded Debian 6 64bit live DVD. Booted it from a USB drive, set only the proxy server address (and no other setting), then tried to update. Same problem ](*,)

---

