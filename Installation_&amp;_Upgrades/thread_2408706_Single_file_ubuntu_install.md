---
title: "Single file ubuntu install"
date: 2018-12-21
forum: Installation &amp; Upgrades
---

### Post by grearsem0nk on 2018-12-21
Hello everyone, 
I am a systems integrator (think robots without wheels) and am unable to switch to ubuntu for 90% of the work I do. 
I can't even stay with a single Windows version. Right now I have 4 installs of Win 10, 1 of Win 8.1 and 1 of 7 each with a different version of the development environment I use and supporting software. 
I do this by multi-booting windows and installing each version of windows into a VHD/VHDX file. This allows me to native boot to any of the options and have full access to all the hardware resources on the computer (minus the slight hit for using a VHD/VHDX). 
Another reason I do this is so I can "recover" an old environment in less then an hour (file transfer time and a reboot)

From what I have found the VHD/VHDX options are not supported by any current version of linux. 
I have found wubi along with quite a few strong opinions about it. 

My question is this, is there another better way to do this?
I don't mind creating a new partition for the linux distro's (yes I will end up with more then one if this works) so I can have more then a single partition file format or what ever is needed. But I want to keep the single file "virtual hard-drive" for various reasons. 

And the follow on question, are there known draw backs to running ubuntu like this? 

Thanks and Merry Christmas everyone!
GreaseM0nk aka. Ryan

---

### Post by TheFu on 2018-12-21
Wubi is dead and unsupported and has been for a while.

Seems like you'd be happiest using virtual machines.  Those can use single files as virtual disks, within limits of the specific hypervisor used.  If you have network storage, there are additional capabilities.  Linux hypervisors generally support "snapshots", so recovering to that point is basically instantaneous. Snapshots do not replace backups, however.
With a properly configured hypervisor like kvm-qemu getting 90-95% of native performance is possible for non-graphical needs without too much effort.
If you need great performance AND GPU intensive capabilities, with the right hardware, you can passthru a 2nd GPU to a guest virtual machine. Gamers do this and get fantastic framerates, sometimes faster than native because the underlying access to hardware is streamlined.

As for disk performance, using fast SSDs solves any of those issues.

qemu-img supports these disk formats:
```
$ qemu-img --help
....
Supported formats: rbd host_cdrom blkdebug qcow host_device vpc qcow2 cloop vdi sheepdog qed nbd tftp ftp vvfat ftps https dmg http vmdk iscsi parallels raw bochs quorum null-aio null-co vhdx blkverify file
```

The main issue with Windows virtual machines is that Windows doesn't like when the hardware changes as will happen when the VM is presented with a virtual motherboard that cannot possibly match what a real install had.  But once you switch to a hypervisor, now your Windows installs are portable to other physical machines, since the hypervisor presented hardware will be the same.

---

### Post by grearsem0nk on 2018-12-21
Hi TheFu,
Thanks for the quick reply. 
For Wubi, you are correct that it is not officially supported. However it is not quite dead yet...here is what I found... [https://github.com/hakuna-m/wubiuefi/releases](https://github.com/hakuna-m/wubiuefi/releases)

Part of the challenge I have is the development software. It uses a lot of divers and needs access to the system bus, USB ports, Ethernet drivers, and in some cases the cpu. The GPU is actually the one thing I usually don't worry about. I have yet to find a virtualization platform that can run this environment with out problems. This is a big reason for the virtual hard drives. 
I will look at kvm-qemu, that sounds very interesting.

---

### Post by wildmanne39 on 2018-12-21
If you go with wubi you will need to contact the people maintaining it for help, I do not believe we offer any support for wubi anymore and I serious doubt anyone here can help, I use virtualbox with no issues on ubuntu but on windows 10 it is slower because something is always running in the back ground slowing the system down.

---

