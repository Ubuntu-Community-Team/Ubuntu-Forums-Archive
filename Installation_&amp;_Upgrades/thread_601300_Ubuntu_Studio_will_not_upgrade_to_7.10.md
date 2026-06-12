---
title: "Ubuntu Studio will not upgrade to 7.10"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by mark_lar on 2007-11-03
Hello.

I have Ubuntu Studio 7.04 installed, so I go to the package manager, click the distribution update button and it starts? Except, it doesn't. It gets some files, then shows an error about packages not being found on the server. Any ideas?

Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg) Could not resolve &#8216;archive.ubuntustudio.org&#8217;
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_GB.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_GB.bz2) Could not resolve &#8216;archive.ubuntustudio.org&#8217;
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_GB.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_GB.bz2) Could not resolve &#8216;archive.ubuntustudio.org&#8217;
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz) Could not resolve &#8216;archive.ubuntustudio.org&#8217;
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz) Could not resolve &#8216;archive.ubuntustudio.org&#8217;


Mark

---

### Post by gerlach1025 on 2007-11-04
I'm having the same issue. According to this link the repos are closed.[http://ubuntuforums.org/showthread.php?t=592639]("http://ubuntuforums.org/showthread.php?t=592639") Does anyone know if disabling the 3rd party repo will mess up the upgrade to Gutsy? Maybe it would just be better to download the ISO and install from scratch? :confused:

---

### Post by gerlach1025 on 2007-11-05
I took out the reference to Ubuntu Studio in the 3rd party repositories and ran the distro upgrade using update manager. After doing this I was able to correctly upgrade to Gutsy. :)

---

### Post by chamel2xl2 on 2007-11-10
I had the exact same problem. And gerlach1025's suggestion also worked for me!

The only thing, I didn't know how to "take out the reference to Ubuntu Studio in the 3rd party repositories". Since I then figured out, I just tought I would post the way to do so here.

System -> Administration -> Software Sources
Third-Party Software Tab
Uncheck the box next to [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio)

The next time you run the Package Upgrader and then the Distribution Upgrade, it should work with no problem!

---

### Post by mark_lar on 2007-11-10
And then you re-enable it when you have updated?

---

### Post by mattymattysidebyeach on 2007-11-27
LOL - my question exactly!

however, since the packages from ubuntustudio are already installed, one might assume theyd be upgraded from being available in the regular repositories...

...i.e. ubuntustudio is more a "distribution list" of  items than it is a set of specific versions of packages.

am i on the right track here?

:confused:

---

### Post by Drunky on 2007-11-28
Someone please correct me if I am wrong but, I believe that UbuntuStudio.org used to maintain it's own repositories up to Feisty.

Since the release of Gutsy the Ubuntu Studio packages have been moved into the main repositories.  Therefore, you there should be no need to re-enable UbuntuStudio.org repositories.

---

### Post by Endolith on 2007-12-26
> **Drunky said:**
> Someone please correct me if I am wrong but, I believe that UbuntuStudio.org used to maintain it's own repositories up to Feisty.

Since the release of Gutsy the Ubuntu Studio packages have been moved into the main repositories.  Therefore, you there should be no need to re-enable UbuntuStudio.org repositories.

I was going to ask you for evidence, but here is the evidence itself: [http://ubuntuforums.org/showthread.php?t=592639](http://ubuntuforums.org/showthread.php?t=592639)

---

### Post by Knightsky on 2008-01-20
So, I had this same problem I think...but I've already attempted the install, and it partially installed. My install attempts will halt at either the libxdmcp6 configuration, or at the linux kernel install (83% on the progress bar.) Is there a way to save my installation attempt without having to completely reformat?

---

### Post by uncreative on 2008-01-29
Thanks, this has been a point of frustration for me and a few of my users on [www.cyqo.com](www.cyqo.com) who I suggest this OS to.

I finally broke down and started reading today on how to fix it.

Works perfectly!

---

