---
title: "Installed ubuntu LTA and din't select install Third Party hardware."
date: 2024-11-24
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2024-11-24
I was having a difficult time installing ubuntu LTA so opted to ignore looking for and down loading Third Party hardware. 

So, what might I do to perform the same operation after install, other than since it is newly installed, perform install again?

---

### Post by deadflowr on 2024-11-24
Not sure what LTA is but 3rd party drivers packages relate to multimedia codecs and possibly closed source hardware drivers.

Usually you can get hardware drivers, if applicable to your system, with
```
ubuntu-drivers devices
ubuntu-drivers list
sudo ubuntu-drivers install <listed-driver-name>
```
replace <listed-driver-name> with the proper driver name.

Note that this only applies to closed source restricted drivers such as nvidia and a handful of wireless networking devices.

And install the multimedia codecs with
```
sudo apt install ubuntu-restricted-extras
```

---

