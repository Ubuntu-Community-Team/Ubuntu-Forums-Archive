---
title: "New Install Plan - Have Questions - Semi ish sudo familiar ish"
date: 2020-04-19
forum: Installation &amp; Upgrades
---

### Post by mclaughlin-peter on 2020-04-19
Howdy,

So new here, figured i'd ask and waive the noob flag and admit, I truly don't have the answers and wish to learn. (Serious)

[https://www.msi.com/Motherboard/support/Z87-GD65-GAMING#](https://www.msi.com/Motherboard/support/Z87-GD65-GAMING#)

That's the motherboard i'll have.

I"m intending with additional raid cards, etc... (pci-e 1x or 4x depending variant).

To have...

3x 4tb 3.5"
4x 1tb 3.5" (some internal, some in external enclosures on usb 3 or esata)
Some additional 2.5" drives such as.

1x 1tb
1x 500gb, 320, 250, 200gb (old drives)

They're all smart stat 100%, pre formatted initial NTFS just so the main ubuntu install can see it, then I can journal/format it properly to best recommended for performance options.


Intention of install:

- Plex
- Virtual Machines
- Folding@Home (Fight covid! Yay!)
- Stand alone box/auto login for easy update reboots. Using KVM with integrated Intel4600hd...


Specs:

z87-GD65 Gaming motherboard.
i5 4670k (stock, no overclock, solid cooling but... playing nice).
32gb ddr3/xmp/2400.

Intel HD4600 video (vga/dvi/hdmi, using dvi only, 1080p screen, single).

Specs of pci-e cards:

2 of them I found online, the other 2 not sure exactly until I plug them in...

[https://www.amazon.ca/IOCrest-SI-PEX40098-Port-SATA-RAID/dp/B010B716BI](https://www.amazon.ca/IOCrest-SI-PEX40098-Port-SATA-RAID/dp/B010B716BI)

& 

[https://www.tweaktown.com/reviews/7281/vantec-ugt-pc370a-2-port-usb-3-1-gen-ii-type-pcie-card-review/index.html](https://www.tweaktown.com/reviews/7281/vantec-ugt-pc370a-2-port-usb-3-1-gen-ii-type-pcie-card-review/index.html)



Reference pictures "of" the cards..

[https://photos.app.goo.gl/GYcNkWo6iNhRLCFLA](https://photos.app.goo.gl/GYcNkWo6iNhRLCFLA)

Back & Front in HD as best as possible.




My ask,

Will I be needing drivers potentially? Or something of the equivalent?

Any special install suggestions? Or flavours of ubuntu that I should delve more into?

I'm seeking performance options, power is not a concern as i'll have a 650+watt psu to handle this (measured amps required etc, and have surplus headroom for spikes/max usage etc).

Intending to push this system.


Any apps you would recommend or monitoring tools, for smart / temps / Traffic?


I use also a windows and apple system, and i'd like to use this as a data "esk" server like concept. So i'm aiming, network drives, etc. (I have a gigabit nic as well, separate from motherboard incase of any challenges).

Thanks in advance for review.


Regards,

- RMLeLoup

---

### Post by grahammechanical on 2020-04-19
Decision time. Ubuntu Desktop Edition or Server Edition? Or both? At the end of April the latest version of Ubuntu will be released. It is called 20.04. The latest is the greatest. It will have the best hardware support as part of the Linux kernel. The latest hardware needs the latest Linux/Ubuntu OS.

And Ubuntu 20.04 is a Long Term Support (LTS) version.

[https://ubuntu.com/blog/what-is-an-ubuntu-lts-release](https://ubuntu.com/blog/what-is-an-ubuntu-lts-release)

I am not sure if the server version comes with video card drivers. Not supposed to be needed? But the desktop version does. Anyway we can add and remove programs as we like to get the system that we prefer.

Regards.

---

### Post by TheFu on 2020-04-19
Don't use HW-RAID or Fake-RAID.  Use SW-RAID, but only if you must and only AFTER you have backups 100% sorted first.  If the VMs aren't Windows, you'll probably only need 4-8G of storage for each VM.  Just depends on the data.  If you deploy using LXD, move the zero left - 10x less storage needed for the OS.  If you need a JBOD storage card, get one from LSI and make certain the drivers are included in the Linux kernel first.  Claims of RAID drivers for Linux are usually for any other kernel than you have and bring all sorts of issues.  The only time anyone should use a HW-RAID card is if there is a battery included in the RAID controller to ensure writes complete after a power hit.  Any others just aren't worth it and aren't as fast as Linux SW-RAID.  
Read this: [https://arstechnica.com/information-technology/2020/04/understanding-raid-how-performance-scales-from-one-disk-to-eight/](https://arstechnica.com/information-technology/2020/04/understanding-raid-how-performance-scales-from-one-disk-to-eight/)

When using RAID on disks over 1TB in side, there's only 2 RAID types to consider. RAID1 or RAID10.  Avoid all others, especially RAID0+1.  RAID5/6 will have terrible performance.  ZFS allows RAIDz or RAIDz2, but with those we really want an SSD assigned as a cache device to prevent terrible performance.

Whenever setting up systems, it is important to be consistent.  [https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)  Lots of tools listed for alarming, monitoring, watching lots, IDS (very light), stuff like that.

Networking with Intel GigE adapters is easy. Some of the other, cheaper, options, can cause hassles you don't want and use more CPU.

Don't use NTFS. Use xfs, ext4, or zfs.  If you don't use ZFS, strongly, consider using LVM2 to gain easier management of storage. Libvirt will use lvm for allocating storage to a VM as a block device which is crazy-handy for all sorts of reasons, including performance, but also for backups.  

If you are really new to Linux, perhaps deploying something like Proxmox would be faster. It uses LVM, supports KVM and Docker and makes the storage stuff not-so-much manual.

If you might want to use LXD (ubuntu's container solution that's halfway between Docker and KVM), then you'll want to use ZFS on some of the storage but the pool needs to be dedicated to LXD, if seems.  lxd is a snap package (only). v4 was just release this month. LXD doesn't have the same limitations that Docker does, while having some of the limitations that Linux Containers do but keeps the docker-like performance and relatively tiny file system requirements.

I'm certain I've forgotten something, perhaps important. Ask if I did.

---

### Post by oldfred on 2020-04-19
This user with a newer MSI card had to turn off external SATA setting.
Not sure if newer MSI UEFI or Ubuntu resolves those issues.

MSI Z97 turn off external SATA
[https://ubuntuforums.org/showthread.php?t=2411446](https://ubuntuforums.org/showthread.php?t=2411446)

---

### Post by mclaughlin-peter on 2020-04-19
> **grahammechanical said:**
> Decision time. Ubuntu Desktop Edition or Server Edition? Or both? At the end of April the latest version of Ubuntu will be released. It is called 20.04. The latest is the greatest. It will have the best hardware support as part of the Linux kernel. The latest hardware needs the latest Linux/Ubuntu OS.

And Ubuntu 20.04 is a Long Term Support (LTS) version.

[https://ubuntu.com/blog/what-is-an-ubuntu-lts-release](https://ubuntu.com/blog/what-is-an-ubuntu-lts-release)

I am not sure if the server version comes with video card drivers. Not supposed to be needed? But the desktop version does. Anyway we can add and remove programs as we like to get the system that we prefer.

Regards.

Definitely will consider the LTS variant, always was a fan. First picked up ubuntu because of a maximum pc magazine article maybe 15+ years back, especially the drawing fire on my screen feature.. >_> (eh, it was epic before you could do smartphone stuff).

Definitely will consider the desktop edition more, so I can test it further, maybe off and on use it to process a bit more, but definitely to tinker with.

Thanks! (Seriously was looking for the +rep icons if that was a thing here)


> **TheFu said:**
> Don't use HW-RAID or Fake-RAID.  Use SW-RAID, but only if you must and only AFTER you have backups 100% sorted first.  If the VMs aren't Windows, you'll probably only need 4-8G of storage for each VM.  Just depends on the data.  If you deploy using LXD, move the zero left - 10x less storage needed for the OS.  If you need a JBOD storage card, get one from LSI and make certain the drivers are included in the Linux kernel first.  Claims of RAID drivers for Linux are usually for any other kernel than you have and bring all sorts of issues.  The only time anyone should use a HW-RAID card is if there is a battery included in the RAID controller to ensure writes complete after a power hit.  Any others just aren't worth it and aren't as fast as Linux SW-RAID.  
Read this: [https://arstechnica.com/information-technology/2020/04/understanding-raid-how-performance-scales-from-one-disk-to-eight/](https://arstechnica.com/information-technology/2020/04/understanding-raid-how-performance-scales-from-one-disk-to-eight/)

When using RAID on disks over 1TB in side, there's only 2 RAID types to consider. RAID1 or RAID10.  Avoid all others, especially RAID0+1.  RAID5/6 will have terrible performance.  ZFS allows RAIDz or RAIDz2, but with those we really want an SSD assigned as a cache device to prevent terrible performance.

Whenever setting up systems, it is important to be consistent.  [https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)  Lots of tools listed for alarming, monitoring, watching lots, IDS (very light), stuff like that.

Networking with Intel GigE adapters is easy. Some of the other, cheaper, options, can cause hassles you don't want and use more CPU.

Don't use NTFS. Use xfs, ext4, or zfs.  If you don't use ZFS, strongly, consider using LVM2 to gain easier management of storage. Libvirt will use lvm for allocating storage to a VM as a block device which is crazy-handy for all sorts of reasons, including performance, but also for backups.  

If you are really new to Linux, perhaps deploying something like Proxmox would be faster. It uses LVM, supports KVM and Docker and makes the storage stuff not-so-much manual.

If you might want to use LXD (ubuntu's container solution that's halfway between Docker and KVM), then you'll want to use ZFS on some of the storage but the pool needs to be dedicated to LXD, if seems.  lxd is a snap package (only). v4 was just release this month. LXD doesn't have the same limitations that Docker does, while having some of the limitations that Linux Containers do but keeps the docker-like performance and relatively tiny file system requirements.

I'm certain I've forgotten something, perhaps important. Ask if I did.

/bowsBeforeGreatness

Drives are temp formatted in NTFS just so they're easily accessible, can see their current partition existence, and understand drive 0,1,2,3,4 etc. I've used repeatedly Raid 10, huge fan for platter systems for storage efficiency and redudancy. Definitely can do at minimum 1x raid 10 (4x1tb probably).

I've debated 5/6 but probably won't. The google photo link has reference to the actual cards i'm intentioning.

The GigE adapter I have is specific to a Intel card separate from mobo onboard. Figured try to spread some of the processing onto actual parts, etc.

I'll be rereading your reference notes here thoroughly, Whole heartedly in agreement.

> **oldfred said:**
> This user with a newer MSI card had to turn off external SATA setting.
Not sure if newer MSI UEFI or Ubuntu resolves those issues.

MSI Z97 turn off external SATA
[https://ubuntuforums.org/showthread.php?t=2411446](https://ubuntuforums.org/showthread.php?t=2411446)

I'll definitely check this in the off chance it does interfere. (e-sata). I haven't re looked if I have one, but i'll double check to be safe. Thanks!

---

