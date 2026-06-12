---
title: "EFI dual boot boots Win 10 first regardless of settings in efibootmgr"
date: 2017-03-11
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2017-03-11
I've been setting up a Win 10 + Ubuntu Xenial dual boot with a prehistoric Intel board (DB43LD) and I chose to enable UEFI boot rather than install to a standard MSDOS partition table so I could brush up on this procedure before I must do so on UEFI only systems. Both the Win 10 and Ubuntu installs went off without a hitch but after installing Ubuntu instead of being greeted with a grub boot menu the box just booted straight to Win 10.

No problem I thought because I can boot to grub if I press F10 during boot to display the BIOS boot menu and select Ubuntu. Both the Ubuntu and Windows boot entries in grub boot just fine so I poked around with efibootmgr after creating a backup of the EFI boot partition, but all looks fine:

```
lance@lance-desktop:~$ sudo efibootmgr
[sudo] password for lance:
** Warning ** : Boot000a is not EFI 1.10 compliant (lowercase hex in name)
** Warning ** : Boot000e is not EFI 1.10 compliant (lowercase hex in name)
** Warning ** : please recreate these using efibootmgr to remove this warning.
BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0002,0003,0000,0001,000E
Boot0000* CD/DVD Drive
Boot0001* Hard Drive
Boot0002* ubuntu
Boot0003* Windows Boot Manager
Boot0009  Hard Drive
Boot000a  CD/DVD Drive
Boot000e* INTERNAL EFI SHELL: WDC WD1600AAJS-60Z0A0
```

I even fiddled around and changed the order just to see what happens and it really doesn't matter, but I set it all back to its original condition. There is nothing in the BIOS to allow changing the boot order so I may just be stuck :( Regardless I thought it couldn't hurt to pick a few other brains for possible solutions. I did run boot repair just in case it might help but the only thing it did was add some unwanted entries in /etc/grub.d/25_custom that I need to clean up:

[http://paste2.org/Bn5t9fzc](http://paste2.org/Bn5t9fzc)

Any ideas would be appreciated.

---

### Post by kansasnoob on 2017-03-11
My memory is toast :redface:

I had the same problem on the same hardware with a Win 8.1 + Ubuntu dual boot:

[https://ubuntuforums.org/showthread.php?t=2264348](https://ubuntuforums.org/showthread.php?t=2264348)

So I'll read that closer and see what I can figure out. Maybe I'll get lucky twice.

---

### Post by RobGoss on 2017-03-11
Hello and welcome, I'll try to help as much as I can with your issue

Let me start out by saying these days dual booting requires a bit more configuring to the **BIOS**, If this machine is newer and has UEFI / BIOS, then that means Windows is installed in UEFI mode, since that's the case **Ubuntu** needs to be installed in the same way **UEFI,** this is the reason you're not greeted with the Grub because you most likely installed Windows in **Legacy**mode and if that is the case the only way to boot in to Ubuntu is by accessing your BIOS and changing it to Legacy

OldFred has some great information on dual booting and **UEFI** this might help you get started [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by oldfred on 2017-03-11
Running Boot-Repair now copies shimx64.efi from /EFI/ubuntu to /EFI/Boot and renames to bootx64.efi. Thread referenced showed manually copying files.

The /EFI/Boot/bootx64.efi is a fallback or hard drive boot entry. Newer UEFI often find that entry. Older UEFI may not work with that entry directly as it was an update to the UEFI standard that allowed use of that entry for internal drive. But that entry is the only way you boot external drives including both the Windows installer and the Ubuntu installer in UEFI mode (obviously bootx64.efi is a different file).

       You can add your hard drive entry to boot fallback file UEFI assumes sda1 as default, if ESP is sda1, you do not need drive & partition options:
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' [COLOR=#ff0000]-d /dev/sdX -p Y[/COLOR]
sdX is drive, Y is efi partition if ESP is not sda1.


   Mine was sda, and ESP is sda1, so I used -p 1 to get this, but did not need to use it:
Boot0001* UEFI hard drive    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\Boot\bootx64.efi) 
The c37xxx number is the GUID of the ESP partition.
You can see that with PARTUUID is GUID for a partition with gpt:
      
 lsblk -o +PARTUUID /dev/sda

---

### Post by kansasnoob on 2017-03-11
The solution ended up being very, very simple :)

I just set the Windows Boot Loader option to inactive:

```
lance@lance-desktop:~$ sudo efibootmgr
[sudo] password for lance: 
Timeout: 5 seconds
BootOrder: 0000,0002,0001,0003,0004
Boot0000* CD/DVD Drive
Boot0001* Hard Drive
Boot0002* ubuntu
Boot0003  Windows Boot Manager
Boot0004  INTERNAL EFI SHELL: WDC WD1600AAJS-60Z0A0
Boot0009  Hard Drive

lance@lance-desktop:~$ sudo efibootmgr -v
Timeout: 5 seconds
BootOrder: 0000,0002,0001,0003,0004
Boot0000* CD/DVD Drive	BBS(CDROM,,0x0)
Boot0001* Hard Drive	BBS(HD,,0x0)
Boot0002* ubuntu	HD(2,GPT,51053c6f-95a4-4bbf-8fba-7241eabfe676,0xe1800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003  Windows Boot Manager	HD(2,GPT,51053c6f-95a4-4bbf-8fba-7241eabfe676,0xe1800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004  INTERNAL EFI SHELL: WDC WD1600AAJS-60Z0A0	PciRoot(0x0)/Pci(0x1f,0x2)/Ata(1,0,0)/HD(2,GPT,51053c6f-95a4-4bbf-8fba-7241eabfe676,0xe1800,0x32000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot0009  Hard Drive	BBS(HD,,0x0)        USB Flash Memory1.00.

```

I had also removed those two bad entries (000a and 000e) just as a matter of housecleaning but that didn't seem to actually effect anything.

Now the machine boots directly to grub and I can boot either Ubuntu or Win 10 from the grub boot menu :guitar:

To set a boot entry active, run:

```
sudo efibootmgr -b <bootnum> -a
```

To set a boot entry inactive, run:

```
sudo efibootmgr -b <bootnum> -A
```

---

### Post by oldfred on 2017-03-11
Grub only boots working Windows.
Or Windows cannot need chkdsk nor have hibernation fast start up on.

Since Windows will turn on fast start up with updates and does occasionally need chkdsk make sure you can still boot Windows directly from UEFI or have a Windows repair flash drive.
Most have said booting Windows from grub does not give enough time to press f8 to get into internal repair console.
A few said after multiple trie, they could get it to work if timing exactly correct or almost at same time as pressing entry in grub.

So if not active can you still choose that from UEFI one time boot key, or does it not show? 
I assume you could in UEFI turn it back on if necessary.

---

### Post by kansasnoob on 2017-03-11
I'd have to set it back active from Ubuntu before I'd be able to boot it directly but that's not really a worry to me. I'm curious to see how things go with some of these newer UEFI only machines, hopefully they'll be more mature in their behavior.

---

