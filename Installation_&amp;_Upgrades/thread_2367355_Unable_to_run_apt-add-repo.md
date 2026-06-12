---
title: "Unable to run apt-add-repo"
date: 2017-07-29
forum: Installation &amp; Upgrades
---

### Post by shridhar-kapshikar on 2017-07-29
Hi, During ubuntu installtion, I have received update-grub failed and then I have booted the machine in LIVE USB. 
Trying to install boot-repair but getting below error 

```

/# grub-install /dev/sda
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.

```

Hence I am trying to install boot-repair repo to fix this grub error

```

ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 95, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu Canonical Support/xenial
ubuntu@ubuntu:~$ 

```


Is there any other way to install boot-repair.

---

### Post by slickymaster on 2017-07-29
You need to update your distribution template. Open a terminal window (Ctrl+Alt+T) and run the following code, one at a time```
sudo -i
gedit /etc/lsb-release 
```Now edit that file so it looks like this```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
```Save and close the file and you should be able to add-apt-repository.

---

### Post by shridhar-kapshikar on 2017-07-29
Thank you. Its working like charm.

---

