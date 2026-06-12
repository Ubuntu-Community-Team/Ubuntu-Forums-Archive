---
title: "PCI: Failed to allocate I/O resource #7:1000@10000"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by fgosse on 2007-04-21
Hi,

Since i 've update to feisty, I have a message during the boot (just before the usplash):

PCI: Failed to allocate I/O resource #7:1000@10000

what does it mean ?
What to do next ?

Thanks a lot

F.G

---

### Post by fgosse on 2007-04-30
No help ?

---

### Post by orphzirra on 2007-05-01
I have had the same error since upgrading from edgy to feisty.

May  1 14:23:10 laptop kernel: [    7.720391] PCI: Failed to allocate I/O resource #7:1000@10000 for 0000:00:1e.0

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)

Also, this doesn't have any overt effect on the machine.

---

### Post by fgosse on 2007-05-02
So, wait and see !!!

---

### Post by kdevil on 2007-05-19
I just upgraded my laptop to feisty, and got the same message - only it wouldn't boot at all on the 2.whatever-386 kernel (which was the default).  It only booted successfully after I made it use the 2.whatever-generic kernel.

---

### Post by nabla on 2007-05-30
I get the exact same message, I'm running a Dell Inspiron 6000 laptop.

---

### Post by KSU guy on 2007-08-09
I am getting that exact same message, and also running a Dell Laptop. It doesn't appear to cause any performance problems, though.

---

### Post by fgosse on 2007-11-02
No problem with gusty :)

---

