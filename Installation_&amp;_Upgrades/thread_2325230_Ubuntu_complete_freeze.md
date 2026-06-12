---
title: "Ubuntu complete freeze"
date: 2016-05-20
forum: Installation &amp; Upgrades
---

### Post by giovilix47 on 2016-05-20
Hi, I'm writing this post because I've a problem which appeared on Ubuntu 14.04.4 LTS and still happen on Ubuntu 16.04 LTS, both 32 bit and 64 bit. Indeed, after some time (without any criterion) my PC freezes completely, and this makes impossible to use the mouse and to open the shell, so I always have to shut down it with the power button. This thing happens independently on what I'm doing with my PC, but it happens more frequently when I'm watching Youtube videos. When I switch on my PC, it doesn't report any error, neither in the log. 
If this can be helpful, my PC is an Acer ES1-512-P2C7.
I hope you will help me.

---

### Post by user1397 on 2016-05-20
Are you dual booting this PC with Windows or just use ubuntu on it?

---

### Post by vanadium on 2016-05-20
This might be failing hardware. Keep an eye on it with dmesg. In Ubuntu 16, you can have dmesg continuously display kernel mesages with the command "dmesg -w" (or "dmesg -wH" for more human readable time stamps). This option is not there in older versions of dmesg, but you can use "watch dmesg" to have a refresh every two seconds.

---

### Post by RobGoss on 2016-05-20
Hello and welcome, Not knowing what the specs are for your machine makes it just a bit harder determining what may be causing your problem, so after reading your post it seems your having this problem with distributions that may not be suitable for that machine in question

Seeing your machine is constantly freezing it may be because you need a lighter version of Ubuntu maybe [Lubuntu ]("http://lubuntu.net/")or [Kubuntu]("http://www.kubuntu.org/") these distros require less to run and make work better on your machine.

When posting and asking for help with your machine it's best to provide the specs in order to get the help you need

---

### Post by giovilix47 on 2016-05-21
Hi, and thanks for the replies!

Specs of my PC: 

CPU: Intel® Pentium(R) CPU N3540 @ 2.16GHz × 4
Graphic Card: Intel® Bay Trail x86/MMX/SSE2
RAM: 3,8 GiB DDR3 L Memory
Hard Disk: 1000 GB HDD

My PC doesn't run Ubuntu and Windows at the same time, just Ubuntu.

---

### Post by oldfred on 2016-05-22
You mention bay trail:

Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by RobGoss on 2016-05-22
> **giovilix47 said:**
> Hi, and thanks for the replies!

Specs of my PC: 

CPU: Intel® Pentium(R) CPU N3540 @ 2.16GHz × 4
Graphic Card: Intel® Bay Trail x86/MMX/SSE2
RAM: 3,8 GiB DDR3 L Memory
Hard Disk: 1000 GB HDD

My PC doesn't run Ubuntu and Windows at the same time, just Ubuntu.

Have you try a lighter distribution of Ubuntu it may preform better on that machine like Lubuntu or Kubuntu, it worth a try this way if it does work better you know that Ubuntu 16.04 maybe a little to much for your machine. Looking at the specs you seems to have more then enough Ram but I'm uncertain about your graphic card, [COLOR=#000000]none of my machines use **Bail trial** so I'm not that familiarized whit that type of graphic card but that may be a factor[/COLOR]

---

### Post by giovilix47 on 2016-06-02
Hi everybody. I can finally confirm that what oldfred posted works fine.
Here you can discover (read the last paragraph) how to add permanently a Kernel parameter: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

The parameter I added is: intel_idle.max_cstate=0
It works perfectly for me, but if it still freezes you can use: intel_idle.max_cstate=1

---

