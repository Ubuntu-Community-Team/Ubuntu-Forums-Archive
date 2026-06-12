---
title: "Cant un-install vbox"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2016-02-22
Want to upgrade to new version of Oracle Virtual Box but Ubuntu OS says not possible because it will break existing version (?). Then tried Ubuntu Software Centre to remove existing version but Vbox is not listed as installed in the software packages list. What gives? is there some secret here I don’t know about?

---

### Post by howefield on 2016-02-22
Does the terminal command

```
dpkg -l virtualbox*
```

return anything ?

---

### Post by mayagrafix on 2016-02-22
> **howefield said:**
> Does the terminal command

```
dpkg -l virtualbox*
```

return anything ?

**It runs AoK, I just cant seem to un install.**
```
mayagrafix@mother:~$ dpkg -l virtualbox*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                   Architecture              Description
+++-=========================================-=========================-=========================-========================================================================================
rc  virtualbox                                4.1.18-dfsg-1ubuntu1.1    amd64                     x86 virtualization solution - base binaries
un  virtualbox-2.0                            <none>                    <none>                    (no description available)
un  virtualbox-2.1                            <none>                    <none>                    (no description available)
un  virtualbox-2.2                            <none>                    <none>                    (no description available)
un  virtualbox-3.0                            <none>                    <none>                    (no description available)
rc  virtualbox-4.2                            4.2.18-88780~Ubuntu~rarin amd64                     Oracle VM VirtualBox
ii  virtualbox-4.3                            4.3.30-101610~Ubuntu~rari amd64                     Oracle VM VirtualBox
un  virtualbox-dkms                           <none>                    <none>                    (no description available)
un  virtualbox-guest-additions-iso            <none>                    <none>                    (no description available)
un  virtualbox-guest-modules                  <none>                    <none>                    (no description available)
un  virtualbox-ose                            <none>                    <none>                    (no description available)
un  virtualbox-ose-qt                         <none>                    <none>                    (no description available)
rc  virtualbox-qt                             4.1.18-dfsg-1ubuntu1.1    amd64                     x86 virtualization solution - Qt based user interface
un  virtualbox-source                         <none>                    <none>                    (no description available)
mayagrafix@mother:~$ 
 
```

---

### Post by howefield on 2016-02-23
Looks like virtualbox-4.3 is installed so remove with..

```
sudo apt-get remove virtualbox-4.3
```

You should get the opportunity to review what is being removed before you commit, but using the -s switch to simulate what will happen might be considered before running it for real.

```
sudo apt-get remove -s virtualbox-4.3
```

---

