---
title: "After attempted dual boot with windows no grub"
date: 2017-10-09
forum: Installation &amp; Upgrades
---

### Post by patrick852 on 2017-10-09
I tried boot repair in the live environment and it gave [http://paste.ubuntu.com/25710036/](http://paste.ubuntu.com/25710036/) . When that did not work I tried [https://ubuntuforums.org/showthread.php?t=2052009&p=12246811#post12246811](https://ubuntuforums.org/showthread.php?t=2052009&p=12246811#post12246811) and it also failed.
My computer is a alienware alpha ASM100&#8209;1580 with a Nvidia GeForce [FONT=Roboto]GTX 860M variant.
I have disabled secure boot and fast boot also but it did not help.
In the f2 screen I can view the boot order and ubuntu does not show but windows boot manager does.[/FONT]

---

### Post by oldfred on 2017-10-10
It looks like you still have Windows fast start up on. That is a Windows setting different than UEFI fast boot. Note that Windows updates may turn fast start back on. Grub will not then boot Windows as it is hibernated. Just directly boot Windows from UEFI and turn fast start up off again.
> Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda3 /mnt/boot-sav/sda3


       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Can you from UEFI, using f12(?) for UEFI boot menu boot Ubuntu?
You may need nomodeset until you install the nVidia driver.
       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 
    
 If you can boot, you can install nVidia driver from System Settings, Software & Updates, Additional Drivers tab. 

Or from command line/terminal. Do not install directly from nVidia.
[https://ubuntuforums.org/showthread.php?t=1743535&p=13694956#post13694956](https://ubuntuforums.org/showthread.php?t=1743535&p=13694956#post13694956)

---

### Post by patrick852 on 2017-10-11
Fast startup and hibernation are off and still I do not see grub. When I do f12 it shows a menu that allows me to select ubuntu or windows boot manager and some other settings when I select ubuntu it still just boots windows. Also when I restart in windows holding shift and select use a device I can choose ubuntu or Hard drive but when I select ubuntu it still boots windows. In the f2 screen under boot options I can select windows boot manager, usb storage, ect. but ubuntu is not an option.

---

### Post by oldfred on 2017-10-11
Do you ever get to grub menu?
Or just UEFI boot menu with f12?

If from f12 and Ubuntu entry, it boots Windows it is saying ubuntu entry not bootable and defaulting to next in boot order.

But your entries looks correct.
Have you updated UEFI and SSD firmware? Dells often need that and you are very similar to Dell.

perhaps some clues here?
 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr) 


Do you have UEFI Secure boot on? Boot-Repair original report said it is off.
And to install nVidia driver you will need to have Secure Boot off.

You may need nomodeset when you get to grub menu.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by patrick852 on 2017-10-11
No, I never get to the grub menu. No, I have never updated UEFI or SSD firmware. And secure boot is off.

---

### Post by oldfred on 2017-10-11
Best then to update UEFI & firmware.

---

### Post by patrick852 on 2017-10-11
I updated everything that had an update available. And I went into the live environment and ran boot repair again to see if it would fix the problem and it gave me [http://paste.ubuntu.com/25723704/](http://paste.ubuntu.com/25723704/) and it did not work.
Also when I checked my f2 screen to make sure it did not reset my settings (which it did not) I noticed it was set to boot UEFI with legacy OPROM enabled which I did not change.

---

### Post by oldfred on 2017-10-11
Do not really see anything wrong.
I might try the full uninstall/reinstall of grub2 in Boot-repairs advanced options.

I have seen where Dell's need the legacy on, even when booting in UEFI mode. That is unusual as most systems then only boot in legacy/BIOS/CSM boot mode.

If re-install of grub does not work, then we can try the fallback/hard drive boot entry. 
Boot-Repair has already copied shimx64.efi to /EFI/Boot/bootx64.efi. That is a fallback entry and is the same type of entry used by all external devices for UEFI boot.

       Check entries are there.
sudo efibootmgr -v  

 sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sdX -p Y
sdX is drive, Y is efi partition example for sda2, your ESP is sda1.

 sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sda -p 1

Check entries are there.
sudo efibootmgr -v
Then see if you can boot the UEFI hard drive entry.

---

### Post by patrick852 on 2017-10-12
Grub reinstall did not work, it gave [https://paste.ubuntu.com/25728653/](https://paste.ubuntu.com/25728653/) . When I ran the commands the first gave ```
 BootCurrent: 0006Timeout: 0 seconds
BootOrder: 0000,0006,0001,0004,0005
Boot0000* Windows Boot Manager	HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...&................
Boot0001* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004  Hard Drive 	BBS(HD,,0x0)..GO..NO........O.T.O.S.H.I.B.A. .M.Q.0.1.A.C.F.0.5.0.................>..Gd-.;.A..MQ..L. . . . . . . . . . .6. .R.6.C.L.6.B.T.Q........BO
Boot0005  USB HDD	BBS(9,,0x0)..GO..NO........O.S.a.n.D.i.s.k. .C.r.u.z.e.r. .1...2.6.................>..Gd-.;.A..MQ..L.2.0.0.4.2.6.0.5.6.3.1.3.F.9.6.0.5.8.A.E........BO
Boot0006* UEFI: SanDisk Cruzer 1.26	PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,GPT,53358354-9ca2-4202-b752-9514179d7df7,0x800,0xee83df)..BO
 
``` Second ```
 BootCurrent: 0006Timeout: 0 seconds
BootOrder: 0003,0002,0000,0006,0001,0004,0005
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0002* UEFI hard drive
Boot0004  Hard Drive 
Boot0005  USB HDD
Boot0006* UEFI: SanDisk Cruzer 1.26
Boot0003* Boot0002

``` Final ```
 BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0003,0002,0000,0006,0001,0004,0005
Boot0000* Windows Boot Manager	HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...&................
Boot0001* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0002* UEFI hard drive	HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\Boot\bootx64.efi)
Boot0003* Boot0002	HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\Boot\bootx64.efi)
Boot0004  Hard Drive 	BBS(HD,,0x0)..GO..NO........O.T.O.S.H.I.B.A. .M.Q.0.1.A.C.F.0.5.0.................>..Gd-.;.A..MQ..L. . . . . . . . . . .6. .R.6.C.L.6.B.T.Q........BO
Boot0005  USB HDD	BBS(9,,0x0)..GO..NO........O.S.a.n.D.i.s.k. .C.r.u.z.e.r. .1...2.6.................>..Gd-.;.A..MQ..L.2.0.0.4.2.6.0.5.6.3.1.3.F.9.6.0.5.8.A.E........BO
Boot0006* UEFI: SanDisk Cruzer 1.26	PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,GPT,53358354-9ca2-4202-b752-9514179d7df7,0x800,0xee83df)..BO

