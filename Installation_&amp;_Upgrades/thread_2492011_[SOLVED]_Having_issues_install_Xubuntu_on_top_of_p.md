---
title: "[SOLVED] Having issues install Xubuntu on top of previous Arch install"
date: 2023-10-27
forum: Installation &amp; Upgrades
---

### Post by kingthrillgore on 2023-10-27
Good afternoon. After some unexpected issues with Arch, I decided to start fresh with Xubuntu 22.04.3 LTS on my Lenovo Thinkpad X1 Carbon. I did the following things before I began the install:

* Use Windows Recovery to overwrite the existing Grub bootloader
* Deleted the Arch and Swap partitions in Windows 10 and left them unallocated

And then I went through the LiveUSB install. However, the install failed because it couldn't install Grub, said there was a fatal error. I did some additional research and learned that it could be fixed with boot-repair. So I booted back into the LiveUSB, mounted the EFI, and then ran boot-repair. Unfortunately, it didn't work, failing with: ```
NVram is locked (Ubuntu not found in efibootmgr). Please report this message to boot.repair@gmail.com
```

And that's kind of where I'm at right now. I'm not sure why it won't accept Grub. Its possible that its still hanging on to the Arch Grub. Grub doesn't boot at all, the Windows bootloader is what starts unless interrupted. The system BIOS is set with Secure Boot to OFF, and its on UEFI Boot mode only. The pastebin generated boot-repair can be viewed [here]("https://paste.ubuntu.com/p/Gq2ddvRxsX/"). Any insight on what I can do to get this working would be great! Thanks in advance.

---

### Post by #&amp;thj^% on 2023-10-27
The first thing that jumps out is this:
```
/dev/sda4  5955584 30031808 24076225 11.5G Linux filesystem
```
Is that the size you used when installing?
Plus I see Fedora and Arch, but no matter if 11.5Gigs is all you allowed then it's not enough for Ubuntu
Still reading the report though
And I see loads of left overs:
```
 GiB - GB             File                                 Fragment(s)
            ?? = ??             vmlinuz-linux                                  1
            ?? = ??             vmlinuz-linux-zen                              8
            ?? = ??             initramfs-linux-fallback.img                   4
            ?? = ??             initramfs-linux.img                            2
            ?? = ??             initramfs-linux-zen-fallback.img              17
            ?? = ??             initramfs-linux-zen.img                        2

```
And this as well:
```
nvme0n1p5: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17 05:35 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

```
Are you planing on keeping Windows then?

---

### Post by kingthrillgore on 2023-10-27
I think it says /dev/sda4 because its talking about the LiveUSB I'm running on, the install was done on /dev/nvme0n1 and I think these changes are being made there, unless the system is installing to the USB stick. 

If these leftovers on Grub are causing issues, what would be the best way to remove them? I've never had to work with EFI before so this is all greek to me.

And yes, I do plan on keeping Windows for now.

---

### Post by tea for one on 2023-10-27
> **kingthrillgore said:**
> And yes, I do plan on keeping Windows for now.

[COLOR="#0000FF"]Line 4594[/COLOR] - Boot files:        /EFI/refind/refind.conf /efi/Boot/bootx64.efi 
[COLOR="#0000FF"]Line 4645[/COLOR] - OS#2:   Windows XP on nvme0n1p3

Are you using rEFInd as a boot manager?
Is line 4645 correct, you have Windows XP?

The boot-repair report does not even suggest a recommended repair, therefore, the first priority is to backup all your personal data.
Please reply when you have done this.

---

