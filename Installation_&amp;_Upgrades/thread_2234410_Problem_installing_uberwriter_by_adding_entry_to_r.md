---
title: "Problem installing uberwriter by adding entry to repo"
date: 2014-07-14
forum: Installation &amp; Upgrades
---

### Post by aryakaran on 2014-07-14
Hello,

Today I installed uberwriter in my linux mint desktop computer without problems by using:
```
sudo add-apt-repository ppa:w-vollprecht/ppa
sudo apt-get update
sudo apt-get install uberwriter 
```
as it is specified in the [website of the developer]("http://uberwriter.wolfvollprecht.de/").
Then I tried to install it in my lubuntu laptop with the same procedure, but I encounter a problem. When I run:
```
sudo apt-get update
```
I get the errors:

W: Failed to fetch [http://ppa.launchpad.net/w-vollprecht/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/w-vollprecht/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/w-vollprecht/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/w-vollprecht/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

I can't figure out what is the issue here, Thanks.

---

### Post by bapoumba on 2014-07-14
[https://launchpad.net/~w-vollprecht/+archive/ubuntu/ppa](https://launchpad.net/~w-vollprecht/+archive/ubuntu/ppa)
There are no packages for trusty..

---

### Post by aryakaran on 2014-07-14
Thanks bapoumba. And there is any alternative way to do it?

---

### Post by bapoumba on 2014-07-14
I have no idea, never heard of uberwriter before you mentioned it :)

[https://launchpad.net/uberwriter](https://launchpad.net/uberwriter) < looks like the development stopped in 2012.

[https://bugs.launchpad.net/uberwriter/+bug/1309634](https://bugs.launchpad.net/uberwriter/+bug/1309634) < may be here.

---

### Post by aryakaran on 2014-07-14
Thanks again bapoumba. On that link there is a trusty version of such an amazing editor.

---

### Post by bapoumba on 2014-07-14
Yep, if that solves you issues, please mark your thread as such (under thread tools), thanks :)

---

