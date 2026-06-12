---
title: "ubuntu 13 linux-image won't upgrade"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by rpms on 2014-03-21
My system is ubuntu 13.10 which was upgraded from 13.04 with software updater. Perhaps the kernel image has not upgrade since the 13.04 > 13.10 upgrade.
I recently did software updates that included linux-headers for which there are no image files in /boot. The only image and related files in /boot are for version 3.8.

    ```
/boot/abi-3.8.0-30-generic
    /boot/config-3.8.0-30-generic
    /boot/initrd.img-3.8.0-30-generic
    /boot/System.map-3.8.0-30-generic
    /boot/vmlinuz-3.8.0-30-generic
```

Here is an example of what was installed for instance (taken from /var/log/dkpg.log)..

    ```
2014-03-06 14:08:18 install linux-headers-3.11.0-18:all <none> 3.11.0-18.32
    2014-03-06 14:08:28 install linux-headers-3.11.0-18-generic:amd64 <none> 3.11.0-18.32
```

I see I am getting ONLY the headers, and never the images!..

    ```
$ dpkg -l | grep linux- 
    ii  linux-firmware                            1.116.2                                 all          Firmware for Linux kernel drivers
    ii  linux-headers-3.11.0-14                   3.11.0-14.21                            all          Header files related to Linux kernel version 3.11.0
    ii  linux-headers-3.11.0-14-generic           3.11.0-14.21                            amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
    ii  linux-headers-3.11.0-15                   3.11.0-15.25                            all          Header files related to Linux kernel version 3.11.0
    ii  linux-headers-3.11.0-15-generic           3.11.0-15.25                            amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
    ii  linux-headers-3.11.0-17                   3.11.0-17.31                            all          Header files related to Linux kernel version 3.11.0
    ii  linux-headers-3.11.0-17-generic           3.11.0-17.31                            amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
    ii  linux-headers-3.11.0-18                   3.11.0-18.32                            all          Header files related to Linux kernel version 3.11.0
    ii  linux-headers-3.11.0-18-generic           3.11.0-18.32                            amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
    ii  linux-headers-generic                     3.11.0.18.19                            amd64        Generic Linux kernel headers
    rc  linux-image-3.8.0-19-generic              3.8.0-19.30                             amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
    ii  linux-image-3.8.0-30-generic              3.8.0-30.44                             amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
    rc  linux-image-extra-3.8.0-19-generic        3.8.0-19.30                             amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
    ii  linux-image-extra-3.8.0-30-generic        3.8.0-30.44                             amd64 
```

I have watched many linux-image upgrades go by with similar results. I do not get the upgrades into /boot. When I boot up and select advanced options, only 3.8 is listed. I worry.

Anybody know what may be going wrong?

---

### Post by Bashing-om on 2014-03-22
rpms; Hi !

Maybe at some point the "meta package" for the images got removed (??).
Try:
```

sudo apt-get clean all
sudo apt-get update
sudo apt-get install linux-generic linux-headers-generic linux-image-generic
sudo apt-get update ##again
sudo apt-get upgrade
sudo apt-get dist-upgrade ##to pick up on and install any "held packages"

```

Please to advise on results.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by rpms on 2014-03-23
@Bashing-om >>
Thanks! That looks very promising and mercifully uncomplicated. I was about to take all of those steps. But it looks like I am just up to date at the moment with the kernel version on this (the problem) machine. It the same version as on my other machines. Here it is..
```

$ dpkg -l | grep 3.11.0-18
ii  linux-headers-3.11.0-18                   3.11.0-18.32                            all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-18-generic           3.11.0-18.32                            amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.11.0-18-generic             3.11.0-18.32                            amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-extra-3.11.0-18-generic       3.11.0-18.32                            amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                      3.11.0-18.32                            amd64        Linux Kernel Headers for development

```
What I did after posting to finally get a kernel update was simply..
```
$ sudo apt-get install linux
```
But after that thing were not so simple. Things got shaky. I couldn't update at all ( some messages about broken package(s) ) until I did something like $ sudo apt-get -f install. I can't remember exactly what I did but at least I can update again. But no kernel updates have been offered yet.

Now I think I ought to wait for the next kernel image update to roll out and if this machine still does not update I will try what you have kindly suggested. Best regards to you!

---

### Post by Bashing-om on 2014-03-24
rpms; Hey ;

Things do look promising ! All to the good.

Let's look and see what kernel you have loaded and operating from:
```

uname -r

```
Mine for reference:
> 
sysop@1310mini:~$ uname -r
3.11.0-18-generic
sysop@1310mini:~$


