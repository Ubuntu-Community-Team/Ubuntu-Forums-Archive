---
title: "During Ubuntu 18.04 install: grub install /dev/sda failed"
date: 2018-09-04
forum: Installation &amp; Upgrades
---

### Post by albev on 2018-09-04
Hi,

I want to install Ubuntu 18.04 on my Dell  XPS14 laptop alongside Win10. I created the USB install with rufus,  selected the try without install option and then install. Unfortunately,  "grub install /dev/sda" failed. In the details it says  that it can not open "/boot/efi/EFI/ubuntu/grubx64.efi" since it is no  directory. I tried both, the "alongside Windows"  option and other.

I looked into a few threads here but the  answers became very specific and technical very fast. And I am hesitant  to follow instructions that are not tailored to my case and I don't  understand. Plus my knowledge of the whole subject is negligible so I have  problems  understanding how some "solutions" translate into actions.

What I did till now:

    In windows switch off fast-boot (following this [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)).
    In windows switch off hibernate with powercfg.exe /hibernate off.
Bios update.


Here is the Boot-Info report: [http://paste.ubuntu.com/p/9Hhq34rVxD/](http://paste.ubuntu.com/p/9Hhq34rVxD/)

Thank you for your time.

---

### Post by yancek on 2018-09-04
Your boot repair output shows you have Ubuntu installed on /dev/sda6 partition.  You failed to install the Grub bootloader so you won't be able to boot Ubuntu until you change that.  You have an EFI install of windows but did not install any Ubuntu boot files to the EFI partition which is necessary.  The best I can suggest is to go to the source, the official Ubuntu documentation page on dual booting UEFI with windows which is at the link below.  If after reading that, you still have problems/question, please post back.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ubfan1 on 2018-09-04
Nothing looks amiss.  Maybe a filesystem problem on the EFI partition (it's just a FAT filesystem).  Can you mount it and create the /EFI/ubuntu directory?  if not maybe a chkdsk or fsck is necessary to try and repair the fs.  Backup the files first (copy them somewhere just in case the repair is bad).

---

### Post by albev on 2018-09-05
> **yancek said:**
> Your boot repair output shows you have Ubuntu  installed on /dev/sda6 partition.  You failed to install the Grub  bootloader so you won't be able to boot Ubuntu until you change that.   You have an EFI install of windows but did not install any Ubuntu boot  files to the EFI partition which is necessary.  The best I can suggest  is to go to the source, the official Ubuntu documentation page on dual  booting UEFI with windows which is at the link below.  If after reading  that, you still have problems/question, please post back.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I read the documentation and found that I forgot to disable Intel Smart Response Technology. I did that but it still failed at the same point.


> **ubfan1 said:**
> Nothing looks amiss.  Maybe a filesystem problem on the EFI partition (it's just a FAT filesystem).  Can you mount it and create the /EFI/ubuntu directory?  if not maybe a chkdsk or fsck is necessary to try and repair the fs.  Backup the files first (copy them somewhere just in case the repair is bad).

I mounted it, found that there is a FILE called ubuntu and not a directory. I renamed the file and created the directory, tried again and it worked! Unfortunately, I couldn't start Win10 now. Probably because of disabling SRT (there was a warning that this could happen). Turning it on again did not help. I made a Win10 USB stick and navigated to repair. It told me it couldn't repair the problem. Despite this, Win10 started fine afterwards. And Ubuntu also still works.

So thanks a lot for the help. Funny that it was such a simple thing.

---

