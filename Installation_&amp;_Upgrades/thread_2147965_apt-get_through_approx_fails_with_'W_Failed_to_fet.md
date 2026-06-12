---
title: "apt-get through approx fails with 'W: Failed to fetch'"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by ecowan on 2013-05-23
I have a small network of five computers - three laptop clients and two tower servers - all running Ubuntu 12.04. I use approx to reduce network traffic and to speed updates. It's been great, but inconsistent. It will run for a few months, and then I start to get
 "W: Failed to fetch [http://localhost:9999/base/dists/precise/main/source/Sources](http://localhost:9999/base/dists/precise/main/source/Sources)  404  Not Found" 
sort of errors.

I've tried to recover by running approx-gc, by cleaning out the appox-cache on the approx server; by cleaning out /var/apt/lists on the clients and running apt-get clean and apt-get update. Sometimes this does the trick. But not this tme.
 
I had trouble getting my head around the proper coding for approx.conf and sources.list, but the attached versions did work until recently.

Any suggestions on how to get approx working smoothly and consistently?

Thanks. - Erny

---

### Post by josephmills on 2013-05-23
this might not be what you want to hear but have you ever thought about salt or chef or even better 
puppet 
[https://puppetlabs.com/](https://puppetlabs.com/)

I know nothing about approx I sure that you will get a better answer then this but I hope that this helps

---

