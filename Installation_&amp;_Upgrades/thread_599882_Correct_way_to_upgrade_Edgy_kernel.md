---
title: "*Correct* way to upgrade Edgy kernel"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by djbloc on 2007-11-01
Hi,

I would like some advice on the correct way to upgrade the kernel in Edgy using "Aptitude". I tried upgrading the kernel many months ago when I first installed Edgy from CD and something went wrong with the upgrade. I couldn't boot properly and in the end I had to reinstall from CD. So please forgive me if this is simple but as they say, one bitten...

Using Aptitude 0.4.1, I the following packages available:

Under Upgradable Packages - base -  main

i     linux-image-2.6.17-10-server                                                                              2.6.17-10. 2.6.17.1-1
i     linux-image-server                                                                                               2.6.17.10  2.6.17.12.
i     mount                                                                                                                 2.12r-11ub 2.12r-11ub
i     startup-tasks                                                                                                      0.2.7-7    0.2.7-7.2
i     system-services                                                                                                  0.2.7-7    0.2.7-7.2
i     tar                                                                                                                       1.15.91-2u 1.15.91-2u
i     upstart                                                                                                                 0.2.7-7    0.2.7-7.2
i     upstart-compat-sysv                                                                                           0.2.7-7    0.2.7-7.2
i     upstart-logd                                                                                                         0.2.7-7    0.2.7-7.2
i     util-linux                                                                                                            2.12r-11ub 2.12r-11ub

Under Upgradable Packages - base -  restricted

i     linux-server                                                                                                        2.6.17.10  2.6.17.12.

Under New Packages - admin - main 

p     update-manager-core                                                                                    <none>     0.56~edgy4

Under New Packages - base - main

p     linux-image-2.6.17-12-386                                                                             <none>     2.6.17.1-1
p     linux-image-2.6.17-12-generic                                                                       <none>     2.6.17.1-1
p     linux-image-2.6.17-12-server                                                                         <none>     2.6.17.1-1
p     linux-image-2.6.17-12-server-bigiron                                                            <none>     2.6.17.1-1

Under New Packages - devel - main

p     linux-headers-2.6.17-12                                                                                 <none>     2.6.17.1-1
p     linux-headers-2.6.17-12-386                                                                          <none>     2.6.17.1-1
p     linux-headers-2.6.17-12-generic                                                                     <none>     2.6.17.1-1
p     linux-headers-2.6.17-12-server                                                                       <none>     2.6.17.1-1
p     linux-headers-2.6.17-12-server-bigiron                                                         <none>     2.6.17.1-1
p     linux-image-debug-2.6.17-12-386                                                                  <none>     2.6.17.1-1
p     linux-image-debug-2.6.17-12-generic                                                             <none>     2.6.17.1-1
p     linux-image-debug-2.6.17-12-server                                                             <none>     2.6.17.1-1
p     linux-image-debug-2.6.17-12-server-bigiron                                                 <none>     2.6.17.1-1

My overall goal is to upgrade to Feisty using this method but I understand all Edgy upgrades are needed first. I believe I installed Edgy "Server" originally. The hardware is an old Dell Dimension, Pentium II 233, 384MB RAM.

Uname says: Linux seb 2.6.17-10-server #2 SMP Fri Oct 13 18:47:26 UTC 2006 i686 GNU/Linux

So could someone tell me which of the numerous "linux-XXX" packages above should I select (and in what order of priority) to install to get the latest kernel updates?

Many thanks for your help

---

### Post by djbloc on 2007-11-02
I should have said before, I've been searching the wiki and google for a while and not come up with any concrete answers.

So all help is appreciated.
Thanks

---

### Post by djbloc on 2007-11-06
Please feel free to point me in the right direction if I have missed any documentation that could answer this question.

In particular, which of the following packages should I select for the correct upgrade of the kernel in Edgy:

linux-image-2.6.17-10-server
linux-image-server
linux-server 

Thanks

---

### Post by LinuxGuy1234 on 2007-11-06
> **djbloc said:**
> Please feel free to point me in the right direction if I have missed any documentation that could answer this question.

In particular, which of the following packages should I select for the correct upgrade of the kernel in Edgy:

linux-image-2.6.17-10-server
linux-image-server
linux-server 

Thanks

The package would be:
linux-image-2.6.17-10-server

Every Ubuntu kernel has this:
linux-image-version-rev-generic or server

For example, take my computer that is a Dapper machine.
It would be:
linux-image-2.6.15-26-686
and be:
linux-image-2.6.15-26-386 

(Note: all of these are generic kernels unless noted in the package name)

In Edgy Desktop:
linux-image-2.6.17-10-generic

---

### Post by djbloc on 2007-11-06
> **LinuxGuy1234 said:**
> The package would be:
linux-image-2.6.17-10-server

Every Ubuntu kernel has this:
linux-image-version-rev-generic or server


Thanks for the recommendation. I was about to hit the upgrade 'button' but on reading the last sentance in the package information, it seems to contradict your recommendation

> 
  Description: Linux kernel image for version 2.6.17 on x86/x86_64
    This package contains the Linux kernel image for version 2.6.17 on x86/x86_64.

    Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in
    an unbootable state after an update.

    Supports Server processors.

    Geared toward server systems.

    [B]You likely do not want to install this package directly. Instead, install the linux-server meta-package, which will ensure that upgrades work
    correctly, and that supporting packages are also installed.[/B]
  Priority: optional
  Section: base
  Maintainer: Ben Collins <ben.collins@ubuntu.com>
  Compressed size: 23.6M
  Uncompressed size: 69.1M
<snip>
  --\ Versions
i    2.6.17-10.33
p    2.6.17.1-10.34


I'm sure there is a simple answer but I'm just :confused:

---

