---
title: "Install hang at detecting file systems"
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by chenzhiwei2 on 2014-09-20
Hi all,

When I try to install Ubuntu on my Desktop, I encountered errors.

The installation will hang at "Detecting file systems", and I don't know how to solve it.

I tried below methods to solve this error:

1. Mount `/` as ext3/ext4/brtfs format.

2. Using 14.04/13.04/12.04 and encountered the same error.

There is already two OS on my Desktop, they are Win7 and Deepin.

My install type is to put vmlinz.efi and initrd.lz to Win7 C's root directory, and also put the ubuntu ISO to this root directory. Then use EasyBCD to set an installation menu. I did this and installed Deepin, but can't install Ubuntu.

Screenshots below are the full step of installation:

A. Choose installtion type [Something else]

[ATTACH=CONFIG]256563[/ATTACH]

B. /dev/sda10 uses ext4 filesystem type, and mounted as `/`.

[ATTACH=CONFIG]256564[/ATTACH]

C. Hang at `Detecting file systems...`

[ATTACH=CONFIG]256565[/ATTACH]

Can anyone give some tips? This is an weird issue.

And when I try to access partitions of Windows7, I got this error `unable to access 'xxxx', Not authorized to perform operation`.

[ATTACH=CONFIG]256566[/ATTACH]

I am not sure this is an EFI issue, I used GIGABYTE B85 and Intel i3-4150.

[ATTACH=CONFIG]256567[/ATTACH]


========================

After my latest try, I was successfully installed Ubuntu 14.04.1, I don't know the reason.

---