### Post by kingthrillgore on 2023-10-27
> **tea for one said:**
> [COLOR=#0000FF]Line 4594[/COLOR] - Boot files:        /EFI/refind/refind.conf /efi/Boot/bootx64.efi 
[COLOR=#0000FF]Line 4645[/COLOR] - OS#2:   Windows XP on nvme0n1p3

Are you using rEFInd as a boot manager?
Is line 4645 correct, you have Windows XP?

The boot-repair report does not even suggest a recommended repair,  therefore, the first priority is to backup all your personal data.
Please reply when you have done this.

I mean, I have rEFInd installed but am not using it. Booting in with  rEFInd in fact, does not load any OS besides Windows, which works as  intended. Right now, it just boots with the Windows bootloader. Any attempt to boot Ubuntu from here kicks me back to rEFInd.

I keep all my personal data on a NAS at home, so i'm backed up.

---

### Post by tea for one on 2023-10-27
Is line 4645 correct, you have Windows XP?

---

### Post by MAFoElffen on 2023-10-27
Being I contribute some to boot-repair... From booted from the Boot-Repair LiveUSB media, open a terminal then... Do this _first_:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```
To confirm which Boot mode you booted into. Especially with Lenovo's and HP's that have a hybrid boot mode as a UEFI setting.

That is always the first thing I suspect and have to rule out when I see the it reports the NVRAM as locked.

---

### Post by kingthrillgore on 2023-10-27
> **tea for one said:**
> [COLOR=#0000FF]Line 4594[/COLOR] - Boot files:        /EFI/refind/refind.conf /efi/Boot/bootx64.efi 
[COLOR=#0000FF]Line 4645[/COLOR] - OS#2:   Windows XP on nvme0n1p3

Are you using rEFInd as a boot manager?
Is line 4645 correct, you have Windows XP?

The boot-repair report does not even suggest a recommended repair, therefore, the first priority is to backup all your personal data.
Please reply when you have done this.

> **tea for one said:**
> Is line 4645 correct, you have Windows XP?

Nope, only Windows 10. And in response to the above comment, it returned "UEFI Firmware mode."

---

### Post by tea for one on 2023-10-27
rEFInd has an option to boot the Linux kernel directly.
Have you tried it?

If you hover over the icons, you should see something like:-
Boot boot\vmlinuz-6.2.0-26-generic from 634.8 GiB ext4 volume

---

### Post by #&amp;thj^% on 2023-10-27
> **kingthrillgore said:**
> 
I keep all my personal data on a NAS at home, so i'm backed up.

rarely do we see a newer member with this plan intact, I commend you!:popcorn:
Now I have a 7th Gen X1 carbon and it fills up with prior installs ie:
```
efibootmgr
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0008,0007,0003,0000,2002,2003,2001
Boot0000* ubuntu
Boot0001* EFI PXE 0 for IPv4 (00-2B-67-51-92-B0) 
Boot0002* EFI PXE 0 for IPv6 (00-2B-67-51-92-B0) 
Boot0003* EFI Hard Drive (SAMSUNG MZVLB256HBHQ-000L2)
Boot0004* EFI USB Device (Sabrent)
Boot0007  GhostBSD
Boot0008* crystal
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network

```
might help if we take a peek there as well, this is a time consumer, Due to the fact Windows needs to stay for now.
I'm on the fly today back and forth, but you have two members here with excellent skills to help you along.
I'll check back, but be aware this one is a mess. ;)

---

### Post by kingthrillgore on 2023-10-27
> **tea for one said:**
> rEFInd has an option to boot the Linux kernel directly.
Have you tried it?

If you hover over the icons, you should see something like:-
Boot boot\vmlinuz-6.2.0-26-generic from 634.8 GiB ext4 volume

Interestingly, I did see a boot option for Ubuntu (or at least ubuntu\grubx64.efi) and one for a Linux kernel that isn't there anymore (the linux-zen for Arch) and loading either just kicked me back to rEFInd. Only the Windows boot option works.
> **1fallen said:**
> rarely do we see a newer member with this plan intact, I commend you![IMG]https://ubuntuforums.org/images/smilies/new_popcornsmiley.gif[/IMG]
Now I have a 7th Gen X1 carbon and it fills up with prior installs ie:
```
efibootmgr
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0008,0007,0003,0000,2002,2003,2001
Boot0000* ubuntu
Boot0001* EFI PXE 0 for IPv4 (00-2B-67-51-92-B0) 
Boot0002* EFI PXE 0 for IPv6 (00-2B-67-51-92-B0) 
Boot0003* EFI Hard Drive (SAMSUNG MZVLB256HBHQ-000L2)
Boot0004* EFI USB Device (Sabrent)
Boot0007  GhostBSD
Boot0008* crystal
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network

```
might help if we take a peek there as well, this is a time consumer, Due to the fact Windows needs to stay for now.
I'm on the fly today back and forth, but you have two members here with excellent skills to help you along.
I'll check back, but be aware this one is a mess. [IMG]https://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]

Not my first rodeo. Since you posted the efibootmgr, I thought i'd do the same:

```

xubuntu@xubuntu:~$ efibootmgr 
BootCurrent: 0019 
Timeout: 0 seconds 
BootOrder: 001B,0002,0001,0013,0014,0015,0016,0017,0018,0019,0012,001A,000C,000D 

Boot0001* rEFInd Boot Manager 
Boot0002* grub 
Boot0003  Setup 
Boot0004  Boot Menu 
Boot0005  Diagnostic Splash Screen 
Boot0006  Lenovo Diagnostics 
Boot0007  Regulatory Information 
Boot0008  ThinkShield secure wipe 
Boot0009  Startup Interrupt Menu 
Boot000A  Rescue and Recovery 
Boot000B  MEBx Hot Key 
Boot000C  Other CD 
Boot000D  Other HDD 
Boot000E* USBR BOOT CDROM 
Boot000F* USBR BOOT Floppy 
Boot0010* ATA HDD 
Boot0011* ATAPI CD 
Boot0012* PXE BOOT 
Boot0013* USB CD 
Boot0014* USB FDD 
Boot0015* NVMe0 
Boot0016* NVMe1 
Boot0017* ATA HDD0 
Boot0018* ATA HDD1 
Boot0019* USB HDD 
Boot001A* LENOVO CLOUD 
Boot001B* Windows Boot Manager

```

So yeah there's a lot of entries here. Things were easier before EFI, the last time I dual booted a decade ago.

---

### Post by MAFoElffen on 2023-10-27
> **kingthrillgore said:**
> 
```

xubuntu@xubuntu:~$ efibootmgr 
...
BootOrder: 001B,0002,0001,0013,0014,0015,0016,0017,0018,0019,0012,001A,000C,000D 
Boot0002* grub 
Boot001B* Windows Boot Manage
...

```

See the boot order set there? Try swapping the order for the boot order between 0002, & 001B so they start in that order... That would be to Grub, then the Windows Boot Loader.

---

### Post by kingthrillgore on 2023-10-28
> **MAFoElffen said:**
> See the boot order set there? Try swapping the order for the boot order between 0002, & 001B so they start in that order... That would be to Grub, then the Windows Boot Loader.

I changed the boot order, and it does load grub, but it can't load `/grub/x86_64-efi/normal.mod` (says file not found) and kicks me to Rescue mode. I'm in the dark on how to use Rescue mode, so I will probably go back to LiveUSB for the next steps.

---

### Post by tea for one on 2023-10-28
In your UEFI settings, can you check if any of the following are enabled:--
TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module) or TPT (Trust Platform Technology)
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
If enabled, try disabling them.

---

### Post by kingthrillgore on 2023-10-28
> **tea for one said:**
> In your UEFI settings, can you check if any of the following are enabled:--
TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module) or TPT (Trust Platform Technology)
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
If enabled, try disabling them.


Device Guard is off. Couldn't find OS Optimized defaults. I turned TPM off, same results as before: Grub loads and it can't find the file so it goes to Rescue Mode.

---

### Post by tea for one on 2023-10-28
Now that TPM is disabled, two more suggestions:-

[LIST]
[*]Boot into a live session and run boot-repair - it may install Grub correctly.
[*]Boot into your PC and use rEFInd to open an EFI shell - from there we can find the boot file
[*]
[/LIST]
If you have to use the EFI shell, the instructions are similar to this:-
Identify your Efi System Partition e.g. FSO
Type FSO: i.e. FSO and colon symbol (press enter)
Then type \EFI\ubuntu\grubx64.efi (and hit enter)

---

### Post by kingthrillgore on 2023-10-28
> **tea for one said:**
> Now that TPM is disabled, two more suggestions:-

[LIST]
[*]Boot into a live session and run boot-repair - it may install Grub correctly. 
[*]Boot into your PC and use rEFInd to open an EFI shell - from there we can find the boot file 
[/LIST]
If you have to use the EFI shell, the instructions are similar to this:-
Identify your Efi System Partition e.g. FSO
Type FSO: i.e. FSO and colon symbol (press enter)
Then type \EFI\ubuntu\grubx64.efi (and hit enter)

Okay, so i'll start with what i've done up to this point:

* Booted to LiveUSB, connected to internet, mounted the EFI partition (/dev/nvme0n1p1) to /efi
* Installed boot-repair
* Ran BootInfo summary you can view here [https://paste.ubuntu.com/p/6SQtrFYXvQ/](https://paste.ubuntu.com/p/6SQtrFYXvQ/)

I noticed that there is a /boot here in the filesystem that I assume is part of the LiveUSB.

I will attempt a repair with boot-repair next.

Edit: Gave that an attempt, and again, NVram is locked. Pastebin for that is [https://paste.ubuntu.com/p/yqjN4WGbrp](https://paste.ubuntu.com/p/yqjN4WGbrp). Going to try rEFInd next as recommended.

Edit 2: I decided to check the EFI partition myself and here's an ls

```

xubuntu@xubuntu:~$ ls /efi 

'$RECYCLE.BIN'   grub_old                           refind_linux.conf 

 bootmgr         initramfs-linux-fallback.img      'System Volume Information' 

 boot_rm         initramfs-linux.img                vmlinuz-linux 
 EFI             initramfs-linux-zen-fallback.img   vmlinuz-linux-zen 
 grubfont.pf2    initramfs-linux-zen.img 
 
xubuntu@xubuntu:/efi/EFI$ ls /efi/EFI 

Boot  EFI  GRUB  Microsoft  refind  tools  ubuntu

```

The ubuntu/grubx64.efi is in that EFI directory, so I am wondering if there's something amiss with the directory hierarchy here.

Edit 3: I did not see an option for an EFI Shell in rEFInd, its likely it never installed when I configured rEFInd whenever it installed (or whatever installed it). It should be possible to add it, though...

---

### Post by jeremy31 on 2023-10-28
You might need to look around in BIOS setting to see if there is a UEFI boot order you can change, put ubuntu first, save settings and boot

---

### Post by tea for one on 2023-10-28
> **kingthrillgore said:**
> Edit 3: I did not see an option for an EFI Shell in rEFInd, its likely it never installed when I configured rEFInd whenever it installed (or whatever installed it). It should be possible to add it, though...
In emergencies, I use rEFInd on a portable USB stick.
The option to boot an EFI Shell is in the portable version.
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)  - Option 5

The USB version may also find and boot the kernel directly (as mentioned in post 9)

While you are in a live "Try Ubuntu" session, it would be useful to run fsck against the ESP
```
sudo fsck /dev/nvme0n1p1
```

---

### Post by kingthrillgore on 2023-10-28
> **tea for one said:**
> In emergencies, I use rEFInd on a portable USB stick.
The option to boot an EFI Shell is in the portable version.
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)  - Option 5

The USB version may also find and boot the kernel directly (as mentioned in post 9)

While you are in a live "Try Ubuntu" session, it would be useful to run fsck against the ESP
```
sudo fsck /dev/nvme0n1p1
```

I'm currently burning a LiveUSB for rEFInd. In the meantime, I ran fsck on Ubuntu LiveUSB and I got this prompt:

```

xubuntu@xubuntu:~$ sudo fsck /dev/nvme0n1p1 

fsck from util-linux 2.37.2 
fsck.fat 4.2 (2021-01-31) 

There are differences between boot sector and its backup. 

This is mostly harmless. Differences: (offset:original/backup) 

  65:01/00 

1) Copy original to backup 

2) Copy backup to original 
3) No action 
[123?q]?

