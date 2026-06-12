---
title: "Kernel Upgrade: Bad page state in process 'Xorg'"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Cappy on 2007-03-02
Here is my problem -
Recently my kernel was upgraded automatically and my computer basically froze during it. 
Once I rebooted synaptic told me to run a dpkg --configure -a (or something). 
I typed it in and it said a package was broken and needed to be reinstalled. My X then crashed and my computer rebooted itself.
Now, the problem is that my computer has become unstable and sometimes crashes and I've received this error in my console:
Bad page state in process 'Xorg'

I found my problem here:
[http://www.tutorials-blog.com/linux-development/kernel-page-153149/]("http://www.tutorials-blog.com/linux-development/kernel-page-153149/")
It basically says to force the kernel upgrade even when packages fail. I wasn't having any trouble at all before I did this kernel upgrade. Everything worked perfectly.

So, my question is, should I upgrade or downgrade? I'll do whatever is easier but I have
no idea how to do either in this situation.
I found a guide on building a new kernel [http://howtoforge.com/roll_a_kernel_debian_ubuntu_way]("http://howtoforge.com/roll_a_kernel_debian_ubuntu_way")
but I don't want to risk the OS when I don't even know if it will help my situation.

---

### Post by ffxr on 2007-03-02
cant you boot into the old kernel by selecting it in grub..?

you could also try reinstalling the new kernel by removing and reinstalling it from aptitude..

[ also i compiled the 2.6.20 using that link and it was a cince and have had little or no issues.. ]

---

### Post by Cappy on 2007-03-02
Thank you for the speedy reply! I took your advice and reinstalled the kernel image + headers and this time I received no errors =)

A quick guide for anyone with my same problem:
I found out my kernel version (that is currently running) using this command (or you can just look on your GRUB boot): 
$ uname -r
2.6.17-11-generic

I then searched Synaptic for "2.6.17-11" which brought up all of the packages I needed. I just clicked re-install next to the ones that were "installed". I got no errors this time =)

Thanks again =)

---

