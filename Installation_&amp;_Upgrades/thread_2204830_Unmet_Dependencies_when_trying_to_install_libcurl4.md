---
title: "Unmet Dependencies when trying to install libcurl4-openssl-dev"
date: 2014-02-10
forum: Installation &amp; Upgrades
---

### Post by jose21 on 2014-02-10
Need help installing this package. 

```

root@ns5001047:/usr/local/apache2/bin# apt-get install  libcurl4-openssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.


Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
  libcurl4-openssl-dev: Depends: libc6-dev but it is not going to be installed or
                                 libc-dev
                        Depends: libkrb5-dev but it is not going to be installed or
                                 hurd but it is not installable
                        Depends: libssl-dev but it is not going to be installed
                        Depends: zlib1g-dev but it is not going to be installed
E: Broken packages



```



I have tried

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install -f

---

