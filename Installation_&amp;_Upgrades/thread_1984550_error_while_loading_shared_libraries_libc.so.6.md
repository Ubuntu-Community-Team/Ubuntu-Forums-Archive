---
title: "error while loading shared libraries: libc.so.6"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by eekrazyk on 2012-05-21
I'm running a 64-bit Ubuntu Server 11.10 and am attempting to install an old 32-bit tool for work.

The installer is a script that sets some environment variables then attempts to create a director under /tmp.  This is where it fails with the following error:

```
$ sudo ./setup
mkdir: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
ERROR: Could not make directory in /tmp
```

This is the problem line from the installer script:

```
      if [ -d "/tmp/windu" ]
      then
         /bin/rm -rf /tmp/windu
      fi

      mkdir -p /tmp/windu
      if [ $? -ne 0 ]
      then
           echo "ERROR: Could not make directory in /tmp"
           exit 1;
      fi

```


```
$ ldd bin/lin/windu_registryd44
        linux-gate.so.1 =>  (0xf77ac000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7772000)
        libcrypt.so.1 => /lib32/libcrypt.so.1 (0xf7741000)
        libm.so.6 => /lib32/libm.so.6 (0xf7716000)
        libc.so.6 => /lib32/libc.so.6 (0xf759c000)
        libnsl.so.1 => /lib32/libnsl.so.1 (0xf7583000)
        /lib/ld-linux.so.2 (0xf77ad000)

```

I have installed ia32-libs.  I'm not finding much on the forums for this problem.  Can anyone point me in the right direction?

---

### Post by jadtech on 2012-05-21
check this out 

[http://publib.boulder.ibm.com/infocenter/director/v5r2/index.jsp?topic=/diricinfo_5.20/fqm0_r_tbs_tasks_process_mgt_linux_error.html](http://publib.boulder.ibm.com/infocenter/director/v5r2/index.jsp?topic=/diricinfo_5.20/fqm0_r_tbs_tasks_process_mgt_linux_error.html)

[http://stackoverflow.com/questions/480764/linux-error-while-loading-shared-libraries-cannot-open-shared-object-file-no-s](http://stackoverflow.com/questions/480764/linux-error-while-loading-shared-libraries-cannot-open-shared-object-file-no-s)

---

### Post by eekrazyk on 2012-05-22
Thanks jadtech!

There was a part in the installation script that set the LD_ASSUME_KERNEL variable, so I modified that:

```
# set $LD_ASSUME_KERNEL for Linux
if [ "$platform" = "Linux" ]
then
#       LD_ASSUME_KERNEL=2.4.7
        LD_ASSUME_KERNEL=
        export LD_ASSUME_KERNEL
fi
```

Now I'm getting the following error:

```
$ sudo ./setup
/usr/bin/nohup: redirecting stderr to stdout
/home/user/ISE6.3_Disc1Lin/xilsetup: relocation error: /home/user/ISE6.3_Disc1Lin/bin/lin/libwinsock44.so: symbol h_errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference


************ setup done! ***************
```

```
$ locate libc.so.6
/home/user/libc6/lib/libc.so.6
/lib/i386-linux-gnu/libc.so.6
/lib/x86_64-linux-gnu/libc.so.6
/lib32/libc.so.6
/usr/lib32/libc.so.6
```

okay...

```
$ strings /lib32/libc.so.6 | grep GLIBC
GLIBC_2.0
GLIBC_2.1
GLIBC_2.1.1
GLIBC_2.1.2
GLIBC_2.1.3
GLIBC_2.2
GLIBC_2.2.1
GLIBC_2.2.2
GLIBC_2.2.3
GLIBC_2.2.4
GLIBC_2.2.6
GLIBC_2.3
GLIBC_2.3.2
GLIBC_2.3.3
GLIBC_2.3.4
GLIBC_2.4
GLIBC_2.5
GLIBC_2.6
GLIBC_2.7
GLIBC_2.8
GLIBC_2.9
GLIBC_2.10
GLIBC_2.11
GLIBC_2.12
GLIBC_2.13
GLIBC_PRIVATE
GNU C Library (Ubuntu EGLIBC 2.13-20ubuntu5.1) stable release version 2.13, by Roland McGrath et al.

```

```
$ export LD_LIBRARY_PATH=/lib32/
----------------------------------------------------------------------------------------------------------- 09:15:45
user@mordac:~/ISE6.3_Disc1Lin$ sudo ./setup
/home/user/ISE6.3_Disc1Lin/xilsetup: relocation error: /home/user/ISE6.3_Disc1Lin/bin/lin/libwinsock44.so: symbol h_errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference


************ setup done! ***************
```

Any ideas?

---

### Post by jadtech on 2012-05-22
hehe hmm 

i'm not much for scripts  to be honest  and in my search this problem different causes depending  on  what you are trying to do .. 
most common seems to be related to something about trying to run an older version of a program with more modern library or the other way around ..

here is a link these guys seem to have found a solution  not sure if its you answer or not ..

[http://ubuntuforums.org/archive/index.php/t-300843.html](http://ubuntuforums.org/archive/index.php/t-300843.html)

[http://www.linuxquestions.org/questions/linux-software-2/error-on-install-glibc_2-0-not-defined-234637/](http://www.linuxquestions.org/questions/linux-software-2/error-on-install-glibc_2-0-not-defined-234637/)

---

