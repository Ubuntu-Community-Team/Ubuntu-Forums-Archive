---
title: "Remove old kernels stuff"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by zkab on 2018-05-09
I have xubuntu 17.10 ...

~$ uname -a
Linux loke 4.13.0-41-generic #46-Ubuntu SMP Wed May 2 13:38:30 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

when I do ...

~$ dpkg --list | grep linux-

I get as follows ...

```
ii  binutils-x86-64-linux-gnu             2.29.1-4ubuntu1                          amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                            4.5ubuntu1                               all          Linux image base package
ii  linux-firmware                        1.169.3                                  all          Firmware for Linux kernel drivers
ii  linux-generic                         4.13.0.41.44                             amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.13.0-31               4.13.0-31.34                             all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-31-generic       4.13.0-31.34                             amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-36               4.13.0-36.40                             all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-36-generic       4.13.0-36.40                             amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-39               4.13.0-39.44                             all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-39-generic       4.13.0-39.44                             amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-41               4.13.0-41.46                             all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-41-generic       4.13.0-41.46                             amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                 4.13.0.41.44                             amd64        Generic Linux kernel headers
rc  linux-image-4.13.0-16-generic         4.13.0-16.19                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-17-generic         4.13.0-17.20                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-19-generic         4.13.0-19.22                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-21-generic         4.13.0-21.24                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-25-generic         4.13.0-25.29                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-31-generic         4.13.0-31.34                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-32-generic         4.13.0-32.35                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-36-generic         4.13.0-36.40                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-37-generic         4.13.0-37.42                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-38-generic         4.13.0-38.43                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-39-generic         4.13.0-39.44                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-41-generic         4.13.0-41.46                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-16-generic   4.13.0-16.19                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-17-generic   4.13.0-17.20                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-19-generic   4.13.0-19.22                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-21-generic   4.13.0-21.24                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-25-generic   4.13.0-25.29                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-31-generic   4.13.0-31.34                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-32-generic   4.13.0-32.35                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-36-generic   4.13.0-36.40                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-37-generic   4.13.0-37.42                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-38-generic   4.13.0-38.43                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-39-generic   4.13.0-39.44                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-41-generic   4.13.0-41.46                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-generic                   4.13.0.41.44                             amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  4.13.0-41.46                             amd64        Linux Kernel Headers for development
ii  linux-signed-generic                  4.13.0.41.44                             amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-4.10.0-20-generic  4.10.0-20.22                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-21-generic  4.10.0-21.23                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-22-generic  4.10.0-22.24                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-24-generic  4.10.0-24.28                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-26-generic  4.10.0-26.30                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-28-generic  4.10.0-28.32                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-30-generic  4.10.0-30.34                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-32-generic  4.10.0-32.36                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-33-generic  4.10.0-33.37                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-35-generic  4.10.0-35.39                             amd64        Signed kernel image generic
rc  linux-signed-image-4.10.0-37-generic  4.10.0-37.41                             amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-16-generic  4.13.0-16.19                             amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-17-generic  4.13.0-17.20                             amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-19-generic  4.13.0-19.22                             amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-21-generic  4.13.0-21.24                             amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-25-generic  4.13.0-25.29                             amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-31-generic  4.13.0-31.34                             amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-32-generic  4.13.0-32.35                             amd64        Signed kernel image generic
ii  linux-signed-image-4.13.0-36-generic  4.13.0-36.40                             amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-37-generic  4.13.0-37.42                             amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-38-generic  4.13.0-38.43                             amd64        Signed kernel image generic
ii  linux-signed-image-4.13.0-39-generic  4.13.0-39.44                             amd64        Signed kernel image generic
ii  linux-signed-image-4.13.0-41-generic  4.13.0-41.46                             amd64        Signed kernel image generic
ii  linux-signed-image-generic            4.13.0.41.44                             amd64        Signed Generic Linux kernel image
```

How can I get rid of all linux stuff except 4.13.0-41 and 4.13.0-39 ?

---

### Post by dino99 on 2018-05-09
'autoremove' script might do the job; but you can indeed delete the unneeded entries from /boot/ dir

---

### Post by sp40140 on 2018-05-09
Try
(for some reason this leaves blank entries in the dpkg list for me.)
```

sudo apt autoremove

```

OR
```

sudo apt purge linux-image-x.x.x-x-generic
sudo apt purge linux-image-extra-x.x.x-x-generic

```

---

### Post by zkab on 2018-05-09
Thanks - I removed them with 'apt purge' command and now I have ...

```
$ dpkg --list | grep linux-
ii  binutils-x86-64-linux-gnu             2.29.1-4ubuntu1                          amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                            4.5ubuntu1                               all          Linux image base package
ii  linux-firmware                        1.169.3                                  all          Firmware for Linux kernel drivers
ii  linux-generic                         4.13.0.41.44                             amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.13.0-39               4.13.0-39.44                             all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-39-generic       4.13.0-39.44                             amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-41               4.13.0-41.46                             all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-41-generic       4.13.0-41.46                             amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                 4.13.0.41.44                             amd64        Generic Linux kernel headers
ii  linux-image-4.13.0-39-generic         4.13.0-39.44                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-41-generic         4.13.0-41.46                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-39-generic   4.13.0-39.44                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-41-generic   4.13.0-41.46                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-generic                   4.13.0.41.44                             amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  4.13.0-41.46                             amd64        Linux Kernel Headers for development
ii  linux-signed-generic                  4.13.0.41.44                             amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-4.13.0-39-generic  4.13.0-39.44                             amd64        Signed kernel image generic
ii  linux-signed-image-4.13.0-41-generic  4.13.0-41.46                             amd64        Signed kernel image generic
ii  linux-signed-image-generic            4.13.0.41.44                             amd64        Signed Generic Linux kernel image

```

