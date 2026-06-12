---
title: "finding the url that apt-get/aptitude uses"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by cong06 on 2010-05-24
First background:
I'm on a very unstable connection. In many cases, it's much faster and more reliable to use wget to download the deb files that I need for upgrades/installations.

The advantage of wget over apt is probably mostly due to the apt-cacher proxy I'm behind. Apt-cacher isn't capable of continuing incomplete downloads yet, instead it just trashes them and I'm forced to start over.

Now the project.
I want to make a script that will allow me to select a package, wget them, and then import them to my apt-cacher cache. The second two parts are rather easy, and I have them already:

```

wget -c $url
# check to make sure it completed
if [ $? -eq 0 ]; then
    mv $file*.deb /var/cache/apt-cacher/import/; /usr/share/apt-cacher/apt-cacher-import.pl
fi

```

What I want is to be able to specify a package, and then get the apt-get/aptitude url that **they** would use to download.

The best I have is this:
```

url=`apt-cache show $file | grep -A 15 "^Maintainer: Ubuntu" | grep "^Filename: "| cut -d ' ' -f 2`

```
But this only works for the default repositories. (and then I have to add the prefix "http://ke.archive.ubuntu.com/ubuntu/")

Ideally (now that I think about it) I would be able to run a program like apt-get or aptitude that is built into all the /etc/apt/ configurations and just have it return the address that it *would* download.

---

### Post by dino99 on 2010-05-24
depend of which server is used to download updates

[https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)

---

### Post by cong06 on 2010-05-24
I guess you didn't understand.
I have multiple repositories:
launchpad
debian
archive.ubuntu.com
deb.google.com
etc.
I want to get the url from aptitude without aptitude actually downloading the package that I specify. Something like:

aptitude --simulate-download sun-java6-bin

It doesn't have to be aptitude...

---

### Post by cong06 on 2011-03-17
I switched to apt-cacher-ng.

---

### Post by pmorch on 2012-07-13
I was looking for the same thing, albeit for a different reason. Found [the answer]("http://linuxers.org/article/find-download-location-urlname-size-and-md5-sum-software-package-using-apt-get"). I've modified it a little to be:

```
# sudo apt-get install -qq --reinstall --print-uris bash | perl -lne "/'(.*?)'/;print \$1"
http://server/debian/pool/main/b/bash/bash_4.1-3_i386.deb
```

---

