---
title: "VMware 6.5 install Karmic Host"
date: 2009-05-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tonyric on 2009-05-31
When attempting to install and run VMware 6.5.2 I get the following error when compiling modules:

C header files matching your running kernel not found. Refer to your distributions documentation for installation instructions.

I have installed the headers (build-essential) for the running kernel and even tried linux-source which has worked in the past for the same problem. Anyone else have this problem?

---

### Post by tonyric on 2009-06-01
No one is having problems? Or has no one tried Workstation 6.5.x?

---

### Post by psyke83 on 2009-06-01
> **tonyric said:**
> No one is having problems? Or has no one tried Workstation 6.5.x?

Karmic is using a release candidate kernel (based off 2.6.30-rc6, which is already out of date). Don't expect any applications that require a compiled third-party kernel module to work, until the kernel is finalized and the software is updated to support it.

---

### Post by Astrak on 2009-08-03
Maybe I am late, but tried recently to install vmware workstation 6.5.2 and had some trouble compiling the kernel 2.6.31 modules.

This vmware community thread helped me compile them, but now I am having a bit of trouble with the keyboard and mouse grab (this issue is also mentioned in the thread below).
[http://communities.vmware.com/thread/221724](http://communities.vmware.com/thread/221724)

I am trying now to solve these keyboard issues :confused:. Help would be welcome.

Best Regards.

---

### Post by xebian on 2009-08-03
> **Astrak said:**
> Maybe I am late, but tried recently to install vmware workstation 6.5.2 and had some trouble compiling the kernel 2.6.31 modules.

This vmware community thread helped me compile them, but now I am having a bit of trouble with the keyboard and mouse grab (this issue is also mentioned in the thread below).
[http://communities.vmware.com/thread/221724](http://communities.vmware.com/thread/221724)

I am trying now to solve these keyboard issues :confused:. Help would be welcome.

Best Regards.

I don't have $185(VMWare) so I can't help you here.  But may I suggest VirtualBox 3.0.2?

---

### Post by tonyric on 2009-08-03
> **xebian said:**
> I don't have $185(VMWare) so I can't help you here.  But may I suggest VirtualBox 3.0.2?

While on the surface this may seem like a good suggestion, but, in reality, it isn't.

---

### Post by darco on 2009-08-03
In the VMWare forums, they have a patch that may work for your kernel issues....I needed it for my .30 kernel.

darco

---

### Post by wayne_cat on 2009-08-03
> **Astrak said:**
> Maybe I am late, but tried recently to install vmware workstation 6.5.2 and had some trouble compiling the kernel 2.6.31 modules.

This vmware community thread helped me compile them, but now I am having a bit of trouble with the keyboard and mouse grab (this issue is also mentioned in the thread below).
[http://communities.vmware.com/thread/221724](http://communities.vmware.com/thread/221724)

I am trying now to solve these keyboard issues :confused:. Help would be welcome.

Best Regards.

Well ... it is not a solution ... only a workaround until they have found the problem.

You can enable VNC in the VMware configuration and access the system with a VNC clients (i.e. viangre).

---

