---
title: "compile a kernel + couldn't install the new one"
date: 2014-11-16
forum: Installation &amp; Upgrades
---

### Post by mohdforever007 on 2014-11-16
hello everybody,

good day for all,,,,,,,

sorry for my language
I'm a new ubuntu user. I'm using ubuntu 14.04 64bit on my Asus K55J.

unfortunately, I tried to upgrade my kernel "Linux.3.13-035" to latest stable one "3.17.3" but nothing happen.

I followed many tutorial on youtube and other website but the output was only error.

______________

#uname -r
3.13.0-35-generic

________

after compiling the kernel, the files created was :

[LIST=1]
[*]*linux-headers-3.17.0-031700_xxx_all.deb* 
[*]*linux-headers-3.17.0-031700-generic_3.17.0-031700.xxx_amd64.deb* 
[*]*linux-image-3.17.0-031700-generic_3.17.0-031700.xxx_amd64.deb* 
[*]linux-firmware-image-3.17.3_1.hammody_amd64.deb 
[*]linux-libc-dev_1.hammody_amd64.deb 
[/LIST]

_______

the outpu of sudo dpkg - i linux*.deb  was 


Preparing to unpack linux-image-3.17.3-dbg_1.hammody_amd64.deb ...
Unpacking linux-image-3.17.3-dbg (1.hammody) over (1.hammody) ...
Preparing to unpack linux-libc-dev_1.hammody_amd64.deb ...
Unpacking linux-libc-dev (1.hammody) over (1.hammody) ...
Setting up linux-firmware-image-3.17.3 (1.hammody) ...
Setting up linux-headers-3.17.3 (1.hammody) ...
Setting up linux-image-3.17.3 (1.hammody) ...
update-initramfs: Generating /boot/initrd.img-3.17.3
W: Possible missing firmware /lib/firmware/radeon/hainan_smc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/hainan_rlc.bin for module radeon
W: Possible m >>>>>>>>>>>>>>


and long long list 



pls any solution ??????????????????


I did my best

---

### Post by Doug S on 2014-11-16
Hi and welcome to Ubuntu forums.

Is there a reason you want to compile your own kernel? If not, then perhaps try the pre-compiled one from the [kernel ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") (perhaps [this one]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.3-vivid/")) Even if you do need to compile your own, then a trick I use is to install the PPA one, just so that I can steal the Ubuntu kernel config file and use it for my compile.

Now, if you do need to compile your own kernel, then please tell us how you do it. There are several methods, and it is hard to comment without knowing your process.

---

### Post by mohdforever007 on 2014-11-16
> **Doug S said:**
> Hi and welcome to Ubuntu forums.Is there a reason you want to compile your own kernel? If not, then perhaps try the pre-compiled one from the [kernel ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") (perhaps [this one]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.3-vivid/")) Even if you do need to compile your own, then a trick I use is to install the PPA one, just so that I can steal the Ubuntu kernel config file and use it for my compile.Now, if you do need to compile your own kernel, then please tell us how you do it. There are several methods, and it is hard to comment without knowing your process.May be I did a tricky things while compiling my kernelAfter installed the ppa one , the way it go was smooth. And now I've solved this problem by doing a standard compile with nothing special.But really I dont know whats wronge with other setting I've done.Thank you all guys.Best regards

---

