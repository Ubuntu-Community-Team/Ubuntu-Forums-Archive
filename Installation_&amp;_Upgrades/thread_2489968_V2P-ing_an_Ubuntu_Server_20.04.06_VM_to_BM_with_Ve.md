---
title: "V2P-ing an Ubuntu Server 20.04.06 VM to BM with Veeam"
date: 2023-08-16
forum: Installation &amp; Upgrades
---

### Post by sbi-spidler on 2023-08-16
I know, I know... why would I do this? There are good reasons, but that's a long story that also reveals far too much of my infrastructure than I'm willing, so let's move past all of that. ;)

I used Veeam to backup the VM, then did a restore to baremetal. I mapped the partitions properly, but when trying to boot I get "no boot devices available."
Here's the link to the boot-repair [pastebin]("https://paste.ubuntu.com/p/d3Kmrnf4GJ")

Any ideas what I'm missing here?

I should note that I HAVE tried the Recommended Boot Repair fix only to get the "Please enable a repository containing the [grub-efi] packages in the software sources of Ubuntu 20.04.6 LTS (mapper/vgdarktrace-vsensor-root)" error message.

---

### Post by MAFoElffen on 2023-08-16
Do it again, but with /dev/sda (first) partitioned as GPT, then flag /dev/sda1 as ESP, bootable. Is currenlty partitioned as MBR/MSDOS.

I think that is what I see there.

---

### Post by sbi-spidler on 2023-08-16
Hmmm... I'm not sure if I have the ability to do any of that within the Veeam recovery console. Or, would I want to restore and then change that stuff within the Live Ubuntu boot enviro?

---

### Post by MAFoElffen on 2023-08-16
I don't know Veam. I quickly looked over it's docs. It says it can restored whole images or pieces of, down to individual files.

What I was thinking was to partition your target drive manually to replicate what existed on the VM. Then restore what was contained in those partitions to the partitions you created. 

If it does not boot after that, mount the root lv from a LiveUSB and reinstall the Grub2 boot loader.

---

