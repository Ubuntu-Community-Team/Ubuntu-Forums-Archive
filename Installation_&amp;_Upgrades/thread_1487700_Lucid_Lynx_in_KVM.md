---
title: "Lucid Lynx in KVM"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by tjajab on 2010-05-19
I have a 32-bits Ubuntu Hardy installation, on which I was trying to install an image of Lucid Lynx 10.04 server with the following command:
```
sudo virt-install --connect qemu:///system -n ubuntu-lucid-test -r 1526 -f /opt/virtualmachines/ubuntu-lucid-test.img -s 10 -c ubuntu-10.04-server-i386.iso --noautoconsole --vnc -v --accelerate
```
When connecting to the domain with virt-viewer, I get a black screen after I choose "Install Ubuntu Server". The last message I see is "Trying to enable the frame buffer". I have tried with different vga modes, but it is doesn't help.

Then I tried installing the machine without --accelerate, and it suddenly worked. I could later redefine the domain by editing "/etc/libvirt/qemu/mymachine.xml" by changing qemu to kvm in the <domain>-tag and the <emulator>-tag to kvm (instead of qemu), and running define /etc/libvirt/qemu/mymachine.xml in virsh.

Also Lucid alternate ISO fails in the same way when using accelerate. Is this a known problem?

---

