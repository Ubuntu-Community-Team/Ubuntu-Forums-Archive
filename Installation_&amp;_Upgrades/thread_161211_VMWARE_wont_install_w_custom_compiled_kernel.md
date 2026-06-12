---
title: "VMWARE wont install w/ custom compiled kernel"
date: 2006-04-16
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-04-16
When i try to install vmware i get the following error: 

```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The kernel defined by this directory of header files does not have the same
address space size as your running kernel.

```

I have a custom compiled VANILA 2.6.15 with ARCH PATCH SET. 

Can anyone help me out?

ps. another user has the same problem:
[http://ubuntuforums.org/showpost.php?p=927453&postcount=123](http://ubuntuforums.org/showpost.php?p=927453&postcount=123)

---

### Post by Abild on 2006-04-16
I did a search on the vmware forum and it seems like you'll have to upgrade to vmware 5.5.1 and  [apply a patch]("http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update101.tar.gz") to make it work.

---

### Post by ashrack on 2006-04-17
with this tweak it works great

---

### Post by Didjit on 2006-04-25
[quote=ashrack]with this tweak it works great[/quote]

Did you just apply the patch and rerun vmware-config while you were booted in the new kernel? I did this and still see the device-mapping errors, which the other thread states is a VMware issue. Wondering if there is something else I should do...

Tx
Didjit

---

### Post by tubo on 2006-05-05
i can confirm the any-any patch works on my custom 2.6.16 kernel and VMWare 5.5.1.

tubo

---

### Post by gsic on 2008-03-07
Hello,

  I'm using the vmware 5.5.1 and when I try to recompile the kernel the shared folder with the vm vanishes, I don't know how to make it come back... anyone could I do? the /mnt/hgfs is just empty.

Thkz!

---

