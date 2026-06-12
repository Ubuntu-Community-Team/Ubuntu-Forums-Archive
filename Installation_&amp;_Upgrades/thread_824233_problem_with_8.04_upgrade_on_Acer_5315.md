---
title: "problem with 8.04 upgrade on Acer 5315"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by samtr on 2008-06-09
Hi everyone. I just upgraded my Acer Aspire 5315-2153 from Ubuntu 7.10 to 8.04. The install went well but now it boots part way and I get the following lines:

1202
fsck 1.40.8 (13-Mar-2008 )
/dev/sda1: clean 177499/9404416 files, 2287122/18786001 blocks

*Checking file systems...
1202
fsck 1.40.8 (13-Mar-2008 )

*Mounting local filesystems...
*Activating swapfile swap...

Then it just freezes like that. I have no idea what this means so I hope someone has a solution and can help me out. Thanks in advance for any help.

---

### Post by Pumalite on 2008-06-09
Check the UUID of /swap against /etc/fstab:
blkid (to get UUID's)
cat /etc/fstab
If you need to edit:
sudo nano /etc/fstab

---

### Post by Pumalite on 2008-06-09
If nothing comes off that; burn a new CD at 4x after doing md5sum and reinstall.

---

### Post by samtr on 2008-06-10
Thank you for your responses, but I can't access the computer with Ubuntu on it since it doesn't even finish booting up so I can't get to Terminal to type in those commands and the computer I am typing this out right now has a glitch with the cd burner so I can't burn the iso image. I guess I'll have to keep searching.

---

