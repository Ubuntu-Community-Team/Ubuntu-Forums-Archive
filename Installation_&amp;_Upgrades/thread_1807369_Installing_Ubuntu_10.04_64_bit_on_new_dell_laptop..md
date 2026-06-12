---
title: "Installing Ubuntu 10.04 64 bit on new dell laptop."
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by bearly230 on 2011-07-19
I just purchased a new Dell Inspiron n7110 and am trying to install ubuntu 10.04 lts on it.

The issue I have is, it doesn't detect my internal nic or my wireless. 

Here is the link to my specific laptop.

[http://www.bestbuy.com/site/Dell+-+Inspiron+Laptop+/+Intel%26%23174%3B+Core%26%23153%3B+i5+Processor+/+17.3%22+Display+/+8GB+Memory+/+750GB+Hard+Drive+-+Diamond+Black/2629094.p?id=1218340950203&skuId=2629094](http://www.bestbuy.com/site/Dell+-+Inspiron+Laptop+/+Intel%26%23174%3B+Core%26%23153%3B+i5+Processor+/+17.3%22+Display+/+8GB+Memory+/+750GB+Hard+Drive+-+Diamond+Black/2629094.p?id=1218340950203&skuId=2629094)

Any suggestions would be greatly appreciated.

---

### Post by pjd99 on 2011-07-19
I assume it comes with the [B]Intel® Centrino® Wireless-N 1030.
[/B]It won't be easy to get this card working in the current LTS version. It requires kernel version 2.6.36, and 10.04 was shipped with 2.6.32.
10.10 uses 2.6.35, so no luck there either.

Unfortunately, you'll need Natty or newer for support out-of-the-box.

I'd guess the same applies for the wired ethernet. Dell have used Realtek chips for a while. Might need newer kernel for that as well.

What is the output of the following two commands:
```

lspci | grep Network
lspci | grep Ethernet

```Looks like there is a WiMax adapter in there too. Are you looking to have that working as well?

---

### Post by bearly230 on 2011-07-19
11.04 would be an option other than my brother 2270dw printer driver won't install.

Guess I'm going to have to look at another distro. 

Thanks.

---

### Post by pjd99 on 2011-07-19
I did find a blog about getting newer kernels installed in 10.04 via ppa:
[http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/](http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/)

Also, see these regarding the printer and 11.04:
[http://ubuntuforums.org/showthread.php?t=1745084](http://ubuntuforums.org/showthread.php?t=1745084)
[http://ubuntuforums.org/showthread.php?t=1678093](http://ubuntuforums.org/showthread.php?t=1678093)

---

### Post by bearly230 on 2011-07-19
I appreciate the feedback. 

The issue with the printer is it only has a 32 bit driver, under both 10.04 and 10.10 64bit it will install and work great. However under 11.04 I get messages about packages missing etc. I've gone through both of those threads and it didn't resolve the issue. So I was looking at going to a previous version.

---

### Post by pjd99 on 2011-07-19
If it's the libc dependency issue, there's a workaround here:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/701856/comments/20](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/701856/comments/20)

I remember similar issues when trying to get the Fuji-Xerox machine at work talking to 8.10. Had to compile fxlinuxprint from source, and some tweaking was required to get the driver compiled on the 64 bit machine.

---

### Post by bearly230 on 2011-07-19
Thanks I'll give that a try tomorrow and let you know how it went.

---

