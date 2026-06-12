---
title: "i2c problems (ref: Velleman, K8000, parport, i2c-parport, i2c-dev)"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by mapi on 2006-07-15
Hi there,

I am trying to setup K8000 Velleman board with Ubuntu server and found two separate problems, that seem to be new for this forum (forum search finds nothing for k8000 nor velleman):

1. can't compile a C code, that uses i2c device
2. can't insert kernel modules supporting i2c

Configuration:

--HW: Abit SA6 mobo, w/ Intel PIII/733, 512MB RAM, Adaptec 29160N + SEAGATE ST173404LW, 3c595, Linksys EG1032 v3 Gbit Eth, SB Live!.
--SW: fresh, netinstalled from scratch, Ubuntu 6.06, w/ 2.6.15-23-server kernel for 686 family

**DESCRIPTION FOR #1:**

The library package for K8000 board ([http://struyve.mine.nu:8080/other/libk8000-2.2.0.tar.gz)](http://struyve.mine.nu:8080/other/libk8000-2.2.0.tar.gz)), reported as working under Fedora Core 4 ([http://www.lavrsen.dk/twiki/bin/view/Mixed/KernelBuildForVellemanK8000](http://www.lavrsen.dk/twiki/bin/view/Mixed/KernelBuildForVellemanK8000)) fails to make from source under Ubuntu 6.06, with gcc messages starting with:

```
[FONT="Fixedsys"][SIZE="1"]gcc -c  -o k8000.o k8000.c
In file included from /usr/include/linux/sem.h:4,
                 from /usr/include/linux/sched.h:15,
                 from /usr/include/linux/module.h:9,
                 from /usr/include/linux/i2c.h:30,
                 from k8000.c:53:
/usr/include/linux/ipc.h:10: error: redefinition of 'struct ipc_perm'
In file included from /usr/include/linux/sched.h:15,
                 from /usr/include/linux/module.h:9,
                 from /usr/include/linux/i2c.h:30,
                 from k8000.c:53:
/usr/include/linux/sem.h:24: error: redefinition of 'struct semid_ds'
In file included from /usr/include/linux/sched.h:15,
                 from /usr/include/linux/module.h:9,
                 from /usr/include/linux/i2c.h:30,
                 from k8000.c:53:
/usr/include/linux/sem.h:39: error: redefinition of 'struct sembuf'
/usr/include/linux/sem.h:54: error: redefinition of 'struct seminfo'
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from /usr/include/linux/i2c.h:30,
                 from k8000.c:53:
make: *** [k8000.o] Interrupt[/SIZE][/FONT]
```

Quite some years have passed since I've quit coding in C, but I can still manage to:

```
[FONT="Fixedsys"][SIZE="1"]root@ubielak:/home/Works/k8000/libk8000# cat /home/Works/h.c
#include <stdio.h>
#include <linux/i2c.h>

int main (void )
{
  printf( "Hello!\n" );
  exit( 0 );
} 

root@ubielak:/home/Works/k8000/libk8000# gcc -o h /home/Works/h.c
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from /usr/include/linux/i2c.h:30,
                 from /home/Works/h.c:2: 
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from /usr/include/linux/i2c.h:30,
                 from /home/Works/h.c:2: 
/usr/include/linux/time.h:9: error: redefinition of 'struct timespec'
/usr/include/linux/time.h:15: error: redefinition of 'struct timeval'
/usr/include/linux/time.h:20: error: redefinition of 'struct timezone'
/usr/include/linux/time.h:47: error: redefinition of 'struct itimerval'
In file included from /usr/include/linux/i2c.h:30,
                 from /home/Works/h.c:2: 
/usr/include/linux/module.h:41: error: field 'attr' has incomplete type
/usr/include/linux/module.h:49: error: field 'kobj' has incomplete type
In file included from /usr/include/linux/i2c.h:33,
                 from /home/Works/h.c:2: [/SIZE][/FONT]
```
to see, that compile problems are not libk8000 specific...

I assume that there is something wrong with system C headers as they should not produce SYNTAX errors during compilation. Any hints?

Additional info:

```
[FONT="Fixedsys"]root@ubielak:/home/Works# uname -a
Linux ubielak 2.6.15-26-server #1 SMP Fri Jul 7 20:32:10 UTC 2006 i686 GNU/Linux

root@ubielak:/home/Works# apt-get install gcc libc6 libc6-dev linux-headers-2.6.15-26-686
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
libc6 is already the newest version.
libc6-dev is already the newest version.
linux-headers-2.6.15-26-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@ubielak:/home/Works# gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)[/FONT]

```

**DESCRIPTION FOR #2:**

I have tried to:

```
[FONT="Fixedsys"]root@ubielak:/home/Works# modprobe i2c-parport
root@ubielak:/home/Works# modprobe i2c-dev
root@ubielak:/home/Works# lsmod|grep i2c
i2c_dev                11136  0 
i2c_parport             7176  0 
i2c_algo_bit           10760  1 i2c_parport
i2c_core               23296  2 i2c_dev,i2c_algo_bit
parport                39624  3 i2c_parport,lp,parport_pc
root@ubielak:/home/Works# lsmod|grep parport
i2c_parport             7176  0 
i2c_algo_bit           10760  1 i2c_parport
parport_pc             38724  1 
parport                39624  3 i2c_parport,lp,parport_pc

/var/log/syslog:

Jul 15 18:15:34 ubielak kernel: [42949408.190000] parport: PnPBIOS parport detected.
Jul 15 18:15:34 ubielak kernel: [42949408.190000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 15 18:15:34 ubielak kernel: [42949409.760000] lp0: using parport0 (interrupt-driven).
Jul 15 19:37:01 ubielak kernel: [42949415.050000] parport0: cannot grant exclusive access for device i2c-parport
Jul 15 19:37:01 ubielak kernel: [42949415.050000] i2c-parport: Unable to register with parport
Jul 15 19:37:01 ubielak kernel: [42949415.090000] i2c /dev entries driver

root@ubielak:/home/Works# ps axuww
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.2  0.1   1564   528 ?        S    19:36   0:02 init [2]
root         2  0.0  0.0      0     0 ?        S    19:36   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   19:36   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    19:36   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   19:36   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   19:36   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   19:36   0:00 [kthread]
root         9  0.0  0.0      0     0 ?        S<   19:36   0:00 [kblockd/0]
root        10  0.0  0.0      0     0 ?        S<   19:36   0:00 [kacpid]
root       109  0.0  0.0      0     0 ?        S    19:36   0:00 [pdflush]
root       110  0.0  0.0      0     0 ?        S    19:36   0:00 [pdflush]
root       112  0.0  0.0      0     0 ?        S<   19:36   0:00 [aio/0]
root       111  0.0  0.0      0     0 ?        S    19:36   0:00 [kswapd0]
root       700  0.0  0.0      0     0 ?        S<   19:36   0:00 [kseriod]
root      1695  0.0  0.0      0     0 ?        S<   19:36   0:00 [scsi_eh_0]
root      1826  0.0  0.0      0     0 ?        S<   19:36   0:00 [khubd]
root      1945  0.0  0.0      0     0 ?        S    19:36   0:00 [kjournald]
root      2124  0.1  0.1   2104   544 ?        S<s  19:36   0:00 /sbin/udevd --daemon
root      2902  0.0  0.0      0     0 ?        S    19:36   0:00 [shpchpd_event]
root      2957  0.0  0.0      0     0 ?        S    19:36   0:00 [w1_control]
root      2959  0.0  0.0      0     0 ?        S    19:36   0:00 [w1_bus_master1]
root      2976  0.0  0.0      0     0 ?        S<   19:36   0:00 [kgameportd]
root      3411  0.0  0.0      0     0 ?        S    19:36   0:00 [kjournald]
root      3412  0.0  0.0      0     0 ?        S    19:36   0:00 [kjournald]
syslog    3731  0.0  0.1   1768   672 ?        Ss   19:36   0:00 /sbin/syslogd -u syslog
root      3748  0.0  0.0   1680   496 ?        Ss   19:36   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      3750  0.0  0.2   2392  1316 ?        Ss   19:36   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      3781  0.0  0.2   4756  1044 ?        Ss   19:37   0:00 /usr/sbin/sshd
root      3800  0.0  0.0   1624   296 ?        Ss   19:37   0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
daemon    3813  0.0  0.0   1796   392 ?        Ss   19:37   0:00 /usr/sbin/atd
root      3823  0.0  0.1   2120   720 ?        Ss   19:37   0:00 /usr/sbin/cron
root      3858  0.0  0.2   2580  1136 tty1     Ss   19:37   0:00 /bin/login --     
root      3859  0.0  0.0   1564   496 tty2     Ss+  19:37   0:00 /sbin/getty 38400 tty2
root      3860  0.0  0.0   1564   496 tty3     Ss+  19:37   0:00 /sbin/getty 38400 tty3
root      3861  0.0  0.0   1564   496 tty4     Ss+  19:37   0:00 /sbin/getty 38400 tty4
root      3862  0.0  0.0   1560   492 tty5     Ss+  19:37   0:00 /sbin/getty 38400 tty5
root      3863  0.0  0.0   1560   492 tty6     Ss+  19:37   0:00 /sbin/getty 38400 tty6
root      3880  0.0  0.3   3992  1856 tty1     S+   19:37   0:00 -bash
root      3895  0.0  0.4   7516  2368 ?        Ss   19:37   0:00 sshd: pm [priv]  
pm        3897  0.0  0.3   7516  1568 ?        S    19:37   0:00 sshd: pm@pts/0   
pm        3898  0.0  0.4   4516  2156 pts/0    Ss+  19:37   0:00 -bash
pm        3940  0.0  0.4   4500  2144 pts/1    Ss+  19:38   0:00 -bash
root      3949  0.0  0.3   4008  1888 pts/3    Ss   19:38   0:00 /bin/bash
root      4036  0.0  0.1   2396  1016 pts/3    R+   19:48   0:00 ps axuww[/FONT]
```

Any hints for making i2c-parport working under ubuntu?


Brgds,
pm

---

### Post by eldaria on 2006-12-15
Did you get this working?

I'm also looking on how to get the k8000 card working in Ubuntu.
I found how to get it working without the kernel module, but that is only by running application as root.

I have no idea on how to compile kernel modules. :-)
And certainly not from a description made for another system. :-)

---

### Post by mapi on 2006-12-15
I had a problem with kernel-related part of C headers, and after installing correct ones and recompiling kernel **modules** my problem has gone away. 

You don't need to recompile the kernel to compile kernel MODULE and you can insert and remove kernel module without rebooting.

Anyway, K8000 works by now with a generic kernel downloaded from Ubuntu (my version is 2.6.15-26).

Brgds,
*pm*

---

