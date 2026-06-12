---
title: "Can't boot original OS"
date: 2014-11-05
forum: Installation &amp; Upgrades
---

### Post by Ikinnik on 2014-11-05
Hello,

I just tried to install Ubuntu on my notebook alongside with my Windows 7. But something went wrong (well propably I screwed something up). I installed it but then I couldn't boot my original OS (Windows7). I used Boot repair and it finished with errors. Could you be so kind and help me with recovering my Windows 7? This is the error message [http://paste.ubuntu.com/8834233/](http://paste.ubuntu.com/8834233/) . I will be really happy for any help.

Thank you for your time

---

### Post by Impavidus on 2014-11-05
Your Windows is gone. On your hard drive you've got an EFI partition and three Linux partitions, for root, /home and swap, all exactly the same size (about 19GB). Which is BTW very large for the swap partition. The remaining 943GB of your drive is unallocated. There are no Windows partitions present.

I hope you had backups of all your important files. If not, you need some file recovery. As 94% of your drive is unused, chances are you can recover quite a lot, but not your entire Windows system. To get Windows back, you need Windows recovery DVDs or a Windows installation disk.

---

### Post by Ikinnik on 2014-11-05
Well that's what I thought and feared... I already searched some possible solutions for this. Would something like this help me?
> So basically, if you have this problem, download [PowerISO]("http://www.poweriso.com/"),  format a USB drive, click Create Bootable USB drive, select the Windows  Recovery Disc (you can download it online), boot from USB, click  command prompt, and do what it says there.

  For me, bootsect wasn't there, so I typed in Bootrec.exe /FixBoot and then Bootrec.exe /FixMbr like a link in that link says. Then I restarted my computer and it worked.



This guy accidentally removed his Windows 7 partition and he solved it with this. Or would you have another advise?

Thank you in advance

---

### Post by yancek on 2014-11-05
If you have your windows installation medium, install windows first and then Ubuntu again.  I would suggest you read a few tutorials on how to install Ubuntu before trying again.  A couple of links below.  The second link is to the Ubuntu site but is very simple and show the "Install Alongside" option.  If that's what you used before, then try the manual option which is referred to as "Something Else" which gives you more information and control.  The first link is much more detailed on the installation.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

### Post by Ikinnik on 2014-11-05
THank you for your answers. I really appreciate your help. Sooo do you think that there is a actual chance of recovering some data? Shouldn't I try that before installing Win7 again?

---

### Post by Mark Phelps on 2014-11-05
I'm not aware of any Windows "recovery" disks being available online -- presuming those can be use to REINSTALL Windows.  What IS availabe online is Windows REPAIR disks -- and those can only be used to fix problems, such as boot loader corruption.  They can not be used to reinstall Windows.

To reinstall Windows, you'll need full Windows install DVD.

---

### Post by QIII on 2014-11-05
Yes, DO try to recover your files before you reinstall.

I'm not familiar with the Windows tools, but I know there are many -- for a price.

Photorec is included in TestDisk, which is free.  It's not perfect and you often lose file names and much of the metadata.

Best wishes.

---

### Post by oldfred on 2014-11-05
You have UEFI capable hardware, and installed Ubuntu a second time with UEFI. It looks like you installed a first time with BIOS as you also have grub in the MBR. 

With multiple installs less data will be recoverable. Every time you write something or even use hard drive more old data is overwritten. So only use live installer, and immediately turn swap off or boot gparted or parted magic as they do not mount swap on boot. Installer auto uses swap on boot to speed up install, but your swap is near beginning of drive so use of swap is also overwriting data.

Was Windows 7 installed in UEFi boot mode with gpt partitioning or in BIOS boot mode with MBR partitioning. If MBR you need to use testdisk in MBR mode to find old partitions. If gpt you need it in gpt mode.

Only a few systems were UEFI hardware with Windows 7 in UEFI boot mode, most just before Windows 8 came out. But there were many UEFI hardware capable systems with Windows 7 in BIOS/CSM boot mode.

---

### Post by Ikinnik on 2014-11-06
I am trying to recover some data and then I'll just reinstall it all. Thank you all for help guys.

---

