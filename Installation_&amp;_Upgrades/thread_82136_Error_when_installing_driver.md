---
title: "Error when installing driver"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by JollyRoger on 2005-10-25
I was trying to install a driver for my ethernet controller, and I know you guys won't know much about the driver or anything, but I was wondering if any of you had an idea of what I should do..:

+++ Install mode: User
+++ Driver version: 8.28.1.2 (beta) (Sep-29-2005)
+++ Kernel version 2.6.12-9-386
+++ smp_count=0
+++ cpu_number=1
+++ kernel_machine=i686
+++ Architecture: i386
+++ Make not found
+++ Mismatch!!! Kernel:3.4.5 != gcc:4.0.2

---

### Post by daller on 2005-12-01
[QUOTE=JollyRoger]I was trying to install a driver for my ethernet controller, and I know you guys won't know much about the driver or anything, but I was wondering if any of you had an idea of what I should do..:

+++ Install mode: User
+++ Driver version: 8.28.1.2 (beta) (Sep-29-2005)
+++ Kernel version 2.6.12-9-386
+++ smp_count=0
+++ cpu_number=1
+++ kernel_machine=i686
+++ Architecture: i386
+++ Make not found
+++ Mismatch!!! Kernel:3.4.5 != gcc:4.0.2[/QUOTE]

You have to install "make" and "gcc":

sudo apt-get install make gcc

---

### Post by akiro.yamamoto on 2005-12-01
Search synaptic for build-essential and you may have to install gcc-3.4 as well to get the driver to compile and install..I think it's on the install cd as well..
Regards

---

