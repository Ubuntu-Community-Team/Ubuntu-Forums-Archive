---
title: "Grub rescue from external HDD"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by david178 on 2014-03-31
Hello, i have a problem, big time:
I have no SO on my laptop, but grub rescue pops in, i cant boot from cd's or access to BIOS.
So i thought of installing ubuntu into an external hdd and do the commands on grub rescue I saw on the internet(like ls hd0, set root, set boot, set prefix etc...), unfortunately no success.
In the hdd, I have hd1, hd1,msdos1/5/6 however, when I execute ls, either error bad name, or file not found or something like that.

Options left?

Thanks for your attention.

---

### Post by sudodus on 2014-03-31
Welcome to the Ubuntu Forums :-)

Please explain what you mean by SO, and please describe your computer. The more you tell us, the better we can give tips and advice.

- Computer brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

And please tell us what version of Ubuntu you are trying to run!

Finally, how did you install Ubuntu (or linux, which now makes grub rescue pop in)?

---

### Post by david178 on 2014-03-31
Thanks for replying so soon.
-Samsung NP270E5E-X02PT
-Intel i5 CPU
-RAM: 8Gb
-NVIDIA® Geforce® 710M (Optimus&#8482;) with dedicated 2 GB gDDR3
-802.11b/g/n

I am trying to run ubuntu-13.04-desktop-i386

I installed ubuntu on my external hdd via usb on my desktop computer:
I have 2 pc's, laptop and desktop - I booted my desktop via usb, install on External hdd (I selected the option co-exist with other SO in spite of not having another SO on the HDD)
I connected my HDD to my Laptop USB and started. Grub rescue popped in and i command 'ls'. That is when hd1 and hd1,msdos etc appeared.

---

### Post by sudodus on 2014-03-31
The computer has enough horsepower and RAM.

- What about Windows and BIOS or UEFI? If UEFI, things are more complicated than with old style BIOS.

- Optimus is also making things more difficult. There is Bumblebee ... search the internet for ***linux bumblebee*** and find information about it.

Maybe you installed grub into the wrong place, either to the wrong drive or to a partition instead of the head of the drive.

You have three options:

1. Reinstall and use 'Something else' at the partitioning page. It gives you better control of what is happening.

2. Repair grub according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

```

sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda

```

3. Run Boot-Repair and let it do it's job. In this case I suggest that you disconnect any drives (even internal drives) that you do not want to involve in the repair job.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2014-03-31
You need to install a newer version.
 EOL Notice: Raring (13.04) will be End of Life on January 27, 2014
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

And you need to install a 64 bit verison. If you install a 32 bit version it will not work with UEFI. Do you have Windows in UEFI boot mode?

---

### Post by david178 on 2014-03-31
> **oldfred said:**
> You need to install a newer version.
 EOL Notice: Raring (13.04) will be End of Life on January 27, 2014
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

And you need to install a 64 bit verison. If you install a 32 bit version it will not work with UEFI. Do you have Windows in UEFI boot mode?

No, it is not on UEFI MODE, it is on Legacy mode, i guess that is why i cant access BIOS.
Thanks for answering.

---

### Post by david178 on 2014-03-31
> **sudodus said:**
> The computer has enough horsepower and RAM.

- What about Windows and BIOS or UEFI? If UEFI, things are more complicated than with old style BIOS.

- Optimus is also making things more difficult. There is Bumblebee ... search the internet for ***linux bumblebee*** and find information about it.

Maybe you installed grub into the wrong place, either to the wrong drive or to a partition instead of the head of the drive.

You have three options:

1. Reinstall and use 'Something else' at the partitioning page. It gives you better control of what is happening.

2. Repair grub according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

```

sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda

```

3. Run Boot-Repair and let it do it's job. In this case I suggest that you disconnect any drives (even internal drives) that you do not want to involve in the repair job.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

-Bios on Legacy mode...

In relation to your advices:
1- I will try to reinstall using tha whole Externall HDD

2-Repair Grub? I cant access to anything, how do i do that? In my Desktop computer?

3. Boot-repair where? In my Desktop computer? Disconnect which drives (Laptop/Desktop)

I am sorry i am so Inexperienced, i am just very worrried about my computer, i messed up, i know. Any help is appreciated.
Thanks you once again.

---

### Post by oldfred on 2014-03-31
Some computers have issues if UEFI and you did not turn off fast boot in Windows or some also have settings in UEFI/BIOS.
Often you have to do a full power down. If a laptop remove battery and hold power switch for a few seconds to drain residual power. Then see if you can get into UEFI/BIOS with whatever key is correct for your computer.
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Boot-Repair is a app/tool you install into Ubuntu live installer or can be downloaded as its own liveCD. Will only do minor Windows fixes as you have to have a Windows repair CD or flash drive to fully fix Windows issues. You make that from Windows.
      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by david178 on 2014-03-31
> **oldfred said:**
> Some computers have issues if UEFI and you did not turn off fast boot in Windows or some also have settings in UEFI/BIOS.
Often you have to do a full power down. If a laptop remove battery and hold power switch for a few seconds to drain residual power. Then see if you can get into UEFI/BIOS with whatever key is correct for your computer.
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Boot-Repair is a app/tool you install into Ubuntu live installer or can be downloaded as its own liveCD. Will only do minor Windows fixes as you have to have a Windows repair CD or flash drive to fully fix Windows issues. You make that from Windows.
      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Tried the power off and drain battery, it did not work :(
And since i cant even boot from anywhere else,I guess this is the end of my laptop.

Thank you for your concern.

---

### Post by oldfred on 2014-03-31
There were some older Samsung computers that would be bricked but fixes have been out for over a year.
 If Samsung check model number as some can only be installed in legacy/CSM mode or computer may be bricked.
Kernel updates being released and Samsung needs to update UEFI/BIOS.
      
 UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
[http://mjg59.dreamwidth.org/25091.html](http://mjg59.dreamwidth.org/25091.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.
[http://mjg59.dreamwidth.org/23554.html](http://mjg59.dreamwidth.org/23554.html)

    Other Samsungs
 Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

