---
title: "Grub 2 dual boot problems."
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by casbahdk on 2012-09-06
I have just installed Ubuntu 12.04 64-bit as dual boot with Windows 7 on my home built desktop computer. I have an Asus Sabertooth 990FX mobo, which has a UEFI bios. Windows 7 is installed on /dev/sdb and Ubuntu 12.04 installed on /dev/sda

I have two boot problems that are interrelated:
1) I can't get a GRUB menu at startup by pressing either the "shift" or "esc" keys.
2) I believe that the Windows boot loader was overwritten when I installed Ubuntu on /dev/sda. I have tried to check this by running the following:
```
$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
```

Anyone out there that can offer some advice?

---

### Post by oldfred on 2012-09-06
If UEFI, both Windows & Ubuntu need to be installed in UEFI/gpt or BIOS/MBR modes. Since separate drives in may be possible to boot if not the same but you have to go into BIOS and change modes each time and then switch drives.

Are both drives gpt?

Post BootInfo link from this. It will add a Windows efi boot entry to grub if otherwise installed correctly. It also fixes BIOS installs of Ubuntu when on same drive as it will convert from grub-pc to grub-efi, but I not sure about two drives.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
UEFI installs in BIOS, Boot-Repair to fix
[http://ubuntuforums.org/showthread.php?t=2048457](http://ubuntuforums.org/showthread.php?t=2048457)

---

### Post by casbahdk on 2012-09-06
Thanks for the quick reply. I have two TB-Western WD1002FAEX Black-7200RPM-SATA-III-64M drives. They are MBR drives. I have had various Linux distros installed on them before. Despite my mobo having an UEFI bios, Grub2 (grub-pc) seems to work fine on my computer.

My BootInfo can be found [here]("http://paste.ubuntu.com/1189446/").

Edit: I had to install this new mobo, after the last time that I have installed Linux, but the distro I used at the time booted without problems with the new mobo, and without changing to the efi version of Grub.

---

### Post by darkod on 2012-09-06
You are right, both disks are MBR but in that case it means you are not using UEFI boot since win7 needs gpt to work with uefi. Keep it that way since dual boot with uefi is more complex than with standard bios boot.

Your problem in this case is that you are missing the win7 boot files. I guess they were somewhere on /dev/sda because windows doesn't tell you where it puts the boot files, and you destroyed them with the ubuntu install.

Open Gparted and turn OFF the boot flag on /dev/sda1, then turn ON the boot flag on /dev/sdb1. Windows always follows the boot flag when writing boot files.
Then boot with your win7 dvd and run the Repair This Computer process 3-4 times (often you need to run it more than once). That should detect your win7 and put the boot files on sdb1.
It might or might not put the bootloader on sda deleting grub2, but restoring grub2 is very easy. Most important part is to get the win7 boot files done. You can restore grub2 easily if windows deletes it.

---

### Post by oldfred on 2012-09-06
Darko is  right,  you are missing the two boot files that Windows puts in the boot/repair partition. Often systems with two drives have sda set as boot drive. So an install of Windows on sdb will still put a 100MB boot partition with two of Windows boot files in that sda1 100MB partition.

You need a Windows repairCD or full install DVD to repair the Windows install. That will add the bootmgr & bcd back into sdb and grub can then find it and let you boot it.  If you put the Windows boot loader in sdb, then you can also directly boot it.

You are missing the files in red.
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

If you have the repairCD that will fix it. Or if you know someone or have access to another Windows 7 install that is either 32bit or 64bit and the same as yours.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by casbahdk on 2012-09-06
I have run the "startup repair" option six times for Windows 7, but Grub still does not recognize a Windows system on /dev/sdb when I update Grub. Should I turn the boot flag on /dev/sdb "off" again? Is there something else I should do?

---

### Post by darkod on 2012-09-06
Well, the windows repair process is very stupid sometimes. Try the manual way, in the command prompt, as explained in this link in the section Restore Windows Vista or 7 bootloader (the end of the first post).
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If that doesn't work, I'm not sure what's best to do. This is a windows issue and that it doesn't recognize it to repair the boot.

---

### Post by casbahdk on 2012-09-06
Weelll, bootrec.exe /fixmbr definately cleared the MBR, but bootrec.exe /fixboot returns "element not found".

Could this have something to do with Ubuntu erasing a "hidden" 100 MB partition that Windows uses?

---

### Post by oldfred on 2012-09-06
It may need chkdsk also.

One user just copied the bootmgr and the /boot/bcd to his install. Of course the BCD was not for the install and had to be updated. 

Windows only works on boot flag or active partitions. Did you also change BIOS to boot sdb first as Windows may be trying to look at the Ubuntu drive and of course cannot find anything as it does not see Linux partitions.

Generally easier just to have Windows as sda. While you can make it work in other drives it is not quite as automatic.

---

### Post by casbahdk on 2012-09-06
I am running chkdsk at this moment. I can try to see if Windows will boot if I change the BIOS to boot from sdb first, but I am at this point assuming that the boot loader was installed to sda as I lost the ability to boot into Windows 7 when Ubuntu installed Grub 2 on sda. When I prepared for installing Windows 7, I backed up my files and erased both disks, so that Windows could choose the disk to install on. I didn't even know until I was installing Ubuntu, that Windows had been installed on sdb.

Edit:

OK, chkdsk caught a minor problem with the MBR, but that was it. Windows still does not boot from sdb, when I select the drive at startup in the bios.

---

### Post by darkod on 2012-09-07
Try running repair again after the chkdsk. Auto or manual, your choice. The /fixboot was supposed to detect the new boot flag on sdb1. You did set it like we mentioned, right?
Not only to remove it from sda1, you need to set it ON on sdb1.

As oldfred says, copying bootmgr and boot/BCD from another machine can work. You will only need to do some modifications after since in your case windows is on the second disk, not as usually on the first one.

---

### Post by casbahdk on 2012-09-08
I have been on another [forum]("http://www.sevenforums.com/installation-setup/251460-dual-boot-win-7-ubuntu-12-04-borked.html"), trying to sort out the Windows 7 side of things. When I tried another round of "startup repair", I ran diskpart and made sure that partition "1" on disk "1" (sdb) was marked as active. However, I was not sure that marking the active partition lasted from session to session of rerunning "startup repair", so when I went in the second time to run startup recover, I ran diskpart again to make sure that the correct partition was marked as active. Now when I run startup recover, I get a message that repairs can not take place automatically, plus a dialog for sending a message to Microsoft. The detailed view only reveals a bunch of zeros in the different categories. Nothing is specified.

The general opinion on the Win forum appears to be that it will be a lot easier just to reinstall the entire Win system. If I do that, I have been advised that I will need to unplug /dev/sda to make sure that nothing happens to my Ubuntu 12.04 install, which is my main system. Will this work with Grub2 when I plug /dev/sdb in again? It sounds pretty logical. Will I just need to run an update-grub command?

---

### Post by oldfred on 2012-09-08
Yes, a sudo update-grub will find the new install once plugged back in.

I might keep Windows as the first drive since you install it as sda or first drive. Windows XP used hard coded drives & partitions like the older Ubuntu's used devices like /dev/sda1. But for whatever reason Windows still prefers to be first (and only ).

Be sure to backup any data that your want to save before reformating Windows drive.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

