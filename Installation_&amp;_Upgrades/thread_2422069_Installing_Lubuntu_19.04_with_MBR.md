---
title: "Installing Lubuntu 19.04 with MBR"
date: 2019-07-01
forum: Installation &amp; Upgrades
---

### Post by thoughtfulmonkey on 2019-07-01
Hi,

Could someone please tell me the correct partition setup to use in order to install Lubuntu 19.04 with MBR?

I'm trying to resurrect a family member's old PC (HP ms22uk) where the hard drive failed. It cannot boot from USB and the DVD drive is faulty. So I mount the new hard drive in an external USB enclosure, attach it to my laptop, and try to install from a Lubuntu live USB.

The default GPT configuration didn't work. MBR with a single partition also didn't work. The PC includes a diagnostic tool, and in both cases it highlighted that no bootable drive was detected.

However, if I install the Lubuntu live image to the hard drive, and then reinsert it in the PC, then that boots successfully. I see that the live install uses MBR, so I'm guessing I just need to setup MBR correctly? 

Thanks,

Matthew

---

### Post by yancek on 2019-07-02
More specifics on your hardware would be help ful as 'old' is a relative term.  If it wont boot from a usb it must be at least 10 years old.
A standard/basic partition setup would be one partition for the '/' root filesystem and sometimes a swap partition.  After that it is  matter of choice.

If I understand, you are attaching a new drive you purchased for this old computer and are using a newer laptop with the new hard drive attached on which to try to install Lubuntu, correct?  If that is the case then you need to create a partition table on the new empty drive.  YOu can use GParted which should be on the Lubuntu install usb to do this, select the msdos option.  Not sure what the 'no bootable drive' questions is about as it seems to be an empty drive so obviously would not be bootable.

[QUOTEHowever, if I install the Lubuntu live image to the hard drive, and then  reinsert it in the PC, then that boots successfully. I see that the  live install uses MBR, so I'm guessing I just need to setup MBR  correctly? 
][/QUOTE]

Is this the new, empty drive and is the PC in question the old PC?  How did you do this?

---

### Post by oldfred on 2019-07-02
I used gpt on my old 2006/2009 system with BIOS only starting in 2010, but always had to have a bios_grub partition on the gpt drive for grub to install correctly to the gpt's protective MBR.
 With MBR partitioning boot starts with MBR, but grub has more boot info in core.img which is in sectors just after MBR. With gpt there are no available sectors after the protective MBR, so bios_grub partition is required.

Not sure if a BIOS can tell the difference between MBR partitioning & gpt as once BIOS is done, all it does is pass boot to MBR. And if MBR.

But if installing to an external drive, you must use Something Else and at bottom of partitioning screen select external drive's MBR (just drive, not a partition), for grub2's boot loader. Then it will be in MBR of external drive. Grub normally default to install to MBR of first drive or sda or hd0 before boot.

Some older BIOS have a limit on where boot files on drive are. The newest limit was 137GB, but really old system had many smaller limits, but those are so old as probably not a usable system now.
If that limit applies, best to use smaller / (root) of 25 to 30GB at beginning of drive and use rest as /home or data. 

Shows older versions but process is the same. Skip Windows dual boot screens.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

