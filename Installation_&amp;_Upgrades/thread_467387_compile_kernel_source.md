---
title: "compile kernel source"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by wilso027 on 2007-06-07
I have to have the kernel source in place so I can install zaptel for asterisk. I installed the kernel-source with apt-get and did the following:

cd /usr/src
sudo tar xjvf linux-source-2.6.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.20 /usr/src/linux
sudo mv /usr/src/linux/include /usr/src/linux/include2
sudo ln -s /usr/src/linux-headers-2.6.20-15/include /usr/src/linux/include
cd linux
/usr/src/linux$ sudo make
scripts/kconfig/conf -s arch/i386/Kconfig
***
*** You have not yet configured your kernel!
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release
'.  Stop.
zm@australia:/usr/src/linux$ 

I can't install the source so that I can compile zaptel. Can anyone tell me what I am doing wrong? Thanks

Allan

---

### Post by pbw on 2007-06-07
exactly what it says..

> 
*** You have not yet configured your kernel!


You need to configure the kernel first.

```

sudo -s
make menuconfig

```

(like it says)
> 
*** Please run some configurator (e.g. "make oldconfig" or
 *** "make menuconfig" or "make xconfig").


-- pbw

---

### Post by wilso027 on 2007-06-08
So I ran
```
sudo make menuconfig
```
I didn't change anything I just exited back out. I just need the kernel there so I can compile zaptel against it. I then ran make and it errored out.

```
zm@australia:/usr/src/linux$ sudo make menuconfig
scripts/kconfig/mconf arch/i386/Kconfig
*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.
zm@australia:/usr/src/linux$ sudo make
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-i386
  CC      arch/i386/kernel/asm-offsets.s
arch/i386/kernel/asm-offsets.c:7:26: error: linux/crypto.h: No such file or directory
arch/i386/kernel/asm-offsets.c:8:25: error: linux/sched.h: No such file or directory
arch/i386/kernel/asm-offsets.c:9:26: error: linux/signal.h: No such file or directory
arch/i386/kernel/asm-offsets.c:10:31: error: linux/personality.h: No such file or directory
arch/i386/kernel/asm-offsets.c:11:27: error: linux/suspend.h: No such file or directory
arch/i386/kernel/asm-offsets.c:12:26: error: asm/ucontext.h: No such file or directory
In file included from arch/i386/kernel/asm- offsets.c:13:
arch/i386/kernel/sigframe.h:3: error: expected ':', ',', ';', '}' or '__attribute__' before '*' token
arch/i386/kernel/sigframe.h:13: error: expected ':', ',', ';', '}' or '__attribute__' before '*' token
arch/i386/kernel/asm-offsets.c:14:24: error: asm/fixmap.h: No such file or directory
arch/i386/kernel/asm-offsets.c:15:27: error: asm/processor.h: No such file or directory
arch/i386/kernel/asm-offsets.c:16:29: error: asm/thread_info.h: No such file or directory
arch/i386/kernel/asm-offsets.c:17:21: error: asm/elf.h: No such file or directory
arch/i386/kernel/asm-offsets.c:18:21: error: asm/pda.h: No such file or directory
arch/i386/kernel/asm-offsets.c: In function 'foo':
arch/i386/kernel/asm-offsets.c:30: warning: implicit declaration of function 'offsetof'
arch/i386/kernel/asm-offsets.c:30: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:31: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:32: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:33: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:34: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:35: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:36: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:37: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:38: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:41: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:42: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:43: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:44: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:45: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:46: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:47: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:48: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:51: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:52: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:53: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:54: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:55: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:56: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:57: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:58: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:61: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:62: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:63: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:66: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:67: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:68: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:69: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:70: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:71: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:72: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:73: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:74: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:75: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:76: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:77: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:78: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:79: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:80: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:81: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:84: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:85: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:88: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:89: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:90: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:93: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:93: error: invalid application of 'sizeof' to incomplete type 'struct tss_struct'
arch/i386/kernel/asm-offsets.c:96: error: 'PAGE_SIZE' undeclared (first use in this function)
arch/i386/kernel/asm- offsets.c:96: error: (Each undeclared identifier is reported only once
arch/i386/kernel/asm-offsets.c:96: error: for each function it appears in.)
arch/i386/kernel/asm-offsets.c:97: error: 'VDSO_PRELINK' undeclared (first use in this function)
arch/i386/kernel/asm-offsets.c:99: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:102: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:103: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:107: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:108: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:109: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:110: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:111: error: expected expression before 'struct'
arch/i386/kernel/asm-offsets.c:112: error: expected expression before 'struct'
make[1]: *** [arch/i386/kernel/asm-offsets.s] Error 1
make: *** [prepare0] Error 2

```
I just need to compile the kernel on feisty so that I can compile the zaptel module from asterisk against it. Thanks for the help.

Allan

---

### Post by veerakumar on 2007-06-08
Why don't you try a vanilla kernel.
Buy the way it may have just kernel headers in
/usr/src/linux

And /usr/src/linux is deprecated.

---

### Post by wilso027 on 2007-06-08
I thought when I apt-get installed the kernel-source that is what I was doing but the zaptel module still did not install properly because everything was not built properly in lib modules.

Can you give more steps about trying the vanilla kernel. I am not sure what you mean by depriciated kernel in this instance. Does this mean that it doesn't have everything? This is my problem.

Allan

---

