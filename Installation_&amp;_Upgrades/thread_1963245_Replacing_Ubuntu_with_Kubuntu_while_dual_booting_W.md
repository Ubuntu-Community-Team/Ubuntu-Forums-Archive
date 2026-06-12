---
title: "Replacing Ubuntu with Kubuntu while dual booting Win7"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by George B on 2012-04-22
Hello, this is a preventive sort of thread in that a problem hasn't occurred yet but I've foreseen that it might so I'm sort of asking for help in advance.

On my laptop I dual boot Ubuntu 11.10 and Win 7 and it's been working very well but I would like to move to Kubuntu 11.10 in place of Ubuntu and I've burned a Live CD for that purpose, yes I know I could get the KDE environment from within Ubuntu with the synaptic packet manager but I really want a fresh start for the Linux side of my laptop.

My problem is that I'm bad with navigating the Live Cd install and the grub menu configuration, last year I needed again to wipe my Ubuntu partitions clean and install a newer Ubuntu from alive CD andin the end the best I could do was having both versions of Ubuntu installed and switching most of the space from the old Ubuntu to the newer one, but at least they all still appeared in the grub.

So In short what I want to is:

[LIST=1]
[*]Completely replace my Ubuntu with Kubuntu while having the Linux partitions stay the same, i.e the same size I want the old data to be deleted with Ubuntu
[*]The Kubuntu install to be done from the Kubuntu live CD I burned
[*]The Windows 7 partitions to be unchanged, I need some programs on it.
[*]Kubuntu and Win7 to appear in the grub menu, and at this part please explain in detail because I have no experience what so ever with modifying the grub.
[/LIST]
 So if you could please tell me if it's possible. ie from the Kubuntu Live CD complete replacement of Ubuntu plus if I have to sudo gedit something in the grub etc.

---

### Post by ajgreeny on 2012-04-22
It should be easy to do, but means you MUST choose **"Something Else"** at the disk preparation stage.  Having done that the system will scan all the disks and partitions on your system.  Your windows partitions will be either NTFS or FAT32, and the ubuntu partitions will be ext4 and swap, the latter possibly within an extended partition.

Just choose to replace those ubuntu partitions with the new kubuntu partitions and all should be good.  Come back again if you need to, as I do not have enough time at the moment to explain in more detail, but can do so if needed.

---

### Post by George B on 2012-04-22
> **ajgreeny said:**
> It should be easy to do, but means you MUST choose **"Something Else"** at the disk preparation stage.  Having done that the system will scan all the disks and partitions on your system.  Your windows partitions will be either NTFS or FAT32, and the ubuntu partitions will be ext4 and swap, the latter possibly within an extended partition.

Just choose to replace those ubuntu partitions with the new kubuntu partitions and all should be good.  Come back again if you need to, as I do not have enough time at the moment to explain in more detail, but can do so if needed.

Thank you for the reply, so then I take it the Live CD will know to replace the options in the Grub without any hassle from my part because that's what I'm mainly afraid of not that I have to take a lounger more careful install but that I would be locked out of Win.

---

### Post by ajgreeny on 2012-04-22
> **George B said:**
> Thank you for the reply, so then I take it the Live CD will know to replace the options in the Grub without any hassle from my part because that's what I'm mainly afraid of not that I have to take a lounger more careful install but that I would be locked out of Win.
You are correct; the new install will by default overwrite the old grub (and grub menu) with the new one from Kubuntu, and should pick up the Win7 OS andf add it without a problem.

When you get to the disk preparation stage, as I said above choose Something Else, usually the third option of the three, I think.  The machine's disks will be scanned and a list of partitions will then show.

Win7 will probably have several partitions, and will be the first ones on the disk, I imagine.  Your ubuntu root partition will show as an ext4 partition and depending on how you installed Ubuntu the first time, may be a primary partition, or a logical partition within an extended partition.  Any partition numbered above 4, eg sda5 will be a logical partition which is inside an extended partition, which itself can be numbered anything from sda1 to sda4.

If you are not sure about how to proceed, boot to the live CD/USB and run gparted, then post a screenshot of the gparted window here for more detailed advice.  Not knowing how comfortable you are with partition management makes it difficult to give you more advice at the moment.

---

