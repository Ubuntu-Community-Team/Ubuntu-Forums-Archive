---
title: "I'm all confused about partitioning!"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by RedMartin on 2008-10-05
I have 8.04 on a 250gb HDD with no partitions. 

What I'd like to do is add a new partition to the drive and install XP into it.

Is that possible? All I can seem to find is ways to add Ubuntu to XP and stuff that is done during the first Ubuntu install.

I thought that Gparted would do it but I can't modify the drive. It shows an error message if I try to unmount it.

What am I doing wrong?

---

### Post by howefield on 2008-10-05
I think you'll need to use the Live CD to boot up and use gparted from there.

---

### Post by spooky655 on 2008-10-05
By no partitions do you mean ubuntu's the only one? If it is and you have enough free space I'm pretty sure you can resize it. I think you have to use the live cd though to unmount and shrink the partition because I don't think you can unmount the HDD with the system files that you are using.

---

### Post by RedMartin on 2008-10-05
> **spooky655 said:**
> By no partitions do you mean ubuntu's the only one? If it is and you have enough free space I'm pretty sure you can resize it. I think you have to use the live cd though to unmount and shrink the partition because I don't think you can unmount the HDD with the system files that you are using.

That makes sense (as does the poster above you). I will give it a go. I'm assuming it'll need to be NTFS as well?

---

### Post by spooky655 on 2008-10-05
Ya, it'll be NTFS. And if you are going to dual boot xp and ubuntu with ubuntu installed first, you are going to have to reinstall the grub boot loader with the live cd after you install xp. Go here to see how to do it:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

---

### Post by RedMartin on 2008-10-05
Nice one! I'll give it a go when I feel brave. It seems to have the potential to go horribly wrong.

---

### Post by Bucky Ball on 2008-10-05
> **RedMartin said:**
> It seems to have the potential to go horribly wrong.

That is true and the rule of thumb is to install windoze first. Because windoze wants sda1 always. Having said that there are ways around this (fooling windoze into thinking it is on the first partition) so with a bit of research and a grub tweak or two you should be right. :)

---

### Post by RedMartin on 2008-10-05
> **Bucky Ball said:**
> That is true and the rule of thumb is to install windoze first. Because windoze wants sda1 always. Having said that there are ways around this (fooling windoze into thinking it is on the first partition) so with a bit of research and a grub tweak or two you should be right. :)

Oh no! It all looked so simple from the APCmag link above. I'll do some research this week and attempt it next weekend.

---

### Post by Bucky Ball on 2008-10-05
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

That is the page. Linux installed first. The one you posted seems to be Windoze first.

---

### Post by spooky655 on 2008-10-05
> **Bucky Ball said:**
> [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

That is the page. Linux installed first. The one you posted seems to be Windoze first.

I'm pretty sure it's linux installed first :)

---

### Post by Sef on 2008-10-05
> Ya, it'll be NTFS. And if you are going to dual boot xp and ubuntu with ubuntu installed first, you are going to have to reinstall the grub boot loader with the live cd after you install xp. Go here to see how to do it:

[http://apcmag.com/how_to_dual_boot_l...rst.htm?page=5]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5")

I prefer using [super grub disk]("http://supergrubdisk.org").

---

### Post by caljohnsmith on 2008-10-05
> **Bucky Ball said:**
> That is true and the rule of thumb is to install windoze first. [COLOR="Blue"]Because windoze wants sda1 always[/COLOR]. Having said that there are ways around this (fooling windoze into thinking it is on the first partition) so with a bit of research and a grub tweak or two you should be right. :)
Bucky Ball, I don't believe that is true. You can install Windows easily to any primary partition and get it to work, so it doesn't have to be the first partition. :) It is even possible to install Windows to a logical partition, but if you do that, Windows will try to put its boot files in one of your primary partitions. And it is even possible to boot Windows directly from a logical partition, but definitely not worth the trouble unless there are special circumstances that require putting Windows in a logical partition in the first place. So RedMartin, just create a primary partition for Windows, and you should be all set. :)

---

### Post by RedMartin on 2008-10-12
Update:

I got XP installed but it proved to be unable to recognise about half of my hardware. I couldn't get on the net as it refused to acknowledge my network devices so I had no chance of finding the necessary drivers.

I gave up after a few hours and I'm now happily back with Ubuntu.

Thanks to all for the help though.

---

