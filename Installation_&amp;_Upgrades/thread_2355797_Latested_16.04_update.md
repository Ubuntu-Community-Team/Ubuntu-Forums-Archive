---
title: "Latested 16.04 update"
date: 2017-03-16
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2017-03-16
Hi, where can I find information on what the latest update to the version I am using.

I am using 16.04 and today there were updates to the kernel. I was wondering why and what is new/changed in the kernel and any other updates that were included.

Thanks in advance. Bob.

---

### Post by howefield on 2017-03-16
Not sure if this is what you mean..

[https://lists.ubuntu.com/archives/xenial-changes/](https://lists.ubuntu.com/archives/xenial-changes/)

---

### Post by bob brazie on 2017-03-16
No not really. There have been several updates in just this month and I am wondering what was changed and why.
In the download list there is a section you can click to see an explanation for each new update.
This is the information I am looking for.

---

### Post by Bashing-om on 2017-03-16
bob brazie; Hello;

System tells all, if one just knows what to ask and where .

Take a look in the system logs.
A place to start is :
```

cat /var/log/apt/history.log
cat /var/log/unattended-upgrades/unattended-upgrades-dpkg.log

```

[INDENT][INDENT]who what when where AND why
[/INDENT][/INDENT]

---

### Post by bob brazie on 2017-03-16
Thanks, the commands give me a list of the upgrades but not an explanation of what and why it was changed.

---

### Post by howefield on 2017-03-17
Using the mutt package as an example, how about

```
apt-get changelog mutt | more
```

you get a reverse chronologically ordered changelog with output as follows ..

```
apt-get changelog mutt | more
Get:1 http://changelogs.ubuntu.com mutt 1.7.2-1 Changelog [106 kB]
mutt (1.7.2-1) unstable; urgency=medium

  * New upstream Mutt release.
  * New upstream NeoMutt release, 2017-01-13.
  * debian/patches:
    + all patches refreshed.
    + upstream/gpgme-set-sender.patch removed because it is already upstream.

 -- Antonio Radici <antonio@debian.org>  Fri, 20 Jan 2017 21:47:49 +0000

mutt (1.7.1-5) unstable; urgency=medium

  * debian/patches:
    + add upstream/gpgme-set-sender.patch otherwise the package
      does not build due to conflicting declarations.

 -- Antonio Radici <antonio@debian.org>  Thu, 01 Dec 2016 20:41:44 +0000

mutt (1.7.1-4) unstable; urgency=medium

  * New upstream NeoMutt release, 2016-11-26.
    + All patches refreshed.
    + upstream/549204-clear-N-on-readonly-imap-folders.patch pulled from the
      repo because it could cause bad interactions with the pager (I will
      revisit the decision in the next release).
  * debian/rules:
    + explicitely added --with-tokyocabinet otherwise the package does not
      build.

 -- Antonio Radici <antonio@debian.org>  Thu, 01 Dec 2016 08:28:54 +0000

snipped the rest for brevity
```

Pressing Q quits from the output if you don't want to go all the way back.

Example for the kernel on this machine..

```
apt-get changelog linux-image-4.10.0-13-generic | more
Get:1 http://changelogs.ubuntu.com linux 4.10.0-13.15 Changelog [661 kB]
linux (4.10.0-13.15) zesty; urgency=low

  [ Tim Gardner ]

  * Release Tracking Bug
    - LP: #1671614

  * ehci-platform needed in usb-modules udeb (LP: #1671589)
    - d-i: add ehci-platform to usb-modules

  * irqchip/gic-v3-its: Enable cacheable attribute Read-allocate hints
    (LP: #1671598)
    - irqchip/gic-v3-its: Enable cacheable attribute Read-allocate hints

  * iommu: Fix static checker warning in iommu_insert_device_resv_regions
    (LP: #1671599)
    - iommu: Fix static checker warning in iommu_insert_device_resv_regions

  * QDF2400: Fix panic introduced by erratum 1003 (LP: #1671602)
    - arm64: Avoid clobbering mm in erratum workaround on QDF2400

  * QDF2400 PCI ports require ACS quirk (LP: #1671601)
    - PCI: Add ACS quirk for Qualcomm QDF2400 and QDF2432

  * tty: pl011: Work around QDF2400 E44 stuck BUSY bit (LP: #1671600)
    - tty: pl011: Work around QDF2400 E44 stuck BUSY bit

  * CVE-2017-2636
    - tty: n_hdlc: get rid of racy n_hdlc.tbuf

  * Sync virtualbox to 5.1.16-dfsg-1 in zesty (LP: #1671470)
    - ubuntu: vbox -- Update to 5.1.16-dfsg-1

 -- Tim Gardner <tim.gardner@canonical.com>  Thu, 09 Mar 2017 06:16:24 -0700

linux (4.10.0-12.14) zesty; urgency=low

  [ Tim Gardner ]
```

---

