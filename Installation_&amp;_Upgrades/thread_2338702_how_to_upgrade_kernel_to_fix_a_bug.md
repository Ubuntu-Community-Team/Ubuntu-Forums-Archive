---
title: "how to upgrade kernel to fix a bug"
date: 2016-09-30
forum: Installation &amp; Upgrades
---

### Post by pradeep8985 on 2016-09-30
Hi All,

I came to know due to the following settings in ubuntu kernel, my disks are automatically getting partitioned after the reboots.


# grep ACORN config-3.19.0-25-generic
CONFIG_ACORN_PARTITION=y
CONFIG_ACORN_PARTITION_CUMANA=y
CONFIG_ACORN_PARTITION_EESOX=y
CONFIG_ACORN_PARTITION_ICS=y
CONFIG_ACORN_PARTITION_ADFS=y
CONFIG_ACORN_PARTITION_POWERTEC=y
CONFIG_ACORN_PARTITION_RISCIX=y

Below URL tells me that it is fixed in [COLOR=#333333][FONT=monospace]package linux - 3.19.0-26.28[/FONT][/COLOR]

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1453117](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1453117)

 I am relatively new to ubuntu. How do i upgrade this kernel version alone to fix the bug. Moreover i do not want to upgrade any other packages as my application is stable with current setup.

Please guide me.

---

### Post by ian-weisser on 2016-09-30
Please show us the output of the following command:
```
uname -r
```

---

### Post by pradeep8985 on 2016-10-01
> **ian-weisser said:**
> Please show us the output of the following command:
```
uname -r
```

Here is the output
```
~$ uname -r
3.19.0-25-generic

```

---

### Post by deadflowr on 2016-10-01
What Ubuntu version?

The 3.19.0-XX kernel came with the now dead 15.04 release.
But also came with Ubuntu 14.04.3.
If on 14.04 or 14.04.3 then you can upgrade to the 4.4 kenrel series, which presumably has the fix.

Quick references:
[http://www.ubuntu.com/info/release-end-of-life]("http://www.ubuntu.com/info/release-end-of-life")

[https://wiki.ubuntu.com/1404_HWE_EOL]("https://wiki.ubuntu.com/1404_HWE_EOL")

Though, in reality, the first question about what version will go far to being able to help any further.

---

### Post by pradeep8985 on 2016-10-01
Ubuntu version is 14.04.3 

My Question is how can i upgrade it that kernel version alone as i am new to ubuntu.

---

### Post by deadflowr on 2016-10-01
Option #1: you should be getting a notice when you run the software updater about hwe and how to easily install the updates.
(a message should appear in the update window about it, from what I remember)

Option #2: from here:[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
```
sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial 

```

---

### Post by Bashing-om on 2016-10-01
pradeep8985; Hello;

> 
how can i upgrade it that kernel version alone


The terminal way - as the terminal is a universal language :
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```
which I do expect to bring you up to the current 14.04.5 with xenial's kernel installed . Be aware will not only update the kernel but all installed packages that have updates . It is most highly advised to keep the system fully updated !
IF there are no errors reported - back in your terminal , then ->
Reboot the system to see the effect.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

