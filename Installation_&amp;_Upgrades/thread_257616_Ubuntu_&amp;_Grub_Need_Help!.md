---
title: "Ubuntu &amp; Grub: Need Help!"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by HeLiS on 2006-09-14
Hi Guys,

Well after installing Ubuntu 3 times all to a point failed I have cut away most of the mess and found an issue with GRUB that i just dont know how to fix.

I have 3 IDE drives and 1 SATA drive. My Ubuntu install is installed on the second partition of my third IDE drive so Ubuntu has the root set as (hd2,1) which is correct BUT when the MBR boots it sees (hd2,1) as a fat32 partition which I do have but the fat32 parition is actually at (hd1,1)

So I burned a copy of Super Grub Disk and noticed that hdc2 kept failing with a error 17.

I got bored and tried hd1,1 which actually worked and Ubuntu loaded with out any problems.

Now why does GRUB in Ubuntu see hd1,1 as fat32 and fails to let me set that as root but via the SGD the only way i can boot is by setting the config path to hd1,1 as hd2,1 fails saying its a fat partition.

Ubuntu says
hd1,1 is fat32
hd2,1 is ext3

Super Grub Disk says
hd2,1 is fat32
hd1,1 is ext3

right now i need to use the SGD everytime i want to boot and then remove that disk when i want to just boot my windows os.

thanks in advance for anyone who can lend me some assistance.

Mathew

---

### Post by HeLiS on 2006-09-14
BTW when i try to do this below...


sudo grub
find /boot/grub/stage1
root (hd1,1)
setup (hd0)


At this "root (hd1,1)" it comes back saying partition is fat etc etc.

so if the MBR points to 2,1 it will fail yet Ubuntu/Grub wont let me change it to hd1,1 which does work if done via the SGD

---

### Post by HeLiS on 2006-09-15
I had the idea just before of changing the fat drive into a ext3 partition and then making a copy of my /boot folder and putting it on the new ext3 partition that way no matter where it tries to look it will find the info it needs....

this may work but i'd really like a way to resolve this issue if possible.

I also had the idea of shrinking my main hard drive and installing ubuntu on there so windows and ubuntu are on the same hard drive as the MBR hopefully avoid this problem as well...

---

