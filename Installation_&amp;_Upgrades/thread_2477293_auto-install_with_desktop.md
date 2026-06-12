---
title: "auto-install with desktop"
date: 2022-07-20
forum: Installation &amp; Upgrades
---

### Post by kelvorel on 2022-07-20
Hello,

For some project, i am trying to custom an ubuntu livecd iso with two goals:

[LIST=1]
[*]Installation shall be fully automatic. 
[*]Specific packages shall be installed. 
[/LIST]
 
We have also some constraints:[INDENT]a) Installation shall be done offline
b) The installed computer has no internet access
c) We would like to have 2 different ways to install Ubuntu on the same iso:
[/INDENT]
[INDENT=2]c.1) Ubuntu Server + QEMU/KVM
c.2) Ubuntu Server + Desktop
In other words, we would like to have additional packages in the iso live environment and define which ones are installed using the grub entry menu. 
[/INDENT]
[INDENT]d) Ubuntu Server 22.04
[/INDENT]
 
Currently, I am following this tuto: [https://www.pugetsystems.com/labs/hpc/How-To-Make-Ubuntu-Autoinstall-ISO-with-Cloud-init-2213/](https://www.pugetsystems.com/labs/hpc/How-To-Make-Ubuntu-Autoinstall-ISO-with-Cloud-init-2213/)
The only difference is that I am using Cubic to unzip and re-generate the iso because I do not know how to handle the missing of isolinux files. 

Using autoinstall, cloudinit, I am able to make a simple automatic install using a simple user-data file: 

```
#cloud-config
autoinstall:
  version: 1
  identity:
    hostname: ubuntu-server
    password: $6$mJVTTRGurkB4Z3Ka$dKbSKsjHTqdZ.ZiY.vKG7BC57nFsMmY.wnWhMDNAUa9zFt0263UiGktrXIn.AcIlfqLBIIJRgwg/pJS8XN2yF0
    username: ubuntu    
```

This works fine and then I can install ubuntu-desktop using
```

sudo apt install ubuntu-desktop
```

However, I do not know how to pre-download the "ubuntu-desktop" in the iso and to automatically install it during the auto-installation. 

Using Cubic, I have tried to install ubuntu-desktop in the chroot terminal: 

```
root@cubic:~# apt install ubuntu-desktop
```

But I have one error. I can still generate the iso but the installation fails. 

My question is:

**Does someone have an idea how I can have the package available in my iso (offline constraint) and auto-install it when selected in the grub menu ?**

Thank you,

---

### Post by tea for one on 2022-07-20
According to the package manifest, the installers for Ubuntu 22.04 Server and Ubuntu 22.04 Desktop are different.

Ubuntu 22.04 Desktop uses ubiquity 22.04.15
Ubuntu 22.04 Server uses snap:subiquity stable/ubuntu-22.04 

Perhaps revisit your Cubic (Ubuntu Desktop) Iso and change the installer.

---

### Post by kelvorel on 2022-07-21
Thank you for your answer.

> Ubuntu 22.04 Desktop uses ubiquity 22.04.15
Ubuntu 22.04 Server uses snap:subiquity stable/ubuntu-22.04 

I am aware of this. This is why I want to use the Ubuntu Server to manage both Desktop and Server with the same auto-install method. Some people said they did that.

> Perhaps revisit your Cubic (Ubuntu Desktop) Iso and change the installer.

I do not understand concretely what do you mean ?

---

### Post by tea for one on 2022-07-21
Your project is quite complicated so I may well have misunderstood the process.

You wrote that you use Cubic to add ubuntu-desktop and generate a new iso.
Subsequently, the installation fails.

During the process of using Cubic, have you tried to remove subiquity and add ubiquity.
In effect, the generated Desktop iso will have the usual installer.

Whether this will work, I do not know but worth a look.

---

### Post by kelvorel on 2022-08-02
At the end, I found a way to reach my goal. 

1) I generate a local repository with all the required packages. 
2) I "extract" the Ubuntu 22.04 Server .iso by mounting it and copying the content. 
3) I "extract" the filesystem .squashfs by mounting it and copying the content. 
4) I put in the filesystem my local_repository and I edit in /etc/apt/,  source.list where I comment everything (I am offline) and I add source.list.d/local.list which links my local repository. 
5) I re-generate my squashfs file using mksquashfs
6) In the ISO file I have extracted, I replace /boot/grub/grub.cfg by a custom grub.cfg file which indicates several user-data files in three locations: server/user-data, workstation/user-data
7) I re-generate the ISO using xorriso.

I have now a ISO which can allow me to auto-install several type of machines offline with all the packages I need.

---

### Post by ActionParsnip on 2022-08-03
Could use chef/puppet for a standardized set of settings. Once you add a system to the chef/puppet system then it will start adding the configurations it should have

---

