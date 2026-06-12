---
title: "In this situation, what Steps to upgrade kernel?"
date: 2015-11-07
forum: Installation &amp; Upgrades
---

### Post by ross4 on 2015-11-07
I installed Xubuntu 14.04.3 LTS on two computers, a Toshiba notebook and a Toshiba laptop, about a year and a half ago (see below for system details). Just this week I discovered that the notebook is using *3.13.0-65-generi**c *but the laptop is using *3.16.-0-52-generic*. I am pretty sure the difference is because /boot on the notebook filled up with old kernels. When I do *ls /boot | grep vmlinuz && df -m *I get over 20 different *vmlinuz-3.13.0. *After doing a lot of searching, I figure I know how to clear out most (all but two most recent) of these but I am wondering what my next step(s) should be. Do I slowly  upgrade step-by-step, from *3.13.0-65 *to  *3.16.-0-52* or can I jump, somehow, directly to  *3.16.-0-52.*

If it the latter is an option, how would I go about this?

I am asking this because I THINK that when the last software updates icon appeared and I clicked on it, it was trying to load 13.13-(something) and not 13-16-(something) so I inferred that software updates wants to install the next version not the latest. Could be wrong about this since installation screen disappeared rather quickly.
Regards,
Ross


Systems:
Notebook: Toshiba NB200-002, Intel Atom CPU N280 @1.66GHz, .99GB of RAM

Laptop: Toshiba Satellite P100, Intel core two CPU T5500, 1.67 GHz, 2.00 GB of RAM

---

### Post by Bashing-om on 2015-11-07
ross4; Hello;

I expect, not something to fret about.
HardeWare Enablement stack :
[http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement](http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

To remove the old kernels:
```

sudo apt-get autoremove

```

For your reference:
My system:
```

sysop@1404mini:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
sysop@1404mini:~$

sysop@1404mini:~$ uname -r
3.13.0-67-generic
sysop@1404mini:~$

```

But do need to address getting the 3.16 kernel upgraded to that of vivid.

[INDENT][INDENT]my bit to try  and help
[/INDENT][/INDENT]

---

### Post by ross4 on 2015-11-08
I removed the old kernels on the notebook using Synaptic as I couldn't figure out how to use apt-get autoremove. The removal of most of the old kernels freed up lots of space in /boot. In fact, "Softwear Updater" was able to install vmlinuz-3-13.0-67-generic. Having done that, my notebook system info is the same as yours above, Bashing-om. So I guess my next question is should I bother to try to bring it up to *3.13.0-65-generi**c?  *And then, of course, if this is a good idea, how do I do it?

---

### Post by Bashing-om on 2015-11-08
ross4; Well ..

Just cheap - real cheap - insurance to have a backup kernel .
What now is installed on the box:
```

dpkg -l | grep linux-

``` then we can better address the need to install the -65 version of the kernel .

[INDENT][INDENT]no biggy to do so
[/INDENT][/INDENT]

---

### Post by ross4 on 2015-11-09
After removing more images and headers, here is the output from that command:

```
~$ dpkg -l | grep linux-
ii  linux-firmware                             1.127.16                                all          Firmware for Linux kernel drivers
ii  linux-firmware-nonfree                     1.14ubuntu3                             all          Non-free firmware for Linux kernel drivers
ii  linux-generic                              3.13.0.67.73                            i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-65                    3.13.0-65.106                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic            3.13.0-65.106                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-67                    3.13.0-67.110                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic            3.13.0-67.110                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                      3.13.0.67.73                            i386         Generic Linux kernel headers
rc  linux-image-3.13.0-24-generic              3.13.0-24.47                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic              3.13.0-65.106                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-67-generic              3.13.0-67.110                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic        3.13.0-24.47                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic        3.13.0-29.53                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic        3.13.0-65.106                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic        3.13.0-67.110                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                        3.13.0.67.73                            i386         Generic Linux kernel image
ii  linux-libc-dev:i386                        3.13.0-67.110                           i386         Linux Kernel Headers for development
ii  linux-sound-base       
```

Hope it fits the bill and you can make some suggestions. One particular difference I notice about this from the notebook vs the lap top is the second line: "ii  linux-firmware-nonfree..." Didn't see anything like that on the lap top.
Ross

---

### Post by Bashing-om on 2015-11-09
ross4; Hey ;

Looks good so far .

As to " linux-firmware-nonfree " pertains to proprietary drivers installed .
> 
Description-en: Non-free firmware for Linux kernel drivers
 This package provides non-free firmware used by Linux kernel drivers.


Is all set now to for booting ?
```

ls -al /vmlinuz*
ls -al /initrd.img*

```

next to finish the clean up is those packages marked 'rc':
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
The state is rc, the package is removed, but the config files are not removed. This little number will deal with it handily.

[INDENT][INDENT]all over with now
[INDENT][INDENT][INDENT]not even any crying
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ross4 on 2015-11-10
Thank you. That definitely cleaned out more stuff. I'm going to keep all these examples handy to keep my /boot clean. 
I now have *vmlinuz-3.16.0-50-generic* running on my laptop and *vmlinuz-3.13.0-68-generic* on the notebook.

I gathered from Synaptic that, if I want to have the same kernels running on both computers, that I "likely do not want to install"  the linux-image-*3.16.0-50-generic* on to the notebook but that I should "install the linux-generic meta-package".

I investigated Synaptic further and I found I have linux-generic-lts-utopic version 3.16.0.53.44 on the laptop and linux-generic version 3.13.0.68.74 on the notebook. I am guessing these are the respective meta-packages. So **IF** I want the same kernels, I should install lts-utopic on that notebook. Am I correct or even getting close?

---

### Post by Bashing-om on 2015-11-10
ross4; Well ..

The purpose of HWE is to support newer hardware . If it ain't broke, do not fix it . IF the need for a different kernel and X does not exist, why add an additional layer of complexity ?
Now all that said .. kernel vmlinuz-3.16.0-50-generic  is of utopic. And is now End_Of_Life. Need to get that box up to vivid's kernel and X stack.
[http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement](http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

> 
 I should install lts-utopic on that notebook. Am I correct or even getting close?

close but no tomatoes .. change your focus to vivid now as uptopic (3.16.XXX) is EOL .
Shortly ( January ) vivid goes EOL and next up is wily (15.10) for the HWE upgrade.


[INDENT][INDENT]keep'n the ducks
[INDENT][INDENT][INDENT]all in a row
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-11-10
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

... should get you to .65. In fact, that will probably get you to .67, as that is where it is currently at. 3.13.0-67

---

### Post by ross4 on 2015-11-12
Bashing-om, thanks very much for your on-going help, and Buck Ball for your added note. I will be away from the computers for a while so I won't try any updating or upgrading until I come back. I'll mark this as solved and then if I need further help later, I'll start another, similar thread. Thanks again.

---

