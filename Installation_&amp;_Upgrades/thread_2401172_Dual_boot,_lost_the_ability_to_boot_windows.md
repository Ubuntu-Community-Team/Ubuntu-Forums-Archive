---
title: "Dual boot, lost the ability to boot windows"
date: 2018-09-14
forum: Installation &amp; Upgrades
---

### Post by raccoonstrait on 2018-09-14
Hi,

This is weird. I have had no problems with this and have been doing this same behavior for years. Current Xubuntu is 18.04 running on a System76 Bonobo notebook.

Yesterday, as usual, after the usual daily update/upgrade I rebooted to change over to Windows (Flight Simulator fan here) and it didn't work, but booting Xubuntu did. After reading the forums for a while I created a live USB boot disc and followed the instructions for installing and running boot-repair. That worked and I had my Windows session.

Today, again Windows won't boot. Now I did run update-grub this morning, not sure if that had anything to do with anything, but full disclosure and all. So I inserted the USB and opened a live session and re-installed boot-repair and ran it. Windows still won't open.

Here is the link to my pastebin from today's boot-repair session

[https://paste.ubuntu.com/p/F8T2f5RpPY/](https://paste.ubuntu.com/p/F8T2f5RpPY/)

I sure hope someone has some suggestions.

Raccoon Strait

I don't know if this will help, but I have two pastebins from yesterday. This first one is before running boot-repair

[https://paste.ubuntu.com/p/xvV9YQS5zh/](https://paste.ubuntu.com/p/xvV9YQS5zh/)

This second one is after running boot-repair, the one that worked yesterday.

[https://paste.ubuntu.com/p/kXvHxsrCsG/](https://paste.ubuntu.com/p/kXvHxsrCsG/)

---

### Post by oldfred on 2018-09-14
I do not see much.

Boot-Repair only does very minor fixes to Windows. If Windows issues you either have to directly boot from UEFI boot menu, or use your Windows repair flash drive. 
You do have a repair drive for current version of every installed system?

Grub only boots working Windows. Or if Windows needs chkdsk or has turned its fast start up back on, which it does with updates, then grub will not boot Windows. You may be able to boot from UEFI and use f8 to get into internal repair console.

       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by raccoonstrait on 2018-09-14
Hi,

Thanks for your response. The Windows is version 8.1, and updates are turned off (I didn't want to be forced into Win10 as so many reported). The only things that gets updated on the Windows side is Windows Defender along with Intel (which seems to only update the WiFi) and the NVidia drivers, which updated recently, but not yesterday. While I do run the Chrome Browser (which updates itself) the only thing I really do in Windows is run Flight Simulator. I then return to Linux.

It appears that all of the options you list require being in Windows, and the Windows installation came from a network install, if I remember correctly. No I do not have a Windows recovery disk. I will check again, but I believe it is booting from UEFI.

Raccoon Strait

---

### Post by raccoonstrait on 2018-09-14
OK, this is interesting. Windows won't boot from the selections presented (by grub I guess) but when I use F7 (on my system) and select Windows it works. I think that probably means it isn't a CHKDSK issue, or an MBR issue. Not sure what is left.

Raccoon Strait

---

### Post by oldfred on 2018-09-14
Could be chkdsk, or fast start up or anything that Windows sees as a problem.
The  grub boot of Windows seems to only work if Windows works normally. Not  sure why it should be different than directly booting from UEFI, but it  is.

       Windows 8 UEFI fixes, if no repair flash drive you may be able to download Window installer and use it.

       Windows 8 UEFI fixes, if no repair flash drive you may be able to download Window installer and use it.
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows UEFI ows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html](http://www.eightforums.com/tutorials/2269-system-recovery-options-boot-windows-8-a.html)
Not free but they are good tools
[http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/](http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/)

---

### Post by raccoonstrait on 2018-09-14
oldfred,

Thanks for your help. I have a Windows repair flash drive now, I made one as soon as I got in. It worked, but when I asked it to take me to Windows it basically rebooted. Still needed to use F7 and select from that list to get into Windows. I did find fast boot turned on and turned it off. So far as I know it has been on all along. Didn't seem to matter. 

I tried using the recovery drive, but it keeps telling me it is invalid.

I am going to try a Windows System Restore and see if that helps.

Raccoon Strait

---

### Post by raccoonstrait on 2018-09-14
Windows System Restore didn't work. I think this issue is in grub somewhere, because Windows does boot, but only when I go to that F7 menu (I think you call it the UEFI menu, but it is not marked as such). 

That the Windows System Restore didn't work isn't a problem for here. I have never gotten that to work, and I have been using Windows since 3.1.

Maybe someone has some ideas about the grub issue and what I might be able to do about that. Yes I know it is a big assumption on my part, but nothing else makes sense.

Thanks for all your help oldfred, I do appreciated your efforts.

Raccoon Strait

---

### Post by oldfred on 2018-09-14
I do not know Windows restore as never used it.
But from what I have seen, different vendors seem to do it differently, or maybe different Windows versions.
Some will just restore Windows. Others only want Windows standard partitions. And some totally erase drive and restore to as new and may or may not keep your data. I think most now do try to keep data.

Some users that only boot Windows or Ubuntu occasionally, just use the UEFI boot menu. Since grub only boots working Windows, that avoids most Windows issues.

If you have fast start up off (and Microsoft did not do another update & turn it back on) and have run chkdsk, I would expect grub to then be able to boot Windows. Not sure of any other Windows issues that prevent grub from booting it, especially if Windows directly boots.

---

### Post by raccoonstrait on 2018-09-14
I went back and ran c:chkdsk /f /r and got no errors. Windows still doesn't boot from the grub menu, but does from the UFEI menu. So I do not think the issue is on Windows, it works. But the grub menu, which has worked for a couple of years, now doesn't. It will boot Xubuntu, but not the Windows Boot Manager, I have to go to the UEFI menu. 

I looked at /etc/default/grub and compared that with a couple of older files put on when the system was created, but did not see much difference, or any difference that seemed important. I also looked at /etc/grub.d but that has a bunch of scripts which I don't really want to mess with as I don't no what they are supposed to look like.

Any other thoughts?

Raccoon Strait

---

### Post by oldfred on 2018-09-14
Boot-Repair added two more UEFI boot entries for Windows. Have you tried all 3?

Did you turn UEFI Secure boot on, may be Windows or Other where Other is Secure boot off.
Grub will not boot Windows with UEFI Secure Boot on. Chain of trust is lost.

---

### Post by raccoonstrait on 2018-09-14
Yes, I noticed those extra entries and gave them a try, but no joy for them, the ubuntu entry still works without going to the UEFI menu so grub is not totally trashed. I did not enable secure boot in Windows, or bios.

Raccoon Strait

---

### Post by oldfred on 2018-09-14
I do not see much difference between report that you say did not work and one that did work.

It just about is that Boot-Repair added the new 25_custom boot entries and backed up /EFI/Boot/bootx64.efi to bkpbootx64.efi and made bootx64.efi a copy of shimx64.efi to boot Ubuntu from hard drive or fallback entry. It added in 25_custom a boot of Windows using bkpbootx64.efi.

But if nothing works, I do not know what issue is. Still think it is more Windows as grub only boots fully working Windows, where from UEFI you can get Windows to boot but it can do its own fixes or recovery from hibernation.

---

### Post by raccoonstrait on 2018-09-15
I went back and tried those 3 additional entries. Two of them flashed an error message that went by so fast I had to get my camera out and snap a picture so I could read them. The message says:

Failed to open /EFI/Boot/grubx64.efi - not found Failed to load image /EFI/Boot/grubx64.efi: Not Found start_image() returned Not Found

Using Catfish I looked for grubx64.efi and found it in two places:

/boot/efi/EFI/ubuntu
/usr/lib/grub/x86_64-efi-signed

I am wondering if it should also be in /boot/efi/EFI/Boot/  ?

Could it be as simple as copying it over? I don't want to make things worse, so I don't want to attempt this unless you think it a good idea.

I also tried loading Windows and then used shutdown rather than restart. It didn't help.

Thank you again for your time and effort.

Raccoon Strait

---

### Post by oldfred on 2018-09-15
I have seen that error, and I think it is from the shimx64.efi in /EFI/Boot. 
I would try copying grubx64.efi to /EFI/Boot. Copy from /EFI/ubuntu.

I normally copy all of /EFI/ubuntu to /EFI/Boot and then just rename shimx64.efi. But I do not have a bootx64.efi as none is created. I believe new grub installs now do create a bootx64.efi if it does not exist. But Boot-Repair backups up the Windows copy & copies just shimx64.efi and that has worked in the past.  Recently they have made some updates to grub and perhaps that is the change?

---

### Post by raccoonstrait on 2018-09-15
I first tried copying only grubx64.efi and tried it. No joy. I then tried copying all of boot/efi/EFI/ubuntu to boot/efi/EFI/Boot. Again no joy.

You mention renaming shimx64.efi but you didn't say what you renamed it too. grubx64.efi is 1.1 mb and shimx64.efi is 1.3 mb. If you meant renaming shimx64.efi to grubx64.efi could that make some difference? They don't seem to be text files as mouspad won't open them so I cannot see the difference.

There is a bootx64.efi in /boot/efi/EFI/Boot/ as well as a BOOTX64.CSV which has only one entry which is shimx64.efi.

The error message went away in two of the alternate startups, but the third one still has an error message but it is so fast I cannot even capture it with my camera.

I also took a look at /boot/efi/EFI/Boot/grub.cfg:

search.fs_uuid 76d39694-ac38-49be-936e-e0e18122267f root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

The thing I noticed is that that uuid relates to sda2 rather than sda1, which is listed as the EFI system partition by blkid

[FONT=monospace][COLOR=#000000]/dev/sda1: UUID="4B50-A76C" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="129e496b-1a4c-4469-9505-4c83015aeeec"

[/COLOR][/FONT][FONT=monospace][COLOR=#000000]/dev/sda2: UUID="76d39694-ac38-49be-936e-e0e18122267f" TYPE="ext4" PARTUUID="e8f00205-55ce-401f-8d6d-2de88f144130"[/COLOR]
[/FONT][FONT=monospace]
Does that make sense to you?[/FONT]

Raccoon Strait

Oh, and there is a directory in /boot/efi/EFI/ubuntu called FW, which is empty. If empty, why is it there?

---

### Post by oldfred on 2018-09-15
I rename shimx64.efi to bootx64.efi in /EFI/Boot. 

The 3 line grub.cfg in the ESP is a configfile entry to the full grub.cfg in your Ubuntu install's boot partition.

I have multiple Ubuntu installs, and every new install overwrites my  /EFI/ubuntu folder in sda. So I have multiple backups of my ESP. But I  normally just edit grub.cfg in ESP with UUID of my 18.04 install and add  entry into 40_custom to boot test install. I have os-prober off as it  takes forever with many installs.

My UEFI throws some errors that are not critical, system still works.

I have lost track of what is correct in ESP, as I have same ESP since 14.04 with 16.04 & 18.04 and many test installs. Updates then have added & removed files & entries, but based boot is still the same.

rant - not related to your issues.
Something happened with my system and boot from my sda, stopped working. First error was out of space (in UEFI?) then I noticed it was updating UEFI with all the entries in all the folders in my ESP. Since I had many backups in ESP, I could see why it might be too much. But I housecleaned, reinstalled UEFI (which changes settings to defaults, but remembers most boot entries) and still can only boot with rEFInd that I have on sdc & on an emergency boot flash drive.
[https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1787692](https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1787692)
/rant

---

### Post by raccoonstrait on 2018-09-15
Sorry, you lost me with ESP. I looked for grub.cfg but there are none in anything called ESP. I looked for ESP and got lots of them but the only stand alone ESP's were in places like /usr/src/linux-headers-4.15.0-33-generic/include/config/inet/esp/ and that doesn't seem to be relevant.

What do you think about purging grub:

sudo aptitude purge grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed grub2-common 

Which should take the configuration files and then re-installing?

sudo aptitude install grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed grub2-common 

Would there be anything I would need to do after that to get it to look for all OS's?

Raccoon Strait

---

### Post by oldfred on 2018-09-15
I believe the total reinstall of grub from command line as you posted is the same as what Boot-Repair does with a full reinstall of grub.

The ESP - efi system partition should show in parted. It is the FAT32 partition with the boot flag and/or esp flag. One of my ESP, this one labeled as c so from sdc.
```

 Number  Start   End     Size    File system  Name      Flags
 1      1049kB  525MB   524MB   fat32        esp_c     boot, esp 
```

---

### Post by raccoonstrait on 2018-09-15
Well oldfred, I did the command line re-install and it worked. I still have all those extra entries in the grub list, but the Windows Manager one worked...twice.

So I guess I can mark this solved now.

Thank you for your time, effort and patience.

Raccoon Strait

---

### Post by oldfred on 2018-09-15
The extra entries are in 25_custom which is created by Boot-Repair not by grub. 
You can delete any or all of them, if desired or if not using any of them. If you turn off execute bit with -x, then it will not run with the update to grub.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
edit entries:
sudo nano /etc/grub.d/25_custom
Or turn off entirely
sudo chmod a-x /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by raccoonstrait on 2018-09-15
oldfred

That worked perfectly. I chose the turn off option as I was not sure what to remove from 25_custom, I didn't want to delete too much.

Thanks again

Raccoon Strait

---

