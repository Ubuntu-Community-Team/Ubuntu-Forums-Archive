---
title: "Cannot Update Ubuntu 18.04 HWE Kernel?"
date: 2023-10-26
forum: Installation &amp; Upgrades
---

### Post by msantangelosdoc on 2023-10-26
I have two VMs running on the same host, and on one esxi host I get: ```
mike@forms:/home/mike# uname -a 
Linux forms 5.4.0-165-generic #182~18.04.1-Ubuntu SMP Fri Oct 6 09:10:46 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```
but on the other I get: ```
mike@newsletter:/home/mike# uname -a 
Linux newsletter 5.4.0-150-generic #167~18.04.1-Ubuntu SMP Wed May 24 00:51:42 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```
No matter what I do, I can't get newsletter to get a new kernel up to -165 and I am unsure why. Is there anything people can suggest? They're both HWE and ESM enabled.
So now I've added a 3rd VM and it is updating to 5.4.0-165 successfully too, so I am thinking there is something wrong with the Apt sources for newsletter too...
```
mike@tftp:/home/mike# uname -a 
Linux tftp 5.4.0-165-generic #182~18.04.1-Ubuntu SMP Fri Oct 6 09:10:46 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```
I don't see anything out of sorts in apt sources and when I do a search for that kernel in newsletter I get:
```
mike@newsletter:~# apt update && apt list linux-image-
```
I get a list of linux images and 5.4.0-165 is definitely there but when I try:
```
mike@newsletter:~# apt install linux-image-5.4.0-165-generic
 Reading package lists... Done
Building dependency tree
 Reading state information... Done 
Package linux-image-5.4.0-165-generic is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package 'linux-image-5.4.0-165-generic' has no installation candidate
```

Any advice? Nothing seems out of sorts in apt repos and I am spinning my wheels on this.

---

