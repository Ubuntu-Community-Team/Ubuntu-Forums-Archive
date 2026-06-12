---
title: "Kernel dissappeared after install?"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sandertje on 2010-04-12
Hi,

Today, my kernel was being updated to linux-image-2.6.32-20-generic. When I rebooted, grub didnt show 2.6.32-20, only 2.6.32-19 and 2.6.32-16. When I tried to see in synaptic whether 2.6.32-20 was installed, i couldnt find it. Manually trying to download it resulted in this error: 

```
Package linux-image-2.6.32-20-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-image-2.6.32-20-generic has no installation candidate
```

I need it to fix my alsa drivers (since I dont have sound through my headphones), as outlined in [this thread]("http://ubuntuforums.org/showthread.php?t=1427902"). 

I've tried updating grub, but to no avail. I'm using 10.04. 

Thanks in advance!

---

### Post by mikewhatever on 2010-04-12
What version of Ubuntu are you running? What's the output of the following:

aptitude search linux-image

---

### Post by Sandertje on 2010-04-12
I'm using 10.04 lucid. 

This is the output of the command
```

p   linux-image                     - Generic Linux kernel image.               
v   linux-image-2.6                 -                                           
p   linux-image-2.6.31-10-rt        - Linux kernel image for version 2.6.31 on I
i   linux-image-2.6.32-16-generic   - Linux kernel image for version 2.6.32 on x
i   linux-image-2.6.32-19-generic   - Linux kernel image for version 2.6.32 on x
p   linux-image-2.6.32-20-virtual   - Linux kernel image for version 2.6.32 on x
p   linux-image-2.6.32-304-ec2      - Linux kernel image for version 2.6.32 on x
p   linux-image-ec2                 - Linux kernel image for ec2 machines       
pB  linux-image-generic             - Generic Linux kernel image                
p   linux-image-preempt             - Linux kernel image for Low Latency Servers
p   linux-image-rt                  - Realtime (RT) Linux kernel image          
p   linux-image-server              - Linux kernel image on Server Equipment.   
p   linux-image-virtual             - Linux kernel image for virtual machines 


```

The funny thing is that linux-headers-lbm-2.6.32-20-generic and linux-headers-2.6.32.20-generic ARE installed. Only the linux-image is missing.

---

### Post by florus on 2010-04-12
It would help if you posted in the correct forum - Lucid Lynx Testing and Discussion in the Development and Programming section.

---

### Post by mikewhatever on 2010-04-12
Was that an upgrade or a clean install? Can you post your sources list.

gedit /etc/apt/sources.list

---

### Post by sisco311 on 2010-04-12
linux-image-2.6.32-20-generic was removed from the repos, see:
[thread]1452744[/thread]

---

### Post by overdrank on 2010-04-12
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by ronparent on 2010-04-12
Linux-image-2.6.32-20-generic is back in the repos. Seems to now be working fine!

---

### Post by Sandertje on 2010-04-13
Yeps, installed :-). Thread can be closed :-).

---

### Post by ranch hand on 2010-04-13
You could just mark it solved (under thread tools at the top of the page).

---

