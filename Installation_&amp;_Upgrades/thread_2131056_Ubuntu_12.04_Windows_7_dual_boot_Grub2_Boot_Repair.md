---
title: "Ubuntu 12.04/ Windows 7 dual boot Grub2 Boot Repair Issue"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by kgriff on 2013-03-31
My computer is EFI enabled. 
System config
Mobo:  Gigabyte 78LMT-S2P
Video: MSI R5450 MDIGH  (Radeon)

I am trying to set up a dual boot with Windows 7.  I have had this computer confugured in this manner in the past.  In fact, up until a couple days ago.  At that point, I "broke" Ubuntu by messing around with things I shouldn't have been.  I figured my easiest path forward was to reinstall.  I installed Ubuntu again, but couldn't get Grub to come up.  Next I started from scratch - Reformat hard drive, install windows, resize windows partition, install Ubuntu.  Still can't get Grub to come up.
The first time around I ran Boot Repair twice.  The first time was Recommended Repair.  When that didn't work, I did Advanced and got everything working.  I didn't really do anything in Advanced, just left all of the default settings.

The second time around, I have run Boot Repair in the same manner, only this time, since things didn't work out, I've tried a few of the Advanced options.  I'm not too worried about breaking anything, since I can only boot Windows at this point, anyway.  If I break anything beyond recognition, I can always reinstall.

Here are the URL's listed after Boot Repair.  The first is from a couple months ago, when I had a functional Grub, the other is from today.  I have looked at these and don't see anything obvious, but I don't know what I'm looking for.
Hopefully, there's someone here that can help.

URL when grub did work:
[http://paste.ubuntu.com/5602254/](http://paste.ubuntu.com/5602254/)

URL from today.  Grub is mia at boot:
[http://paste.ubuntu.com/5664848/](http://paste.ubuntu.com/5664848/)

---

### Post by Jay_E on 2013-03-31
do you have two disks?
there is/was a grub bug.

I used raring install dvd to repair.

have fun,
jay

---

### Post by Jay_E on 2013-03-31
I forgot to say....

try doing a google on ubuntu bug grub

and see if any apply to you.   :-)

Jay

---

### Post by kgriff on 2013-03-31
Can you provide any more information about how the raring dvd helped you fix your problem?

---

### Post by oldfred on 2013-03-31
If you just go into your UEFI and boot Windows do you get grub menu?

It looks like Boot-Repair modified Windows boot file to be shim. Many Windows 8 systems with secure boot will only boot the Windows efi file, hard coded into UEFI, and not per standard. You should not need that and probably can undo it with Boot-Repair. Then you should have both ubuntu & Windows in UEFI menu & grub menu will also let you boot Windows.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

Also have you updated UEFI/BIOS? Many early Gigabyte board had limited UEFI support.

---

### Post by kgriff on 2013-04-01
> **oldfred said:**
> If you just go into your UEFI and boot Windows do you get grub menu?

No grub menu at all, no matter what I do, since I reinstalled Ubuntu and, subsequently, wiped everything out, reinstalled Windows, then reinstalled Ubuntu.

> **oldfred said:**
>    To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.

During Boot Repair I was prompted to copy-paste three commands in terminal.  I assume this is normal since I've gotten this each time.
The third command:
**sudo chroot "/mnt/boot-sav/sda5" apt-get purge -y -force-yes grub*-common shim-signed linux-signed***
yielded several not unexpected things, but one that seems like it might be bad;
**'dpkg: warning: while removing grub-common, directory '/etc/grub.d' not empty so not removed.'**
This may be normal, also.  I wasn't looking this thoroughly in past iterations.

The final command coming up in a new pop-up:
**sudo chroot "/mnt/boot-sav/sda5" apt-get install -y -force-yes grub-efi linux**
resulted in the following, and seems okay:
[B]Creating config file /etc/default/grub with new version
BootCurrent: 0000
Timeout: 3 seconds
BootOrder: 0002,0000,0001
Boot0000* EFI DVD/CDROM
Boot0001* OsLoader0000
Boot0002* ubuntu
Installation finished.  No error reported.
Setting up grub-efi (2.00-7ubuntu11)[/B]

Upon reboot, I get the same as before:  POST, slight delay at a black screen with a non-blinking line-cursor in the upper left corner, then boot Windows.


> **oldfred said:**
> Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

Also have you updated UEFI/BIOS? Many early Gigabyte board had limited UEFI support.

Secure Boot is not an option with this Bios.  I do have the latest Bios rev.  I was able to dual boot in EFI mode a few days ago, and I haven't changed anything in bios, so I don't think that's the issue.

---

### Post by oldfred on 2013-04-02
If you do not have secure boot (only Windows 8 systems do currently), you should have both Windows and Ubuntu in UEFI menu. Not sure what osloader0000 is?

Post new BootInfo just to see if files look like they are in correct places.

---

### Post by kgriff on 2013-04-02
BootInfo
[http://paste.ubuntu.com/5669202](http://paste.ubuntu.com/5669202)

I believe OsLoader0000 is attempting to refer to Windows.  I believe, when I installed as dual boot and everything worked out, somewhere along the way I got an indication that Boot Repair recognized the existance of Windows.  This time around, I've gotten no such indication, so I'm not too sure what's going on.

Edit - Forgot to mention - In Bios I can only select "Hard Disk" as boot source.  I'm not sure what you mean by "UEFI menu".  Grub never comes up.

---

### Post by darkod on 2013-04-02
You are willing to do a format and clean reinstall of both OSs if I understood right, right?

In that case, forget about UEFI. The uefi dual boot is still much more comlicated to do than the older type legacy dual boot.

If you are willing to format the disk again, here is my suggestion:
1. Go into bios and disable uefi boot. Set it at Legacy Only or how ever it's called in your bios. This will make sure you don't boot an install cd in uefi mode by mistake.
2. Boot the ubuntu cd in live mode, open terminal and write new blank msdos table on the disk:
```
sudo parted /dev/sda
mklabel msdos
quit
```
This is better to be done with ubuntu since windows is a real idiot if you try to convert gpt disk to msdos.
3. Boot the win7 dvd and make the installation. Give it the amount of space you want for win7, leave the rest of the disk as unallocated.
4. Boot the ubuntu cd and install it, using the auto method or manual, as you prefer.

Enjoy your new dual boot. You are not getting anything useful with uefi anyway, only problems.

---

### Post by oldfred on 2013-04-02
There are different choices in UEFI/BIOS. With my BIOS system it is a sub-menu under hard drive, but some have it as a totally different menu entry somewhere else in BIOS to specify which hard drive device to boot. It is similar with UEFI but instead of hard drive devices it is the entries in the efi partition.

From UEFI/BIOS you should get three choices - Boot, ubuntu & Windows which are the folders in your efi partition.

 /EFI/Boot/bootx64.efi 
/EFI/ubuntu/grubx64.efi 
/EFI/Microsoft/Boot/bootmgfw.efi 

And I see Boot-Repair added a correct chain load entry to Windows in 25_custom.

 menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 2E2F-337B
chainloader (${root})/EFI/Boot/bootx64.efi
}

Someone also posted that you can change the names used by UEFI.
>  Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


---

### Post by kgriff on 2013-04-02
This is a brand new system so, no, I have no issue with reformat, reinstall.

I had already though about going back to "legacy" mode, but I'd like to understand why UEFI worked on this system once and won't now.

My other option is just to skip Windows and run Ubuntu only.  The few things I might use Windows for I can do with a Windows Virtual Machine.

Thanks a lot for the suggestion, and it may well be what I wind up doing, but I want to explore the UEFI thing a bit more.  It appears to be the way things are going and I'd like to get a better understanding of the potential problems and solutions.  I agree, though, that it does seem to cause a lot of problems for a lot of people.

---

### Post by darkod on 2013-04-02
No problem, you have a valid point. It might be only me, but i still look at UEFI as a way for Microsoft to stop easy dual booting, and that most manufacturers are Microsoft oriented only. oldfred explained it very good in one post: It will take time until linux developers do reverse engineering to make uefi easier. Nobody is working with them in advance so they have to do it reverse. :)

