---
title: "Grub loading error"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by scottym on 2006-09-02
I have attempted to install ubuntu on my ibm laptop thinkpad using the partition option. On rebooting "Grub loading stage 1.5, error, Grub loading please wait, error 18" appears and the computer locks up. I attempted to boot using windows xp and can't boot in windows either. I can start the computer with the ubuntu disc but that is it. What now. Any help greatly appreciated.
Thanks,
Scotty

---

### Post by whizbaby on 2006-09-02
Can you be a little more verbose about *using the partition option*?
What did you actually do?

---

### Post by scottym on 2006-09-02
The program gave me three choices:
1)Wipe the hard drive
2)Let the program select the appropriate partition
3)Manually partition

I selected option 2.

---

### Post by garenasix on 2006-09-02
[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

6. Grub Error 18

Situation

Code Listing 6.1: Grub Output

kernel (hd1,4)/bzImage root=/dev/hdb7

Error 18: Selected cylinder exceeds max supported by BIOS

Solution

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range).

---

### Post by whizbaby on 2006-09-02
Was your XPensive partition's size equal to the whole drive's ? I experienced  buggy behaviour of the ubuntu installer if it comes to ntfs resize. Can you access the hds from your ubuntu live system ? (I know I'm gonna get roasted in hell for this:twisted: : have you tried the auto-repair-option of MSdoze-install-cd to check if it can recover the partition ? If it can, get partition magic and resize ntfs with that )

What I did:
connect second hard drive, save valuable data, make hd blank and start from there. (If you still need the dozer install it first and check it's not grabbing your whole space again)

---

### Post by scottym on 2006-09-02
Ok, How do I move the boot partition. I assume it must be in the BIOS?

---

### Post by scottym on 2006-09-02
Among other problems when I load ubuntu from the cd it show:"RAID monitoring services failed". What does this mean

Can someone tell me how to get win xp started at this point. When I boot the machine it will not give me any options for selecting winxp. also with ubuntu running i cannot access any of the previous files i have because it will not load drive c.

---

### Post by whizbaby on 2006-09-02
A few thinkings ...
-if the hard drive size isn't supported by the BIOS, why was it before ? (didn'read anything about a new drive plugged in)
-ubuntu can't enable hardware you don't have installed (for example my PCMCIA driver loading at bootup fails because I don't have a PCMCIA device)

A few questions :

(1)Was your XPensive partition's size equal to the whole drive's ?
(2)Have you tried the auto-repair-option of MSdoze-install-cd ?
(3)How did you try to access the drive from linux live system ?

(one could think of just re-installing grub, but isn't it better to get sure not to lose too much data?)

---

### Post by scottym on 2006-09-02
(1)Was your XPensive partition's size equal to the whole drive's ?
(2)Have you tried the auto-repair-option of MSdoze-install-cd ?
(3)How did you try to access the drive from linux live system ?

1)The drive was not partitioned to begin with. 
2)No MSdos install cd. Are you kidding this an IBM!!! It didn't come with any discs.
3)I attempted to access it from explorer type menu which shows the various drives.

---

### Post by scottym on 2006-09-02
Good News!!!I now seem to have both XP and Ubuntu running. I got rid of the partitions Ubuntu created, decreased the size of the xp partition to less than half of the harddrive space and reinstalled Ubuntu.Thanks to all for the responses and help. 
Scottyhttp://ubuntuforums.org/images/smilies/eusa_clap.gif
=D>

---

### Post by whizbaby on 2006-09-02
Self-solving is best!

---

