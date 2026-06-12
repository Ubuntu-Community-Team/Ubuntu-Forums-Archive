---
title: "Clone Ubuntu 13.10 with Clonezilla - restore on a computer with different hardware."
date: 2013-12-20
forum: Installation &amp; Upgrades
---

### Post by Nane_89 on 2013-12-20
Hey!

Today i cloned my Ubuntu 13.10 with Clonezilla - and i successfully restored it on a different pc with Virtual Box. I'm thinking about buying one more hard drive to a computer with different hardware and restore my laptops Ubuntu installation to this machine. Is this a good way to clone an installation, or can i run in to problems later on?

Thanks!

---

### Post by sudodus on 2013-12-20
An installed Ubuntu operating system is portable between computers, if you have not installed any proprietary drivers (and there is no incompatible hardware). So you can clone a HDD or SSD or USB pendrive and expect that it will work in another computer.

It is possible to clone to a device with the same or larger size with ***Clonezilla*** or ***dd***, but not to a smaller device. An alternative is to make a tarball, and expand it into the new device (HDD, SSD or USB pendrive). Then it will also be possible to port it to a smaller device. (It is not true cloning). There is a tool for that process, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), that works for systems with a root partition and an optional swap partition.

---

### Post by C.S.Cameron on 2013-12-20
One Button Installer +1

---

### Post by elim-qiu on 2014-03-21
I'd like to confirm this in my situation: I have two Dell latitude D430, Both are multi-boot. I like to copy a ubuntu 13.10 partition from one to the other. Is it possible to use clonezilla with basic partition clone option? 

Thanks a lot

---

### Post by sudodus on 2014-03-22
@*elim-qiu*

I think you mean not to copy the whole drive, but only one partition, the 'ubuntu' partition using Clonezilla.

It is possible if the partitions are 'the same', for example the same size. Otherwise it it possible to delete all files in the target partition and copy all files from the source partition with rsync. You may or may not need to reinstall grub depending on the situation.

You can use this command assuming you boot from a third drive and connect the source and target drives to the same computer.

```
rsync -Havn /path-to-mount-point-of-source-partition/ /path-to-mount-point-of-target-partition
```

You can also copy via a local network with rsync: [FONT=courier new]**user@ip-adress:/path-to-mount-point-of-{source-or-target}-partition**[/FONT]

See ```
man rsync
``` and this link

[https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

---

