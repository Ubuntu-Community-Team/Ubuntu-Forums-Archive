---
title: "Problem with updating my Ubuntu"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by Primus92 on 2010-06-27
Hi i have used my Ubuntu for long period but suddenly when i wanted to update there showed an error which said that Ubuntu could not download all repository index.

Under the problem was written this : 

Cant be found [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

Because of this i cannot update my Ubuntu so i would really like to update my Ubuntu. I am using Ubuntu 10.04 LTS - the Lucid Lynx. Please help me.

Bye

---

### Post by quixote on 2010-06-29
Every once in a while, the server for a repository goes down.  Assuming the server isn't really offline for good (which you could check by trying to go to that site or one of its parent pages using a browser) just try it again later.

---

### Post by tommcd on 2010-06-30
> **Primus92 said:**
> 
Cant be found [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

I get a 404 also when trying to go to that url also. I think the problem is that there is currently no Lucid repo on that ppa exaile repo:
[http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/)
The question is: Is the Lucid repo on that ppa repo gone for good, or is it just a temporary thing? 
To temporarily work around this, just comment out (put a # in front of) that repo in your */etc/apt/sources.list* file.
Then run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
to get the updates. This will skip the problematic ppa exaile repo.
You can also exclude that repo by going to: system > administration > software sources, and unchecking or removing that repo from your list. Then click the "reload" button when prompted.

You could always add that repo back (just remove the # in front of it in your /etc/apt/sources.list file; or add it again from the "software sources" menu) and try it again later if the Lucid repo reappears.
FYI: Those ppa repos can sometimes be problematic like this. Use them with caution! And use them sparingly. You will avoid problems like this.

And welcome to the Ubuntu forums!

---