```

I'm gonna hold off on any action until I get a recommendation, out of caution.

---

### Post by tea for one on 2023-10-28
I would recommend that you repair the partition.

Copy backup to original.

---

### Post by kingthrillgore on 2023-10-28
> **tea for one said:**
> I would recommend that you repair the partition.

Copy backup to original.

Okay, thats done. Should I attempt to restart and boot into Grub or rEFInd next?

Edit: I attempted to boot into Grub, same normal.mod error as before.

---

### Post by #&amp;thj^% on 2023-10-28
> **kingthrillgore said:**
> Okay, thats done. Should I attempt to restart and boot into Grub or rEFInd next?

Edit: I attempted to boot into Grub, same normal.mod error as before.

i use the same as tea for one "refind" on USB and boot from those options, if possible of course.

---

### Post by kingthrillgore on 2023-10-28
> **1fallen said:**
> i use the same as tea for one "refind" on USB and boot from those options, if possible of course.

Okay, so I booted into rEFInd and ran the commands to get into the right volume, ran the command to run the grubx64.efi, and it returned "Command Error Status: Unsupported."

---

### Post by #&amp;thj^% on 2023-10-28
Note: I'm not a Windows user, so this is something I'm not familiar with:
```
* Use Windows Recovery to overwrite the existing Grub bootloader
* Deleted the Arch and Swap partitions in Windows 10 and left them unallocated
```
Since I've not used this method, I'm wondering if this is the issue.
Recommended to use Linux tools for Linux Systems and Windows tools for Windows.
If Arch was the first install it would handled that on it's own, even Fedora would have done the same.
But for sure on "my" X1 carbon I remove through efibootmgr systems when I'm done with them, reason is efibootmgr never forgets.
I'm not sure how to advise to proceed from here.

---

### Post by tea for one on 2023-10-28
> **kingthrillgore said:**
> Okay, so I booted into rEFInd and ran the commands to get into the right volume, ran the command to run the grubx64.efi, and it returned "Command Error Status: Unsupported."
Did the portable rEFInd show the option to boot the Linux kernel directly?

---

### Post by kingthrillgore on 2023-10-28
> **tea for one said:**
> Did the portable rEFInd show the option to boot the Linux kernel directly?

I checked, it did have this option at the end, and it worked... So  we can get into Xubuntu this way and I am now running it! Now, can we  fix Grub or rEFInd from here? I'll leave it here for now.

> **1fallen said:**
> Note: I'm not a Windows user, so this is something I'm not familiar with:
```
* Use Windows Recovery to overwrite the existing Grub bootloader
* Deleted the Arch and Swap partitions in Windows 10 and left them unallocated
```
Since I've not used this method, I'm wondering if this is the issue.
Recommended to use Linux tools for Linux Systems and Windows tools for Windows.
If Arch was the first install it would handled that on it's own, even Fedora would have done the same.
But for sure on "my" X1 carbon I remove through efibootmgr systems when I'm done with them, reason is efibootmgr never forgets.
I'm not sure how to advise to proceed from here.

Not throwing this out as an option B, but if I wanted to just blast the W10 partition (and assume I never want to go back to it), would it be easier to rectify our issue here if we did a clean install with Xubuntu, or would we still have to fight the EFI boot manager?

---

### Post by #&amp;thj^% on 2023-10-28
> **kingthrillgore said:**
> I checked, it did have this option at the end, and it worked... So  we can get into Xubuntu this way and I am now running it! Now, can we  fix Grub or rEFInd from here? I'll leave it here for now.



Not throwing this out as an option B, but if I wanted to just blast the W10 partition (and assume I never want to go back to it), would it be easier to rectify our issue here if we did a clean install with Xubuntu, or would we still have to fight the EFI boot manager?

Yay your in, before we get to drastic, lets have a peek now from Xubuntu's view.
```
sudo efibootmgr
```
And just add that efimgr never forgets my second X1 for playing shows this:
```
Boot to FW : false
BootCurrent: 001b
Timeout    : 0 seconds
BootOrder  : 0008, 0007, 0006, 0004, 0005, 0001, 0002, 000D, 0000, 000B, 001B, 001F, 0010, 0011, 0012, 0013, 0014, 0015, 0019, 001A, 001C, 001D, 001E, 0020, 0021, 0022, 0023, 0024, 0003
 Boot0008  GhostBSD
 Boot0007* crystal
 Boot0006* arch
 Boot0004* ubuntu
 Boot0005* ubuntu
 Boot0001* ubuntu
 Boot0002* endeavouros
 Boot000D* opensuse-secureboot
 Boot0000* Windows Boot Manager
 Boot000B* ArcoLinux
