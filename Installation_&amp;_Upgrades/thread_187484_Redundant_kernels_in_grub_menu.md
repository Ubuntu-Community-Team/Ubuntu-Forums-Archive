---
title: "Redundant kernels in grub menu?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by paul cooke on 2006-06-03
how do I get rid of them?

I successfully upgraded last night on a pretty non-standard breezy box (had a lot of backports and third-party stuff) and on the reboot saw loads of kernel entries left there for previous breezy kernels. I thought the update program was supposed to clean them out? 

One thing I must say is that the final option given by the update program was to remove some redundant programs, but I skipped this step as there was a lot of stuff in the list that I wanted to keep. I can't remember if the old kernels were in the list though.

It isn't exactly a high priority for me as last night was the first reboot in some 90 odd days... but others who boot daily might be confused by all the old kernels

---

### Post by mjziegle on 2006-06-03
/boot/grub/menu.1st

[QUOTE=paul cooke]how do I get rid of them?

I successfully upgraded last night on a pretty non-standard breezy box (had a lot of backports and third-party stuff) and on the reboot saw loads of kernel entries left there for previous breezy kernels. I thought the update program was supposed to clean them out? 

One thing I must say is that the final option given by the update program was to remove some redundant programs, but I skipped this step as there was a lot of stuff in the list that I wanted to keep. I can't remember if the old kernels were in the list though.

It isn't exactly a high priority for me as last night was the first reboot in some 90 odd days... but others who boot daily might be confused by all the old kernels[/QUOTE]

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=mjziegle]/boot/grub/menu.1st[/QUOTE]
In case you find the above a bit cryptic, it means you should edit the /boot/grub/menu.lst file and manually remove the boot entries you don't want showing up in the list.

---

### Post by paul cooke on 2006-06-03
[QUOTE=BaffledMollusc]In case you find the above a bit cryptic, it means you should edit the /boot/grub/menu.lst file and manually remove the boot entries you don't want showing up in the list.[/QUOTE]

I've found there's a better way... 

use synaptic to remove the redundant packages and it edits grub for you... plus the images are actually removed. Your method leaves the images still there and as far as I know, synaptic will find them and add them back to grub the next time the kernel gets updated...

:)

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=paul cooke]I've found there's a better way... 

use synaptic to remove the redundant packages and it edits grub for you... plus the images are actually removed. Your method leaves the images still there and as far as I know, synaptic will find them and add them back to grub the next time the kernel gets updated...

:)[/QUOTE]
Great, good to know. Thanks!

---

### Post by jonrkc on 2006-06-06
[QUOTE=paul cooke]I've found there's a better way... 

use synaptic to remove the redundant packages and it edits grub for you... plus the images are actually removed. Your method leaves the images still there and as far as I know, synaptic will find them and add them back to grub the next time the kernel gets updated...

:)[/QUOTE]I'm glad to know this.  I've manually edited the menu.lst file over a dozen times now to get rid of the redundant entries--and to restore my primary disk to the first position in the list so the system doesn't boot from a secondary hard drive that's also bootable...

My /boot/grub directory is littered with menu.lst files renamed with very impolite wording.

---

