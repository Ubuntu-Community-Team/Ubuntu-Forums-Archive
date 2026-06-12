---
title: "How to mix debian and ubuntu safely"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by voipfc on 2007-03-12
I am running Ubuntu 6.10 but I want to be able to get some packages from Debian as well.

How should I manage it without running into conflicts and other problems.

---

### Post by zvacet on 2007-03-13
> Mix Ubuntu and Debian
If you want to be able to install packages from either Debian or Ubuntu at will, you can make use of a package-management feature called pinning, which is designed to allow you to lock packages to specific versions while other packages are upgraded. 
Start by adding some basic Debian archive entries to /etc/apt/sources.list: 
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) sarge main non-free contrib 
deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) sarge/non-US main contrib non-free

If you don't have one already, create a file called /etc/apt/preferences and put in these entries: 
Package: * 
Pin: release a=dapper 
Pin-Priority: 700 
Package: * 
Pin: release a=sarge 
Pin-Priority: 600

What this does is give the packages in Dapper a higher priority than the packages in Sarge, so if you apt-get install foo a package, the system will try to install the Dapper version of a package if it's available and fall back to using Debian packages if necessary. In reality, the algorithm for determining package priority is rather more complex than a simple priority, and to fully understand it, you should read the apt_preferences manpage (man apt_preferences). 
Because apt in Ubuntu uses a new security infrastructure to check package signatures, you will also need to install the Debian archive key, or your system will complain every time it tries to install a package from the Debian archives. The Debian archive keys are replaced every year but are located at an address like http://ftp-master.debian.org/ziyi_key_<year>.asc, where <year> is the current year. Use wget to retrieve the current key, import it into your GPG keyring, and then check the fingerprint: 
$ wget [http://ftp-master.debian.org/ziyi_key_2006.asc](http://ftp-master.debian.org/ziyi_key_2006.asc) 
$ gpg --import ziyi_key_2006.asc 
gpg: key 2D230C5F: public key "Debian Archive Automatic Signing Key (2006) <ftpmaster@debian.org>" imported 
gpg: Total number processed: 1 
gpg:               imported: 1 
$ gpg --fingerprint 2D230C5F 
pub   1024D/2D230C5F 2006-01-03 [expires: 2007-02-07] 
      Key fingerprint = 0847 50FC 01A6 D388 A643  D869 0109 0831 2D23 0C5F 
uid          Debian Archive Automatic Signing Key (2006) <ftpmaster@debian.org>

If you want to be really careful, you can then use this fingerprint to prove the authenticity of the key via Debian's web of trust. 
Now install the key into apt so that it will trust packages signed by it: 
$ gpg --armor --export 2D230C5F | sudo apt-key add - 
            

You're now ready to install packages from either Ubuntu or Debian. Any packages you want to specifically pull from the Debian archive can be accessed by adding a -t (target release) flag to apt: 
$ sudo apt-get install -t sarge   myprogram
                 
I hope it helped.

---

### Post by Dr. Nick on 2007-03-13
Is a source compile out of the question?

I would think it may be better then mixing debian/ubuntu.

I tried once and ran into trouble because I used the debian ver of libc6, apparently its a crucial package ;)

---

