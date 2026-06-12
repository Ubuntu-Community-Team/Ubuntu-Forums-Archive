---
title: "trying to repair boot (restoring efi partition?)"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by Pedro_C. on 2015-02-02
Hello everybody, 

The other day I was doing I don't know what exactly, but  the conclusion was that I accidentally deleted the EFI partition, and when I  tried to boot I obtained the message "Reboot and select proper boot  device". After reading some entries in internet I've tried to repair it  using Boot-Repair utility, but I am not able to understand the problem,  so I've decided to ask for help... (of course, I've read some entries  in the forums like [http://ubuntuforums.org/showthread.php?t=2244208](http://ubuntuforums.org/showthread.php?t=2244208), but  without improving my knowledge of the problem).

Using a live usb with Boot-Repair I've made the following

1.-  I ran 'Recommended repair' and obtained the message "GPT detected.  Please create a BIOS-Boot partition (>1MB, unformatted filesystem,  bios_grub flag). This can be performed via tools such as Gparted. Then  try again." Then I went to GParted, selected partition sda1 (512 MB,  which was the EFI partition) and I formatted it as FAT32 with flag  bios_grub. But, this didn't solve the problem.

2.- Before trying anything else I generated a BootInfo summary ([http://paste.ubuntu.com/10012145/](http://paste.ubuntu.com/10012145/))

3.-  Then, someone here told me that the problem was the lack of GRUB in  sda1, then I used "Boot-Repair-->Advanced Options-->GRUB location"  to install GRUB in sda1. After doing that I've obtained the following  summary ([http://paste.ubuntu.com/10012789/](http://paste.ubuntu.com/10012789/)) 

4.- Now, my computer is unable to boot, and even I don't get the message "Reboot and select proper boot device". As you can see in the summaries I have two other partitions, sda2 with the OS (Kubuntu), and sdb with /home/pedro (i.e. my personal data). So, I didn't lose data, but I would like to not reinstall the all the system, as I need several days to tune it ...

I would appreciate very much any help, thank you in advance for your time,

Pedro.

---

### Post by oldfred on 2015-02-02
If looks like you have a BIOS boot install with gpt partitioning.

But grub is not installing correctly.
It looks like you do have a bios_grub partition as sda1. But it must be unformatted and it looks like it is formatted as ext4. Use gparted and change format to unformatted. I think you have to scroll all the way to the bottom to find no format option as there are many formats available.

Then use Boot-Repair to reinstall grub. Probably best to use the advanced option and full uninstall & reinstall option.

---

### Post by Pedro_C. on 2015-02-02
You were right, I didn't see the option 'unformatted' (or 'cleared' as it appears in GParted), then I selected 'ext4'. Changing this in GParted, and applying "Recommended repair" in "Boot-Repair", solved completely the problem.

Thank very very much *oldfred*.

---

### Post by oldfred on 2015-02-02
Your are welcome. :)

---

