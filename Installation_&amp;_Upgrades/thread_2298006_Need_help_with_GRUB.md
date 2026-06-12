---
title: "Need help with GRUB"
date: 2015-10-08
forum: Installation &amp; Upgrades
---

### Post by MrFortyOne on 2015-10-08
Hello everyone, recently I've installed Ubuntu along with Windows 8.1 in my new pc, but I'm having some issues with this. Sorry if this is not the correct place to place this, if that is the case, please tell me where do to it :)

Oh, and I'm a bit noobish, so please, be friendly ;)

What I want to do is: Use GRUB2 has a default boot manager when I turn on the pc, and I want it to show only two options there: Ubuntu and Windows 8.1
Currently what happens when I boot the pc is:
The UEFI loads and it goes directly to windows 8.1, in order for me to use Ubuntu I need to go into de UEFI options -> boot -> and select there the Ubuntu, which opens the GRUB2 with the two options I want.
How can I change this so that when I turn the pc on, I get instantly to GRUB2 with those two options only?

One more thing, when in GRUB2 the Windows 8.1 option opens the boot manager of windows instead of directly loading windows 8.1. how do I change that as well?

Thanks all!

---

### Post by oldfred on 2015-10-08
What brand/model computer?
Is Ubuntu installed in UEFI boot mode?

Do not know or understand Windows issue. Did you add entries to BCD? It may work like grub where one entry directly boots, but more than one entry requires you to make a choice.

---

### Post by android4682 on 2015-10-08
> **MrFortyOne said:**
> Hello everyone, recently I've installed Ubuntu along with Windows 8.1 in my new pc, but I'm having some issues with this. Sorry if this is not the correct place to place this, if that is the case, please tell me where do to it :)

Oh, and I'm a bit noobish, so please, be friendly ;)

What I want to do is: Use GRUB2 has a default boot manager when I turn on the pc, and I want it to show only two options there: Ubuntu and Windows 8.1
Currently what happens when I boot the pc is:
The UEFI loads and it goes directly to windows 8.1, in order for me to use Ubuntu I need to go into de UEFI options -> boot -> and select there the Ubuntu, which opens the GRUB2 with the two options I want.
How can I change this so that when I turn the pc on, I get instantly to GRUB2 with those two options only?

One more thing, when in GRUB2 the Windows 8.1 option opens the boot manager of windows instead of directly loading windows 8.1. how do I change that as well?

Thanks all!

Check your Boot sequence in your BIOS and set Ubuntu before Windows that should do the trick if I understand you correctly.

---

### Post by MrFortyOne on 2015-10-08
Hi oldfred!

My PC:
-Intel Core i3 4160 3.6GHz 3MB
Asus H81-Gamer
Asus Geforce GTX960 2GB GDDR5
8Gb ram
120GB SSD
1TB 7200rpm

I'm not entirely sure Ubuntu is in UEFI boot mode, I'm not even sure if I really understand the meaning of that. But when I press delete in pc boot, in the new fancy bios interface, I can launch Ubuntu from there. And when I launch it from there I go to GRUB2.

I did add an Ubuntu entry to BCD at some point, but deleted it after a while. Could that have messed things up? :s

And Hey android4682!

