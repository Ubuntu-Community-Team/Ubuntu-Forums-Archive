---
title: "vmlinuz has invalid signature"
date: 2019-03-03
forum: Installation &amp; Upgrades
---

### Post by VMC on 2019-03-03
I have two linux installed. Neither can boot the other, but I can boot each one separately. Here's what I get:

[B]/boot/vmlinuzxxxxx has invalid signature
you need to load kernel first[/B]

update-grub from either one's grub and it builds the other, but fails on restart with the above message.

Much googling I found several answers. One of which suggests the other kernel needs to be signed. [example: sudo mokutil --import MOK.der]
I have an original hard drive that I loaded ubuntu, deepin, lubuntu without issue.

Secure Boot enabled. 

```
From ubuntu booted:
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0002,0000,0003
Boot0000  Windows Boot Manager
Boot0001* ubuntu
Boot0002* Fedora
Boot0003  deepin

```
Strange because this hard drive never had Windows or deepin. The efi partition was freshly installed along with two ext4 partitions?!

---

### Post by oldfred on 2019-03-03
Try with Secure Boot off.
What brand/model system?

If not working then.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by VMC on 2019-03-04
I'd rather not have Secure Boot off. I did try with it though. Same result.

Acer TC-885-UR12

This gets stranger as times goes by. That hard drive above that contained Fedora. But it reappeared using 'efibootmgr' on the new hard drive?!. Acer BIOS has no mention of Fedora after the swap. [I removed the boot appearance using efibootmgr.] Not sure how it got there though.

Now with new hard drive I edited Ubuntu's grub.cfg to a very small file so I could keep tabs on who boots what. From Acer BIOS I made Deepin 1st boot order, after which I did update-grub from Deepin.
After that and on reboot [Deepin now in control] boots all three linuxes: Deepin, Ubuntu, Lubuntu just fine. BUT it used Ubuntu's grub.cfg file!!! The one I modified.

I'm new to **efi**. Used **mbr** since conception (around 1980). I don't particularly like boot-repair because all the fixes happen between closed doors and I just get a printout. I like to know what took place and in what order. 

I will fire up live and install the ppa version to see what's what adn how it works.

---

### Post by oldfred on 2019-03-04
If you know what you want to fix, often best not to run Boot-Repair auto-fix and then use its advanced options.
But you can run the report without running repairs.

With UEFI you should be using gpt.

All Acer have required UEFI updates, if an SSD firmware updates and the setting of "trust" from within UEFI.

       One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

### Post by VMC on 2019-03-04
```
Model: ATA ST1000DM010-2EP1 (scsi)Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: [COLOR=#ff0000]**gpt**[/COLOR]
Disk Flags: 


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  106MB   105MB   fat32           EFI system partition          boot, esp
 2      106MB   123MB   16.8MB                  Microsoft reserved partition  msftres
 3      123MB   108GB   108GB   ntfs            Basic data partition          msftdata
 4      108GB   527GB   419GB   ntfs            Basic data partition          msftdata
 6      527GB   632GB   105GB   ext4            ubuntu
 7      632GB   737GB   105GB   ext4            linux
 8      737GB   842GB   105GB   ext4            EXT4
 9      842GB   998GB   156GB   ext4
 5      998GB   1000GB  2131MB  linux-swap(v1)
```