``` And when I tried to boot to the hard drive through the f12 screen it also failed and just booted windows.

---

### Post by oldfred on 2017-10-12
Your Ubuntu entry does not look correct. That may be a BIOS/CSM type entry, not sure but have seen it before.

Entry shoud be like the Windows or Boot0002 entry showing drive, GUID & path/file to boot.

Have you tried Boot0002 entry?

---

### Post by patrick852 on 2017-10-13
Yes, I tried to boot Boot0002 and it also failed to boot ubuntu.

---

### Post by oldfred on 2017-10-13
Boot-Repair should have copied shimx64.efi to bootx64.efi so Ubuntu boots.

Please check ESP that /EFI/Boot/bootx64.efi is the same size as /EFI/ubuntu/shimx64.efi, not same as /Microsoft/Boot/bootmgfw.efi.
It might be same as shimx64.efi.

---

### Post by patrick852 on 2017-10-13
bootx64.efi and shimx64.efi are the same size and different from bootmgfw.efi.

---

### Post by oldfred on 2017-10-13
Any UEFI system should boot an entry /EFI/Boot/bootx64.efi as that is considered the fallback or hard drive boot entry. It is also the only entry that works for external devices with UEFI.

And normally Dell (and related systems with similar UEFI) just work. But may need the settings I think you have already changed in UEFI.

---

### Post by patrick852 on 2017-10-14
I think I found what I did wrong, I was looking at the wrong file, the file I was looking at was the EFI folder in the live usb. So I went to my ubuntu install while in the live environment and their was no EFI folder in / I tried ctrl + h but there was still no /EFI folder.

---

### Post by oldfred on 2017-10-14
From a normal install the ESP is hidden as it sets very restrictive permissions.
It is then mounted in /boot/efi.
And the path on the partition is /EFI/ubuntu and /EFI/Boot.
So in an install it is /boot/efi/EFI/ubuntu and normally not accessible. But Boot-Repair changes permissions so it can run updates.

From Live Installer you have to mount the ESP partition often sda1 or sda2.
And then default mounts are in /media/$USER where $USER is your login name.
You can see your user name:
fred@Z170N:~$ echo $USER
fred

The live installer also has /EFI/Boot folder as that is UEFI default for all external devices.

---

### Post by patrick852 on 2017-10-16
Ok, bootx64.efi, shimx64.efi, and bootmgfw.efi are all the same size.

---

### Post by oldfred on 2017-10-16
bootmgfw.efi is the Windows boot file and should not be same size, unless by coincidence.

System may have bootx64.efi as copy of Windows boot file bootmgfw.efi.

But normally Boot-Repair creates a backup of bootx64.efi as bkpbootx64.efi and copies shimx64.efi to bootx64.efi.

I am now confused.

From Live installer mount ESP.

change in terminal to that and post this.
change to /EFI/ubuntu , but you should have /media/$USER/???? before that. ??? may be long UUID.
I like to label partitions, particularly those I only sometimes mount, so then they mount by label.

I mounted my backup and ESP on drive sdb.

```
fred@Z170N:~$ cd /media/fred/ESP_B
fred@Z170N:/media/fred/ESP_B$ ls -l
total 8224
drwxr-xr-x 2 fred fred   32768 Mar  7  2017 EFI
-rw-r--r-- 1 fred fred 8388608 Mar 10  2016 Z170NG5.F4
fred@Z170N:/media/fred/ESP_B$ cd EFI
fred@Z170N:/media/fred/ESP_B/EFI$ ls -l
total 3520
-rw-r--r-- 1 fred fred   72144 Mar  7  2017 fbx64.efi
-rw-r--r-- 1 fred fred     126 Mar  7  2017 grub.cfg
-rw-r--r-- 1 fred fred 1099128 Mar  7  2017 grubx64.efi
-rw-r--r-- 1 fred fred 1168464 Mar  7  2017 mmx64.efi
-rw-r--r-- 1 fred fred 1169992 Mar  7  2017 shimx64.efi



