---
title: "Why do I have to install ubuntu-desktop on a Server?"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by chubbard on 2006-06-22
> Make sure that you have ubuntu-desktop, kubuntu-desktop, or edubuntu-desktop installed (depending on which distribution you are using). This is VITAL for apt to perform the upgrade successfully.

Under the "Upgrading by changing sources and the command line" instructions the first step is the text above.  I installed ubuntu on a server so I didn't put XWindows on it to save some space.  Why do I now have to put one of these on there to upgrade to Dapper?

I really just want to install a new package from dapper drake.  Could I use the Breezy Backports package to install it on my Breezy installation?

Thanks in advance
Charlie

---

### Post by mips on 2006-06-22
I honestly don't see how you would need a desktop for apt-get to work correctly.

---

### Post by rcarring on 2006-06-22
You can do it all from the command line.

Change your sources.list by commenting out the Breezy bits, add the Dapper bits and then do:

```

sudo apt-get update
sudo apt-get install --name of package ---

```

If the package requires Xorg then you will probably need to install at least xserver-xorg with dependencies satisfied.

---

### Post by aysiu on 2006-06-22
Forget those instructions--they're targeted specifically at desktop (not server) users.

Just change your sources.list and do the ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

