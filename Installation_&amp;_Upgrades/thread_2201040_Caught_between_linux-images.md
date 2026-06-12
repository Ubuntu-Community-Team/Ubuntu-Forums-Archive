---
title: "Caught between linux-images"
date: 2014-01-22
forum: Installation &amp; Upgrades
---

### Post by mats4 on 2014-01-22
Just upgraded from 12.04 to 12.10. After this evereything (apparently) works but I can not update or upgrade. I can not install anything either. Whem I try to use:
$apt-get install <something> 
I get  the same error as when I try to do the update/upgrade: (It apperently detects that the new images are not in use and tries to remove them, without luck)
Removing linux-image-3.2.0-53-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
Update-initramfs: Deleting /boot/initrd.img-3.2.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
Generating grub.cfg ...
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-53-generic.postrm line 328.
dpkg: error processing linux-image-3.2.0-53-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already

I have tried:









$sudo apt-get --purge remove <Kernel>
with the same result (and error) as above.

The newer images not in use cannot be removed via synaptic either. 

The images are NOT in grub. Here the old version is the only option: linux-image-3.5.0-45-generic

When I try:
$dpkg -l 'linux-image*'
I get:
[B]Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                 Architecture            Description
+++-====================================-=======================-=======================-==============================================================================
ii  linux-image                          3.5.0.45.61             amd64                   Generic Linux kernel image.
un  linux-image-3.0                      <none>                                          (no description available)
rH  linux-image-3.2.0-53-generic         3.2.0-53.81             amd64                   Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-54-generic         3.2.0-54.82             amd64                   Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-55-generic         3.2.0-55.85             amd64                   Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-57-generic         3.2.0-57.87             amd64                   Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rH  linux-image-3.2.0-58-generic         3.2.0-58.88             amd64                   Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-23-generic         3.5.0-23.35             amd64                   Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-40-generic         3.5.0-40.62             amd64                   Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-41-generic         3.5.0-41.64             amd64                   Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-42-generic         3.5.0-42.65             amd64                   Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-44-generic         3.5.0-44.67             amd64                   Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-45-generic         3.5.0-45.68             amd64                   Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-45-generic   3.5.0-45.68             amd64                   Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                  3.5.0.45.61             amd64                   Generic Linux kernel image[/B]

Any suggestions on what to do to remove the newer images (or somehow activate them) ?

Sincerely

/Mats

---

### Post by TheFu on 2014-01-22
For a while (and maybe still), Ubuntu would get in a bad situation if the /boot partition filled during an upgrade. Manually cleaning up old kernels to free the storage was necessary.

The output from both these will let us know if that is the issue or not.
```
df -i
df -h
```

Please use the Adv Reply and wrap the output in "code" tags so things line up.

---

### Post by mats4 on 2014-01-23
Thanks for your reply! This is the output:

$df -i
```
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sda5        3129344 388785   2740559   13% /
udev             8238599    582   8238017    1% /dev
tmpfs            8240939    514   8240425    1% /run
none             8240939      3   8240936    1% /run/lock
none             8240939      9   8240930    1% /run/shm
none             8240939     25   8240914    1% /run/user
/dev/sdd1      279091592    127 279091465    1% /media/mats/S018521_Disk2
```

$df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        47G   17G   28G  38% /
udev             32G  4.0K   32G   1% /dev
tmpfs            13G  940K   13G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none             32G  220K   32G   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/sdd1       466G  200G  267G  43% /media/mats/S018521_Disk2
```

/Mats

---

### Post by mats4 on 2014-01-23
Since we probably have a time difference here I'll post additional info as well. 

In grub.cfg kernel versions 23-44 and 53-58 (Linux 3.2.0-23-generic etc) is listed as "Previous versions of Linux". The default is "Linux 3.2.0-45-generic". However when I list the items in /boot the kernel versions 53-58 is not there at all. 

Thanks for any suggestions...

Sincerely

/Mats

---

### Post by mats4 on 2014-01-23
Sorry, all kernel numbers should be Linux 3.5.0-45-generic etc (with 5 instead of 2).

/Mats

---

### Post by mats4 on 2014-01-23
When I check the status on one of the "missing" kernels with dpkg -s it says  "half-installed". The same output for the other kernels...

d$pkg -s  linux-image-3.2.0-53-generic
```
Package: linux-image-3.2.0-53-generic
Status: deinstall ok half-installed
Priority: optional
Section: kernel
Installed-Size: 146262
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux
Version: 3.2.0-53.81
Config-Version: 3.2.0-53.81
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3), crda (>= 1.1.1-1ubuntu2) | wireless-crda
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo (>= 19.1)
Suggests: fdutils, linux-doc-3.2.0 | linux-source-3.2.0, linux-tools
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 3.2.0 on 64 bit x86 SMP
 This package contains the Linux kernel image for version 3.2.0 on
 64 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

