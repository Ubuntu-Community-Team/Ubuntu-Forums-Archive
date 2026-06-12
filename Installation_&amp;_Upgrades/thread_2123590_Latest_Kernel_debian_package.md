---
title: "Latest Kernel debian package"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by Lord Wodan on 2013-03-08
Hi,
i am running Ubuntu 12.04.2, and would like to know when ubuntu upgrades to latest kernel 3.7??
i am running version: uname -r3.2.0-38-generic-pae



thanks

---

### Post by grahammechanical on 2013-03-08
As you know 12.04 is a Long Term Support release (5 years) and people who prefer the LTS do not like things such as the kernel upgraded. So, although the system says that is it 12.04.2 it does not have the Linux 3.5 kernel which is on Ubuntu 12.10. I understand that a fresh install of Ubuntu 12.04.2 will give you Linux kernel 3.5.

As for Linux 3.7 I can tell you that Raring Ringtail (13.04) is now up to Linux kernel 3.8. So, Ubuntu does not get the Linux kernel 3.7. Those who want or need the latest (almost) kernels and applications should upgrade or fresh install the latest Ubuntu when it is released. 

Regards.

---

### Post by cortman on 2013-03-08
You can download and compile the latest kernel yourself if you really want it, but as graham says, you'll have to wait for an version upgrade to get it through the repositories.

---

### Post by grahammechanical on 2013-03-08
This link will show you the instructions I followed some months back to install the Quantal kernel 3.5 on 12.04. It worked fine for me but I was testing this out on an additional installation of 12.04 on a spare partition. If you want to take the risk of doing this to your only installation of 12.04, then it is your choice. There are also instructions on how to revert back.

Keep in mind that if the 3.5 kernel does not work out for you and you have problems loading Ubuntu, than at the Grub boot menu select one of the older 3.2 kernels. The kernel that you are using at the moment.

[http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/25321/downloads](http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/25321/downloads)

If things work fine but at some point in the future you hit issues updating then open Software Sources and uncheck that PPA. No need to Purge the PPA if things go well. Just uncheck it from Software Sources.

Regards

---

### Post by Cheesemill on 2013-03-08
The 3.5 kernel is available in the standard repositories for 12.04 as part of the [LTS hardware enablement stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").
You can install it by running...
```
sudo apt-get install linux-generic-lts-quantal
```

I wouldn't recommend installing anything later as it won't have been tested for 12.04.

---

### Post by The Spectre on 2013-03-08
You can easily Update to the Latest Linux Kernel yourself.

Just Download the appropriate deb files for your system.

The three i386.deb files plus the all.deb file for 32bit Systems.

Or the three amd64.deb files plus the all.deb file for 64bit Systems.

The Latest Stable Release (Recommended)...
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.2-raring/)

The Latest RC Release...
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc1-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc1-raring/)

Copy these files into your Home directory.

Open terminal and enter this command. 
```
sudo dpkg -i linux*.deb
```

Usually the only time that anyone has any major problem Updating to the latest Linux Kernel is when they are using the Proprietary ATI or [FONT=arial]NVIDIA Video Card Drivers insted of using the Video Driver that is built into the Linux Kernel itself.

I am currently using Linux Kernel v3.8.2 in Ubuntu 12.10 and I also have an old Pentium 4 system that is running Ubuntu 12.04 with one of the [/FONT][FONT=arial]v3.7.x [/FONT][FONT=arial]Linux Kernel's I haven't used it in a while so I don't remember exactly which one[/FONT][FONT=arial]...

[/FONT][ATTACH=CONFIG]239924[/ATTACH]

---

### Post by Lord Wodan on 2013-03-10
thanks all

i consider to upgrade to Ubuntu 13.04 next month.

---

