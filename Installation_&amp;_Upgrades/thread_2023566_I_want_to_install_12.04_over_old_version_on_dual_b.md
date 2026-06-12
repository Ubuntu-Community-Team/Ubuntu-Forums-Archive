---
title: "I want to install 12.04 over old version on dual boot system"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by lindsay7 on 2012-07-12
Here is what my drive looks like,

[ATTACH]221151[/ATTACH]

When I use the live DVD to install I get mixed up on what to do to the partitions. I know that I want to format and install the new Ubuntu version on Sda6 and set it as / or the root. And I think that want to mount Sda3 as /home. Do I need to do anything else with the other partions. When I click on them to see what to do there are options like "do not use", and ext3 or ext 4. Do I need to mount any of these?

I have look all over for the directions to clear this up for me but I have not found them yet.

All help on this would be greatly appreciated.

---

### Post by zwygart on 2012-07-12
Yes this should be all, just also add the swap as swap.

---

### Post by oldfred on 2012-07-13
Just be sure not to reformat your existing /home but do reformat /.

Just a couple of comments. 

Boot flag only needs to be on the primary partition with Windows. Grub does not use the boot flag, but Windows does. It does not matter when booting Windows from grub, but if directly booting Windows it is vital. Also Windows only repairs the partition with the boot flag.

Also your NTFS partition looks very full. Windows typically wants 30% free space, slows with 20% and just about stops at 10% free. You may be to the point you cannot defrag except over several days as there is not enough room to move things around.

---

### Post by lindsay7 on 2012-07-13
Thanks for the the tips Old Fred.  How do I set the boot flag from the Ubuntu live cd, or should I do this later from Gparted,

Also, just to make sure I understand this correctly,when I use the manual install option with the live cd, I do not need to do any thing with the other partition except the / root and the /home and I do not need to make any other settings. Also I should install Grub on Sda?

---

### Post by darkod on 2012-07-13
> **lindsay7 said:**
> Thanks for the the tips Old Fred.  How do I set the boot flag from the Ubuntu live cd, or should I do this later from Gparted,

Also, just to make sure I understand this correctly,when I use the manual install option with the live cd, I do not need to do any thing with the other partition except the / root and the /home and I do not need to make any other settings. Also I should install Grub on Sda?

Yes, grub2 goes to /dev/sda (without any number in it).

Also yes, during the install you click the Change button to set and use sda6 as /, sda3 as /home and the swap as swap area.
Also, for /home make sure you select the exact same filesystem in the Use As field. Otherwise it will try to format it because it can't change the filesystem without that.

No need to touch other partitions during the install, although later you might wanna mount sda5 as some storage because you seem to be using it from ubuntu. But that can be done easily in /etc/fstab once you have the new system running.

---

