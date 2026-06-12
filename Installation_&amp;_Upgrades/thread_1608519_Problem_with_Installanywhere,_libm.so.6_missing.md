---
title: "Problem with Installanywhere, libm.so.6 missing"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by ashok.ericsson on 2010-10-29
Hi all,
 
I am facing problem with one software designed using INSTALLANYWHERE(Macrovision). It is RadioNetworkController ElementManager (RNC EM). It is used to configure the WCDMA RNC of ERICSSON. Generally we use windows but I am trying it out in Linux as linux version is available but ERICSSON doesnot provide any support for it. Trying to install it in Ubuntu 9.10. After installing JRE 1.4.2-19, the application installs correctly but when i try to launch the application i get the following error```
root@ubuntu:/usr/ericsson/Ericsson# cd EM
root@ubuntu:/usr/ericsson/Ericsson/EM# ls
CPP_Element_Manager  CPP_Element_Manager.lax  icon_EM_16.gif  lax.jar
root@ubuntu:/usr/ericsson/Ericsson/EM# ./CPP_Element_Manager
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
/usr/java/j2re1.4.2_19/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
root@ubuntu:/usr/ericsson/Ericsson/EM# 

```
 
 
Before installing i run following command that i found after googling but that did not help.```
cp em_install_lin.bin em_install_lin.bin.bak
 
cat em_install_lin.bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_Kernel/" > em_install_lin.bin

```
 
I am not a expert in linux, i could not understand why the error is coming and what is the workaround. Need help. 
 
Regards
Ashok

---

