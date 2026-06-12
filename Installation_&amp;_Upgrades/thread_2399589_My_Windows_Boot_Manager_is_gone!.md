---
title: "My Windows Boot Manager is gone!"
date: 2018-08-27
forum: Installation &amp; Upgrades
---

### Post by drpeppercan on 2018-08-27
Hi all!

I am setting up a dual boot system (Win10 & Ubuntu) in a 2 year old desktop pc.
I had Windows 10 reinstalled just a couple days ago. In my 1 Tb HD.
Then I installed Ubuntu in my 120 Gb SSD.
Then Grub was not found, so it would boot straight to Windows 10. Which I was expecting.
Then I disabled fast startup in Windows 10, I forgot to disable fast boot in UEFI settings. I can't do the latter now because WBM is not available to boot from.
Then I used bcdedit to set a new entry for Ubuntu: ```
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
``` (I can't recall where I got it from, but [here they have a very similar tutorial]("https://itsfoss.com/no-grub-windows-linux/")). I had used this trick before and it worked.
Then I rebooted, but instead of showing me Grub, it was a black screen with two lines of text: 

"Reboot and Select proper Boot Device or Insert Boot Media in selected device and press any key."

Then I went in the BIOS, and that's when I no longer saw Windows Boot Manager as an option!
I booted off from Boot Repair Disk, and supposedly fixed Grub, but I still can't see WBM, and even though I do see Ubuntu in Bios, it still yields the above line of text (Reboot and Select...). But BRD generated a report, [here it is]("http://paste.ubuntu.com/p/jC6jWhFGmD/")
Presently, and temporarily, I am only able to boot into Ubuntu or Windows 10 as long as I first boot off from a [rEFInd]("http://www.rodsbooks.com/refind/") Live USB drive. The rEFInd finds them both and allows me to choose.

Hopefully the BRD report can help you to see what's going on.
The way I see it, I need to either remake/repair the MBR for Win10, or have it in the right disk. Something along those lines, I guess.
I just don't know which should be the booting disk (sda1 ?). 

For now, I'll try to disable fast boot in UEFI settings of Win10. I don't know if it'll work because that requires to reboot with Shift, and hope that it'll be back. Like I said, at the moment I can only load either OS with the rEFInd Live USB.

Thanks in advance!

---

### Post by drpeppercan on 2018-08-27
It's all good now! :p
I just booted Win10 with Shift, then I went to Advd ops/Start-up Repair (Fix problems that keep Windows from loading). Strangely it said it was not successful. Then I went to UEFI Firmware Settings, but when I clicked that choice it only had a Restart button available. It brings you to the BIOS. But once there, in the Boot Options tab, there was nothing that would allow me to turn off/on Fast Boot. 
Windows Boot Manager was nowhere in sight still.
Then I restarted, and Grub showed up! Along with the Windows choices too. 
So I no longer need to boot from the rEFInd USB drive.

I want to ask for my next time, where should I tell Ubuntu to install the booting files? Assuming Windows has been installed already, and I'm installing Ubuntu on a separate drive.

Thanks guys!

---

### Post by oldfred on 2018-08-27
UEFI fast boot often is so fast you do not have time to press any key to get into UEFI or UEFI boot menu. It assumes no system change and jumps immediately to booting. Often a full cold boot/power down (remove laptop battery if laptop) & hold power switch to drain any left over power, then cold boot forces a full UEFI boot with scan for hardware and you have time to press key to get into UEFI or UEFI boot menu.

Boot-Repair shows this on lin e1193:
      >  Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.) 

    
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You are showing Ubuntu entry in UEFI. If you can get to UEFI boot menu does that boot?

Since you seem to have lost the Windows entry, you should be able to add it back:
       
 if ESP sdb1, you have to specify drive & partition with -d & -p options, check drive order first with
sudo parted -l
sudo efibootmgr -c  -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/sdb -p 1 

    
See also:
man efibootmgr

---

### Post by drpeppercan on 2018-08-31
I am back.
I was taking some time to fix rEFInd, with the help of Rod, the developer actually!

oldfred, here are the results of the commands you gave me:

