---
title: "/proc/sys/vm/vdso_enabled missing on 10.04 LTS?"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by hochl on 2011-02-25
Dear all,

I have a rather ancient build environment where I switch into using chroot. The script looks like this:

```

echo 0 > /proc/sys/vm/vdso_enabled
echo 4096 > /proc/sys/vm/mmap_min_addr
chroot `pwd` /usr/bin/env -i \
        HOME=/root TERM="$TERM" PS1='[CR]\u:\w\$ ' \
        PATH=/bin:/usr/bin:/sbin:/usr/sbin \
        /bin/bash --login

```This has worked flawlessly on Debian, with the following kernel:

```

# cat /proc/version
Linux version 2.6.32-5-686 (Debian 2.6.32-30) (ben@decadent.org.uk) (gcc version 4.3.5 (Debian 4.3.5-4) ) #1 SMP Wed Jan 12 04:01:41 UTC 2011

```Now after switching to Ubuntu 10.04 LTS, the entry /proc/sys/vm/vdso_enabled does not exist anymore. This can be confirmed using sysctl:

```

Debian:
# sysctl -a | grep vdso
vm.vdso_enabled = 0
#

Ubuntu:
# sysctl -a | grep vdso
#

```The Ubuntu kernel:

```

# cat /proc/version
Linux version 2.6.32-28-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011

```What am I missing here? How can I chroot into my build system? I now get the following error:

```

# bash chroot.sh 
chroot.sh: line 1: /proc/sys/vm/vdso_enabled: No such file or directory
Inconsistency detected by ld.so: rtld.c: 1180: dl_main: Assertion `(void *) ph->p_vaddr == _rtld_local._dl_sysinfo_dso' failed!

```

Cheers,
H.

---

### Post by hochl on 2011-02-28
Ok, the solution:

```

echo 0 > /proc/sys/abi/vsyscall32

```

Thanks for your help! :popcorn:

---

