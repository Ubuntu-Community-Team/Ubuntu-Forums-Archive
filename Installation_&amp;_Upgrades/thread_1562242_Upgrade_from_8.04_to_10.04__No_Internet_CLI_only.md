---
title: "Upgrade from 8.04 to 10.04  No Internet CLI only"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by rpete on 2010-08-27
Hi, I have had few problems up until now with my Hardy Heron 8.04 system.  I was notified of the upgrade and decided to do it yesterday.  When it didn't work, I posted last night and today couldn't locate the post even searching my posts.  When I boot the computer I end up with this on the black screen: Ubuntu 10.04.1 LTS dell desktop tty1

I login with user and password and have this:

richard@dell_desktop:~$

Now what?  I have no Internet connection.  I noticed in some error messages during the upgrade that python is not working.  I can't even shut down the computer. I disconnect it from AC power and pull out the battery!  

I don't know any commands, really. 

Will it damage my files if I just reinstall 8.04 from a CD?  I am reluctant to do this because I am afraid all my files will not be available.  Better still if I can type in the appropriate commands to 1)get my Internet connection working again, and 2)return my screen to a graphical user interface where I can access system and administration, repository,etc. 

One message I got that may be relevant is: /usr/bin/dpkg returned on error code (1)

Richard

---

### Post by zvacet on 2010-08-29
> One message I got that may be relevant is: /usr/bin/dpkg returned on error code (1)

Try with 

```
sudo dpkg --configure -a
```

---

### Post by zvacet on 2010-08-30
When you login in tty you can also try 

```
startx
```

to back in graphic environment.

---

