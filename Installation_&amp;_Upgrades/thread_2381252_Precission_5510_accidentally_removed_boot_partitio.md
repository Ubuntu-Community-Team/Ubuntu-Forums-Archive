---
title: "Precission 5510 accidentally removed boot partition"
date: 2017-12-28
forum: Installation &amp; Upgrades
---

### Post by tim-rijckaert on 2017-12-28
Hi there, long time Ubuntu user first question;

While wanting to format my SD-card of 4gigs I accidentally removed a 4gig partition on my main drive in GParted. I believe this was a boot partition :(.
The system obviously wouldn't boot anymore.
Not even showing Grub.

I tried the Recommanded Repair from [Boot-Repair-Disk]("https://sourceforge.net/p/boot-repair-cd/home/Home/"), but it almost fails immediately with:

GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

Since I already proved myself as an expert on Gparted I came here looking for some answers or guidance. I have a 512gig NVME SSD in RAID0 if that helps.
Also this laptop came with Ubuntu 14.04 pre-installed.
I'll also attach a link to my BootInfo [here]("https://paste.ubuntu.com/26272258/").

The logs state I'm not in UEFI, but my BIOS is set to UEFI?

Any idea how I can boot back into Ubuntu without completely reinstalling Ubuntu?
Thanks in advance.
Tim

---

