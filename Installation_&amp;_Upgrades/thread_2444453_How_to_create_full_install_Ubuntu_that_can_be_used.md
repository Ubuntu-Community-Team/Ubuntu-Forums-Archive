---
title: "How to create full install Ubuntu that can be used in any computers?"
date: 2020-05-30
forum: Installation &amp; Upgrades
---

### Post by hendits on 2020-05-30
I installed a completed UBUNTU 20.04 LTS on a USB Flash Drive (16 Gb Toshiba).
After the installation is completed in my computer (let say it: Computer-A - Dell with Windows 10), it created a new boot option "UBUNTU" in BIOS.
So now there are two selection in BIOS in my computer: "Windows Boot Manager" and "UBUNTU".


If I restarted my computer (Computer-A) and select "UBUNTU", then I can access to my UBUNTU operating system that I just installed, and it looks good.


But if I insert my USB Flash Drive into another computer (let say Computer-B - it is also Dell with Windows 10) , I do not see the selection to choose "UBUNTU".
And if i check the BIOS in Computer-B, there is no selection to choose my USB Flash Drive as a boot loader. 
It seems my USB is not recognize as bootable device.


_**The question is**_: How to make my USB Flash (with completed/real UBUNTU) to be able to use it in any computers?


_FYI, this is how I prepared the installation for the completed UBUNTU._


I prepared 2 USB Flash Drive:


1.) USB-1 (Scandisk 30Gb) - this USB is for the live UBUNTU (I will use this USB to do the installation for the target USB)
    - I follow these steps: the [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)
    - I used RUFUS and get the Ubuntu 20.04LTS ISO file from ubuntu.com


2.) USB-2 (Toshiba 16Gb) - The completed Ubuntu to be installed here
    - I did 3 partitions:
       Partition 1: Fat32 - set flag as boot and esp
       Partition 2: SWAP (2048 Mb)
       Partition 3: Ext3 (size: the rest of space) - mount point to /


So using the USB-1, I do the installation with target USB-2.

---

### Post by yancek on 2020-05-30
The most likely scenario is that you did a UEFI (default for windows 10) of Ubuntu and Ubuntu wrote the EFI files to the EFI partition on the first drive of the first computer you installed to.  The Ubuntu installer by default will install EFI files to the first drive.  If you want to boot EFI on another computer, you need to create an EFI partition on the USB drive and write/copy the ubuntu efi files there. Take a look at the Ubuntu documentation at the link below.  In order for this to work, your second computer must also be UEFI capable which it should be if it is fairly new.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by lazyteddy on 2020-05-30
During installation, which device did you choose for the boot loader installation? And which device is set as the first / default boot device in BIOS / UEFI? My guess is you installed the boot loader to the hard disk, which the computer boots from by default. You would have to install it on the USB drive, and select the USB as boot device during start up.

Edit: I guess I took to long formulating this one out :-)

---

### Post by oldfred on 2020-05-30
Even if you tell the installer to install to the ESP - efi system partition on an external drive, Ubuntu's Ubiquity installer in UEFI mode only installs to the first drive seen, usually the internal drive's ESP.

Several work arounds.
Since you have ESP on flash drive, you can just copy /EFI/Ubuntu &  /EFI/Boot to external drive's ESP. And edit fstab with external drive's UUID for the ESP, so if grub does a major reinstall/update, it updates the correct ESP.
External drives actually boot from /EFI/Boot/bootx64.efi which is same name, slightly different version of grub you used to boot flash drive installer. It will show as UEFI:flash drive just like installer did.
From system with grub on internal drive, you can use ubuntu entry or boot using UEFI boot menu & flash drive's boot entry. 

Other alternatives are to totally reinstall grub2. Grub installs to external drives but you need the removeable parameter so it knows to create /EFI/Boot (even though now a default). You can do this manually from within install or with Boot-Repair.

Or you can reinstall and use the work around on the bug report. Please add to bug report. It is years old and we do not seem to be getting much help. Also other related bugs.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

---

### Post by C.S.Cameron on 2020-05-31
You can't go wrong if you unplug any existing HDD before proceeding with install to USB.
Here is a step by step for making full install USB's: 
[https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)
Perhaps at this point you can just reinstall GRUB to your bootable USB from a Live USB booted in UEFI mode:
```
sudo mount /dev/sdxY /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdx
```
Where x is the USB drive letter and Y is the partition number.
Confirm that the existing EFI partition is not referenced in fstab, if it is # it out.
:

