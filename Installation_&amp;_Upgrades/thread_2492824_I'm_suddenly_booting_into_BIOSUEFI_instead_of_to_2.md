---
title: "I'm suddenly booting into BIOS/UEFI instead of to 22.04 login screen"
date: 2023-11-23
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2023-11-23
A few weeks back I noticed that my desktop workstation was no longer booting directly into the login screen for Ubuntu MATE 22.04, but straight to the BIOS/UEFI.
 
From the BIOS screen I can hit the*** F1*** key, select the "Boot" menu and from there select which OS to boot into (but, of course, I shouldn't have to do that). 

I have ***22.04*** on an internal nvme drive, ***20.04*** on a 2nd internal nvme drive, and a backup ***20.04*** on an internal SSD. I do not use Microsoft Windows. 

I can access the GRUB menu by pressing ESC, and choose which OS to boot to from there, but I suspect some recent software update (or perhaps kernel update) caused this change.

Any tips on where I should begin to troubleshoot?  And has this happened to anyone else? Thanks.

---

### Post by sudodus on 2023-11-23
Boot [the awkward way] to the Ubuntu system that you want to be the default one and run

```

sudo update-grub

```
Then reboot. Did it solve the problem? Did something change? In that case what happens now? Or is it the same problem as before?

---

### Post by watchpocket on 2023-11-23
The problem doesn't occur on reboots. It also doesn't occur after complete shutdown and waiting a few minutes. 

 It occurs when I boot up the next morning, or after some longer (longer than 5 minutes) time period.  So I don't yet know if the situation has changed.

I'm going to try doing a shutdown and then waiting an hour.

Btw, I believe I have a grub on all 3 of my OS installs. (I entered the *sudo update-grub* command on all 3.) 

How do I determine which grub is the active one?  Thanks.

---

### Post by tea for one on 2023-11-23
> **watchpocket said:**
> Btw, I believe I have a grub on all 3 of my OS installs. (I entered the *sudo update-grub* command on all 3.) 
How do I determine which grub is the active one?  Thanks.
The active one will be the last OS where you updated grub.

---

### Post by sudodus on 2023-11-23
> **watchpocket said:**
> The problem doesn't occur on reboots. It also doesn't occur after complete shutdown and waiting a few minutes. 

 It occurs when I boot up the next morning, or after some longer (longer than 5 minutes) time period.  So I don't yet know if the situation has changed.


I would suspect that one of the drives is a slow starter. Maybe it will work better, if you add some seconds waiting time at boot. You can do that via editing the file

**[FONT=Courier New]/etc/default/grub[/FONT]**

to increase the **[FONT=Courier New]GRUB_TIMEOUT[/FONT]** variable and after that running again

**[FONT=Courier New]sudo update-grub[/FONT]**

from the system, that should have priority. See [this link](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2).

---

### Post by ubfan1 on 2023-11-23
You can always just edit the /boot/grub/grub.cfg file and change the wording on the menu items.  Or make a unique /etc/grub.d/40_custom for each disk.  With three disks, each getting grub installed, the order you run update-grub doesn't matter, the bootorder determines which runs.  But if the first fails, then the second one may get run. Might be a good idea to run the smartmontools package smartctl on your disks.

---

### Post by MAFoElffen on 2023-11-23
You didn't say what make/model/kind of system it is... 

From changing personalities from just booted, to a difference after it has sat for awhile (overnight, days, etc.), I would also check the voltage of the CMOS battery. A long-shot, but suspect.

There is a way to do that "programatically"... On shutdown, do
```

dd if=/dev/nvram of=cmos_ram_01.bin 

```
On startup do it again to a comparison file
```

dd if=/dev/nvram of=cmos_ram_02.bin 
TEST=$(cmp -b cmos_ram_01.bin cmos_ram_02.bin) # This will printout any bytes that differ
if [! -z "$TEST" ]
then 
  logger "NVRAM corrupted." # This will enter a message into the syslog
fi

```

---

### Post by oldfred on 2023-11-24
Ubuntu's default install is to one ESP on first drive. Whatever UEFI/BIOS defines as first drive.
Do you have separate ESP on each drive or just the one?

An update grub only updates menu.
But a grub install resets settings in UEFI boot menu & ESP to use that install as default boot. Then grub menu should have all installs in it.  Major update to grub may do a new grub-install, resetting that install to default.
Boot into preferred install and manually do a sudo grub-install to reset that to default boot.

Often easier to run Boot-Repair to see where everything is at.
But you can check GUID/partUUID used by UEFI settings.
sudo efibootmgr -v
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

And if ESP using default 0077 entry difficult to see entry, Boot-Repair changes to older entry of "defaults" in fstab, which may be less secure, but lets you see files when mounted. Otherwise you can use live installer & manually mount.

In ESP will be a 3 line grub.cfg that uses UUID of install. So with 3 installs, it could be any of them. Compare using lsblk -f or above command. You can manually edit or when booted into preferred default, do a  sudo grub-install to make that one the default.

---

### Post by watchpocket on 2023-11-24
> *You didn't say what make/model/kind of system it is.*

I built my desktop workstation computer myself. The only relevant info I can think of to answer this is in my sig.


> [I]Whatever UEFI/BIOS defines as first drive.

[/I]The first drive to boot is defined in UEFI/BIOS as my 22.04 nvme1 Jammy Jellyfish.


> [I]Do you have separate ESP on each drive or just the one?

[/I]I have an ESP on each of the three drives.


> [I]In ESP will be a 3 line grub.cfg that uses UUID of install.

[/I]```
--> [COLOR=#0000FF]*cat /boot/efi/EFI/grub/grub.cfg*[/COLOR] 

search.fs_uuid 3bcf9a37-e310-4945-87a8-dac0932a16cb root set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg 
```

(The above identical file -- with same UUID number -- is also in */boot/efi/EFI/**ubuntu**/grub.cfg*)


> [I]Boot into preferred install and manually do a sudo grub-install to reset that to default boot.
[/I]
Before I do that, I will lay out some likely relevant general info here:

```
-->[COLOR=#0000FF]* sudo efibootmgr -v*[/COLOR] 

BootCurrent: 0001

Timeout: 1 seconds

BootOrder: 0001,0000,0002,0006

Boot0000* 20.04__Focal-Fossa    HD(1,GPT,337ce8d2-65a0-4051-8c12-55cc22666e7e,0x4000,0xc9000)/File(\EFI\UBUNTU\SHIMX64.EFI)

Boot0001* 22.04_NVMe1__Jammy-Jellyfish    HD(1,GPT,90af4214-eca8-4265-8e5f-9c2e3301bba9,0x4000,0xc939a)/File(\EFI\UBUNTU\SHIMX64.EFI)

Boot0002* 20.04_SSD____Focal-Fossa    HD(1,GPT,684141f2-20c3-41be-b2c4-7058d9488896,0x4000,0x113229)/File(\EFI\UBUNTU\SHIMX64.EFI)

Boot0006* grub    HD(1,GPT,684141f2-20c3-41be-b2c4-7058d9488896,0x4000,0x113229)/File(\EFI\GRUB\SHIMX64.EFI)

```
 

```
--> [COLOR=#0000FF]*lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid*[/COLOR] 

NAME        FSTYPE   SIZE FSUSED LABEL       PARTLABEL                  MOUNTPOINT UUID                                 PARTUUID
sda                894.3G                                                                                               
&#9500;&#9472;sda1      vfat   550.3M        SSD_ESP     SSD_EFI-system-partition              6DE5-0FF8                            684141f2-20c3-41be-b2c4-7058d9488896
&#9492;&#9472;sda2      ext4   893.7G        20.04_SSD   UbuntuMATE-20.04_SSD                  21697ef7-83e3-4414-a859-91841f61dce8 7cc6f822-eb23-4829-9039-6d09e6e0ca55
sdb                894.3G                                                                                               
&#9492;&#9472;sdb1      ext4   894.3G        WeirdBeard  WeirdBeard_data                       70e15e24-a75c-4115-9c83-29cb585676f6 5ab70820-78e7-466e-9c0f-101054d5df9b
nvme0n1            931.5G                                                                                               
&#9500;&#9472;nvme0n1p1 vfat     402M        NVME0_ESP   nvme0_EFI-system-partition            2BD2-4199                            337ce8d2-65a0-4051-8c12-55cc22666e7e
&#9492;&#9472;nvme0n1p2 ext4   931.1G        20.04_NVMe0 UbuntuMATE-20.04                      07041e0f-1cde-4caf-9b1d-86851e9601ed 0657b873-53c2-4a40-9e60-3b26c891fd1b
nvme1n1            931.5G                                                                                               
&#9500;&#9472;nvme1n1p1 vfat   402.5M  10.3M NVME1_ESP   nvme1_EFI-system-partition /boot/efi  E23B-29C2                            90af4214-eca8-4265-8e5f-9c2e3301bba9
&#9492;&#9472;nvme1n1p2 ext4   931.1G    53G 22.04_NVMe1 UbuntuMATE-22.04_nvme1     /          3bcf9a37-e310-4945-87a8-dac0932a16cb 77706804-715d-4276-9824-a184ed00df4f

```


Also, and this may be important here (though I think this file is correct and has been serving me well for months), 
I have an ***/etc/grub.d/06_custom ***file. 
(It's 258 lines; ignore all the "*......." - they're invisible characters denoting spaces; same for "____" which denotes a line-continuation).

That file is on pastebin at [https://paste.ubuntu.com/p/tQhsBzDpWr/](https://paste.ubuntu.com/p/tQhsBzDpWr/) 

Thanks for looking at this info.

---

### Post by MAFoElffen on 2023-11-25
"Asus ROG Crosshair VIII Hero wifi" was released July 1, 2019. About 4 years ago or so. Life expectancy of a CMOS battery is 3-5 years.

Possible. But can be ruled out easy enough on that board. (not a laptop of notepad, where it is somethings is 'under' the motherboard.)

---

### Post by oldfred on 2023-11-25
I have tried renaming entries in UEFI by changing /etc/default/grub. But Ubuntu's grubx64.efi seems to be hard coded to use the /EFI/ubuntu folder.
For example my grub  entry for external drive.
[FONT=monospace][COLOR=#000000]GRUB_DISTRIBUTOR=ssk
[/COLOR]And I keep grub entries in 40_custom simple. Either just boot stanza or configfile.
```
[/FONT][FONT=monospace][COLOR=#000000]menuentry "Ubuntu 23.04 lunar  (on /dev/sda9)" { [/COLOR]
    #set root=(hd1,gpt9)     
    search --set=root --label lunar  --hint hd1,gpt9 
    configfile /boot/grub/grub.cfg 
}

[/FONT][FONT=monospace]
```

[/FONT]Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)[FONT=monospace]




[/FONT]

---

### Post by watchpocket on 2023-12-01
> **MAFoElffen said:**
> 
I would also check the voltage of the CMOS battery. A long-shot, but suspect.
There is a way to do that "programatically"... On shutdown, do
```

dd if=/dev/nvram of=cmos_ram_01.bin 

```
On startup do it again to a comparison file
```

dd if=/dev/nvram of=cmos_ram_02.bin 
TEST=$(cmp -b cmos_ram_01.bin cmos_ram_02.bin) # This will printout any bytes that differ
if [! -z "$TEST" ]
then 
  logger "NVRAM corrupted." # This will enter a message into the syslog
fi

```

I am also at this point suspecting the CMOS battery, but could I maybe get some clarification about running the the above commands?

So just before shutting down, I created a *cmos_ram_01.bin *file with your first line above.

Then I re-started and created the* cmos_ram_02.bin* file immediately after starting up.  


The rest is what I have trouble with. I can enter this line at my prompt:
[I]TEST=$(cmp -b cmos_ram_01.bin cmos_ram_02.bin)

[/I]and nothing happens, except that I am returned to my shell prompt. (Maybe nothing is supposed to happen yet.)

But when I enter:
if [! -z "$TEST" ]

I am put into a secondary "if -->"  prompt (which I may have long ago set up as a python prompt, something like that) and nothing else happens.  I can then enter *logger "NVRAM corrupted."  *but none of these entries return any info on the commandline.

Maybe what I need to see from this is in the syslog, but I don't recall exactly where in the file system *syslog* is located.  

Wait -- just now opening the* lnav* app, it puts me into *syslog_log*, and I see this:

[I]Dec  1 16:07:43 rjbox rj: NVRAM corrupted.

[/I]But that's only because I wrote *"logger "NVRAM corrupted" *at the prompt, right? Shouldn't I see somewhere a voltage difference?

  I'm afraid I'm not clear on how to run the commands you put above.

(For what it's worth, I did this (thoug it may not tell the whole story):
```
--> cat /proc/driver/rtc | grep batt 
batt_status    : okay

```

---

### Post by watchpocket on 2023-12-02
SOLVED.  It's the CMOS battery.  

I always turn off the power supply as well as the motherboard.  Yesterday I left the power supply on all night and booted today directly into the preferred OS install, instead of to the UEFI setup.  

That means the battery got enough power overnight to keep all its memory intact.

Now I know that I just need to replace the battery soon.

---

