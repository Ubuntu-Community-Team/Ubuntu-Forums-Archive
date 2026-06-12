---
title: "install alongside Win 10"
date: 2021-01-28
forum: Installation &amp; Upgrades
---

### Post by jorgemarmo on 2021-01-28
Hi, 
I'm trying to install Lubuntu 20.04LTS on a HP Pavilion dm1.
The BIOS let me enable Legacy support but it states that if UEFI is available it will only get priority...

I tried to change my win10 from GPT to MBR using EaseUS, I shrunk the NTFS partition and then using the "other" option under Lubuntu Graphic Installer (which I believe is not the same as the Ubuntu one) I partitioned the unallocated space into \ ext4 and swap.... Lubuntu installed and then it didn't boot... anything.... tried to bring back win with bootrec fixmbr and stuff.... nothing

I started all over again (from a working windows 10 UEFI GPT system... is not a fresh win 10 installation, is from an image I would like to keep) I installed Lubuntu again, this time using the graphic installer to shrink the partition (it took loooong) and it installed, and then it rebooted to win 10... no way to access Lubuntu....

I pulled a BootRepairDisk... I let it do its magic, I followed the instructions it gave me... and the system now reboots on Lubuntu, I tried to make grub update as suggested by BootRepair, but no way to bring back Win10...  here is the BootRepair log [http://paste.ubuntu.com/p/Cx74kCcmcZ/](http://paste.ubuntu.com/p/Cx74kCcmcZ/)

I could come back to the original image and do the lubuntu installation again, but I would like to be sure to make it right this time, if you can help me. All the information I've found seems to be for an older version or for Ubuntu (for instance I don't get the same options on the installation "partition" options).

