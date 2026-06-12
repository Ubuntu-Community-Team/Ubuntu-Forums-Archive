---
title: "Am I using a LTS kernel ?"
date: 2018-08-14
forum: Installation &amp; Upgrades
---

### Post by linuxyogi on 2018-08-14
Hi,

I am using Ubuntu 18.04. Just doing the usual apt-get update/upgrade has updated my installation to 18.04.1.

[I read here in the forum]("https://ubuntuforums.org/showthread.php?t=2397526&p=13788342#post13788342") that if I don't upgrade the kernel manually using it wont upgrade the kernel on its own.

I am atm using 

```
$ uname -a
Linux ubuntu 4.15.0-30-generic #32-Ubuntu SMP Thu Jul 26 17:42:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

Is there anything called a Long Term Support kernel ?

Am I using a LTS kernel ?

---

### Post by #&amp;thj^% on 2018-08-14
Have a read : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by linuxyogi on 2018-08-14
> **1fallen said:**
> Have a read : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

>  However, if one wants to remain on the original GA (General Availability) stacks, the options are: 
[LIST]
[*]Install  from a previous 12.04.0/12.04.1/14.04.0/14.04.1/16.04.0/16.04.1 point  release and update. Previous releases are archived at [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) 

[*]Perform an update or upgrade to an LTS release from a previous release. 
[*]Perform a network install using the netboot images rather than the new <**release**>-netboot images. 

[/LIST]


So if I want to stay with the "GA (General Availability) stacks" simply running apt-get update / upgrade from 18.04.1 will do ?

---

### Post by #&amp;thj^% on 2018-08-14
> **linuxyogi said:**
> So if I want to stay with the "GA (General Availability) stacks" simply running apt-get update / upgrade from 18.04.1 will do ?

In short yes. :)
EDIT: More information.
Don't forget you can check with: "**hwe-support-status --verbose**"
Hardware Enablement Stacks (HWE) are incorporated into installers for select Ubuntu LTS (Long Term Support) point releases. It is a special Ubuntu feature that provides an LTS release with hardware support introduced in newer Ubuntu releases. For Ubuntu 12.04 the point releases are .2/.3/.4/.5 and the corresponding Ubuntu releases.

---

### Post by linuxyogi on 2018-08-14
> **1fallen said:**
> In short yes. :)

Thanks.

---

### Post by linuxyogi on 2018-08-14
> **1fallen said:**
> In short yes. :)
EDIT: More information.
Don't forget you can check with: "**hwe-support-status --verbose**"
Hardware Enablement Stacks (HWE) are incorporated into installers for select Ubuntu LTS (Long Term Support) point releases. It is a special Ubuntu feature that provides an LTS release with hardware support introduced in newer Ubuntu releases. For Ubuntu 12.04 the point releases are .2/.3/.4/.5 and the corresponding Ubuntu releases.


This is what I get 

```
$ hwe-support-status --verbose
You are not running a system with a Hardware Enablement Stack. Your system is supported until April 2023.


```

---

### Post by LHammonds on 2018-08-14
> **linuxyogi said:**
> I am using Ubuntu 18.04. Just doing the usual apt-get update/upgrade has updated my installation to 18.04.1.
That is expected.  The .1 is the first point release of 18.04.  They typically have 5 point releases over the lifespan of a particular LTS version.

> **linuxyogi said:**
> Am I using a LTS kernel ?
Type the following at a terminal:
```
lsb_release -a
```

You should get something like:
```
:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
```

You can see from the description that it identifies itself as Ubuntu 18.04.1 **LTS**.

LHammonds

---

### Post by #&amp;thj^% on 2018-08-14
I get the same.
```
hwe-support-status --verbose
You are not running a system with a Hardware Enablement Stack. Your system is supported until April 2023.

```
Just means you are running the  "GA (General Availability) stacks"

---

### Post by linuxyogi on 2018-08-14
> **LHammonds said:**
> That is expected.  The .1 is the first point release of 18.04.  They typically have 5 point releases over the lifespan of a particular LTS version.


Type the following at a terminal:
```
lsb_release -a
```

You should get something like:
```
:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
```

You can see from the description that it identifies itself as Ubuntu 18.04.1 **LTS**.

LHammonds

Yes but for example in Linux Mint which is based on LTS releases we can install a variety of kernels which may not be a LTS kernel. Thats why I ask if the kernel I am using is a LTS kernel or not.

---

### Post by linuxyogi on 2018-08-14
> **1fallen said:**
> I get the same.
```
hwe-support-status --verbose
You are not running a system with a Hardware Enablement Stack. Your system is supported until April 2023.

```
Just means you are running the  "GA (General Availability) stacks"

Got it / Thanks

---