In your case, you want to learn, which is great, but imagine how many people already blamed Ubuntu for "simply not working and installing as it should", when the real reason lies more in uefi than in ubuntu.

For uefi, I would say double check the EFI system partition is still there and working, and it's also important to make sure to boot the ubuntu cd in uefi mode when installing. In general, that should be enough, but in reality at this moment the dark forces start working... :)

---

### Post by kgriff on 2013-04-02
I think the issue is actually with the Bios.  I've done some looking and found many complaints that Gigabyte's UEFI implementation is questionable.
I have no option in bios to select anything other than "Hard Drive".  Once I figure out that people referring to "UEFI Boot menu" were referring to the boot menu that I can get to by pressing F12 at startup, I realized that I have no additional options there, either.
That all led me down the path of a bios shortcoming, so I started looking there and found the Gigabyte complaints.  So far, I haven't found anyone with a good solution, though I still don't understand why it worked once, but won't now.
I intend to keep looking and listening for a bit but, ultimately, will probably wind up redoing the system.  I'll probably give it another UEFI shot then, if that doesn't work, I'll turn off UEFI and go to "legacy" mode.
You can probably tell that this is my first go at UEFI installation.  Even as little as I know about it, I am in agreement that UEFI is a Microsoft "no dual boot" technique, but I'm certain the Linux community will overcome.  I've been with Linux long enough to know that most manufacturer's have done the same thing in the past, and many still do.  Though Linux is gaining greater acceptance by manufacturer's, there is still an unfortunate amount of reverse engineering that has to be done.

---

### Post by oldfred on 2013-04-02
Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www.rodsbooks.com/gb-hybrid-efi/](http://www.rodsbooks.com/gb-hybrid-efi/)
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)

I did once find a Gigabyte upgrade to its UEFI for certain motherboards from a hybrid or partial to a full UEFI. But lost the link, since it did not apply to my old system.

Video
 Upgrade Gigabyte to UEFI (Windows)
[http://www.youtube.com/watch?v=D-FcRUp2A-E](http://www.youtube.com/watch?v=D-FcRUp2A-E)

---

### Post by darkod on 2013-04-02
I have a Gigabyte F2A85X-D3H board (AMD) but the first thing I did after installing it and powering on the computer was to select Legacy Only for the boot option. :) So, I can't help much with the uefi implementation.

Although, I moved the SSD with existing legacy dual boot and only upgraded board/cpu/memory so using it in legacy boot was not really a difficult choice. I had no intention reinstalling everything just to give uefi a go. In general as a manufacturer I have great confidence in Gigabyte, but can't really comment on uefi implementations.

---

### Post by kgriff on 2013-04-04
Thanks, all, for the help and suggestions.
I wound up reverting to "legacy" bios mode and reinstalling.
As you may have guessed, everything went smoothly and I now have a functional system.

---

