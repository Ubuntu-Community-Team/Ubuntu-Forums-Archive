---
title: "Authenticating PPA not working"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by neogarfield on 2010-02-13
EDIT : Its working now... It WAS a port being blocked. For others having the same problem, you need to open port 11371. Thank you for taking the time to check out this post though!

And others with similar problems, check out : [https://bugs.launchpad.net/ubuntu-website/+bug/435193](https://bugs.launchpad.net/ubuntu-website/+bug/435193)

Hey,
I'm not able to authenticate 3rd party PPAs using the sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys command. Somehow, it just keeps timing out. I tried searching for an solution to the problem, but I could not find a working result. I tried using alternate keyservers which were mentioned in some of the posts I could find... Still timing out. All the servers can't be down right, and not over such a long period - this has been happening for almost 4 weeks now, ever since I started using Ubuntu...

The only thing I can think of is if the command uses a different port than 80, because my organisation has blocked unused ports, with an option to open whichever port necessary by contacting the system admin. So if it uses a different port, I can open it up, but I will have to know which port...

Any insights?
(I'm a Linux newbie, so in simple language might be good :) )

---

