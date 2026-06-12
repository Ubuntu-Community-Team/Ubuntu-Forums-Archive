---
title: "no boot menu at startup after installing ubuntu alongside win7"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by bipbip293 on 2012-04-02
Hi community,

  I just finished to install ubuntu alongside windows 7, but now there is no possibility to choose which partition to boot from at the start up. 

The partitions on the disk looks like the following. 

[[IMG]http://img62.imageshack.us/img62/1264/ubuntuwin7dualboot.jpg[/IMG]]("http://imageshack.us/photo/my-images/62/ubuntuwin7dualboot.jpg/")

 
Do I have to do this Grub rescue method or is there maybe a simpler fix ?
[IMG]http://imageshack.us/photo/my-images/62/ubuntuwin7dualboot.jpg/[/IMG]

---

### Post by oldfred on 2012-04-02
Are you directly booting to Windows or Ubuntu. 

If Ubuntu it does not show a menu if only one system found. This should find Windows and then you will get a menu.
```

sudo update-grub
```

If booting into Windows, grub2 did not install boot loader to MBR correctly.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by bipbip293 on 2012-04-04
It was booting directely to Windows.

I added Boot fix during a Ubuntu Live session and ran the recommended repair.

Now GRUB shows up at start up. Thanx for the help.

---

