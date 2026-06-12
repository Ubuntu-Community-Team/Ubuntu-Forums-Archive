---
title: "no wubildr"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by emongev on 2011-05-28
Ive been having this problem when i wubi installed ubuntu 11.04 64bit from windows 7.

Apparently after a while of showing the

Try (hd0, 0) NTFS5: No wubildr

error, ubuntu ends up booting eventually, but i don't like things having errors coming up on boot, especially on my OS.

I tried following the Wubi Megathread Problem #2 Solution #1, but had no luck with it, any ideas? =(

Thanks in advance =)

---

### Post by bcbc on 2011-05-28
It's not an error, it's verbose output from grub4dos - the bootloader Wubi uses to transfer control to Grub2 (Ubuntu's bootloader). If the delay bothers you, just copy wubildr to the root of your first partition /dev/sda1

---

### Post by emongev on 2011-05-28
Just to be clear, what specifically does setting "wubildr" to the root entail? 

i have a "ubuntu" folder on my windows D drive, should i make a "ubuntu" folder on C drive (sda1) and copy the winboot folder?

or should i take the no extension "wubildr" and set it directly on C:/?

---

### Post by bcbc on 2011-05-29
It should be on C:\ already. Your first partition might be a boot/recovery partition. You probably would have to mount it from Ubuntu and copy "wubildr" to the root.

How long does it take between displaying the "Try (hd0,0): NTFS5: No wubildr" and booting?

---

### Post by emongev on 2011-05-29
Ohh i see it now, youre totally right, im gonna tryout this method and see, theres no issue with me writing on the boot/recovery partition is there?

---

### Post by bcbc on 2011-05-29
> **emongev said:**
> Ohh i see it now, youre totally right, im gonna tryout this method and see, theres no issue with me writing on the boot/recovery partition is there?

There shouldn't be any problem with adding wubildr:
```
sudo mount /dev/sda1 /mnt
cp /host/ubuntu/winboot/wubildr /mnt/wubildr
sudo umount /mnt
```

Sometimes Ubuntu will update the wubildr (when package grub-pc is updated). I believe that - since Natty - it will search and update all the wubildr files that exist (in the root of all partitions), so should be good. 

If the delay is not so long I wouldn't bother. Maybe you just need to defrag C:\ to get a quicker response.
Or partition and install direct - eventually you'll be doing this if you like Ubuntu anyway.

---

### Post by emongev on 2011-05-29
i did just that (except the location of the mount xD) but i havent restarted yet since im battling a c program that truncates a number when dividing, but as soon as i solve this ill restart, and the delay is quite noticeable actually, not due to it being fragmented (i have a defragmentation OCD), but im guessing due to the fact that the wubildr was on sda5 (had to check 4 to get there)

---

### Post by emongev on 2011-05-29
ok, the problem was solved :D thanks bcbc, if i lived near you id invite you to a drink of your preference :D

---

### Post by mojo706 on 2012-05-06
hello is it unmount /mnt or umount /mnt?

---

