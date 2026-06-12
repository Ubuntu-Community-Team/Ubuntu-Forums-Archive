---
title: "Grub broken after re-installing Ubuntu 16.04"
date: 2016-11-12
forum: Installation &amp; Upgrades
---

### Post by gicanzo on 2016-11-12
As in title, my grub broke after I re-installed Ubuntu 16.04 alongside Windows 10. I do not get the boot loader screen anymore at start-up and windows is automatically started.
I tried to fix this with boot-repair, but I get a message that there was an error and grub is still broken. This is the URL I get:

[http://paste2.org/DVpNMOBs](http://paste2.org/DVpNMOBs)


Thanks in advance for any help

---

### Post by gdesilva on 2016-11-12
Give this a try.....

1. boot off a Ubuntu LiveCD
2. on a terminal run sudo -s to gain root access
3. mount the ubuntu 16.04 partition - mount -t ext4 /dev/sdaX /mnt where X is the partition number of the Ubuntu installation assuming your boot drive is sda.
4. run grub-install --boot-directory /mnt/boot /dev/sda
5. reboot and eject livecd to boot from HDD
6. if you can now get to your Ubuntu installation then, run 'update-grub' and 'update-initramfs -u' commands which should pick up your Windows installation as well.

---

### Post by gicanzo on 2016-11-12
I get the following error when running grub-install --boot-directory /mnt/boot /dev/sda:

Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.

Dunno if this is relevant information, but I am on a UEFI pc (and 64 bit system)

---

### Post by gdesilva on 2016-11-12
Sorry, I should have thought about that. Yes, it is because you are on a UEFI pc. You would need to change the files in the efi partition. I do not have an efi machine so cannot be give exact details but check this out...

[https://linux.die.net/man/8/efibootmgr](https://linux.die.net/man/8/efibootmgr) 

and this...

[http://askubuntu.com/questions/463929/how-to-change-my-boot-efi-mount-partition](http://askubuntu.com/questions/463929/how-to-change-my-boot-efi-mount-partition)

Hope this is useful.

---

### Post by gicanzo on 2016-11-13
I cannot really understand what I should do from the first link you posted. Sorry but I am not an expert, so I kind of need to see what commands exactly I should run.

The second link is not what I need, I think.

Any other suggestions?

---

### Post by gicanzo on 2016-11-13
I also tried to purge and reinstall grub, but boot-repair got stuck in installing kernel... I really don't know what to do.

Please help!

---

### Post by oldfred on 2016-11-13
Your Boot-Repair said this:
```
 Reinstall the grub-efi-amd64-signed of sda6
Installing for x86_64-efi platform.
Installation finished. No error reported. 


```

What brand/model system?

If you go to UEFI boot menu, often f10 or f12 (check manual), can you select ubuntu entry? You actually have two ubuntu entries, one uses shim for secure boot and the other is grub. Both should work with Secure Boot off. But only shim entry will work with Secure boot on, if you add the signed kernel files.

---

### Post by gicanzo on 2016-11-13
> **oldfred said:**
> Your Boot-Repair said this:
```
 Reinstall the grub-efi-amd64-signed of sda6
Installing for x86_64-efi platform.
Installation finished. No error reported. 


```

What brand/model system?

If you go to UEFI boot menu, often f10 or f12 (check manual), can you select ubuntu entry? You actually have two ubuntu entries, one uses shim for secure boot and the other is grub. Both should work with Secure Boot off. But only shim entry will work with Secure boot on, if you add the signed kernel files.

I have a Toshiba L850, if that is what you mean. I don`t see what you mean by selecting ubuntu entry in UEFI boot menu. When I open it, I can only select boot priority between HDD, USB, etc. Isn`t that what`s supposed to show in UEFI boot menu?

Not sure what shim is and what you mean by `two ubuntu entries`, but Secure boot is disabled (and it was already when I installed).

---

### Post by oldfred on 2016-11-13
My old BIOS Toshiba used f12 to get to just a boot menu. I believe newer Toshibas still use f12.
If you are getting into boot priority that would be f2 and into UEFI/BIOS settings.

Most models of Toshiba use same UEFI, with just different hardware options enabled.
Many Toshiba now are like HP & Sony in that they use description as part of UEFI boot. That is specifically not allowed per UEFI. And Canonical has a policy statement against using description. And of course only valid description is "Windows Boot Manager". But there are many work arounds depending on your configuration. Most that dual boot use the fallback or hard drive entry that still works for all systems. That requires copying /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi and booting UEFI:hard drive or similar entry in UEFI, not ubuntu entry. Some have to also add UEFI entry for UEFI:hard drive.

       
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
 	'Use the standard EFI file' in advanced options.     

Older threads where users manually copied files:
       Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair
[/URL]
 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 
      
 Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061) 
    


[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]
[/URL]

---

### Post by gicanzo on 2016-11-13
Oh now I see what you mean. Yes, if I press F12 I get a boot menu and after selecting my HDD I have one entry for Windows and two entries for Ubuntu.

I don't think this is any issue connected to my laptop model. I had this laptop for 4 years and ran many dual boot installs with Windows and Ubuntu alongside each other. Never had a problem with grub. This problem arised just yesterday when I decided to re-install my Ubuntu system.

---

### Post by oldfred on 2016-11-13
Does the ubuntu entry boot into Ubuntu?

How did you have it configured before?

Old versions of Boot-Repair used to rename the Windows .efi boot entry to really be grub's boot entry. But then Windows updates would break grub boot.
So that is not recommended any more.

We have seen where grub incorrect reinstalls on upgrades, but I have not had a problem on any normal updates, even major reinstall of a newer grub.

---

### Post by gicanzo on 2016-11-13
> **oldfred said:**
> Does the ubuntu entry boot into Ubuntu?

How did you have it configured before?

Old versions of Boot-Repair used to rename the Windows .efi boot entry to really be grub's boot entry. But then Windows updates would break grub boot.
So that is not recommended any more.

We have seen where grub incorrect reinstalls on upgrades, but I have not had a problem on any normal updates, even major reinstall of a newer grub.

So as we said before from the UEFI boot loader I have two Ubuntu entries. When I select any of them, they both send me to the purple Grub v2.02 screen where I have 5 entries available:
- Windows UEFI bootmgfw.efi
- Windows Boot UEFI loader
- EFI/ubuntu/fwupc64.efi
- EFI/ubuntu/MokManager.efi
- Windows Boot Manager (on /dev/sda2)

The EFI/ubuntu/fwupc64.efi does nothing, simply reloads the same grub screen. The EFI/ubuntu/MokManager.efi opens a blue page which asks me whether to enter Mok Management, or wait 10 seconds to boot. If I wait for the boot, it redirects me again to the grub screen.

My configuration before was simply a dual boot with Windows 10 and Ubuntu 16.04 and worked smoothly (and I had installed both less than two weeks ago, so I don't think I had an old grub version). Everything I did was re-install Ubuntu 16.04, with the usual procedure, but after install the grub was gone.

---

### Post by oldfred on 2016-11-13
It looks like you have no kernel installed.
Grub menu has not found one.

I would use Boot-Repair's full uninstall reinstall of grub and tick/check install kernel also.

---