```

---

### Post by mats4 on 2014-01-23
Now I actually see that all the probelmatic kernels actually have the "2" instead of "5". I.e., linux-image-3.[COLOR=#ff0000]2[/COLOR].0-53-generic etc for the problematic and linux-image-3.[COLOR=#ff0000]5[/COLOR].0-45-generic for the functional ones. The error message from $dpkg -s also states this...Could the issue be in this fact?

Thanks!

/Mats

---

### Post by TheFu on 2014-01-23
a) My first guess at the issue was completely wrong. Sorry, but it has happened a bunch.
b) You've been busy! Fantastic!
c) I don't have a good answer, but having too many old kernels around can "get in the way" from a dependency perspective. Perhaps a little cleanup would help, though I doubt it will fix the root issue. [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) explains and provides a script.  Be certain to have 2 or 3 working kernels left.  Also,  **/usr/bin/sudo /usr/bin/apt-get purge** is the core command I always use, though I've seen it the way you did it too.  
d) Perhaps **aptitude** can clean things up? It is smarter. Use the same options, just s/apt-get/aptitude/  Aptitude has been recommended by the Debian guys for a few years.

I'm very curious. Why go from an LTS release to a release that will be out of support in 3 months? 12.04 has support until 2017 and 14.04 is coming soon - also an LTS release w/ 5 yrs of support.

I'll cross my fingers.

---

### Post by mats4 on 2014-01-24
Hi and thanks for your efforts in trying to help me!

Tried aptitude with essentially the same error:

```
mats@astraxeon:~$ sudo /usr/bin/aptitude  --purge remove linux-image-3.2.0-53-generic
[sudo] password for mats: 
The following packages will be REMOVED:  
  libdrm-intel1:i386{pu} libdrm-nouveau2:i386{pu} libllvm3.1:i386{pu} libpciaccess0:i386{pu} linux-image-3.2.0-53-generic 
The following partially installed packages will be configured:
  grub-pc 
0 packages upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 170 MB will be freed.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate a file for the linux-image-3.2.0-54-generic package. This might mean you need to manually fix this package.
E: I wasn't able to locate a file for the linux-image-3.2.0-54-generic package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
```

I guess that the reason is the the new kernels aren't actually installed (they are not listed under /boot). However, the kernels from 'linux-image-3.2.0-53-generic' to '...58' is listed as "Previous verions" when I boot (although the default which I use is an older version - linux-image-3.5.0-45-generic). So they must be listed somewhere since every effort in doing anything new (install/update/upgrade) preoduce the error referring to the newer kernels. 

I'm a Linux newbie but reading the error that was in one of the previous posts when I ran
$dpkg -s  linux-image-3.2.0-53-generic, one of the lines says:
```
Description: Linux kernel image for version 3.2.0 on 64 bit x86 SMP
 This package contains the Linux kernel image for version 3.2.0 on
 64 bit x86 SMP
