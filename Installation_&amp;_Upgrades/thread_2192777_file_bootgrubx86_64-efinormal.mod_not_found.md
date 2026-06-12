---
title: "file /boot/grub/x86_64-efi/normal.mod not found"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by antonioalonzi85 on 2013-12-09
Hi guys,

I need some help with boot-repair in order to properly setup my grub.

When I restart my computer it cannot boot and grub rescue starts.
The error given to me is: "**file /boot/grub/x86_64-efi/normal.mod not found**".

I can anyway boot ubuntu manually loading the kernel as follows:
```

set root=(hd0,gpt8)
set prefix=(hd0,gpt8)/boot/grub
insmod linux
linux /vmlinuz root=/dev/sda8 ro
initrd /initrd.img
boot

```

When I launch boot-repair in order to fix the boot it runs successfully but then I restart and I got always the same problem: computer not booted and redirected to grub rescue.
[LIST]
[*] Here my boot Summary Info: [http://paste.ubuntu.com/6547779/](http://paste.ubuntu.com/6547779/)
[/LIST]


Any suggestion to solve this?

Kind regards
Antonio

---

### Post by oldfred on 2013-12-09
Welcome to the forums.

Are you booting in UEFI mode? 
Do you have secure boot on or off? It does look like you have signed kernels installed so it should even boot with secure boot on.

---

### Post by antonioalonzi85 on 2013-12-12
My Bios settings are:
[LIST]
[*]Legacy Mode: Disabled
[*]Secure Boot: Disabled
[/LIST]

I tried to change my settings with:
[LIST]
[*]Legacy Mode: Disabled
[*]Secure Boot: Enabled
[/LIST]
And instead of starting the shell of "grub rescue" it starts the shell of "grub" (not the normal menu of grub to start).

I tried to change my settings with:
[LIST]
[*]Legacy Mode: Enabled
[*]Secure Boot: Disabled
[/LIST]
And I got a strange error that my boot is wrong and needs to be correct, insert a code and press enter to automatically fix it. I do it and it starts "grub rescue".

It's weird, I had until a couple of weeks ago the kubuntu 13.04 installed on this machine with this very same settings: (Legacy Mode: Disabled; Secure Boot: Disabled).
Then I upgraded to 13.10, but my wifi was not working anymore and I decided to reinstall 13.04.

I remember that I struggled the first time to install 13.04 and make the system boot without problems.
I tried myriads of times boot-repair and then the last time I tried magically worked.

But it looks like I'm not magic any more.

What do you think should I do?

---

### Post by oldfred on 2013-12-12
UEFI boots from efi partition, BIOS/Legacy/CSM boots from MBR. So if you have a UEFI install all boot files are in efi partition. Trying to boot in BIOS mode will find an empty MBR.

Besure to boot in UEFI mode.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Ubuntu live Installer which you can add Boot-Repair to will also boot in both UEFI or BIOS modes. 
      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by antonioalonzi85 on 2013-12-13
Hi oldfred,

Not sure I understand what you're suggesting.

About boot-info, are you asking something different from what I posted on my first thread?

[LIST]
[*][http://paste.ubuntu.com/6547779/](http://paste.ubuntu.com/6547779/)
[/LIST]

Regarding the secure boot when I set Secure Boot: Enabled my computer still fails to boot. I need to manually load the kernel how described and manually boot. The difference is that now I'm in "grub" shell instead then ""grub rescue" which seems better.

I tried to launch the system and run again boot-repair when I have the Boot: Enabled setting.
It gives me a warning: Please disable SecureBoot in the BIOS. Then try again.Do you want to continue?

If I continue it still installs correctly, but when I restart the computer still does not boot.

I'm getting always more confused with this. :(

Anyway I ran again boot-info with Secure Boot: Enabled and realized that the output is slightly different:

[LIST]
[*][http://paste.ubuntu.com/6568386/](http://paste.ubuntu.com/6568386/)
[/LIST]

Okay guys,

I'm doing some steps forward.

I realized that I can get the grub menu with:
```
configfile (hd0,gpt8)/boot/grub/grub.cfg
```

Then I realized that when I'm in Secure Boot: Enabled my prefix variable is as follows:
```

prefix=(hd0,gpt2)/EFI/ubuntu

```
And when I'm in Secure Boot: Disabled my root and prefix variables are as follows:
```

root=(hd0,gpt6)
prefix=(hd0,gpt6)/boot/grub

```
(this is output from either "grub" either "grub rescue" shells when digiting the command "set").

Now both of them are wrong:
[LIST]
[*]Secure Boot: Enabled: The actual ubuntu partition is not /dev/sda2 -> /EFI/ubuntu but /EFI/kubuntu;
[*]Secure Boot: Disabled: The boot is installed in gpt8 and not gpt6 (sda8 and not sda6);
[/LIST]

My first idea was to have the computer in Secure Boot: Enabled and rename the folder /dev/sda2 -> /EFI/kubuntu but /EFI/ubuntu;
Very bad idea: _*never do that*_!
The bios in someway see that the secure boot partition has been changed and won't allow to do anything at all. I needed to use again a live distro and run again boot-repair to at least enter again into the grub menu.

So my last option is to change the root and/or prefix to the correct path.
Unfortunately I'm struggling to do that.

"sudo grub-install /dev/sda8:" This command looks like it just installs the grub under sda8 but does not change the prefix.
Adding a "set prefix=(hd0,gpt8)/boot/grub" under /etc/grub.d/40_custom does not help either.

If I discover something else I'll update you.

Kind regards
Antonio

I solved, probably in the worst manner I could ever resolve but I succeeded.

The idea is to copy the /boot/grub where it is expected to be:

From "grub rescue" (not UEFI modality) check where the grub is expected with set (in my case prefix and root were pointing to gpt6 or sda6).
This partition was supposed to contain my home.

Launch the system and
```

# mount the partition
mkdir tmp
sudo mount /dev/sda6 mnt
cd mnt

# copy the boot there
sudo cp -r /boot .
cd ..

# unmount the partition and reboot
sudo umount mnt
rmdir mnt
sudo reboot

```

After that I can see the grub menu when the computer starts.

I hope this can help somebody.

Kind regards
Antonio

---

### Post by oldfred on 2013-12-13
Sorry missed link to BootInfo report in your first thread.

With UEFI or UEFI and secure boot, grub2 boot files are in the efi partition. All installed systems put their boot files into one efi partition. You can only have one efi partition per hard drive.
You do not install grub to a partition or PBR (or almost never).l
If in BIOS mode then you do install grub to the MBR.

There a some systems that will not boot Windows 8 or 8.1 from grub menu with secure boot on. There is a bug report for that. It seems that an extra character or two are in the string used to boot.
       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

Some systems have 'buggy' UEFI that only boots Windows not the ubuntu or  kubuntu entry in UEFI. Boot-Repair has a work around where it renames  the Windows efi file to really be shim. Then UEFI thinks it is booting Windows and it boots grub. But then you can only boot Windows from the  grub menu as it has the renamed efi file.
Some also use f12 or one time boot key to choose which to boot as UEFI/BIOS just does not support changing boot order. 
Most of these are UEFI issues or grub issues. Often Linux has to work around vendors who only design for Windows.

    
Your last link looks like Boot-Repair did run the rename. If you can boot the kubuntu entry that your UEFI has then undo the rename. It looks like it is in UEFI but not in boot order?
 line 603
efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 3001,3000,2001,2002
Boot[COLOR=#ff0000]0000[/COLOR]* kubuntu    HD(2,c8800,82000,d633e275-857a-41de-8ba7-cf3caff97b36)File(EFIkubuntushimx64.efi)
Boot0001* Windows Boot Manager    HD(2,c8800,82000,d633e275-857a-41de-8ba7-cf3caff97b36)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
If you cannot boot kubuntu from UEFI or one time boot key, you may need to keep the rename, but if Windows does updates it may overwrite the renamed file and then you need to rename again.


Someone with RAID posted that he had to add another grub.cfg in the efi partition in the ubuntu (kubuntu for you) folder with just the commands he had to manually enter. 

You could try creating a grub.cfg in kubuntu and just add the configure file and maybe the prefix commands. 

Your system has a lot of HP .efi files. I am not sure what they all are, many vendors have them in another partition that is FAT32 but not the efi partition. But since they are all .efi Boot-Repair does not know if you need them or not. You can edit 25_custom as that entire file was created by Boot-Repair. Instructions in the link in my signature.

---

