---
title: "Can't compile simple module program with Custom Kernel."
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by thahir1986 on 2010-07-08
Hi,

I have been install the custom kernel (2.6.24 with rtai 3.6.1 patch) in my system. After compilation the custom kernel source folder size is 1.5gb. I want to remove this folder, 

For checking ,I compile the simple hello module program with /lib/modules/2.6.24-rtai(custom kernel)/build (link to /usr/src/linux-headers-2.6.24-rtai) instead of  /lib /modules/2.6.24-rtai(custom kernel)/build(link to /usr/src/linux-2.6.24-rtai). I got this error:

```
include/linux/time.h:172: error: expected declaration specifiers or ‘...’ before ‘u64’
include/linux/time.h: In function ‘timespec_add_ns’:
include/linux/time.h:174: error: ‘ns’ undeclared (first use in this function)
include/linux/time.h:174: error: (Each undeclared identifier is reported only once
include/linux/time.h:174: error: for each function it appears in.)
include/linux/time.h:174: error: ‘struct timespec’ has no member named ‘tv_nsec’
include/linux/time.h:177: error: ‘struct timespec’ has no member named ‘tv_sec’
include/linux/time.h:179: error: ‘struct timespec’ has no member named ‘tv_nsec’
In file included from include/linux/module.h:10,
                 from /root/rtai_workout/hello-1.c:1:
include/linux/stat.h: At top level:
include/linux/stat.h:63: error: expected specifier-qualifier-list before ‘u64’
In file included from include/linux/kmod.h:23,
                 from include/linux/module.h:13,
                 from /root/rtai_workout/hello-1.c:1:
include/linux/errno.h:4:23: error: asm/errno.h: No such file or directory
In file included from include/linux/module.h:13,
                 from /root/rtai_workout/hello-1.c:1:
include/linux/kmod.h: In function ‘call_usermodehelper’:
include/linux/kmod.h:74: error: ‘ENOMEM’ undeclared (first use in this function)
include/linux/kmod.h: In function ‘call_usermodehelper_keys’:
include/linux/kmod.h:86: error: ‘ENOMEM’ undeclared (first use in this function)
In file included from include/linux/module.h:14,
                 from /root/rtai_workout/hello-1.c:1:
include/linux/elf.h:6:21: error: asm/elf.h: No such file or directory
In file included from include/linux/module.h:14,
                 from /root/rtai_workout/hello-1.c:1:
include/linux/elf.h: At top level:
include/linux/elf.h:18: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf32_Addr’
include/linux/elf.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf32_Half’
include/linux/elf.h:20: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf32_Off’
include/linux/elf.h:21: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf32_Sword’
include/linux/elf.h:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf32_Word’
include/linux/elf.h:25: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf64_Addr’
include/linux/elf.h:26: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf64_Half’
include/linux/elf.h:27: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf64_SHalf’
include/linux/elf.h:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf64_Off’
include/linux/elf.h:29: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf64_Sword’
include/linux/elf.h:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf64_Word’
include/linux/elf.h:31: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf64_Xword’
include/linux/elf.h:32: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Elf64_Sxword’
include/linux/elf.h:126: error: expected specifier-qualifier-list before ‘Elf32_Sword’
include/linux/elf.h:134: error: expected specifier-qualifier-list before ‘Elf64_Sxword’
include/linux/elf.h:149: error: expected specifier-qualifier-list before ‘Elf32_Addr’
include/linux/elf.h:154: error: expected specifier-qualifier-list before ‘Elf64_Addr’
include/linux/elf.h:159: error: expected specifier-qualifier-list before ‘Elf32_Addr’
include/linux/elf.h:165: error: expected specifier-qualifier-list before ‘Elf64_Addr’
include/linux/elf.h:171: error: expected specifier-qualifier-list before ‘Elf32_Word’
include/linux/elf.h:180: error: expected specifier-qualifier-list before ‘Elf64_Word’
include/linux/elf.h:193: error: expected specifier-qualifier-list before ‘Elf32_Half’
include/linux/elf.h:210: error: expected specifier-qualifier-list before ‘Elf64_Half’
include/linux/elf.h:232: error: expected specifier-qualifier-list before ‘Elf32_Word’
include/linux/elf.h:243: error: expected specifier-qualifier-list before ‘Elf64_Word’
include/linux/elf.h:288: error: expected specifier-qualifier-list before ‘Elf32_Word’
include/linux/elf.h:301: error: expected specifier-qualifier-list before ‘Elf64_Word’
include/linux/elf.h:362: error: expected specifier-qualifier-list before ‘Elf32_Word’
include/linux/elf.h:369: error: expected specifier-qualifier-list before ‘Elf64_Word’
include/linux/elf.h:374:5: warning: "ELF_CLASS" is not defined
include/linux/elf.h:396: error: expected declaration specifiers or ‘...’ before ‘loff_t’
In file included from include/linux/kobject.h:24,
                 from include/linux/module.h:16,
                 from /root/rtai_workout/hello-1.c:1:
include/linux/sysfs.h:30: error: expected specifier-qualifier-list before ‘mode_t’
include/linux/sysfs.h:64: error: expected specifier-qualifier-list before ‘size_t’
include/linux/sysfs.h:75: error: expected specifier-qualifier-list before ‘ssize_t’
include/linux/sysfs.h:93: error: expected declaration specifiers or ‘...’ before ‘mode_t’
In file included from include/linux/kobject.h:27,
                 from include/linux/module.h:16,
                 from /root/rtai_workout/hello-1.c:1:
include/linux/kref.h:24: error: expected specifier-qualifier-list before ‘atomic_t’
In file included from include/linux/kobject.h:29,
                 from include/linux/module.h:16,
                 from /root/rtai_workout/hello-1.c:1:
include/linux/wait.h:26:25: error: asm/current.h: No such file or directory
In file included from include/linux/module.h:16,
                 from /root/rtai_workout/hello-1.c:1:
include/linux/kobject.h:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘uevent_seqnum’
include/linux/kobject.h:228: error: expected specifier-qualifier-list before ‘ssize_t’
include/linux/kobject.h:243: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /root/rtai_workout/hello-1.c:1:
include/linux/module.h:19:23: error: asm/local.h: No such file or directory
include/linux/module.h:21:24: error: asm/module.h: No such file or directory
In file included from /root/rtai_workout/hello-1.c:1:
include/linux/module.h:49: error: expected specifier-qualifier-list before ‘ssize_t’
include/linux/module.h:222: error: expected specifier-qualifier-list before ‘local_t’
include/linux/module.h:223: error: requested alignment is not a constant
include/linux/module.h:314: error: field ‘arch’ has incomplete type
include/linux/module.h:327: error: ‘NR_CPUS’ undeclared here (not in a function)
include/linux/module.h:341: error: expected specifier-qualifier-list before ‘Elf_Sym’
include/linux/module.h: In function ‘__module_get’:
include/linux/module.h:403: error: implicit declaration of function ‘BUG_ON’
include/linux/module.h:404: error: implicit declaration of function ‘local_inc’
include/linux/module.h:404: error: implicit declaration of function ‘get_cpu’
include/linux/module.h:405: error: implicit declaration of function ‘put_cpu’
/root/rtai_workout/hello-1.c:14:2: warning: no newline at end of file
make[2]: *** [/root/rtai_workout/hello-1.o] Error 1
make[1]: *** [_module_/root/rtai_workout] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24'
make: *** [all] Error 2
```


But it's run successfully ,if i compile the simple module program with /lib/modules/linux-2.6.24-rtai/build(link to custom kernel source code)

Here my doubt is :

Is it possible to remove the compiled custom kernel source code and i could use the custom linux-headers for that?.

Thnks in advance

---

### Post by thahir1986 on 2010-07-10
no one ?

---

### Post by thahir1986 on 2010-07-12
No one reply to this post...i think , i  have not explained my doubts clearly here....but any how i got the solution ...

There was a problem in the makefile...now solved ....

Thanks for the people who made a views....

---

### Post by votteraz on 2011-07-26
and can you explain the solution you find?
I understand that the post is quite old.. but I'm trying to solve the vary similar problem now...

---

### Post by rathin2j on 2012-08-20
hello...

        can u please give complete method of this patching??i m trying to patch ubuntu with 2.5.31.8 with RTAI-3.8 and infact i intend to patch kernel 3.x also but i dont have any through procedure.. looking forward to it.. thank u

---

