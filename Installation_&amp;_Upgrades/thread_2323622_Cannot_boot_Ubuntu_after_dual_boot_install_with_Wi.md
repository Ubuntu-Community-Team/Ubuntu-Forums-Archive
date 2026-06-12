---
title: "Cannot boot Ubuntu after dual boot install with Windows 10 UEFI"
date: 2016-05-06
forum: Installation &amp; Upgrades
---

### Post by uli9 on 2016-05-06
I installed Ubuntu 16.04 on an Acer Aspire R laptop with Windows 10 UEFI secure boot preinstalled.
During install I chose 3rd party software and created a 'disable secure boot' password.
All install partitions were created by me beforehand. So, I did 'something else' install.
Wasn't sure about 'mount point', thought it should be /boot/efi, but didn't work, so I used /.
It finished install. But now it only boots into Windows.
What can I do?

---

### Post by yancek on 2016-05-06
Did you boot and install Ubuntu UEFI?  I don't use it myself so all I can suggest is you read through the Ubuntu documentation on dual-booting UEFI at the link below and compare it to what you did.  Someone else with more detailed knowledge should be along.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by uli9 on 2016-05-06
I did read through that and much more. The installer seemed to recognize that it is an UEFI install. I did not see any choice anywhere.

---

### Post by uli9 on 2016-05-06
What I don't understand is if grub2 is supposed to take over the bootloading or if Ubuntu gets added to the Windows bootloader.

---

### Post by ubfan1 on 2016-05-06
UEFI allows multiple bootloaders.  The first one run is selected in the firmware, and evidently you have Windows as the first bootloader to run.  You can select which bootloader to run manually with the EFI menu, which runs when you type some function key (varies by machine) to get a device/OS selection to boot.  Select Ubuntu, then you can use efibootmgr -v to see the entire boot order, and use efibootmgr to change the order to what you want.  Or just keep using the EFI menu.

---