---

### Post by hendits on 2020-05-31
Thanks all for your explanation. All your reply are aligned and provided me a direction on what's missing.
So you right, Ubuntu installer always find the first drive seen.
And yes, in my previous installation, I did NOT disable my existing HDD in computer, because I was assuming it will install the EFI system to the target USB (because I tought I did not touch the HDD at all during the installation).


Now I managed to fix this issue, and I just tried my USB to another computers (Windows), and now it is bootable. It is really good!


_**And FYI, below is what I did.**_


_**Background**_: Partitions in target USB (full installed UBUNTU):
> Partition 1: sdc1: Fat32 - set flag as boot and esp
> Partition 2: sdc2: SWAP (2048 Mb)
> Partition 3: sdc3: Ext3 (size: the rest of space) - mount point to /


_**For reference**_, I tried to read these links that you gave me earlier:
*> [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)*
*> [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)*
*> [https://bugs.launchpad.net/ubuntu/+s...y/+bug/1396379](https://bugs.launchpad.net/ubuntu/+s...y/+bug/1396379)*
*> [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)*


_**And then I did the following steps:**_
[COLOR=#ff0000]*Note: I am not so familiar with some of below commands. So perhaps anyone can advise if whether below steps can be simplified.*[/COLOR]
[COLOR=#ff0000]*Perhaps some steps that I did below are not necessary, I just tried to follow based on various resources.*[/COLOR]


Step 1. Copy the boot and the EFI folders from the Ubuntu ISO file to the boot,esp partition sdc1.


Step 2. Copy grub.cfg from partition sdc3 /boot/grub/ to partition sdc1 /boot/grub/ overwriting the grub.cfg file.


Step 3. Run Terminal


Step 4. sudo mount /dev/sdc1 /mnt


Step 5. sudo grub-install --boot-directory=/mnt/boot /dev/sdc


At this stage, it shows error: failed to get canonical path of '/cow'.


So I continue do below:


Step 6. sudo mount /dev/sdc3 /mnt


Step 7. sudo chroot /mnt


In root@ubuntu:
Step 8: grub-install /dev/sdc --boot-directory=/mnt/boot /dev/sdc


It shows another error: cannot find a device for /mnt/boot/grub (is /dev mounted?)


Then I exit, and try to get some info from this youtube: *[https://www.youtube.com/watch?v=8lod8sRb_6I](https://www.youtube.com/watch?v=8lod8sRb_6I)*
And continue steps below.


Step 9. 
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/prc /mnt/proc
sudo mount --bind /dev/sys /mnt/sys
sudo chroot /mnt


In root@ubuntu:


Step 10. grub-install /dev/sdc --boot-directory=/mnt/boot /dev/sdc


It shows another error: cannot find EFI directory.


Then exit from root@ubuntu and read this link: *[https://askubuntu.com/questions/853497/grub-install-error-cannot-find-efi-directory](https://askubuntu.com/questions/853497/grub-install-error-cannot-find-efi-directory)*
And I continue do the following:


Step 11. sudo -i


Step 12. mount /dev/sdc1 /mnt/boot/efi


Step 13. grub-install /dev/sdc --boot-directory=/mnt/boot /dev/sdc


And now the installation is finished successfully.

---

### Post by hendits on 2020-05-31
I choose the boot loader installation to sdc1 (partition 1 in target USB). But it seems Ubuntu installer always install to the first drive seen first (see other replies above). Thanks for your help!

---

### Post by dragonfly41 on 2020-05-31
If you want to install a boot loader in /dev/sdc1 you can try installing rEFInd and at installation time specify the prepared /dev/sdc1 (EFI partition with boot flags enabled) to receive the rEFInd boot loader.
rEFInd can install without impact on existing grub and runs in a different universe. At least it works fine for my needs and I have Ubuntu in external SSD.

---

### Post by C.S.Cameron on 2020-06-01
@hendits
Thanks for the report.

What would you suggest that I change in the step by step instructions to improve them? 
Have you tried booting in BIOS/Legacy mode yet? Or on another computer?
I think the install goes a little smoother if Legacy mode is available, Then the HDD does not need to be unplugged.

---

### Post by hendits on 2020-06-04
@C.S.Cameron 
Thanks for the message, and apologies for late reply.

Yes I managed to boot in another computer (BIOS). But I have not try yet in legacy mode.
It is looks good now! 

Thanks again for your help. Very helpful!
Cheers.

---