```

Does that mean that the upgrade from 12.04 to 12.10 tried to install x86 instaed of amd64 architecture (which I have) or is that the same?

I tried to use, as you suggested, only purge ($apt-get purge <kernel>) without the "remove" but it gave the same error. I noted though one line saying:
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-58-generic.postrm line 328

This is the code around line 328:
```
if (-d "/etc/kernel/postrm.d") {
  warn "Examining /etc/kernel/postrm.d .\n";
328  system ("run-parts --verbose --exit-on-error --arg=$version " .
          "--arg=$realimageloc$kimage-$version " .
          "/etc/kernel/postrm.d") &&
            die "Failed to process /etc/kernel/postrm.d";
}
```

When I search for "linux-image-3.2.0-53-generic", "...54" etc they are listed in the following directories:

```
mats@astraxeon:/boot$ locate linux-image-3.2.0-53-generic
/var/crash/linux-image-3.2.0-53-generic.0.crash
/var/crash/linux-image-3.2.0-53-generic.0.upload
/var/crash/linux-image-3.2.0-53-generic.0.uploaded
/var/lib/dpkg/info/linux-image-3.2.0-53-generic.list
/var/lib/dpkg/info/linux-image-3.2.0-53-generic.md5sums
/var/lib/dpkg/info/linux-image-3.2.0-53-generic.postinst
/var/lib/dpkg/info/linux-image-3.2.0-53-generic.postrm
/var/lib/dpkg/info/linux-image-3.2.0-53-generic.preinst
/var/lib/dpkg/info/linux-image-3.2.0-53-generic.prerm
```

Is i t possible to just delete those or will that mess things up even more?

Thanks for the help!

Sincerely

/Mats

---

### Post by mats4 on 2014-01-24
Oh and the reason for upgrade was that I aimed for even newer versions (> 13.04). Being a newbie I followed a post in askubuntu on how to do and the consensus was that I had to upgrade chronologically, I.e., upgrading one version at a time. The overall reason was that I needed a libc6 library for one of my applications. In 12.04 the version was glib-2.15 but I needed at least 2.16. No matter how I tried upgrading that library I couldn't. Again as a newbie, the other approach was to upgrade to at least 13.04 where the newer library was default.

---

### Post by monkeybrain20122 on 2014-01-24
You should just save your data and do a clean install. I think 'upgrade' is a trap, many problems are related to "upgrade", not to mention it takes a very long time. A clean install takes 25 min. I also suggest a separate /home partition it makes it so much easier to keep your settings.

"Upgrade" is easily the most broken Ubuntu 'feature' based on the number of threads related to blotched upgrade. I wonder how they get away year after year without even putting a big warning in upgrade manager.

---

### Post by TheFu on 2014-01-24
> **mats4 said:**
> Oh and the reason for upgrade was that I aimed for even newer versions (> 13.04). Being a newbie I followed a post in askubuntu on how to do and the consensus was that I had to upgrade chronologically, I.e., upgrading one version at a time. The overall reason was that I needed a libc6 library for one of my applications. In 12.04 the version was glib-2.15 but I needed at least 2.16. No matter how I tried upgrading that library I couldn't. Again as a newbie, the other approach was to upgrade to at least 13.04 where the newer library was default.

Well, we are beyond my skills with APT. Sorry.  I would start reading the APT manual **very carefully** to see if something jumps out to help fix things. Regardless, it is a bad idea to manually delete any files managed via APT. 

Most of us users, need to stay on LTS releases. Period.  Newer isn't usually better.  It is true that getting to that version of libc would mandate migrating from 12.04, 12.10, 13.04, 13.10 and then to 14.04 when it is released.  However, if you can wait until April, 14.04 is an easy update from 12.04  ... just 1 step.  I think developers suck and I was one for over a decade.  We always stayed a few releases behind the latest, so our customers were the driver to all OS updates.  F/LOSS developers spend more time migrating to newer and newer Linux releases than they should. LTS releases is where they need to be.  This is a major issue for why businesses cannot adopt Linux - drastic, incompatible, changes from release to release.  Anarchy sucks, sometimes.

Well, good luck to you.  I'm staying on 12.04 until June-ish myself. A few of my servers are still running 10.04 (also LTS), which is still under support, BTW.

---

### Post by mats4 on 2014-01-24
Ok. Thanks anyway for trying to help! I appreciate it.

Sincerely

/Mats

---

### Post by monkeybrain20122 on 2014-01-24
> **TheFu said:**
> 
Most of us users, need to stay on LTS releases. Period.  Newer isn't usually better.  It is true that getting to that version of libc would mandate migrating from 12.04, 12.10, 13.04, 13.10 and then to 14.04 when it is released.  However, if you can wait until April, 14.04 is an easy update from 12.04  ... just 1 step.

I won't tell people to stick to LTS because most non LTS are fine and the best Ubuntu releases in my experience are not LTSes so 10.10 is better 10.04, 13.04 and 13.10 are better than 12.04.. The only thing I would say is DON'T DO "UPGRADE"!! Always do a fresh install (keep a separate /home). Easily half the problems reported on this forum have nothing to do with the new releases themselves, but bad upgrades. I really think that there should be a big warning sign in upgrade manager.

---