+Boot001B* NVMe0
 Boot001F* USB HDD
 Boot0010  Setup
 Boot0011  Boot Menu
 Boot0012  Diagnostic Splash Screen
 Boot0013  Lenovo Diagnostics
 Boot0014  Regulatory Information
 Boot0015  ThinkShield secure wipe
 Boot0019* USB CD
 Boot001A* USB FDD
 Boot001C* NVMe1
 Boot001D* ATA HDD0
 Boot001E* ATA HDD1
 Boot0020* PXE BOOT
 Boot0021* HTTPS BOOT
 Boot0022* LENOVO CLOUD
 Boot0023  Other CD
 Boot0024  Other HDD
 Boot0003* Linux-Firmware-Updater

```

---

### Post by kingthrillgore on 2023-10-28
> **1fallen said:**
> Yay your in, before we get to drastic, lets have a peek now from Xubuntu's view.
```
sudo efibootmgr
```

Done.

```

ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:~$ sudo efibootmgr | tee output2.txt
ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:~$ pastebinit -i output2.txt
https://paste.ubuntu.com/p/xhjQGtHqDm/

```

```

BootCurrent: 0019
Timeout: 0 seconds
BootOrder: 0002,001B,0001,0013,0014,0015,0016,0017,0018,0019,0012,001A,000C,000D
Boot0001* rEFInd Boot Manager
Boot0002* grub
Boot0003  Setup
Boot0004  Boot Menu
Boot0005  Diagnostic Splash Screen
Boot0006  Lenovo Diagnostics
Boot0007  Regulatory Information
Boot0008  ThinkShield secure wipe
Boot0009  Startup Interrupt Menu
Boot000A  Rescue and Recovery
Boot000B  MEBx Hot Key
Boot000C  Other CD
Boot000D  Other HDD
Boot000E* USBR BOOT CDROM
Boot000F* USBR BOOT Floppy
Boot0010* ATA HDD
Boot0011* ATAPI CD
Boot0012* PXE BOOT
Boot0013* USB CD
Boot0014* USB FDD
Boot0015* NVMe0
Boot0016* NVMe1
Boot0017* ATA HDD0
Boot0018* ATA HDD1
Boot0019* USB HDD
Boot001A* LENOVO CLOUD
Boot001B* Windows Boot Manager

