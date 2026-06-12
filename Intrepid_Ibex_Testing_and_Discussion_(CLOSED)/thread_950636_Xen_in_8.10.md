---
title: "Xen in 8.10"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by johnwards on 2008-10-17
Hello,

I am trying to setup Xen Desktop in 8.10.

I have a clean 8.10 installation and have managed to install ubuntu-xen-desktop and boot into the new kernel it installs.

It provides a server based kernel.

However reading the description of xen-hypervisor-3.3 in synaptic it says that I have to compile my own kernel and a sample config and instructions on how to build it will be found in the xen-docs package. However I can't see any config or instructions.

xend is not started and when I try to I get:

```
grep: /proc/xen/capabilities: No such file or directory
```

Which I am guessing is because my kernel doesn't have the hypervisor in it.

My kernel is:
```
2.6.27-7-server #1 SMP Tue Oct 14 19:36:09 UTC 2008 i686 GNU/Linux
```

Thanks..

---

### Post by Black Raven on 2008-10-18
I have exactly the same problem... Is there any suggestions how to solve it?

---

### Post by exiztone on 2008-10-18
Same here. I'm assuming that the 'linux-server' package is a placeholder for a Xen compiled kernel. I'm having such a nightmare compiling and running the kernel source from xen.org so I'm really hoping this package will be fixed soon. :KS

---

### Post by johnwards on 2008-10-19
i think the solution is to use kvm rather than xen.

kvm seems to be the supported/ prefered way to do virtualization in ubuntu.

i was planning to test it on my box this weekend but it doesn't have the virt support, so i will have to wait until monday at work.

---

### Post by bedge on 2008-10-19
Xen is the top contender in open source virtualization and it's only a matter of time until the xen kernels show up in the repositories.
That's the whole reason I installed 8.10. ( 2.6.27 is the first kernel to support 64 bit guest OSs.) I had assumed the xen kernels were already there.

...I just wish that they'd hurry up :-)

---

### Post by wgrant on 2008-10-19
The normal kernels support Xen **domU** functionality. We do not and will not have a dom0 kernel in 8.10.

---

### Post by AreonEpta on 2008-10-19
> **wgrant said:**
> The normal kernels support Xen **domU** functionality. We do not and will not have a dom0 kernel in 8.10.
So then what would be the best choice for Intrepid Host, Windows XP guest for gaming and software testing/development, Mr. Developer?

---

### Post by wgrant on 2008-10-19
> **AreonEpta said:**
> So then what would be the best choice for Intrepid Host, Windows XP guest for gaming and software testing/development, Mr. Developer?

The preferred Ubuntu virtualisation setup is KVM.

---

### Post by lckarssen on 2008-10-19
I've run into the same problem. 
So, KVM is the preferred virtualisation method, but if I'm correct, KVM requires hardware virtualisation support in the CPU/main board, whereas Xen does not. I'm testing Intrepid (8.10) on an older box here without said support. What would be the best solution? Work with (k)Qemu instead of KVM, or try to compile a Xen dom0 kernel myself (possibly using the kernel config file from a 8.04 kernel)?

---

### Post by bedge on 2008-10-19
> The normal kernels support Xen domU functionality. We do not and will not have a dom0 kernel in 8.10.
__________________
William Grant
Ubuntu Developer 

In that case, what is one supposed to use for the dom0 kernel?

The standard kernel has no /proc/xen/capabilities.

---

### Post by exiztone on 2008-10-19
> **wgrant said:**
> The normal kernels support Xen **domU** functionality. We do not and will not have a dom0 kernel in 8.10.

This is really disappointing. I'm not able to use KVM because of their Intel VT requirements. Do you have any suggestions for getting a working dom0 kernel?

I do hope the Ubuntu team would reconsider this decision. Xen isn't dead yet :-)

---

### Post by wgrant on 2008-10-19
Canonical apparently doesn't wish to support Xen, so it's up to the community to have it working. The amount of work involved in porting the Xen patches from older kernels isn't exactly small! You could use a Hardy dom0 kernel, perhaps, but Ubuntu 8.10 is not intended to be a dom0 without custom kernels. I believe that Debian is making a similar decision for Lenny.

I use kqemu on my hardware that doesn't support KVM. With DKMS it's particularly easy to install kqemu now.

---

### Post by lckarssen on 2008-10-19
It's a pitty that there's no dom0 kernel planned. So, since I've been using qemu up till now, I'll just continue doing that. 
Thanks for you replies, wgrant.

---

### Post by dbaxps on 2008-10-25
Regardless, you wrote that generic kernel has normal Xen DomU functionality.
This functionality won't understand paravirtual guests.
It's just KVM and nothing else.

---

### Post by wgrant on 2008-10-25
> **dbaxps said:**
> Regardless, you wrote that generic kernel has normal Xen DomU functionality.
This functionality won't understand paravirtual guests.
It's just KVM and nothing else.

Why exactly would a domU understand paravirtual guests? A domU *is* generally a paravirtual guest.

---

### Post by wroopy on 2008-10-26
I need to allocate PCI-devices to my guest OS. As I've understand it only XEn supports this and KVM does not (at least not yet).
How ta handle that if there will be no Dom0 support in intrepid?
Is there someone in the community that is working on dom0 support  for Intrepid?

---

