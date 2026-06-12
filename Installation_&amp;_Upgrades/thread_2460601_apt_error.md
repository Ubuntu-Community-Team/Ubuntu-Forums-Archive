---
title: "apt error"
date: 2021-04-14
forum: Installation &amp; Upgrades
---

### Post by tendouser on 2021-04-14
I guess I made a mistake installing unsigned kernel to my xubuntu

now I get this APT issue

:~$ sudo apt upgrade
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-headers-5.4.110-0504110-generic needs to be reinstalled, but I can't find an archive for it.

---

### Post by deadflowr on 2021-04-14
>  linux-headers-5.4.110-0504110-generic
That's a mainline kernel which isn't available from any repo.
You need to grab it from here manually:
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4.110/]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4.110/")

---

### Post by tendouser on 2021-04-14
after i do reinstall this header how do i stop unsigned kernels to automatically install back again on the system?

---

### Post by deadflowr on 2021-04-14
Mainline kernels are unsigned.
If you want a signed kernel install the stable kernels from the normal repos.

Are you in need of the mainline kernel for some reason?
Are you testing kernels?

---

### Post by tendouser on 2021-04-14
noup....

i just wanted to install a newer kernel but i see that every time i sign into my session a new unsigned kernel is installed automatically but i don't know how to stop it

if i do stop it certainly i will be back to my the regular kernels and continue my apt manual upgrades and with them signed regular kernel too

---

### Post by tendouser on 2021-04-14
sudo dpkg --install linux-headers-5.4.110-0504110-generic_5.4.110-0504110.202104071335_amd64.deb
Selecting previously unselected package linux-headers-5.4.110-0504110-generic.
(Reading database ... 275059 files and directories currently installed.)
Preparing to unpack linux-headers-5.4.110-0504110-generic_5.4.110-0504110.202104071335_amd64.deb ...
Unpacking linux-headers-5.4.110-0504110-generic (5.4.110-0504110.202104071335) over (5.4.110-0504110.202104071335) ...
Setting up linux-headers-5.4.110-0504110-generic (5.4.110-0504110.202104071335) ...
 
done!

how how do i remove and stop those unsigned kernels to install automatically in my system?

---

### Post by grahammechanical on 2021-04-14
Please tells how you obtained this mainline kernel and how you installed it. Did you perhaps set up the Ubuntu mainline kernel PPA? Did you install an application called Mainline from its PPA?

The Ubuntu Handbook says that this Mainline app "Downloads and installs packages automatically." 

[https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/](https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/)

The app called Mainline must act like a repository.

Regards

---

### Post by tendouser on 2021-04-14
done!

I didn't recall I installed uktools

I just uninstalled and everything is fine now

the thing is that i still have so many of these lines when i query using dpkg->

rc  linux-image-4.18.0-15-generic                4.18.0-15.16~18.04.1                  amd64        Signed kernel image generic
rc  linux-image-4.18.0-22-generic                4.18.0-22.23~18.04.1                  amd64        Signed kernel image generic
rc  linux-image-4.18.0-24-generic                4.18.0-24.25~18.04.1                  amd64        Signed kernel image generic
rc  linux-image-4.18.0-25-generic                4.18.0-25.26~18.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.0.0-23-generic                 5.0.0-23.24~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.0.0-25-generic                 5.0.0-25.26~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.0.0-27-generic                 5.0.0-27.28~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.0.0-29-generic                 5.0.0-29.31~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.0.0-31-generic                 5.0.0-31.33~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.0.0-32-generic                 5.0.0-32.34~18.04.2                   amd64        Signed kernel image generic
rc  linux-image-5.0.0-35-generic                 5.0.0-35.38~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.0.0-36-generic                 5.0.0-36.39~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.0.0-37-generic                 5.0.0-37.40~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.3.0-26-generic                 5.3.0-26.28~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.3.0-28-generic                 5.3.0-28.30~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.3.0-40-generic                 5.3.0-40.32~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.3.0-42-generic                 5.3.0-42.34~18.04.1                   amd64        Signed kernel image generic
rc  linux-image-5.3.0-46-generic                 5.3.0-46.38~18.04.1                   amd64        Signed kernel image generic

how do i get rid of those and do they represent any files still on the system or they are only records of previous kernels?

thxs to all guys!

---

### Post by deadflowr on 2021-04-15
The rc indicates that the package is not installed, but that there are however some leftover configs on the system.
You can clear those by removing with a command like
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -y
```

---

### Post by tendouser on 2021-04-16
thxs in advance!
 
i've removed rc status packages remaining successfully out of the system..... now a question.... why APT manager is not getting rid of those when AUTOREMOVE is used?

cheers guys!

---

### Post by grahammechanical on 2021-04-16
It is my understanding that when we get a new Linux kernel through the Ubuntu repositories the packages that make up the different parts of the kernel are especially marked so that the autoremove command knows what to remove when the command is run either through the terminal or as part of Software Updater's update/upgrade processes. I see Software Updater as doing four things - 1) Update 2) upgrade) 3) autoremove 4) update snaps.

Kernels that we install through some other process do not get marked as something that can be removed by the autoremove command. This is my guess.

Regards

---

### Post by Bashing-om on 2021-04-16
tendouser;

In addition: my take on autoremove.
Apt has the concept that it will not remove config files - as you might want to keep them.
One must tell apt to also remove the config files as you do not want to keep them.
```

sudo apt --purge autoremove

```

will do that trick.

[INDENT]a bit of arcane knowledge
[/INDENT]

---

