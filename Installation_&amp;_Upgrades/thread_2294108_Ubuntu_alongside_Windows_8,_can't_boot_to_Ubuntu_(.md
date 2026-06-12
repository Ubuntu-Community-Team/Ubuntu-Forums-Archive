---
title: "Ubuntu alongside Windows 8, can't boot to Ubuntu (14.04)"
date: 2015-09-09
forum: Installation &amp; Upgrades
---

### Post by fede-est on 2015-09-09
First of all, I had this configuration working, but some recent updates to Windows broke it.

When the laptop starts, it boots the Windows Boot Manager (I think, it doesnt exactly say). Which "lets me choose" between Windows 8.1 and Ubuntu (actually XUbuntu but it's the same).

If I select Ubuntu, it gives an error screen saying:

"Windows could not be started. (...)

File: \NST\NeoGrub.mbr
State: 0xc000007b
Information: could not load application or operative system due to a missing or corrupted file."

If I press Esc and then F9 (Boot Device Options) which shows:

"OS boot Manager
ubuntu (...)
Ubuntu (...)
Boot From EFI File"

I dont know why I have two options for Ubuntu (actually I'll make a post later maybe since I've seen some weird stuff in gparted) but if I pick any of those, Grub 2.02 starts and I can choose XUbuntu with no problem.

I ran boot-repair with default configurations, here's the report: [http://paste.ubuntu.com/12324210/](http://paste.ubuntu.com/12324210/)

Nothing changed, and actually, now, on Grub, the list of options is much larger, showing many options which end in ".efi"

The report says at the end:

> [COLOR=#000000]Boot successfully repaired.[/COLOR]
You can now reboot your computer.


The boot files of [COLOR=#666666][[/COLOR]The OS now in use - Ubuntu 14.04.2 LTS[COLOR=#666666]][/COLOR] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition [COLOR=#666666]([/COLOR]EXT4, >200MB, start of the disk[COLOR=#666666])[/COLOR]. This can be performed via tools such as gParted. Then [COLOR=#AA22FF]**select **[/COLOR]this partition via the [COLOR=#666666][[/COLOR]Separate /boot partition:[COLOR=#666666]][/COLOR] option of [COLOR=#666666][[/COLOR]Boot Repair[COLOR=#666666]][/COLOR]. [COLOR=#666666]([/COLOR]https://help.ubuntu.com/community/BootPartition[COLOR=#666666])[/COLOR]

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, [COLOR=#AA22FF]**then **[/COLOR][COLOR=#AA22FF]type [/COLOR]the following [COLOR=#AA22FF]command [/COLOR]in an admin [COLOR=#AA22FF]command [/COLOR]prompt: [COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\u**[/COLOR][COLOR=#000000]buntu[/COLOR][COLOR=#BB6622]**\s**[/COLOR][COLOR=#000000]himx64.efi[/COLOR]

I checked the boot other on the BIOS, but either with OS Boot Manager and HardDrive/USB/etc. its the same as I mentioned before.
I tried running that command on the Windows console, but nothing changes.
I went to do the gparted and the boot partition thing, but when I opened gparted I encountered this:

[IMG]http://s4.postimg.org/8tkq2l43g/Screenshot_090915_20_36_00.jpg[/IMG]

(maybe thats why I have two Ubuntu options in the Boot Device Options menu) and didn't really wanted to screw anything up.



Basically, what can I do to fix this boot issue?

---

### Post by oldfred on 2015-09-09
You have two options because one is grub for standard UEFI and the other is shim for Secure UEFI boot. Shim also then requires signed kernels but should also work with unsigned and secure boot off.

Most HP have needed a work around. Boot-Repair several years ago renamed the Windows efi boot file, but Windows updates regularly overwrote that, so now it just suggests the edit of the BCD.

Most with HP do a different work around to copy grub and/or shim into /EFI/Boot and rename to bootx64.efi and use hard drive boot entry in UEFI. That is a default entry for UEFI.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
Details also in link in my signature.
       
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

           
 HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

You also have 25_custom. That is created by Boot-Repair for all the extra .efi files found in the ESP - efi system partition. But most are just for HP and you do not need them. You can backup and manually delete all the ones you do not want.
       
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

    


[URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL]

---

