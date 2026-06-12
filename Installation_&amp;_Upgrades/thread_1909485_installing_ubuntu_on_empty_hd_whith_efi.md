---
title: "installing ubuntu on empty hd whith efi"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by boregard on 2012-01-15
hi everyone,i am currently using OO. 11.10 on acer laptop and am wanting to purchase intel based barebones kit & build my own comp.i have been reading all the threads in the forum of the problems people have, getting ubuntu to boot on newer computers with efi instead of bios. my question is would i run into same problems even though it would have empty hd and strictly use ubuntu os only? wanted to know before i made purchase. all my searches turn up with, advice on intel based macs.appreciate any help or advice.Thanks.

---

### Post by darkod on 2012-01-15
I haven't had a chance to work with efi so far, but from I read here the main problem happens in dual boot situation because both windows and ubuntu try to save the bootloader info on the same efi partition and overwrite the other OS files.

In single boot you should be fine.

But you will have to boot in live mode first and use parted to create a 1MB EFI System Partition as first primary partition. This is necessary to exist before you start the install I think.

If you are not familiar too much with the text based tool parted, just google "manpage parted". I don't think you can do it with Gparted, and similar... But I might be wrong.

EDIT: It seems the partition should be at least 100MB, not only 1MB.

---

### Post by darkod on 2012-01-15
Update: I just checked and a better text tool for partitioning is cfdisk. You start it with:

sudo cfdisk /dev/sda

It will allow you to create any partitions you want. The EFI partition should have EF code/type. It seems easier to use than parted but it's still a text tool. On first glance parted doesn't seem to have the EF option, while cfdisk does.

---

### Post by boregard on 2012-01-15
thanks for your help darkod. i'll look into your suggestions, hopefully i can understand it because i am not familiar with partitioning drves. have a good one.

---

