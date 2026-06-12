---
title: "Trouble getting Grub loader to appear"
date: 2016-12-09
forum: Installation &amp; Upgrades
---

### Post by dblakenz on 2016-12-09
[COLOR=#111111][FONT=Ubuntu]Hi there all,

First up I'm new to the world of Ubuntu and Lunix, but I consider myself fairly technically savvy. 
So have just started a web development and of I need to work in Ubuntu most of the time. We have the option to run a Ubuntu via a virtual machine, however I have found the performance to not be that great, and prefered to be able to dual boot it off my laptop (Sony VAIO Pro 13) alongside Windows 10. I have been able to install ubuntu off a live usb without any problems, however I'm struggling to get the grub menu to appear, no matter what I do it just boots straight into Windows 10. I have been scouring the internet  for the last couple of weeks trying to find a solution and get it to show, but have had no luck so far, and so I was hoping for some help here.

Now full disclosure - I should note is that I have previously had Ubuntu (and the grub menu) running on this same laptop a few weeks back - at the time I installed it (just to make sure it would actually work - it did!) and then uninstalled (deleted it) the next day as I wanted to play around with partition sizes and remove the recovery partitions and so figured it would be easy enough to just reinstall again after I'd finished playing around with the partition sizes.... So I have reinstalled it again, but now I cannot get the grub menu to show!

Ok so this is what have I tried so far to resolve it:

[/FONT][/COLOR]
[LIST]
[*][COLOR=#111111][FONT=Ubuntu]Running Boot Repair via a live Ubuntu USB.[/FONT][/COLOR]
[*]In Windows Command Prompt running the following: bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
[*]Turning off secure boot in the BIOS.
[*]Turning off Fastboot in Windows power setting.
[*]Running eufibootmgr to change boot order (Ubuntu not listed - see image below)
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Here is the pastebin results from Boot Repair: [http://paste2.org/YNZJW1fx](http://paste2.org/YNZJW1fx)

Attached are screen captures from eufibootmgr, GParted, and Windows partition manager as well... looks like I have two EFI system partitions which i dont think is normal?

[ATTACH=CONFIG]272629[/ATTACH][ATTACH=CONFIG]272630[/ATTACH][ATTACH=CONFIG]272631[/ATTACH]

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have also tried:
sudo nano /etc/default/grub
and updating this
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to this
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash libata.force=noncq"
however when i run
sudo update-grub
I get the following error: /usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.


I'm pretty much out of ideas, and not really sure what's wrong or what to do next.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][SIZE=2][FONT=arial]
[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by oldfred on 2016-12-09
The /cow is copy on write or your installer. Or you are trying to edit something on installer, not on your install. 

It looks at some point you had installed grub in BIOS boot mode to gpt's protective MBR. Just do not try to boot in BIOS mode as that grub will not work. It is ok as the protective MBR is just used to prevent old partition tools from thinking drive is blank or BIOS boot.

Some vendors have a second FAT32 partition for boot files into recovery mode or other system utilities. As long as only one FAT32 had boot flag or is seen as ESP - efi system partition then should be ok. Not sure if somewhere boot flag got switched or not?

Windows normally boots from this:
/EFI/Microsoft/Boot/bootmgfw.efi  
Windows may boot from this file as it is a copy of the bootmgfw.efi
/EFI/Boot/bootx64.efi 
If you run Boot-Repair it copies above file to this:
/EFI/Boot/bkpbootx64.efi
And then Boot-Repair copies /EFI/ubuntu/shimx64.efi to bootx64.efi.

All UEFI systems now seem to work with the fallback or hard drive boot entry using /EFI/Boot/bootx64.efi.
Sony violates UEFI spec that specifically says not to use Description as part of boot. And only valid description is "Windows Boot Manager". But many work arounds including using the fallback entry which Boot-Repair may have already done.

But you show many "Windows Boot Manager", some using different files.

sudo efibootmgr -v

Embedded in the UEFI entry is the GUID and your entries show three different GUIDs. Not sure which is then correct or if some are for recovery partition. Your sda2's GUID should match some of the entries in the efibootmgr -v.
      
 to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda 

I would houseclean out the incorrect entries. Perhaps keeping one the uses sda1's boot as it may be a Sony recovery.
see
man efibootmgr

      
 Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B 

You should be able to boot into grub using the entry that is this, if Boot-Repair has copied shimx64.efi (you can check file sizes) and entry has correct GUID:

 /File(EFIBootbootx64.efi)

---

### Post by dblakenz on 2016-12-09
Hi oldfred, thanks for coming back to me!

You are right, I agree that my boot entries definitely being cleaned up is probably a good place to start! Although I'm not entirely sure which ones I should keep and which I should delete.

As you suggested I ran sudo efibootmgr -v and lsblk -o +PARTUUID /dev/sda which provided the following output:
[ATTACH=CONFIG]272642[/ATTACH]

```

BootNext: 0010
BootCurrent: 0011
Timeout: 0 seconds
BootOrder: 0011,0009,000B,000A,000C,0008,000E,000D,0000,0007,0005,0010
Boot0000* Windows Boot Manager    HD(2,GPT,d9519a87-c8fc-4e4e-8ccd-e057fe784035,0x82800,0x82000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...s................
Boot0005* Windows Boot Manager    HD(1,GPT,6a367050-36bf-4c50-86e0-97d33778e4ff,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot0007* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x425800,0xea55c4f)/File(\EFI\Boot\bootx64.efi)
Boot0008* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x144800,0xed36fc9)/File(\EFI\Boot\bootx64.efi)
Boot0009* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x425800,0xc98544f)/File(\EFI\Boot\bootx64.efi)
Boot000A* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x144800,0xb2857c9)/File(\EFI\Boot\bootx64.efi)
Boot000B* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x425800,0xb2857cf)/File(\EFI\Boot\bootx64.efi)
Boot000C* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x144800,0xb5667c9)/File(\EFI\Boot\bootx64.efi)
Boot000D* Windows Boot Manager    HD(2,GPT,d9519a87-c8fc-4e4e-8ccd-e057fe784035,0x82800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot000E* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x144800,0xb57f7c9)/File(\EFI\Boot\bootx64.efi)
Boot0010* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x144800,0xc626fc9)/File(\EFI\Boot\bootx64.efi)
Boot0011* UEFI: USB Flash DISK 1100    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x92,0x800,0x78b800)..BO


```

```


NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT PARTUUID
sda      8:0    0 119.2G  0 disk            
&#9500;&#9472;sda1   8:1    0   260M  0 part            6a367050-36bf-4c50-86e0-97d33778e4ff
&#9500;&#9472;sda2   8:2    0   260M  0 part            d9519a87-c8fc-4e4e-8ccd-e057fe784035
&#9500;&#9472;sda3   8:3    0   128M  0 part            2d5c1cbe-8eb6-4272-9ba0-52ede3b18b36
&#9500;&#9472;sda4   8:4    0  90.8G  0 part            f515a722-82c8-494e-8983-9af5d2c0fb95
&#9500;&#9472;sda5   8:5    0    24G  0 part            ac7f3798-78f9-45f6-8433-cd0ec8d4ba9f
&#9492;&#9472;sda6   8:6    0   3.9G  0 part [SWAP]     9fd0edf6-2c54-4261-8876-3a2be78ef033


```

From what I can tell this is how the partitions are linked up to each boot record:
sda1 > Boot0005
sda2 > Boot0000, Boot000D
sda3 > none (although this is just some empty space, not sure where it came from)
sda4 > Boot0007, Boot0008, Boot0007, Boot000A, Boot000B, Boot000C (this is my windows partition)
sda5 > none (unbutu)
sda6 > none (unbutu swap)

Any suggestions on what ones I could clean out and delete?

Thanks again, and let me know if there is any further information I can provide to help!

---

### Post by oldfred on 2016-12-09
It looks like all these with this GUID are invalid.
f515a722-82c8-494e-8983-9af5d2c0fb95

Others are sda1 or sda2

---

### Post by dblakenz on 2016-12-09
Ok, so I deleted anything using f515a722-82c8-494e-8983-9af5d2c0fb95. Its definitely somewhat cleaner, however as soon as I restart a couple reappear Boot0007 and Boot0008. I have tried deleting them multiple times but, but if i restart and use the live usb they are back again as per below:

```

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootNext: 0007
BootCurrent: 000E
Timeout: 0 seconds
BootOrder: 000E,000D,0005,0007,0008,0000
Boot0000* Windows Boot Manager    HD(2,GPT,d9519a87-c8fc-4e4e-8ccd-e057fe784035,0x82800,0x82000)/File(\EFI\ubuntu\shimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...s................
Boot0005* Windows Boot Manager    HD(1,GPT,6a367050-36bf-4c50-86e0-97d33778e4ff,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot0007* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x144800,0xed36fc9)/File(\EFI\Boot\bootx64.efi)
Boot0008* Windows Boot Manager    HD(4,GPT,f515a722-82c8-494e-8983-9af5d2c0fb95,0x144800,0xb57f7c9)/File(\EFI\Boot\bootx64.efi)
Boot000D* Windows Boot Manager    HD(2,GPT,d9519a87-c8fc-4e4e-8ccd-e057fe784035,0x82800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot000E* UEFI: USB Flash DISK 1100    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x92,0x800,0x78b800)..BO

```

```

ubuntu@ubuntu:~$ lsblk -o +PARTUUID /dev/sda
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT         PARTUUID
sda      8:0    0 119.2G  0 disk                    
&#9500;&#9472;sda1   8:1    0   260M  0 part /mnt/boot-sav/sda1 6a367050-36bf-4c50-86e0-97d33778e4ff
&#9500;&#9472;sda2   8:2    0   260M  0 part /mnt/boot-sav/sda2 d9519a87-c8fc-4e4e-8ccd-e057fe784035
&#9500;&#9472;sda3   8:3    0   128M  0 part                    2d5c1cbe-8eb6-4272-9ba0-52ede3b18b36
&#9500;&#9472;sda4   8:4    0  90.8G  0 part /mnt/boot-sav/sda4 f515a722-82c8-494e-8983-9af5d2c0fb95
&#9500;&#9472;sda5   8:5    0    24G  0 part /mnt/boot-sav/sda5 2e804693-b0ca-48c5-b65c-79ef976fffb0
&#9492;&#9472;sda6   8:6    0   3.9G  0 part [SWAP] 

```

Also I believe there should be a boot entry for Unbutu right? But there is still nothing there.

I have tried a fresh install again, but sitll no joy. 
Have also tried running Boot Repair (new paste bin here [http://paste2.org/LYvWGfdh](http://paste2.org/LYvWGfdh)) but that hasn't changed anything, and there is still no Ubuntu showing up after runing efibootmgr.

Any further thoughts? 
Thanks again!

---

### Post by oldfred on 2016-12-09
It will not add an Ubuntu boot entry. Normally grub or Boot-Repair reinstalling all of grub during install uses efibootmgr to add an ubuntu entry.

Do not understand why or how it expects to boot the Windows main partition, unless Sony has some hidden recovery files/folders in that partition. 

If you boot the Windows entry that is 0000, not sure how you tell when booting, does it boot into grub menu or ubuntu? That entry has shimx64.efi, but has some additional Windows stuff in entry?

These are my two entries

```
Boot0000* ubuntu    HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xfa000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0002* UEFI OS    HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xfa000)/File(\EFI\BOOT\BOOTX64.EFI)..BO

```

My ubuntu install added 0000 and another not shown to boot grubx64.efi.
I manually added the UEFI OS and copied shimx64.efi to /EFI/Boot/bootx64.efi for that as a backup entry. That normally is not added by grub, although there are bug reports asking for it to do it, but discussion about whether they should do it or not.

---

### Post by dblakenz on 2016-12-11
Hi again oldfred, thanks again for you help.
So yesterday after trying plenty of things to get this going I thought I would just go all in and delete everything - delete the windows partitions, boot partitions, that random sony partition and then see what happens if I just install ubuntu on its own. Sadly still no luck, tired quite a few things to get it going but it still kept wanting to boot to windows - even using efibootmgr I could still not see and reference to ubuntu - just windows bootmanager, which is weird - but if i ran boot repair it would list it. 
So ended up having to re-installing windows as I just had a bricked laptop at that point. 
After the reinstall of windows I again installed ubutu and again still no luck, just keeps booting to windows. 

Here is the latest pastebin from boot repair: [http://paste2.org/0OgKtwh1](http://paste2.org/0OgKtwh1)
grubx64.efi and shimx64.efi are both clearly there, but again they dont appear on efibootmgr so I cant make them boot first :/
[ATTACH=CONFIG]272665[/ATTACH]
Get the feeling that this isn't going to happen... :(

---

### Post by oldfred on 2016-12-11
I do not understand the 2nd & 3rd Windows boot entries. The GUID is for sda4 or the Windows partition. I can understand them not working, but do not know how or why they are created, probably by Sony's UEFI.

You can try adding these entries. Make sure the bootx64.efi is really a copy of shimx64.efi. You can just check sizes.

       You can add your hard drive entry to boot fallback file:
sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'
sdX is drive, Y is efi partition 
Or for your sda2 as ESP:
sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'
If description has to be Windows even for the fallback entry.
sudo efibootmgr -c -g -d /dev/sda -p 2 -w -L "Windows Boot Manager" -l '\EFI\Boot\bootx64.efi'

But keeping track of which Windows Boot Manager is correct entry becomes difficult.
      sudo efibootmgr -v  
See also 
man efibootmgr

           Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[URL="http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr"]http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr
[/URL]sudo efibootmgr -o 2,1

A lot of these are now older Sony & Ubuntu versions. Have not seen many Sony's recently.
  HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)
 Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
[http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive](http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)
UEFI With encryption but you do not have to and with efi file boot rename
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)
One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)
Sony Vaio  - EFI dualboot Ubuntu 12.04 and Windows 8 in Raid 0 
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)

---

### Post by dblakenz on 2016-12-11
Thanks again for you help on this and for digging up the above resources! 
It's a weird one, but I will read though some of the above and see if I have any success, although probably wont have time until next weekend.
Will let you know if I have any success!

---

### Post by danielbu on 2016-12-25
What worked for me was the solution mentioned in this: [https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/)

---

### Post by MikeCyber on 2016-12-26
No, that doesn't work with the latest Win10 as of yesterday.

---

