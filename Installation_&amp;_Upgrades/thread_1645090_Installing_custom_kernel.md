---
title: "Installing custom kernel"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by palobicho on 2010-12-14
Hello Guys,

Im a old fashion Windows user ^^ so Im doing my best in order to understand all this world of kernel, compilation and operating system architecture which is Linux. Im not a newbie; but sometimes I loose a lot of time trying to do things, that at the end, are basic #-o..

Well, I subscribed today because I'm trying to install a custom Kernel into my Ubuntu 10. 
My newest kernel, the one who came with Ubuntu 10 is 2.6.35-23-generic. I tried to compile and install an older one (2.6.32.1), because I need this kernel to run in order to work with an application that doesn't support the last kernel, So Im forced to switch to and older kernel. I don't know at all if switching to and older version of kernel will crash my Linux environment. 

What I did was to follow the step by step guide from this site, I think Is quite good an easy reading:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
[http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)

Finally everything seemed to be okay. I updated grub and I acutally have the kernel displayed during booting. When I choose the older kernel, there is a Panic Error and linux doesn't boot. 
The error is quite long so I will just copy some of it:


[ ] CR2 0000000080b52380
[ ] ---[end trace 93d72a36b9146f22 ]---
[ ] Kernel panic - not syncing: Attempted to kill init!
[ ] Pid: 1, comm: swapper Tained: G     D    2.6.32.1-13102010 #1
[] Call Trace:
[ ] [] ? printk+0x1d/0x20
[ ] [] panic+0X48/0Xf3
[ ] [] do_exit+0X5cd/0X6e0
[ ] [] ? print_oops_end_marker+0X2f/0X40
[ ] [] oops_end+0X95/0Xd0
[ ] [] no_context+0Xbe/0X150
[ ] [] __bad_area_nosemaphore+0X90/0X130

there are a lot of numbers between the brackets, let me know if you need them. 

Thanks in advance!

---

### Post by 73ckn797 on 2010-12-14
One way to get an earlier kernel is from Synaptic Package Manager.

---

### Post by palobicho on 2010-12-14
Ok, but when I do a search: "2.6.32" I have the list of headers and images. Which one should I install? 

linux-headers-2.6.32-305
linux-headers-2.6.32-305-ec2
linux-image-2.6.32-305-ec2
linux-ec2-source-2.6.32

What does the ec2 means? or which of headers should I install? 

Once finished the installation should I update my grub or grub2? There are a lot of thing than just installing in Synaptic isn't? 

Thanks again for any help you could give me! ;)

---

### Post by 73ckn797 on 2010-12-14
You will have to read the info provided in the links of the kernel description(s). Synaptic will reconfigure Grub during installation.

I believe that you will need, as an example, linux-headers-###, linux-image-###, linux-headers-###-generic. ### being the particular version number.

Your particular needs seem to be something that I have not dealt with. The program you are wanting to run has not been specified. Search the forums for that program. Possibly someone has asked about it before.

You have not given a lot of information which would help answer your question.

A good search tool is: [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

### Post by palobicho on 2010-12-15
Hello!

I solved the problem. But was very very tricky. My actual kernel is 2.6.35-23-generic and Im running Ubuntu 10.10 . 

I tried, as I said, to install a custom kernel 2.6.32.1. Once I compiled the sources downloaded from the Official Website, the new (custom) kernel appeared at the grub (during the boot), so no problem, everything seemed to be working fine. I had this Panic Error that I mentioned above when I choose this kernel to boot (2.6.32.1). 

What I did was to compile in another machine, then bring back the .deb files and reinstall it. And that's it! .... the new custom kernel is working and booting without problems. I'm very afraid that the compiler that comes with Ubuntu 10.10 is the responsible of the problem. I'm very disappointed, so I'm switching to Debian now. 

Hope this could help someone!

---

