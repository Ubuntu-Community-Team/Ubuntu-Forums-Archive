---
title: "Upgrading The Kernel In 14.04"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by grace3 on 2016-04-03
Hello,

I think I read somewhere that it's possible to upgrade the kernel in Ubuntu distros. If this is true, how do I do it? Also, what are the risks; and has anyone actually done it successfully?

---

### Post by grahammechanical on 2016-04-03
All supported Ubuntu releases get security fixes for the Linux kernel. That action can be thought of as upgrading the kernel. Newer kernels come with newer releases of Ubuntu and for LTS releases the newer kernels come with the LTS point releases. For example, Ubuntu 14.04 just received the 14.04.4 release and that version of 14.04 would have had the hardware enablement stack (including kernels) that came with Ubuntu 15.10. To find out what kernel you are using run this command

```
uname -a
```

If it is kernel 4.2 then you already have the latest upgraded kernel that the developers think is safe to release on to the trusting Ubuntu user. There is a way to install the 15.10 (wily) enablement stack and also way to install even newer (less tested) Linux kernels. First, we find out what you are now on and if you want to go further and install either a later hardware enablement stack or a very new kernel.

Regards.

---

### Post by grace3 on 2016-04-05
> **grahammechanical said:**
> All supported Ubuntu releases get security fixes for the Linux kernel. That action can be thought of as upgrading the kernel. Newer kernels come with newer releases of Ubuntu and for LTS releases the newer kernels come with the LTS point releases. For example, Ubuntu 14.04 just received the 14.04.4 release and that version of 14.04 would have had the hardware enablement stack (including kernels) that came with Ubuntu 15.10. To find out what kernel you are using run this command

```
uname -a
```

If it is kernel 4.2 then you already have the latest upgraded kernel that the developers think is safe to release on to the trusting Ubuntu user. There is a way to install the 15.10 (wily) enablement stack and also way to install even newer (less tested) Linux kernels. First, we find out what you are now on and if you want to go further and install either a later hardware enablement stack or a very new kernel.

Regards.

```
I'm on me@me-5520:~$ uname -a
Linux me-5520 3.19.0-56-generic #62~14.04.1-Ubuntu SMP Fri Mar 11 11:03:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
me@me-5520:~$ 

```

I'd like to install the newest kernel I can.

Thanks

---

### Post by kansasnoob on 2016-04-05
The 3.19 series kernel is Trusty-LTS-Vivid and it's supported until August of this year:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

When you reach HWE EOL the update manager will notify you that you need to upgrade to the Xenial HWE stack. I try to avoid this by using the original LTS kernel series which is what you get if you install with the archived 14.04.1 iso.

---

### Post by grace3 on 2016-04-05
Thanks for the reply. I'd still like to learn how to upgrade the kernel manually please.

---

### Post by sammiev on 2016-04-05
> **grace3 said:**
> Thanks for the reply. I'd still like to learn how to upgrade the kernel manually please.

At your own risk and [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") is where I get them. Newer ones at the bottom.

I usually download them into the Downloads directory without any other Deb files.

Then run from Terminal:

```
cd ~/Downloads/
```

```
sudo dpkg -i linux*.deb
```

---

### Post by Bucky Ball on 2016-04-06
Or you can just double click the .deb file and it will open Software Centre.

If you want to run the latest possible kernel, why not run the latest possible release that's known to run with it, but is not released yet, 16.04?

Chuck that kernel into 14.04 but don't get a shock if things go bang, fizzle, pop.

The only good reason I can think of for installing the latest kernel (not related to your install) is if it handles problematic hardware better than the kernel you're already using. The only other reason is curiousity and the learning curve. You may need to put some time aside to assess the damage and fix, if required, or be prepared to drop back to a 'known to work' kernel if things go pear-shaped.

---