```
sudo parted -l
[sudo] password for drpeppercan: 
Model: ATA Patriot Torch LE (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size   File system  Name  Flags
 1      1049kB  120GB  120GB  ext4




Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32        EF    boot, esp
 2      538MB   1000GB  1000GB  ntfs               msftdata

```

The other command line didn't give me anything: 
```
[COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/sdb -p 1[/COLOR]

```

---

### Post by oldfred on 2018-08-31
I like to have an ESP - efi system partition on every drive. 
In fact, I am using rEFInd to boot from an ESP I put on sdc as my UEFI has gone berserk. It now does not recognize either sda (normal default boot) nor sdb's ESP with grub boot loaders. 
But both sdc's ESP and an emergency flash drive with rEFInd both boot.

What does this now show?
sudo efibootmgr -v

Mine shows this now. The GUID of eb2.... shown & bootx64.efi are my sdc's ESP & rEFInd as bootx64.efi.
```
fred@bionic-z97:~$ sudo efibootmgr -v
[sudo] password for fred: 
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0004
Boot0003* UEFI OS    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(4,65535,0)/HD(1,GPT,eb2a429a-acce-4632-a75b-6c92d9a23af6,0x800,0xfa000)..BO
Boot0004* UEFI OS    HD(1,GPT,eb2a429a-acce-4632-a75b-6c92d9a23af6,0x800,0xfa000)/File(\EFI\BOOT\BOOTX64.EFI)..BO
```

---

### Post by drpeppercan on 2018-08-31
Are you telling me to have an ESP - efi system partition on every drive?
Do I do it with Gparted?

---

### Post by oldfred on 2018-08-31
Not a requirement, just a suggestion. 
Then each drive may be bootable on its own, or you can have another boot loader on that drive. I also have several larger USB drives with full installs of Ubuntu for emergency boot. And recently redid a smaller flash drive with rEFInd.

I always put both an ESP and a bios_grub (really only for BIOS boot) as first two partitions on every new or totally reformatted drive. I still add bios_grub as I started using gpt with my old BIOS system in 2010. Probably do not need it any more as I have not used a BIOS boot for ages.

---

### Post by drpeppercan on 2018-09-01
Ok. So I'll make the necessary partitions with Gparted. Then, do I copy the booting files I have to the new partitions?
Or there's a special way to make them?

---

### Post by oldfred on 2018-09-01
I just copy files. 
Ubuntu's grub does not let you directly install to a second drive unless you unplug first drive.
On my sdc, I just installed rEFInd as if external drive, so it is /EFI/Boot/bootx64.efi with the other refind files in that folder.

When I installed Fedora as a test to understand grub differences, it did let me directly install to sdb drive and booted from that drive without issue. I did not have to unplug sda.

---

### Post by drpeppercan on 2018-09-01
Ok. So having booting files and a copy of rEFIind along with them in each drive won't create a conflict?
I wonder how will that show once both loaders load.

---

### Post by oldfred on 2018-09-01
Depends on the UEFI.

Many UEFI autofind Windows and the fallback entries at /EFI/boot/bootx64.efi.  But none seem to find Ubuntu or other systems. So we use efibootmgr to add entries to UEFI.Grub's install does this.

Otherwise just having bootable files in an ESP, does not automatically add then to UEFI boot menu.
And if you physically disconnect a drive, UEFI forgets all entries from that drive.

---

### Post by drpeppercan on 2018-09-02
One last question before I attempt this.
So I suppose the boot files need to be in a separate partition with: FAT32, flags: boot, esp. 
Right?

---

### Post by oldfred on 2018-09-02
Each drive can have one ESP - efi system partition. 
When you add the boot flag/esp flags that converts a standard FAT32 to the ESP.
Some do have a second FAT32 and move boot flag to dual boot Windows or other systems.

