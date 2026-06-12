---
title: "Jaunty does not allow user to log in"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hewhocutsdown on 2009-03-14
Hello

I recently upgraded to Jaunty on my IBM Thinkpad T43.

did a 'sudo gedit /etc/apt/sources.list', find/replace of intrepid with jaunty, 'sudo apt-get update', 'sudo apt-get dist-upgrade'.

I had some errors with a couple packages, so I rebooted into a command line root view, ran the dpkg cleanup and the rest seemed to go ok.

The only request for overwriting configuration files that I denied was for PAM. I did this because just last week I downloaded thinkfinger to allow me to use the fingerprint login functionality, and I didn't want to have to reconfigure it.

System boots fine, loads up the login screen, I can enter my user but when I hit enter after entering the password, it just sits there - doesn't do anything.

To compare, I booted back into console mode, ran 'useradd guest' and 'passwd guest' and 'mkdir /home/guest' and 'chown guest:guest /home/guest' and then rebooted. Login screen pops up, I sign in as guest and all is well.

So I'm guessing something screwy with authentication for my user. I ran 'password <my user>' but it still is causing problems.

Any thoughts?

---

### Post by nyarnon on 2009-03-15
Make a new user add it to the admin group, login and go to the user control panel. Check privileges, permission and groups for the user that has the problem.

---

### Post by MacUntu on 2009-03-15
I had the same problem, may we see the output of:

```
ls -l /dev/null
```
? If it's something other than 

```
crw-rw-rw- 1 root root 1, 3
```
you need to remove /dev/null and recreate it with proper permissions:

```
sudo rm /dev/null
sudo mknod -m 0666 /dev/null c 1 3
```

---

### Post by hewhocutsdown on 2009-03-15
MacUntu:

ls -l /dev/null came up with the expected results, so that looks ok.

nyarnon:

For whatever reason, the <user> that was failing was no longer a part of the <user> group. I changed that, and tried signing on again: failed, failed, success. No idea why the third time worked...now I'm afraid to sign off! :)

I've also uninstalled the version of thinkfinger-tools that I had, and reinstalled from the jaunty repos (a slightly older version than the one I removed).

Now it seems it does not see the fingerprint scanner:
```

$ tf-tool --acquire

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...Could not claim USB device.

```

---

### Post by hewhocutsdown on 2009-03-15
I think I may have found the inconsistency issue with logging in...the error below doesn't happen consistently, but about 1 in 3 times.

Note that I *DID NOT* swipe my finger, I simply entered the password.

