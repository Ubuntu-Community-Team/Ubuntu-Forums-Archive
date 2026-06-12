---
title: "installation/livecd issues"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by nathanhillinbl on 2007-02-01
I am fairly new to linux,and this error confused the crap out of me. I wanted to try out ubuntu. So i downloaded the iso, and burnt it to a cd. I've been having motherboard ide connector issues prior to this, so im not sure if this is attributed to that or what. Upon boot up, bios detects the cd drives, and hard drives, and boots to the ubuntu cd that i burnt. When i select install/start ubuntu, it gives me the error code that i will manually  type below:

df20 000000000
[56.871831] ffffffff c01e489c 000d4845 000000000 000000000a 00000246 0000000d0 d7feff20
[56.872279] 00000000 c0166b94 c03ebf7c 00800b00 c03bfb c0135a6 00000f9e 00000292
[56.872727] Call Trace:
[56.872819] <c0122759> release_console_sem+0x199/0x1f0 <c01e49c> vsnprintf +0x55c/0x640
[ 56.873148] <c0166b94> kmem_cache_alloc+0x64/0x70 <c01335a6> alloc_pid+0x16/0x270
[56.873490] <c0122759> release_console_sem+0x199/0x1f0 <c012161e> do_fork+0x10
[56.874495] <c010143e>kernel_thread+0x8e/0xb0 <c0100320> init+0x0/0x320
[56.874157] <c0100320> init+0x0/0x320 <c0101000> kernel_thread_helper+0x0/0x10
[56.874495] <c0100651> rest_init+0x11/0x30 <c03f07a1> start_kernel+0x321/0x3a0
[56.874835] <c03f0210> unknown_bootoption+0x0/0x270
[56.875071] Code: (A bunch of hex i dont have the energy to type)
[56.878006] EIP: [<c0166cd7>] cache_alloc_refill+0x137/0x540 SS:ESP 0068:c03ebea4
[56.878170] <0>Kernel panic - not syncing: Attempted to kill the idle task!
[56.878281]


End of error code.
That just took me 15 mins to type, so i hope someone can decipher what that means and let me know.


Thanks in advance,
Nate


ps. this :guitar: emoticon is da $hit.

---

### Post by scrooge_74 on 2007-02-01
Did you try booting in recovery mode (or safe mode), sometimes you can get a bad iso and it will give problems booting

---

### Post by Sef on 2007-02-01
```
So i downloaded the iso, and burnt it to a cd.
```

1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) If you did both, then try the alternate cd.  It is a text based installer and sometimes works where the Live CD fails.

4) What are you system specs?

---

### Post by nathanhillinbl on 2007-02-01
I burnt at 2x, and i have no idea what md5sum is. I also tried booting it on another computer,and after selecting start/install, got a continuous bouncing bar with ubuntu above it, and nothing happened.

---

### Post by scrooge_74 on 2007-02-01
is probably the cd

---

### Post by nathanhillinbl on 2007-02-01
i'm going to try to boot it again on this computer, and i'll post results.

---

### Post by nathanhillinbl on 2007-02-01
it might be the cd, but i cant run the check cd thing on the boot up screen, the load screen just does the bounce thing.

---

### Post by scrooge_74 on 2007-02-02
Download the image again, check that it does not get interrupted during download and then burn again at 2x

---

