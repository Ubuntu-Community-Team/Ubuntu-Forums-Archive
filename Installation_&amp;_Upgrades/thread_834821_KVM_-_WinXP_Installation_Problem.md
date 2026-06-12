---
title: "KVM - WinXP Installation Problem"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by jshome on 2008-06-19
while creating VM running windowsXPsp2 I am getting following error. 

installation reference document: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)


prior to the following step, the installation ram smoothly.



root@jshome:/home/windows# virt-install --connect qemu:///system -n xpsp2 -r 512 -f devserver.img -s 5 -c WindowsXPsp2.iso --accelerate --vnc --noautoconsole


Starting install...
libvir: QEMU error : 
libvir: QEMU error : 
libvir: QEMU error : 
Creating storage file...  100% |=========================| 5.0 GB    00:00     
Creating domain...                                                 0 B 00:00 
Domain installation still in progress.  You can reconnect to 
the console to complete the installation process.
root@jshome:/home/windows# virt-viewer -c qemu:///system xpsp2

(virt-viewer:25896): Gtk-WARNING **: cannot open display: 
root@jshome:/home/windows# 


Any help ?

---

