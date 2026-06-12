---
title: "Ubuntu 16.10 no such device, grub rescue"
date: 2017-03-27
forum: Installation &amp; Upgrades
---

### Post by brutikk on 2017-03-27
I've looked at a few threads but have not been able to fix my issue yet.  The most common solution I've seen involves using boot-repair-disk, which hasn't been successful for me yet (pasted below).

During a previous attempt at installing Ubuntu 16.10, I received the message ```
[COLOR=#111111][FONT=Consolas]grub-efi-amd64-signed failed installation /target/[/FONT][/COLOR]
```.  After retrying the installation, I noticed an error message which said that I was trying to install in UEFI mode.  I opted not to do it this time, and the above error went away.  However, after trying to boot, I enter the grub rescue screen, with the message:

```
error: no such device: b8b6b11d-0755-...

Entering rescue mode...
grub rescue>
```

Some threads I've seen give instructions for what to do here, but I haven't been able to apply their instructions.  When I type ls at this console, I see:

```
(hd0) (hd0,msdos1) (hd1) (hd1,msdos4) (hd1,msdos3) (hd1,msdos2) (hd1,msdos1)
```

Ubuntu was installed on /dev/sda4, and the location to install the bootloader was set to /dev/sda.

Here are my boot-repair-disk results: [paste.ubuntu.com/24262472](paste.ubuntu.com/24262472)

---

### Post by egeezer on 2017-03-27
If you type grub rescue > ls (hd1, msdos4), I'll bet you see it formatted as ext2, which indicates it is your Linux partition.  Knowing that, you can follow the rest of the instructions you found.

---

### Post by brutikk on 2017-03-27
To be clear, you mean this should work?

