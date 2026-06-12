---
title: "Need help in understanding menu options my GRUB2 Menu List"
date: 2018-07-18
forum: Installation &amp; Upgrades
---

### Post by karung on 2018-07-18
There are lots of options in my GRUB2 Menu List
I want to understand what each options stands for and remove the unwanted ones

Following are the details from boot-repair tool.

[http://paste.ubuntu.com/p/yKWczxYfm9/](http://paste.ubuntu.com/p/yKWczxYfm9/)


I am using Ubuntu 18.04 LTS

---

### Post by deadflowr on 2018-07-18
Do you have two listed for Ubuntu and something like eight or nine for Windows?
(Ubuntu's would show one as Ubuntu and the other as Advanced Options (with a few more entries within the Advanced Options menu.)

For Ubuntu each entry represents a bootable linux kernel and then , by default settings, a recovery mode option.
Recovery mode is a minimal configured setup that starts a bare system. allowing for basic troubleshooting without the need to load the full system.

(Ubuntu keeps older kernels as a fail safe, in case a new one has problems)
You can remove them usually through Ubuntu's software package management system, apt.
(new Ubuntu releases allow removal of older kernels through software updater
like so
[ATTACH=CONFIG]280447[/ATTACH]
(see how it lists an option to remove unused kernels.)

You can also run a simple terminal command to remove
```
sudo apt autoremove
```
which will also clear out those older kernels.

(There are several other methods to remove older kernels, these two are probably the simplest)

Whatever you do, never try to manually delete kernels.
As that can cause grief with the package management system.


As to the Windows entries, those are simply what grub found doing it's probing.
Ubuntu won't do anything about those. And shouldn't, you would need to do any settings involving those entries on Windows, imo.

Theoretically what you can do to not show those entries is to disable grub's os-prober
and turn off the executable bit for the custom files the Windows entries are associated with.
But since you only have a single hard drive, that isn't the best option, since disabling those would leave you without access to windows at all.

(If you had Windows and Ubuntu on separate hard drives then you could disable os-prober et al, and then bios boot between each, by selecting different hard drives to boot at machine startup.
But that's only an option when you have more than one hard drive, which you do not)


Last, as i tend to forget this, would be entries for memtest.
It is exactly what it sounds like it is, an entry to start a memory testing utility.
This allows you to run diagnostic checks on the memory used by the system.
you can turn that off if you like by removing the memtest package:
[https://askubuntu.com/questions/608632/how-can-i-remove-memtest-from-boot-menu]("https://askubuntu.com/questions/608632/how-can-i-remove-memtest-from-boot-menu")
or by disabling it.

That's my random rambling two cents

make any sense?

---

### Post by oldfred on 2018-07-18
Report says you have UEFI Secure boot on. And it says Windows is hibernated or its fast start up is on.

Grub only boots working Windows or Windows that is not hibernated.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Then with UEFI systems you have multiple boot managers or menus. Grub is both a boot manager & boot loader, UEFI has a boot manager & Windows BCD is a boot mananger, but it only normally shows Windows.

You also ran Boot-Repair and when it sees extra .efi boot files in the ESP - efi system partition it creates a new grub script 25_custom with all those extra .efi boot files as boot options in grub. Most turn off 25_custom or significantly edit it to exclude most options.

       
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also or you can also turn off execute bit on 25_custom
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 

    
 You also show multiple Ubuntu entries in UEFI boot menu. And only one of them is using shimx64.efi which is grub's Secure Boot version. And normal installs just have one shim & one grub Ubuntu entry.
You can delete all the duplicate ubuntu entries in UEFI menu.

This shows the UEFI entries, as it is shown in Boot-Repair's report.
      
 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr) 
        
This says you booted with 0008 which is grub entry. I would not expect that to work if Secure Boot is on?
```
 BootCurrent: 0008
Timeout: 10 seconds
BootOrder: 0001,0008,0000,0007,0006,0005,0004,0003,0002,2001
Boot0000* Windows Boot Manager    HD(3,GPT,50015823-05f0-49c2-91eb-9146d0a2403b,0x363800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* ubuntu    HD(3,GPT,50015823-05f0-49c2-91eb-9146d0a2403b,0x363800,0x82000)/File(EFIubuntu[COLOR=#ff0000]shimx64[/COLOR].efi)
Boot0002* Ubuntu    HD(3,GPT,50015823-05f0-49c2-91eb-9146d0a2403b,0x363800,0x82000)/File(EFIubuntu[COLOR=#ff0000]grubx64[/COLOR].efi)RC
Boot0003* Ubuntu    HD(3,GPT,50015823-05f0-49c2-91eb-9146d0a2403b,0x363800,0x82000)/File(EFIubuntugrubx64.efi)RC
Boot0004* Ubuntu    HD(3,GPT,50015823-05f0-49c2-91eb-9146d0a2403b,0x363800,0x82000)/File(EFIubuntugrubx64.efi)RC
Boot0005* Ubuntu    HD(3,GPT,50015823-05f0-49c2-91eb-9146d0a2403b,0x363800,0x82000)/File(EFIubuntugrubx64.efi)RC
Boot0006* Ubuntu    HD(3,GPT,50015823-05f0-49c2-91eb-9146d0a2403b,0x363800,0x82000)/File(EFIubuntugrubx64.efi)RC
Boot0007* Ubuntu    HD(3,GPT,50015823-05f0-49c2-91eb-9146d0a2403b,0x363800,0x82000)/File(EFIubuntugrubx64.efi)RC
Boot0008* Ubuntu    HD(3,GPT,50015823-05f0-49c2-91eb-9146d0a2403b,0x363800,0x82000)/File(EFIubuntugrubx64.efi)RC
Boot2001* EFI USB Device    RC 

    

```
The two red entries (scroll right) are normal. All the other Ubuntu entries with grub look like duplicates.

---

### Post by karung on 2018-07-19
Thanks for your response, I am trying out the suggestions meanwhile,
following is the image of the GRUB Menu which I want to clean-up.

[https://photos.app.goo.gl/y92PCEQji9o9uuoGA](https://photos.app.goo.gl/y92PCEQji9o9uuoGA)

Thanks,
Karun.

---

### Post by oldfred on 2018-07-19
Half those are in 25_custom which you may or may not want.

Even simpler is to manage grub menu yourself.
       Configuring the Boot Menu in Ubuntu - Boot Order in grub
[http://www.psychocats.net/ubuntu/bootmenu](http://www.psychocats.net/ubuntu/bootmenu)
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

I have several installs of Ubuntu, so os-prober finds too much. So I turn off os-prober and only add entries I want to 40_custom. Similar to 25_custom that Boot-Repair created.

---

### Post by karung on 2018-07-22
Thanks again for your help.
yes, most of unwanted options were in 25_custom created by Boot-Repair, 
removing the execute permission for this file and running update-grub solved the issue

---

