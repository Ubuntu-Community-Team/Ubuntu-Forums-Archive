---
title: "Getting confused with two versions of R"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by akm3 on 2011-06-29
I used to run R 2.10 on Ubunutu 10.04, and tried to install R 2.11 from the source at the same time.
It seems that doing the second installation, I have messed up with some files or system paths, resulting in not being able to use either version of R on my system.

I get the following message in terminal, whenever I try to run R now:
```

/usr/local/bin/R: line 227: /usr/local/lib/R/etc/ldpaths: No such file or directory
/usr/local/bin/R: line 250: /usr/local/lib/R/bin/exec/R: No such file or directory
/usr/local/bin/R: line 250: exec: /usr/local/lib/R/bin/exec/R: cannot execute: No such file or directory

```

I've tried to re-install R using apt-get doing:

```

sudo apt-get update
sudo apt-get remove r-base 
sudo apt-get autoremove 
sudo apt-get install r-base 

```

Although the installation seems to be successful, I get the same error above trying to run R.
Any suggestions how I can clean up all the leftovers from the previous two installations, and get back to the r-base available in repository?

---

