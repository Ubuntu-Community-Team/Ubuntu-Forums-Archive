---
title: "How to install kernel-image-2.4.27-2-686-smp"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by Kobold3012 on 2010-01-30
[FONT=Times New Roman][SIZE=3]I want to install package kernel-image-2.4.27-2-686-smp, but when i use terminal to install , write **sudo apt-get install kernel-image-2.4.27-2-686-smp** but **couldn't find this packag**e. 
In my synaptic i can't find this package to install.
I downloaded from [http://packages.ubuntu.com](http://packages.ubuntu.com) this package kernel-image-2.4.27-2-686-smp_2.4.27-12_i386.deb ,when i install , to appear error: "dependency is not satisfiable: initrd-tools", i downloaded this package initrd-tools and install but appear this error:"dependency libdevmapper1.02", in my synaptic i saw this package libdevmapper1.02 already installed.
Please tell me how to install package  **kernel-image-2.4.27-2-686-sm**p from terminal or from synaptic.[/SIZE][/FONT]??

---

### Post by oldos2er on 2010-01-30
Which version of Ubuntu are you running?

---

### Post by Kobold3012 on 2010-01-31
> **oldos2er said:**
> Which version of Ubuntu are you running?

I use Ubuntun DVD 9.10 , but i don't know what does this error? I can't install this package?

---

### Post by 73ckn797 on 2010-01-31
That kernel is for the Dapper 6.06 version which will not work in Karmic 9.10. That is why you cannot find it in Synaptic or via apt-get.

---

### Post by Kobold3012 on 2010-02-01
> **73ckn797 said:**
> That kernel is for the Dapper 6.06 version which will not work in Karmic 9.10. That is why you cannot find it in Synaptic or via apt-get.

It's that mean, in ubuntu 9.10 can't install that kernel ? Or use other way to install that kernel? Tell me ,plz

---

### Post by 73ckn797 on 2010-02-01
> **Kobold3012 said:**
> It's that mean, in ubuntu 9.10 can't install that kernel ? Or use other way to install that kernel? Tell me ,plz
No. That kernel is for the Dapper 6.06 version which will not work in Karmic 9.10. That is why you cannot find it in Synaptic or via apt-get.

I looked it up and it applies to Dapper Drake 6.06. What in particular did you want it for?

---

### Post by Kobold3012 on 2010-02-03
> **73ckn797 said:**
> No. That kernel is for the Dapper 6.06 version which will not work in Karmic 9.10. That is why you cannot find it in Synaptic or via apt-get.

I looked it up and it applies to Dapper Drake 6.06. What in particular did you want it for?

Thanks ! I want to install kernel for Enabling Multiple CPUs (SMP) i read it in a book? With Karmic 9.10 how to Enable Multiple CPUs?

---

### Post by oldos2er on 2010-02-03
SMP should work by default in 2.6.xx kernels.

---

### Post by Kobold3012 on 2010-02-03
> **oldos2er said:**
> SMP should work by default in 2.6.xx kernels.

By default this kernels 2.6.x.x already install? How can start it?

---

### Post by adam814 on 2010-02-03
You don't have to do anything to make it work.  It just will.  If you don't believe it this command will show you how many CPUs are in use on your system:
```
cat /proc/cpuinfo | grep processor | wc -l
```

---

