---
title: "No Boot Loader?"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by jbdevega on 2014-07-19
I installed Ubuntu about two weeks ago but still have trouble booting it.  If i just let the computer run it comes to a black screen and says "no boot device found".  Ubuntu will still boot but i have to tell my computer to manually boot it.  when i ran bootrepair as far as i can tell (im not very tech savy) there is no boot loader in the VG partition.  I dunno if this is a result of me doing something wrong while installing Ubuntu or a hardware issue but any  help would be appriciated.

[[COLOR=#0072c6]http://paste.ubuntu.com/7753279/[/COLOR]]("http://paste.ubuntu.com/7753279/")

---

### Post by ajgreeny on 2014-07-19
It looks as if you may have a system with either one or other, or both, of LVM and raid array for the disks/partitions.

Both of those baffle me totally, so I offer this info in case it is helpful to you when searching further for possible answers.

---

### Post by oldfred on 2014-07-19
You also have it booting with UEFI.
So you need to be sure you set UEFI/BIOS to boot in UEFI mode and have secure boot off.

What model computer? 
Some want to only boot Windows and need the efi modified to make it think it boots Windows but really boots grub or shim.

---

### Post by jbdevega on 2014-07-19
its a HP Pavilion m6-1035dx
came from the Factory with 
Microsoft Windows 7 Home Premium 64-bit Edition 
6 GB RAM  
AMD A10-4600M 2.3 GHz processor
640 GB HDD 
AMD Radeon HD 7660G

When i look in the BIOs i dont see any option to boot it in UEFI mode or anything about secure boot.  I know when i have windows installed it will boot fine and when i tried dual booting it it would just automatically load windows.

---

### Post by oldfred on 2014-07-19
Most Windows 7 systems were installed in BIOS boot mode even if hardware was newer and would boot in UEFI mode. But some of the early UEFI implementations were not so good and UEFI/BIOS updates were required.

Best now to see all the details. Post link from Boot-Info report. Do not run auto fix.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jbdevega on 2014-07-19
encountered a rather new problem, this is what i get now when i try to run boot repair.  cant get past this because bootrepair just tells me grub is still installed.

Edit:

got past that then ended up with this.
[http://paste.ubuntu.com/7821837/]("http://paste.ubuntu.com/7821534/")

this also appears to have made Ubuntu more unstable...first time i tried a reboot, it loaded Ubuntu but the graphic interface was all scrambled...havent seen anything like that sense i ran windows XP.

---

### Post by oldfred on 2014-07-19
But you still should be able to run the report and then post the link it gives. I have run many reports without issue.

---

### Post by jbdevega on 2014-07-19
Could this be my problem?

"Or for those UEFI that only boot Windows, Boot_Repair backs up/renames Windows efi file to boot with.  [COLOR=#ff0000]Caution [/COLOR]-  if you have the "buggy" UEFI and run rename, undo rename before running  Windows updates or versions of bootmgfw.efi may get out of sync (backup  may be old and cannot be restored). Best to also backup efi partition  also:
Original Windows efi file bootmgfw.efi renamed bkpbootmgfw.efi.  UEFI  boots shim file renamed to be bootmgrw.efi, so code in UEFI thinks it  still boots Windows. but actually boots grub.
menuentry "Windows UEFI bkpbootmgfw.efi" {
With rename you cannot boot Windows directly from UEFI, but only the renamed file from grub menu."

---

### Post by oldfred on 2014-07-19
That is only an issue on how you Boot Windows or grub from your install.
You can always run Boot-Repair from the Ubuntu installer or download the Boot-Repair liveCD version.

But cannot tell if renamed or not without report. You should be able to look into your /efi/ folders and see if renamed.

 If renamed:Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

### Post by jbdevega on 2014-07-19
ok this is what i have when i manually look, i have /boot/efi/EFI/ubuntu
the following files are present:
grub.cfg 
grubx64.efi
MokManager.efi
shimx64.efi

---

### Post by oldfred on 2014-07-19
You did the LVM install of Ubuntu which is a full drive and with UEFI. 
Or you have totally erased Windows.
Is that what you wanted to do? 
Did you have a good backup of Windows?

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by jbdevega on 2014-07-20
I dont want to use Windows anymore because of all the problems it gave me so reformatted my HDD and installed Ubuntu.

---

### Post by oldfred on 2014-07-20
It could be that your HP has the modified UEFI that only boots Windows but also after it does not find Windows will boot another UEFI boot entry.

      ```
 BootOrder: 0001,0000
Boot0000* Notebook Hard Drive
Boot0001* ubuntu.


```    

Most with HP have to modify efi files so when it boots Windows or specify boot of hard drive actually boots grub directly.

Most systems have these if dual booting:
 /EFI/Boot
/EFI/Microsoft
/EFI/ubuntu


You only show the ubuntu folder.
I would create the /efi/Boot folder and copy grubx64.efi into that folder. Then rename it to bootx64.efi and change boot order to boot hard drive.

---

### Post by jbdevega on 2014-07-21
This may sound dumb but how do i create that folder?  I tryied to just left click and create a new folder but it wont let me in that file area.

---

### Post by oldfred on 2014-07-21
Since it is FAT32 I would not think there is a permissions issue.

How is it mounted, from Live installer?
Is it then in /media/EFI

If so from terminal, note case matters with Linux but not with FAT32 or NTFS, but anyway if efi use that.
cd /media/EFI
sudo mkdir Boot

fred@fred-Precise:~$ cd /media
fred@fred-Precise:/media$ ls
efi  floppy  floppy0  trustySSD
fred@fred-Precise:/media$ cd efi
fred@fred-Precise:/media/efi$ ls
fred@fred-Precise:/media/efi$ sudo mkdir Boot
[sudo] password for fred: 
fred@fred-Precise:/media/efi$ ls
Boot
fred@fred-Precise:/media/efi$

---

### Post by jbdevega on 2014-07-24
when i tried to do that it just told be "cd" didnt exist.  figured it could be cause i booted Ubuntu off a USB thumb drive so i tried to get it to run off that but no avail.  I may be going the wrong route about trying to fix this problem but i feel we are on the right path now.  also i cant seem to find any folder or drive called "media"

---

### Post by oldfred on 2014-07-24
Are you at a grub prompt, not a Ubuntu terminal?

 Get a terminal by <ctrl_+alt+F1> & back to gui with ctrl alt f7


[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by jbdevega on 2014-07-25
when i tried that it just told me all those directorys didnt exist.

---

### Post by oldfred on 2014-07-25
Type this in Ubuntu terminal:
ls

Copy & paste output of terminal here:

Did you leave the space after the command? Often better to copy commands, as you can copy & paste into terminal. That helps avoid typos. And even spaces can be a typo.

---

### Post by jbdevega on 2014-07-26
devega@devega-HP-Pavilion-m6-Notebook-PC:~$ ls
Boot     Documents  examples.desktop  Pictures  Templates   Videos
Desktop  Downloads  Music             Public    Ubuntu One
devega@devega-HP-Pavilion-m6-Notebook-PC:~$

EDIT:  also looked around the forum for any other help and one suggestion lead me to search for my boot manager, this is what i came up with.
devega@devega-HP-Pavilion-m6-Notebook-PC:~$ sudo efibootmgr -v
[sudo] password for devega: 
BootCurrent: 0001
BootOrder: 0000,0001
Boot0000* Notebook Hard Drive    BIOS(2,500,00)................-.%.......%.A.%........................................
Boot0001* Ubuntu    HD(1,800,100000,71acef52-1308-491a-9c18-a76ac3024a23)File(\EFI\ubuntu\grubx64.efi)RC

could my problem be with Boot0000 having no boot manager?  note that in bio it only gives me the option of booting from notebook harddrive and no where else does it state a harddrive.

---

### Post by oldfred on 2014-07-26
Your ls listing is of /home.

You should not need an entry for your hard drive, if you have a working Ubuntu entry. But the /efi/boot entry we are trying to create should be the hard drive entry.

From live installer mount the efi partition on hard drive:
       mount /dev/sda1 /mnt
cd /mnt/efi

us ls to see if created correctly
ls -l
mkdir Microsoft
mkdir Microsoft/Boot

      
 cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi

---

### Post by jbdevega on 2014-07-27
toke a little bit but i was able to make the folder and copy and rename the file but it didnt resolve the problem.

---

### Post by oldfred on 2014-07-27
For UEFI to recognize new efi partition entries may take a reboot or two. And then you have to select that entry in UEFI menu.

What does this show
       sudo efibootmgr -v

      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by jbdevega on 2014-07-27
devega@devega-HP-Pavilion-m6-Notebook-PC:~$ sudo efibootmgr -v
[sudo] password for devega: 
BootCurrent: 0001
BootOrder: 0000,0001
Boot0000* Notebook Hard Drive    BIOS(2,500,00)................-.%.......%.A.%........................................
Boot0001* Ubuntu    HD(1,800,100000,71acef52-1308-491a-9c18-a76ac3024a23)File(\EFI\ubuntu\grubx64.efi)RC

---

### Post by oldfred on 2014-07-27
It looks like it also need the /efi/boot folder with a file.

mount /dev/sda1 /mnt
cd /mnt/efi

us ls to see if created correctly
ls -l
mkdir Boot

 cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by jbdevega on 2014-07-29
I did that was able to successfully create the folder and copy and rename the file again.  but still no fix.  Still only seems to only recongnize the grub.

devega@devega-HP-Pavilion-m6-Notebook-PC:~$ sudo efibootmgr -v
[sudo] password for devega: 
BootCurrent: 0001
BootOrder: 0000,0001
Boot0000* Notebook Hard Drive    BIOS(2,500,00)................-.%.......%.A.%........................................
Boot0001* Ubuntu    HD(1,800,100000,71acef52-1308-491a-9c18-a76ac3024a23)File(\EFI\ubuntu\grubx64.efi)RC
devega@devega-HP-Pavilion-m6-Notebook-PC:~$

---

### Post by oldfred on 2014-07-29
Can you change boot order to make 1 first. Or is HP auto changing boot order?

       [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)


 You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu entry -- for instance, it might be Boot0005. You'd then type sudo efibootmgr -o 5 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2 to use 5, then 1 if that fails, then 2 if both 5 and 1 fail.)

so this may make entry 1 or Ubuntu as first.
efibootmgr -o 1,0



Some HP's only default to an UEFI entry with Windows in description.


  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\grubx64.efi"

---

### Post by jbdevega on 2014-07-30
Well i tried to change the boot order and it didnt work and just returned to default so i tried the windows boot manager and that didnt work either and it still defaulted back.
After doing all those changes this is what i get as an end result.

devega@devega-HP-Pavilion-m6-Notebook-PC:~$ sudo efibootmgr -v
[sudo] password for devega: 
BootCurrent: 0001
BootOrder: 0000,0001
Boot0000* Notebook Hard Drive    BIOS(2,500,00)................-.%.......%.A.%........................................
Boot0001* Ubuntu    HD(1,800,100000,71acef52-1308-491a-9c18-a76ac3024a23)File(\EFI\ubuntu\grubx64.efi)RC
devega@devega-HP-Pavilion-m6-Notebook-PC:~$

---

### Post by oldfred on 2014-07-30
Go back to post #21 and create the Microsoft folder in UEFI so it thinks it is booting Windows, but really boots grub.

---

### Post by jbdevega on 2014-07-31
I did that but the result is the same.

---

### Post by oldfred on 2014-07-31
Lets see an updated BootInfo report. Post link it gives.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jbdevega on 2014-08-02
[http://paste.ubuntu.com/7936175/](http://paste.ubuntu.com/7936175/)

---

### Post by oldfred on 2014-08-02
It looks like you booted Boot-Repair in BIOS mode so it may just not have shown the efi files in your efi partition. But you have to boot in UEFI mode not BIOS mode as system is configured with UEFI, gpt partitions and LVM, cannot tell if you encrypted it or not?

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)

---

### Post by jbdevega on 2014-08-04
[http://paste.ubuntu.com/7955760/](http://paste.ubuntu.com/7955760/)

This should be correct this time.

---

### Post by oldfred on 2014-08-04
It still is not showing files in efi partition, but I assume that is a script issue not that your files are missing.
And it is having issues mounting the LVM.

But it shows ubuntu in UEFI as a boot option and says it reinstalled grub correctly as Exit error code 0 is no errors. 

       efibootmgr -v
BootCurrent: 0001
BootOrder: 0001,0000
Boot0000* Notebook Hard Drive	BIOS(2,500,00)................-.%.......%.A.%........................................
Boot0001* ubuntu	HD(1,800,100000,71acef52-1308-491a-9c18-a76ac3024a23)File(EFIubuntushimx64.efi)

   
Reinstall the GRUB of mapper/ubuntu--vg-root into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

---

### Post by jbdevega on 2014-08-09
Well im almost the the point of giving up trying to fix this problem.  its not a deal breaker but would be nice it work correctly.

---

### Post by oldfred on 2014-08-10
You may need to create a folder and boot file with Windows file names, so system thinks it is booting Windows but really boots grub.

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

      
 HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

One user did this:

 > The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )

But if not also booting Windows you can rename bootmgfw.efi or rename both.

If Windows folder /efi/Microsoft/Boot does not exist recreate it.

---

### Post by jbdevega on 2014-08-12
I tried all that and still no luck.  they all show progress but it just seems like the computer isnt affected by any of the changes because its booting from drive 0000 while all the changes i make seem to appear from drive 0001 or 0002.

devega@devega-HP-Pavilion-m6-Notebook-PC:~$ sudo efibootmgr -v
[sudo] password for devega: 
BootCurrent: 0002
BootOrder: 0000,0001,0002
Boot0000* Notebook Hard Drive    BIOS(2,500,00)................-.%.......%.A.%........................................
Boot0001* Ubuntu    HD(1,800,100000,71acef52-1308-491a-9c18-a76ac3024a23)File(\EFI\ubuntu\grubx64.efi)RC
Boot0002* Windows Boot Manager    HD(1,800,100000,71acef52-1308-491a-9c18-a76ac3024a23)File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
devega@devega-HP-Pavilion-m6-Notebook-PC:~$

---

### Post by oldfred on 2014-08-12
Then do this one and if you do not have an /EFI/Boot folder create it.

The trick was to manually copy the ubuntu Boot directory in place of the  \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi  (not \EFI\Microsoft\Boot\bootmgfw.efi )

And post the contents of this:
/EFI/ubuntu/grub.cfg

---

### Post by jbdevega on 2014-08-14
ok i deleted all the files and started fresh by recopying the boot directory and this is the content of the grub.cfg:
search.fs_uuid 1b3f46d6-e01e-4f33-914f-790ce7c46db2 root hd0,gpt2 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

---

### Post by oldfred on 2014-08-14
That UUID is the UUID of sda2 per last Boot info report, so should be correct.

This user was able to recreate Windows folders and boot from those.
 Ubuntu only on HP, recreate Windows folder and grub as Windows boot file
[http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714)

Beyond that I do not know LVM well enough to know it all those references are correct or not. Generally look ok, but details can matter.

---