My partitions just for reference, every user has unique partitioning requirements. My own optimal partitioning may change in a few years and has changed somewhat over the years. Note I still have some unallocated space also:
```

fred@bionic-z97:~$ sudo parted -l
[sudo] password for fred: 
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot, esp
 2      525MB   527MB   2097kB                           bios_grub
 3      527MB   26.7GB  26.2GB  ext4            trusty
 6      26.7GB  53.0GB  26.2GB  ext4            xenial
 7      53.0GB  83.8GB  30.8GB  ext4            bionic
 5      115GB   126GB   11.5GB  ext4            iso_ssd
 4      126GB   128GB   2000MB  linux-swap(v1)


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name      Flags
 1      1049kB  525MB   524MB   fat32           ESP_b     boot, esp
 2      525MB   527MB   2097kB                            bios_grub
 3      527MB   26.7GB  26.2GB  ext4            xenial_b
 4      26.7GB  446GB   419GB   ext4            data
 5      446GB   501GB   54.9GB  ext4            backup
10      501GB   527GB   26.2GB  ext4            bionicb
11      527GB   538GB   10.5GB  ntfs            test      msftdata
 8      538GB   565GB   27.3GB  ext4            debian
12      565GB   592GB   27.3GB  ext4            cosmic_b
 6      984GB   998GB   13.5GB  ext4            iso_hdd
 7      998GB   1000GB  2201MB  linux-swap(v1)


Model: ATA WDC WD6400AACS-0 (scsi)
Disk /dev/sdc: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  525MB   524MB   fat32        esp_c     boot, esp
 2      525MB   527MB   2097kB                         bios_grub
 3      527MB   27.8GB  27.3GB  ext4         rootc
 4      27.8GB  451GB   424GB   ext4         backup_c
 5      451GB   640GB   189GB   ext4         old_data
```

---

### Post by drpeppercan on 2018-09-02
I can see that you have a partition with both boot, and esp flags. But another partition with Grub. 
I thought that the same partition with both boot, and esp flags, would also host all the boot files, Grub files, and rEFInd files.

---

### Post by oldfred on 2018-09-02
My bios_grub partition is just for the old BIOS boot mode. I really do not need that anymore as I have not used BIOS to boot for ages.

The ESP only has the parts of grub needed to chainload/configfile into the /boot folder inside your actual install.

---

### Post by drpeppercan on 2018-09-02
Ok, I have booted off of the Ubuntu Live USB drive.
Like you, I have an HD and an SSD drive. I am trying to duplicate what I have on the HD, in the SSD too.
I don't have a booting partition in the SSD drive. So I opened Gparted, and I chose to resize the one partition I have by entering 500 Mb in the Free space preceding cell. 
But Gparted is warning me: ```
Moving a partition might cause your operating system to fail to boot. You have queued an operation to move the start sector of partition /dev/sda1.  Failure to boot is most likely to occur if you move the GNU/Linux partition containing /boot.
```
What do you think?

---

### Post by drpeppercan on 2018-09-02
Strange, I just noticed that there's two mounts, one for "efi", and another one for "filesystem" (with a boot folder). They are on my Ubuntu desktop.
I suppose the efi folder is the one in the fat32 boot/esp partition, right?

[IMG]http://pasteall.org/pic/show.php?id=6acb8c886f580a46276638829cc429aa[/IMG]

---

### Post by oldfred on 2018-09-02
Usually you do not see the ESP or is that from the other drive. 
I have to manually mount any ESP on another drive.
And my working install has the ESP mounted at /boot/efi/EFI/ubuntu. Even though a different partition it is mounted into /boot inside my / (root).

---

