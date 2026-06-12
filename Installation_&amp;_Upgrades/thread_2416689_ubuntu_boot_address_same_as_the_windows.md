---
title: "ubuntu boot address same as the windows"
date: 2019-04-13
forum: Installation &amp; Upgrades
---

### Post by ilhampratama24 on 2019-04-13
Hello guys,im new to ubuntu 18.04 LTS and i have just installed dual boot ubuntu and win 10 in different partition and have a different boot address. At first it runs good untill the win 10 update and no grub showing up, and i try to enter the boot mode and the address of ubuntu and win10 was just the same but in different partition!. I've tried boot-repair using sudo boot-repair -d but it always stuck in Reinstall GRUB. this may require several minutes and it takes forever to finish. Is there anyone who can help? Thanks a lot

---

### Post by oldfred on 2019-04-13
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2019-04-13
As suggested above, if you have little familiarity with bootloaders, the best option with boot repair is to Create BootInfo Summary and post the output so members with more experience can view it and make suggestions.  I'm not sure what you mean when you say "boot address" but if you did a major update in windows, it likely turned hibernation on again and also changed the boot order.  Those are just 2 reasons why you need to post the boot repair output because there are a number of other possible problems.

---

### Post by ilhampratama24 on 2019-04-13
After i do boot-info summary it shows this link [http://paste.ubuntu.com/p/Mh8csYqh6K/](http://paste.ubuntu.com/p/Mh8csYqh6K/)

---

### Post by oldfred on 2019-04-13
One issue is fast start up which sets the hibernation flag.
And even if you turned it off before, Windows updates, which you may not notice will turn it back on.
Grub will not boot Windows when hibernation flag is set. Nor will you be able to read/write any NTFS partitions.

> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
Windows is hibernated, refused to mount.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Not sure what you mean by address is the same. You show two different UEFI boot entries, Windows & Ubuntu.

---

### Post by ilhampratama24 on 2019-04-13
I have unchecked the turn off fast in windows but it directed me to GNU Grub version 2.0.2. What should i do next?

---

### Post by oldfred on 2019-04-13
Does grub boot?

And since during install grub was not able to see Widnows, you may need to run this to add Windows to grub menu.
sudo update-grub

---

### Post by ilhampratama24 on 2019-04-14
i do input sudo update-grub but it says that usr/sbin/grub-probe: error: failed to get canonical path of /cow

---

### Post by ilhampratama24 on 2019-04-14
by the way it always stuck at line before it hangs 
=> [PY] => reinstall the grub-efi-amd64-signed of sda6

---

### Post by ilhampratama24 on 2019-04-14
and after it takes forever the screen pop up like this [https://drive.google.com/file/d/1whWh4izir1WF1QU6SQ5MU9nQ-8UC9dlH/view?usp=drivesdk](https://drive.google.com/file/d/1whWh4izir1WF1QU6SQ5MU9nQ-8UC9dlH/view?usp=drivesdk) and what i mean the boot address is the same is like this [https://drive.google.com/file/d/1Y-kSDkWJVzwejtmEFL-quV2ZVCmhWCOL/view?usp=drivesdk](https://drive.google.com/file/d/1Y-kSDkWJVzwejtmEFL-quV2ZVCmhWCOL/view?usp=drivesdk) at first the windows boot manager and ubuntu have different (P1: address) but now it just the same

---

### Post by oldfred on 2019-04-14
/cow is copy on write.
Or you ran a command to update using live installer. Command was intended to be run if you could boot your install.

This is the model of your hard drive:
       ata-[COLOR=#ff0000]ST1000LM035-1RK172[/COLOR]_WDE57SVT-part1 -> ../../sda1 

So that Windows & Ubuntu are booting from same hard drive is normal.
And they share the same ESP - efi system partition on that drive.

---

### Post by ilhampratama24 on 2019-04-14
Alright thanks for the advice! now i can boot to my ubuntu by updating grub and initramfs but now the problem it will directed boot ubuntu without showing any grub menus. i've tried to boot repair and this is my paste bin: [http://paste.ubuntu.com/p/sHQHXX964p/](http://paste.ubuntu.com/p/sHQHXX964p/) . Any ideas?

---

### Post by oldfred on 2019-04-14
Your sda2 is now shown as bios_grub but 204,800 sectors. That typically is the size of a Windows boot partition which would have boot flag.
A bios-grub only needs to be 1 or 2 sectors as core.img is small.

So you erased bootmgr & /boot/BCD by converting Windows boot partition to bios_grub.
You do have a copy of bootmgr in your main Windows partition sda4, but no BCD. You do not have to have the Boot partition, but then must have boot files in main install partition, your c: drive and boot flag on that partition.

You will have to add boot flag to sda4 as Windows will not otherwise try to repair it. Then temporally install Windows boot loader to MBR. I think Windows repair console was in its boot partition, not sure if f8 will still get you to a repair console or you just have to use your Windows repair flash drive to run Windows fixes to create a new BCD.
Once Windows boots, then you can restore grub to MBR and run sudo update-grub to add Windows to grub menu.
Grub only boots working Windows, and Windows 10 will keep turning on fast start up with updates, preventing grub from booting it. So keep Windows flash drive handy and Ubuntu live installer handy. 
New systems are all UEFI and from UEFI you can directly boot Windows if grub does not boot it. But with BIOS/MBR and only one drive, you can only have one boot loader in MBR.

---

