---
title: "Windows Raid 0 and Ubuntu (Non-Raid)"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by arcanum on 2007-11-14
I've searched the forum but I can't find a post that quite describes my situation, which is as follows:

I have 2 160GB sata drives (sda, sdb) setup in raid, which I have Windows Vista installed on. I'm using my [[COLOR="DarkOliveGreen"]mainboard's onboard raid controller[/COLOR]]("http://www.evga.com/products/moreinfo.asp?pn=122-CK-NF68-T1&family=400"). 

I also have a 320GB sata with Ubuntu installed on a 50GB partition (/sdc2).

The problem is that I can't get grub to recognize both (it won't boot either one), I suspect because the primary hard drive is part of a raid partition. It comes up with an error saying it cannot find the partition.
I am new to Ubuntu so I would appreciate any help, especially of the step by step variety.

---

### Post by Kurumi on 2007-11-14
It's a royal PITA to get it to work and I only got the setup you are trying to do buy using openSUSE.  For some reason, Ubuntu doesn't load Grub correctly on the MBR on the RAID 0/1/5/whatever array and you can't boot into *nix.  Even with openSUSE, I had to boot off the CD to get it to boot to *nix and Grub was 1/2 broken (memtest and Vista worked fine).  You might have to install Grub on the single 320GB and have that as the primary HD to boot from and therefore, telling Grub to boot off the RAID array.

---

### Post by arcanum on 2007-11-15
I finally solved it, though what I did is more of a hack than an elegant solution.

1. Unplug my windows raid hard drives

2. Install Ubuntu on my 320GB drive. Shut down computer.

3. Plug in my sata raid drives again

4. Go into bios and set my Ubuntu drive as first boot priority

5. Boot Ubuntu. Go into terminal and type

    sudo gedit /boot/grub/menu.lst

When it asks for the root password just type in whatever you entered for the account you set up.

6. Add the following at the end of the file:
title Windows Vista
root (hd1,0) //ie. 2nd hard drive, 1st partition (numbers start at 0)
chainloader +1

Now save the file, the next time you boot you will have the option of pressing Esc and booting to Vista. You can also make Vista the default boot option if you prefer, but that's covered elsewhere.


Theoretically, when you install Ubuntu you should be able to set grub to install to the Ubuntu hardrive, then change your bios to boot from this drive. Then use the installation CD to make changes to the grub menu file, if required. It didn't seem to work for me though (I probably made a mistake somewhere, I am new to linux) so I resorted to this ugly hack. Well it's all the same in the end.
__________________

---

