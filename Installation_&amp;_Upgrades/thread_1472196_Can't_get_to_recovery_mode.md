---
title: "Can't get to recovery mode"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by cdcooper on 2010-05-04
I need help recovering a partial upgrade to Lucid.

4 core Xeon , was running 64 bit 9.10.

Upgrading over the weekend, but it failed, and suggested running dpkg-reconfigure -a

I couldn't launch any terminal/xterm windows, and couldn't login via ssh (kicked me out with xmalloc failure) or through a virtual console (showed garbled characters)

So I had to reboot.

Now the boot process -- I've tried recovery mode for all othe kernels I've got installed, but all fail in the same way:

```
Begin: Starting AppArmor profiles...
bash: xmalloc: ../bash/locale.c:73: cannot allotate 225469542417 bytes (0 bytes allocated)
Failure: AppArmor profiles failed to load.
Done.
init: Error while reading from descriptor: Bad file descriptor
init: hwclock main process (447) terminated with status 2
init: plymouth main process (446) terminated with status 2
[    11.782252] hostname[445]: segfault at blah ip 00000000040139d sp blah error 7 in hostname[400000+3000]
init: hostname main process (445) killed by SEGV signal
bash: xmalloc: ../bash/locale.x:73: cannot allocate 225469542417 bytes (0 bytes allocated)
...
more xmalloc failures
...
init: mountall-shell post-stop process (453) terminated with status 2
```


It looks like it might be a libc problem.  At any rate, I'd like to get into a recovery console to restart the update.

Any suggestions gratefully received

---

### Post by bcbc on 2010-05-04
Any idea why the upgrade failed?

I'd try boot from live CD and chroot into your ubuntu. Then try continuing the upgrade or do the suggested dpkg fix. In the instructions below change sda5 to your ubuntu partition. Make sure you connect to the net before chrooting.

```
sudo mount /dev/sda5 /mnt
for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo cp /etc/resolv.conf /mnt/etc
sudo chroot /mnt 
```

Run recovery attempt.
You could try:
```
apt-get update
apt-get upgrade
```

Exit chroot:
```
exit
for i in dev/pts dev proc sys /; do sudo umount /mnt/$i;done 
```

---

### Post by cdcooper on 2010-05-04
Thanks for the prompt response.

Unfortunately that gets the same error:

ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt
ubuntu@ubuntu:~$ for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc
ubuntu@ubuntu:~$ sudo chroot /mnt
bash: xmalloc: ../bash/locale.c:73: cannot allocate 225469542417 bytes (0 bytes allocated)

---

### Post by bcbc on 2010-05-04
That doesn't look good. That's the only method I can think of - hopefully someone has a better idea.

---

### Post by cdcooper on 2010-05-04
ok - thanks

Interestingly, if I force the shell to /bin/sh, I see
xmalloc: ../bash/shell.c:1595: cannot allocate 225469542417 bytes (0 bytes allocated)

... which suggests the problem lies with xmalloc rather than bash or locale.

---

