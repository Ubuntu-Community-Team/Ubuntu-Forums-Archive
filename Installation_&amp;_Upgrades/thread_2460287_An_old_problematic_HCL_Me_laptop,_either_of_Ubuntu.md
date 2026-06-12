---
title: "An old problematic HCL Me laptop, either of Ubuntu or Debian Live ISOs won't run"
date: 2021-04-06
forum: Installation &amp; Upgrades
---

### Post by bkpsusmitaa on 2021-04-06
Well, they run only up to a point, both the latest 20.10 Ubuntu LTS and Debian Live. Have been running Ubuntu LTS 14 for a long time, but need upgrade.

The problematic Hardware are:
(1) Audio device        : NVIDIA Corporation MCP79 High Definition Audio (rev b1)
(2) VGA compatible controller        : NVIDIA Corporation MCP79 [GeForce 8200M G] (rev b1) (prog-if 00 [VGA controller])

So every OS based on Debian, i.e., Knoppix and Ubuntu, won't go beyond init 3. Once the system is installed and then the drivers are downloaded and installed from the website of NVIDIA Corporation, the system works quite well. It is an old laptop, but with 4GB RAM works exceptionally well even currently.

Need to update old Ubuntu. Have only one old Knoppix running. All user files have been safely moved. But unless Live Ubuntu ISO runs (Debian Live ISO has installation option too), can't have the Ubuntu installation running. Catch 22 situation.

Have recorded some notes for either of Debian and Ubuntu:

Debian:
----------
[https://www.debian.org/CD/faq/#write-usb]("https://www.google.com/url?q=https%3A%2F%2Fwww.debian.org%2FCD%2Ffaq%2F%23write-usb&sa=D&sntz=1&usg=AFQjCNEpycQz09aJJaakXhn4XwwdSX3uAA")

Several of the Debian and Debian Live images, notably all i386, amd64
and arm64 images, are created using the isohybrid technology, which
means that they may be used in two different ways:

    They may be written to CD/DVD/BD and used as normal for CD/DVD/BD booting.
    They may be written to USB flash drives, bootable directly from
the BIOS / EFI firmware of most PCs.

On a Linux machine, simply use the "cp" command, to copy an image to a
USB flash drive:

cp <file> <device>

Alternatively you can also use "dd":

dd if=<file> of=<device> bs=4M; sync

where:

    <file> is the name of the input image, e.g. "netinst.iso"
    <device> is the device matching the USB flash drive, e.g.
/dev/sda, /dev/sdb. Be careful to make sure you have the right device
name, as this command is capable of writing over your hard disk just
as easily if you get the wrong one!
    "bs=4M" tells dd to read/write in 4 megabyte chunks for better
performance; the default is 512 bytes, which will be much slower
    The "sync" is to make sure that all the writes are flushed out
before the command returns.


Ubuntu:
----------
ISO from page [https://releases.ubuntu.com/20.10/ubuntu-20.10-desktop-amd64.iso]("https://www.google.com/url?q=https%3A%2F%2Freleases.ubuntu.com%2F20.10%2Fubuntu-20.10-desktop-amd64.iso&sa=D&sntz=1&usg=AFQjCNGendaiRV6Wd_EUq5ktz0j0sJFflg")

[https://releases.ubuntu.com/20.10/]("https://www.google.com/url?q=https%3A%2F%2Freleases.ubuntu.com%2F20.10%2F&sa=D&sntz=1&usg=AFQjCNF2PQP-A88FPiHJuK-I1TVZIjMC9w")

String search
write "USB boot drive" with
[https://releases.ubuntu.com/20.10/ubuntu-20.10-desktop-amd64.iso]("https://www.google.com/url?q=https%3A%2F%2Freleases.ubuntu.com%2F20.10%2Fubuntu-20.10-desktop-amd64.iso&sa=D&sntz=1&usg=AFQjCNGendaiRV6Wd_EUq5ktz0j0sJFflg") site:
[ubuntuforums.org/]("http://www.google.com/url?q=http%3A%2F%2Fubuntuforums.org%2F&sa=D&sntz=1&usg=AFQjCNERoroCbekRq4tc95jdmgIi5hxpGQ")

leads to:
[https://help.ubuntu.com/community/mkusb]("https://www.google.com/url?q=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2Fmkusb&sa=D&sntz=1&usg=AFQjCNF8uCpohxlFFPjkBcKHNw-2fkgjHQ")

and [https://help.ubuntu.com/community/mkusb/isohybrid]("https://www.google.com/url?q=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2Fmkusb%2Fisohybrid&sa=D&sntz=1&usg=AFQjCNHpiR0RHBN3_4tpnJhaWXeoTdY_fw")

Some questions:

What is the benefit of mkusb in comparison to dd? Why not use the dd instead of mkusb?

**Please note** that my HCL laptop **doesn't** require a **Lightweight** system like Lubuntu. It is **quite robust **to handle **heavyweight operations** still. Just that the **motherboard audio and video chips** are its **Achilles** **heels**.

Final Open Question:
----------------------------
Any advice in this regard?

---