[INDENT]package manager happy
[INDENT][INDENT][INDENT]everybody is happy
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by frank18 on 2014-03-24
> **rpms said:**
> My system is ubuntu 13.10 which was upgraded from 13.04 with software updater. Perhaps the kernel image has not upgrade since the 13.04 > 13.10 upgrade.
I recently did software updates that included linux-headers for which there are no image files in /boot. The only image and related files in /boot are for version 3.8.

    ```
/boot/abi-3.8.0-30-generic
    /boot/config-3.8.0-30-generic
    /boot/initrd.img-3.8.0-30-generic
    /boot/System.map-3.8.0-30-generic
    /boot/vmlinuz-3.8.0-30-generic
```

Here is an example of what was installed for instance (taken from /var/log/dkpg.log)..

    ```
2014-03-06 14:08:18 install linux-headers-3.11.0-18:all <none> 3.11.0-18.32
    2014-03-06 14:08:28 install linux-headers-3.11.0-18-generic:amd64 <none> 3.11.0-18.32
```

I see I am getting ONLY the headers, and never the images!..

    ```
$ dpkg -l | grep linux- 
    ii  linux-firmware                            1.116.2                                 all          Firmware for Linux kernel drivers
    ii  linux-headers-3.11.0-14                   3.11.0-14.21                            all          Header files related to Linux kernel version 3.11.0
    ii  linux-headers-3.11.0-14-generic           3.11.0-14.21                            amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
    ii  linux-headers-3.11.0-15                   3.11.0-15.25                            all          Header files related to Linux kernel version 3.11.0
    ii  linux-headers-3.11.0-15-generic           3.11.0-15.25                            amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
    ii  linux-headers-3.11.0-17                   3.11.0-17.31                            all          Header files related to Linux kernel version 3.11.0
    ii  linux-headers-3.11.0-17-generic           3.11.0-17.31                            amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
    ii  linux-headers-3.11.0-18                   3.11.0-18.32                            all          Header files related to Linux kernel version 3.11.0
    ii  linux-headers-3.11.0-18-generic           3.11.0-18.32                            amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
    ii  linux-headers-generic                     3.11.0.18.19                            amd64        Generic Linux kernel headers
    rc  linux-image-3.8.0-19-generic              3.8.0-19.30                             amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
    ii  linux-image-3.8.0-30-generic              3.8.0-30.44                             amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
    rc  linux-image-extra-3.8.0-19-generic        3.8.0-19.30                             amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
    ii  linux-image-extra-3.8.0-30-generic        3.8.0-30.44                             amd64 
```

I have watched many linux-image upgrades go by with similar results. I do not get the upgrades into /boot. When I boot up and select advanced options, only 3.8 is listed. I worry.

Anybody know what may be going wrong?


I'm just gonna give you my simple opinion,one should never do upgrades on these Distros while these are in testing mode, only after these are released as LTS from 12.04 LTS to the next LTS, always make an ISO image of the right testing  distro, if you do not follow this advice you're gonna have much aggravation,special if you're not an acknowledge tester.

---

### Post by rpms on 2014-03-24
@Bashing-om; hi again. Thank you for the quick return! Yes, I have the exact same output as you have for uname -v:
```

$ uname -r
3.11.0-18-generic

```
I am watching carefully to see when the next kernel version rolls out on one of my machines and then I will attempt to get this one to update again.

@frank18; I appreciate your input. I do suspect that the 13.04 > 13.10 upgrade over the existing 13.04 has caused this nasty situation. kernel upgrading is critical.

---

### Post by Bashing-om on 2014-03-24
rpms; Well;

All looks good for now.

As you say, the next kernel update will tell the tale. I do though expect that all is ship shape, should have no problems.

[INDENT][INDENT]'till then
[INDENT][INDENT]my regards
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rpms on 2014-04-04
@Bashing-om: your hunch was right.. software installer offered up a new kernel image today and the install worked :)
```
$ uname -r
3.11.0-19-generic
```
I plan to backup ubuntu 13.10 when 14.04LTS is offered up by software installer and then go ahead with the install. It's due out this month. Looks nice on youtube.

---

### Post by frank18 on 2014-04-04
> **rpms said:**
> @Bashing-om: your hunch was right.. software installer offered up a new kernel image today and the install worked :)
```
$ uname -r
3.11.0-19-generic
```
I plan to backup ubuntu 13.10 when 14.04LTS is offered up by software installer and then go ahead with the install. It's due out this month. Looks nice on youtube.

What do you have in 13.10 you don't have in 14.04, i'd say in 13.10 you have more problems,

---

### Post by Bashing-om on 2014-04-04
rpms; Outstanding !

All is well that ends well.

I too am anxiously awaiting 14.04's release.
Will see you there.

[INDENT][INDENT]many are on that band wagon
[/INDENT][/INDENT]

---

