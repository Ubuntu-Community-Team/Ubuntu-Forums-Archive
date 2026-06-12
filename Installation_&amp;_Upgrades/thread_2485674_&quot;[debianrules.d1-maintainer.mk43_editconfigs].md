---
title: "&quot;[debian/rules.d/1-maintainer.mk:43: editconfigs] Error 1&quot; during kernel compile"
date: 2023-04-05
forum: Installation &amp; Upgrades
---

### Post by ziesemer on 2023-04-05
This is a cross-post from [https://askubuntu.com/questions/1460899/warning-configuration-operation-applied-only-to-a-subset-of-architectures-dur](https://askubuntu.com/questions/1460899/warning-configuration-operation-applied-only-to-a-subset-of-architectures-dur) , which has been stale for 10 days.

As I've been doing for a while now, after every Ubuntu-provided kernel update (for security, etc.) - I'm needing to recompile the kernel for a test VM to include some drivers that are otherwise missing from the default config (nor even included as modules).

While following the instructions detailed at [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel), at the end of every run of editconfigs, I'm getting the following warning / error:

```
check-config: 11330/11330 checks passed -- exit 0

WARNING: configuration operation applied only to a subset of architectures (skipped armhf arm64 ppc64el riscv64 s390x)

make: *** [debian/rules.d/1-maintainer.mk:43: editconfigs] Error 1
```

Regardless, continuing with the next [FONT=Courier New]LANG=C fakeroot debian/rules binary[/FONT] command succeeds. However, it seems quite haphazard to proceed past this warning / error - which also results in an exit code of 2 back to the command-line, and prevents further scripting this without completely ignoring the issue. I'm also not doing anything (at least not that I know of) to "skip" these other architectures (assuming there was maybe an option to configure them without even cross-compiling them).

I do see the comment on the above documentation page about:

```
# you need to go through each (Y, Exit, Y, Exit..) or get a complaint about config later
```

... however, while I do recall seeing the repeated menus at some point months back on prior kernel versions, I'm only ever seeing the one edit for "amd64":

```
$ LANG=C fakeroot debian/rules editconfigs
dh_testdir;
conc_level=-j4 /bin/bash -e debian/scripts/misc/kernelconfig editconfigs "true"
Do you want to edit config: amd64/config.flavour.generic? [Y/n]
```

I've seen this on at least Ubuntu kernels 5.19.0-23.24, 5.19.0-35.36, and 5.19.0-38.39, so far.

How can I resolve this warning / error? Or maybe otherwise completely disable even the existence of these other architectures in my build?

---

