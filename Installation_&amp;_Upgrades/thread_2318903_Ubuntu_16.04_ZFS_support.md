---
title: "Ubuntu 16.04 ZFS support"
date: 2016-03-30
forum: Installation &amp; Upgrades
---

### Post by david509 on 2016-03-30
Hi

Will the Ubuntu 16.04 installer offer ZFS as a choice for the root file system? If so, what about encryption, secure boot support and dual-booting with Windows 10?

I've tried searching these forums and online for this info and I haven't found anything so far, other than reading that Ubuntu 16.04 will include support for the ZFS file system - and how good ZFS is supposed to be. ;)

---

### Post by oldfred on 2016-03-30
There may be a monkey wrench in the works. 

[http://www.phoronix.com/scan.php?page=news_item&px=SFC-GPL-ZFS-Linux](http://www.phoronix.com/scan.php?page=news_item&px=SFC-GPL-ZFS-Linux)

---

### Post by david509 on 2016-03-30
> **oldfred said:**
> There may be a monkey wrench in the works. 

[http://www.phoronix.com/scan.php?page=news_item&px=SFC-GPL-ZFS-Linux](http://www.phoronix.com/scan.php?page=news_item&px=SFC-GPL-ZFS-Linux)

I'm aware there's a tricky licensing issue.
Assuming ZFS ships with Ubuntu, would ZFS be included in the list of file systems during install?  I hope so. 8-)

---

### Post by grahammechanical on 2016-03-30
> Will the Ubuntu 16.04 installer offer ZFS as a choice for the root file system?

I do not think so. This page was last edited 22 days ago.

[https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-16.04-to-a-Native-ZFS-Root-Filesystem](https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-16.04-to-a-Native-ZFS-Root-Filesystem)

> In the fresh install path, you will start the installer, get to the  point you are asked to prepare your disks, and hop out to a shell to get  things ready.

Regards

---

### Post by lukeiamyourfather on 2016-04-06
> **david509 said:**
> Will the Ubuntu 16.04 installer offer ZFS as a choice for the root file system?

As of right now it seems the answer is no. ZFS can be used as the root file system but it's not as easy as just selecting a file system in the installer.

> **david509 said:**
> ...and how good ZFS is supposed to be. ;)

I've been using it for several years for file servers. For that purpose it's by far the best file system out there IMHO.

> **oldfred said:**
> There may be a monkey wrench in the works.

Seems like FUD but even if there are real legal problems you can just install ZFS on Linux through their PPA (which is what I've been doing for years).

---

### Post by ivank2139 on 2016-04-17
I really hope  it will be a painless and easy install with the ability to create zfs rpools and mirrored configurations during the install.  Anything less will be detrimental to widespread adoption of zfs.

---

### Post by frogotronic on 2016-04-20
So, when upgrading from 15.10 to 16.04, will one's file system be converted to ZFS or not?

---

### Post by deadflowr on 2016-04-20
> **cement_head said:**
> So, when upgrading from 15.10 to 16.04, will one's file system be converted to ZFS or not?

No.
Why would it be?
Your file system will remain whatever file system you enjoyed before the upgrade.

Unless you mean moving from a self-built zfs system to ubuntu's new zfs-able system, then not sure about how that would work.

---

### Post by frogotronic on 2016-04-20
No, right now it's the vanilla 15.10 ext4 filesystem.  Can one install the ZFS system "on top" of the current ext4 system?  Or would that require a fresh install?

---

### Post by MAFoElffen on 2016-04-21
First read this:
> 
**[SIZE=4][B]ZFS**[/SIZE][/B]

[COLOR=#333333][FONT=Ubuntu Beta]ZFS support was added to Ubuntu Wily 15.10 as a technology preview and comes fully supported in Ubuntu Xenial 16.04. Note that ZFS is only supported on 64 bit architectures.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]To install ZFS, use:
[/FONT][/COLOR]```

sudo apt-get install zfsutils-linux
```

I confirmed that it worked ok in 16.04 during the dev cycle. The way I do this on an install... is to boot up into the Live CD/USB image > install zfs > install Ubuntu

On initial reboot, I do Recovery Menu > drop to root prompt > check out the filesystem, installation, and ensure the zfs util toolset is there...

It could be viewed as somewhat misleading when it says "fully supported," except that the module is now in the newer kernels. So that quote is from the kernel group, who says that the kernel itself now supports it. ZFS is robust, but just like "mdadm and lvm" ... it does you no good unless the learn understand it, how to use it, support it, and use the tool stack enough to be comfortable with it. If not, it is just a novelty. If you don't learn how to manipulate it, then it's a step backwards for that person.
> **cement_head said:**
> No, right now it's the vanilla 15.10 ext4 filesystem. Can one install the ZFS system "on top" of the current ext4 system? Or would that require a fresh install?
Sort of. You cannot convert, without knowing what you are doing and lots of work. That would be like create the filesystem > then the OS frame work, then transfer the config and data to that system. (Similar to what I described above for a fresh install, but much more...)  That would be the same as recreation on a new install.

Can you "ADD" ZFS to existing? Yes. Add tools. Declare new storage as... your new filesytem ... use it.

If you search in the Server Section of this forum, I think you'll find where I answered this, gave instructions and a lot more details, for people to do this.

---

