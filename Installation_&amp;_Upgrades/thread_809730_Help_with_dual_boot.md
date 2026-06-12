---
title: "Help with dual boot"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by jojuman on 2008-05-27
Ok, I'm a total newbie so please bear with me. 

On my pc I had dual boot for XP and Vista and everything worked ok. I guess Vista installed some kind of OS selector. When I installed Ubuntu, I used the partition where I had Vista since I didn't like it anyway. Ubuntu installed without a glitch and worked perfectly. 
Now, when I boot up my machine, I can select Ubuntu from GRUB (I think that's what it's called) or "another OS" BUT when I select Windows XP, the system crashes and I'm never able to boot back into XP.

Sorry for the long explanation but any help or pointers would be greatly appreciated.

Thanks in advance.

---

### Post by Pumalite on 2008-05-27
Post:
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by Rallg on 2008-05-27
In Ubuntu, launch GParted. Find the partition that contains XP. It probably won't be called "XP" but can be identified by NTFS structure, or by partition size.

What is its device number? For example, let's say that XP is on /dev/sda3. That corresponds to Grub device (hd0,2) where the second  hd number is one less than the sda number. Remember this.

Now, go to Terminal:

ls -l /dev/disks/by-uuid

and note the UUID for your XP partition.

Now, have a look at the Grub menu. It's /boot/grub/menu.lst. Does it choose the correct device number and UUID for your XP partition? If not, you can edit the menu:

gksudo gedit /boot/grub/menu.lst

If none of that works, then perhaps there is something peculiar about the XP bootloader in your original Vista/XP system. (If it is as simple as missing an XP file, maybe it can be placed into the XP partition via Ubuntu.)

UPDATE: I see that Pumalite, who knows more than I do, found your post. Listen to him.

---

### Post by jojuman on 2008-05-27
Thanks, I'll try it and will post results.

---

