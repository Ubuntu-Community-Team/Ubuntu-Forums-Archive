---
title: "Wiped HDD and installed Ubuntu, now it won't start."
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by Cause on 2014-05-22
I have reinstalled 14.04 at least 4 times. After the instillation everything is fine until I restart my computer. Then I get a message saying, [I]"Reboot and select proper boot device or insert boot media in selected device and pres a key."

[/I]I have ran boot repair, and this is what it gave me: [I][http://paste.ubuntu.com/7499920/](http://paste.ubuntu.com/7499920/)



[/I]My computer is a Gateway DXseries
DX4380G-UW308

          
[LIST]
[*]                 A6-Series APU A6-5400K (3.6GHz) 
[*]                 6GB DDR3 1TB HDD 
[*]                 Windows 8 
[*]                 AMD Radeon HD 7540D 
[/LIST]
              

It was a gift, and it is practically brand new. Thanks.

---

### Post by LastDino on 2014-05-22
Did you turn off the secure boot before trying this?
And what do you mean you wiped the HD?

---

### Post by Cause on 2014-05-22
No, I don't believe I touched anything to do with secure boot. If I don't know what it is, I don't touch it. I just Googled it and I'm still not too sure how to go about turning it off.

When I reinstalled I completely formatted my computer, and installed it on my primary partition. I also wiped all of the free space.
Looking to make Linux my primary OS again, but haven't used it since Red Hat 9.
I'm pretty dedicated to it, and would love to learn more about it seems how I'm in my second year as a computer science major.

---

### Post by LastDino on 2014-05-22
You need to turn it off in BIOS. Latest Windows machines come with UEFI. Which prevents installing anything other than windows.

There are countless threads here addressing the same issue, please search and read them up as much as possible and try again. I can't be more precise as I don't own any windows machine, but that step is mandatory on W8 (latest machines) machines.

---

### Post by Cause on 2014-05-22
Sounds like a plan. Thanks Dino. I've searched countless threads of people having my problem, but there were always different circumstances causing it. I'll look into it. Thanks a million!

---

### Post by Cause on 2014-05-22
Dino, I disabled secure boot, but the same problem is still there. I guess I will run boot repair one more time, and see if that works. If that doesn't work maybe reinstall it while secure boot is disabled? Really not too sure what to do.

---

### Post by Cause on 2014-05-22
I just ran boot repair, and still the same problem.
For what it's worth, paste.ubuntu.com/7501956

I suppose I should try to reinstall it again.

I was looking forward to joining this community *sad face*

Edit: THERE HAS TO BE A LOGICAL EXPLANATION FOR ALL OF THIS!
Maybe I should try installing it on a USB drive? I have an 8 GB. Not sure that that would work.
I know that the first 2 installs I encrypted my home folder. After I didn't, boot repair made me run a couple of extra commands to run in a terminal. After that it actually worked after a restart! But then the next restart it gave me the same error. I don't want to run boot repair everytime I sign off.
Smh idk what to do. I need to learn to Linux. I don't know too much about it.

---

### Post by LastDino on 2014-05-22
I'm starting to suspect that you didn't create separate /boot partition. It is failing to boot because it is EFI system and you need separate /boot partition on those to load boot files from.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See this page, follow all the possibilities, especially the one mentioned under creating EFI partition.

Here is also step by step instruction of dual booting, you should read this as well.
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

Have some patience, if not me there is rally of experts here who can solve your problem. It might take some time and reading on your part though.

---

### Post by oldfred on 2014-05-22
You do not need a separate /boot partition and BootInfo report shows you have an efi partition.

UEFI still shows a Windows boot entry, it has NVRAM and remembers previous entries.

      >  BootOrder: 0001,0002,0003,0000
Boot0000  Windows Boot Manager
Boot0002* UEFI: ST1000DM003-9YN162
Boot0003* UEFI: HL-DT-ST DVDRAM GH82N
Boot0001* ubuntu.



Some UEFI have been modified by Vendor to only boot the Windows entry. You can modify the Windows entry to boot grub or reinstall in BIOS/CSM mode. But then have to turn off secure boot, and turn on CSM or turn off UEFI.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Even thought you erased Windows from efi partition you can just recreate the folder & a Windows file name but make the file actually be grub or shim.

      
 /EFI/Boot
/EFI/Microsoft
/EFI/ubuntu

Alternatives:

 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   If Description has to be Windows then change description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by Cause on 2014-05-22
> **LastDino said:**
> I'm starting to suspect that you didn't create separate /boot partition. It is failing to boot because it is EFI system and you need separate /boot partition on those to load boot files from.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See this page, follow all the possibilities, especially the one mentioned under creating EFI partition.

Here is also step by step instruction of dual booting, you should read this as well.
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

Have some patience, if not me there is rally of experts here who can solve your problem. It might take some time and reading on your part though.

I had made it this far before I read your post:
I reinstalled Ubuntu and never restarted so I wouldn't get locked out. 
I ran disc repair, and got a different error message.
[http://i.imgur.com/wQxXr10.png](http://i.imgur.com/wQxXr10.png)  "The boot filesof [The OS now in use - Ubuntu 14.04 LTS] are far from the start of the disc. Your bios may not detect them etc. etc."
I followed the tutorial they gave me in the error message ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)). They suggested using Gedit to creat free space in ext4 to of 1000 MB. The problem is, is that it was greyed out. I cannot resize it at all, and I opened Gedit using **gksudo gparted**. [http://i.imgur.com/ySEV9RS.png](http://i.imgur.com/ySEV9RS.png)

Now that I have read your reply and read the links, I am pretty sure that I am still in EFI mode, even after disabling secure boot. I did not disable quickboot/fastboot to my knowledge, or enabled CSM. 

I believe I will be able to get back into Ubuntu on my HDD since I already ran disc repair once so that I can check the bios settings again, but that's not a guarantee. 

OldFred: I'm learning about this, and I'm somewhat fallowing what you are saying, but a lot of it is Greek :p
Hopefully my response to LastDino (the pictures etc.) will help us out some. Are you saying that I can create a partition in the Fat32/boot/EFI that is named something similar to


 /EFI/Boot
/EFI/Microsoft
/EFI/ubuntu

Not exactly understanding what you mean. I'm cramming as much as I can in my head right now. Give me a second to check up on those links. Also, I am not planning on installing Windows on this computer, unless it is on Virtual Box.

Thank you so much for the help!

---

### Post by LastDino on 2014-05-22
You can't re-size while being booted in Ubuntu because it is your root partition of your Linux/Ubuntu. Which is absurdly big, as it is recommended to keep it around 20-24GB. AND that is your real problem. You can however, resize it by booting into live season and running gparted there (I will wait for oldfreds confirmation on this as I've never done it myself)

