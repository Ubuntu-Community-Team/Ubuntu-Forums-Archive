---
title: "Can't install Ubuntu"
date: 2021-05-24
forum: Installation &amp; Upgrades
---

### Post by SixOfOne on 2021-05-24
Ubuntu is failing to install from a usb, i get a few seconds of Ubuntu's coloured screen then the error messages.
System is a gigabyte mobo with amd ryzen 5 3500x cpu, 32 gig corsair ram, radeon rx 5500xt graphics card and a kingston 500 gig ssd

In the past I have never had any problems installing Ubuntu but I've not played with linux for a few years and it seems things have changed.

Error message (not replicated with case sensitive)
[0.601950] ACPI bios error (bug); failure creating named object [\sb.pcio.gpp8.dsm] AE_already_exists (20200528/dsw load 2-326)
[0.601950] ACPI error: AE already exists, during name lookup/catalog (20200528/psobject-220)
[0.945620] R8169 0000:7.00.0: unknown chip XID 641

I'm starting to think God believes i should give up gaming as my trouble started a month ago when MS released an update for win 10 with a known faulty scsi driver that trashed gigabyte mobo's with x570 chipset.
when i finally got that sorted amd trashed the OS with faulty adrenalin graphics drivers..
So, I heard linux had made great advances in the last few years as far as gaming went so i came back and can't even get it to install.

Any ideas on what to do would be greatly appreciated.

---

### Post by TheFu on 2021-05-24
Look for special BIOS settings for the Ryzen CPU and AMD GPU you are using in the Release notes for the specific version of Ubuntu you are attempting to install.
The last few releases, Canonical has been swapping the installation program used each time, so please say exactly which release you are attempting to install.  Normally, I'd say to use 20.04, but with bleeding edge CPU/GPU, sometimes newer kernels are needed. That means using a newer release - which really isn't recommended for people new to Linux.  LTS releases happen in April of even years and get either 3 or 5 yrs of support depending on the specific GUI used.  If a "server" install is used, which doesn't have any GUI, then 5 yrs of standard support is provided with 3-5 additional years of extended support for a limited number of system - or there are paid support offers if more than a few systems need that longer support.

Any release after 20.04 available today gets 9 months of support from the release date, so plan to migrated to the next release every 6 months. There is no choice.

Dog is not involved. Neither is Bob.

---

### Post by ubfan1 on 2021-05-24
Check the vendor's site for any firmware updates.  Those may solve many isues.

---

### Post by SixOfOne on 2021-05-24
The version I'm trying to install is 20.04.2.0 Desktop AMD64 LTS
The mobo is a brand new Gigabyte B550 Aorus Pro and I will check for updates
will also check release notes.

There will be a slight pause in my quest as I'm going interstate for a week tomorrow, but at least I have somewhere to start looking,
Thanks

---

### Post by TheFu on 2021-05-24
Google found this:
[https://askubuntu.com/questions/1234299/amd-ryzen-5-3600-ubuntu-20-04-problems/1241636#1241636](https://askubuntu.com/questions/1234299/amd-ryzen-5-3600-ubuntu-20-04-problems/1241636#1241636)
and [https://www.reddit.com/r/Amd/comments/eka8e8/linux_support_for_ryzen_36003700x3900x/](https://www.reddit.com/r/Amd/comments/eka8e8/linux_support_for_ryzen_36003700x3900x/)

The goal is to get an OS installed, then try to find the best performance options.  I know my Ryzen 2600 is picky about RAM and won't boot the 3200Mhz RAM any faster than 2800Mhz speeds with the XMP profile.  I have 2 separate RAM kits (4 sticks total), same part number, but purchased a year apart, so they aren't "matched." They are in the approved RAM list. I believe if my sticks were all a matched set, then 3200 would be possible using the default profile.

I hadn't used AMD since around 2005, so I had to learn all the AMD terms for what I knew as Intel terms in the BIOS.  18.04 and later should be fine with Ryzen 3xxx CPUs. I've not heard of a 3500x. There is a 3600x and 3700x, most definitely.

Has Gigabyte changed their "we only support Windows" stance?  Last time I needed help from them, that was the only answer I got.  They aren't anti-Linux, but they weren't willing to be helpful either.  Definitely get the latest BIOS. Without support from the MB maker, you get to replace components and try booting lots of different Linux distros - trial and error - to see which work and which don't.

I'd pull 18.04, 20.04, 21.04 Ubuntu and Ubuntu-Mate, create a milti-boot flash drive and try them all, taking careful notes of console messages. To see the console messages, hit <esc> when the first images are displayed. Use the "Try Ubuntu" option - don't install for these tests.

---

### Post by oldfred on 2021-05-24
AMD systems often need IOMMU disabled. In addition to UEFI firmware & SSD firmware updates.
And best to use newest Ubuntu distribution to have newest kernel & drivers.

[https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397](https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397)

---

### Post by TheFu on 2021-05-24
I have IOMMU enabled on an Asus B450 and Ryzen 2600. It is critical for PCIe passthru to work.

```
$ dmesg |grep -i iommu
[    0.438496] iommu: Default domain type: Translated 
[    1.113025] pci 0000:00:00.2: AMD-Vi: IOMMU performance counters supported
....
[    1.117194] pci 0000:00:00.2: AMD-Vi: Found IOMMU cap 0x40
[    1.118186] perf/amd_iommu: Detected AMD IOMMU #0 (2 banks, 4 counters/bank).
```

That isn't a B550 nor a Ryzen 3xxx, which could be very different.

My grub command line (BIOS mode, not UEFI) doesn't disable IOMMU. Inside /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 fsck.mode=force fsck.repair=yes"
```
No iommu=off there.
I'm not ready to secure IPv6, so it is disabled.
Got tired of fighting with systemd changes that broke old capabilities related to */forcefsck* existing to get fsck to happen at the next boot. Just easier to always force it, especially on an SSD. I'd actually forgotten I'd put that setting in months ago. Think I'll keep it. On systems without SSDs, I override the fsck settings for each file system to happen every 30 days.

FWIW, I get warnings on ssh connections about fsck being run at the next reboot:
```
Your Hardware Enablement Stack (HWE) is supported until April 2023.
*** /dev/mapper/istar--vg-root will be checked for errors at next reboot ***
*** /dev/mapper/istar--8TB-istar--back3--b will be checked for errors at next reboot ***
*** /dev/mapper/istar--vg3--back-lv_media3_back will be checked for errors at next reboot ***
*** /dev/sde2 will be checked for errors at next reboot ***
*** /dev/mapper/istar--vg2--back-lv_media2_back will be checked for errors at next reboot ***
*** /dev/mapper/istar--stuff-lv--tv will be checked for errors at next reboot ***
*** /dev/mapper/istar--vg-lv_media will be checked for errors at next reboot ***
*** /dev/mapper/istar--vg2-lv_media2 will be checked for errors at next reboot ***
```
Really which it didn't use the "mapper" directory symlinks for feedback, since the /dev/{vg}/{lv} links are what get used everywhere else and convey information much more clearly.

```
$ uptime 
 07:35:31 up 19 days, 21:51,
```
I don't reboot without a specific reason. All sorts of automation around here. Never know when a file on that storage will be needed by some other system. Sometimes our days shift to match client hours.

---

### Post by SixOfOne on 2021-06-04
Solved........ replaced radeon 5500 graphics card with old gtx950 and ubuntu installed no problems (well there's a network issue)
also win 10 also installed without crashing.
Card is being sent back for testing.

---

### Post by TheFu on 2021-06-04
To mark a thread SOLVED, please use the *Thread Tools* button near the top. This helps all parts of the community.

---

