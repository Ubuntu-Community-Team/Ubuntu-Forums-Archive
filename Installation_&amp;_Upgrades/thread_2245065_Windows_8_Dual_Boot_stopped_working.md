---
title: "Windows 8 Dual Boot stopped working"
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by UngusOptonline.ne on 2014-09-20
I have a Toshiba C55-A running Win8 and Ubuntu 14.04 on a dual boot. The Grub was working fine until I did a Refresh in Windows. Now the only way into Ubuntu is thru the Advanced startup shutdown from windows and then picking Ubuntu from the list of devices to boot.

Obviously the partition is still there and Ubuntu is still up and running when I boot into it, but how do I get my Grub back?

Tried Boot-Repair several times. The last bug# is 8392032.

Any help much appreciated.

---

### Post by grahammechanical on 2014-09-20
Boot Repair gives us a url link to a pastebin location of the report. It would be useful for us to see that report. Boot Repair also gives a recommended repair. Did you accept the recommended repair or decline? If we do not accept the recommended repair then nothing would be changed.

Have you done anything else such as turning EFI off and legacy on? We need to know if Windows 8 and Ubuntu were both installed in the same mode. Either both EFI or both legacy.

Otherwise I would suggest loading into Ubuntu and running

```
sudo update-grub
sudo grub-install /dev/sda
```

But without seeing the Boot Repair report I cannot be sure if I am giving accurate advice. It is up to you.

Regards.

---

### Post by ubfan1 on 2014-09-20
Windows does like to keep puting itself first, so on my Toshiba I now usually use the F12 key to select HDD, then ubuntu.  On Ubuntu, you can change the bootorder with the efibootmgr program, but understand, that will be the start of a never ending struggle with Windows.

---

### Post by LostFarmer on 2014-09-20
> Tried Boot-Repair several times. The last bug# is 8392032.


Is this your boot repair link  [http://paste.ubuntu.com/8392032/](http://paste.ubuntu.com/8392032/)  ?

---

### Post by UngusOptonline.ne on 2014-09-28
My apologies to the board in taking so long to respond. I have tried boot repair several times and I also tried EasyBCD 2.2, but no luck. My latest Boot Repair report is [http://paste.ubuntu.com/8451332/](http://paste.ubuntu.com/8451332/)

Should I just re-install Ubuntu or is there a way to fix the dual boot?

---

### Post by oldfred on 2014-09-29
As ubfan1 suggests does f12 work?

Many have issues and there are a variety of work arounds. Some better than others on various systems. But Windows will keep trying to be first.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

Many find the rename of bootx64.efi in /efi/boot works. Some find rEFInd works and has nice icons as boot manager, but is another app to maintain. Boot-Repairs renaming of the Windows file works but leads to issues later when Windows does updates. And the added entry to BCD has Windows reset UEFI's boot once entry and does a reboot to boot ubuntu.

---

### Post by UngusOptonline.ne on 2014-09-30
OldFred, thanks for the reply. I'll try the links you posted and post the results in this thread.

F12 brings me to a list of options represented by F1-F10 and none seem to lead the Ubuntu boot.

---

### Post by UngusOptonline.ne on 2014-10-04
OK, so my education in Ubuntu and EFI continues as success still eludes me.

I figured out how to get into the EFI partition in windows using the CLI and Diskpart. It contains 4 folders: 

[U]Boot
Microsoft
Toshiba
Ubuntu[/U]

Microsoft and Toshiba look like copies of one another when you open them. There may be some differences, but a quick look they seem identical.

_Boot _had the Bootx64.efi folder
_Ubuntu _had grubx64.efi, grub.cfg, shimx64.efi, and MokManager.efi

Dual boot was not working, so after reading around the 'net I saw a solution that involved copying the Bootx64.efi file to _Ubuntu_. Tried that. Nothing changed. Same problem, not solved.

Next step I copied the grub.efi and grub.cfg to the _Boot_. Again, nothing change and the problem remained the same.

Should I try and get a new Bootx64 and Grubx64 and shimx64 and copy those in?

---

### Post by ubfan1 on 2014-10-04
Your original /EFI/Boot/bootx64.efi was probably just a copy of the Windows boot manager (bootmgfw.efi?) (look at their sizes to tell).  The /EFI/Boot/bootx64.efi is the default bootloader used on removable media (like usb), so on a hard disk, it shouldn't be used at all, BUT on my Toshiba, I put a copy of the shim.efi there (renamed bootx64.efi) which runs if my first nvram boot choice fails (like trying to boot the grubx64.efi when secure boot is enabled).  Probably pretty machine specific, but yours is a Toshiba too so that's what I'd do.   Leave the grub.cfg in the ubuntu directory, it will be found there whatever runs.
  Now, your nvram choices should include /EFI/ubuntu/grubx64.efi (or shim.efi if you are using secure boot).  The boot order may be listed with the command   sudo efibootmgr -v    along with all the boot choices.  You may also use efibootmgr to change the boot order so the ubuntu entry is first.  Again, become familiar with doing this, because Windows keeps putting itself first, so you will need to periodically reset the boot order.

---

### Post by UngusOptonline.ne on 2014-10-05
The Bootx64 was a copy of bootmgfw. I did what you said and replaced it with the shimx and renmed it to bootx. 

The _Boot_ folder has only the renamed shimx to bootx file.

The _Ubuntu_ folder has the original shimx, bootx, grubx, grub.cfg, and the MokManager.efi

I'm going to give this a try and let u know.

---

### Post by UngusOptonline.ne on 2014-10-07
Well, that didn't work. Do I need original bootx, shimx, grubx files? Any other suggestions?

Thx.

---

### Post by oldfred on 2014-10-07
Several other Toshiba models the rename of bootx64.efi and making that file grub or shim has worked.

 [SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by ubfan1 on 2014-10-08
On a removable media (like USB), the default bootloader will be the /EFI/Boot/bootx64.efi, but on the hard disk, that bootloader (on my older Toshiba S855-5378) is invoked after an nvram choice fails (like when secure boot is on, and I try to boot an nvram choice which has the grubx64.efi instead of the proper shim.efi).  The grub.cfg file may remain in /EFI/ubuntu, but the signed grubx64.efi NEEDS to be in the same directory as the (copy of) shim.efi, so /EFI/Boot needs to contain bootx64.efi (which is a copy of shim.efi) and (the signed) grubx64.efi.
  I usually have an nvram choice which works these days (either shim or grub) since I have turned off secure boot, but when I was running  with it on, the valid nvram entry for shim kept getting deleted (and I cannot blame Windows totally for that), so I was frequently falling back to the bootx64.efi.

---

