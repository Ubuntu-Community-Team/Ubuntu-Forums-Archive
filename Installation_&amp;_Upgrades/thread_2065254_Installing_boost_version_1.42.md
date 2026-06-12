---
title: "Installing boost version 1.42"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by alex2356 on 2012-10-01
Hi, 

I am running ubuntu 12.04.1 LTS and need to 'downgrade' my installed version of boost to version 1.42 (1.48 currently installed). How can I do that? 

  aptitude search libboost

shows me only versions 1.46 and 1.48, so how exactly do I remove version 1.48 in order to revert to version 1.42. 

Please no questions about the why, I only require answers to my specific question. 


Thanks, 

  Alex

---

### Post by alex2356 on 2012-10-02
Hi again, 

since I have not received an answer to my question, I would like to ask if this is really a very hard to solve question? Maybe what I am asking is impossible? Any ideas I can try to install a specific version of boost?


Thanks,
  Alex

---

### Post by spjackson on 2012-10-02
Here's what I would do.

First investigate whether debs from earlier Ubuntu versions (Maverick) can be installed. i.e. remove the current package, download the debs and try installing them. 1.42 is less than 3 years old, so I think this might have a chance. However, my concern would be dependency on older versions of the standard library.

So if that failed, I would build it myself. I have built Boost before, but not for a long time; it can be a pain because of its own build system. So I would probably first try downloading the source package for 1.42 from the relevant Ubuntu version.
[https://launchpad.net/ubuntu/+source/boost-defaults/1.42.0.1ubuntu1]("https://launchpad.net/ubuntu/+source/boost-defaults/1.42.0.1ubuntu1")

As a last resort, download from boost.org and build it - painfully!

I'm not claiming the above is the best strategy, but it is what I would do. I hope this helps.

---

