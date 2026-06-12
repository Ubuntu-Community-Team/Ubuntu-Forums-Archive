---
title: "Can I intall 12.04 compatible app in 19.10? If yes, how? Will snap help?"
date: 2019-12-13
forum: Installation &amp; Upgrades
---

### Post by ajparag2 on 2019-12-13
Hi,
I have an app rather a bash script which is only compatible with Ubuntu 12.04. I want to run that script in 19.10. It does not work out-of-the-box.
Here a brief background: I want to install vspace for linux which is compatible only with 12.04 LTS on Ubuntu 19.10 so that I can use the ncomputing L230 thin client hardware. Is it even possible? If yes, can anyone guide me with the process in detail? I will be grateful to you.

---

### Post by The Cog on 2019-12-13
Out of curiosity, I searched for vspace to see what it is. The top result ([https://www.ncomputing.com/products/vSpace/vSpace%20for%20Linux](https://www.ncomputing.com/products/vSpace/vSpace%20for%20Linux)) contains this line: 
> vSpace for Linux supports the popular Ubuntu Desktop (14.04 LTS, 16.04 LTS and 18.04 LTS).

Their web site doesn't actually say what their product is, what it does, so I looked on wikipedia which both told me what the product does, and repeated the support for the three latest LTS releases. You might have better luck with a more recent version of vspace.

---

### Post by ajparag2 on 2019-12-18
> **The Cog said:**
> Out of curiosity, I searched for vspace to see what it is. The top result ([https://www.ncomputing.com/products/vSpace/vSpace%20for%20Linux](https://www.ncomputing.com/products/vSpace/vSpace%20for%20Linux)) contains this line: 


Their web site doesn't actually say what their product is, what it does, so I looked on wikipedia which both told me what the product does, and repeated the support for the three latest LTS releases. You might have better luck with a more recent version of vspace.


Yes, vSpace is available for Ubuntu 14.04, 16.04 and 18.04 respectively. However, it does not support the hardware that I own i.e. ncomputing thin client L230. I need to install the version that is available for 12.04 in order to support my hardware.

---

### Post by ubfan1 on 2019-12-18
This commercial product, L230 was End of Support June 30 2015, and End of Life June 20 2018.  [https://www.ncomputing.com/support/lifecycle](https://www.ncomputing.com/support/lifecycle)      Maybe there's a user community that has figured out how to use these, or put a newer OS on them.  What errors does the bash script output?  I doubt bash is actually the problem, probably some driver.

---

### Post by gsahli on 2019-12-18
I think you should investigate the linux alternative to vSpace, LTSP, at:
[https://ltsp.org/](https://ltsp.org/)
and:
[https://linuxliaison.org/thin-clients-with-ltsp-on-ubuntu-server-16-04/](https://linuxliaison.org/thin-clients-with-ltsp-on-ubuntu-server-16-04/)

I haven't used this, but I think your thin client is supported.

---

### Post by Tadaen_Sylvermane on 2019-12-18
Wholeheartedly recommend LTSP. Using it at home, and it is a dream to work with. Never used vSpace so I can't comment on differences. As far as your client, if it can pxe boot and is i386 / amd64, it will work. May be ways to create a chroot with other architectures but that is out of my scope.

---

