---
title: "Dual boot Windows 8.1 and Ubuntu 14.10, no GRUB"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by DeepSilenceSSN on 2015-03-01
I have been trying to fix this pproblem for a week now. I installed Ubuntu on a new partition, but Windows is the only thing that will boot. I don't rvrn know what the GRUB menu looks like because I have never seen it. I have disabled fast boot and secure boot, and I ran boot repair, which generated the following link:

[http://paste.ubuntu.com/10486579/](http://paste.ubuntu.com/10486579/)

Can someone help me out? I have one day to get this working before I am remote and away from internet for a month. What am I doing wrong?

---

### Post by oldfred on 2015-03-01
Not sure what you have done? You show grub in your NTFS partition sda4:
>      Boot files:        /grub2/grub.cfg /bootmgr /Windows/System32/winload.exe 
                       /grub2/i386-pc/core.img


Looks like a BIOS type install of grub to Windows partition?

What model Toshiba?
You are per UEFI standards supposed to be able to boot any UEFI entry:
```
BootOrder: 0003,0005,0004,0001,0000,0002
Boot0000* Windows Boot Manager    HD(2,200800,32000,0e4900fe-53b7-11e3-adbb-0c54a51af203)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* UEFI: IP4 Qualcomm Atheros PCIe Network Controller    ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(MAC(2025642ebb04,0)..BO
Boot0002* [COLOR=#ff0000]ubuntu[/COLOR]    HD(2,200800,32000,0e4900fe-53b7-11e3-adbb-0c54a51af203)File(EFIubuntushimx64.efi)
Boot0003* UEFI: TOSHIBA MQ01ABD100    ACPI(a0341d0,0)PCI(1f,2)SATA(0,ffff,0)HD(2,200800,32000,0e4900fe-53b7-11e3-adbb-0c54a51af203)..BO
Boot0004* UEFI: IP6 Qualcomm Atheros PCIe Network Controller    ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(MAC(2025642ebb04,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0005* UEFI: PNY USB 2.0 FD 1100    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,30,1e78750,c3072e18)..BO
```

But many Vendors are modifying UEFI to only directly boot the Windows entry.

I think you should use Boot-Repair's advanced mode and totally uninstall & reinstall grub, so it is fully configured in the correct place.

And then the work around I have seen many Toshiba users use, is to rename the hard drive boot efi entry bootx64.efi and make it really be grub or shim. Then from UEFI you boot hard drive and that really boots grub.

       Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)


 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies. Your efi partition is sda2 and you have /EFI/Boot folder already. It also looks like Boot-Repair already made a rename of bootx64.efi, but I am not sure what bootx64.efi now is? Did it copy grub or shim already. Check files sizes and let me know if /EFI/Boot/bootx64.efi is the same as either /EFI/ubuntu/grubx64.efi or shimx64.efi?


   sudo mount /dev/sda2 /mnt
#only if not already existing,
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by DeepSilenceSSN on 2015-03-01
I used the advice from [http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818). 

sudo mount /dev/sdaX /mnt
sudo cp /mnt/EFI/Microsoft/Boot/bootmgfw.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi.old             
sudo rm /mnt/EFI/Microsoft/Boot/bootmgfw.efi                                                      
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi
sudo shutdown -r now 


I am thus now in Ubuntu through the GRUB. However, I have now created the problem where I can't load Windows anymore. Everytime I select Windows in the GRUB menu, the screen goes black and it reloads GRUB menu in a never ending cycle. I get the feeling I should not be surprised by that.

Anyway, does anyone know how to fix this issue now? I did still need to use Windows... :-|

---

### Post by oldfred on 2015-03-01
If you rename the Windows boot file,you have to create a new boot stanza to boot the renamed file. It used to be that grub did not create a valid UEFI boot entry, so Boot-Repair renamed Windows efi file & created a new boot stanza to boot the renamed file.
But then Windows updates overwrote it, Grub updates would not be in copy (still an issue) and if grub broke for any reason, you could not boot Windows from UEFI directly.
Now grub finds Windows efi file & creates a valid UEFI boot for it. But if you renamed it to be grub you are just looping back around. 

Much better to not rename Windows efi file, but rename the hard disk boot entry or bootx64.efi. See post #2. And undo rename of Windows that you did.

---

### Post by DeepSilenceSSN on 2015-03-01
I undid my change to the bootfile from post #3 above, then I followed  the terminal commands in post #2 (thank you oldfred!), and now it works!  Thank you, thank you, thank you! I can't tell you how much frustration  this has caused me over the past week, and fixed just in time for my  upcoming departure.

For future reference to anyone else reading  this thread, my computer is a Toshiba Satellite P55-A, 64 bit. I'm going  to mark this thread as closed.

---

### Post by kabir2 on 2015-07-21
Hello, I have the same problem that is mentioned here. I tried to install ubuntu 14.04. Intalation go well but when I restart the computer only windows start. Grub never display. I ran repair-boot and this link was generated [http://paste.ubuntu.com/11914653/](http://paste.ubuntu.com/11914653/)
Also, I tried already the solution posted in this forum, but I am not sure if I applied it correctly.
can someone help me please?

---

### Post by oldfred on 2015-07-21
@kabir2
Usually better to post your own thread as even is similar issue, yours may be different.

Boot-Repair did not post fstab, but does show it found it?
Have you gone into UEFI and in UEFI boot tab chosen the ubuntu entry. Or one time boot entry often using f10 or f12 to get just boot UEFI boot options.

What brand/model system?
You show duplicate Network UEFI boot options, you may want to eliminate the duplicates with efibootmgr. And you have entry 2001 as first in boot order, you want 0001 or 0002 as first. efibootmgr can change boot order if your UEFI does not have that option in boot tab.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

Adds hard drive entry:

 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
sudo efibootmgr -v

      
 You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu entry -- for instance, it might be Boot0001. You'd then type sudo efibootmgr -o 1 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 1,0,4 to use 1, then 0 if that fails, then 4 if both 1 and 0 fail.)

---