```

0019 was the USB stick (well, a USB HDD) I used to run rEFInd.

---

### Post by jeremy31 on 2023-10-28
See if it can be fixed from in Windows [https://askubuntu.com/questions/655011/windows-10-upgrade-kills-grub-and-boot-repair-doesnt-help](https://askubuntu.com/questions/655011/windows-10-upgrade-kills-grub-and-boot-repair-doesnt-help)

---

### Post by #&amp;thj^% on 2023-10-28
That dose not look bad at all, can you now install Grub?
Lets look at that drive:
```
df -hT
```

---

### Post by kingthrillgore on 2023-10-28
> **1fallen said:**
> That dose not look bad at all, can you now install Grub?
Lets look at that drive:
```
df -hT
```

I don't think we're installing anything on that drive, its use is 100%
```

ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:~$ df -hT
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  1.6G  2.0M  1.6G   1% /run
/dev/nvme0n1p5 ext4   624G   11G  582G   2% /
tmpfs          tmpfs  7.7G     0  7.7G   0% /dev/shm
tmpfs          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p1 vfat   256M  256M     0 100% /boot/efi
tmpfs          tmpfs  1.6G  100K  1.6G   1% /run/user/1000

```

Can we remove records from the EFI part w/o damaging the NVRam? If so, I think first step is to delete the vmlinuzs for Arch that don't go anywhere anymore, that we dug up earlier in the thread. Advise me on how we should go about recovering space here w/o bricking the system.

---

### Post by tea for one on 2023-10-28
> **kingthrillgore said:**
> I checked, it did have this option at the end, and it worked... So  we can get into Xubuntu this way and I am now running it! Now, can we  fix Grub or rEFInd from here? I'll leave it here for now.
As you are now booted into Xubuntu via rEFInd USB, I hope that Grub can now be repaired given that TPM is disabled and the ESP has been repaired.
If this throws an error, then you should still be able to boot via rEFInd portable.
From your installed system, terminal command:-
```
sudo grub-install /dev/nvme0n1
```

Stop one second, your ESP is full!
```
ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:~$ df -hT
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  1.6G  2.0M  1.6G   1% /run
/dev/nvme0n1p5 ext4   624G   11G  582G   2% /
tmpfs          tmpfs  7.7G     0  7.7G   0% /dev/shm
tmpfs          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
[COLOR="#FF0000"]/dev/nvme0n1p1 vfat   256M  256M     0 100% /boot/efi[/COLOR]
tmpfs          tmpfs  1.6G  100K  1.6G   1% /run/user/1000
```

Here is the website to help you manage efibootmgr.
[https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

---

### Post by #&amp;thj^% on 2023-10-28
> **kingthrillgore said:**
> I don't think we're installing anything on that drive, its use is 100%
```

ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:~$ df -hT
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  1.6G  2.0M  1.6G   1% /run
/dev/nvme0n1p5 ext4   624G   11G  582G   2% /
tmpfs          tmpfs  7.7G     0  7.7G   0% /dev/shm
tmpfs          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p1i vfat   256M  256M     0 100% /boot/efi
tmpfs          tmpfs  1.6G  100K  1.6G   1% /run/user/1000

