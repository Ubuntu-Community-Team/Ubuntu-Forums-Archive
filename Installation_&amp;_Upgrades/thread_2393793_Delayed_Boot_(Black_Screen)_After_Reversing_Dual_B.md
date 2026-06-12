---
title: "Delayed Boot (Black Screen) After Reversing Dual Boot"
date: 2018-06-08
forum: Installation &amp; Upgrades
---

### Post by jnabasny on 2018-06-08
I had a dual-boot of Windows 10 and Xubuntu 16.04 that worked great. Then, I decided to update Xubuntu to 18.04 by doing a fresh install on that partition. Afterwards, I resized the partitions in GParted to give more room to Ubuntu. Once I did this, I started having a problem with my Windows partition.


The Windows partition wouldn't boot anymore (because of changes to bootloader, it said). So I decided to just delete the Windows partition and merge that hard drive space with my Ubuntu partition. Here is a picture of my current partition arrangement: 

[ATTACH=CONFIG]280040[/ATTACH] 

After this, the bootloader screen changed and removed the Windows option. This is when the problem started: there is now a full minute of black screen between selecting Ubuntu from the grub menu and the Xubuntu splash screen popping up. This lag didn't happen before and I have tried a couple ways to fix it.


Method 1: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?)
I thought it was a grub issue, so I tried using the "Repair" option from my Live Ubuntu USB. The "Repair" option, however, was greyed out because the Live USB autodetected that there was a "Windows Bootloader" on my system. Weird. Since that didn't work, I downloaded the "Boot-Repair" tool and used that. It didn't fix the problem, but it added a few more Windows-related options to my grub menu. I tried one more time using the advanced options of Boot-Repair to purge and reinstall the grub. Here is the latest info on it: [http://paste.ubuntu.com/p/VgwRzrQfc3/](http://paste.ubuntu.com/p/VgwRzrQfc3/)


Method 2: [https://askubuntu.com/questions/760694/really-slow-boot-on-16-04?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/760694/really-slow-boot-on-16-04?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)
I realized that my /etc/fstab file listed the wrong UUID for my swap partition after I had deleted the Windows parition. I updated it, but this didn't fix the problem either.


Does anyone have any other ideas on how to fix this?

---

### Post by oldfred on 2018-06-08
Post these:
       systemd-analyze  
      
 systemd-analyze blame 
    
Your Windows probably did not work as you resized it from gparted. Always resize NTFS from Windows and reboot immediately as it needs to run chkdsk to update size. 

You can delete the /EFI/Microsoft folder.
And delete the UEFI boot entries.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

What brand/model system?
A few are not happy not having a Windows boot entry by description. If that is the case we can use efibootmgr to create a new entry to boot Ubuntu/grub but says "Windows Boot Manager".

---

### Post by jnabasny on 2018-06-09
Thanks for the reply, oldfred! Here is the systemd-analyze output:

```
$ systemd-analyzeStartup finished in 1.907s (firmware) + 3.602s (loader) + 36.941s (kernel) + 30.248s (userspace) = 1min 12.700s
graphical.target reached after 30.241s in userspace
$ systemd-analyze blame
         14.593s systemd-journal-flush.service
         13.936s dev-sda5.device
         11.446s systemd-modules-load.service
         10.618s systemd-udevd.service
          8.632s snap-firefox-85.mount
          6.451s NetworkManager-wait-online.service
          3.687s NetworkManager.service
          3.268s udisks2.service
          3.207s accounts-daemon.service
          3.131s snapd.service
          2.980s ModemManager.service
          2.442s networkd-dispatcher.service
          2.371s grub-common.service
          2.025s thermald.service
          1.815s polkit.service
          1.298s dev-loop2.device
          1.294s dev-loop0.device
          1.293s dev-loop1.device
          1.264s keyboard-setup.service
          1.258s dev-loop3.device
          1.130s nmbd.service
          1.020s plymouth-start.service
           905ms avahi-daemon.service
           768ms systemd-tmpfiles-setup-dev.service
           656ms dev-mqueue.mount
           643ms systemd-remount-fs.service
           615ms sys-kernel-debug.mount
           608ms dev-hugepages.mount
           592ms systemd-fsck@dev-disk-by\x2duuid-1684\x2d71C1.service
           579ms upower.service
           550ms gpu-manager.service
           465ms winbind.service
           440ms smbd.service
           414ms apparmor.service
           386ms wpa_supplicant.service
           355ms binfmt-support.service
           304ms systemd-random-seed.service
           294ms ufw.service
           288ms boot-efi.mount
           266ms systemd-logind.service
           263ms systemd-rfkill.service
           251ms systemd-journald.service
           242ms rsyslog.service
           233ms plymouth-read-write.service
           221ms systemd-resolved.service
           211ms systemd-tmpfiles-setup.service
           202ms lm-sensors.service
           158ms apport.service
           149ms systemd-timesyncd.service
           148ms lightdm.service
           145ms plymouth-quit-wait.service
           124ms bluetooth.service
           124ms speech-dispatcher.service
           110ms systemd-sysctl.service
           106ms systemd-udev-trigger.service
           101ms pppd-dns.service
            98ms setvtrgb.service
            92ms dev-disk-by\x2duuid-127206be\x2debd0\x2d4b59\x2d9721\x2d98d31ca3c60f
            66ms snap-core-4650.mount
            50ms user@1000.service
            47ms kmod-static-nodes.service
            44ms snapd.seeded.service
            42ms snap-firefox-89.mount
            41ms systemd-update-utmp.service
            36ms snap-firefox-97.mount
            31ms snapd.socket
            16ms alsa-restore.service
            16ms hddtemp.service
            11ms kerneloops.service
            11ms sys-kernel-config.mount
             8ms ureadahead-stop.service
             7ms sys-fs-fuse-connections.mount
             7ms systemd-backlight@backlight:intel_backlight.service
             6ms proc-sys-fs-binfmt_misc.mount
             5ms systemd-update-utmp-runlevel.service
             5ms rtkit-daemon.service
             4ms systemd-user-sessions.service
             4ms console-setup.service
...skipping...
           106ms systemd-udev-trigger.service
           101ms pppd-dns.service
            98ms setvtrgb.service
            92ms dev-disk-by\x2duuid-127206be\x2debd0\x2d4b59\x2d9721\x2d98d31ca3c60f
            66ms snap-core-4650.mount
            50ms user@1000.service
            47ms kmod-static-nodes.service
            44ms snapd.seeded.service
            42ms snap-firefox-89.mount
            41ms systemd-update-utmp.service
            36ms snap-firefox-97.mount
            31ms snapd.socket
            16ms alsa-restore.service
            16ms hddtemp.service
            11ms kerneloops.service
            11ms sys-kernel-config.mount
             8ms ureadahead-stop.service
             7ms sys-fs-fuse-connections.mount
             7ms systemd-backlight@backlight:intel_backlight.service
             6ms proc-sys-fs-binfmt_misc.mount
             5ms systemd-update-utmp-runlevel.service
             5ms rtkit-daemon.service
             4ms systemd-user-sessions.service
             4ms console-setup.service

```

I followed your instructions with efibootmgr and deleted all UEFI and Windows entries. There were two Ubuntu entries (0001 and 000A). I would've kept both, but accidentally deleted 0001 (I'll blame that silly mistake on lack of sleep after taking care of a 3-week-old all night). When I booted back into my installed version, I also ran "sudo efibootmgr -c", changed the bootorder, and updated the grub. Here is the original and current boot info:

Original:
```
BootCurrent: 000CTimeout: 2 seconds
BootOrder: 0001,0003,0000,0006,0007,000A,000B,000C
Boot0000* Windows Boot Manager    HD(1,GPT,c35dffd3-c564-4db3-b3c0-3f6e9633591f,0x800,0x82000)/File(\EFI\UBUNTU\GRUBX64.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD(1,GPT,c35dffd3-c564-4db3-b3c0-3f6e9633591f,0x800,0x80bef)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0003* UEFI OS    HD(1,GPT,c35dffd3-c564-4db3-b3c0-3f6e9633591f,0x800,0x82000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0006* Windows Boot Manager    HD(1,GPT,c35dffd3-c564-4db3-b3c0-3f6e9633591f,0x800,0x82000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot0007* Windows Boot Manager    HD(1,GPT,c35dffd3-c564-4db3-b3c0-3f6e9633591f,0x800,0x80bef)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot000A* ubuntu    HD(1,GPT,c35dffd3-c564-4db3-b3c0-3f6e9633591f,0x800,0x80bef)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO
Boot000B* UEFI OS    HD(1,GPT,c35dffd3-c564-4db3-b3c0-3f6e9633591f,0x800,0x80bef)/File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot000C* UEFI: Lexar USB Flash Drive 1100    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x63fda129,0x800,0x1ddb800)..BO
```

Current:
```
BootCurrent: 000ATimeout: 2 seconds
BootOrder: 0000,000A
Boot0000* Linux    HD(1,GPT,c35dffd3-c564-4db3-b3c0-3f6e9633591f,0x800,0x80bef)/File(\EFI\UBUNTU\GRUB.EFI)
Boot000A* ubuntu    HD(1,GPT,c35dffd3-c564-4db3-b3c0-3f6e9633591f,0x800,0x80bef)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO
```

When I restarted, the grub still included the Windows boot options. More importantly, the problem of the delayed boot hasn't changed. I'm running an ASUS F555LA-AB31. Hopefully this information helps.

---

### Post by oldfred on 2018-06-09
Ubuntu normally has two UEFI boot entries. One uses grubx64.efi and the other shimx64.efi.
Shim is for UEFI Secure Boot. Grub only works with Secure boot off. But shim works with secure boot off, so I do not know why both? Or rename shim to grub and be done with it.

If you need proprietary drivers you have to have UEFI secure boot off. But if you must have UEFI Secure Boot then we would have to add the shim entry back in. I have Secure boot off, and normally use shimx64.efi to boot.
Not sure why your 0000 entry is called Linux. And whenever I have tried to rename the entry in UEFI, I find that it still uses the /EFI/ubuntu/grub.cfg to boot. Or rename does not really work.

To remove Windows entries in grub, you just need to update grub menu. It previous found Windows and added it to menu. An update then will not find Windows and not add it to menu.
sudo update-grub

Similar model Asus need another boot parameter.
       Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[URL="https://ubuntuforums.org/showthread.php?t=2327570"]https://ubuntuforums.org/showthread.php?t=2327570
      [/URL]
 Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive) 
    

