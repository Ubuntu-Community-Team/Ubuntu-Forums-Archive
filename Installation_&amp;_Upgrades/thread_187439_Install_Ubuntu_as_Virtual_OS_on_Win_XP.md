---
title: "Install Ubuntu as Virtual OS on Win XP?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by neoaddict on 2006-06-03
Since I can't fully abandon Windows yet and having a dual-boot system is inefficient, how would I install Ubuntu as a virtual operating system under Windows XP?

Thanks.

---

### Post by skaboss on 2006-06-03
Have you tried vmware ?
But why do you say dual boot is inefficient ?

---

### Post by neoaddict on 2006-06-03
I want to have Ubuntu and Windows app side by side, and VMWare won't allow you to use your original NTFS partition, plus my Windows XP is OEM.

---

### Post by neoaddict on 2006-06-04
Any suggestions?

---

### Post by rcarring on 2006-06-04
Go to easyvmx.com and create your vm.

Download vmplayer and install it.

Boot the vm with your alternate cd (NOT live) and install Ubuntu.

You will need:

128MB ram
SCSI 10GB hard file (these start very small and grow)
Floppy disk drive
CD Rom Drive
Sound
1 CPU

If you are lucky you will not need to install vmware tools into guest system. If you do need them then:

Install gcc when the system is booted, and then add the vmware tools.

Not sure if you can do this in vmplayer though.

---

### Post by .t. on 2006-06-04
Or you could try the new VMWare Server beta, which is much easier to configure.

---

### Post by neoaddict on 2006-06-04
I'll try EasyVMX once I get my parents to buy the 1 GB RAM chip that I've been saving up for.

I'll post when I try it.

---

