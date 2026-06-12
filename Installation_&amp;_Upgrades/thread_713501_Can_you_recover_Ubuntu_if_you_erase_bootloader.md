---
title: "Can you recover Ubuntu if you erase bootloader?"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Marfish on 2008-03-02
Heya, I have installed ubuntu onto a seperate hdd and still have my windows on my internal hdd. Since my windows is malfunctioning pretty bad, I was wondering if I would be able to completely reinstall my windows, erasing the bootloader, and still recover the ubuntu system on the other hard drive. I was thinking that, when I installled ubuntu a while back, I saw that it asked you if you wanted bring a prexisting account from the hard drive (of course I had none then). Would it be possible to either bring back my ubuntu acoount by reinstalling ubuntu on the hard drive, or by some other means?

---

### Post by Rocket2DMn on 2008-03-02
Yes, just make sure you don't overwrite linux when reinstalling windows.  When you do the reinstall, windows will automatically take over the MBR so you won't be able to boot into Ubuntu until you restore GRUB.  Here is how: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-9f28b5a7f41d3659b2ae759665f8bc89ed5b351d](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-9f28b5a7f41d3659b2ae759665f8bc89ed5b351d)
It's OK to overwrite the windows bootloader, that can also be restored if you ever decided to get rid of linux.

---

### Post by confused57 on 2008-03-02
[deleted]...beaten to the punch by Rocket2DMn

---

### Post by Victormd on 2008-03-03
Almost similar but totally different problem, just don't know where to post :).
I have XP, Ubuntu, and Linux Mint installed on three different partitions of the same HDD.
the systems were installed on that order so right now, my boot menu is set to look for menu.lst off of the partition where Linux Mint is installed. However, I don't want it anymore, I installed it just to see if it would be any faster than my Ubuntu install but found out that after all the tweaking I've done to Ubuntu, it'll be hard to get another OS to run as smooth out of the box so I'm going to stick to it.

Now, I want to remove the partition where Linux Mint is installed (and delete it to "grow" my Ubuntu partition) and redirect GRUB to the partition where Ubuntu is installed. Note that I have access to windows partition and both Linux systems so I can do anything from anywhere. What's the best and safest route to restore GRUB? If there's a way to do that without having to use supergrub or the live CD, please let me know.

Thanks

---

### Post by Rocket2DMn on 2008-03-03
Victormd, you will need to use a CD to modify the partitions on your hard disk and to grow your Ubuntu partition since you can't mess with them when they are mounted, that's where the LiveCD or GParted LiveCD come in.  You should be able to restore it the same way as in the link I posted above.  If you need more help, please start another thread about your problem and somebody will be happy to assist.
Good luck.

---

### Post by Victormd on 2008-03-03
> **Rocket2DMn said:**
> Victormd, you will need to use a CD to modify the partitions on your hard disk and to grow your Ubuntu partition since you can't mess with them when they are mounted, that's where the LiveCD or GParted LiveCD come in.  You should be able to restore it the same way as in the link I posted above.  If you need more help, please start another thread about your problem and somebody will be happy to assist.
Good luck.

I knew that I would need the liveCD or something to repartition but I wanted to know if I could restore the grub without the CD and yes, the link you provided earlier did the trick!

thanks

---

### Post by Rocket2DMn on 2008-03-03
You will need a cd to reinstall GRUB since without a bootloader... you can't actually boot into anything to do a restore from!
:lolflag:

---

### Post by Victormd on 2008-03-03
> **Rocket2DMn said:**
> You will need a cd to reinstall GRUB since without a bootloader... you can't actually boot into anything to do a restore from!
:lolflag:

In my case, I had access to all three OSs installed but I wanted to get rid of Linux Mint and since Mint was the last one installed, I had to redirect GRUB to the partition where Ubuntu was installed using grub setup (hd0,1) and that did the trick!

---