[COLOR=#d3d3d3]In my Boot sequence I've already tried getting Ubuntu on a higher preference level and still nothing :\
[/COLOR]**EDIT2: I managed to get Ubuntu to boot first right to the GRUB2. I wasn't being able to do it because there are two entries for Ubuntu in the boot sequence list, is that normal btw?**

I am really sorry for being so ignorant, I never tried something like this :\


[B]EDIT: So, I just used the reset BCD configuration button and did not enter any entry before rebooting. So... Is it bad?
And how do I add an entry on GRUB2?(I'm using GRUB Customizer)

EDIT3:

More info:

[/B]If i type```
 sudo update-grub2
``` I get :

```
Generating grub configuration file ...
using custom appearance settings
Found background image: /home/aleixo/Downloads/1.jpeg
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
```
and if I type ```
sudo fdisk -l
``` I get:```
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 133525B7-8E5F-4DC0-B19B-E1F2824DC9D1

Device         Start        End    Sectors   Size Type
/dev/sda1       2048     616447     614400   300M Windows recovery environment
/dev/sda2     616448     819199     202752    99M EFI System
/dev/sda3     819200    1081343     262144   128M Microsoft reserved
/dev/sda4  117272576 1933043711 1815771136 865,8G Microsoft basic data
/dev/sda5    1081344   40142847   39061504  18,6G Linux filesystem
/dev/sda6   40142848  117272575   77129728  36,8G Linux filesystem

Partition table entries are not in disk order.
Disk /dev/sdb: 111,8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 48E3E0B6-3DF1-4B0E-BF7B-E4ADA7993DA9

Device         Start       End   Sectors   Size Type
/dev/sdb1       2048    264191    262144   128M Microsoft reserved
/dev/sdb2     264192 218056703 217792512 103,9G Microsoft basic data
/dev/sdb3  218056704 219033599    976896   477M Linux filesystem
/dev/sdb4  219033600 227033087   7999488   3,8G Linux swap

```

How messed up is this?

---

### Post by oldfred on 2015-10-08
That looks correct for UEFI boot with gpt partitioning. That fdisk works to show gpt partitioning is something that only the very newest version of Ubuntu shows. Normally we use parted or gdisk.

Did you have to use nomodeset to boot? Normally with nVidia card you need that until you install the proprietary driver.

---

### Post by MrFortyOne on 2015-10-09
Hey again oldfred, I'm a bit sad about about all this. I did not use the nomodeset to boot, but I guess I will need to, since my HDMI output is not sending audio, and I haven't been able to install nVidia drivers yet, since it says I need to exit the X server and to do so I need to use the ctrl+alt+f1 but I can't see a thing when I use that virtual terminal :( 

My situation besides the problem with the drivers:


I boot up the pc, all smooth until I get to the GRUB2, there I have 2 options:
 The Ubuntu, that works fine although sometimes there's an error of GRUB CUSTOMIZER (I guess it about the resolution) and besides Ubuntu option, I have:
The Windows 8.1 option that goes nowhere and now says "ERROR: can't find command 'inmod'." and "ERROR: disk 'hd0, gpt1' not found."
Before these two errors (that I think are about a bad config in the /etc/grub.d/ custom stuff ) the Windows 8.1 option would only say:

File: \BCD
Status: 0x0000098

How do I fix this whole mess?

EDIT2: I forgot to say Ubuntu launches normally besides the warning from GRUB customizer, but that error doesn't always show up.
EDIT: Huge thanks in advance, I'm a bit hopeless since I've stopped being able to use windows 8.1 in any way :\
**EDIT3: I tried the boot-repair tool again, this is the result : [http://paste.ubuntu.com/12723371/](http://paste.ubuntu.com/12723371/)**

---

### Post by oldfred on 2015-10-09
I do not use grub customizer, although many want a gui or easy way to change things. It also creates its own scripts to modify some things which then can lead to issues.
If you want to remove grub customizer you also have to do a full uninstall/reinstall of grub which you can do with Boot-Repair.

Make sure you only boot in UEFI mode, you do have boot loader in protective MBR for BIOS/CSM boot that will not work.

Grub only boots working Windows, so always best to have a Windows repair flash drive.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

I do not know all the changes grub customizer may have made. And Boot-Repair then has also added some grub menu entries.

Can you directly boot Windows from UEFI or one time boot key? Note that it uses bootmgfw.efi.
```
Boot0006* Windows Boot Manager	HD(2,96800,31800,d54b782d-1e71-4eb2-a136-abf3efe037dd)File(EFIMICROSOFT[COLOR=#ff0000]BOOTBOOTMGFW[/COLOR].EFI)..BO
```


Which Windows boot entry are you using? Boot-Repair backed up bootmgfw.efi as bkpbootmgfw.efi and added boot entries directly to it in 25_custom. See lines starting at 517 in Summary report. Try all the entries with Windows in description.

Boot-Repair used to copy grub's efi boot file into /EFI/Microsoft and rename it to bootmgfw.efi and then you could only boot the "Windows" entry in UEFI which really was grub and only boot Windows form grub menu. But any Windows update overwrote the file with a new Windows file. Now we do not recommend that and have several other work arounds for those systems that only like to boot Windows. But your Asus motherboard should have have that issue.

I have an Asus Z97-ar. I did have to change UEFI from Windows to "Other" and change several UEFI entries (which was under the CSM main entry?) for UEFI only boot.

---

### Post by MrFortyOne on 2015-10-09
Ok, I choose the UEFI only mode options in the CSM menu in the UEFI BIOS and that got my pc "bricked" I hat to disconnect the SATA cables and restore that. I'm ok now.

I also got rid of the GRUB customizer.

About booting windows from the UEFI BIOS, I can't, and there are like 6 or 7 "Windows Boot Manager" entries there --' This is ridiculous I know...


About the "Windows repair flash drive.", how do I do that? The links you provided only explain how to do it from inside the Windows :\ But I have no way of launching my Windows 8.1 copy :\


Where you said > (...) you do have boot loader in protective MBR for BIOS/CSM boot that will not work. what did you mean?
Sorry I don't understand most of techical jargon here :\ Plus my english is not that good

---

### Post by oldfred on 2015-10-09
I only see one entry in UEFI, which you should see in UEFI boot tab, or one time boot key like f10 or f12. I think my Asus uses f8 though.

```
 BootCurrent: 0007
Timeout: 1 seconds
BootOrder: 0000,0006,0007,0003,0004
Boot0000* ubuntu	HD(2,96800,31800,d54b782d-1e71-4eb2-a136-abf3efe037dd)File(EFIubuntushimx64.efi)
Boot0003* Hard Drive 	BIOS(2,0,00)..GO..NO........O.S.T.1.0.0.0.D.M.0.0.3.-.1.E.R.1.6.2.................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .4.Z.5.Y.Q.X.A.F........BO..NO........O.K.I.N.G.S.T.O.N. .S.V.3.0.0.S.3.7.A.1.2.0.G.................>..Gd-.;.A..MQ..L.0.5.2.0.B.6.7.7.5.5.4.0.E.0.A.7. . . . ........BO
Boot0004* CD/DVD Drive 	BIOS(3,0,00)..GO..NO........O.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a.................>..Gd-.;.A..MQ..L.1.S.L.0.8.6.F.E.0.B.1.1.C.Y. . . . . . ........BO
Boot0006* [COLOR=#ff0000]Windows Boot Manager	[/COLOR]HD(2,96800,31800,d54b782d-1e71-4eb2-a136-abf3efe037dd)File(EFIMICROSOFTBOOTBOOTMGFW.EFI)..BO
Boot0007* UEFI: (FAT) KingstonDataTraveler 3.0	ACPI(a0341d0,0)PCI(1c,5)PCI(0,0)USB(0,0)HD(1,1f80,3a9a580,fdd6f4af)..BO


```
Can you boot above Windows entry?

If you are seeing lots of entries that is from grub menu where Boot-Repair added all the efi boot files.
You can edit or remove all entries created by Boot-Repair in 25_custom.
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by MrFortyOne on 2015-10-09
Hey again oldfred! I just ran into another "freeze" in the ASUS "press DEL or F2 to enter UEFI BIOS" for no apparent reason and had to unplug the SATA cable again :( for it to boot.
Also, now if I don't press any key, I just go to GRUB2 and there I can't use the keyboard(but the Ubuntu option is set as default and as soon as it starts booting it the num lock light goes on)
Pretty messed up now, I really need help please :((

About the Windows entries, I do have a ton of them in the UEFI BIOS menu --' but not a single one works...

---

### Post by oldfred on 2015-10-09
My Asus had a fast boot setting. I turned that off so I could easily get into UEFI. Otherwise system would boot so fast you could not get into UEFI or one time boot key to change anything. And if it does not boot then you have issues. Mine had two settings, one cold boot which I kept as normal and warm or reboot which after I had system configured turned on fast boot, but set a 3 second delay.

Have you updated UEFI/BIOS to latest version from Asus? That will reset everything to defaults and besure to change the settings you already changed again. I had to keep a list as I changed a lot.

Some with major issues have to jumper reset pins on motherboard, or remove battery for a bit on motherboard. I have not had to do that. Most users can cold boot but may have to hold power switch with system unplugged to drain all power then reboot.

Post this from terminal in live installer booted in UEFI mode. You may have to install efibootmgr?
sudo apt-get install efibootmgr
sudo efibootmgr -v

Should show same as Boot-Repair's summary report with just one Windows entry in UEFI. If duplicated we should house clean the duplicates out. 

Have you reviewed link in my signature below. It is a lot and much may not apply but good back ground anyway. Then you may understand the details in what I post.

---

### Post by MrFortyOne on 2015-10-10
Hi once again oldfred, I was in the #ubuntu and #windows IRC channels and I was advised to just run the windows 8 repair disk or something like that, I'm not quite sure. Where can I get this Windows boot repair tool? I don't have my windows cd around but I have the key.

And here's the result from sudo  efibootmgr -v

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0033
Timeout: 1 seconds
BootOrder: 0031,002F,0003,002E,0030,0032,0033,0004
Boot0003* Hard Drive     BIOS(2,0,00)..GO..NO........O.S.T.1.0.0.0.D.M.0.0.3.-.1.E.R.1.6.2................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .4.Z.5.Y.Q.X.A.F.......BO..NO........O.K.I.N.G.S.T.O.N. .S.V.3.0.0.S.3.7.A.1.2.0.G...............>..Gd-.;.A..MQ..L.0.5.2.0.B.6.7.7.5.5.4.0.E.0.A.7. . . . .......BO
Boot0004* CD/DVD Drive     BIOS(3,0,00)..GO..NO........O.A.S.U.S. . . . . .D.R.W.-.2.4.F.1.S.T. . . .a................>..Gd-.;.A..MQ..L.1.S.L.0.8.6.F.E.0.B.1.1.C.Y. . . . . . .......BO
Boot002E* Windows Boot Manager    ACPI(a0341d0,0)PCI(1f,2)SATA(0,ffff,0)HD(2,96800,31800,d54b782d-1e71-4eb2-a136-abf3efe037dd)..BO
Boot002F* ubuntu    ACPI(a0341d0,0)PCI(1f,2)SATA(0,ffff,0)HD(2,96800,31800,d54b782d-1e71-4eb2-a136-abf3efe037dd)..BO
Boot0030* Windows Boot Manager    HD(2,96800,31800,d54b782d-1e71-4eb2-a136-abf3efe037dd)File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot0031* ubuntu    HD(2,96800,31800,d54b782d-1e71-4eb2-a136-abf3efe037dd)File(\EFI\UBUNTU\GRUBX64.EFI)..BO
Boot0032* Windows Boot Manager    HD(2,40800,cfb4000,62356c93-d481-4b4d-b912-86e0d78c53a2)File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot0033* UEFI: (FAT) KingstonDataTraveler 3.0    ACPI(a0341d0,0)PCI(1c,5)PCI(0,0)USB(0,0)HD(1,1f80,3a9a580,fdd6f4af)..BO


```

In fact, there are more than one windows Windows Boot Manager entry there, how can I "clean the house"?

---

### Post by oldfred on 2015-10-10
Did you install Windows several times?
The ACPI entries for Ubuntu & Windows probably are BIOS boot and can be deleted.
The Windows boot entries show different GUID. The Ubuntu & Window entries for 30 & 31 have the same drive, GUID so I think those should be the working ones.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

If you boot the 0030 entry of Windows (it will not show that in UEFI boot menu), does it boot Windows, or can you use f8 to get into Windows own internal repair console?

---

### Post by MrFortyOne on 2015-10-10
> **oldfred said:**
> If you boot the 0030 entry of Windows (it will not show that in UEFI boot menu), does it boot Windows, or can you use f8 to get into Windows own internal repair console?

How would I know the 0030 is the one I'm choosing, in the UEFI they all just say Windows Boot Manager there. Also there's one of Ubuntu that doesn't work, and the one that does says P1 Ubuntu. What is that?

BTW, I did not install Windows 8 several times, it came with the pc.

Oh, and thanks oldfred for the support.

---

### Post by oldfred on 2015-10-10
I think they stay in order, so try second one.

Or just try all Windows entries and see what errors you get. I would expect the valid one to work or at least let you then try f8 to get into Windows own internal repair console.

We can also change description if needed with efibootmgr, but never have done that. Normally just deleted & created. 

Probably -b XXXX & -L "new description" options in efibootmgr.
Where -b is change number XXXX and -L is change label/description.
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

