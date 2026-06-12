---
title: "Ubuntu 11.04 will not recognize ram"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by musahossein on 2011-09-29
Hi I installed Ubuntu on a Toshiba Satellite M35X. It has 4 Gigs of ram. But Ubuntu only reconizes 2 Gigs. I had Suse Linux installed before and it recognized 4 Gs,so why not Ubuntu? Any help would be greatly appreciated, thanks!

---

### Post by zvacet on 2011-09-30
**System>administration>synaptic **and in search box type linux-image and then find linux-image pae and install it.

---

### Post by musahossein on 2011-09-30
> **zvacet said:**
> **System>administration>synaptic **and in search box type linux-image and then find linux-image pae and install it.
did it. The restarted the computer, checked system. Still shows 1.9G. Synaptic-package manager shows all -image as being installed. Help!

---

### Post by pkg9991 on 2011-09-30
is your RAM functioning properly check with other OS

---

### Post by Blasphemist on 2011-09-30
zvacet didn't fully explain. The PAE kernel is the 32 bit kernel that allows for having 4GB or more memory. This page tells you how to install it and why it may not be. You can see that kernel detail on the grub screen to verify that this is the issue. [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

I think you'll also need to do this command to update grub to show the new kernel.
```
sudo update-grub
```

---

### Post by musahossein on 2011-09-30
> **Blasphemist said:**
> zvacet didn't fully explain. The PAE kernel is the 32 bit kernel that allows for having 4GB or more memory. This page tells you how to install it and why it may not be. You can see that kernel detail on the grub screen to verify that this is the issue. [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

I think you'll also need to do this command to update grub to show the new kernel.
```
sudo update-grub
```

Did the -grub part. But a search of the Synaptic Pkg manager does not list any pae, or 
linux-image-generic-pae

---

### Post by musahossein on 2011-09-30
> **pkg9991 said:**
> is your RAM functioning properly check with other OS
I only have ubuntu 11.04 loaded on this machine. Before it was suse and it detected 4G fine.

---

### Post by dFlyer on 2011-09-30
> **musahossein said:**
> Hi I installed Ubuntu on a Toshiba Satellite M35X. It has 4 Gigs of ram. But Ubuntu only reconizes 2 Gigs. I had Suse Linux installed before and it recognized 4 Gs,so why not Ubuntu? Any help would be greatly appreciated, thanks!

Check your memory and if good, install the pae kernel.

---

### Post by MAFoElffen on 2011-09-30
> **dFlyer said:**
> Check your memory and if good, install the pae kernel.
[EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE?action=fullsearch&context=180&value=linkto%3A%22EnablingPAE%22")

---

### Post by kaniko on 2012-05-01
Hello, I've installed Ubuntu 11.04  64 bits

$ uname -a 


Linux MyComputer 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

$ free -m 

             total       used       free     shared    buffers     cached
Mem:          3646       3574         72          0        107       1732
-/+ buffers/cache:       1733       1913
Swap:         1950          0       1950


$ sudo lshw -C memory


 *-memory
       description: System Memory
       physical id: 1000
       slot: System board or motherboard
       size: 8GiB


I don't know what is the problem, Could anybody help me. I searched a lot, but with the Ubuntu 64 bits it shouldn't be a problem.

Thanks in advance

---

