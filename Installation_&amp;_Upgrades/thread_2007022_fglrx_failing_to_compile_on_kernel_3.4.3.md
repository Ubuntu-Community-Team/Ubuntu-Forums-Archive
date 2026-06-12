---
title: "fglrx failing to compile on kernel 3.4.3"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by Bushi86 on 2012-06-20
Hello,

I upgraded to linux kernel 3.4.3 earlier today, and now my AMD drivers are acting a little funny.

When trying to install using jockey-gtk, I get the following error(s) in the /var/log/jockey.log:
```

2012-06-19 23:45:31,172 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-06-19 23:45:31,404 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-19 23:45:31,404 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2012-06-19 23:45:31,404 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-06-19 23:45:44,129 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf

```

When trying to install using manual method (found [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")), I get the following output:
```

Selecting previously unselected package fglrx.
(Reading database ... 261454 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.961-0ubuntu1_amd64.deb) ...
restore of system environment completed
Error! There are no instances of module: fglrx
8.961 located in the DKMS tree.
Errors during DKMS module removal
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss.
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.961-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.961-0ubuntu1_amd64.deb) ...
Setting up fglrx (2:8.961-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.961 DKMS files...
First Installation: checking all kernels...
Building only for 3.4.3-030403-generic
Building for architecture x86_64
Building initial module for 3.4.3-030403-generic
**ERROR (dkms apport): kernel package linux-headers-3.4.3-030403-generic is not supported**
Error! Bad return status for module build on kernel: 3.4.3-030403-generic (x86_64)
Consult /var/lib/dkms/fglrx/8.961/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.961-0ubuntu1) ...
Setting up fglrx-dev (2:8.961-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.4.3-030403-generic

```

After both methods, amdcccle is installed, and I can run it just fine. I also have a dual-screen configuration that is configured correctly. However, I cannot enable any compiz effects, and running fglrxinfo in the terminal returns:
```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  138 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

The line in bold (2nd code block) is obviously the problem; the kernel is not supported. Is there anything that I can do about that, or do I have to wait for AMD to release an update (since they are propietary/closed-source drivers)?

Any help would be greatly appreciated! Thanks in advance

---