```

Can we remove records from the EFI part w/o damaging the NVRam? If so, I think first step is to delete the vmlinuzs for Arch that don't go anywhere anymore, that we dug up earlier in the thread. Advise me on how we should go about recovering space here w/o bricking the system.

Well we can but which ones? I not sure from what all is shown now, if you look at mine, it has names for better views.
Now after my clean up now reads:
```
sudo efibootmgr -b 0006 -B
Removing boot variable 'Boot0006'
Removing 0x6 from BootOrder
Boot to FW : false
BootCurrent: 001b
Timeout    : 0 seconds
BootOrder  : 0008, 001B, 001F, 0010, 0011, 0012, 0013, 0014, 0015, 0019, 001A, 001C, 001D, 001E, 0020, 0021, 0022, 0023, 0024, 0003
 Boot0008  GhostBSD
+Boot001B* NVMe0
 Boot001F* USB HDD
 Boot0010  Setup
 Boot0011  Boot Menu
 Boot0012  Diagnostic Splash Screen
 Boot0013  Lenovo Diagnostics
 Boot0014  Regulatory Information
 Boot0015  ThinkShield secure wipe
 Boot0019* USB CD
 Boot001A* USB FDD
 Boot001C* NVMe1
 Boot001D* ATA HDD0
 Boot001E* ATA HDD1
 Boot0020* PXE BOOT
 Boot0021* HTTPS BOOT
 Boot0022* LENOVO CLOUD
 Boot0023  Other CD
 Boot0024  Other HDD
 Boot0003* Linux-Firmware-Updater

