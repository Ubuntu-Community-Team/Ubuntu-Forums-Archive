---
title: "Difference b/w Wubi &amp; regular installation"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by emmagood on 2012-08-26
Hi,

  Can anyone pls. tell me the difference b/w Ubuntu installation with Wubi and regular installation. A friend was telling me that through Wubi installation, one can access the windows drives, viz. C:/, D:/ etc whereas through normal installation, it is not possible. Also, when is Wubi installation done and when is regular installation preferred ?

Thanks,
Emma Good

---

### Post by SLIREAND on 2012-08-26
Wubi  is a Windows installer program and using this you may install Ubuntu within your Windows operating system.

If you wish to use Ubuntu as a separate operating system whilst retaining Windows then consider a dual boot.

Information on this can be found on the Ubuntu Wiki, and these forums.

I hope that this is of help,

Thanks,
Slireand

---

### Post by oldos2er on 2012-08-26
> **emmagood said:**
> Hi,

  Can anyone pls. tell me the difference b/w Ubuntu installation with Wubi and regular installation. A friend was telling me that through Wubi installation, one can access the windows drives, viz. C:/, D:/ etc whereas through normal installation, it is not possible.


That is not true, Windows partitions can be mounted when running Ubuntu from a "normal" (i.e., not Wubi) installation. Wubi installs Ubuntu to a virtual disk within your Windows NTFS partition. It's intended to be a demo, not permanent, so Windows users can try it out without changing their current disk partitions.

[https://wiki.ubuntu.com/WubiGuide/](https://wiki.ubuntu.com/WubiGuide/)

---

### Post by kurt18947 on 2012-08-27
> **emmagood said:**
> Hi,

  Can anyone pls. tell me the difference b/w Ubuntu installation with Wubi and regular installation. A friend was telling me that through Wubi installation, one can access the windows drives, viz. C:/, D:/ etc whereas through normal installation, it is not possible. Also, when is Wubi installation done and when is regular installation preferred ?

Thanks,
Emma Good

As others have said, you can certainly access Windows drives from Linux installations.  It's done all the time to rescue data from Windows installs that won't boot.  In Linux drives are not designated C:\  D:\ what whatever.  They're typically sda, sdb etc.  If you want to 'get your feet wet' with Linux/Ubuntu without messing with your Windows install, I'd recommend a live install.  A live install won't touch your hard drive or windows install.

 I found this totally foreign when first starting .  How can I possibly have a functioning computer without installing to the hard drive?  It turns out that not only can I have a functioning PC, it works quite well:D.  There are a few different options.  I've had the best luck with live CDs/DVDs booting on any machine made in the past 10 years.  A live USB is faster and can have persistence but I have one machine that won't boot certain USB drives as a  live USB unless that USB drive is first formatted on a Windows machine.

Some reading:

[http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html](http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html)

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

If you do choose to try a live CD or USB,  you may have to change your PC's boot order in BIOS or manually select which drive to boot.  How to do this varies between machines.  It usually involves pressing some key immediately after powering up.  I have my machines set to first check for bootable USB HDD, then bootable CD, then hard drive.

---

### Post by emmagood on 2012-08-27
Thanks all for replies.

  Well I am not really new to ubuntu... I had tried it with wubi previously. So I suppose I will go for regular installation. 

 I have 2 HDDs. In the first Windows is installed. Will be installing Wubi in the second one (it is an old 80 GB ATA HDD). Can anyone tell me how to do so. Presently second HDD is visible to Windows. 

After that, is it possible to map the windows HDD to Ubuntu.

Emma

---

### Post by Mark Phelps on 2012-08-27
Since you have two physical drives, there is no reason to use Wubi anymore.  Just install Ubuntu to the second drive -- using the whole drive.

Would recommend the following:
1) Have only the second drive connected, NOT the MS Windows drive
2) Boot into the Ubuntu LiveCD/USB
3) Install Ubuntu using the option to utilize the entire drive
4) When done, reconnect the MS Windows drive -- but continue to boot from the Ubuntu drive.  This is important.
5) When inside Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB configuration file, adding and entry for Windows.

When you reboot, you will be presented with a GRUB menu allowing you to select whichever OS you want to run.

---

### Post by emmagood on 2012-08-29
Thanks Mark,

  It is a little different situation. In the second HDD, I am planning to install both Ubuntu & Win 7. So, as I understand, I will have to install Win 7 first, then disconnect first HDD and then start the steps. When I have completed the Ubuntu installation,  boot into Ubuntu only and update Grub to get win 7 in boot menu. Then connect the first drive back, again boot in Ubuntu and again update the Grub.

Pls. confirm if my understanding is correct.

Regards,
Emma

---

### Post by darkod on 2012-08-29
Not exactly. There is no need to update grub to get win7 onto the menu, since it will be on the same disk the ubuntu installer will detect it and add it to the menu. You run update grub when the disk with the other OS was disconnected during the installation.

To get the windows from the first disk onto the menu, yes, you will need to run update grub, only once.

Also, when installing win7 make sure you don't let it use the whole disk. This is the default windows action but since you already plan to dual boot makes no sense, and can get you into trouble when shrinking the win7 later.

You can create the win7 partition on the 80GB disk using the win7 installer, or you can prepare it in advance using Gparted from ubuntu live mode (running from the cd). In any case, make the win7 partition the size you plan to use for win7, and leave the rest of the disk unallocated for ubuntu. The installer will detect and use this space, if you use the auto method. If you install ubuntu manually, you will create partitions into this unallocated space.

---

### Post by emmagood on 2012-08-29
OK, thanks Darkod. Will try that.

Emma.

---

