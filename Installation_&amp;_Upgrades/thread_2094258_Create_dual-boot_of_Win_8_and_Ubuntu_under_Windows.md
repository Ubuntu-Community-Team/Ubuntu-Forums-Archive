---
title: "Create dual-boot of Win 8 and Ubuntu under Windows Boot Manager"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by johnnyluu on 2012-12-13
I've never used ubuntu before. I got interested when I was replacing openSUSE on my granny's new laptop with ubuntu yesterday. I really liked ubuntu's UI and the way it installs applications, so I've decided to install one alongside Windows 8 on my laptop.

I went into a lot of trouble when I was installing ubuntu for my granny, and wasted more than 10 hours trying to figure out the best way to solve the issues without compromising functions, so I want to be more prepared this time. I've started the liveCD many times but haven't pressed the install now button once because I keep noticing issues.

Here are the most troubling issues I found with installing a dual-boot under Windows 8:
1. ubuntu doesn't recognise Windows 8,need to manually set up partitions;
2. can't boot from DVD with UEFI, but can boot from a USB after swithing off secure boot;
3. grub might mess up Windows Boot Manager, need to recover Windows.
4. fast boot (or whatever that's called) doesn't give the option to choose operating systems.

The goal is to create a dual-boot of Windows 8 and ubuntu under Windows Boot Manager without recovering Windows 8, or going through any complicated processes to switch bootloader. After googling for hours, I didn't find anything that solves all the problems, but I think I might make it work by combining some of the solutions. So this is what I intend to do (noted that I don't really understand computers, so it might be ridiculously wrong):

1. download the 12.10 version, which I heard is more compatible with UEFI and secure boot;
2. set up the partitions for ubuntu (some say a EFI partition also is needed, but is quite hard to set up, so I guess I can ignore this step?);
3. run the second option of wubi, which adds a ubuntu option in windows boot manager;
4. boot the liveCD under UEFI,
5. install to the partition for ubuntu, rather than the whole drive (should I choose the swap drive or the other one?), which might solve the grub messing up Win Bootloader issue.
6. go make a cup of coffee as suggested, and pray.
7. turn off fast boot at some point, haven't figured out how.

So specialists, do you think this will work? I'm downloading the 12.10 amd64 version right now. Anyone keen to save me from wrecking my laptop before I start the project? Or is there an easier way to do this? Thanks.

---

### Post by zaiger on 2012-12-13
I'm having basically the same troubles. 

