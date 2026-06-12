---
title: "Duality"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Misbah on 2008-02-21
Ok guys, so I've been running feisty, now gutsy, smoothly for a while. But heres the deal. I moved for a while and left my computer at home. All my sensitive stuff is on my ubuntu drive, and my windows is pretty much used for HALO, because ubuntu wireless drivers still blow. And WINE regression blows. So the way I did my install back then was I installed Ubuntu first on SATA 1, deactivated the channel via bios, activated channel 2 which was a seperate hard drive, and installed windows on that, and i did a hard switch via the bios whenever i needed to switch to windows/ubuntu. Well thats what I do now, I did that so I could keep the ubuntu drive deactivated and pretty much a dead hidden drive in my comp so ppl who used my comp would have no idea it was there. Now I've moved back. And its annoying to not be able to access the other drive from whchever one I'm using. As far as they are concerned, the other does not exist. I want to merge them to a true dual boot, C holding Ubuntu, D holding windows. I'm afraid what will happen if i leave both SATA channels active and boot up, I'm afraid either MBR or GRUB will get corrupted, and I wont have access to either drive. Is my thinking correct? How can I do this? I really don't want to reinstall.

---

### Post by Misbah on 2008-02-21
OK so I bit the bullet, and activated both channels. I set the boot drive as windows and restarted. Nothing really happened. Windows booted up, detected the new drive, installed it, and recognizes it as a local disk volume but cant see it because its ext3. 

Then I restarted and switched the boot drive to ubuntu. It installed the Local Disk to the desktop, and can read all my NTFS windows files fine.

Now there are two problems left.

1) I don't really need any of my windows stuff when I'm ubuntu, more so that I need ubuntu stuff when I'm on windows. How can I get my WinXP NTFS drive to read the EXT3 buntu drive when i boot into windows?

2) Now instead of activating/deactivating SATA channels, i have to order/reorder the boot sequence, which is pretty much the same problem. How can I get a boot menu up so that I can choose which drive I would like to boot without having to go into the BIOS?

---

### Post by Misbah on 2008-02-21
Ok so I solved the first problem by using fs-driver. Worked flawlessly. Can read/write from XP to Ubuntu and vice versa now. Now I just need to deal with the second problem of:

Creating a boot menu by referencing GRUB in MBR or vice versa (although I'm pretty sure MRB is the 'dominant' loader)

And a second problem has arisen. FS Driver automatically mounts/unmounts my buntu drive. However in ubuntu I have to manually mount/unmount my XP drive. Kind of annoying, would like to automate it, maybe by adding to FStab? Don't know what to add. It's late and I've made progress.. will continue tomorrow. If this works, this thread will be a good guide to merge from separate disks to dual boot if you've already installed ubuntu and windows simultaneously and swap/switch drives. Although I think I'm one of the few who does this "hard" type dual boot.

---

