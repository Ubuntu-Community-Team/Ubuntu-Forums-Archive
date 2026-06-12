---
title: "Ubuntu on External HDD, Windows 8.1 on Internal, GNU Grub keeps happening?"
date: 2015-09-01
forum: Installation &amp; Upgrades
---

### Post by glitterandspots on 2015-09-01
Here's what looks like an FAQ, but this is specific to my laptop I guess.

**Model**: Toshiba Satellite C50-C
**Primary OS** (on internal HDD): Windows 8.1
**Secondary OS** (on external HDD): Ubuntu (most recent LTS version)

I installed Ubuntu on a second 500GB partition on my external HDD (WD "My Passport" Ultra 2TB) a few days ago, hoping I could keep my internal HDD free for Windows related things. I basically just installed it so I can do all my activism work on Ubuntu because my country has iffy surveillance laws and (apparently) reason to watch what I do on my laptop. I know Ubuntu is more difficult to get into than Windows for them. Plus I just like it. I've dualbooted before on an older device with Windows 7 and it worked really well for me with no complications, and moved to Ubuntu only for a while there too. Need Windows for college though, so I need to dualboot.

When I boot my laptop with my external HDD plugged in, it goes straight to the Ubuntu "choose where to boot to" screen, which I'm cool with. Sometimes I just wanna use my first partition on my external drive with Windows so that choice is neat. 

When I boot it without my external HDD, hoping to just use Windows, it opens GNU Grub 2.02 (beta?). And I can't for the life of me find a command or set of commands that I understand how to use, or that works.

How do I make GNU Grub make Windows Bootloader happen every time I turn on my laptop without the external HDD plugged in?

(Plain English please, my ability to process information isn't fabulous these days)

Thanks!
Scout

---

### Post by ajgreeny on 2015-09-01
Unfortunately for you, when you install the way you did to a separate drive you need to choose the "Something Else" option at partitioning as that is the only way to ensure that grub is installed on the external disk; the installer by default puts grub on the first internal HDD, as has happened in your case.

For grub to run successfully it needs the root partition of your Ubuntu installation and if the external disk is missing  the grub config files are also missing.

Most importantly you need to restore the Win8.1 boot loader, which you can do either from the Win8 DVD you may have, or from the recovery DVDs you were advised to make when you first ran Windows on the machine.
Before you do that you need to boot to Ubuntu again and run ```
sudo grub-install /dev/sdx
``` where sdx is the external device which you can find that from command ```
sudo blkid -c /dev/null
``` 
You will  also need to put the external drive as first option in your UEFI, so that when it is present it will boot to grub, but if absent the machine will go straight to the Win8 bootloader
If you do not have either of the DVDs I mentioned, I am not sure what alternatives are available to you as I no longer use Windows, so wait for more replies, or search on "Restoring Win 8 bootloader" on the Microsoft web-site to see if you can find it yourself.

I will also probably be helpful to other posters if you can run Boor-Repair from my signature below, and use the boot-info script.  Post back with the pastebin link you get to the report but don't accept the default repair option at this stage.

---

### Post by glitterandspots on 2015-09-01
Thanks ajgreeny!

I did select the "something else" option and followed instructions I'd found on several different sites (that all said the same thing, but didn't mention what to do about grub). 

My laptop came preinstalled with Windows 8, so it didn't come with a recovery disk. I can get into Windows Bootloader when my external HDD is plugged in. 

Will try to run boot-repair when I'm home tonight. Thank you though!

---

### Post by ubfan1 on 2015-09-01
Actually the preinstalled Win 8 machines are UEFI, so the Windows bootloader is just sitting in the EFI partition.  You just need to run efibootmgr and reorder the bootloader order to make grub not run by default on the internal hard disk.  If you can select the external disk to be before the internal disk in boot order, you can copy the ubuntu bootloader, grubx64.efi, to /EFI/Boot/bootx64.efi (or use shimx64.efi as the bootx64.efi if you are running secure boot and just have grubx64.efi in the same directory). Also ensure the /EFI/ubuntu directory is copied over from the internal disk to the external.  That should do it.

---

### Post by glitterandspots on 2015-09-02
So I ran the commands cjgreeny gave me, and got the following: ```

scout@Satellite-C50-C:~$ sudo grub-install /dev/sdb
[sudo] password for scout: 
Installing for x86_64-efi platform.
Installation finished. No error reported.
scout@Satellite-C50-C:~$ sudo blkid -c /dev/null
/dev/sda1: LABEL="WinRE" UUID="5C18676618673DE0" TYPE="ntfs" 
/dev/sda2: LABEL="ESP" UUID="0668-5E5B" TYPE="vfat" 
/dev/sda3: UUID="86E0FBEEE0FBE27B" TYPE="ntfs" 
/dev/sda4: LABEL="TI80186000D" UUID="741272BE12728540" TYPE="ntfs" 
/dev/sda5: LABEL="Recovery" UUID="EECE5184CE51464D" TYPE="ntfs" 
/dev/sdb1: LABEL="My Passport" UUID="F474B7AA74B76DCC" TYPE="ntfs" 
/dev/sdb2: UUID="dd0c82e8-99ab-4c9d-86fb-91cbf321af45" TYPE="swap" 
/dev/sdb3: UUID="a86a562e-f23f-498a-9a38-cb2c00ae151e" TYPE="ext4"
```

I actually have no idea what to do after I've done this though? 

Here's the pastebin after I've run Boot-Repair [http://paste.ubuntu.com/12260107/](http://paste.ubuntu.com/12260107/)

I'm going to reboot in a second and see if I can change the UEFI settings /at all/, but I'm 90% sure they're okay. 

(If this doesn't work, I'll try ubfan1's idea, but I don't totally understand how to do what they're suggesting...?)

EDIT: 
Okay I rebooted and had a look at the boot order, it's HDD/SDD, USB, ODD then LAN. Which should be fine and good. I just need to now make Windows Bootloader definitely happen instead of Grub when I boot without external HDD.

---

### Post by ubfan1 on 2015-09-03
You now have Windows on your hard disk booting with UEFI, and Ubuntu on the external booting legacy -- possible to use, but inconvenient with all the necessary mode switching.  Some reading about UEFI:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by oldfred on 2015-09-03
You actually have a configuration I thought was not possible but have seen others with it and it does sorta work.
Normally UEFI boot uses gpt partitioned drives. Windows requires gpt for UEFI boot and requires MBR(msdos) for BIOS boot.
But Ubuntu can boot from gpt with either UEFI or BIOS if you have an efi partition for UEFI or a bios_grub partition for BIOS boot.

But you have MBR partitions on external drive which should be only for BIOS boot. But Boot-Repair (or installer?) found the ESP - efi system partition on sda which is gpt partitioned. So it installed an UEFI boot loader for the Ubuntu on the MBR drive. In that configuration, external drive cannot be booted without ESP on sda internal drive.

Much better to have external drive booting with BIOS only if you have to keep drive as MBR.

Or convert drive to gpt and install as UEFI install. But that will erase all data and you may not want to do that unless you have all data fully backed up and can easily restore it.

---

