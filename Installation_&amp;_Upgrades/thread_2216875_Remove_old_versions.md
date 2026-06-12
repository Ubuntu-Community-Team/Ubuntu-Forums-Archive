---
title: "Remove old versions"
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by Shaobo_Sun on 2014-04-14
[B]Hello there,

By running "sudo dpkg --list 'linux-image*'" I got a long list of linux images/versions, and I'd like to remove all the unnecessary versions:[/B]

un  linux-image                <none>                     (no description available)
un  linux-image-3.0            <none>                     (no description available)
un  linux-image-3.2.0-23-gener <none>                     (no description available)
rc  linux-image-3.2.0-26-gener 3.2.0-26.41                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-27-gener 3.2.0-27.43                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-29-gener 3.2.0-29.46                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-31-gener 3.2.0-31.50                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-32-gener 3.2.0-32.51                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-gener 3.2.0-33.52                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-gener 3.2.0-34.53                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-gener 3.2.0-35.55                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-gener 3.2.0-36.57                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-gener 3.2.0-37.58                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-gener 3.2.0-38.61                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-gener 3.2.0-39.62                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-gener 3.2.0-40.64                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-gener 3.2.0-41.66                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-gener 3.2.0-43.68                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-44-gener 3.2.0-44.69                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-45-gener 3.2.0-45.70                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-gener 3.2.0-48.74                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
in  linux-image-3.2.0-51-gener <none>                     (no description available)
in  linux-image-3.2.0-55-gener <none>                     (no description available)
in  linux-image-3.2.0-59-gener <none>                     (no description available)
ii  linux-image-3.2.0-60-gener 3.2.0-60.91                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic-pae    3.2.0.51.61                Generic Linux kernel image

**However, when I tried to run "sudo apt-get remove linux-image-3.2.0-36-gener", I got the following:**

Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-image-3.2.0-36-generic-pae' for regex 'linux-image-3.2.0-36-gener'
Note, selecting 'linux-image-3.2.0-36-generic' for regex 'linux-image-3.2.0-36-gener'
Package linux-image-3.2.0-36-generic is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.51.61) but 3.2.0.60.71 is to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-51-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

**By running "sudo apt-get -f install" I got the following:**

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,108 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-51-generic-pae; however:
  Package linux-image-3.2.0-51-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.51.61); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.51.61); however:
  Version of linux-headers-generic-pae on system is 3.2.0.60.71.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

**Anyone has seen similar issues and knows how to resolve this?**

[B]Thanks,

Shaobo[/B]

---

### Post by Bashing-om on 2014-04-14
Shaobo_Sun; Hi ! My Welcome to the forum.

An approach to the situation from an alternate perspective. Let's insure that you have not run out of space in '/boot' or elsewhere preventing any additional install of the kernels. Check for this condition; Terminal codes:
```

df -h
df -i

``` IF and only IF it is verified that there are no space constraints, then try this:
```

sudo apt-get install linux-generic linux-generic-pae linux-headers-generic linux-headers-generic-pae  linux-image-generic linux-image-generic-pae

```

Then before removing the excess kernels, make sure of what kernel you are presently running - DO NOT - remove this kernel:
```

uname -r

```

Finally, after the excess kernels have been removed, the remaining config files need to be removed. In your "sudo dpkg --list 'linux-image*'"  output, see those lines starting with 'rc', well the 'rc' means Removed but config files remain. To remove those stragglers:
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

If you are out of room, then other means will be introduced to clean things up. 

Advise and let us know how it goes.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