> 
[COLOR=#000000]*1. set prefix=(hdX,Y)/boot/grub*[/COLOR]
[COLOR=#000000]*Use the values determined earlier. Example: If the Ubuntu system is on sda5, enter: set prefix=(hd0,5)/boot/grub*[/COLOR]
[COLOR=#000000]*2.* set root=(hdX,Y)*[/COLOR]
[COLOR=#000000]*Example: set root=(hd0,5)*[/COLOR]
[COLOR=#000000]*3. insmod normal*[/COLOR]
[COLOR=#000000]*Attempt to load the normal module.*[/COLOR]
[COLOR=#000000]*4. normal*[/COLOR]
[COLOR=#000000]*Activate the normal module. If successful, the GRUB 2 menu may appear.*[/COLOR]
[COLOR=#000000]*5. set*[/COLOR]
[COLOR=#000000]*(Optional) Review the current settings.*[/COLOR]
[COLOR=#000000]*6. ls /boot*[/COLOR]
[COLOR=#000000]*(Optional) Check for a vmlinuz and a initrd.img entry.*[/COLOR]
[COLOR=#000000]*7. insmod linux*[/COLOR]
[COLOR=#000000]*An error message usually means the path is incorrect.*[/COLOR]
[COLOR=#000000]*8.* linux /vmlinuz root=/dev/sdXY ro*[/COLOR]
[COLOR=#000000]*Selects the latest kernel. Example: linux /vmlinuz root=/dev/sda5 ro*[/COLOR]
[COLOR=#000000]*9. initrd /initrd.img*[/COLOR]
[COLOR=#000000]*Selects the latest initrd image.*[/COLOR]
[COLOR=#000000]*10. boot*[/COLOR]

source: [https://ubuntuforums.org/showthread.php?t=1854142](https://ubuntuforums.org/showthread.php?t=1854142)

edit: insmod normal results in saying the normal.mod is not found

---

### Post by oldfred on 2017-03-27
You Summary report shows issues with sda4.
And then Boot-Repair's only option was to install syslinux or a Windows type boot loader to MBR.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda4 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda4
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda4 

If then you can mount/see sda4, use Boot-Repair to install grub to MBR.

---

### Post by brutikk on 2017-03-27
Here are the results of the commands you asked me to run: [https://pastebin.com/SM2fMXHr](https://pastebin.com/SM2fMXHr)

And here is the script after I install boot-repair on the flash ubuntu and ran it: [http://paste2.org/H4fnYxCC](http://paste2.org/H4fnYxCC)

No luck still

---

### Post by oldfred on 2017-03-27
It now sees your Linux partition and installed grub.
But this time you ran Boot-Repair in UEFI mode. 
Your Windows is installed in the 35 year old BIOS boot mode on MBR partitioned drive.
System is a newer UEFI system.

Make sure Secure boot is off in UEFI.
Some systems call Secure boot "Windows" or "Other" but Windows 7 has to use "Other" as it does not support Secure Boot.
Should have CSM/Legacy/BIOS boot mode on, which you only can use if Secure boot is off.

You show nVidia, have you tried nomodeset.
Do you now get grub menu?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by brutikk on 2017-03-28
I followed the instructions here: [http://askubuntu.com/questions/207663/cannot-update-grub-with-parameters-on-live-usb](http://askubuntu.com/questions/207663/cannot-update-grub-with-parameters-on-live-usb) along with the instructions you gave me to properly set nomodeset.  I still enter the grub rescue screen.

Edit:

And I am booting with the Legacy option.

---

### Post by oldfred on 2017-03-29
You should only need nomodeset on first boot or any boot before you install the proprietary drivers from Ubuntu's repository.
Best not to permanently set it.

But you may need to do a full un-install & reinstall of grub from Boot-Repair's advanced mode.
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by brutikk on 2017-03-29
Understood, I will remove that parameter later.  I cannot boot into boot-repair unless it is in UEFI mode.  When I try, I just go to the grub rescue prompt again.

When I am in the boot-repair disk, I am prompted to restore the MBR, and the GRUB related tabs are inaccessible.

---

### Post by oldfred on 2017-03-29
Do you then have Secure Boot on? That turns off BIOS boot mode.
Or you may have other settings in UEFI, Boot or secuity screens to allow USB boot in BIOS mode.
And then UEFI should show two boot options for flash drive, one UEFI:flash and the other just flash (and then is the BIOS boot) where flash is name, label or something that is flash drive.

---

### Post by brutikk on 2017-03-29
Correct, I can see one that is the name/label without the UEFI mode.  Under that option is the same thing, but with UEFI mode.  When I try to boot into the non-UEFI, I go to grub rescue.

---

### Post by oldfred on 2017-03-29
But UEFI boots ok?
You should not get grub rescue, but a black screen and install options.
Do you get two tiny icons at bottom of screen as soon as you boot flash drive in BIOS mode. And press any key while they show. You then can add boot parameters like nomodeset.

---

### Post by brutikk on 2017-03-29
I just tried with a boot-repair-disk CD (non UEFI) and I still only have the option to restore MBR, with the GRUB tabs inaccessible.
I do not get two tiny icons at the bottom of the screen when I boot the flash drive in BIOS mode; it goes straight to GRUB rescue.  Are there any diagnostic commands I can run at this point that would help you?

edit:

Yes, UEFI works OK

---

### Post by oldfred on 2017-03-29
In BIOS boot with installer grub is not directly involved. You do not get grub menu & it uses syslinux to boot.
Only UEFI boot uses grub as menu & boot loader.
If then getting grub errors, is it not seeing installer correctly and defaulting to install on hard drive which does not work?

Did you verify that download was correct for the ISO?

---

### Post by brutikk on 2017-03-29
> **oldfred said:**
> In BIOS boot with installer grub is not directly involved. You do not get grub menu & it uses syslinux to boot.
Only UEFI boot uses grub as menu & boot loader.
Does that mean I should use MBR if my BIOS is legacy?

> If then getting grub errors, is it not seeing installer correctly and defaulting to install on hard drive which does not work?
I'm not sure what you mean here or what I should do to give you the right information.

> Did you verify that download was correct for the ISO?

The download for the ISO was correct.  I installed it onto a USB using Rufus, choosing the GPT for UEFI partition scheme.  I've also tried the MBR for Legacy setting (before I posted).

---

### Post by oldfred on 2017-03-30
If not installing Windows and you want BIOS boot, you still can use gpt partitioning but must have a bios_grub partition (1 or 2MB unformatted) for grub to install correctly to the gpt's protective MBR.
Windows only boots in UEFI boot mode from gpt partitioned drives, so then better to have Ubuntu in UEFI boot mode.

---

### Post by brutikk on 2017-03-30
I am not installing Windows, but I want to keep my windows partition and I want to be able to boot into it.  So, should I reinstall Ubuntu and create a bios_grub partition?  Or, should I use the MBR partition (not sure if I even have one, but there's a small partition that exists for reasons I don't know)?

---

### Post by oldfred on 2017-03-30
There is no MBR partition. The MBR in BIOS boot is just the first sector of a hard drive. You do not see it in partitioning tools.

How you boot install media, UEFI or BIOS is then how it installs, you you want to boot in BIOS mode.

Since Windows is BIOS, you should not even be dealing with UEFI and gpt partitioning. Windows in BIOS mode cannot boot from gpt, but must use the 35 year old MBR(msdos) partitioning.

Do not attempt to install Ubuntu in UEFI mode as that will convert drive to gpt and prevent Windows from working.

If able to boot Ubuntu installer in UEFI mode you must have newer hardware, but Windows installed in the old BIOS/MBR configuration. You could only convert Windows to UEFI by reinstalling. And it works like Ubuntu in that how you boot install media is then how it installs.

IF you have not already done full backup of Windows or at least your data, if you have Windows installer do it now.

---

### Post by brutikk on 2017-03-30
I do not have a Windows installer.

My partitions are as follows:

```
/dev/sda ATA ST31000524AS (1.0 TB)
/dev/sda1 ntfs 104MB 29MB used Windows 7 (loader)
/dev/sda2 ntfs 912682 unknown used Windows 7 (loader)
/dev/sda4 ext4 / 79224MB Ubuntu
/dev/sda3 swap 8191MB unknown used
```

```
/dev/sdb  ATA SAMSUNG HD 103SI (1.0TB)
/dev/sdb1 ntfs 1000202MB unknown used Windows 10 (loader)
```

I believe the /dev/sdb is an old external hard drive that I installed internally.  Why is the Windows 10 loader there?  Note that I previously had Windows 7 installer, and upgraded to 10 from Windows 7.

When using boot-repair-disk, should "partition booted by the MBR" be sda4, ubuntu?

Edit:

That is what I've tried, [http://paste.ubuntu.com/24282256/](http://paste.ubuntu.com/24282256/)  I still go to grub rescue

---

### Post by oldfred on 2017-03-30
You have BIOS/MBR.
And then unless you have Windows installer need to stay with BIOS to be able to boot Windows.

It shows error on ext4 partition.
It looks like you did not run the e2fsck from post #4??

---

### Post by brutikk on 2017-03-30
I did run it previously, but did not run it after my most recent installation attempt.  Here are the results from me just running it: [https://pastebin.com/C0UqjV1k](https://pastebin.com/C0UqjV1k)

To confirm, I should now run boot-repair to restore the MBR on /dev/sda and set the partition booted by the MBR to be /dev/sda4?

---

### Post by oldfred on 2017-03-30
Boot-Repair has to "see" the ext4 partition sda4. If it cannot see it due to too much corruption then install of bootloader will fail.

---

### Post by brutikk on 2017-03-30
I ran the e2fsck commands, I thought that would make boot-repair see sda4?  If I am booted into the boot-repair disk, how can I check that it can "see" the ext4 partition?

I am wondering about the options "Restore the MBR of: sda (generic mbr)".  Should I change that to something else?  Also the option "Partition booted by the MBR: sda2 (Windows 7)" seems wrong, shouldnt it be "sda4 (Ubuntu 16.10)"?

---

### Post by oldfred on 2017-03-30
If Boot-Repair cannot see the ext4 partition with boot files inside it, it then only offers to install the Windows boot loader. It uses a generic Windows type boot loader - syslinux which works. 

From live installer can you mount, or even click on sda4 and see files or still an error message?

---

### Post by brutikk on 2017-03-30
I can successfully mount /dev/sda4 from an ubuntu live flash drive.

---

### Post by oldfred on 2017-03-31
Then Boot-Repair should be able to see you have an Ubuntu install and offer to install the grub2 boot loader.
If that does not work, but it still sees Linux, you can use advanced mode and a full un-install/reinstall of grub2 which resets all of grub.
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by brutikk on 2017-03-31
Boot-Repair does not have the option to install GRUB.  It can only restore MBR.

---

### Post by oldfred on 2017-03-31
Default option is just reinstall of grub to MBR.
Advanced options let you choose which operating system it sees, and which drive to install operating system into.Always choose drives with MBR, never partitions.
And advanced options have  the total erase of grub and reinstall of grub.
But again it has to see your ext4 partition with Ubuntu installed.

---

### Post by brutikk on 2017-03-31
I cannot do that, because the GRUB location and GRUB options menus are both grayed out (inaccessible).  I ONLY have MBR options under the advanced tab.

I know I can mount /dev/sda4 on an ubuntu flash drive, but does that mean that boot-repair can see it?

---

### Post by oldfred on 2017-03-31
It should.
But does full Summary Report from Boot-Repair show issues?

You can try to manually reinstall grub.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]
 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda4 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda4 if not correct:
sudo fdisk -l
#confirm that linux is sda4
sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub 

[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by brutikk on 2017-03-31
Indeed it does show errors: [http://paste.ubuntu.com/24289938/](http://paste.ubuntu.com/24289938/)

> 
sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs [COLOR=#AA22FF]type[/COLOR], bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by oldfred on 2017-03-31
If you can manually mount and see your data and do not have backups, now is the time to copy all of it.

Does hard drive show it is ok? 
In Disks click on icon in upper right corner and check Smart Status. 
It can run lots of tests on a drive, but all I know is good or bad.

If fsck has errors, you can try some advanced options.
Your original Boot-Repair summary report had this.
Are you running repairs from 16.04? Or the now old Boot-Repair live ISO system?
Best to use current version of Ubuntu and add Boot-Repair to that.

       f drive issues
sudo badblocks -wsv /dev/sdXY
sudo badblocks -v /dev/sda4

      
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda4 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda4
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by brutikk on 2017-03-31
Here is the summary from using boot-repair within an ubuntu live disk: [http://paste2.org/3w0gdYwI](http://paste2.org/3w0gdYwI)

It seems only the syslinux install had errors.

edit:

I can boot into windows, but havent confirmed that I can boot into ubuntu.  I think my ubuntu installation might be on my removable hard drive, because it looks like win10 is on /dev/sdb, but win10 is supposed to be on my internal drive...

---

### Post by oldfred on 2017-04-01
Report says this:
ata-ST31000524AS_5VPB6V2F -> ../../sda
ata-SAMSUNG_HD103SI_S1Y5J90S431617 -> ../../sdb

An sdb has one large NTFS partition.

Syslinux is only on your flash drive installer. Sometimes it shows issues that are not issues.

---