First experiment with boot parameters while booting. Replace or add at quiet splash on Linux line.
Then if parameter works we add it permanently to grub, so every time menu is updated it adds that entry.

For permanet change add after the quiet splash. Then run sudo update-grub to add to menu.
       sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
[https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel. 
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only. 
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".      [URL="https://ubuntuforums.org/showthread.php?t=2327570"]
[/URL]

---

### Post by jnabasny on 2018-06-09
"Linux" was the default name of the 0000 boot entry after I used the "sudo efibootmgr -c" command.

I've updated the grub several times over the past couple days as I've been troubleshooting. When I update it, this is what I see:

```
Generating grub configuration file ...Found linux image: /boot/vmlinuz-4.15.0-22-generic
Found initrd image: /boot/initrd.img-4.15.0-22-generic
Found linux image: /boot/vmlinuz-4.15.0-20-generic
Found initrd image: /boot/initrd.img-4.15.0-20-generic
Adding boot menu entry for EFI firmware configuration
done
```

But when I boot up, this is what I see:

[IMG]https://photos-2.dropbox.com/t/2/AACzZK_VPTXCa5yMsD-ZthvhpeQcxu_JYj3S98Rp8_Oy8g/12/154321484/jpeg/32x32/1/_/1/2/Photo%20Jun%2009%2C%2011%2050%2034%20AM.jpg/EIqR-3UYgRUgBygH/rNxCpEmgApf5_mVhAlBs0uwotGjjK9gS9DUN13cTTks?size=2048x1536&size_mode=3[/IMG]
[IMG]https://www.dropbox.com/s/mdmglpu2qm5prnt/Photo%20Jun%2009%2C%2011%2050%2034%20AM.jpg[/IMG]
[IMG]https://www.dropbox.com/s/mdmglpu2qm5prnt/Photo%20Jun%2009%2C%2011%2050%2034%20AM.jpg?dl=0[/IMG]

I experimented with the boot parameters as you recommended. I made sure Secure Boot was disabled (although also tried it once when enabled). I added the "pci=nomsi." I tried with and without "quiet splash." I also played with some of the boot settings in the BIOS, enabling/disabling fast boot and CSM. Without the quiet splash, I was able to see that the system hangs for a significant portion of the time on this line:

```
Begin: Running /scripts/local-premount ...
```

I'm not sure why the grub menu at boot is so different than expected, but maybe this new information will help.

---

### Post by oldfred on 2018-06-09
Generally you want UEFI fast boot off while reconfiguring system. It can be so quick you do not have time to press any key to get into UEFI, UEFI boot menu or even grub if timing on it is set lower than default 10 sec.

Never run the efibootmgr with just the -c parameter. It used total defaults. Default partition for ESP is sda1, but you can change with additional parameters. But now some disks are NVMe or MMC so additional parameters are required for those.
see
man efibootmgr
Typical Ubuntu entry with -L 
       sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number. 

I think your Asus model will require the pci=nomsi, not sure about some of the other suggestions or if any others are now better.

Have you updated UEFI from Asus. Every system needs UEFI updates for         Meltdown and Spectre CPU vulnerabilities. Both Windows & Linux have updated kernels for those issues, but UEFI also requires updates.

---

### Post by jnabasny on 2018-06-09
SUCCESS! 

```
Startup finished in 4.394s (firmware) + 4.965s (loader) + 4.752s (kernel) + 32.373s (userspace) = 46.485sgraphical.target reached after 32.366s in userspace
```

Thanks for all of your help oldfred. I looked into updating my UEFI and it seemed like a major project. Fortunately, after looking around some more, I found a solution that worked without updating the UEFI, here: [https://askubuntu.com/questions/1034359/boot-hangs-for-30-seconds-at-begin-running-scripts-local-premount](https://askubuntu.com/questions/1034359/boot-hangs-for-30-seconds-at-begin-running-scripts-local-premount)

The UUID in the "resume" file was set to my Ubuntu partition instead of the swap partition. I set it to "none," as the instructions say, but once I updated, it replaced "none" with the wrong UUID. I reedited it and put in the UUID for my swap partition, updated, and it finally stuck. As you can see, the boot is much quicker!

---