```

---

### Post by patrick852 on 2017-10-21
Ok, sorry it took so long to reply ```
 ubuntu@ubuntu:~/temp$ ls -l
total 12
drwxr-xr-x 3 root root 4096 Oct  9 02:06 boot-repair
drwxr-xr-x 5 root root 4096 Oct  8 23:20 EFI
drwxr-xr-x 2 root root 4096 Sep 30  2016 System Volume Information
ubuntu@ubuntu:~/temp$ cd EFI
ubuntu@ubuntu:~/temp/EFI$ ls -l
total 12
drwxr-xr-x 2 root root 4096 Oct 12 21:34 Boot
drwxr-xr-x 4 root root 4096 Jul 23  2016 Microsoft
drwxr-xr-x 3 root root 4096 Oct  8 23:21 ubuntu

```

---

### Post by oldfred on 2017-10-21
Also post Boot & Ubuntu folders

---

### Post by patrick852 on 2017-10-23
```

ubuntu@ubuntu:~/temp/EFI$ cd Boot
ubuntu@ubuntu:~/temp/EFI/Boot$ ls -l
total 2340
-rwxr-xr-x 1 root root 1224600 Jul 11 01:40 bkpbootx64.efi
-rwxr-xr-x 1 root root 1169992 Oct 12 21:34 bootx64.efi
ubuntu@ubuntu:~/temp/EFI/Boot$ cd ~/temp/EFI
ubuntu@ubuntu:~/temp/EFI$ cd ubuntu
ubuntu@ubuntu:~/temp/EFI/ubuntu$ ls -l
total 3468
drwxr-xr-x 2 root root    4096 Oct  8 23:20 fw
-rwxr-xr-x 1 root root   64352 Oct  8 23:20 fwupx64.efi
-rwxr-xr-x 1 root root     126 Oct 12 21:34 grub.cfg
-rwxr-xr-x 1 root root 1133432 Oct 12 21:34 grubx64.efi
-rwxr-xr-x 1 root root 1168464 Oct 12 21:34 mmx64.efi
-rwxr-xr-x 1 root root 1169992 Oct 12 21:34 shimx64.efi

