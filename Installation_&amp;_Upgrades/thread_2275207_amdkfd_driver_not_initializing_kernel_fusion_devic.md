---
title: "amdkfd driver not initializing kernel fusion device in UEFI boot under Lubuntu 15.04"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by Retro_Trinity on 2015-04-24
Hi! Our Linux desktop dev/experiment machine has been using the amdkfd driver to initialize a kernel fusion device (kfd) ever since mainline kernel 3.19 was released last year.  We did an upgrade from Lubuntu 14.10 to 15.04 without a hitch, and kernel 3.19.0.15 performs pretty-much as expected.  Okra and aparapi-lambda still work as well as ever.  It should be noted that the upgraded installation is on an mbr partition.

We also installed Lubuntu 15.04 again on a different drive - same machine - on what is a gpt partition (it is sharing the drive with Windows 10).  Our intention is to test Project Sumatra on the new partition.  The installation there also went without a hitch, and grub2 is working just fine.  Everything is normal except for one odd thing: the HSA software stack is broken on the new Lubuntu install.

We couldn't figure out why until we tried booting with hardware IOMMU disabled, which normally produces an error during the boot process (something to the effect that "kfd could not be initialized, is hardware iommu enabled?").  When booting to Lubuntu 15.04 on an mbr partition with IOMMU disabled, we still get that error.  When booting to Lubuntu 15.04 on an gpt partition, we get no such error.  The kfd is not initializing, despite the fact that both installations of Ubuntu are using the same kernel! Well, almost.

We also noticed that the kernel packages are slightly different under a UEFI boot: there's an extra package called linux-signed-image3.19.0.15-generic.

Obviously, something is wrong with the signed kernel.  The reason for the signed image is described in Synaptic: it has Canonical's UEFI signing key.  But apparently something about this package is preventing amdkfd from working! Can anyone please shed some light on this problem?

---

### Post by Retro_Trinity on 2015-04-26
Just an update: we had someone look through the source for linux-signed-image-3.19.0.15-generic and it doesn't look like anything specifically to do with amdkfd is in that package.  It looks like that package is only related to secure booting, which means UEFI boot should (theoretically) be possible without that package being installed.  So, it is less clear than before why UEFI booting to 15.04 installed on a gpt partition is messing up initialization of the kfd under 3.19.

Any help would be greatly appreciated, thanks!

---

### Post by Retro_Trinity on 2015-04-28
UEFI boot was a red herring.  The real problem was that you need a kfd.rules file in /etc/udev/rules.d .  The file must say:

```

KERNEL=="kfd", MODE="0666"

```

Installing mainline 3.19 in Ubuntu 14.10 created this file during package installation (we think?), but Ubuntu 15.04 does not create this file by default.  You must do it by hand.  Then the HSA software stack works! Problem solved.

---

