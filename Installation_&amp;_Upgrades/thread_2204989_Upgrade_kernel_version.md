---
title: "Upgrade kernel version"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by sombrancelha on 2014-02-11
Hello,

I'm running precise, with kernel 3.2.0-53-generic. I'd like to upgrade it to 3.10, which according to [Wikipedia]("https://en.wikipedia.org/wiki/Linux_kernel#Maintenance"), is the latest long-term stable release. From [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), I see that Linux 3.10 is associated with Saucy. (v3.10.29) - is that a problem?

Also, is the process as simple as downloading the *.deb's and installing them? What are the potential problems?

---

### Post by slickymaster on 2014-02-11
> **sombrancelha said:**
> Hello,

I'm running precise, with kernel 3.2.0-53-generic. I'd like to upgrade it to 3.10, which according to [Wikipedia]("https://en.wikipedia.org/wiki/Linux_kernel#Maintenance"), is the latest long-term stable release. From [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), I see that Linux 3.10 is associated with Saucy. (v3.10.29) - is that a problem?

No, no problem whatsoever.
Canonical has recently updated Precise into version 12.04.4, shipping it with kernel 3.11, which is the Kernel running by default on Ubuntu 13.10. 

> **sombrancelha said:**
> Also, is the process as simple as downloading the *.deb's and installing them? What are the potential problems?

Actually, the process is quite simple. From [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.10.3-saucy/"), download the linux-headers file that ends with “all.deb”, the linux-headers file that ends with “i386.deb” or “amd64.deb” _depending upon your computer architecture_ and the linux-image file that ends with “i386.deb” or “amd64.deb” again depending _depending upon your computer architecture_.
Afterwards open a terminal window, navigate to the folder where you downloaded those files and run:```
sudo dpkg -i *.deb
```

---

### Post by sombrancelha on 2014-02-13
Thank you for the reply.

I installed 3.11.10-03111003-generic following your instructions, but I just realized that this was not a good choice. The problem is that I need to run [perf](http://en.wikipedia.org/wiki/Perf_%28Linux%29), and it's very picky on kernel and tool versions, which need to match.

Perf is contained on the linux-tools-VERSION package, and from the repositories I can only install up to v3.8.0-35.

So here are my questions:
[list]
[*] Can I just uninstall the *.deb's that I installed before and then install the new kernel?
[*] Where can I find v3.8.0-35? It's not on the [kernel-ppa](http://kernel.ubuntu.com/~kernel-ppa/mainline/).
[/list]

---

### Post by Bucky Ball on 2014-02-13
I generally use Synaptic Package Manager for this stuff because it's easier to see all related software, but you could do a search for the kernel number in Software Centre and uninstall the headers, etc. That will get rid of it. It is no major problem leaving it where it is if you don't mind it taking up not much space. You should still have your previous kernels available at boot. You can just remove it from the menu instead.

---

### Post by sombrancelha on 2014-02-13
> **Bucky Ball said:**
> I generally use Synaptic Package Manager for this stuff because it's easier to see all related software, but you could do a search for the kernel number in Software Centre and uninstall the headers, etc. That will get rid of it. It is no major problem leaving it where it is if you don't mind it taking up not much space. You should still have your previous kernels available at boot. You can just remove it from the menu instead.

This is a remote machine, so a graphical interface is not an option. Nevertheless, I tried removing with apt-get and no other packages depended on it. My only concern is that during the installation of the new kernel some configuration file was altered and now it won't be reverted.

---

### Post by slickymaster on 2014-02-13
> **sombrancelha said:**
> <...snip...>
[LIST]
[*] Can I just uninstall the *.deb's that I installed before and then install the new kernel?
[/LIST]
Since you don't have a graphical interface, here's what you can do. Open terminal and and run the following:```
sudo apt-get --purge linux-image-3.11.10-031110-generic linux-headers-3.11.10-031110 linux-headers-3.11.10-031110-generic
```Afterwards update your Grub:```
sudo update-grub2
```and reboot.
> **sombrancelha said:**
> 

[LIST]
[*] Where can I find v3.8.0-35? It's not on the [kernel-ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").
[/LIST]

Try [here]("http://packages.ubuntu.com/raring-updates/kernel/").

---

### Post by ptn107 on 2014-02-13
If you're running precise (12.04 LTS) why not just use the backported packages that are provided:
```
sudo apt-get purge linux-generic linux-image-generic linux-headers-generic; sudo apt-get install linux-image-generic-lts-saucy linux-headers-generic-lts-saucy
```
that's the whole point of using an LTS release.

---

### Post by sombrancelha on 2014-02-19
Thanks, apt-get followed by update-grub2 solved it.

---