Another thing is that you should break that hard-disk space into something like this for convenience of use;
/ = root= 20-24 GB (ext4)
/home = 100GB (Min should be bigger than /) (ext4)
swap = equal to amount of RAM you have. But since you've lot of RAM 4GB is fine.

Put rest into logical (it will be putted into one automatically once you create this first 3)  
This section of your HD will serve you as storage and place where you can install other linux if you ever want to in future.
You can break it however you like and should format it to Ext4.

I will not confuse you anymore as I'm sure Oldfred can guide you better. And If I was in your shoes, I would wait for his post before I do anything.

---

### Post by oldfred on 2014-05-22
With gpt partitioning there are only one type of partition, and default max is 128.
With MBR(msdos) partitioning you have 4 primary and one primary can be the extended which acts like a container for all the logical partitions you want.

When you erased Windows you also deleted the /efi/Microsoft folder in the efi partition. The UEFI menu still has a Windows boot entry to that now missing entry. And if your UEFI is one of those where vendor screws with the entries and only allows Windows, then you may have to restore the folder and a file named bootmgfw.efi so it thinks it is booting Windows. But that file can be grub or shim and it will work.

As LastDino suggests often much better with the new TB sized drives to have a smaller root of 20 to 25GB and use rest of drive as /home and/or data partition(s).

In UEFI with gpt partitioning the boot flag is used by gparted to define which partition is the efi partition. That is not the same as a boot flag in MBR partitioning. And the efi partition is more equivalent to the MBR in BIOS/MBR configurations. It is not a Boot partition. Both Windows and Ubuntu have more boot files inside their install. And Ubuntu can have a separate /boot partition, but that is not required for desktops, but may be required for server type configurations with RAID, LVM or encrypted LVM.

Ubuntu can boot from gpt partitioned drives with UEFI or BIOS/CSM. And Boot-Repair can easily convert from one to the other if drive is partitioned with gpt. If drive is MBR you can only boot with BIOS.

---

### Post by Cause on 2014-05-23
Ok, phew. First off, what would be the easiest way to go about setting up a gpt partition? Reinstalling, booting from the CD, something else?
And are you guys saying that I should make the ext4 "/" partition 20-25 GB, then make another one that is 100GB for home? I have no idea how I would go about making the 25 GB the root partition, and making the 100GB the /home partition. No clue what so ever where to start.

---

### Post by Cause on 2014-05-23
I GOT IT! I had to reinstall with CSM mode enabled, not just turn it on and try to boot up. Thank you both so much. You are miracle workers. I look forward to seeing you around!

---

### Post by LastDino on 2014-05-23
I was little to no help but I'm glad it worked out for you ^^

---