```

---

### Post by kingthrillgore on 2023-10-28
> **1fallen said:**
> Well we can but which ones? I not sure from what all is shown now, if you look at mine, it has names for better views.
Now after my clean up now reads:
```
sudo efibootmgr -b 0006 -B
Removing boot variable 'Boot0006'
Removing 0x6 from BootOrder
Boot to FW : false
BootCurrent: 001b
Timeout    : 0 seconds
BootOrder  : 0008, 001B, 001F, 0010, 0011, 0012, 0013, 0014, 0015, 0019, 001A, 001C, 001D, 001E, 0020, 0021, 0022, 0023, 0024, 0003
 Boot0008  GhostBSD
+Boot001B* NVMe0
 Boot001F* USB HDD
 Boot0010  Setup
 Boot0011  Boot Menu
 Boot0012  Diagnostic Splash Screen
 Boot0013  Lenovo Diagnostics
 Boot0014  Regulatory Information
 Boot0015  ThinkShield secure wipe
 Boot0019* USB CD
 Boot001A* USB FDD
 Boot001C* NVMe1
 Boot001D* ATA HDD0
 Boot001E* ATA HDD1
 Boot0020* PXE BOOT
 Boot0021* HTTPS BOOT
 Boot0022* LENOVO CLOUD
 Boot0023  Other CD
 Boot0024  Other HDD
 Boot0003* Linux-Firmware-Updater

```

Well, here's what efibootmgr says for me:

```

sudo efibootmgr
BootCurrent: 0019
Timeout: 0 seconds
BootOrder: 0002,001B,0001,0013,0014,0015,0016,0017,0018,0019,0012,001A,000C,000D
Boot0001* rEFInd Boot Manager
Boot0002* grub
Boot0003  Setup
Boot0004  Boot Menu
Boot0005  Diagnostic Splash Screen
Boot0006  Lenovo Diagnostics
Boot0007  Regulatory Information
Boot0008  ThinkShield secure wipe
Boot0009  Startup Interrupt Menu
Boot000A  Rescue and Recovery
Boot000B  MEBx Hot Key
Boot000C  Other CD
Boot000D  Other HDD
Boot000E* USBR BOOT CDROM
Boot000F* USBR BOOT Floppy
Boot0010* ATA HDD
Boot0011* ATAPI CD
Boot0012* PXE BOOT
Boot0013* USB CD
Boot0014* USB FDD
Boot0015* NVMe0
Boot0016* NVMe1
Boot0017* ATA HDD0
Boot0018* ATA HDD1
Boot0019* USB HDD
Boot001A* LENOVO CLOUD
Boot001B* Windows Boot Manager

```

And I mounted EFI and here's the top level

```

ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:/$ sudo mount /dev/nvme0n1p1 /efi
ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:/$ ls /efi
ls: cannot open directory '/efi': Permission denied
ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:/$ sudo ls /efi
'$RECYCLE.BIN'   EFI            initramfs-linux-fallback.img       initramfs-linux-zen.img      vmlinuz-linux
 bootmgr         grubfont.pf2   initramfs-linux.img                refind_linux.conf            vmlinuz-linux-zen
 boot_rm         grub_old       initramfs-linux-zen-fallback.img  'System Volume Information'
ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:/$

```

I can tell you with all certainty that vmlinuz-linux-zen is definitely from Arch. I used the Zen kernel.

---

### Post by tea for one on 2023-10-28
In the past, as an experiment, I removed every EFI entry to see what happens.
The UEFI firmware should rebuild the essential entries to allow you to boot.

You still have REFInd USB as a fallback position.

---

### Post by #&amp;thj^% on 2023-10-28
> **tea for one said:**
> In the past, as an experiment, I removed every EFI entry to see what happens.
The UEFI firmware should rebuild the essential entries to allow you to boot.

You still have REFInd USB as a fallback position.
+1 you read my mind
> **kingthrillgore said:**
> Well, here's what efibootmgr says for me:

```

sudo efibootmgr
BootCurrent: 0019
Timeout: 0 seconds
BootOrder: 0002,001B,0001,0013,0014,0015,0016,0017,0018,0019,0012,001A,000C,000D
Boot0001* rEFInd Boot Manager
Boot0002* grub
Boot0003  Setup
Boot0004  Boot Menu
Boot0005  Diagnostic Splash Screen
Boot0006  Lenovo Diagnostics
Boot0007  Regulatory Information
Boot0008  ThinkShield secure wipe
Boot0009  Startup Interrupt Menu
Boot000A  Rescue and Recovery
Boot000B  MEBx Hot Key
Boot000C  Other CD
Boot000D  Other HDD
Boot000E* USBR BOOT CDROM
Boot000F* USBR BOOT Floppy
Boot0010* ATA HDD
Boot0011* ATAPI CD
Boot0012* PXE BOOT
Boot0013* USB CD
Boot0014* USB FDD
Boot0015* NVMe0
Boot0016* NVMe1
Boot0017* ATA HDD0
Boot0018* ATA HDD1
Boot0019* USB HDD
Boot001A* LENOVO CLOUD
Boot001B* Windows Boot Manager

