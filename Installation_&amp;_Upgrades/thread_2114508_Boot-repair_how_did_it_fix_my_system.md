---
title: "Boot-repair: how did it fix my system?"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by siepo on 2013-02-10
I had an uefi boot problem which has been mysteriously been solved by boot-repair, but I would love to understand what was the problem and what particular action solved it.

I did not make detailed notes, and am as a consequence a bit fuzzy about the details. So, since the problem is solved, I am merely asking whether any of the following rings a bell and whether anyone has any illuminating guesses without spending a lot of time on it.

Was it the addition of EFI/Microsoft? Was it nvram/efivars settings? Did a newer BIOS have anything to do with it? How come both pastebin pages mention a grub legacy?

Now about the problem.

I have a Zotac Zbox ID81. I had originally trouble installing Ubuntu 12.10 in uefi mode, i.e. I had trouble creating a live stick which would boot in uefi mode and offer the option of creating an EFI partition. In the end I succeeded, although I only got a grub prompt rather than a grub menu from the live stick.

This was three months ago. But recently I had to RMA the zbox. Since it was a barebone without an hd, I kept the hd and inserted it in the replacement machine when it arrived. I had expected that would be the end of it.

However, the zbox did not recognize the hd as an uefi boot device in the boot menu of the bios, and I could not boot my live ubuntu stick either. I might get a screen with just the word 'GRUB' and next time the hd would not be present in the bios boot menu at all. However, I could boot a FreeDOS boot stick.

It seems like bios setup, instead of just having a fresh look at the hardware, also remembers previous experiences and draws the wrong conclusions.

Somehow, after running boot repair with recommended repairs twice I finally got a grub prompt (not quite sure about the presence of a grub menu) and could get back into my system. I reinstalled grub-efi-amd64 and ran update-grub and now everything is fine.

The pastebin pages are [paste.ubuntu.com/1625025/]("http://paste.ubuntu.com/1625025/") and [paste.ubuntu.com/1625689/]("http://paste.ubuntu.com/1625689/") There are some spurious differences because the first one was done with a regular ubuntu live stick, with boot-repair installed on the fly, and the second with a ubuntu secure remix live stick with built-in boot-repair.

Also, sda3 is the ubuntu installation I actually use, sda2 is for backup/experimenting purposes and is not regularly updated. I deactivated os-prober because it does not seem to understand this setup and would add nonsense entries.

---

### Post by oldfred on 2013-02-10
Boot-Repair uses magic pixie dust to fix computers, so when you sent computer to be repaired it lost the magic. :)

Both BIOS & UEFI do write hardware info into the hard drive for operating system to use. But UEFI also has some of the boot info in the efi partition and uses that. It seems to read efi partition and then store that back into UEFI memory. So it does not update automatically? So new system need to run the updates to recongize the installed version.

Not sure how you got grub legacy into MBR. With UEFI MBR only exists to have a partition table with one gpt entry so legacy apps know the drive is really partitioned. If in BIOS mode MBR can have the MBR boot loader, but Windows will not boot from gpt drives with BIOS from MBR. And grub legacy does not have support for gpt drives. Boot-Repair will not install grub legacy but will update it to grub2.

Some explanation of what Boot-Repair does, but what you check off on advanced options will make a difference.
       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

    
Boot-repair also saves the info on what changes it made.

---

### Post by siepo on 2013-02-11
Thanks for the links. So pixie dust is not the only possible explanation.

Meanwhile, I have an explanation for the legacy grub: in a previous life, the hd had been in a 2006 macbook which had legacy grub and a hybrid partition table. Somehow, this legacy grub must have survived the repartitioning.

---

