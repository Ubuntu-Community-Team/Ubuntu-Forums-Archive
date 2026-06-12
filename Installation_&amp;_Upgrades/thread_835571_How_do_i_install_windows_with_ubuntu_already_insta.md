---
title: "How do i install windows with ubuntu already installed (dual boot)"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by Lukeukwalker on 2008-06-20
Can someone help with my problem. I am a keen user of ubuntu but miss the games on windows. So i want to install windows on a 20 gig separate partition on the same hdd, so i can dual boot ubuntu and windows. My problem is that when i install windows on the separate partition it wont load ubuntu, so i changed the grub settings i found in other forums, then i can then only boot into ubuntu. everything i have tried from other posts hasn't worked and would like to start afresh? does anyone know where i am going wrong.
I am using Ubuntu 8.04 Hardy Heron.

A separate issue is that when i can log into windows im not sure how to reinstall the Ethernet driver so i can update all drivers online?

Thanks all

Luke

---

### Post by logos34 on 2008-06-20
> **Lukeukwalker said:**
> so i changed the grub settings i found in other forums, then i can then only boot into ubuntu. 

There's a sample windows entry on the /boot/grub/menu.lst.  Copy it to the bottom and replace the 'root' line (ex.: if windows is on the 3rd partition, then 'root (hd0,**2**)' -- grub starts counting from 0)
> 
A separate issue is that when i can log into windows im not sure how to reinstall the Ethernet driver so i can update all drivers online?

Unless you have a motherboard driver cd, you'll need to download it in ubuntu, then copy it to the windows partition (Hardy has ntfs-3g/ntfs write support).  

Forgot: Run [ntfs-config]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-f965f47c447499ba84ded6319e13b0486cb3c360") to add windows to fstab

---

### Post by Lukeukwalker on 2008-06-21
Hey thanks, this worked a treat, i now have xp and ubuntu running fine. I also managed to get the internet drivers working in xp. My only problem now is i cant get the audio /multimedia drivers to work. i d/l them, install them, restart and it says they are not compatable even though they are the ones dell says for me to use for my system. Any idea whats wrong? the point of having xp was for games and audio is kind of essential.
Im using a dell dimension 3100c
Thanks all
Luke

---

### Post by logos34 on 2008-06-21
What Dell model is this?  Soundcard make and model?  If you d/l'd them frm Dell, try the ones directly from the vendor.

---

### Post by Lukeukwalker on 2008-06-22
its ok, i installed the audio driver before the chipset by accident so thats why it wouldnt work. all is working great now
thanks
luke

---