```

---

### Post by oldfred on 2017-10-23
Well, we have confirmed bootx64.efi is shimx64.efi copy.
It really should boot the hard drive entry in UEFI.
And hold escape right after UEFI/BIOS screen to get to grub menu. Then add nomodeset and/or try second menu item or recovery mode.
Make sure fast boot in UEFI is off. Should not matter if UEFI Secure Boot is on or off, but often better off. And will have to be off to install nVidia drivers.

---

### Post by patrick852 on 2017-10-23
Well, for whatever reason it doesn't.

---

### Post by oldfred on 2017-10-24
What mode are drives in? Should be AHCI, not IDE nor RAID.
Dell often used a RAID or Intel SRT setting that looks like RAID even if one drive.
And update to UEFI, often changes some settings back to defaults, so have to update UEFI setting changes again.

---

### Post by patrick852 on 2017-10-24
It's in AHCI mode.

---

### Post by oldfred on 2017-10-24
I am out of ideas.

---

### Post by patrick852 on 2017-10-25
Well thanks for trying, my only ideas are either to wipe the drive and install ubuntu then reinstall windows and run boot repair to add windows to grub, or maybe reinstall windows in legacy mode and then install ubuntu also in legacy mode. But I am not going to try either, right now at least.

---

### Post by patrick852 on 2017-10-26
Ok, so I went to [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to check if I did anything wrong when I installed ubuntu. I saw [https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_UEFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_UEFI_mode) and ran the command in bash on Ubuntu on Windows and it gave ```
Patrick@JJ:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
Legacy boot on HDD
``` but when I go to the setup menu It says everything is setup to boot in UEFI mode.

---

### Post by oldfred on 2017-10-26
Well that makes a difference.
If you have UEFI hardware, generally better to install in UEFI boot mode.
And if Windows is UEFI which all pre-installed from vendor since Windows 8 are, then you want Ubuntu installed in UEFI boot mode.

Boot-Repair can convert a BIOS install on a gpt partitioned drive to UEFI boot by uninstalling grub-pc (BIOS) and installing grub-efi-amd64 (UEFI). That is in advance mode not any default fix in Boot-Repair.

You technically can dual boot with Windows UEFI & Ubuntu as BIOS boot, but have to only boot from UEFI boot menu. 
And with some systems have to turn on/off UEFI or BIOS/CSM/Legacy settings to match how you are booting install.

---

### Post by patrick852 on 2017-10-27
I don't see anything like that in boot-repair's advanced options menu.

---

### Post by oldfred on 2017-10-27
It is the uninstall grub on one tab and reinstall grub on another tab. You need to boot in UEFI mode.
Only use the ppa, not the ISO which is now old.
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by patrick852 on 2017-10-28
It didn't work, it gave [http://paste.ubuntu.com/25838911/](http://paste.ubuntu.com/25838911/) I made certain purge grub before installing and uninstall grub were both enabled. It installed grub-efi-amd64-signed ect. but when I restarted it didn't show grub, also in the f12 menu ubuntu still did not have UEFI: before it, and ubuntu still did not show in the f2 boot settings menu.

---

### Post by oldfred on 2017-10-28
This says you have an Ubuntu entry:

```
 BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0001,0000,0004,0002,0003
