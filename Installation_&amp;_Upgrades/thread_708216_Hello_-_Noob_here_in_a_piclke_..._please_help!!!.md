---
title: "Hello - Noob here: in a piclke ... please help!!!"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Foggy58 on 2008-02-26
Hello,

Well as you can see I am a Noob (yeah I know what your thinking!!) but I am seeriously in a real state!

I STUPIDLY installed Ubuntu on my PC last night over the top of Win XP Pro thinking it would them become a dual boot ... how wrong was I!!
I restarted the PC and it booted straight into Ubuntu!
Where has WXP gone and all my files (that I STUPIDLY didnt back up)!!???..:confused::confused::confused:

Here is some facts:

O/S: Was Windows XP Pro - now appears to just be Linux
RAM: 2GB
HDD 1: 40GB Maxtor
HDD 2: 40GB Toshiba

HDD 2 was formatted thru WXP prior to the install of Ubuntu - now it appears to be partitioned!?...

Please, please please help!!
Many thanks,
Humbly yours

Foggy

---

### Post by mozetti on 2008-02-26
First things first ... when you turn on your computer, after the BIOS POSTs you can hit the "ESC" key to get to the GRUB menu. There, if you installed correctly, you should see an entry for WinXP -- select that and XP should boot.

If that doesn't work, then read on ...

Did you use a tutorial on how to set up a dual-boot system? If so, which one?

When you said you > installed Ubuntu on my PC last night over the top of Win XP Pro 

Do you mean that you installed Ubuntu to the same hard drive partition that WinXP was installed on? Or did you install Ubuntu to the 2nd hard drive that you had formatted?

I always partition my disks manually, so I'm not sure how Ubuntu automatically does it -- it's possible the automatic setup creates /boot, / (aka root), and /home partitions for you. That would explain why it's partitioned now.

When you log into Ubuntu, using Nautilus (the file manager) you should be able to see both hard drives and any partitions on them. Therefore, as long as the XP partition is still there and untouched by Ubuntu you should be able to get the data from it.

---

### Post by Foggy58 on 2008-02-26
Hi Mozetti,

Many thanks for your reply :) 

I have hit the Esc key on startup and I was taken to a 'boot options' type screen and the following are available to me:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+

There is no mention of Win XP :(  and I didn't use any tutorials on dual booting.
With regard to where I installed it I havn't the foggiest!! I started my PC And ran Ubuntu thought I liked the look of it so restarted the PC with the disk in and chose all the standard options.
I feel like such a numpty! I should have known better!!! Any further suggestions would be greatly appreciated :o)

---

### Post by mozetti on 2008-02-26
Well, log into Ubuntu and under the places menu, select computer. Tell us what partitions you see on the left-side pane in Nautilus.

Also, in the terminal type ```
sudo fdisk -l /dev/hda
```

This will show the partitons on your first hard drive (hd**a**). You may need to use _s_da instead of _h_da. Paste those results here.

Then in the terminal type ```
sudo fdisk -l /dev/hdb
```

This will show the partitions on your second hard drive (hd**b**). Again, you may need to use sdb instead of hdb. Paste those results here also.

You could also use a GUI partition editor to get a visual representation of your disks. In terminal, type ```
sudo aptitude install gparted
```

That will install a Partition Editor (similar to the 'Disk Management' tool in WinXP or Partition Magic).

---

### Post by Partyboi2 on 2008-02-26
you can check by booting into ubuntu and when you get to the desktop open a terminal (Applications>Accessories>Terminal) and type
```
fdisk -l
``` with a small L

---

### Post by Pumalite on 2008-02-26
You can also use Super Grub and if there is still XP, you can boot it:[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by emshains on 2008-02-26
I know im not the biggest computer spec, but is there a possible way that your not booting through the right disk? Well if its like that, you could just fix it through your BIOS, or just  disconnect the drive you have ubuntu installed.

Im sorry if your first try of linux was disapointing, but dont let this first prob get to you!:)

---

### Post by Foggy58 on 2008-02-26
WOW!! Thank you all so much for your helpful advice & comments! I have decided to format my HDD and start again so this morning (and afternoon) I have reinstalled WXP Pro and now I am looking for advice (or better still a tutorial!!) on how to partition my HDD and install Ubuntu so I can have a Dual Boot system.

Is there any tutorial guides etc. that show this! I am not going to let it beat me!!

Many thanks once again guys!

Foggy

---

### Post by Pumalite on 2008-02-26
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

