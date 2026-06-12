---
title: "grub2 does not find filesystem"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by ak9tyOne on 2010-01-11
Hello, 
Here is my problem. Grub2 outputs error: unknown filesystem. Then when i use "ls" command it outputs this:
(hd0), (hd0,4), (hd0,2), (hd1)
and when i "ls (hd0,4)/ or any of them it says:
error: no such disk

So, heres my story. I dual boot vista and ubuntu from my main 320GB hdd. Today i tried to fresh install 9.10 on a different external hdd. The 500GB hard drive already had two partitions, a 30GB Fat32 and the rest NTFS. both of these partitions had about 17GB used on them. I installed off a cd and i shrunk the NTFS to allow for more partitions. I made a 4gb swap as logical at the end then a primary ext4 / partition in front of it. The drives are Fat32 sdg0, ntfs sdg1, then an sdg3 (which im confused about and says is extension), and sdg4 (with linux) and sdg5 (swap). When finished with the partitions it asked me to select where to mount the ntfs and i said /windows. 
When i tried to boot up it did not recognize my external apparently because it was plugged in via firewire. I switched to usb and it booted but then i got the error message in grub. Also, when i switched from firewire to usb the drive changed from sdb to sdg. 
How do i fix this problem? Will reinstalling ubuntu fix this? Is there an easier way? I tried reinstalling grub but it did not work.

Thanks

---

### Post by ak9tyOne on 2010-01-12
(this is a bump)

---

