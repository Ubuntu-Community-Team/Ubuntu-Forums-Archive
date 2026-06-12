---
title: "help!!!! hard drive partioning"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by pyronaut on 2005-08-11
hello everyone,
   I used the automatic partioning tool while installation and so ended up with 10G on " / "  and about 20G's on " /home  ".  Now i'm stuck bcos I dont have enough pace to download all the applications i would like. Does anybody have a solution???
  Can I repartition without having to reinstall??? 
  or how do I go about downloading packages to /home and making them run as they normally would from /usr/bin or /usr/sbin   ](*,) 
   Any help will be greatly appreciated.
      cheers

---

### Post by varunus on 2005-08-11
10G isn't enough for your packages?  Wow, you must be installing a lot.  What are you trying to install?

You can use GPARTED to resize partitions, here's instructions on how to install it:
[http://www.ubuntuguide.org/#gparted](http://www.ubuntuguide.org/#gparted)

What do you mean you want to run packages you download to /home in /usr/bin?  Aren't you using synaptic to get your packages?

---

### Post by pyronaut on 2005-08-12
thanks, 
   I'll try to do that... Well i was trying to get both Kubuntu and gnome at the same time and try to get like a lot of the scientific applications going  :wink: .... Also   I was trying to get a lot of the programming packages in and it just didnt do it.....I know i have about 6G with the regular install and then when i tried to do all the downloads it went up by about 4-5G and didnt do the install  :oops: 
  But I'll definitely try Gparted thanks for the info. 
   yeah i am using synaptoc for the packages that are in the repos , but i need to install some packages that are not available in synaptic and then of course those can be done using make install.....well maybe i can try to change parameters during make to redirect them to /home/somewhere and make a link in /usr/bin ???

---

