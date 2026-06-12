---
title: "Preseed Failed when getting cfg"
date: 2015-03-04
forum: Installation &amp; Upgrades
---

### Post by Adam_Barnett on 2015-03-04
Hi All 

I have this strange issue. I am doing a netboot + using local mirrors of trusty 14.04
I have done the following to PXE boot the installer 

```

label trusty-amd64-manual
    kernel images/ubuntu-installer/trusty/amd64/linux
    append vga=normal initrd=images/ubuntu-installer/trusty/amd64/initrd.gz debian-installer/locale=en_GB console-setup/layoutcode=gb  preseed/url=http://blah.com/kickstarts/ubuntu/precise-amd64.cfg

```

Which works fine, the installer loads and starts the process. I can see from the logs that it does a wget on [http://blah.com/kickstarts/ubuntu/precise-amd64.cfg](http://blah.com/kickstarts/ubuntu/precise-amd64.cfg) and saves it in /tmp/debconf-seed

Which is correct.

The strange thing is that as soon as it as does the wget it does another one but just to the root directory i.e 
wget [http://blah.com](http://blah.com) and saves it to the same place /tmp/debconf-seed so now the installer will fail with a corrupted preseed config 

my pressed file looks like this 


```

d-i debian-installer/locale string en_GB
d-i console-setup/layoutcode string 


d-i debconf/priority select critical


d-i mirror/country string manual
d-i mirror/http/hostname string blah
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string
d-i mirror/codename string trusty
d-i mirror/suite string trusty

```


Any help would be great 

Thanks
A

---