Strange now both Deepin and Ubuntu boot each other, and dropping to grub prompt it complains when I do 'ls' that hd0, gpt6 [which is ubuntu partition] is not allowed because of Secure Boot. At least I know now its ubuntu in charge.   There's someother issues I have. Like what's inside efi partition, can zero it out and I re-create it, etc. Also both deepin, ubuntu have efi folders at /boot that refer to efi special nomenclature:
ubuntu /boot/efi/deepin:
```
search.fs_uuid cd9fbc32-1ab6-43bb-b3d6-16d22742bdcf root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

I originally thought the errors where in there.

At any rate, it now works but I'm less informed. It started working after I booted deepin from Acer bios, and did a update-grub. That's the confusing part. If sda belongs to ubuntu, why would deepin update matter.

I don't have an ssd as of yet. Your efi-tips is a big help, and that friendly assassin has good info. thanks. repair-boot soon.

---

### Post by oldfred on 2019-03-04
Each install puts boot files into the ESP - efi system partition (FAT32) in separate folders.

But Ubuntu and all its flavors and some based on Ubuntu only use /EFI/ubuntu. So I have multiple installs of Ubuntu and each overwrites the default /EFI/ubuntu folder. I have to reset it back to my main working install every time I do a test install. The configfile is just to start grub in the install in the partition referred to in the /EFI/ubuntu/grub.cfg (the 3 lines you posted). Some distributions embed the configfile and put more of the boot files normally in Ubuntu's /boot folder and have those boot files in the ESP.

Which grub is in charge will depend on which you use or set as default in UEFI. UEFI's ESP is somewhat like having multiple MBRs all one one drive. So you can choose from UEFI what system to boot.

I do not think it is Secure Boot that prevents you seeing your Ubuntu partition from Deepin. Do not know Deeping, but issue is often ownership (same user name or id as 1000) or permissions.

---

### Post by VMC on 2019-03-04
[Boot-Repair-URL]("http://paste.ubuntu.com/p/QY27PSRwbm/")

From boot-repair text. This looks okay.
```
sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/Boot/bootx64.efi 
                       /EFI/Boot/bootx64.efi-1551554222.bak 
                       /EFI/Boot/fbx64.efi /EFI/Boot/grubx64.efi 
                       /EFI/Boot/mmx64.efi /EFI/deepin/fbx64.efi 
                       /EFI/deepin/grubx64.efi /EFI/deepin/mmx64.efi 
                       /EFI/deepin/shimx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/OEM/Boot/bootmgfw.efi /EFI/OEM/Boot/bootmgr.efi 
                       /EFI/OEM/Boot/memtest.efi
```

sda2 is a ntfs spare fs. Unsure what the complaint is.:
```
Mounting failed:   mount: /mnt/BootInfo/sda2: unknown filesystem type ''.
```


I recall reading about you using 'configfile' on your grub.cfg.

---

### Post by oldfred on 2019-03-04
Microsoft requires the System Reserved partition. It is potentially for serial numbers or other data that it used to put into the sectors after the MBR. But gpt does not have those sectors. Grub does the same for BIOS boot as with MBR, it had core.img in the sectors after the MBR, but with gpt and BIOS boot has to have a bios_grub partition.
Since both System Reserved & bios_grub are unformatted partition or whatever Boot-Repair is using throws an error, but partition has valid gpt GUID, so it should not as being unformatted is a requirement.

---

### Post by VMC on 2019-03-04
Interesting that 'boot-repair' puts its info on each partition @ /boot/efi.

Also I don't see any errors, but what about these messages. 
> =================== Default settings of Boot RepairThe default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda6, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file  




=================== Advice in case of suggested repair
Please disable SecureBoot in the BIOS. Then try again.Do you want to continue?




=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!

Or is it just assuming, that if you use 'boot-repair' somethings wrong. How do I make BIOS boot on sda1/efi , on the last message?

---

### Post by VMC on 2019-03-04
Does this message preferred:


**grub-install --efi-directory=/boot/efi**


over this:


[B]sudo grub-install --recheck --root-directory=/ /dev/sda

[/B]The latter what I have used on efi installed oss's

---

### Post by oldfred on 2019-03-04
The grub-install command has many options and defaults. see
man grub-install

Some for install to another device, some to same device, so boot mode known.
Generally install is in same mode as boot, but then grub can be forced to install UEFI or BIOS (I think).
I have only reinstalled in UEFI boot mode for last 5 years.

From report or this command
```
sudo efibootmgr -v
        BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0003,0001,0000,0004