### Post by ajgreeny on 2023-10-26
Unless you have signed up to **ESM** with **Ubuntu Pro** you are now using a version of Ubuntu that has lost any further support.
See [https://ubuntu.com/pro/tutorial](https://ubuntu.com/pro/tutorial) for more info.
Alternatively you should upgrade to or clean install a fully supported version; I recommend 22.04.

---

### Post by msantangelosdoc on 2023-10-26
We are using ESM as indicated.  We are trying to avoid having to replace that VM, just trying to patch it up a bit.

---

### Post by MAFoElffen on 2023-10-26
I don't have any 18.04 VM's in my test suite on my ESM, so
```

apt list linux*-image-5.4.0-[0-5][4-6][4-9]-generic
apt-cache show linux*-image-5.4.0-[0-5][4-6][4-9]-generic

```
To see what is there...

---

### Post by msantangelosdoc on 2023-10-27
```
mike@newsletter:~# sudo apt list linux*-image-5.4.0-[0-5][4-6][4-9]-generic
Listing... Done
linux-image-5.4.0-144-generic/bionic-updates,bionic-security 5.4.0-144.161~18.04.1 amd64
linux-image-5.4.0-146-generic/bionic-updates,bionic-security 5.4.0-146.163~18.04.1 amd64
linux-image-5.4.0-147-generic/bionic-updates,bionic-security 5.4.0-147.164~18.04.1 amd64
linux-image-5.4.0-148-generic/bionic-updates,bionic-security 5.4.0-148.165~18.04.1 amd64
linux-image-5.4.0-149-generic/bionic-updates,bionic-security 5.4.0-149.166~18.04.1 amd64
linux-image-5.4.0-155-generic/bionic-infra-security 5.4.0-155.172~18.04.1 amd64
linux-image-5.4.0-156-generic/bionic-infra-security 5.4.0-156.173~18.04.1 amd64
linux-image-5.4.0-159-generic/bionic-infra-security 5.4.0-159.176~18.04.1 amd64
linux-image-5.4.0-164-generic/bionic-infra-security 5.4.0-164.181~18.04.1 amd64
linux-image-5.4.0-165-generic/bionic-infra-security 5.4.0-165.182~18.04.1 amd64
```

and

```
mike@newsletter:~# sudo apt-cache show linux*-image-5.4.0-[0-5][4-6][4-9]-genericPackage: linux-image-5.4.0-144-generic
Architecture: amd64
Version: 5.4.0-144.161~18.04.1
Built-Using: linux-hwe-5.4 (= 5.4.0-144.161~18.04.1)
Priority: optional
Section: kernel
Source: linux-signed-hwe-5.4
Origin: Ubuntu
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 10748
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-144-generic
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-144-generic
Conflicts: linux-image-unsigned-5.4.0-144-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-144-generic_5.4.0-144.161~18.04.1_amd64.deb
Size: 10571604
MD5sum: abfdf663aea2decf5546d39a2c4ea1d4
SHA1: c6c7ebf305648dad08edb37cb3b2f9e539170104
SHA256: 5b9cb86065c95649934f3d84165a5a167d6c6ee9de0840a3527f5e15ec36ecdb
SHA512: c1705d53c65b27650a02e081c3a8d0d41b18a92415635ceb8350156659efbe1569013c044728318f90225406a889d421b364f2da6d3f8abaf2b1f004f195dd44
Description-en: Signed kernel image generic
 A kernel image for generic.  This version of it is signed with
 Canonical's signing key.
Description-md5: b0fd0df88b1cd31408007b00d2458952
Supported: 5y


Package: linux-image-5.4.0-146-generic
Architecture: amd64
Version: 5.4.0-146.163~18.04.1
Built-Using: linux-hwe-5.4 (= 5.4.0-146.163~18.04.1)
Priority: optional
Section: kernel
Source: linux-signed-hwe-5.4
Origin: Ubuntu
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 10744
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-146-generic
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-146-generic
Conflicts: linux-image-unsigned-5.4.0-146-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-146-generic_5.4.0-146.163~18.04.1_amd64.deb
Size: 10569416
MD5sum: 57348906e8529c1b4fbc4e2c299377ec
SHA1: 84fa3f90293c9f944222c59ca92c9409e01ae6b8
SHA256: eeb1416ed0a7d102979667f9255e6df59ec05b83f702f6415afa191eeba3a926
SHA512: 3efe7ff217604141b588c9d45146ea194fdcf830bdd93664983ac7f448785ec6ce7fc6d435593698d2300e24a6b0917bc74033bc974a250b9eec781e40b3f3b8
Description-en: Signed kernel image generic
 A kernel image for generic.  This version of it is signed with
 Canonical's signing key.
Description-md5: b0fd0df88b1cd31408007b00d2458952
Supported: 5y


Package: linux-image-5.4.0-147-generic
Architecture: amd64
Version: 5.4.0-147.164~18.04.1
Built-Using: linux-hwe-5.4 (= 5.4.0-147.164~18.04.1)
Priority: optional
Section: kernel
Source: linux-signed-hwe-5.4
Origin: Ubuntu
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 10744
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-147-generic
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-147-generic
Conflicts: linux-image-unsigned-5.4.0-147-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-147-generic_5.4.0-147.164~18.04.1_amd64.deb
Size: 10571612
MD5sum: bf8590bc38654971bc74be20755cc187
SHA1: 11d6d18a450ec9b7f75ee2de698c92f880440201
SHA256: 41c2f817060ed266ff5549aad4e4c314327798a3871ebc96aa88276254a2e2bf
SHA512: a8a5ac9fbd84aadeeae849c2dbabdee26d906403d067254e31bf327f008ca1ea93cb31f27bf5bea8b71b330b045fc26d6a81843c467e5b110a017eae15e6d5e2
Description-en: Signed kernel image generic
 A kernel image for generic.  This version of it is signed with
 Canonical's signing key.
Description-md5: b0fd0df88b1cd31408007b00d2458952
Supported: 5y


Package: linux-image-5.4.0-148-generic
Architecture: amd64
Version: 5.4.0-148.165~18.04.1
Built-Using: linux-hwe-5.4 (= 5.4.0-148.165~18.04.1)
Priority: optional
Section: kernel
Source: linux-signed-hwe-5.4
Origin: Ubuntu
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 10744
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-148-generic
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-148-generic
Conflicts: linux-image-unsigned-5.4.0-148-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-148-generic_5.4.0-148.165~18.04.1_amd64.deb
Size: 10571904
MD5sum: 9fc7a399ecd0d9e37af8e488a51a2e53
SHA1: 7c6016485e2959a7b94bf3e23f1c6b0daa35e19f
SHA256: 6625a5c5e8b0922c7fe63730691e875b543f016d2acebd12cc297b46777f66b1
SHA512: af57f45fc304e8b7ee9e60a7e9fd0bd6f381f45002798f67ffd6a3b9fd5587a9f9341de55e5c0795c98a2cc7e4f514b767a5769c71a06dc347a8a3f529946ca2
Description-en: Signed kernel image generic
 A kernel image for generic.  This version of it is signed with
 Canonical's signing key.
Description-md5: b0fd0df88b1cd31408007b00d2458952
Supported: 5y


Package: linux-image-5.4.0-149-generic
Architecture: amd64
Version: 5.4.0-149.166~18.04.1
Built-Using: linux-hwe-5.4 (= 5.4.0-149.166~18.04.1)
Priority: optional
Section: kernel
Source: linux-signed-hwe-5.4
Origin: Ubuntu
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 10748
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-149-generic
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-149-generic
Conflicts: linux-image-unsigned-5.4.0-149-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-149-generic_5.4.0-149.166~18.04.1_amd64.deb
Size: 10573696
MD5sum: cdb544242d047078695f5e871cb290d1
SHA1: 54a7449d96b7a5230948c2f9841abba0d5c65445
SHA256: 90b1b436d3803fb55844339e4af769698ce491c18594b7a675930019ff325002
SHA512: ea45b7a502f21f14b6f9b449ddf04f8d6652903fbbbd149a8a783679700ff7bb1ffe753a058bfa6ba9b5b36056c7c951ee475447988f9ba23a2d42aa066cff9b
Description-en: Signed kernel image generic
 A kernel image for generic.  This version of it is signed with
 Canonical's signing key.
Description-md5: b0fd0df88b1cd31408007b00d2458952
Supported: 5y


Package: linux-image-5.4.0-155-generic
Source: linux-signed-hwe-5.4
Priority: optional
Section: kernel
Installed-Size: 10772
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Version: 5.4.0-155.172~18.04.1
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-155-generic
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-155-generic
Conflicts: linux-image-unsigned-5.4.0-155-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-155-generic_5.4.0-155.172~18.04.1_amd64.deb
Size: 10591052
SHA256: 849788b9ab3a9aa6ed647b79eca8c60623d5c9db267475a99bf17c2f32b64649
SHA1: 803b2601e30173871d5a04e7ac5e78b1108b74a5
MD5sum: 79ad662a7d07c75b8e1869f995669d21
Description: Signed kernel image generic
Description-md5: b0fd0df88b1cd31408007b00d2458952
Built-Using: linux-hwe-5.4 (= 5.4.0-155.172~18.04.1)


Package: linux-image-5.4.0-156-generic
Source: linux-signed-hwe-5.4
Priority: optional
Section: kernel
Installed-Size: 10780
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Version: 5.4.0-156.173~18.04.1
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-156-generic
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-156-generic
Conflicts: linux-image-unsigned-5.4.0-156-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-156-generic_5.4.0-156.173~18.04.1_amd64.deb
Size: 10594908
SHA256: dcd2cdc6fe6ccccd80717ba619a1a4332025085dcf40e096dd3fd23a84d596a3
SHA1: e6aa1e50cb7bc72d6fee0ebb9c381494a1277e89
MD5sum: edc8ed1f4f1abf6734cfcc200f82772a
Description: Signed kernel image generic
Description-md5: b0fd0df88b1cd31408007b00d2458952
Built-Using: linux-hwe-5.4 (= 5.4.0-156.173~18.04.1)


Package: linux-image-5.4.0-159-generic
Source: linux-signed-hwe-5.4
Priority: optional
Section: kernel
Installed-Size: 10780
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Version: 5.4.0-159.176~18.04.1
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-159-generic
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-159-generic
Conflicts: linux-image-unsigned-5.4.0-159-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-159-generic_5.4.0-159.176~18.04.1_amd64.deb
Size: 10595932
SHA256: 09d694cc26a7c121b831070ace0e42916f16dd76bb2d2ee8a98a27baece83bdb
SHA1: e4583b4e799b07f1c03dac7dff290aa4a2af4cd6
MD5sum: 9be5c6cb9139122791e18c9b40971110
Description: Signed kernel image generic
Description-md5: b0fd0df88b1cd31408007b00d2458952
Built-Using: linux-hwe-5.4 (= 5.4.0-159.176~18.04.1)


Package: linux-image-5.4.0-164-generic
Source: linux-signed-hwe-5.4
Priority: optional
Section: kernel
Installed-Size: 10724
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Version: 5.4.0-164.181~18.04.1
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-164-generic
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-164-generic
Conflicts: linux-image-unsigned-5.4.0-164-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-164-generic_5.4.0-164.181~18.04.1_amd64.deb
Size: 10539892
SHA256: 316b415a03475e78f49f2212e9fbf9a287f959fd4b669f82cfeaa8d7fe286053
SHA1: 9c84419f3bd261791f390bf298d91c59a26cb1ff
MD5sum: 5d5d661a87a19c932359dc56c2ea3cf7
Description: Signed kernel image generic
 A kernel image for generic.  This version of it is signed with
 Canonical's signing key.
Description-md5: b0fd0df88b1cd31408007b00d2458952
Built-Using: linux-hwe-5.4 (= 5.4.0-164.181~18.04.1)


Package: linux-image-5.4.0-165-generic
Source: linux-signed-hwe-5.4
Priority: optional
Section: kernel
Installed-Size: 10724
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Version: 5.4.0-165.182~18.04.1
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-165-generic
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-165-generic
Conflicts: linux-image-unsigned-5.4.0-165-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-165-generic_5.4.0-165.182~18.04.1_amd64.deb
Size: 10539884
SHA256: 7727f445f6404083debeb3fd67cfef692d1f57ec2c369feeaf23034439a68f67
SHA1: 5e5a06ff8c2fe994ad2a40b4a68165bbc831d7e1
MD5sum: 4a47d8de4cfdb49c3ae565327d70d0ef
Description: Signed kernel image generic
 A kernel image for generic.  This version of it is signed with
 Canonical's signing key.
Description-md5: b0fd0df88b1cd31408007b00d2458952
Built-Using: linux-hwe-5.4 (= 5.4.0-165.182~18.04.1)
```

Looks like the 165 kernel is in the cache? Should I try and purge it from the cache?

---

### Post by MAFoElffen on 2023-10-27
> **msantangelosdoc said:**
> ```
mike@newsletter:~# sudo apt list linux*-image-5.4.0-[0-5][4-6][4-9]-generic
Listing... Done
...
linux-image-5.4.0-165-generic/bionic-infra-security 5.4.0-165.182~18.04.1 amd64

```
and
```
mike@newsletter:~# sudo apt-cache show linux*-image-5.4.0-[0-5][4-6][4-9]-genericPackage: linux-image-5.4.0-144-generic
Package: linux-image-5.4.0-165-generic
Source: linux-signed-hwe-5.4
Priority: optional
Section: kernel
Installed-Size: 10724
Maintainer: Canonical Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Version: 5.4.0-165.182~18.04.1
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo, initramfs-tools | linux-initramfs-tool
Suggests: fdutils, linux-hwe-5.4-doc-5.4.0 | linux-hwe-5.4-source-5.4.0, linux-hwe-5.4-tools, linux-headers-5.4.0-165-generic
Provides: aufs-dkms, fuse-module, ivtv-modules, kvm-api-4, linux-hwe-5.4-image, redhat-cluster-modules, spl-dkms, spl-modules, virtualbox-guest-dkms, virtualbox-guest-modules, zfs-dkms, zfs-modules
Depends: kmod, linux-base (>= 4.5ubuntu1~16.04.1), linux-modules-5.4.0-165-generic
Conflicts: linux-image-unsigned-5.4.0-165-generic
Filename: pool/main/l/linux-signed-hwe-5.4/linux-image-5.4.0-165-generic_5.4.0-165.182~18.04.1_amd64.deb
Size: 10539884
SHA256: 7727f445f6404083debeb3fd67cfef692d1f57ec2c369feeaf23034439a68f67
SHA1: 5e5a06ff8c2fe994ad2a40b4a68165bbc831d7e1
MD5sum: 4a47d8de4cfdb49c3ae565327d70d0ef
Description: Signed kernel image generic
 A kernel image for generic.  This version of it is signed with
 Canonical's signing key.
Description-md5: b0fd0df88b1cd31408007b00d2458952
Built-Using: linux-hwe-5.4 (= 5.4.0-165.182~18.04.1)
```
[COLOR=#ff0000]Looks like the 165 kernel is in the cache? Should I try and purge it from the cache?[/COLOR]
That's not what you said you wanted to do.... In Post #1, you said:
> **msantangelosdoc said:**
> 
No matter what I do, I can't get  newsletter to get a new kernel up to -165 and I am unsure why. Is there  anything people can suggest? They're both HWE and ESM enabled.
...
Package  linux-image-5.4.0-165-generic is not available, but is referred to by  another package. This may mean that the package is missing, has been  obsoleted, or is only available from another source
```

E: Package 'linux-image-5.4.0-165-generic' has no installation candidate

```
Any advice? Nothing seems out of sorts in apt repos and I am spinning my wheels on this.

You said that VM was stuck on kernel 5.4.0-160 and you were trying to get it to 5.4.0-165, right?

Let's be clear on what you are trying to do... I see those as saying two different things.

Easier to go up, where you are current with all security patches, than to go backwards, pinning a kernel package to stay at the past...

[hr][/hr]
And to be clear... Support for ESM is formally supposed to be done through "Ubuntu Pro". None of us here are connected with Canonical = we are all just volunteers who are users. We have 'ideas', but are not responsible for giving advice on ESM issues. Just saying, the policy here on this Forum is advice on supported releases. So take what we say on that with a grain of salt.

---

