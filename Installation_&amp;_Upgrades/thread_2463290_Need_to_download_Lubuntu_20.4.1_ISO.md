---
title: "Need to download Lubuntu 20.4.1 ISO"
date: 2021-06-08
forum: Installation &amp; Upgrades
---

### Post by kjgrimm on 2021-06-08
Hello, I am new to this forum, so hopefully following the rules correctly.

I am seeking an LTS version of Lubuntu, with kernel 5.4, which is supported for 5 years. I recently downloaded the latest Lubuntu Desktop from here: [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)
which provides the latest Point Release, which is Lubuntu 20.4.2. But it does also offer a link to download previous versions: [https://cdimage.ubuntu.com/lubuntu/releases/](https://cdimage.ubuntu.com/lubuntu/releases/) 

Unfortunately, that second link only serves up Lubuntu 20.4.2, no matter what directory you choose. I went to here for example: [https://cdimage.ubuntu.com/lubuntu/releases/20.04.1/release/](https://cdimage.ubuntu.com/lubuntu/releases/20.04.1/release/)
but it too only offers 20.4.2. 

I am wondering if anyone can assist. Is it still possible to obtain an ISO for Lubuntu Desktop 20.4.1? Or should I just install 20.4.2 and manually downgrade the kernel (I suspect that might not be safe).
Appreciate assistance if anyone knows.

Thanks.

---

### Post by ActionParsnip on 2021-06-08
You can downgrade the kernel without issue, you'll just the older kernel alongside the newer ones that come down with updates.

---

### Post by Impavidus on 2021-06-08
Lubuntu LTS releases only get 3 years of support. The parts they have in common with Ubuntu (like the kernel) get 5 years.

If you install from the 20.04.2 iso, you'll get kernel 5.8. This will be automatically upgraded every 6 months until you get the same kernel as will be used in Ubuntu 22.04 (whatever that will be), which will be supported for the remainder of the support period of 20.04. With more major kernel upgrades, there's more risk one of them fails. If your hardware is old enough that the 5.4 kernel works, that may be a reason to stay with 5.4

If you install from the 20.04.1 iso, some flavours give you the 5.4 kernel, others the 5.8 kernel. I don't know what Lubuntu does. But you can easily downgrade. Just use the package manager to remove the hwe kernel metapackage and install the standard kernel metapackage. After rebooting on the 5.4 kernel, you can autoremove the 5.8 packages.

The 20.04.1 isos must be archived somewhere with the old releases.

---

### Post by sudodus on 2021-06-08
> **Impavidus said:**
> Lubuntu LTS releases only get 3 years of support. The parts they have in common with Ubuntu (like the kernel) get 5 years.

If you install from the 20.04.2 iso, you'll get kernel 5.8. This will be automatically upgraded every 6 months until you get the same kernel as will be used in Ubuntu 22.04 (whatever that will be), which will be supported for the remainder of the support period of 20.04. With more major kernel upgrades, there's more risk one of them fails. If your hardware is old enough that the 5.4 kernel works, that may be a reason to stay with 5.4

If you install from the 20.04.1 iso, some flavours give you the 5.4 kernel, others the 5.8 kernel. I don't know what Lubuntu does. But you can easily downgrade. Just use the package manager to remove the hwe kernel metapackage and install the standard kernel metapackage. After rebooting on the 5.4 kernel, you can autoremove the 5.8 packages.

Please describe with command lines how to remove the hwe kernel metapackage and install the standard kernel metapackage :-P
> 
The 20.04.1 isos must be archived somewhere with the old releases.

I show 4 work-arounds to get Lubuntu 20.04 with the original kernel series at [this link](https://askubuntu.com/questions/1344457/cant-locate-iso-for-lubuntu-20-04-1/1344459#1344459) to the same question at AskUbuntu.

---

### Post by ajgreeny on 2021-06-08
You can install the 20.04.2 version and then simply remove all the packages with **-hwe** in their names.

Start by removing ***linux-generic-hwe-20.04*** and install the plain ***linux-generic*** which will immediately pull in the most recent 5.4.0-74 kernel plus dependencies, eg the header packages.

You can then reboot to the 5.4 series from grub and remove linux-image-5.8.0-55-generic along with any other versions of the 5.8 series.
Finally run ***sudo apt autoremove --purge*** and you should end up with the same as you would have had with the starting point of Lubuntu-20.04.1, which incidentally, I can not find either, all links that suggest they are for the 20.04.1 version end up at the same point with the 20.04.2 version.

I have done this simply as a test using a virtual install to make sure it is possible. 
In my case I did not even reboot after removing the running kernel but simply installed the 5.4 series in the same operation using synaptic in my case, which would be muon I believe in Lubuntu.
Doing it in one go will give you warnings about removing the current running kernel, but it's OK as long as you do not reboot before installing the earlier version of kernel.

---

### Post by guiverc on 2021-06-08
Also asked at [https://askubuntu.com/questions/1344457/cant-locate-iso-for-lubuntu-20-04-1](https://askubuntu.com/questions/1344457/cant-locate-iso-for-lubuntu-20-04-1)

---

### Post by ActionParsnip on 2021-06-08
Could always install Ubuntu server then install LXDE. This will give you 5 years of support rather than the 3 with Lubuntu

---

### Post by sudodus on 2021-06-08
> **ActionParsnip said:**
> Could always install Ubuntu server then install LXDE. This will give you 5 years of support rather than the 3 with Lubuntu

Yes , it is possible to use LXDE

But

- Lubuntu left LXDE and started using LXQt because LXDE was not very actively developed, so there may be problems with new features and who knows about security updates.

- If I remember correctly, some important developers of LXDE and associated tools moved to LXQt, for example pcman (developer of pcmanfm).

---

### Post by Impavidus on 2021-06-08
> **sudodus said:**
> Please describe with command lines how to remove the hwe kernel metapackage and install the standard kernel metapackage :-P


Sensible request.

Install the package **linux-generic** and remove **linux-generic-hwe-20.04**, using apt, apt-get or one of the GUI package managers. When running the 5.4 kernel, the 5.8 packages (5 per kernel version and a few metapackages) should be autoremovable. Exact command lines are left as an exercise to the reader.

It could be slightly different if you use the unsigned or lowlatency kernels or something like that, but those are not automatically installed on Lubuntu.

---

### Post by sudodus on 2021-06-08
Thanks ajgreeny and Impavidus for the details about downgrading the kernel :KS

---

### Post by kjgrimm on 2021-06-11
Thanks Impavidus, I have been struggling to understand how LTS worked, and why Lubuntu would offer kernel 5.8 with 20.04.2, which is only supported for 9 months. Now it makes sense.

---

### Post by kjgrimm on 2021-06-11
Hi Sudodus. Yes, it does worry me a bit that the Lubuntu team seems to have been split in two. But Ubuntu seems to be supporting lubuntu.me, and LXQt, so that is what I am working with. But I will presume that an upgrade is required by 2023, rather than 2025.

---

### Post by kjgrimm on 2021-06-11
Thanks very much ajgreeny. I have also tested this on a VM, and it worked.

---

### Post by guiverc on 2021-06-11
> **kjgrimm said:**
> Thanks Impavidus, I have been struggling to understand how LTS worked, and why Lubuntu would offer kernel 5.8 with 20.04.2, which is only supported for 9 months. Now it makes sense.

20.04 is available with two kernel choices..

The GA kernel is 5.4 and is supported for the full five years of it's life (even if *flavors* only offer 3 years of support; ie. Lubuntu; 5 years applies to packages from the 'main' repository, ie. those in common with Ubuntu Desktop, Ubuntu Server etc).

The HWE kernel stack choice allows you to use later stacks from non-LTS releases. 

- For 20.04.2 that means the stack from 20.10 (5.8)
- For 20.04.3 that means the stack from 21.04 (5.11)

etc.  until the final stack is used at 20.04.5 being the GA stack from Ubuntu 22.04 (whatever kernel that is).  If you look at the *focal* schedule ([https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule](https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule)) you'll see the ISO is scheduled for release on 19 August 2021, however installed systems will upgrade before that date (ie. installed systems will auto-shift to using the 5.11 kernel currently used by *hirsute* or 21.04 users).

For details on HWE please refer

- [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
- [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

> **kjgrimm said:**
> Yes, it does worry me a bit that the Lubuntu team seems to have been split in two. 

Projects always have people leaving (*busy with other parts of their lives*), and new people joining on.

LXDE used GTK2 libraries which are EOL (GNOME 3 & GTK3 came out years ago, GTK4 is the new one now).  PCMan (mentioned by @Sudodus) ported `pcmanfm` (file manager & handles the desktop of LXDE) to GTK3 but blogged how much heaver GTK3 was. Given the L in LXDE is *light*, a port to Qt5 was done for comparison and it was much lighter.  Thus a majority of LXDE devs joined with Razor-Qt team members creating a new LXQt project; the successor of LXDE.  This however is all *upstream* of Lubuntu.

I'm not sure what you mean by *split in two* though. 

If it's about lubuntu[.net] ; that was **never** a Ubuntu/Canonical/Lubuntu web site; was privately owned and whilst yes, it was used by Lubuntu for awhile, when the owner of the site left the project it was beyond the reach of Ubuntu & Lubuntu so was replaced. This may not be what you mean (all Ubuntu & official links always point to the correct site, even if search engines like google offer many choices, *legit*, *fan* & *fake*).  

FYI: If you check ownership of lubuntu.me, you'll note it's owned by Canonical; the company behind Ubuntu, to ensure ownership of a site isn't lost again.

You'll be able to *release-upgrade* to the next LTS soon **after **22.04.1 has been released, but will have ~6 months after that before the 3 years of supported-life of Lubuntu 20.04 LTS reaches EOL for the Lubuntu team. *(technically you'll still have two years after that before all of 20.04 reaches the end of it's standard support life, so upgrades will be still be possible during this period as well; it's primarily that Lubuntu won't support you**).*

If you have questions about Lubuntu, ask them.  Many of the people here are Lubuntu members  (*my chosen beans-graphic is Ubuntu member as I achieved that first, but I'm Lubuntu member too*), and even if some folks aren't associated with the project, they likely still contain useful opinions.

---

### Post by sudodus on 2021-06-12
+1; I agree about the details explained by @guiverc. (My post was brief and could be misunderstood.)

---

### Post by mikewhatever on 2021-06-12
There is a bittorrent archive of ISOs at [https://distrowatch.com/dwres.php?resource=bittorrent](https://distrowatch.com/dwres.php?resource=bittorrent). 
Lubuntu 20.04.1 is available at [https://distrowatch.com/dwres/torrents/lubuntu-20.04.1-desktop-amd64.iso.torrent](https://distrowatch.com/dwres/torrents/lubuntu-20.04.1-desktop-amd64.iso.torrent).
There are lots of peers, works well.

---

### Post by grahammechanical on 2021-06-12
If we are wondering why an ISO image of Ubuntu/Lubuntu/other flavours is  no longer available then the answer is the BootHole vulnerability in  the Grub boot loader.

[https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

The  fix to Grub could not be backported to ISO images that had already be  built and put out for download. So those earlier releases of the ISO  image with Grub still having the BootHole vulnerability were backlisted  in the UEFI secure boot database and I also guess where removed from  Canonical ISO image download repositories.

In the above linked to document continue reading until you get to the paragraph that reads

> Unlike other security vulnerabilities, where the software update can be  released and installed to remediate the vulnerability , the nature of  UEFI Secure Boot created significant complications.

It also says

> These old install media would then always be trusted, even though they  contain this vulnerable version of GRUB2 and hence could be used to  bypass UEFI Secure Boot on any system.

Use one of these  old install media and we install a version of Grub with some very  serious security flaws that are not present in newer install media.

Regards

---