Is there away to do that automatically in the future when new kernels are installed ?

---

### Post by deadflowr on 2018-05-09
> Is there away to do that automatically in the future when new kernels are installed ?

You can enable unattended-upgrades and then uncomment the line
```
//Unattended-Upgrade::Remove-Unused-Dependencies "false";
```
and change it to
```
Unattended-Upgrade::Remove-Unused-Dependencies "true";
```
in the file /etc/apt/apt.conf.d/50unattended-upgrades.

Downside, of course, is it applies the same rules of autoremove as in

> autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed as dependencies changed or the package(s) needing
           them were removed in the meantime.

           [B]You should check that the list does not include applications you
           have grown to like even though they were once installed just as a
           dependency of another package. You can mark such a package as
           manually installed by using apt-mark(8). Packages which you have
           installed explicitly via install are also never proposed for
           automatic removal[/B]

So be wary of any packages you installed as part of the need of another which you now enjoy.

---

### Post by zkab on 2018-05-12
OK - thanks

---

### Post by garvinrick4 on 2018-05-12
If you want to use a piece of software in GUI then download synaptic package management 
launch and go to search and  Linux headers under provided and will see all installed kernels.
Remove ones you want but leave 3 or so to boot off of if a kernel fails at boot. Is nice to learn
command line removal and get list of all kernels just so you know how and what but sometimes just easier to see all loaded packages and remove
from synaptic.

---

### Post by zkab on 2018-05-13
Thanks

---

### Post by rsteinmetz70112 on 2018-05-13
> **garvinrick4 said:**
> If you want to use a piece of software in GUI then download synaptic package management 
launch and go to search and  Linux headers under provided and will see all installed kernels.
Remove ones you want but leave 3 or so to boot off of if a kernel fails at boot. Is nice to learn
command line removal and get list of all kernels just so you know how and what but sometimes just easier to see all loaded packages and remove
from synaptic.

I have a system which has a number of old things in my /boot directory, They came from a long time ago. Synaptic doesn't know they are there and doesn't list them as installed. Infact according to my system some of them were never installed. So be careful if you rely on it for very old stuff. Other than that the Synaptic can sometimes repair stuff apt and other tools can't.

---

### Post by VMC on 2018-05-13
@OP,
In the years that I have used Linux, I have never needed but one kernel. I know most suggest having at least two.
 Also, I have my own grub.cfg that I use, and never use those scripts.

I wouldn't even be saying this is you were"new", or this topic was the the new category.
My alias for removing kernels:
```
alias rmkern='echo "dpkg -l linux-* | awk '\''/^ii/{ print \$2}'\'' | grep -v -e \`uname -r | cut -f1,2 -d\"-\"\` | grep -e [0-3]| xargs sudo apt-get -y purge --dry-run"'
```

Then again, I only have one kernel to remove. You can run the above code to see what would get removed. Tweak it to keep two if you like

---

### Post by zkab on 2018-05-14
OK - I will test your script

---

### Post by monkeybrain20122 on 2018-05-14
> **rsteinmetz70112 said:**
> I have a system which has a number of old things in my /boot directory, They came from a long time ago. Synaptic doesn't know they are there and doesn't list them as installed. Infact according to my system some of them were never installed. So be careful if you rely on it for very old stuff. Other than that the Synaptic can sometimes repair stuff apt and other tools can't.

How did you get those very old kernels in the first place??

---

### Post by sp40140 on 2018-05-18
I used to remove all but the latest as well. But once I ran into Nvidia driver issue on latest and the previous one allowed me to getby until next kernel fixed it. Since, I keep two just in case.

---

### Post by dr_squalo on 2018-05-26
I used to remove old kernels by 'purge-old-kernels'  script from the byobu package .   But in Bionic it does not work anymore.  Script is now almost empty expect the line 'apt  autoremove'
which doesn't do the stuff.  Developer means, that it should work now only with this command, which is not true in 18.04.
The old kernels are still residiing in /boot/
Can someone confirm?

---

### Post by Doug S on 2018-05-26
There are two very good selective kernel removal scripts available. [here]("https://askubuntu.com/questions/892076/how-to-selectively-purge-old-kernels-all-at-once") (both a desktop and server version) and [here]("https://launchpad.net/linux-purge") (git based).

---

### Post by dr_squalo on 2018-05-27
Thx for the hint. But there occure erros when also checking singed kernel images in this script

---

### Post by Doug S on 2018-05-27
> **dr_squalo said:**
> Thx for the hint. But there occure erros when also checking singed kernel images in this scriptI mainly use the server version from my [1st link]("https://askubuntu.com/questions/892076/how-to-selectively-purge-old-kernels-all-at-once") above. I tried it on an 18.04 desktop computer (an old iMac) and it worked fine with a signed kernel.

---

### Post by dr_squalo on 2018-05-27
Maybe it's due to the fact, that the singed kernel comes as " ... generic.efi.signed".
Then no packages could be found by this pattern  and script terminates /wo removing anything.

---

