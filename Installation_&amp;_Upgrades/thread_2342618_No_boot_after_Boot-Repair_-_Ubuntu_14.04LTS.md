---
title: "No boot after Boot-Repair - Ubuntu 14.04LTS"
date: 2016-11-08
forum: Installation &amp; Upgrades
---

### Post by ggreuel on 2016-11-08
For quite awhile (not sure exactly how long) I have had to manually select the boot device at the BIOS prompt when restarting the server. I finally tired of this approach and loaded Boot-Repair on a USB Live stick and used the "recommended" button. Now I don't get the dreaded, "Reboot and select a proper boot device" screen right away. I get the normal Ubuntu selected and other advanced options available too. The countdown timer ticks away for 30s. Before Boot-Repair, I would have selected "ubuntu" and normal boot would occur. Now when I select "ubuntu" I get this:
> error: file ‘vmlinux-3.16.0-77-generic.efi.signed’ not found.
unaligned pointer 0xcd8263f8
Aborted. Press any key to exit.

The nice thing about Boot-Repair is the detailed system log:
[http://paste.ubuntu.com/23432877/](http://paste.ubuntu.com/23432877/)

A few more notes
[LIST]
[*]Only OS installed/boot is ubuntu 14.04LTS
[*]sda/sdb/sdc/sdd disks are used in RAID. No other partitions or boot partitions here.
[*]sde is the system drive
[*]sdf is the USB Live disk
[/LIST]

I appreciate any assistance.
Greg

---

### Post by yancek on 2016-11-08
The grub.cfg menuentry for Ubuntu points to the kernel in question on "hd3,gpt2" which would be sdd2 not sde2 where your Ubuntu system is.  That's why it isn't found, looking at the wrong drive.  Use the Live USB first and mount sde2 to verify the kernel is there and then change the entry to "hd4,gpt2" in the grub.cfg and reboot to test.

Not sure why this would happen unless you changed the location of various drives?  If the boot succeeds, you need to run "sudo update-grub" when booted.

---

### Post by oldfred on 2016-11-08
Not sure how you got grub installed to an ESP - efi system partition on sdf.
Script did not show fstab which it usually does, which may say in comments # install to sda or similar? Which would then mean you installed before adding RAID set.

Grub, so far only installs to drive seen as sda. Not sure if you can force it to update to any other other place.

One work around has been to make sure you have ESP on sda, and then copy files to another drive.

I have found that SATA port order usually determines UEFI/BIOS drive order which then is grub/ubuntu drive order. But in BIOS boot drive was always hd0 in grub. So I always make sure boot drive is in SATA0 and hard drives are in order I want in SATA port order. If DVD it is last.
Not sure if you change drive port order if that will cause other issues with your RAID.

You may want to file a grub bug. I indirectly refer to issue in this bug, but it was more to get different entries for each version of Ubuntu I have installed.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1450783](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1450783)

---

### Post by ggreuel on 2016-11-08
@yancek - Once I reconfigure the drives I will look at the entries in grub.cfg as you recommend.

@oldfred - sdf is the USB Live. It didn't boot as "USB", but booted when I selected the USB in the EFI option. 

I had a RAID drive fail a few months ago and rearranged the sata plugs. That may have caused the sd[] ordering change and caused my issues. I will try and set the boot to sda as you suggest by cable configuration and see if that at least gets the boot to equal sda.

---

### Post by oldfred on 2016-11-08
If sde, then it is BIOS boot.
Then you are into what type of RAID, which I do not know well.
Some RAID like BIOS RAID or "fakeRAID" install in the /mapper, but hardware RAID or Linux software RAID install to MBR like any standard install.
But then in Boot-Repair you should just be able to select to reinstall grub to sde. Do not use auto fix as that will install grub to the MBR of every drive. Use advanced options and choose install & drive to put grub boot loader into.

---

### Post by ggreuel on 2016-11-08
Solved by
1) Reinstalled an old image via clonezilla. This fixed the boot-repair problem.
2) Moved cables to make boot disk sda. This fixed boot issue.

All well here now. Thanks!

---

