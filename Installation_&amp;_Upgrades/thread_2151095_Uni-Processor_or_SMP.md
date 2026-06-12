---
title: "Uni-Processor or SMP"
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by MichelleH on 2013-06-03
Is there a uniprocessor kernel download for Ubuntu? I am trying to run a couple of data acquisition cards and the drivers required will not work with a SMP kernel. When downloading the Ubuntu installation I do not see any option between the two. Is this a matter of choosing software or is it just dependent on what hardware you have on your machine?

---

### Post by Doug S on 2013-06-03
If your computer has just one CPU, then things should work fine. If your computer has multiple CPU's, but you want to run it using just one CPU, then you could boot using "maxcpus=1" (which I have never tried myself). Let us know, and maybe I will test "maxcpus=1" on my test computer via editing the grub options.

---

### Post by MichelleH on 2013-06-03
Yes the computer has multiple CPUs. I am fairly new to Linux so I'll have to look up how to boot from "maxcpus=1" but any information you could provide will be user.

---

### Post by Doug S on 2013-06-03
First save a copy of your original grub file, for possible restore later:```
sudo cp /etc/default/grub /etc/default/grub.original
```then edit the file and and add the boot command:```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 maxcpus=1"
```Note: the ipv6 part is specific to my system, because I don't run ipv6. And note you have to edit as sudo.
I always increase the timeout as well, so I have time to see the grub menu during boot:```
GRUB_TIMEOUT=10
```Then update the boot stuff (I do not recall the correct lingo):```
sudo update-grub
```Then re-boot```
sudo shutdown -r now
```Your system should be running with only 1 cpu. Kern.log entry:```
Jun  3 12:00:54 s15 kernel: [    0.177027] Brought up 1 CPUs
Jun  3 12:00:54 s15 kernel: [    0.177029] Total of 1 processors activated (6822.39 BogoMIPS).
```Normal Kern.log entry:```
Jun  3 11:52:25 s15 kernel: [    0.932514] Brought up 8 CPUs
Jun  3 11:52:25 s15 kernel: [    0.932516] Total of 8 processors activated (54576.83 BogoMIPS).
```Edit: Adding, when running with one processor, you should also see this in kern.log```
Jun  3 12:00:54 s15 kernel: [    0.004208] SMP alternatives: switching to UP code
```

---

### Post by MichelleH on 2013-06-04
I am a little confused on how to edit the grub file. If I am working through the desktop, do I open the grub.cfg file and add the line "maxcpus=1". If so is there anywhere inparticular in code where this should be added.

---

### Post by Cheesemill on 2013-06-04
You don't edit the crub.cfg file, you edit /etc/default/grub. You can do this by running the following command...
```
gksudo gedit /etc/default/grub
```

Find the line that begins with GRUB_CMDLINE_LINUX_DEFAULT and add maxcpus=1 between the quotes. Save the file and then run...
```
sudo update-grub
```
to regenerate your grub.cfg file with the new settings.

---

### Post by MichelleH on 2013-06-04
The procedure above worked perfectly. Thank you!

---

