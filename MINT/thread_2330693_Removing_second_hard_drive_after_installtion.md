---
title: "Removing second hard drive after installtion"
date: 2016-07-13
forum: MINT
---

### Post by mahela007 on 2016-07-13
Hello. 
First off, this post is about an linux mint installation. 

I have two hard drives on my computer, sda and sdb. sda is old and has windows XP and linux mint 17. sdb is brand new and I installed linux mint 18 on it. GRUB is installed on sdb. 
I wanted to remove the old hard drive after installing LM 18 on the new HD. However, once I remove the old hard drive, there is a significant increase in boot time... it takes about 3 - 4 minutes. While the old drive is plugged in, boot takes less than a minute. 
Why is unplugging the old hard drive producing longer boot times? there is nothing else wrong with the boot procedure.. no errors are shown. 

(at one point, in order to fix this issue, I unplugged the old hard drive and then ran update-grub.. the update was successful but it didn't solve this issue. It also reduced the resolution of the virtual TTYs but i fixed that by editing /etc/default/grub)

---

### Post by grahammechanical on 2016-07-13
Did you transfer the remaining hard drive from the sata2 position on the motherboard to the sata1 position? Grub should not be affected as it uses a drive's Universally Unique Identifier (UUID), a long string of alpa-numeric characters to identify drives.

Regards.

---

### Post by oldfred on 2016-07-13
Moved to Mint sub-forum.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Do not know if Mint uses upstart or systemD. 

 Older systems with Upstart
gksudo gedit /var/log/dmesg
sudo grep -E -i "error|warning" /var/log/dmesg  
   Newer systems with systemd:
systemd-analyze blame

---

