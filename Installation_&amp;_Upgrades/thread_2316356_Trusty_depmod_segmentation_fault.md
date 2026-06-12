---
title: "Trusty: depmod segmentation fault"
date: 2016-03-07
forum: Installation &amp; Upgrades
---

### Post by jeevan4 on 2016-03-07
Hello Experts,

I am trying to compile Open embedded build on my Ubuntu 14.04 machine. I am trying to compile a old kernel(3.10) with Open Embedded for one of my projects and cannot move to latest kernels. Though all the compilation go through, it's segfaulting at depmod stage.

On Ubuntu 14.04, depmod (from module-init-tools) is a dummy package and symlinked to kmod. I went through multiple online blogs but couldn't fine anything related to kmod segfaulting. Since kmod is backward compatible with depmod , I have tried using the latest version of kmod to check if it makes any difference.

```

|   INSTALL block/test-iosched.ko
|   INSTALL crypto/ansi_cprng.ko
|   INSTALL drivers/input/misc/gpio_axis.ko
|   INSTALL drivers/input/misc/gpio_input.ko
|   INSTALL drivers/input/misc/gpio_matrix.ko
|   INSTALL drivers/input/misc/gpio_event.ko
|   INSTALL drivers/input/misc/gpio_output.ko
|   INSTALL drivers/mmc/card/mmc_test.ko
|   INSTALL drivers/spi/spidev.ko
|   DEPMOD  3.10.0+
| kernel/scripts/depmod.sh line 54: 30017 Segmentation fault    "$DEPMOD" -b "$tmp_dir" $KERNELRELEASE 2> /dev/null
| make[1]: *** [_modinst_post] Error 139
| make: *** [sub-make] Error 2
| + die 'oe_runmake failed'
| + bbfatal 'oe_runmake failed'
| + echo 'ERROR: oe_runmake failed'
| ERROR: oe_runmake failed
| + exit 1

```
I tried using strace to find out if there's any wrong file access/memory access, but I am not able to make it out from the log. Can someone please help me in resolving this issue?

```

openat(AT_FDCWD, "/etc/depmod.d", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 3
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
getdents(3, /* 3 entries */, 32768)     = 80
rt_sigprocmask(SIG_BLOCK, [HUP USR1 USR2 ALRM TERM CHLD], [], 8) = 0
--- SIGSEGV {si_signo=SIGSEGV, si_code=SEGV_MAPERR, si_addr=0} ---
+++ killed by SIGSEGV +++
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 19.09    0.000117           2        66           rt_sigprocmask
 18.60    0.000114           4        27        17 open
  9.95    0.000061           4        17           mmap
  7.01    0.000043           4        10           mprotect
  6.20    0.000038           3        11         9 stat
  5.06    0.000031           3        11           read
  4.73    0.000029           2        12           close
  4.08    0.000025           3         8         1 lstat
  3.43    0.000021           4         6           write
  2.77    0.000017           3         5         5 access
  2.45    0.000015           8         2           munmap
  2.28    0.000014           2         6           fstat
  1.79    0.000011           1         8           rt_sigaction
  1.63    0.000010           2         5         2 newfstatat
  1.31    0.000008           1         6           fcntl
  1.31    0.000008           8         1           getdents
  1.31    0.000008           4         2           openat
  1.14    0.000007           2         3           brk
  0.98    0.000006           6         1           connect
  0.82    0.000005           5         1           socket
  0.82    0.000005           3         2         1 futex
  0.49    0.000003           3         1           execve
  0.49    0.000003           3         1           kill
  0.49    0.000003           2         2           fchdir
  0.49    0.000003           3         1           set_tid_address
  0.33    0.000002           2         1           getcwd
  0.33    0.000002           2         1           getrlimit
  0.33    0.000002           2         1           arch_prctl
  0.33    0.000002           2         1           set_robust_list
------ ----------- ----------- --------- --------- ----------------
100.00    0.000613                   219        35 total

```

---

