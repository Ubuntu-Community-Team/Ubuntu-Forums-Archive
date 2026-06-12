---
title: "Setting up grub-efi-amd64-signed fails during 20.04 uprade"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by angryelephant on 2020-04-24
Performed a largely successful upgrade, but hung with the packages grub-efi-amd64-signed and shim-signed. 
```
(Reading database ... 237378 files and directories currently installed.)
Preparing to unpack .../linux-generic_5.4.0.26.32_amd64.deb ...
Unpacking linux-generic (5.4.0.26.32) over (5.4.0.26.32) ...
Setting up grub-efi-amd64-signed (1.142+2.04-1ubuntu26) ...
/boot/vmlinuz-5.4.0-26-generic is signed, but using an unknown key:
        Subject: C = GB, ST = Isle of Man, O = Canonical Ltd., OU = Secure Boot, CN = Canonical Ltd. Secure Boot Signing
E: Your kernels are not signed with a key known to your firmware. This system will fail to boot in a Secure Boot environment.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Setting up linux-generic (5.4.0.26.32) ...
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed | grub-efi-arm64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried to sign the kernel using the key I have successfully used for modules, but had not luck. Is there a way to import the key Canonical used to sign this kernel?

---

### Post by dino99 on 2020-04-24
Looks like there were a problem

Published on 2020-04-16
Changelog
shim-signed (1.40.3) focal; urgency=medium

  * Depend on the correct version of grub-signed (LP: #1871895)

 -- Julian Andres Klode <email address hidden>  Thu, 09 Apr 2020 20:48:31 +0200

---

### Post by angryelephant on 2020-04-24
It is a little odd, since 5.3.0-46 works. So it looks like they changed the signing key for the kernel, but did put in code for the updater to trigger enrolling the new key in UEFI.

---

### Post by angryelephant on 2020-04-25
I was able to get it to work using the instructions here:

[https://github.com/jakeday/linux-surface/blob/master/SIGNING.md](https://github.com/jakeday/linux-surface/blob/master/SIGNING.md)

Rather than using the surface-linux-surface naming convention, I just overwrote the generic kernel.

Separate note, wifi seems rather laggy. I tried reinstalling the iwlwifi-dkms drivers which helped a little.

---

