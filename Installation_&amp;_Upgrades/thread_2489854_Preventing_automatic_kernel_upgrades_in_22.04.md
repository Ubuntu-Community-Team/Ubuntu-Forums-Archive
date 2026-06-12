---
title: "Preventing automatic kernel upgrades in 22.04"
date: 2023-08-11
forum: Installation &amp; Upgrades
---

### Post by hunnypuppy on 2023-08-11
Hi,

I'm running ubuntu 22.04 on ec2 and it's running Linux 6.2.0-1009-aws kernel which I believe is a aws specific kernel for hosted instances. Right now everything is set to automatically upgrade using unattended upgrades.

My question is how do I stop the kernel for upgrading but still have everything else upgrade? Is a way to stop the kernel from being upgraded, both automatically and when I run apt upgrade? (i.e. it should only upgrade when I force it to manually install a new kernel)?

TIA

---

### Post by ian-weisser on 2023-08-11
> **hunnypuppy said:**
> 
My question is how do I stop the kernel for upgrading but still have everything else upgrade? 


One way is to learn the name of your kernel package, then

```

sudo apt-mark hold <package_name>      # stop upgrading
sudo apt-mark unhold <package_name>    # resume upgrading

```



Another way is to learn the name of your kernel *metapackage* (which is what pulls in newer kernel packages), then

```

sudo apt remove <metapackage_name>      # stop upgrading
sudo apt install <metapackage_name>     # resume upgrading

```

Be sure to keep track of which method you use. Write it down -- you are unlikely to recall the details when you need them later.

You are likely to need to resume updating someday: Some security update. Some other requirement. Some other bug.

Many kernel upgrades are security patches. It's not a great idea to skip those. But you asked.

---

### Post by hunnypuppy on 2023-08-13
Thanks. I believe the package name is ```
linux-image-6.2.0-1009-aws
```. I was also reading that there are other "related" packages that need to be stopped from being installed (like headers and another I one I read on stackoverflow but couldn't figure out what it was). Is that required and if so how I find which are the related packages?

Also how do I learn which kernel *metapackage* is installing these updates?

---

### Post by deadflowr on 2023-08-13
> Also how do I learn which kernel metapackage is installing these updates?
Use dpkg command line to help with that.
```
dpkg -l | grep linux
```
For aws kernels it should be linux-aws and its dependencies linux-image-aws and linux-headers-aws.

The linux-aws package does not have to be installed, but the linux-image-aws and the linux-headers-aws would be.
The actual updates are directly tied to the linux-image-aws and linux-headers-aws packages.
Since those two are always updated to depend on the latest kernels that Ubuntu packages.

So putting a hold on those will prevent the kernel updates.


The linux-aws package is a simple package that installs both of those easily.
Removing it won't affect the other two, but removing either of the other two will also force the removal of it.

And there is always a good chance you don't have the linux-aws package installed anyway.


Confused?

---

### Post by hunnypuppy on 2023-08-13
Okay, so you're right I don't see linux-aws installed but I do see a linux-aws-6.2-headers-6.2.0-1009 installed and linux-headers-aws

```

ii  binutils-x86-64-linux-gnu        2.38-4ubuntu2.3                         amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-aws-6.2-headers-6.2.0-1009 6.2.0-1009.9~22.04.3                    all          Header files related to Linux kernel version 6.2.0
ii  linux-base                       4.5ubuntu9                              all          Linux image base package
ii  linux-headers-6.2.0-1009-aws     6.2.0-1009.9~22.04.3                    amd64        Linux kernel headers for version 6.2.0 on 64 bit x86 SMP
ii  linux-headers-aws                6.2.0.1009.9~22.04.3                    amd64        Linux kernel headers for Amazon Web Services (AWS) systems.
ii  linux-image-5.4.0-1018-aws       5.4.0-1018.18                           amd64        Linux kernel image for version 5.4.0 on 64 bit x86 SMP
ii  linux-image-6.2.0-1009-aws       6.2.0-1009.9~22.04.3                    amd64        Signed kernel image aws
ii  linux-modules-5.4.0-1018-aws     5.4.0-1018.18                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-6.2.0-1009-aws     6.2.0-1009.9~22.04.3                    amd64        Linux kernel extra modules for version 6.2.0 on 64 bit x86 SMP

```

So my question here is:
1. Without linux-aws will it still upgrade my kernel?
2. Given the above I see a lot of other linux-aws stuff, does that affect it?
3. What's my best strategy here to hold my kernel and related packages?

TIA

---

### Post by hunnypuppy on 2023-08-26
Any advice on the above here?

---

### Post by ian-weisser on 2023-08-26
Advice: Run "apt show <package_name>" on the packages that you have questions about.

Review the description and the dependencies of each.

Since you are jumping off the treadmill of frequent automated kernel updates, you will need to manually upgrade the correct packages.
That means you must know the purpose of each kernel-related package and the tree of dependencies. Else your first manual upgrade might mangle your system.

---

### Post by hunnypuppy on 2023-08-28
[FONT=arial]Thanks. I also came across this from [Quora]("https://www.quora.com/How-can-I-stop-Ubuntu-from-updating-the-kernel-automatically").

> [COLOR=#282829]To achieve this, you can use the "unattended-upgrades" package, which allows you to control the automatic updates for your system. You can install it by running the following command in your terminal: "sudo apt-get install unattended-upgrades". Once you have installed it, you can then edit the configuration file located at "/etc/apt/apt.conf.d/50unattended-upgrades" and comment out the line that says "Unattended-Upgrade::Kernel "yes";". This will prevent the package from automatically updating the kernel.[/COLOR]

How accurate is this? Asking because I can't find any reference to [COLOR=#282829]**Unattended-Upgrade::Kernel** in the files or anywhere. Does anyone know about this?

Alternatively I came across [this]("https://askubuntu.com/questions/1131060/how-to-exclude-kernel-updates-from-unattended-upgrades") and it suggested to block all updates starting with **linux-** . Is there a downside to blocking all **linux-** packages?[/COLOR][/FONT]

---

### Post by hunnypuppy on 2023-08-30
> **hunnypuppy said:**
> [FONT=arial]Thanks. I also came across this from [Quora]("https://www.quora.com/How-can-I-stop-Ubuntu-from-updating-the-kernel-automatically").



How accurate is this? Asking because I can't find any reference to [COLOR=#282829]**Unattended-Upgrade::Kernel** in the files or anywhere. Does anyone know about this?

Alternatively I came across [this]("https://askubuntu.com/questions/1131060/how-to-exclude-kernel-updates-from-unattended-upgrades") and it suggested to block all updates starting with **linux-** . Is there a downside to blocking all **linux-** packages?[/COLOR][/FONT]

Anyone have any insight or thoughts about the above? Calling the linux guru's. This looked like a fairly basic question to me but it's turning out to be a lot harder than I thought it would be :(

---

