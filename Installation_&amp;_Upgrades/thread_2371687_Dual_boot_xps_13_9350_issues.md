---
title: "Dual boot xps 13 9350 issues"
date: 2017-09-17
forum: Installation &amp; Upgrades
---

### Post by benikens on 2017-09-17
So I've been trying to get a ubuntu install going alongside windows on my xps. I'll list out what I have done so far then get to current issue.
[LIST]
[*]Disabled secure boot 
[*]Checked ACHI mode not RAID 
[*]Created a ubuntu live HDD 
[*]Boot to ubuntu live with UEFI not bios mode 
[*]Open with 'try ubuntu before installing" 
[*]terminal > sudo umount -l -r -f /cdrom (I was getting an error about it not being able to unmount this was the only way to get the install to work) 
[*]Install Ubuntu, check install alongside Windows 
[*]Install completes asks to reboot system 
[/LIST]

Ok so now if I check the boot sequence in bios I can see that it's added a new record for grub, when I try and boot the computer to this I get a grub screen with the following message:
"minimal bash-like line editing is supported...."

Then it just says "grub>" you can press tab and it gives you a bunch of commands available, for example I can try 'boot' and it tells me there is no kernal.
I used the following guide to run boot repair [https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/) and rebooted, I still have the exact same issue.

Edit: If I boot with the ubuntu live usb drive in place my ubuntu seems to work, does this mean my ubuntu is somehow installed on the wrong drive?

Edit2: Ubuntu was in fact installed on the external drive in it's free space, I guess the install alongside windows option isn't smart enough to choose the internal drive. Am now reinstalling with manually created partitions on the internal drive.

Edit3: Reinstall seems to be working now. I used this guide to make the manual partitions for anyone discovering this post in the future: [https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343370](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343370)

---