### Post by LostFarmer on 2016-05-06
Acer seems like it does not play well with linux.  see [http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by ubfan1 on 2016-05-06
Some machines have a silent fallback when the first bootloader fails, they attempt to boot /EFI/Boot/bootx64.efi  before attempting the second bootloader in the list.  Now by default, this bootloader is the windows bootloader, but you can simply replace it with the shimx64.efi from /EFI/ubuntu.  shim needs the grubx64.efi in the same directory, so copy grubx64.efi there too, keeping its name.   Simple enough to try before the other add-trust mechanisms.  Also good because sadly, Windows is not the only one to mess around with the bootloader list.

---

### Post by uli9 on 2016-05-06
@ubfan1
Hold your horses, where is this EFI menu? When I hit F2 I get into what I would call the BIOS/setup menu in the old days. But here I can only chose the boot order and the boot mode: UEFI or legacy. Is there another menu?

---

### Post by uli9 on 2016-05-06
FYI, I just had a chat with Acer 'support' and they basically just disconnected me because of quality reasons....
I think I am going to return this thing if there is no solution.

---

### Post by ubfan1 on 2016-05-06
Yes there is another menu, try F10, or F8, or F12 -- varies by machine, may have to try them all.  You may get a simple list first, like hdd, net,...  choose hdd, then you may get another set of choices for OSes on the hdd.  Or, everything may be listed in one big menu to choose, the name you are looking for is "ubuntu".

---

### Post by uli9 on 2016-05-07
@ubfan1
I tried all function keys, esc and del. There is only F2 for bios/setup and F12 for boot menu, which only displays the Toshiba hdd under Windows Boot Manager (one entry). If I choose that it just boots Windows. I also went into into bios setup and moved the hdd1 and hdd2 entry before Windows boot manager, but nothing changed.
Maybe I did not install Ubuntu correctly. I did not see a choice where to install Grub. But, what do I choose as the MOUNT POINT for the EXT4 FILE SYSTEM. I chose "/"? Do I need to point the the installer somewhere to the UEFI partion? Where?

---

### Post by uli9 on 2016-05-07
Some advice suggested to use Boot Repair, which is not included in the install image. I don't have an ethernet port, only WiFi, which doesn't work. I ordered a USB ethernet adapter, which will come soon. I cannot boot to RescueTux USB stick due to secure boot.
I am willing to start from scratch. I have all partitions backed-up and a Windows 10 install USB stick. I read out the key with Belarc Advisor, because there is no sticker.
Should I wipe everything and install Ubuntu first and then Windows?
Please, someone, there must be a solution?

---

### Post by ubfan1 on 2016-05-07
Generally, it's better to have Windows installed first, then Ubuntu.  You installed / to the ext4 filesystem OK.  The Ubuntu bootloaders (shimx64.efi and grubx64.efi)  should have been copied into EFI Partition's /EFI/ubuntu directory.  Confirm that they are there.  If you boot the live media (in UEFI mode of course), can you run sudo efibootmgr -v   and see all the boot entries, and is ubuntu a listed entry?
The boot-repair report answers these sorts of questions, so it's worth trying to get a copy onto your live media.  If you have the /EFI/ubuntu bootloaders, you can do the copy of both to /EFI/Boot  and rename the shimx64.efi to bootx64.efi (and rename or delete the original bootx64.efi which is a Windows bootloader).  If your efibootmgr -v report has ubuntu before the "Windows Boot Manager", try a boot and see what happens.  If Windows comes up, reboot with live media, and with efibootmgr, change the "ubuntu" name on the entry to "Windows Boot Manager" (now you have two of them, so be aware).  Try to boot again.  If Windows still comes up, reboot with the live media and change the name of the boot file to /EFI/ubuntu/bootmgfw.efi (just like the windows file), and then rename the actual file /EFI/ubuntu/shimx64.efi to /EFI/ubuntu/bootmgfw.efi.  That should do it if nothing else did.  
  Still boots windows, then try the "trust" thing in the BIOS, set a supervisor password, set trust on the ubuntu bootloaders, and try a reboot.  
  You are probably a few name changes away from a working system, but thank the vendor for all the nonsense -- the UEFI standard does not require specific names.  
What BIOS/firmware versions are you running?  Some older machines might need to be updated.

---

### Post by uli9 on 2016-05-07
This is the output of efibootmgr -v:

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0004,0001,2001,2002,2003
Boot0000* ubuntu    HD(1,GPT,d5ea59e8-74c3-4a71-9842-e8d06e75b256,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Linpus lite    HD(1,MBR,0x24,0x3f,0x78bfc1)/File(\EFI\Boot\grubx64.efi)RC
Boot0002* Unknown Device:     HD(1,GPT,d5ea59e8-74c3-4a71-9842-e8d06e75b256,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0003* Network Boot-IPV6: 00-23-57-0C-88-70    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/MAC(0023570c8870,1)/IPv6([::]:<->[::]:,0,0)RC
Boot0004* Windows Boot Manager    HD(1,GPT,d5ea59e8-74c3-4a71-9842-e8d06e75b256,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0005* Windows Boot Manager    HD(2,GPT,b30d8ce8-9777-4e56-a00c-d75c49651c2c,0xe1800,0x31800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC


This is the installed root directory:

ubuntu@ubuntu:/media/ubuntu/04175061-aae0-44c8-a843-3fae3af02064$ ls
bin   cdrom  etc   initrd.img  lib64       media  opt   root  sbin  srv  tmp  var
boot  dev    home  lib         lost+found  mnt    proc  run   snap  sys  usr  vmlinuz


It looks like Ubuntu is there. Where is /EFI? How can I access the UEFI partition? How can I mount it to get access?

Linpus Lite is the install media.

---

### Post by uli9 on 2016-05-07
BTW, this is a new laptop I just bought. So, I have 15 days to bring it back.

Anyways, the BIOS is:

InsydeH20 Setup Utility v1.06

In the BIOS, in the Security tab, where the passwords are, the only thing I can do is 'Set Supervisor Password'.

"Supervisor Password controls access to the whole setup utility. It can be used to boot up when Password on boot is enabled."

What should I do next?

---

### Post by ubfan1 on 2016-05-07
First try to add the 0000 entry to the boot order before 0004 ( sudo efibootmgr -o 0000,0004,0001,2001,2002,2003  )

The EFI partition is not the root partition, what you looked at looks like the running  live media -- in a normal system, the EFI partition gets mounted at /boot/efi, so look there.  If you need to, figure out which partition on the hard disk is the EFI (probably sda1 or sda2, the several hundred meg FAT partition) and mount it yourself.  if /mnt is not already got any amounts, just use it:  sudo mount -tvfat /mnt /dev/sda2  (assuming its sda2 for the example). 
  The version of the setup utility is not the firmware version (it might show briefly at power-up, or from when you run dmidecode, but save that for later.

---

### Post by uli9 on 2016-05-07
So, I am booted into Ubuntu live USB. There is nothing in /mnt. The EFI partition is sda1, I checked with gparted. When I do sudo mount -tvfat /mnt/dev/sda1, I get "mount: can't find /mnt/dev/sda1 in /etc/fstab. If I look at fstab there is nothing listed. This is all on the live USB. What am I doing wrong?

---

### Post by uli9 on 2016-05-07
The directory where Ubuntu is installed on the hdd is /media/ubuntu/04175061-aae0-44c8-a843-3fae3af02064. When I look at /boot/efi in that directory, it's empty.

---

### Post by uli9 on 2016-05-07
I did sudo efibootmgr -o 0000,0004,0001,2001,2002,2003. It still boots into Windows.

---

### Post by uli9 on 2016-05-07
It didn't change it:

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0004,0001,2001,2002,2003
Boot0000* ubuntu    HD(1,GPT,d5ea59e8-74c3-4a71-9842-e8d06e75b256,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Linpus lite    HD(1,MBR,0x0,0x3e,0xf32ba2)/File(\EFI\Boot\grubx64.efi)RC
Boot0002* Unknown Device:     HD(1,GPT,d5ea59e8-74c3-4a71-9842-e8d06e75b256,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0003* Network Boot-IPV6: 00-23-57-0C-88-70    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/MAC(0023570c8870,1)/IPv6([::]:<->[::]:,0,0)RC
Boot0004* Windows Boot Manager    HD(1,GPT,d5ea59e8-74c3-4a71-9842-e8d06e75b256,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0005* Windows Boot Manager    HD(2,GPT,b30d8ce8-9777-4e56-a00c-d75c49651c2c,0xe1800,0x31800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

---

### Post by ubfan1 on 2016-05-07
Good that /mnt is empty, so it may be used as a mount point.  my oops, I reversed things, the mount command should be
sudo mount   -tvfat   /dev/sda1    /mnt
Then an ls  /mnt    should show   EFI    as the top level directory.  See if it contains ubuntu  and look into /mnt/EFI/ubuntu to see it has
the shimx64.efi and grubx64.efi.
  Don't know why the boot order didn't get the 0000 added.  Try a few more times.  Did you set the supervisor password?  That might make a difference.

---

### Post by uli9 on 2016-05-07
OK, I set a supervisor password and have now access to more settings in the BIOS.
I ran the efibootmgr command again and it changed so 0000 is in first place. I rebooted, it booted to Windows again. I boot to live USB and check efibootmgr -v and it's back to the old setting.
I was able to mount the UEFI partition and confirm that shimx64.efi and grubx64.efi are there.
What now?

BTW, I really appreciate your help! I hope we can make this work.

---

### Post by uli9 on 2016-05-07
ubuntu@ubuntu:/mnt/EFI/ubuntu$ ls
fw  fwupx64.efi  grub.cfg  grubx64.efi  MokManager.efi  shimx64.efi

---

### Post by uli9 on 2016-05-07
Thank you!!! I got it. I went into the trusted part in the BIOS and added shimx64.efi and grubx64.efi. So, they showed up in the boot order menu. And I moved them to the top. Now grub comes up at powerup and I can still boot Windows. Holy cow what an ordeal. But it worked. Thank you ubfan1! I hope that helps other noobies.

---

### Post by ubfan1 on 2016-05-07
You're welcome.  Good to hear it's fixed.  Please mark the thread as "solved" with the thread tools at the top right, so others may more easily find a solution.

---

