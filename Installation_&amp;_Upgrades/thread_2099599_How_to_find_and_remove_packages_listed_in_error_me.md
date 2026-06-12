---
title: "How to find and remove packages listed in error message"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by manorfreeman on 2012-12-29
Hey all, first post :)

When I  was brand new to Ubuntu, I downloaded some packages using the APT before fully understanding it. I'm not 100% sure what I did back then, but these packages are causing errors with the 'Software Updater' such that it simply displays an error message, and then closes (however, I am able to update my software using the command line). 

The error message I get from the software updater is: 

Failed to Download Repository Information:
W:Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Anyone have an idea how I can locate and delete the packages listed above that are causing me problems?

Thanks for taking the time to reading this!

Manor Freeman

---

### Post by stinkeye on 2012-12-29
The first three are for an old ppa distributing sun java which no longer applies.
Just remove the ppa entries for **ferramroberto** in software sources > other software.
Run update manager or **sudo apt-get update** and see if that also fixes your last error.

---

### Post by manorfreeman on 2012-12-29
Thank you! You saved me a lot of time and confusion

---

