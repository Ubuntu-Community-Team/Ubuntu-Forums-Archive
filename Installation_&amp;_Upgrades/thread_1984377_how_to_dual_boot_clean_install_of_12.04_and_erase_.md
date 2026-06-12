---
title: "how to dual boot clean install of 12.04 and erase bad 'upgrade from 11.10"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by jesse c on 2012-05-21
I have unuseable update of 12.04 from 11.10 on a dual boot Vista desktop. I bought a CD to do a clean install but dont know how to deal with the partition during install.I followed install without changing anything in partition figureing it would do a 'triple boot' on its own and at the end it told me the install was complete and to restart.After restart the new install is not there just my bad upgrade version,Any tutorials out there?

---

### Post by oldfred on 2012-05-21
Run this and from this run the BootInfo report and post link it makes for the report. Then we can see your entire configuration and make suggestions.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

---

### Post by darkod on 2012-05-21
Boot with the cd first in live mode. Open Gparted. Delete all ubuntu partitions (note, if swap has a keys symbol you need to do right-click Swapoff until the symbol is gone, then you can delete it).

Then start the install and it will install into the unallocated space left.

Or, without deleting the partitions, use the manual partitioning in the installer and tell it to use the root partition with mount point /, the swap as swap area, etc.

---

### Post by jesse c on 2012-05-21
darkod,i did it your way and all seems fine.My only drawback is that now my grub menue has about 20 items now for some reason but since this last install is at top i guess it doesnt matter since it goes right into the working boot,it just looks strange for the couple seconds its on-screen

---

### Post by darkod on 2012-05-21
If it has more entries, sounds like it's finding the old 11.10 kernels. Something is still there.

At this point it might be better to follow oldfred's instructions and run the boot info script and post the link with the results. We can see the details and figure out what's going on exactly.

If you did delete all ubuntu partitions, in the grub2 boot menu you should have only the new 12.04 and vista.

---

### Post by jesse c on 2012-05-22
darkod/oldfred:FYI i did the boot repair thing and it did not fix anything but it did kill my 'software center' availability
I decided to try the GParted route again with success this time.First try i only deleted the swap partitions and not the ext partitions.The only hang up was that the install produced a desktop that was larger than my monitor so all the icons were off-screen and all i had was a blank purple page ,so i had to move my mouse "off page" in the dark ,so to speak and blindly click on where i remembered the icons to be so that i could change the display size. If i had not seen the real screen before ,this would have been another disaster.Why would the default not be a small screen for the viewer to enlarge to fit screen size.All is well now,but it was about a full 10hr 'upgrade'.That would not fly for the general public

---

### Post by AndyOpie150 on 2012-08-28
Fixing to give this a try: New to Ubuntu and made a lot of mistakes in the learning process (trying to get the wireless adapter to functon) so I will do a wipe and install of the same 12.04 version.
Will post how everything goes.
The info about changing the screen size will come in real handy.
 
EDIT: Wipe and re-install went flawlessly. This is actually an option in the install guide (Duh!). This time I checked the box that asked if I wanted it to install third party software. When I booted into Ubuntu and signed in everything looked way better than the first time. I don't know why I left it unchecked the first time (that was a mistake).
 
It it hadn't been for darkod's posting I might not have attempted so soon. Piece of cake.
 
The fun parts when I get everything figured out and decide to go full disk, instead of dual boot (only 117GB of space on hard drive). 
Then I'll use this as my linux machine, and find another for my XP machine or vice a versa (figuring on learning how to develop ROM's for Android Phones).

---

