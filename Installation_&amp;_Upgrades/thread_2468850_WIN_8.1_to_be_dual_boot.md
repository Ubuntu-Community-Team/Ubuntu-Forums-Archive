---
title: "WIN 8.1 to be dual boot ?"
date: 2021-11-11
forum: Installation &amp; Upgrades
---

### Post by oygle on 2021-11-11
I have WIndows 8.1 on an old laptop. Can I boot from a Kubuntu usb and install Kubuntu 20.04 in another partition, so that the laptop is dual boot ?  As Windows seems to be particular about wanting the primary partition, I assume I can just reduce the size of the WIN partition and then add a new partition for the Kubuntu installation, is that correct ?

Any gotchas ?  Also if it works out okay and I boot into Kubuntu, will I be able to see and access all the files in the WINdows partition ?

---

### Post by Impavidus on 2021-11-12
Yes, that should work. Just keep in mind:
- Use Windows tools to shrink Windows partitions, use Linux tools to handle Linux partitions.
- Disable FastStartup in Windows, or Kubuntu won't be able to access the Windows partition. It won't even be able to create an entry for Windows in the grub (boot loader) menu.
- If this is a bios/legacy system with an MBR partitioned hard drive (as opposed to UEFI with GPT partitioning), things get a bit harder and much less reliable. Computers with Windows 8 preinstalled by the retailer are always UEFI, but some home-installed systems or systems upgraded from Windows 7 may be bios/legacy.
- For some hardware, there are some more hoops to jump through.

---

### Post by yancek on 2021-11-12
I'd agree that the first thing you need to do is determine whether your computer is UEFI capable and your windows 8 is installed in UEFI mode.  If you do not know this, the easiest way to determine it is to boot your Kubuntu USB with the Try Kubuntu option, then open a termial and type the following command (Lower Case Letter L in the command)

```
sudo parted -l
```

If it is EFI, it will show one of the partitions as an EFI System Partition and in that case you will need to install Kubuntu UEFI also.  If you don't see the EFI partition, you have a Legacy install and Kubuntu must be installed in Legacy mode.  Ubuntu has a documentation site at the link below explaining how and why you need to do these things so  I would read through that first.  Some of it is specific to Ubuntu but much will apply to Kubuntu also.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I would also suggest that after you determine if your windows 8 is UEFI (or not) you do an online search for installing KUBUNTU UEFI or Legacy, whichever is appropriate.
You shouuld also determine if your drive is GPT which information is available from the parted command above.  If it is, the primary partition business is nothing to worry about.  If it is not GPT you are only allowed 4 primary partitions.  Windows system files do not need to be on a primary partition but its boot files do so if you have no unallocated/free space, you will need to create it by shrinking the largest windows partitions to create free space.  Do not create a partition for Kubuntu from within windows as that can be done with the Kubuntu installer.  You will need to format the Kubuntu partition with a Linux fileystem and that can't be done from windows. 

Tens of  millions of people have done this so do your research, it's not that difficult.  You will need the ntfs-3g software installed in Kubuntu to read/write to your windows partition.  I don't know if Kubuntu has it installed by default.  I would highly recommend that you NOT modify any windows system files from Linux but only use it on data partitions.

---

### Post by mIk3_08 on 2021-11-12
> **oygle said:**
> I have WIndows 8.1 on an old laptop. Can I boot from a Kubuntu usb and install Kubuntu 20.04 in another partition, so that the laptop is dual boot ?  As Windows seems to be particular about wanting the primary partition, I assume I can just reduce the size of the WIN partition and then add a new partition for the Kubuntu installation, is that correct ?
Any gotchas ?  Also if it works out okay and I boot into Kubuntu, will I be able to see and access all the files in the WINdows partition ?
If you need some installation guide for dual boot Operating System here are the guides that can easy help you with your dual or multiple Operating System boot installation concern. Just [click here]("https://help.ubuntu.com/community/MultiOSBoot") to view the guide page. Hope it helps. Good Luck and Regards.

---

### Post by oygle on 2021-11-12
Thanks everyone for your replies. I have now been trying for a few hours just to do

```
sudo parted -l
```

in an attempt to see if the Win 8.1 is EUFI or not. This is an old HP Probook 4330S with no screen. There is an external monitor but on boot it is exteremely hard to 'catch' the sequence to be able to use the external monitor. Then many boots later, even with a Kubuntu usb 20.04.3 boot , Windows wanted to gain control all the time. It was only by getting into BIOS and resetting everything to default that the computer would even successfully boot from the usb. I have used this laptop for Kubuntu for years and only recently installed the WIN 8.1, so I'd have to assume the WIN 8.1 install messed up something with booting or partitions ??

Anyway, now I can boot from the usb, BUT the attached pic is all I see. See [https://ubuntuforums.org/showthread.php?t=1958073&p=14066761#post14066761](https://ubuntuforums.org/showthread.php?t=1958073&p=14066761#post14066761) for a question re getting the correct image on the usb.

Possibly as I had to reset all BIOS to defaults, it is either a EUFI/UFI setting ??

---

### Post by oygle on 2021-11-12
This has forced me to re-evaluate my "need" for Windows. Single boot has worked many times on that laptop, meaning fresh installs by using a usb. I'll steer clear of dual booting on that laptop. The no screen/external monitor may be compounding the issues. Have successfully done a VM on Kubuntu in the past with a WIN 8 running in the VM, so that looks like the only way to have Kubuntu and WIN 8.1

The BIOS 'secure erase' is running now, so _should_ have a clean/clear Kubuntu boot after that. Thanks for your help.

---

