---
title: "installing vm's with KVM on ubuntu 10.04"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by paulclark87 on 2011-03-16
Not sure if this is the correct forum but basically i have kvm installed and im using virt-manager to install my virtual machines. However the first time i installed Ubuntu as a vm and when it finished installing and had to restart i got these error messages saying I/O error. When i tried to rerun the image it came up a black screen and nothign else.
 
Second time around i tried installing xp as a vm and it got to the bit where its saving the files to the installation folder ready to start but when it restarted, the vm shutdown completly and didnt restart. I click the run button on virt-manager but again like ubuntu just came up a black screen.
 
Does anyone know why it isnt working? like something im doing or something to do with kvm.
 
If thats the case then is it possible to install a machine in vmware and convert the file over to a kvm format?
 
thanks

---

### Post by paulclark87 on 2011-03-17
anyone?

---

### Post by TheR on 2011-03-17
Try to look into /var/log/libvirt/qemu/ and see if there is anything meaningful written there.

by
TheR

---