### Post by drpeppercan on 2018-09-03
What do you think about the previous post? ([#16]("https://ubuntuforums.org/showthread.php?t=2399589&p=13797369#post13797369"))

---

### Post by oldfred on 2018-09-03
I do not like moving the start of a partition. That normally requires the entire partition to be copied. And the smaller the change and larger the data, the more steps it has to go thru. And any interruption will totally corrupt partition. So be sure to have good backups.

That said, it normally works. And UUID should not change, so boot should still work. But always good to have an emergency boot drive for the current version of every system you have installed.  And know tools like rEFInd, Boot-Repair and Supergrub/Rescatus.

---

### Post by drpeppercan on 2018-09-03
And I suppose being a booting partition it can't be made after what's there already, right?

---

### Post by drpeppercan on 2018-09-03
Alright, the booting partition is done. I'm still in the Live USB drive.
Now, how do I access the booting files in the HD to copy them to the SDD?

---

### Post by oldfred on 2018-09-03
I have used Nautilus, command line cp.
If issues mounting you can use sudo, but should not just start Nautilus with sudo but with sudo -H.

Or install rEFInd from where ever you have it. I changed into the extracted rEFInd folder.
Installed to my 2GB flash drive labeled as ESP_2GB
sudo bash refind-install --usedefault /media/fred/ESP_2GB --alldrivers
or to my sdd1 ESP:
sudo bash refind-install --usedefault /dev/sdd1 --alldrivers

---

### Post by drpeppercan on 2018-09-03
While I was in Gparted I noticed that you can copy a partition. So I copied the booting partition from HD drive, and pasted it to the one in the SSD drive, and it worked! Now one of my choices in my tux4ubuntu loader is rEFInd. From there I choose Ubuntu, it boots faster than going straight from my tux4ubuntu loader.
Since I can load either OS, I wonder if I need WBM at all!

---

### Post by drpeppercan on 2018-09-04
I guess I do!
Today I can no longer load Win10. Not even from the USB installer! :(
So I guess I better fix WBM after all (some how).

It loads only enough to show its dots-going-around animation, but then it never goes past that. 
And that's whether I have called it from the rEFInd loader or from the Live USB Installer drive.

---

### Post by drpeppercan on 2018-09-22
To bring this to a closure...

I did find the way to get back my WBM.
By allowing a more advanced boot manager to take care of the booting job I was able to kill a few birds with the same stone. Among them, getting back my WBM. In the process I got a nicer looking booting manager. But most importantly a more capable one too = rEFInd.

**Install each OS separately (in their respective drives, while each is unplugged). **This way you keep from meddling with the GRUB, which won't be used/needed when booting anyway.

[FONT=arial][COLOR=#000000][COLOR=windowtext][COLOR=windowtext]The following steps/work-flow assumes you have one small SSD and one larger HD. (my case). But you can adapt the work-flow to your situation.
[/COLOR][/COLOR]
[/COLOR][/FONT][COLOR=#000000][FONT=Calibri]
[LIST=1]
[*][FONT=arial][COLOR=windowtext][COLOR=windowtext]Install Linux on SSD, while HD is unplugged.[/COLOR][/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext][COLOR=windowtext]Swap drives to install Win10 on the HD (as the later might need more space), while SSD is unplugged.[/COLOR][/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext][Install rEFInd]("onenote:Windows.one#Install%20rEFInd%20in%20Win10&section-id={7b2d2230-656a-479e-a388-1b81dbf03774}&page-id={08eeb6a8-e348-459b-886d-0d077f405d5f}&end")[COLOR=windowtext] in Windows 10.[/COLOR][/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext][COLOR=windowtext]Plug the SSD with Linux.[/COLOR][/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext][COLOR=windowtext]Boot up[/COLOR][/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext][COLOR=windowtext]If rEFInd doesn't show, go to the BIOS and swap the order of the drives.[/COLOR][/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext][COLOR=windowtext]Done![/COLOR][/COLOR][/FONT]
[/LIST]
[/FONT][/COLOR][FONT=arial]
[COLOR=#000000][B][COLOR=windowtext][COLOR=windowtext]
Install&#8239;[/COLOR][rEFInd]("https://sourceforge.net/projects/refind/")[COLOR=windowtext]&#8239;in Windows 10.
[/COLOR][/COLOR][/B]
[/COLOR][/FONT][COLOR=#000000][FONT=Calibri]
[LIST=1]
[*][FONT=arial][COLOR=windowtext]Get rEFInd.[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]Expand the ZIP file, and copy the resulting folder to C:[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]Open Command Prompt Admin[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]Enter this command line:&#8239;Mountvol S: /S[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]In the same terminal move two levels up to C:[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]Enter this command line:&#8239; 
xcopy /E refind-bin-0.11.3 S:\efi\refind\&#8239;(accommodate the version number to the one you got)[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]Go to the previouly mounted drive: S:[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]Enter this command line:&#8239; 
cd EFI\refind\refind[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]Enter this command line:&#8239; 
rename refind.conf-sample refind.conf[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]Enter this command line:&#8239; 
bcdedit /set {bootmgr} path \EFI\refind\refind\refind_x64.efi[/COLOR][/FONT]
[*][FONT=arial][COLOR=windowtext]Done![/COLOR][/FONT]
[/LIST]
[/FONT][/COLOR]

---