```

And I mounted EFI and here's the top level

```

ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:/$ sudo mount /dev/nvme0n1p1 /efi
ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:/$ ls /efi
ls: cannot open directory '/efi': Permission denied
ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:/$ sudo ls /efi
'$RECYCLE.BIN'   EFI            initramfs-linux-fallback.img       initramfs-linux-zen.img      vmlinuz-linux
 bootmgr         grubfont.pf2   initramfs-linux.img                refind_linux.conf            vmlinuz-linux-zen
 boot_rm         grub_old       initramfs-linux-zen-fallback.img  'System Volume Information'
ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:/$

```

I can tell you with all certainty that vmlinuz-linux-zen is definitely from Arch. I used the Zen kernel.

I'm very familiar with Arch and naming, but I suggest just dump the rEFInd entry should clear up the lions share.

---

### Post by kingthrillgore on 2023-10-28
> **1fallen said:**
> +1 you read my mind


I'm very familiar with Arch and naming, but I suggest just dump the rEFInd entry should clear up the lions share.

Alright. I went and removed rEFInd and some others, cleaned out the kernels, ran grub-install, and a new and shiny option is at the top of the bootorder:

```

sudo efibootmgr
BootCurrent: 0019
Timeout: 0 seconds
BootOrder: 0000,0002,001B,0013,0014,0019,0012,001A,000C,000D
**Boot0000* ubuntu**
Boot0002* grub
Boot0003  Setup
Boot0004  Boot Menu
Boot0005  Diagnostic Splash Screen
Boot0006  Lenovo Diagnostics
Boot0007  Regulatory Information
Boot0008  ThinkShield secure wipe
Boot0009  Startup Interrupt Menu
Boot000A  Rescue and Recovery
Boot000B  MEBx Hot Key
Boot000C  Other CD
Boot000D  Other HDD
Boot000E* USBR BOOT CDROM
Boot000F* USBR BOOT Floppy
Boot0012* PXE BOOT
Boot0013* USB CD
Boot0014* USB FDD
Boot0019* USB HDD
Boot001A* LENOVO CLOUD
Boot001B* Windows Boot Manager

```

But restarting led to an error in the Lenovo firmware that rebuilt the EFI order and removed the Ubuntu entry

```

ckilgore@ckilgore-ThinkPad-X1-Carbon-Gen-8:~$ sudo efibootmgr
[sudo] password for ckilgore:
BootCurrent: 001F
Timeout: 0 seconds
BootOrder: 0000,0019,001A,001B,001C,001D,001E,001F,0020,0021,0022,0023
Boot0000* Windows Boot Manager
Boot0010  Setup
Boot0011  Boot Menu
Boot0012  Diagnostic Splash Screen
Boot0013  Lenovo Diagnostics
Boot0014  Regulatory Information
Boot0015  ThinkShield secure wipe
Boot0016  Startup Interrupt Menu
Boot0017  Rescue and Recovery
Boot0018  MEBx Hot Key
Boot0019* USB CD
Boot001A* USB FDD
Boot001B* NVMe0
Boot001C* NVMe1
Boot001D* ATA HDD0
Boot001E* ATA HDD1
Boot001F* USB HDD
Boot0020* PXE BOOT
Boot0021* LENOVO CLOUD
Boot0022  Other CD
Boot0023  Other HDD
Boot0024* USBR BOOT CDROM
Boot0025* USBR BOOT Floppy
Boot0026* ATA HDD
Boot0027* ATAPI CD

```

I was able to get back in with rEFInd LiveUSB. This is more progress than we've had so far. Should I try boot-repair again and see what it does? Try grub-install again?

---

### Post by #&amp;thj^% on 2023-10-28
No first try to install grub as tea for one showed earlier
```
sudo grub-install /dev/nvme0n1
```

---

### Post by kingthrillgore on 2023-10-28
> **1fallen said:**
> No first try to install grub as tea for one showed earlier
```
sudo grub-install /dev/nvme0n1
```

And that's all she wrote! System now boots Xubuntu and it detected Windows as well. Guess i'll spend the rest of tonight installing all my software.

Thanks again everyone for your help! I owe you. I'll rename the thread (if I can).

---

### Post by #&amp;thj^% on 2023-10-28
> **kingthrillgore said:**
>  I'll rename the thread (if I can).
You owe us nothing, it's how we roll here, And your first post top right corner "Thread Tools" mark as Solved
Have Fun

---

