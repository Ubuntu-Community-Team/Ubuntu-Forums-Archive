---
title: "intel 536ep"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by daveboy on 2006-09-23
i have a ubuntu 6.06 am tying it instal the moden 
have this 
module preconpile check
current running kernel is 2.6.15-23-386
/lib/modules..... autoconf.h does not exist please install kernel source 
please help:(

---

### Post by JAwuku on 2006-09-26
If you have already access to internet, install the kernel source by:

```
sudo apt-get install linux-headers-386 linux-source-2.6.15
```

and you're ready to go.

But if you have no access, the only way is to manually download all the packages from the Ubuntu site, which is tedious and time-consuming.

If you have access to the Internet on another computer, with access to either a CD-ROM burner or USB pen-drive, you may have to manually retrieve the kernel source packages.

Go to [http://packages.ubuntu.com](http://packages.ubuntu.com)

and look for linux-source-2.6.15

Click on the Dapper label

and download all the individual files and their dependencies (could be a complex tree, of which some of the dependencies may already be installed)

Do the same for linux-headers-386

Put all the dependencies in one directory, and issue:

```
sudo dpkg -i *.deb
```

Otherwise if all else fails, you can still get inexpensive external serial modems which don't require any drivers.

---

### Post by Sethramoth on 2006-10-15
I had the exact same problem daveboy, and what worked for me is:

```
sudo apt-get install linux-headers-`uname -r`
```

As I recall, this code just prompted me to install the kernel source from the Ubuntu installation disk and after that I was good to go.

---

### Post by st3v3 on 2007-06-22
Dear all,

I am using Ubuntu 7.04 with kernel 2.6.20-16
I have installed all of the header kernel file,
but when i make 536 for this intel driver, I found the error message like this :

make[1]: Entering directory `/home/st3v3/Intel-536/coredrv'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/st3v3/Intel-536/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/st3v3/Intel-536/coredrv/coredrv.o
/home/st3v3/Intel-536/coredrv/coredrv.c:73: warning: data definition has no type or storage class
/home/st3v3/Intel-536/coredrv/coredrv.c:73: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
/home/st3v3/Intel-536/coredrv/coredrv.c:73: warning: parameter names (without types) in function declaration
/home/st3v3/Intel-536/coredrv/coredrv.c: In function ‘softcore_init_struct’:
/home/st3v3/Intel-536/coredrv/coredrv.c:339: warning: assignment from incompatible pointer type
/home/st3v3/Intel-536/coredrv/coredrv.c: In function ‘open’:
/home/st3v3/Intel-536/coredrv/coredrv.c:395: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/st3v3/Intel-536/coredrv/coredrv.c: In function ‘close’:
/home/st3v3/Intel-536/coredrv/coredrv.c:439: warning: implicit declaration of function ‘pm_unregister’
/home/st3v3/Intel-536/coredrv/coredrv.c: In function ‘send_data_to_user’:
/home/st3v3/Intel-536/coredrv/coredrv.c:587: error: ‘struct tty_struct’ has no member named ‘flip’
/home/st3v3/Intel-536/coredrv/coredrv.c:592: error: ‘struct tty_struct’ has no member named ‘flip’
/home/st3v3/Intel-536/coredrv/coredrv.c:593: error: ‘struct tty_struct’ has no member named ‘flip’
/home/st3v3/Intel-536/coredrv/coredrv.c:595: error: ‘struct tty_struct’ has no member named ‘flip’
/home/st3v3/Intel-536/coredrv/coredrv.c:596: error: ‘struct tty_struct’ has no member named ‘flip’
/home/st3v3/Intel-536/coredrv/coredrv.c:597: error: ‘struct tty_struct’ has no member named ‘flip’
/home/st3v3/Intel-536/coredrv/coredrv.c: At top level:
/home/st3v3/Intel-536/coredrv/coredrv.c:665: error: expected ‘)’ before string constant
/home/st3v3/Intel-536/coredrv/coredrv.c:778:39: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/home/st3v3/Intel-536/coredrv/coredrv.c:778: warning: data definition has no type or storage class
/home/st3v3/Intel-536/coredrv/coredrv.c:778: warning: type defaults to ‘int’ in declaration of ‘DECLARE_WORK’
/home/st3v3/Intel-536/coredrv/coredrv.c:779:37: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/home/st3v3/Intel-536/coredrv/coredrv.c:779: warning: data definition has no type or storage class
/home/st3v3/Intel-536/coredrv/coredrv.c:779: warning: type defaults to ‘int’ in declaration of ‘DECLARE_WORK’
/home/st3v3/Intel-536/coredrv/coredrv.c: In function ‘wake_up_interruptible_persistReadQ’:
/home/st3v3/Intel-536/coredrv/coredrv.c:793: error: ‘wait_wq’ undeclared (first use in this function)
/home/st3v3/Intel-536/coredrv/coredrv.c:793: error: (Each undeclared identifier is reported only once
/home/st3v3/Intel-536/coredrv/coredrv.c:793: error: for each function it appears in.)
/home/st3v3/Intel-536/coredrv/coredrv.c: In function ‘interruptible_sleep_on_timeout_persistReadQ’:
/home/st3v3/Intel-536/coredrv/coredrv.c:827: error: ‘wait_wq2’ undeclared (first use in this function)
/home/st3v3/Intel-536/coredrv/coredrv.c: At top level:
/home/st3v3/Intel-536/coredrv/coredrv.c:880: warning: initialization makes integer from pointer without a cast
make[3]: *** [/home/st3v3/Intel-536/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/st3v3/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/st3v3/Intel-536/coredrv'
2.6.20-16-generic

can you please help me to solve this problem ??

thx before.

> **JAwuku said:**
> If you have already access to internet, install the kernel source by:

```
sudo apt-get install linux-headers-386 linux-source-2.6.15
```

and you're ready to go.

But if you have no access, the only way is to manually download all the packages from the Ubuntu site, which is tedious and time-consuming.

If you have access to the Internet on another computer, with access to either a CD-ROM burner or USB pen-drive, you may have to manually retrieve the kernel source packages.

Go to [http://packages.ubuntu.com](http://packages.ubuntu.com)

and look for linux-source-2.6.15

Click on the Dapper label

and download all the individual files and their dependencies (could be a complex tree, of which some of the dependencies may already be installed)

Do the same for linux-headers-386

Put all the dependencies in one directory, and issue:

```
sudo dpkg -i *.deb
```

Otherwise if all else fails, you can still get inexpensive external serial modems which don't require any drivers.

---

### Post by Diaz on 2007-06-27
I too am having a problem, when I 'sudo make 536', I get this;
```

user@fileserver:/home/public/ModemDriver/intel-536EP-2.56.76.0$ sudo make 536
   Module precompile check
   Current running kernel is: 2.6.20-15-server
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.20-15-server
make[1]: Entering directory `/home/public/ModemDriver/intel-536EP-2.56.76.0/coredrv'
make -C /lib/modules/2.6.20-15-server/build SUBDIRS=/home/public/ModemDriver/intel-536EP-2.56.76.0/coredrv modules
/usr/src/linux-headers-2.6.20-15-server/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.20-15-server/scripts/gcc-version.sh: line 12: gcc: command not found
make[2]: gcc: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-server'
  CC [M]  /home/public/ModemDriver/intel-536EP-2.56.76.0/coredrv/coredrv.o
/bin/sh: gcc: not found
make[3]: *** [/home/public/ModemDriver/intel-536EP-2.56.76.0/coredrv/coredrv.o] Error 127
make[2]: *** [_module_/home/public/ModemDriver/intel-536EP-2.56.76.0/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-server'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/public/ModemDriver/intel-536EP-2.56.76.0/coredrv'
2.6.20-15-server
Failed to build driver

```

Any Chance of help?


Never mind, I jsut needed to install GCC :)

---