```

$ sudo apt-get update
Password or swipe finger: 
*** glibc detected *** sudo: malloc(): memory corruption: 0x082c9f78 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7edb276]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x95)[0xb7edc9c5]
/lib/tls/i686/cmov/libc.so.6[0xb7f041db]
/lib/tls/i686/cmov/libc.so.6(opendir+0x63)[0xb7f04373]
/lib/libusb-0.1.so.4(usb_os_find_busses+0x22)[0xb7e00472]
/lib/libusb-0.1.so.4(usb_find_busses+0x1f)[0xb7dfd9bf]
/usr/lib/libthinkfinger.so.0[0xb7fe487b]
/usr/lib/libthinkfinger.so.0(libthinkfinger_verify+0x31)[0xb7fe4fd1]
/lib/security/pam_thinkfinger.so[0xb7fe97e1]
/lib/tls/i686/cmov/libpthread.so.0[0xb7e0b4ff]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7f4d49e]
======= Memory map: ========
08048000-08063000 r-xp 00000000 08:01 440166     /usr/bin/sudo
08063000-08064000 r--p 0001a000 08:01 440166     /usr/bin/sudo
08064000-08065000 rw-p 0001b000 08:01 440166     /usr/bin/sudo
08065000-08068000 rw-p 08065000 00:00 0 
082c1000-082fd000 rw-p 082c1000 00:00 0          [heap]
b6d3c000-b6d49000 r-xp 00000000 08:01 529483     /lib/libgcc_s.so.1
b6d49000-b6d4a000 r--p 0000c000 08:01 529483     /lib/libgcc_s.so.1
b6d4a000-b6d4b000 rw-p 0000d000 08:01 529483     /lib/libgcc_s.so.1
b6d4b000-b6d4c000 ---p b6d4b000 00:00 0 
b6d4c000-b754c000 rw-p b6d4c000 00:00 0 
b754c000-b754d000 ---p b754c000 00:00 0 
b754d000-b7d4d000 rw-p b754d000 00:00 0 
b7d4d000-b7d83000 r-xp 00000000 08:01 529943     /lib/libdbus-1.so.3.4.0
b7d83000-b7d84000 r--p 00035000 08:01 529943     /lib/libdbus-1.so.3.4.0
b7d84000-b7d85000 rw-p 00036000 08:01 529943     /lib/libdbus-1.so.3.4.0
b7d96000-b7dae000 r-xp 00000000 08:01 529386     /lib/libselinux.so.1
b7dae000-b7daf000 r--p 00017000 08:01 529386     /lib/libselinux.so.1
b7daf000-b7db0000 rw-p 00018000 08:01 529386     /lib/libselinux.so.1
b7db0000-b7db9000 r-xp 00000000 08:01 546334     /lib/tls/i686/cmov/libcrypt-2.9.so
b7db9000-b7dba000 r--p 00008000 08:01 546334     /lib/tls/i686/cmov/libcrypt-2.9.so
b7dba000-b7dbb000 rw-p 00009000 08:01 546334     /lib/tls/i686/cmov/libcrypt-2.9.so
b7dbb000-b7de2000 rw-p b7dbb000 00:00 0 
b7de2000-b7dee000 r-xp 00000000 08:01 529782     /lib/security/pam_unix.so
b7dee000-b7def000 r--p 0000b000 08:01 529782     /lib/security/pam_unix.so
b7def000-b7df0000 rw-p 0000c000 08:01 529782     /lib/security/pam_unix.so
b7df0000-b7dfc000 rw-p b7df0000 00:00 0 
b7dfc000-b7e02000 r-xp 00000000 08:01 530228     /lib/libusb-0.1.so.4.4.4
b7e02000-b7e03000 r--p 00005000 08:01 530228     /lib/libusb-0.1.so.4.4.4
b7e03000-b7e05000 rw-p 00006000 08:01 530228     /lib/libusb-0.1.so.4.4.4
b7e05000-b7e1a000 r-xp 00000000 08:01 548486     /lib/tls/i686/cmov/libpthread-2.9.so
b7e1a000-b7e1b000 r--p 00014000 08:01 548486     /lib/tls/i686/cmov/libpthread-2.9.so
b7e1b000-b7e1c000 rw-p 00015000 08:01 548486     /lib/tls/i686/cmov/libpthread-2.9.so
b7e1c000-b7e1e000 rw-p b7e1c000 00:00 0 
b7e22000-b7e24000 r-xp 00000000 08:01 441160     /usr/lib/libck-connector.so.0.0.0
b7e24000-b7e25000 r--p 00001000 08:01 441160     /usr/lib/libck-connector.so.0.0.0
b7e25000-b7e26000 rw-p 00002000 08:01 441160     /usr/lib/libck-connector.so.0.0.0
b7e26000-b7e28000 r-xp 00000000 08:01 529671     /lib/security/pam_ck_connector.so
b7e28000-b7e29000 r--p 00001000 08:01 529671     /lib/security/pam_ck_connector.so
b7e29000-b7e2a000 rw-p 00002000 08:01 529671     /lib/security/pam_ck_connector.so
b7e2a000-b7e2d000 r-xp 00000000 08:01 529761     /lib/security/pam_limits.so
b7e2d000-b7e2e000 r--p 00003000 08:01 529761     /lib/security/pam_limits.so
b7e2e000-b7e2f000 rw-p 00004000 08:01 529761     /lib/security/pam_limits.so
b7e2f000-b7e39000 r-xp 00000000 08:01 548481     /lib/tls/i686/cmov/libnss_files-2.9.so
b7e39000-b7e3a000 r--p 00009000 08:01 548481     /lib/tls/i686/cmov/libnss_files-2.9.so
b7e3a000-b7e3b000 rw-p 0000a000 08:01 548481     /lib/tls/i686/cmov/libnss_files-2.9.so
b7e3b000-b7e44000 r-xp 00000000 08:01 548483     /lib/tls/i686/cmov/libnss_nis-2.9.so
b7e44000-b7e45000 r--p 00008000 08:01 548483     /lib/tls/i686/cmov/libnss_nis-2.9.so
b7e45000-b7e46000 rw-p 00009000 08:01 548483     /lib/tls/i686/cmov/libnss_nis-2.9.so
b7e46000-b7e5b000 r-xp 00000000 08:01 548478     /lib/tls/i686/cmov/libnsl-2.9.so
b7e5b000-b7e5c000 r--p 00014000 08:01 548478     /lib/tls/i686/cmov/libnsl-2.9.so
b7e5c000-b7e5d000 rw-p 00015000 08:01 548478     /lib/tls/i686/cmov/libnsl-2.9.so
b7e5d000-b7e5f000 rw-p b7e5d000 00:00 0 
b7e5f000-b7e66000 r-xp 00000000 08:01 548479     /lib/tls/i686/cmov/libnss_compat-2.9.so
b7e66000-b7e67000 r--p 00006000 08:01 548479     /lib/tls/i686/cmov/libnss_compat-2.9.so
b7e67000-b7e68000 rw-p 00007000 08:01 548479     /lib/tls/i686/cmov/libnss_compat-2.9.so
b7e68000-b7e69000 rw-p b7e68000 00:00 0 
b7e69000-b7fc5000 r-xp 00000000 08:01 546330     /lib/tls/i686/cmov/libc-2.9.so
b7fc5000-b7fc6000 ---p 0015c000 08:01 546330     /lib/tls/i686/cmov/libc-2.9.so
b7fc6000-b7fc8000 r--p 0015c000 08:01 546330     /lib/tls/i686/cmov/libc-2.9.so
b7fc8000-b7fc9000 rw-p 0015e000 08:01 546330     /lib/tls/i686/cmov/libc-2.9.so
b7fc9000-b7fcd000 rw-p b7fc9000 00:00 0 
b7fcd000-b7fcf000 r-xp 00000000 08:01 546335     /lib/tls/i686/cmov/libdl-2.9.so
b7fcf000-b7fd0000 r--p 00001000 08:01 546335     /lib/tls/i686/cmov/libdl-2.9.so
b7fd0000-b7fd1000 rw-p 00002000 08:01 546335     /lib/tls/i686/cmov/libdl-2.9.so
b7fd1000-b7fdb000 r-xp 00000000 08:01 529490     /lib/libpam.so.0.81.12
b7fdb000-b7fdc000 r--p 00009000 08:01 529490     /lib/libpam.so.0.81.12
b7fdc000-b7fdd000 rw-p 0000a000 08:01 529490     /lib/libpam.so.0.81.12
b7fdd000-b7fde000 r-xp 00000000 08:01 529770     /lib/security/pam_permit.so
b7fde000-b7fdf000 r--p 00000000 08:01 529770     /lib/security/pam_permit.so
b7fdf000-b7fe0000 rw-p 00001000 08:01 529770     /lib/security/pam_permit.so
b7fe0000-b7fe1000 r-xp 00000000 08:01 529750     /lib/security/pam_deny.so
b7fe1000-b7fe2000 r--p 00000000 08:01 529750     /lib/security/pam_deny.so
b7fe2000-b7fe3000 rw-p 00001000 08:01 529750     /lib/security/pam_deny.so
b7fe3000-b7fe6000 r-xp 00000000 08:01 439929     /usr/lib/libthinkfinger.so.0.0.0
b7fe6000-b7fe7000 r--p 00002000 08:01 439929     /usr/lib/libthinkfinger.so.0.0.0
b7fe7000-b7fe8000 rw-p 00003000 08:01 439929     /usr/lib/libthinkfinger.so.0.0.0
b7fe8000-b7fea000 r-xp 00000000 08:01 529888     /lib/security/pam_thinkfinger.so
b7fea000-b7feb000 r--p 00001000 08:01 529888     /lib/security/pam_thinkfinger.so
b7feb000-b7fec000 rw-p 00002000 08:01 529888     /lib/security/pam_thinkfinger.so
b7fee000-b7ff0000 rw-p b7fee000 00:00 0 
b7ff0000-b7ff1000 r-xp b7ff0000 00:00 0          [vdso]
b7ff1000-b800d000 r-xp 00000000 08:01 529952     /lib/ld-2.9.so
b800d000-b800e000 r--p 0001b000 08:01 529952     /lib/ld-2.9.so
b800e000-b800f000 rw-p 0001c000 08:01 529952     /lib/ld-2.9.so
bf9fa000-bfa0f000 rw-p bffeb000 00:00 0          [stack]
Aborted

```

---

### Post by hewhocutsdown on 2009-03-18
Moot issue, I've reported it and reinstalled the OS.

---

