---
title: "synaptic is broken - E: Dynamic MMap ran out of room."
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by davethewave83 on 2012-01-07
I tried to add the repositories for debian so that I could install basiliskii, but I'm not really sure how to do that, so I think I broke synaptic. 

now, synaptic won't run for very long. It comes up but pops up an error window

```
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing mbrola-hu1 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/http.us.debian.org_debian_dists_stable_non-free_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

```

how would I remove these repositories?

---

### Post by hansdown on 2012-01-07
Hi, davethewave83.

You could also increase your apt cache limit.

This should help.

[http://aziest.wordpress.com/2011/01/24/how-to-increase-your-apt-cache-limit/](http://aziest.wordpress.com/2011/01/24/how-to-increase-your-apt-cache-limit/)

---

### Post by davethewave83 on 2012-01-07
> **hansdown said:**
> Hi, davethewave83.

You could also increase your apt cache limit.

This should help.

[http://aziest.wordpress.com/2011/01/24/how-to-increase-your-apt-cache-limit/](http://aziest.wordpress.com/2011/01/24/how-to-increase-your-apt-cache-limit/)

the instructions add a . to the end of the file name. so it didn't work at first, I removed the . in the file name and now it does. Thanks!

there's still no basiliskii available for download though, I can't figure it out.

---

### Post by hansdown on 2012-01-07
> **davethewave83 said:**
> the instructions add a . to the end of the file name. so it didn't work at first, I removed the . in the file name and now it does. Thanks!

there's still no basiliskii available for download though, I can't figure it out.

You "may" need to go here.

[http://linux.softpedia.com/get/System/Emulators/Basilisk-II-11915.shtml](http://linux.softpedia.com/get/System/Emulators/Basilisk-II-11915.shtml)

---

### Post by davethewave83 on 2012-01-22
> **hansdown said:**
> You "may" need to go here.

[http://linux.softpedia.com/get/System/Emulators/Basilisk-II-11915.shtml](http://linux.softpedia.com/get/System/Emulators/Basilisk-II-11915.shtml)

just going through my old posts and realized I never said thanks, or marked as solved. So thanks! Softpedia was the answer, and also I think it was a bad idea to add the debian repositories as, when I did a system upgrade, it broke my ubuntu and I had to re-install :D 

live and learn.

---

### Post by hansdown on 2012-01-22
Haha!

Glad you fixed it, davethewave83.

Upgrades can be a birch,

---

