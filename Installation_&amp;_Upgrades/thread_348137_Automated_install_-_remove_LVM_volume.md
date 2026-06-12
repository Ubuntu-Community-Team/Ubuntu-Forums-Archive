---
title: "Automated install - remove LVM volume"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by tall-male on 2007-01-28
I'm experimenting doing an automated install using preseeding. So far so good. I'm able to use LVM.
However; if a LVM physical volume is already excists I get an error "one or more physical volumes already exists". Obvioulsy, the volume must be delete first. I tried to include 
d-i partman-lvm/confirm boolean true.
Too bad, it doesn't work. The volume is still there and I still get the error. :( 

A part of my preseeding file:

d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto-lvm/disk string /dev/sda
d-i partman-auto/choose_recipe \
       select Separate /home, /usr, /var, and /tmp partitions

I'm using a vmware virtual machine for this. Anyone an idea? :confused:

---