All I want is to have the option for the 2 OS at boot, I don't really care if it is with grub, lilo or even windows as I've seen on some tutorials (that didn't really worked for me...)

---

### Post by Impavidus on 2021-01-28
Keep both systems on UEFI and GPT.

Using UEFI, there will be two bootloaders installed, one for Windows and one for Linux (grub). The Windows bootloader can only boot Windows, but the Linux bootloader can boot both. Make sure FastStartup is disabled in Windows, as otherwise grub won't recognise the Windows system and won't be able to boot it. But even then you can boot both systems by choosing the bootloader in UEFI.

---

### Post by jorgemarmo on 2021-01-28
> **Impavidus said:**
> Keep both systems on UEFI and GPT.

But even then you can boot both systems by choosing the bootloader in UEFI.

I don't get this.... or I'm not able to do this with my BIOS...

---

### Post by yancek on 2021-01-28
First take a look at the boot repair output on line 190 which tells you that the disk is GPT.  If you do an online search, you will find sites similar to the one below at microsoft which tell you that you need to install in UEFI mode if you are using a GPT disk.  If you install windows in UEFI mode, you must also install your Ubuntu/Lubuntu in UEFI mode if you want Grub to be able to boot both.

[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-setup-installing-using-the-mbr-or-gpt-partition-style](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-setup-installing-using-the-mbr-or-gpt-partition-style)

Boot repair shows EFI options so you should be able to access the Boot Options in the BIOS firmware and select either OS.  That won't work until you do a proper EFI install which you do not have now.

---

### Post by tea for one on 2021-01-28
> **jorgemarmo said:**
> I don't get this.... or I'm not able to do this with my BIOS...

To access  Boot Options for HP devices, F9 is the dedicated key to press when powering up the PC

---

### Post by jorgemarmo on 2021-01-28
And how do I "force" lubuntu to install in EFI?
Is it by forcing UEFI instead of UEFI+Legacy when burning the image into the USB with rufus?

---

### Post by tea for one on 2021-01-28
Have you already installed Windows 10 in UEFI mode?
Have you created free space for Lubuntu using Windows tools?

I see Rufus has a couple of options.
I would choose:-
Partition Scheme: [COLOR="#0000FF"]GPT[/COLOR]
Target System: [COLOR="#0000FF"]UEFI[/COLOR]

If you can, then disable Legacy mode in your UEFI set up.

Boot Lubuntu in UEFI mode and you can check that you have booted correctly with this terminal command:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"

```
The important thing to remember is [COLOR="#0000FF"]Boot in UEFI mode = Install in UEFI mode[/COLOR]

More info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by jorgemarmo on 2021-01-28
> **tea for one said:**
> [COLOR=#000000]
Have you already installed Windows 10 in UEFI mode?[/COLOR]
[COLOR=#000000]Have you created free space for Lubuntu using Windows tools?[/COLOR]

Yes, yes.

> **tea for one said:**
> 
The important thing to remember is [COLOR=#0000FF]Boot in UEFI mode = Install in UEFI mode[/COLOR]


quite interesting, I'm going to give it a try forcing rufus to GPT/UEFI

---

### Post by jorgemarmo on 2021-01-28
ok, so I:
- disabled legacy support on BIOS
- re-burned the Lubuntu image forcing rufus to GPT/UEFI
- Re installed Lubuntu, prior to re-install I checked with << [COLOR=#000000][FONT=&amp][ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy" >> and it echoed UEFI
[/FONT][/COLOR][ATTACH=CONFIG]287844[/ATTACH][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][ATTACH=CONFIG]287845[/ATTACH][COLOR=#000000][FONT=&amp]
- now the computer only restarts in Lubuntu.
- I tried sudo update-grub, but still no windows
- F9 on startup gives me this (no windows entry)
[/FONT][/COLOR][ATTACH=CONFIG]287846[/ATTACH]

- Boot repair tell me to create a BIOS-Boot partition >1M unformatted, bios_grub flag, this can be done with Gparted... and then try again
the new boot repair report  [http://paste.ubuntu.com/p/xrn2CvBCbW/](http://paste.ubuntu.com/p/xrn2CvBCbW/)

---

### Post by tea for one on 2021-01-28
In post no. 8, you confirmed that you had installed Windows 10 in UEFI mode, but the report shows:-

[COLOR="#0000FF"]Line 320[/COLOR] LegacyWindows detected

Both Windows 10 and Lubuntu will need to be installed in UEFI mode.

Here is the link again  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by jorgemarmo on 2021-01-28
> **tea for one said:**
> In post no. 8, you confirmed that you had installed Windows 10 in UEFI mode, but the report shows:-

[COLOR=#0000FF]Line 320[/COLOR] LegacyWindows detected

Both Windows 10 and Lubuntu will need to be installed in UEFI mode.

Here is the link again  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

but it was, I checked with msinfo32, and when using windows, Legacy was disabled in Bios, and Secure boot was enabled....
[edit from here down]

on line 176 of previous boot repair log 
[COLOR=#BB4444]Boot0003* Windows Boot Manager	HD(1,GPT,2b5cf397-ff80-4591-88e3-05dcc69c7111,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC

I[/COLOR] have not changed windows since... I just reinstalled Lubuntu.

---

### Post by tea for one on 2021-01-28
The previous boot-repair is not relevant now, I can only point out the situation from your[COLOR="#FF0000"] latest[/COLOR] report in post 9.

Do you have back ups of your data?
If not, back up now with a live Lubuntu session.

Then, reinstall Windows 10 in UEFI mode with GPT.
Double check as much as you can especially:-
[COLOR="#0000FF"]Check via System Information > System Summary > BIOS mode > UEFI[/COLOR]

Then re-install Lubuntu in UEFI mode

---

### Post by jorgemarmo on 2021-01-28
So, I reinstalled everything.
But this time I used the first option "install alongside" (or something like that, so I have no control on the SWAP and ROOT partitions)

[ATTACH=CONFIG]287851[/ATTACH]
[ATTACH=CONFIG]287850[/ATTACH]

So it kind of worked.... the PC boots directly on windows without grub, but I can access grub/lubuntu with F9...

[ATTACH=CONFIG]287849[/ATTACH]

---

### Post by tea for one on 2021-01-28
As you can boot both Windows 10 and Lubuntu, I would be more generous and say that [COLOR="#0000FF"]It does work[/COLOR].

Anyway, I get the impression that you would prefer grub to be available to control the choice of OS?

Please boot into Windows and double check that Fast Start Up (i.e. hibernation) is disabled in Windows settings.

Then boot into Lubuntu and run via the terminal:-
```
sudo update-grub
```

Hopefully, the process will find Window Boot Manager and add it to grub.

Power off the PC and then Power On - Is grub there?

---

### Post by jorgemarmo on 2021-01-29
> **tea for one said:**
> As you can boot both Windows 10 and Lubuntu, I would be more generous and say that [COLOR=#0000FF]It does work[/COLOR].

Anyway, I get the impression that you would prefer grub to be available to control the choice of OS?

Please boot into Windows and double check that Fast Start Up (i.e. hibernation) is disabled in Windows settings.

Then boot into Lubuntu and run via the terminal:-
```
sudo update-grub
```

Hopefully, the process will find Window Boot Manager and add it to grub.

Power off the PC and then Power On - Is grub there?

thank you for your support. 

About the boot, I will keep it like this for a while, then I might change it.

I'll mark this thread as solved.

[edit]

And I have no SWAP.....

---

### Post by jeremy31 on 2021-01-29
Go into BIOS settings system configuration, there might be an OS boot menu that needs to have ubuntu at the top, then press F10 twice, save settings and see if grub is default

---

### Post by tea for one on 2021-01-29
> **jorgemarmo said:**
> And I have no SWAP.....

Does Lubuntu not include a swapfile in a default installation?

You can create a swap partition with the partition editor in a live session.
Alternatively, you can add a swapfile - plenty of tutorials on the internet.

If you are unsure how to do this, I would suggest that you start a new thread with swap in the title.

---

