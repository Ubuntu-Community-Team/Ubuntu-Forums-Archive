---
title: "Upgrade fails to 7.04"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by dcostelloe on 2007-04-26
:guitar: 

I keep getting the following errors when I try to upgrade to 7.04

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)


Thanks

---

### Post by skwishybug on 2007-04-26
I was having the same problem, this worked for me:

Go to: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) and generate a new default for your source list

Once it has been generated, type in: 
```
gksu gedit /etc/apt/source.list
```Replace the source list with the one generated above (copy and paste)

Save the file and run: 
```
gksu "update-manager -c"
```Hope it works for you too.

---

### Post by zvacet on 2007-04-27
You dont need to run any commands if your Edgy is up-to-date.If it is update manager will tell you that you can upgrade to the new version.If you didn´t change your source list just comment (put # sign in front of line) that two lines.When you are finish with upgrade change your source list from Edgy to Feisty
```
  sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

After that uncomment two lines that gives you trouble and 

```
sudo aptitude update && sudo aptitude upgrade
```

---