Boot0000* Windows Boot Manager    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...&................
Boot0001* [COLOR=#ff0000]ubuntu[/COLOR]    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(EFIubuntushimx64.efi)
Boot0002* [COLOR=#b22222]UEFI hard drive[/COLOR]    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0003* Boot0002    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004* UEFI: SanDisk Cruzer 1.26    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(2,0)/HD(1,GPT,3b432cf3-a932-4a37-9d6d-5f45cea590be,0x800,0xee83df)..BO 


```

I do not know nor understand the VenHw type UEFI settings. Not sure if just BIOS or if a UEFI hard drive default entry.
You have this entry that should be a hard drive or fallback UEFI boot. Does the UEFI hard drive entry boot this, as Boot-Repair copied shimx64.efi to be that and created the backup.
 /EFI/Boot/bootx64.efi

---

### Post by patrick852 on 2017-10-28
No, it doesn't, I selected ubuntu in the f12 menu and it failed to boot.

---

### Post by oldfred on 2017-10-28
Did you try UEFI hard drive?

And when you say failed to boot, exactly what happened.
Did you get grub menu, or UEFI error? And if grub menu, then you may need other boot parameters.

---

### Post by patrick852 on 2017-10-30
It doesn't seem to allow me to change the hard drive setting. It did not show grub or give an error it just booted into windows.

---

### Post by oldfred on 2017-10-30
Your system should still boot the Hard Drive entry from UEFI menu, even if Ubuntu entry does not work.
That is a fallback entry for backup or emergency boot if main entry does not work.

---

### Post by patrick852 on 2017-10-30
When I select UEFI hard drive in the f12 menu it just boots windows.

---

### Post by oldfred on 2017-10-30
Hard drive entry should be booting this:
/EFI/Boot/bootx64.efi
And Boot-Repair backed up the original and made it a copy of shimx64.efi to boot Ubuntu.

Lets add another hard drive entry:
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'

---

### Post by patrick852 on 2017-10-30
I ran the code, restarted, and there was grub, but when I restarted again there was no grub I tried to boot UEFI hard drive, ubuntu, ect. it just booted windows. Here's what the command outputted.
```
ubuntu@ubuntu:~$ sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
** Warning ** : Boot0002 has same label UEFI hard drive
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0007,0000,0004,0002,0003,0001,0005,0006
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0002* UEFI hard drive
Boot0003* Boot0002
Boot0004* UEFI: SanDisk Cruzer 1.26
Boot0005  Hard Drive 
Boot0006  USB HDD
Boot0007* UEFI hard drive
```

---

### Post by oldfred on 2017-10-31
I think you must have a very bad UEFI from vendor. I thought Alienware was by Dell & Dells normally are pretty good.
But other brands do have UEFI that want to switch only to Windows, but then fallback entry works.

I would contact Alienware. Then may say they only support Windows, so you have to be persistent.

---

### Post by patrick852 on 2017-10-31
I don't think I made it clear what happened. grub was working but when I restarted it was not.

Update: I ran sudo efibootmgr -c -g -w -L "custom" -l '\EFI\Boot\bootx64.efi' to see if it would make a difference and when I restarted I selected ubuntu in grub and I booted into ubuntu and everything was functional, but when I restarted, it booted windows. In the f12 menu I selected custom and it still booted windows.

---

### Post by oldfred on 2017-10-31
That sounds like UEFI is copying bootx64.efi back to the Windows version.
Can you check sizes in ESP of /EFI/Boot/bootx64.efi and compare to Windows bootmgf.efi in /EFI/Microsoft and shimx64.efi in /EFI/ubuntu?
Boot-Repair copies shim to bootx64 for the fallback entry to work.

Do entries in UEFI change from one the works once, to afterwards?
sudo efibootmgr -v

UEFI does have a one time boot entry.
Boot-Repair has at end a suggestion on editing Windows BCD. I believe that reboots to boot Ubuntu using UEFI one time entry.

---

### Post by patrick852 on 2017-10-31
bootx64.efi is 1.2mb I could not find bootmgf.efi but bootmgfw.efi is 1.2mb shimx64.efi is also 1.2mb.

before running sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'
```

BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0000,0004,0001,0007,0002,0005,0006
Boot0000* Windows Boot Manager    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...&................
Boot0001* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0002* custom    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004* UEFI: SanDisk Cruzer 1.26    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,GPT,3b432cf3-a932-4a37-9d6d-5f45cea590be,0x800,0xee83df)..BO
Boot0005  Hard Drive     BBS(HD,,0x0)..GO..NO........O.T.O.S.H.I.B.A. .M.Q.0.1.A.C.F.0.5.0.................>..Gd-.;.A..MQ..L. . . . . . . . . . .6. .R.6.C.L.6.B.T.Q........BO
Boot0006  USB HDD    BBS(9,,0x0)..GO..NO........O.S.a.n.D.i.s.k. .C.r.u.z.e.r. .1...2.6.................>..Gd-.;.A..MQ..L.2.0.0.4.2.6.0.5.6.3.1.3.F.9.6.0.5.8.A.E........BO
Boot0007* UEFI hard drive    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)

```
after in the live environment.
```

BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0003,0000,0004,0001,0007,0002,0005,0006
Boot0000* Windows Boot Manager    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...&................
Boot0001* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0002* custom    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0003* UEFI hard drive    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\Boot\bootx64.efi)
Boot0004* UEFI: SanDisk Cruzer 1.26    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,GPT,3b432cf3-a932-4a37-9d6d-5f45cea590be,0x800,0xee83df)..BO
Boot0005  Hard Drive     BBS(HD,,0x0)..GO..NO........O.T.O.S.H.I.B.A. .M.Q.0.1.A.C.F.0.5.0.................>..Gd-.;.A..MQ..L. . . . . . . . . . .6. .R.6.C.L.6.B.T.Q........BO
Boot0006  USB HDD    BBS(9,,0x0)..GO..NO........O.S.a.n.D.i.s.k. .C.r.u.z.e.r. .1...2.6.................>..Gd-.;.A..MQ..L.2.0.0.4.2.6.0.5.6.3.1.3.F.9.6.0.5.8.A.E........BO
Boot0007* UEFI hard drive    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)

```
after in ubuntu install
```

BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0003,0002,0007,0008,0004,0000,0005,0006
Boot0000* Windows Boot Manager    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...&................
Boot0001* ubuntu    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0002* custom    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot0003* UEFI hard drive    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot0004* UEFI: SanDisk Cruzer 1.26    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,GPT,3b432cf3-a932-4a37-9d6d-5f45cea590be,0x800,0xee83df)..BO
Boot0005  Hard Drive     BBS(HD,,0x0)..GO..NO........O.T.O.S.H.I.B.A. .M.Q.0.1.A.C.F.0.5.0.................>..Gd-.;.A..MQ..L. . . . . . . . . . .6. .R.6.C.L.6.B.T.Q........BO
Boot0006  USB HDD    BBS(9,,0x0)..GO..NO........O.S.a.n.D.i.s.k. .C.r.u.z.e.r. .1...2.6.................>..Gd-.;.A..MQ..L.2.0.0.4.2.6.0.5.6.3.1.3.F.9.6.0.5.8.A.E........BO
Boot0007* Windows Boot Manager    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot0008* ubuntu    HD(1,GPT,30289c20-915d-4c29-9be4-ae3ea974318d,0x800,0xfa000)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO

```
After another restart and booting into the live usb drive it is the same as the first.

---

### Post by oldfred on 2017-10-31
I do not understand the VenHW type entries. Are those BIOS/CSM type. Or do you have a BIOS/CSM install, not UEFI?

The final (after UEFI install) entries you show are the more typical UEFI entries.

---

### Post by patrick852 on 2017-10-31
I think they are UEFI because I do not need Legacy option rom on to boot windows. Also I ran [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" ||  echo "Legacy boot on HDD" in the ubuntu install and it says EFI boot on  HDD.

---

### Post by oldfred on 2017-10-31
Is this similar to yours? They had no issue.
[https://www.reddit.com/r/AlienwareAlpha/comments/3so0ea/going_full_linux_desktop_a_little_feedback/](https://www.reddit.com/r/AlienwareAlpha/comments/3so0ea/going_full_linux_desktop_a_little_feedback/)


This says no drivers required from Dell.
[http://www.dell.com/support/home/us/en/04/product-support/product/alienware-alpha/drivers](http://www.dell.com/support/home/us/en/04/product-support/product/alienware-alpha/drivers)
It also showed last BIOS update as Nov 2016, is that what you have.
There also were firmware drivers for drives.

---

### Post by patrick852 on 2017-11-01
Yes, I think it is similar to mine although they did release the Alienware R2, they did not say which they have. Yes, that is the BIOS version I have and I updated the firmware.

Update: Also I have an HDD, not an SSD I assumed that Alienware would not send out a "gaming" computer with an HDD but I guess I was wrong.

---

### Post by patrick852 on 2018-06-05
[FONT=arial][SIZE=2]I have fixed the problem I updated my BIOS to the latest version then ran this in the Windows command prompt as admin, [/SIZE][/FONT]```
[COLOR=#545454][FONT=Roboto][FONT=arial][SIZE=2]bcdedit[/SIZE][/FONT][/FONT][/COLOR][FONT=arial][SIZE=2][COLOR=#545454] /set {bootmgr} path \EFI\[/COLOR][COLOR=#6A6A6A]**ubuntu**[/COLOR][COLOR=#545454]\grubx64.efi [/COLOR][/SIZE][/FONT]
```[FONT=arial][SIZE=2][COLOR=#545454] then restarted and there was grub, then to find out if Windows would break it like it did earlier, I restarted into Windows and it wanted to run scan disk but I stopped it, and when I restarted again, Windows did not break grub and Ubuntu works fine now.[/COLOR][/SIZE][/FONT]

---

