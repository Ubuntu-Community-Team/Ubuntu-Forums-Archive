---
title: "Will Ubuntu/Lubuntu install on an NVMe Raid 0 array (multiple m.2 drives)?"
date: 2016-04-05
forum: Installation &amp; Upgrades
---

### Post by josiah14 on 2016-04-05
I wanted to ask here before buying anything to see if anyone has had success installing an Ubuntu distribution (preferrably 15.10) on an NVMe Raid 0 array.

I'm particularly eyeing the AORUS X5S V5-SL1 with 3 256GB Samsung 950 Pro SSDs, and I won't have SLI in case that helps anyone.

(I did Google around, and discovered that since some of the posts in 2015 I encountered, people have been able to boot mainstream OSes like Windows from a Raid 0 NVMe.  I haven't been able to dig up anything conclusive regarding Ubuntu or some other Linux distro, though).

---

### Post by oldfred on 2016-04-05
You do understand bleeding edge hardware often takes a release or two before it works easily with Linux.
If you want you may have to use ppa to get kernels that are just updated, but not yet in a distribution. Same with support software and video drivers.

I have seen users install to RAID, install to NVMe drives, install with dual video, and with new Skylake processors.
But you have all of them. So a bit of effort probably required. And even though not yet released, 16.04 will be better, but is now a kernel version or two behind, it uses 4.4, and 4.6 is being worked on.

Also some vendors UEFI is better than others. So more main stream systems often work better.

RAID 0 is not recommended and with SSD even less so. It was more popular with gamers and the older slower hard drives, SATA2.
Most things run in RAM, so if you have a lot of RAM, the RAID 0 only speeds hard drives which are not used much. Internet is not faster, you cannot type faster, and RAM is not faster, only drive.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by josiah14 on 2016-04-05
Well, I would like to use this laptop for developing software that performs machine learning, linear regression, etc. types of algorithms over fairly large datasets (hence the RAM), but I'll be using both Spark and Hadoop (hence the desire for a fast disk). [I realize Spark and Hadoop are meant for clusters, but during development, I test things out on data in the 100s of GB range against Docker containers running Spark/Hadoop as a sanity check and for convenience so that I don't have to be connected to a cluster to test my development work until it's reasonably complete and ready for performance analysis].

I've installed Ubuntu before to boot from a Raid 0 configuration, but that was through a SATA III setup.  I was also looking at the Clevo P650-RE3 as an alternative.  I'd lose out on the Raid 0 NVMe, but since they are faster than anything I've had before, I think I could live with it.

I'm also not too concerned about disks dying for two reasons: 1. SSDs have a much lower failure rate and 2. All of my important information is stored in GitHub or on Google Drive.  Once the OS is installed, I even have my environment scripted up to automate the installation of all the software I use (programming languages, IDEs and editors, etc.).  Getting my environment back, provided I can install an Ubuntu distro, is easy as pie.

---

### Post by oldfred on 2016-04-06
All I can suggest is try Ubuntu.

But if a developer, I would think a desktop would be more appropriate. And dual monitors.

I am not a fan of laptops where many use them. They may be required if you job moves from on location to another. And ok for short term use.
But laptop is not ergonomic. Screen should be higher and larger, keyboard lower. While every generation of laptop that comes out says it is a desktop replacement, then new generation desktop is always more powerful.
And with desktop you get larger monitor, better keyboard(may cost a bit), and can upgrade individual components.

My wife like her ipad, but if she wants to do anything other than read, watch videos, she use desktop for larger screen and full keyboard. And it is better for travel. But ads saying adding a small keyboard to a tablet replaces a laptop to me is pure marketing hype. For a few it may be just barely adequate.

I just retired my 10 year old laptop for a new SFF desktop. But I was only using laptop as a snowbird, going from Chicago to Florida for Winter. Just built new SFF system I will keep in Fla and larger screen alone is worth it. I can easily move all data back and forth on flash drive.

---

