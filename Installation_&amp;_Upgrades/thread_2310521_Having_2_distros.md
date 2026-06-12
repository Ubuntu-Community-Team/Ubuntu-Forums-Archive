---
title: "Having 2 distros"
date: 2016-01-20
forum: Installation &amp; Upgrades
---

### Post by kkk5 on 2016-01-20
I'd like to have 2 distros in my system; Ubuntu and Mint. 

I'm already on Kubuntu, and I'd like to be able to switch between them. **How can I do this?**

---

### Post by Dennis N on 2016-01-20
Install and run one in a virtual machine for simultaneous operation.  Otherwise, investigate dual booting.

---

### Post by ajgreeny on 2016-01-20
We need a lot more info before we can give you any details on exactly how to do this.
What hardware do you have?
Is it a UEFI boot system?
Does it have a version of Windows that you want to keep; I assume not from your query?
What is your current partition setup as that will have a great bearing on the detail of what you can do?

In spite of all these uncertainties I can assure you that it is very possible to have several distros on one machine without any conflicts, you just need to be sure of how you set up the OSs.

Until about 2 years ago when I made a decision on what was to be my main OS I had up to six OSs, all Linux, on my single desktop.  I had two hard disks, but that makes no real difference your the ability to do this.

---

### Post by grahammechanical on 2016-01-20
I often have more than one Linux OS on my machine. They are different flavours of Ubuntu. So that I can access my data from any OS I have all my documents in a separate partition.

With Linux we only need one swap partition and that will be used by each Linux distribution. So, it then becomes a matter of using GParted from a live session to create 20GB - 25GB partitions for each Linux OS. And then using the Something Else option.

Things get a bit more complicated if we have MBR partitioning & its 4 primary partition limit. And then things get different again if we have a UEFI boot system. In this case we may have GPT partitioning and there is no limit to the number of primary partitions but we have to give consideration to the fact that all OS need to be installed in the same mode, either EFI mode or BIOS mode.

We also need to give consideration to the fact that to  install an OS on a GPT disk in EFI mode will require a efi boot partition. But installing an OS in BIOS/Legacy mode on a GPT disk will require a bios boot partition. But just one that can be used by all the OS.

It is as clear as mud. So, it is best to know where you are starting from & work out a plan from there.

Regards.

---

### Post by Bucky Ball on 2016-01-20
There's a ton of info online about [dual-booting Ubuntu]("https://duckduckgo.com/?q=Dual+boot+ubuntu+and+mint") and Mint and a ton about virtualisation.

For future reference, please do some research on your question before posting in a support area. Highly encouraged.

---

