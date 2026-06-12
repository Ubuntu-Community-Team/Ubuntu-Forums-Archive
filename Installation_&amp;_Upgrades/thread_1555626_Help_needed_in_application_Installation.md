---
title: "Help needed in application Installation"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by sushant_ceb on 2010-08-18
Hi, i am a newbie of Ubuntu, and using Ubuntu 10.04 LTS. I have installed this Ubuntu in virtual-box running in windows xp.

my INTERNET connection is working fine but i m using proxy for that.

my problem is that when i want to install something through sudo apt-get install xxxx(whatever)
it gives error "Couldn't find package".

Example:
#sudo apt-get install wine

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine

---

### Post by lukeiamyourfather on 2010-08-18
Are you able to access the internet from the guest?

```
ping www.ubuntuforums.org
```

Are you able to update the package lists?

```
sudo apt-get update
```

---

### Post by sushant_ceb on 2010-08-19
No I am not able to  update the package lists and PING is also not working 

But My Internet connection working , I am able to browse Internet.

sudo apt-get update also show error 

root@sushant-desktop:/home/sushant# apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update

What's going wrong i can't understand ??????????????????

---

### Post by daksai3 on 2010-08-19
maybe the proxy is interfering. disable proxy and try again. srry i havent even touched ubuntu yet, but yea, sometimes the biggest problems have the simplest solutions.

---

### Post by sushant_ceb on 2010-08-19
If i will disable the proxy then how could  i connect to internet.

I am running linux in virtualbox.

---

### Post by daksai3 on 2010-08-19
u need a proxy to access the internet?

---

### Post by sushant_ceb on 2010-08-19
In browser setting i have to add proxy then only i can access Internet.

---

### Post by daksai3 on 2010-08-19
either way, first thing you have to do is try to isolate the problem. from what u are describing, im assuming that u will still be able to access the internet, just that someone else will also be able to use it at the same time. but just try it for a few mins and then apply the proxy again, just to see if that may be the problem. if it is try experimenting with diff proxies.

srry, im a bigger noob than u, but whatever.

---

### Post by sushant_ceb on 2010-08-19
I removed proxy, my internet is working now but problem still remain same..

now what to do???

---

### Post by daksai3 on 2010-08-19
i dont know sh** but try [http://ubuntuforums.org/showthread.php?t=179](http://ubuntuforums.org/showthread.php?t=179)

seems as if someone had similar problems.

---