I have both OS's (Ubuntu 12.10 and win8) installed on my EFI x64 machine with secure-boot turned off, but GRUB2 won't boot into Windows8. I tried Boot-repair and I got this output: [http://paste.ubuntu.com/1429657/](http://paste.ubuntu.com/1429657/)

I'd like to be able to use the windows boot manager, but as of right now I have no way to boot into Windows, only Ubuntu.

---

### Post by johnnyluu on 2012-12-13
> **zaiger said:**
> I'm having basically the same troubles. 

I have both OS's (Ubuntu 12.10 and win8) installed on my EFI x64 machine with secure-boot turned off, but GRUB2 won't boot into Windows8. I tried Boot-repair and I got this output: [http://paste.ubuntu.com/1429657/](http://paste.ubuntu.com/1429657/)

I'd like to be able to use the windows boot manager, but as of right now I have no way to boot into Windows, only Ubuntu.
OK, i'll give it a try. Wish me luck!

---

### Post by oldfred on 2012-12-13
If UEFI system you have to install  12.10 64 bit Ubuntu in the same mode Windows was installed in. If a new Windows pre-installed system it will be UEFI so Ubuntu has to also be installed in UEFI. If you upgraded or manually installed or have a newer Windows 7 system it may be in BIOS mode or it could be in UEFI, so you have to know before installing Ubuntu. Boot-Repair can convert a Ubuntu BIOS install to UEFI by uninstalling grub-pc and installing grub-efi.

       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
Grub has a bug in its os-prober. It does not create a correct entry to chain load to Windows. It creates a BIOS type entry when an UEFI type entry is required (if UEFI). But again Boot-Repair can fix it.
       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Grub's standard incorrect entries that will not work are like this:
'Windows ...) (on /dev/sdXY)'


With UEFI every boot manager is equal in the efi partition. Only grub allows chain loading back to Windows. So if you do not want grub as default, you have to go into the UEFI and choose from UEFI which system to boot.

@johnylui
If you have Windows installed and do not have an efi partition, then you are BIOS/MBR not UEFI/gpt. And you have only 4 primary partitions you have MBR. Do not create partitions with Windows as it will convert to dynamic partitioning which is Windows proprietary and does not work with Ubuntu.

---

### Post by johnnyluu on 2012-12-13
> **oldfred said:**
> If UEFI system you have to install  12.10 64 bit Ubuntu in the same mode Windows was installed in. If a new Windows pre-installed system it will be UEFI so Ubuntu has to also be installed in UEFI. If you upgraded or manually installed or have a newer Windows 7 system it may be in BIOS mode or it could be in UEFI, so you have to know before installing Ubuntu. Boot-Repair can convert a Ubuntu BIOS install to UEFI by uninstalling grub-pc and installing grub-efi.
It's pre-installed Windows 8, and the boot manager is installed in UEFI.

> **oldfred said:**
> With UEFI every boot manager is equal in the efi partition. Only grub allows chain loading back to Windows. So if you do not want grub as default, you have to go into the UEFI and choose from UEFI which system to boot.
You're right, the option wubi created in Windows boot manager leads to an error. Have to change the UEFI boot order everytime.

Guess I'll have to use grub 2. The problem now is that wifi's not working for me, and hard drive looks very messy. Guess I'll have to start all over again.

---

### Post by johnnyluu on 2012-12-13
Also, I did install ubuntu under UEFI, but didn't creat a EFI partition, would that cause problem? There was a 500M EFI partition already existed before the installation.

---

### Post by N00b-un-2 on 2012-12-13
simple solution is to install [EasyBCD]("http://neosmart.net/EasyBCD/") on Windows.

---

### Post by N00b-un-2 on 2012-12-13
simple solution is to install [EasyBCD]("http://neosmart.net/EasyBCD/") on Windows.

as for disabling fastboot, I believe the proper way to accomplish this is to disable the hiberfile.sys.  On Windows 8, start an elevated command prompt.  At the Modern UI screen type 'cmd.exe', then right click the cmd icon when it shows up.  Select "run as administrator" down at the bottom of the screen.  The WIndows "smart screen" will probably pop up with a warning.  Just click continue/agree/confirm/whatever the warning says...
then once you are in an elevated cmd.exe prompt, enter the command

```
powercfg /hibernate off
```

then reboot.  Hibernate and Fast Boot will be disabled, which will eliminate NTFS mount errors and constant chkdsk errors when booting OS aside from Windows 8.  The downside is that boot time is marginally increased on Windows, but not terribly so.

---

### Post by johnnyluu on 2012-12-13
> **N00b-un-2 said:**
> simple solution is to install [EasyBCD]("http://neosmart.net/EasyBCD/") on Windows.

I don't think it works for me. It only shows the boot options availble in UEFI, which includes Windows 8 and ubuntu. I need to add window 8 to grub 2 or ubuntu to windows boot manager.

---

### Post by oldfred on 2012-12-13
Not sure if they have updated EasyBCD to work with UEFI, yet. But I do not really see much reason for EasyBCD as a grub entry works.

You can only have one efi partition and it should be large enough for all the boot loaders. None are large. Some systems may want to install the entire kernel and what would normally be in /boot but Ubuntu does not, it just adds grub file which then looks in your install for the rest of grub in the /boot folder or partition. 

Wubi does not work with gpt partitions, so you cannot use wubi with pre-installed Windows 8.

Boot-Repair adds a correct chain entry to Windows.

If you want to add a chain entry manually back to  Windows. see entry on 
Non-Mac x86_64 UEFI specific info
[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)

---

### Post by johnnyluu on 2012-12-14
> **oldfred said:**
> Boot-Repair adds a correct chain entry to Windows.
yeah, I think I'll try boot repair after I fix my wifi issue.

---