Boot0000* Windows Boot Manager	HD(1,GPT,9d11c193-4aad-450b-83be-249ba57ed87d,0x800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu	HD(1,GPT,9d11c193-4aad-450b-83be-249ba57ed87d,0x800,0x32000)/File(EFIubuntushimx64.efi)
Boot0003* deepin	HD(1,GPT,9d11c193-4aad-450b-83be-249ba57ed87d,0x800,0x32000)/File(EFIdeepinshimx64.efi)
Boot0004* UEFI: SanDisk U3 Cruzer Micro 4.05	PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/CDROM(1,0x3aabe8,0x4d00)..BO 


```

UEFI will not show details, so you just see ubuntu or deepin.  When Secure Boot is off, you get two Ubuntu entries, one shimx64.efi and one grubx64.efi. Since shim works with Secure boot off also, not sure why grubx64.efi is still used.

---

### Post by VMC on 2019-03-05
Thanks Fred! I booted live disk and checked all the OS's and their efi folders are empty. It's efi partition where all the info is. I was very confused when booted to a OS and check its /boot/efi folder. Now I'm starting to understand much more. Lots of blogs to read. [COLOR=#242729][FONT=Consolas]rEFInd[/FONT][/COLOR] is and interesting alternative.

I'm having a bit of an odd experience with lubuntu 19.04. It doesn't build grug.cfg or install a loader. It doesn't complain about the efi partition and its flags.

---

### Post by oldfred on 2019-03-05
The ESP which has /EFI/ubuntu or other /EFI/grub is mounted by fstab at /boot/efi. So when booted you can see an /boot/efi in your system. But then if you look at other systems they do not have a /boot/efi, just an empty mount point. Files are actually in /EFI in ESP.

Every Ubuntu I install, overwrites my main working install /EFI/ubuntu. Have not yet had issues with any of all the files being newer versions and still reset to boot my main working install. The file I replace or edit back to boot main install is the /EFI/ubuntu/grub.cfg, which you posted in post #5. I just edit UUID & partition info.

---

### Post by VMC on 2019-03-05
> **oldfred said:**
> The ESP which has /EFI/ubuntu or other /EFI/grub is mounted by fstab at /boot/efi. So when booted you can see an /boot/efi in your system. But then if you look at other systems they do not have a /boot/efi, just an empty mount point. Files are actually in /EFI in ESP.

Every Ubuntu I install, overwrites my main working install /EFI/ubuntu. Have not yet had issues with any of all the files being newer versions and still reset to boot my main working install. The file I replace or edit back to boot main install is the /EFI/ubuntu/grub.cfg, which you posted in post #5. I just edit UUID & partition info.
".. issues with any of all the files being newer versions and still reset to boot my main working install"
Not sure what you mean here.

"I just edit UUID & partition info"
Good point. With mbr and had a script I used that found and edit my grub.cfg. Once I'm sure of myself will probally do the same for efi.

---

### Post by oldfred on 2019-03-05
I have been a bit concerned that I always keep my main working install 18.04, which may have an older version of grub.
But I test install every new version in another partition and it fully updates all the files in the ESP with the latest grub. Since I do not restore entire ESP, but just edit the grub.cfg in the ESP, I do not know if grub in ESP and grub in my install may have conflicts. 

But I guess that the grub in the ESP does the booting and the grub in my install has the configuration settings and menu.
Grub is both a boot loader (all from ESP?) and a boot manager (menu) from grub.cfg in the install.

---

### Post by VMC on 2019-03-05
At the time I'was aware of ESP grub, but when I edit ubuntu's /boot/grub/grub.cfg it did change.

---

### Post by oldfred on 2019-03-05
You should not edit /boot/grub/grub.cfg, but can edit /EFI/ubuntu/grub.cfg.

The grub in /boot/grub is recreated with every update to grub either new kernel or actual grub software update.
It uses setting in /etc/default/gruband scripts in /etc/grub.d.

---

### Post by VMC on 2019-03-06
I'm running ubuntu right now and the mount:
/dev/sda1 on /boot/efi type vfat

Accessing that device, here's what there:
```
$ sudo ls /boot/efi
boot-repair  EFI
$ sudo ls /boot/efi/EFI
Boot  deepin  Microsoft  OEM  ubuntu
$ sudo ls /boot/efi/EFI/ubuntu
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi
$ sudo cat [B]/boot/efi/EFI/ubuntu/grub.cfg
[/B]
[FONT=courier new]search.fs_uuid ee394ebe-47a2-4012-91bd-734e0caa01aa root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg[/FONT]
```

As you can see, its a different type of grub. Its using that configfile convention. Is that what your editing?

---

### Post by oldfred on 2019-03-06
Yes that is a grub I do edit. It is created by the installer, not sure when it might get updated as an install it should not change.
But every version and flavor of Ubuntu installs to the same location. And I want to normally boot my main working install and use its grub, not some temporarily grub that may be deleted shortly. 

My current edited grub, I have a test install of disco on sdb8, and often reinstall to that partition, 18.04 is in sda4:
```
fred@Bionic-Z170N:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
#search.fs_uuid 7a5bc8f2-30cd-46b2-8756-7d248a09a883 root hd1,gpt8 
search.fs_uuid c29fc361-ea05-420b-b919-850aeef65dd4 root hd0,gpt4 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

---

### Post by VMC on 2019-03-07
I'm unsure how you edit that grub, since it only has a reference to configfile.

Another thing, no matter who I install, when I drop to grub prompt, 'ls' isn't allowed anymore. The one thing it does show is the partition that grub is installed to.

---

### Post by oldfred on 2019-03-07
The grub terminal only has a few limited commands related to booting, it is not the full bash terminal that you get once you have fully booted.

The configfile should be a reference to the partition and grub with the install your want to boot from as default.

---

