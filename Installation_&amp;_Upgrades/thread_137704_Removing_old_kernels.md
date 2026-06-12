---
title: "Removing old kernels"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2006-02-28
The install defaults to a i386 kernel and since then I've moved to an i686 kernel and I want to remove the i386 kernel as I don't use it anymore (let alone the "older" versions of the i686).

I can remove it from Grub easy enough but I want to eliminate it from my system and keep only the latest (and one previous version until I have vetted out the new one).

Since I have a dial-up, it takes 1 hour +/- to download a new kernel and this last time I finally got it downloaded when I realized it was for the i386 and I'm using the i686! Had to wait for another night to download it.

I'm sure it's already been posted or written somewhere but I haven't run across it yet so if somebody could point me in the right direction, that would be great!

thanks.

---

### Post by Lux Perpetua on 2006-02-28
You should be able to uninstall them from Synaptic.

---

### Post by aysiu on 2006-02-28
Open up Synaptic Package Manager and do a name search for *386*.

---

### Post by uberlaff on 2006-02-28
You can remove the old ones from Synaptic. (or Adept if your using KDE)  I actually just did this yesterday. As long as your confident that everything is working I don't see it be being a problem.  I would definitely keep at least one previous stable version just in case.

---

### Post by uberlaff on 2006-02-28
wow, a lot of people picked up on that one!   good luck!

---

### Post by Dragonbite on 2006-03-02
It took my like maybe 5 minutes or so to do it.

I looked up 386 like you suggested, (did 686 to make sure they were present too ;) ) and marked to uninstall the kernels and it nicely took out all of the extra pieces and updated Grub to remove them.

Thanks again!

---

### Post by mhenriday on 2007-07-12
I'm running a triple-boot set-up - (**Windows XP Home** and ditto **Vista Business** on one 250 GB harddisk (**sda**), and **Feisty**, which I installed from Canonical's 64-bit live CD on a second harddisk (**sdb**) - all on an **AMD 64 X2 5000+** machine. After installing the recent **Feisty** kernel update from **2.6.20-15** to **2.6.20-16**, my **GRUB** entry for the **Ubuntu** in **gedit** (I'm running the **Grub 2 beta**) read as follows :

title Ubuntu, kernel 2.6.20-16-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=8da527e1-381a-4b9c-979f-65c6379afc8f ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=8da527e1-381a-4b9c-979f-65c6379afc8f ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=8da527e1-381a-4b9c-979f-65c6379afc8f ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=8da527e1-381a-4b9c-979f-65c6379afc8f ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiets :

Given that the **2.6.20-16** kernel seems to be performing perfectly (OK, _nearly_ perfectly), I found it difficult to conceive of a situation in which I should wish to boot to the earlier version, and I therefore decided to uninstall the headers and images related to **2.6.20-15** in **Synaptic**. This I was informed, would free about 189 MB of disk space. After performing the operation, I see that the relevant lines have all been unchecked in **Synaptic**, but when I list my **GRUB** files in **gedit**, I still see those related to the **2.6.20-15** kernel, and they also show up as **GRUB** alternatives when I boot my machine. Have I missed something ?...

Henri

---

### Post by yj09 on 2007-07-12
I also got same grub... i already upgrade 2.6.20.15 to 2.6.20.16-29 kernel... but on grub still 2.6.20.15. When I check kernel using uname-a ...system detect as 2.6.20.15 kernel. I check on adept and 2.6.20.16 was installed and already remove 2.6.20.15 kernel. I don't know and have no idea...

---

### Post by mhenriday on 2007-07-13
**Yj09**, when I type in ```
uname -a
```I get the following result :> Linux mhenriday-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux
i e, no 2.6.20-15 kernel. But it still appears in **GRUB**, both when I boot my machine and when I check with ```
sudo gedit /boot/grub/menu.lst
``` I still get :> title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8da527e1-381a-4b9c-979f-65c6379afc8f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8da527e1-381a-4b9c-979f-65c6379afc8f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8da527e1-381a-4b9c-979f-65c6379afc8f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8da527e1-381a-4b9c-979f-65c6379afc8f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

...Go figure !...

Henri

---

