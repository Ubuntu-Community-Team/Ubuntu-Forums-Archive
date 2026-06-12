---
title: "[SOLVED] Installation on two HD's"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Mariachi on 2007-07-19
Hi,

I tried to install Ubuntu on my other hard drive but it didn't work.  My main hard drive has XP installed on it, I have a second one where I use to store all my data and I got a third one where I want to install Ubuntu.

It installed, apparently normal but when booting it showed a message saying Grub Error 17...  So I, just disconnected the HD with ubuntu on it but still with the same message.  What I had to do is to repair Windows using the repair command that comes with the windows CD.

I still want to install Ubuntu on my other HD, please help, I'm newbie with Linux.



Thank you guys in advance!!!!

---

### Post by Pumalite on 2007-07-19
You can install Grub in the hard drive where you installed and then edit windblows bootloader to boot Ubuntu. Step 7 of installer>Advanced Tab allows you to choose where to install Grub.

---

### Post by Mariachi on 2007-07-19
Thank you Pumalite, but how do I edit windblows bootloader?  Is it on step 7 of Ubuntu installer?

I apologize for re-questing but I'm a total newbie when it comes to linux.

Thanks!

---

### Post by confused57 on 2007-07-19
> **Mariachi said:**
> Thank you Pumalite, but how do I edit windblows bootloader?  Is it on step 7 of Ubuntu installer?

I apologize for re-questing but I'm a total newbie when it comes to linux.

Thanks!
If your bios is capable of booting first to the drive with Ubuntu...boot up the live cd and install grub to the mbr of this drive:
```
sudo grub
find /boot/grub/stage1
```
this should something like "root (hd2,0)", you would then enter:
```
root (hd2,0)
setup (hd2)
quit
```

Then go into bios & set this drive as the first boot device, you should get a grub boot menu...if you do, highlight your Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd2,0), to (hd0,0)...you'll need to adjust this to what your root partition actually is, e.g. (hdx,y) to (hd0,y)...press "enter, then "b" to boot.  If this works, it's temporary, but you can make it permanent in your /boot/grub/menu.lst.

---

