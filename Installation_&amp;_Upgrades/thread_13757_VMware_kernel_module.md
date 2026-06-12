---
title: "VMware kernel module"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by ming0 on 2005-02-02
I can't get the VMware module to build?? I've got the kernel headers installed, but get the following error on configuration:

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.8.1-4

The path "/usr/src/linux-headers-2.6.8.1-4" is an existing directory, but it
does not contain at least one of these directories "linux", "asm", "net" as
expected.
```

Any help is appreciated :)

---

### Post by Tichondrius on 2005-02-02
[QUOTE=ming0]I can't get the VMware module to build?? I've got the kernel headers installed, but get the following error on configuration:

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.8.1-4

The path "/usr/src/linux-headers-2.6.8.1-4" is an existing directory, but it
does not contain at least one of these directories "linux", "asm", "net" as
expected.
```

Any help is appreciated :)[/QUOTE]
 try "ln -s /usr/src/linux-headers-2.6.8.1-4 /usr/src/linux"

---

### Post by ming0 on 2005-02-03
Okay, that helped a little bit--now it's throwing a version error, and as far as I can tell, I'm using the same version??

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The directory of kernel headers (version 2.6.8.1) does not match your running
kernel (version 2.6.8.1-4-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

```Thanks!

---

### Post by Tichondrius on 2005-02-03
Try this:

sudo ln -s /usr/src/linux-headers-2.6.8.1-4 /lib/modules/2.6.8.1-4-386/source

Or if that doesn't help, why not just compile a new kernel:

01 $ sudo adduser myusername src    # logout and login for this to take effect
02 $ sudo apt-get install linux-source-2.6.8.1 build-essential fakeroot kernel-package
03 $ cd /usr/src
04 $ tar jxvf linux-source-2.6.8.1.tar.bz2
05 $ ln -s linux-source-2.6.8.1 linux
06 $ cd linux
07 $ cp /boot/config-`uname -r` .config
07 $ make oldconfig
08 $ make-kpkg clean
09 $ fakeroot make-kpkg --initrd --append-to-version custom1 kernel_image
10 $ cd /usr/src
11 $ sudo dpkg -i kernel-image-2.6.8.1custom1*.deb

Reboot into the new kernel and you're done !  
You've got a new properly setup kernel+source tree in 11 lines !!!

Btw, VMware works great in Ubuntu. I've got VMs running WinXP and also Mepis Linux (wanted to try it out). You can try out new distros without burning a CD, because VMware let's you use the ISO image file as a virtual CD-ROM in the VM. Also you never have to physically reboot your machine, so it's kind of cool when you restart a VM which is running fullscreen, it looks like the machine is rebooting (but it doesn't really).

Everything works including networking and sound in the guest operating systems. Installing Windows in a VM was simple, but installing Mepis linux was more involved, as it refused to "boot" with the default kernel. I think the initrd file it comes with does something strange. Anyway, I could still boot the Mepis CD in the VM, so I mounted the (virtual) root partition and used chroot to compile a new kernel, and everything worked afterwards.

One problem I encountered with hoary-amd64 - the VMwafre kernel module fails to compile, as the source code doesn't identify the AMD64 envrionment correctly (although it is supposed to support 64 bit hosts, it seems like it's checking for X86_64 macros, and not AMD64?).

---

### Post by flyfishin on 2005-02-03
You do not need to compile a new kernel to get VMware to work on Hoary or Warty  Based on this link:

[http://linux.simple.be/vmware/](http://linux.simple.be/vmware/)

I installed the following packages:

linux-image
linux-headers
linux-source

Or were those called kernel-image, kernel-headers, and kernel-source?  I work on a Debian test machine and Ubuntu and I think they use different names.  It's one of the two. Make sure that you get the packages for the same kernel version.  The install worked flawlessly after that.

---

### Post by Tichondrius on 2005-02-03
[QUOTE=flyfishin]You do not need to compile a new kernel to get VMware to work on Hoary or Warty  Based on this link:

[http://linux.simple.be/vmware/](http://linux.simple.be/vmware/)

I installed the following packages:

linux-image
linux-headers
linux-source

Or were those called kernel-image, kernel-headers, and kernel-source?  I work on a Debian test machine and Ubuntu and I think they use different names.  It's one of the two. Make sure that you get the packages for the same kernel version.  The install worked flawlessly after that.[/QUOTE]
 I know you don't need to compile the kernel,  but sometimes it's easier because all the directories and links are in sync (believe it or not, compiling the kernel is quite simple and has other benefits of possible customization and optimization).  Btw, the link you provided gives incomplete and misleading information about VMware on woody. It looks like the writer did not install vmware tools, which handles the keyboard/mouse isseues, as well as providing a vmware virtual graphics driver, which is a lot faster then using framebuffer modules. Suffice to say that it's possible to install VMware on Ubuntu (as I have done) and run a debian-based Linux and Windows XP in a VM, with all hardware including networking, sound, keyboard, mouse working in windowed and full screen mode.  File sharing with the host also works ok, but you need to compile another kernel module inside the guest  linux VM, which is a little tricky (similar to the original problem of compiling the vmware host kernel module).

---

### Post by flyfishin on 2005-02-03
[QUOTE=ming0]I can't get the VMware module to build?? I've got the kernel headers installed, but get the following error on configuration:

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.8.1-4

The path "/usr/src/linux-headers-2.6.8.1-4" is an existing directory, but it
does not contain at least one of these directories "linux", "asm", "net" as
expected.
```

Any help is appreciated :)[/QUOTE]

You don't need the linux-source installed to install VMware.  Here is how VMware acts on my system when it gets to the same question:

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.10-2-386/build/include]

Once you have linux-headers installed pass it the /lib/modules directory for your kernel and it should work.

---

### Post by flyfishin on 2005-02-04
All right.  I new a little something was eluding my memory when I was posting.  I just did a fresh install of Warty on my machine.  I performed the install and hadn't patched the system.  To get VMware to install correctly I had to install two packages, gcc and linux-headers.  You have to make sure you install the correct linux-headers.  Here are the aptitude commands I ran:

aptitude update
aptitude install gcc
aptitude install linux-headers-`uname -r`

I know I read about the last aptitude command somewhere and should give the person credit but I can't remember where I found it.  Anyway, install gcc and the correct linux-headers package and VMware installs perfectly.
Any time you upgrade/change your kernel VMware won't run until you rerun the vmware-config command to build the proper VMware modules for you current kernel.  You will have to make sure you have the proper headers installed for vmware-config to work again.  Just run the last aptitude command after a new kernel install to make sure you have the matching linux-headers and vmware-config will work perfectly.

---

### Post by ming0 on 2005-02-04
Okay, I'll give that a try once my computer is back up (the PSU is fried :-(). 

Thanks :o

---

### Post by StacyWebb on 2005-02-10
they easiest way is this

apt-get  linux-headers-`uname -r`
cd /usr/src
ln -s linux-headers-<your version>/ linux
cd /path/to/vmware-distrib/
./vmware-install.pl

that'll do it
but do make sure you have the latest gcc as refered to by flyfishing.

---

