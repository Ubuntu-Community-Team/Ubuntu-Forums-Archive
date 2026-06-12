---
title: "can't boot to Windows 8 after Ubuntu installation"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by parminides on 2012-11-18
I just bought a a Samsung series 5 Ultra laptop (NP520U4C-A01UB). I was able to disable the secure boot feature in the bios and install Ubuntu 12.04 (as dual boot with Windows eight). Ubuntu works fine, but I can't boot to Windows in Grub. I get the following messages:

```

error: unknown command 'drivemap'
error: invalid EFI filepath

```

Does anyone know how to fix or work around this?

---

### Post by darkod on 2012-11-18
Did you install ubuntu in uefi mode or the older legacy mode?

With uefi boot you actually don't use grub as far as I know. You use the uefi bootloader.

But you have to make sure you install ubuntu in uefi mode, in other words boot the ubuntu cd/usb as uefi device, not as standard bios device.

---

### Post by oldfred on 2012-11-18
If you are booting in UEFI mode, grub-efi has a bug and finds the Windows install, but thinks it still is a BIOS install and creates an incorrect BIOS boot when it should be an efi chain boot entry.

       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

    
You can use Boot-Repair to automatically create the correct entry (or convert from BIOS Ubuntu boot to UEFI boot) or  manually add a UEFI chain load entry.

You can just install into your current Ubuntu, use liveCD or USB or download a full repairCD.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       ```

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```
    
So grub does not add the incorrect entries (you can turn on if reconfiguring in the future with other systems).
       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

    
       Copy above entry into 40_custom:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by parminides on 2012-11-18
I don't know if I installed in uefi or legacy mode. I did what old fred suggested and it worked. Thank you so much.

Specifically, I booted up to an Ubuntu 12.04.1 liveCD and opened a terminal. Then,

```

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

In boot-repair, I did the recommended repair. When it finished, it gave me the url [http://paste.ubuntu.com/1369049/](http://paste.ubuntu.com/1369049/).

There were two new entries in the grub menu,

```

Windows UEFI loader
Windows Boot UEFI boot64.efi

```

which both booted to Windows 8.

The old entries were still in grub,

```

Windows 8 (loader) (on /dev/sda2)
Windows Recovery Environment (loader) (on /dev/sda6)

```

and they still don't work. I can get to the recovery option with the F4 key after powering up, so I'm going to mark the thread solved. But it would be nice to have recovery mode as a grub option if there's an easy fix.

---

### Post by diesousil on 2013-04-01
I tried fix this issue all the week on many forums, but this one is the only post that fix my problem. Thank you so much oldfred :)

---

### Post by ilyesissaoui on 2013-05-21
Hello,
please I have the some prob, and i used boot reapir to fix the prob,
Now I can access to ubuntu (13.04) but windows 8 no!
this is repprt url of boot repair : [http://paste.ubuntu.com/5688390/](http://paste.ubuntu.com/5688390/)
I have Asus k56c 
thanks

---

### Post by oldfred on 2013-05-21
Boot-Repair will not fix internal Windows issues.

It looks like you have installed EasyBCD. It supposedly was updated to work with UEFI. But you should not need it.

Did you turn off hibernatiion in Windows?

Boot-Repair renames the Windows boot file and makes shim be the Windows boot file as many UEFI systems are modified to only boot the Windows efi file. But from grub you should be able to boot Windows. The UEFI menu may only boot the renamed shim.

You have done this. Not sure if you have to or not but second run of Boot-Repair does the rename.
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

You can unrename and see if Windows boots from UEFI/BIOS directly. And you may be able to run Windows fixes.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

Or 

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

But if yours is one that only boots Windows efi file you will have to rename again.

---

### Post by ilyesissaoui on 2013-05-23
Tanks Oldfred,
Yes I have installed EasyBCD,
on booting, if I chose windows 8, it show me this message : error file 'efi/EFI/Boot/bkpbootx64.efi' not found.
however I checked that this file exist.

---

