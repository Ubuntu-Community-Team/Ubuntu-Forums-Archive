---
title: "Dual boot ubuntu and vista (1 harddrive). General questions, and a procedure to check"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by Eoghanalbar on 2007-06-12
Currently I have only ubuntu, but I'm think I should make a strategic retreat to a dual boot system for a while.

Will I be able to:

A. Read my files whether I'm in ubuntu or vista. To what extent and can I make it work both ways, or, if only one way, which? Are there different ways of doing this? I really don't want to have to switch back and forth to get documents I wrote or music or whatever. 

B. Get rid of vista and take over that space if I want to at some later time. By just taking over the partition it was on, or could I get rid of that partition and extend the one my files are on to fill up that space?

C. Easily fix some problem arising from misallocating space to the partitions when I first install? Do I have to be careful setting it up so that I don't run into trouble installing some big program on either OS?

Any special cautions, or programs, or experiences, or anything?[

I want to install vista without getting rid of ubuntu first. I understand this means I'll have to put GRUB back, yes? But there's no good reason it would be better for me to uninstall ubuntu, install vista, then install ubuntu again, right?

[this is the friendliest looking set of directions I've found yet]("http://apcmag.com/5045/how_to_dual_boot_vista_with_linux"), although I suspect I just feel that way because of the nice big shiny pictures at the top. Using that site and probably some other stuff I can't remember, I made a list of directions for myself (I'll print them out for myself on another computer, since I still can't get my crappy ubuntu unsupporting printer to work :p). I mixed some different sets of directions together to get what I wanted, so do you see any problems? I bolded some questions I had along the way.


Using the ubuntu live CD and the **Toshiba recovery disks, rather than a plain vista disk. Does anyone know if that'll cause problems?**

1. Boot from ubuntu live CD

2. [System > Administration > GNOME Partition Editor]

3. Right click on my main partition (the big one, the ext3, the one with the boot flag, with mountpoint /) and click "resize/move"
[B]
? How much is enough? 10GB? For "Vista Home Premium"?[/B]

5. Apply.

6. Same partition, right click and "manage flags".

7. Remove boot flag. Close. Shutdown.

8. Boot from "Toshiba recovery disk"

9. "Where do you want to install Windows?" screen. Should be a "Disk 0 Unallocated Space" with all free space and no type (primary, logical, etc). Next. Wait for it to finish.


I want to reinstall GRUB and configure it to boot vista rather than... the other way. Using the MBR but putting the GRUB in some other partition or whatever it is.

Soooo...


10. Boot from ubuntu live cd, terminal, type (with enter after each line):

grub

root (hd0,0)

setup (hd0)

quit
[B]
(? hd0,0 is right for me since I've got /dev/sda1 as the current boot partition for this system with only ubuntu? I can find a file named "grub" under /boot in my GUI filesystem)[/B]

11. Reboot. Press Esc during GRUB's window of oppurtunity. Select Vista if I want to load Vista.

12. Boot into ubuntu. Terminal, type:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak

sudo gedit /boot/grub/menu.lst

13. Change default value to a number one below the number of the list item I want to be default. "Other operating systems" counts as a list item.

14. I can up the boot menu "timeout".

---

### Post by kidders on 2007-06-13
Hi there,

> **Eoghanalbar said:**
> A. Read my files whether I'm in ubuntu or vista.No problem. You may however encounter some minor irritations (mostly because Microsoft refuses to support other companies' filesystems, or release good documentation for its own ones). The most significant issue is the lack of support for decent file access controls on FAT & NTFS, but once you sort things like that out, you should be fine.

> **Eoghanalbar said:**
> B. Get rid of vista and take over that space if I want to at some later time.I would strongly recommend against resizing partitions, but there is no reason why you wouldn't be able to find other uses for disk space you no longer require. :-)

> **Eoghanalbar said:**
> C. Easily fix some problem arising from misallocating space to the partitions when I first install?This wouldn't be easy, and would be very error-prone. You should aim to play with your partition tables as little as humanly possible.

> **Eoghanalbar said:**
> I want to install vista without getting rid of ubuntu first. I understand this means I'll have to put GRUB back, yes?I'm not quite sure what you mean by that. If, for instance, you're using a different bootloader (eg lilo), there's no reason you can't keep it ... Unless Vista is somehow different (I wouldn't know, I'm afraid), virtually all bootloaders are happy to boot Windows.

> **Eoghanalbar said:**
> Right click on my main partition (the big one, the ext3, the one with the boot flag, with mountpoint /) and click "resize/move"I wouldn't! But it's your PC. :-) How much space to allocate very much depends on how much you intend to use the OS in question. Don't feel like you have to allocate *all* the space on a disk, right from day 1 ... the hard disk in my machine has over 300GiB of unallocated space on it at the moment, simply because I have no particular use for it.

I hope that's of some help.

---

### Post by kidders on 2007-06-13
Sorry for replying to *myself*, but I just realised there's something you've made no mention of ... personal file storage. If you don't already have a separate /home partition, I would strongly recommend setting one up. Among other things, this will allow you to...

[LIST]
[*]Treat /home without regard for the health of the rest of your system (eg running out of disk space, fragmenting it by performing millions of creations/deletions, and so on).
[*]Switch distro (or drop Linux altogether) in the future, without having to worry about losing personal data (ie the reverse of the above).
[*]Select an appropriate filesystem (eg Ext3) for use with Windows, while giving yourself more freedom with the rest of your Linux system.
[*]Mount only your personal data in Windows (rather than your entire Linux filesystem), to avoid the risk of damage.
[*]Better predict the amount of space an individual OS will need, by allowing you to disregard space consumed by personal data.
[*]Etc...
[/LIST]

---

