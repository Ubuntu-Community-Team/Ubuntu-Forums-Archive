---
title: "Ubuntu 9.10 install not detecting win7 OS"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by pmeves on 2010-03-01
My first problem was not detecting any partitions created by Windows 7. Now that I can see the partitions, the installation cannot detect win7 installed on my system.

Here is the RESULTS.txt i got with [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03be1519

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048       411,647       409,600 System/Boot Partition
/dev/sda2         411,648       673,791       262,144 Microsoft Windows
/dev/sda3         673,792   922,273,791   921,600,000 Linux or Data
/dev/sda4     922,273,792   976,773,119    54,499,328 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        72C3-7D06                              vfat                                     
/dev/sda3        F674C26A74C22D65                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda3        /media/F674C26A74C22D65  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr1         /media/20071017_131019   iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
```

I have troubles with an option in Bios, which give me the choice of booting only legacy OS or trying EFI boot first.

After the last time i booted ubuntu with live cd, i needed to change this option to boot legacy only, because it tried EFI and went directly to win7 without booting the cd -_- 

EFI must be related with the first partition i have ( dev/sda1 ). Then, when i only tried to boot win7, without the EFI option enabled, Windows don't boot! the system just stays blank...

I tried to install linux that way but with Grub it was a big confusion and i couldn't add an entry for win7.

I have a Clevo w860cu. Bios is sager last version.

---

### Post by darkod on 2010-03-01
I have no experience with GPT but here is an idea. Set BIOS to legacy boot, not EFI.
Boot with the ubuntu cd and start the installer. In step 4 select Manual partitioning and see which partitions it is showing in the list. Do not proceed with the install, just look what it says.

Because the results file is confusing too. sda3 and sda4 are reported as Linux partitions but on the other hand it says sda3 has the windows boot file winload.exe. And sda2 is too small to be a full win7 install, it looks barely 250MB.

---

### Post by pmeves on 2010-03-01
> **darkod said:**
> I have no experience with GPT but here is an idea. Set BIOS to legacy boot, not EFI.
Boot with the ubuntu cd and start the installer. In step 4 select Manual partitioning and see which partitions it is showing in the list. Do not proceed with the install, just look what it says.

Because the results file is confusing too. sda3 and sda4 are reported as Linux partitions but on the other hand it says sda3 has the windows boot file winload.exe. And sda2 is too small to be a full win7 install, it looks barely 250MB.

sda2 has information about microsoft, it's a MSR partition, but in the same time, that partition should be the one with windows. So it's like, ok i have your windows OS installed on sda2 but the files are located in sda3 lol

I did so much times what you're asking me but i cannot remember clearly for each partitions which are the properties.

I'll post exactly what there is.

---

### Post by pmeves on 2010-03-01
[IMG]http://img38.imageshack.us/img38/53/screenshotpq.png[/IMG]

[IMG]http://img715.imageshack.us/img715/502/screenshot1jj.png[/IMG]

---

### Post by darkod on 2010-03-01
I have no idea, sorry. I hope a GPT expert will jump in, it looks like that's the issue. sda2 and sda4 filesystems are not even recognized. :(

---

### Post by pmeves on 2010-03-01
> **darkod said:**
> I have no idea, sorry. I hope a GPT expert will jump in, it looks like that's the issue. sda2 and sda4 filesystems are not even recognized. :(

Thanks darkod ;)

---

### Post by oldfred on 2010-03-01
Not all linux tools are GPT aware, some may call GPT partitions as FAT partitions.

I have read just enough on GPT to be dangerous. As I understand it GPT has a MBR and for booting requires a GPT boot partition. Grub2 will install part to the MBR and part to the boot partition. I bet that your windows7 boot files that are missing were in the boot partition and grub2 over wrote them.

---

### Post by darkod on 2010-03-01
> **oldfred said:**
> Not all linux tools are GPT aware, some may call GPT partitions as FAT partitions.

I have read just enough on GPT to be dangerous. As I understand it GPT has a MBR and for booting requires a GPT boot partition. Grub2 will install part to the MBR and part to the boot partition. I bet that your windows7 boot files that are missing were in the boot partition and grub2 over wrote them.

Unless they are actually still on /dev/sda2 but since it's not recognized by ubuntu it can't see them. That small 120MB partition looks like a boot partition.
Strangely enough, wikipedia says grub2 supports GPT.

---

### Post by oldfred on 2010-03-01
Since win7 is supposed to be GPT aware, I would try to repair with the win7 CD/DVD. I believe that with the efi boot it jumps straight to the boot partition to boot. I do not know if grub2 will boot that way or has to have the legacy boot with part in MBR and part in boot partition.

I would try to repair with legacy boot set so windows may install its fixes to the win partition. That may not work as in MBR the boot flag must be set but there does not seem to be a boot flag in GPT.

The apple forum here has a lot more info on GPT as that is their standard. GPT is also used in the server versions of new windows. If the repair does not work you could try posting in the other forums here but with GPT in your title.

---

### Post by pmeves on 2010-03-02
> **oldfred said:**
> Since win7 is supposed to be GPT aware, I would try to repair with the win7 CD/DVD. I believe that with the efi boot it jumps straight to the boot partition to boot. I do not know if grub2 will boot that way or has to have the legacy boot with part in MBR and part in boot partition.

I would try to repair with legacy boot set so windows may install its fixes to the win partition. That may not work as in MBR the boot flag must be set but there does not seem to be a boot flag in GPT.

The apple forum here has a lot more info on GPT as that is their standard. GPT is also used in the server versions of new windows. If the repair does not work you could try posting in the other forums here but with GPT in your title.

I did not install grub/ubuntu yet, because I know what will happen. The last time I did what you are saying, windows boot files gone missing, tried a lot of different methods to repair windows boot and none worked.

What i think is that windows is installed with information about EFI, so the boot is in the EFI partition, and ubuntu will look at the windows 7 partition and cannot find boot files (and that's why i cannot boot windows only with legacy boot). So i should install Windows with legacy mode only, but from my experiences, when i do that, the partitions created with windows won't be found at all by ubuntu, but it's the only way,and i'm really tired of always format everything- reinstall everything.

i should ask the seller about it. they say they can help with OS instalations, but i just can't give my pc to them now, i need it for work... I will contact them and see what they think about it.

---

### Post by pmeves on 2010-03-02
"Some EFI platforms support both UEFI and BIOS firmware. On some of those systems, it is not always clear if the default DVD boot option is an EFI or BIOS boot option. On these systems, using the EFI shell command may be required. If you do not specifically start Windows Setup by using the EFI boot entry, the default firmware boot entry for BIOS may be used. If Windows Setup starts in BIOS mode on a combined EFI/BIOS system, the ESP and MSR partitions are not created. After Windows Setup completes, use the Diskpart command to verify that the ESP and MSR partitions were created."

from [http://technet.microsoft.com/en-us/library/dd744321%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744321%28WS.10%29.aspx)

---

### Post by amsoares on 2010-03-05
Can you verify if the workaround i found works for you ?
 
[http://ubuntuforums.org/showthread.php?t=1414179&page=6](http://ubuntuforums.org/showthread.php?t=1414179&page=6)

---

### Post by pmeves on 2010-03-11
> **amsoares said:**
> Can you verify if the workaround i found works for you ?
 
[http://ubuntuforums.org/showthread.php?t=1414179&page=6](http://ubuntuforums.org/showthread.php?t=1414179&page=6)

I will try it when ill have some time. For now i cannot format all over again.

I've been searching about EFI and it looks like that's the problem. EFI is managing the boots ( windows 7 ) and linux must work with that, so that's why it doesnt find the OS.

Before trying your option, I will convert to MBR my HDD and install without EFI, just legacy boot, because i have no intention of having more than 4 partitions ( the reason why GPT is "better" ).

Thanks amsoares, I'll be givin news^^

---

