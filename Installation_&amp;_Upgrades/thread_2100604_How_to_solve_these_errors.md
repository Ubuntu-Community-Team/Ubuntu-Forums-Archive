---
title: "How to solve these errors"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by Mohan1289 on 2013-01-02
```


Err http://archieve.canonical.com precise/partner i386 Packages
  Something wicked happened resolving 'archieve.canonical.com:http' (-5 - No address associated with hostname)
Err http://archieve.canonical.com precise/partner Translation-en_US
  Something wicked happened resolving 'archieve.canonical.com:http' (-5 - No address associated with hostname)
Err http://archieve.canonical.com precise/partner Translation-en
  Something wicked happened resolving 'archieve.canonical.com:http' (-5 - No address associated with hostname)
Fetched 490 B in 17s (28 B/s)
W: GPG error: http://www.duinsoft.nl debs Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E18CE6625CB26B26
W: Failed to fetch http://archieve.canonical.com/dists/precise/Release.gpg  Something wicked happened resolving 'archieve.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  403  Forbidden: category denied

W: Failed to fetch http://archieve.canonical.com/dists/precise/partner/source/Sources  Something wicked happened resolving 'archieve.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archieve.canonical.com/dists/precise/partner/binary-i386/Packages  Something wicked happened resolving 'archieve.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archieve.canonical.com/dists/precise/partner/i18n/Translation-en_US  Something wicked happened resolving 'archieve.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archieve.canonical.com/dists/precise/partner/i18n/Translation-en  Something wicked happened resolving 'archieve.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by dino99 on 2013-01-02
you are using "archieve" instead of "archive"

sudo gedit /etc/apt/sources.list

---

### Post by Mohan1289 on 2013-01-02
> **dino99 said:**
> you are using "archieve" instead of "archive"

sudo gedit /etc/apt/sources.list


Thank you but all the errors are not resolved...
```

W: GPG error: http://www.duinsoft.nl debs Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E18CE6625CB26B26
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  403  Forbidden: category denied

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

how to resolve these errors and warnings

---

### Post by ibjsb4 on 2013-01-02
For GPG error

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Mohan1289 on 2013-01-03
```
 The action would require the installation of packages from not authenticated sources. 
```

This message is being popped up whenever i tried to update using update manager.
how can i resolve this error

---

### Post by ibjsb4 on 2013-01-03
Did you resolve that gpg error?  Looks like the same thing.

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+action+would+require+the+installation+of+packages+from+not+authenticated+sources&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+action+would+require+the+installation+of+packages+from+not+authenticated+sources&as_qdr=all&sa=Google+Search&lang=en)

```
sudo apt-get update
```

---

### Post by oldos2er on 2013-01-03
> **Mohan1289 said:**
> how to resolve these errors and warnings

Install the gpg key ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E18CE6625CB26B26
```

---

### Post by Mohan1289 on 2013-01-04
> **oldos2er said:**
> Install the gpg key ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E18CE6625CB26B26
```


What are the uses of these keys?? can anybody explain??

---

### Post by Mohan1289 on 2013-01-04
```

Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine1.5 i386 1.5.20-0ubuntu2
  403  Forbidden: category denied
Err http://www.duinsoft.nl/pkg/ debs/all update-sun-jre all 1.2.8
  403  Forbidden: category denied
Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine1.5-i386 i386 1.5.20-0ubuntu2
  403  Forbidden: category denied
Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine i386 1.5.20-0ubuntu2
  403  Forbidden: category denied
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine1.5_1.5.20-0ubuntu2_i386.deb  403  Forbidden: category denied
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine1.5-i386_1.5.20-0ubuntu2_i386.deb  403  Forbidden: category denied
Failed to fetch http://www.duinsoft.nl/pkg/pool/all/update-sun-jre_1.2.8_all.deb  403  Forbidden: category denied
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine_1.5.20-0ubuntu2_i386.deb  403  Forbidden: category denied
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
how to correct these errors i tried 

```
sudo apt-get --fix-missing
```
but it says there's no command like that :(

---

### Post by ibjsb4 on 2013-01-04
I see extra spaces that should not be there.  Examples ..

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) precise/main wine1.5 i386 1.5.20-0ubuntu2

/ precise/main wine1.5 i386  should be 
/precise/main wine1.5 i386

[http://www.duinsoft.nl/pkg](http://www.duinsoft.nl/pkg)

/ debs/all update-sun-jre all 1.2.8 should be
/debs/all update-sun-jre all 1.2.8

---

### Post by dannyboy79 on 2013-01-04
> **Mohan1289 said:**
> What are the uses of these keys?? can anybody explain??repository keys are used as a security measure to ensure you're connecting to the correct repository and not some fake one claiming to be the repository.

according to Wiki: Apt-get package management uses public key cryptography to authenticate downloaded packages.

---

### Post by oldos2er on 2013-01-04
> **Mohan1289 said:**
> What are the uses of these keys?? can anybody explain??

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

