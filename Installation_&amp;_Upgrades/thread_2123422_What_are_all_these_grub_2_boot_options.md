---
title: "What are all these grub 2 boot options?"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by Scotsilv on 2013-03-07
I've installed Ubuntu 12.04 (from the British "Linux the Complete Manual" I recently bought at Barnes & Noble) on a new HP P7-1222 that came with Windows 7.  The UEFI business is rearing its head.

Initially Win 7 would not boot with the only option available "Windows Boot UEFI loader", giving an "invalid EFI file path" error, so I downloaded and booted Linux-secure-12.10-64bit and ran boot-repair.

It worked but left me a bunch of options, some of which are obvious, but others not so much.

Can anyone tell me what the options I've labeled as "**WHAT IS THIS?" **are?  Thanks.


Grub2 boot options:

---------------------------

[I]'Ubuntu, with Linux 3.2.0-38-generic' - BOOTS LINUX OK

'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)'

"Previous Linux versions"

"Memory test (memtest86+)"

"Memory test (memtest86+, serial console 115200)"

"Windows UEFI bkpbootmgfw.efi" - **WHAT IS THIS?  IT SEEMS TO ALSO BOOT WIN 7**, **WHY IS IT HERE?**

"Windows Boot UEFI loader"  - **THIS BOOTS WIN 7** **OK**

"EFI/boot/bootx64.efi" - **WHAT IS THIS?**

"EFI/boot/bootx64.efi.efi" - **WHAT IS THIS?**

"Windows 7 (loader) (on /dev/sda3)"  - **THIS STILL DOES NOT WORK, RETURNS TO GRUB SCREEN**
[/I]
---------------------------

I also note that hibernation of Win 7 (full hibernation - I do this and unplug the computer) used to work before Ubuntu installation, but now attempts to wake from hibernation give an error "Windows resume loader cannot come out of hibernation 0xc000009a", and I then have to select the Win option to delete the hibernation file on the next attempt and do a normal boot.

Turning hibernation off & on again via 'powercfg', defrag, etc. make no difference & I've turned hibernation off as an option for now, until and unless a fix exists for this.  Anyone see this before?

---

### Post by oldfred on 2013-03-08
Was computer originally Windows 7. If so you do not have secure boot and Boot-Repair should not have to create the bkp backups of the Windows boot files. With Windows 8 and secure boot some UEFI systems only will boot the Windows boot file. Ubuntu has the Windows UEFI key in shim file so Boot-Repair renames the Windows file to be a backup and lets the UEFI boot the renamed shim file so it thinks it is booting Windows. Then grub  boots the backup Windows file.
If you do not have secure boot, you should be able to directly boot both Windows & Ubuntu without the rename. Boot-Repair can undo the rename.
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

Without details from a run of BootInfo report I am not sure about the other files. Boot-Repair adds an entry for every efi bootable file in your efi partition. Some may be to recovery boot and usually there may be several boot files all going to the same place.

Grub2's os-prober has a bug. That is why Boot-Repair has to create correct efi chain load entries. You can for now turn off the os-prober and eliminate those entries if you want.
      
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

      
 # I add this line to grub configuration or turn off the execute bit on 30_os-prober
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub

All the entries in 25_custom were added by Boot-Repair. You can edit if you want.
      
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/25_custom_backup
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/25_custom_backup
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by Scotsilv on 2013-03-08
Yes, I bought the Win 7 version of the computer and it has no secure boot.  

Any idea why Win 7 cannot now come out of hibernation, once hibernated, and requires normal reboot?  Does that have to do with the rename?

Also - simply - how can Boot-Repair "undo the rename?"

Thanks for any help you can provide.

----

p.s. tested those other options:

[I]
"Windows UEFI bkpbootmgfw.efi" --> boots Windows 7

"Windows Boot UEFI loader" ---> boots Windows 7

"EFI/boot/bootx64.efi"  ---> Brings up 'Windows Boot Manager' screen.   It reports "Windows failed to start, File: \EFI\Microsoft\Boot\BCD, 0xc000000f, error occured while attmpting to read boot configuration data."

"EFI/boot/bootx64.efi.efi" ---> Brings up 'EFI shell environment' with command prompt.[/I]

---

### Post by oldfred on 2013-03-08
I thought this explained it. But I do not know details.
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

Hibernation with dual boot is dangerous. If you do anything to the Windows partition from Ubuntu, it will corrupt hibernation.


 WARNING for Windows 8 Dual-Booters - discusses issues of hibernation
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

### Post by Scotsilv on 2013-03-10
Thanks for all the help.  I've decided to leave the extra Grub entries as they are.  The machine works and boots into both Win 7 and Ubuntu, so I won't fix what's not broken.

Re:  *Hibernation with dual boot is dangerous. If you do anything to the Windows partition from Ubuntu, it will corrupt hibernation.*

The Ubuntu authors seem to have prevented that.

I have another, older BIOS-based "throwdown" machine for experimentation, a Celeron D 352 -based eMachines, on which reside both Win 7 and Ubuntu 12.04 (it was my experimentation with Ubuntu on that machine that led me to buy this faster machine in fact).  It does permit Win 7 hibernation and comes out of hibernation fine...and Ubuntu gives an error message and refuses to mount the Win 7 partition if I try to mount it from file manager - "**Cannot mount windows partition because it is in hibernation**" or words to that effect.   

(I don't know if that can be overridden from the command line, as I never tried.)

If anyone else reading this has the experience of installing Ubuntu 12.04 alongside Win 7 in dual-boot, and then finds Win 7 unable to come out of hibernation after hibernated, please let me know.

p.s. Ubuntu 12.04 and Unity run darn well on the Celeron 352 eMachines which has Intel 945 graphics, 2 Gb DDR2 RAM and an early SATA hard drive!

---

