---
title: "Dual Boot Ubuntu 12.10 on PreInstalled Windows 8 Sony Vaio T"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by bananabuntu on 2013-04-08
Hola,

I have just installed Ubuntu 12.10 on my Sony Vaio T. I first shrank my C: in Windows 8. Then installed Ubuntu and used the space to set up a Swap and the rest was my /. I ran Boot-Repair. ect ect.

So my problem is that the GRUB menu will come up and Windows won't start. It will go to the troubleshoot screen. Then I CAN start Windows through there. BUT when I shut down and reboot my computer it boots automatically to Windows. So I ran the Live USB and did Boot Repair again and the GRUB menu shows up when I shut down Ubuntu. But again Windows would not boot. 

I have read that the Boot Repair should fix the problem with Windows loading properly. So ... I'm at a loss. 

Here is my file from Boot Repair

[http://paste.ubuntu.com/5690757](http://paste.ubuntu.com/5690757)

Help? :) 

Yes I am a Linux NEWB

---

### Post by oldfred on 2013-04-08
I think the issue is your Intel SRT. That has caused issues. 
Are you resetting UEFI to boot grub? But even that with the cached entries that Intel SRT does may just revert everything. 
Boot-Repair does have a function to rename the Windows boot file so it really boots grub and you only boot Windows from the grub menu.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 


  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

### Post by bananabuntu on 2013-04-08
[COLOR=#000000]"Are you resetting UEFI to boot grub?"

1st off I have no Idear what that means :)

I looked at the other links that you provided and the only difference that I can see is that I did not disable the QuickStart from the power options menu. I disabled the Intel SRT previously. Also I didn't run the exact code to update Boot Repair when I ran it. So I'm hoping maybe those two things will fix my issue. As soon as I try those two things I will let you know. 

I will also try the other suggestions you posted. 

Thanks ALOT :)

I ran Ubuntu in a Virtual Machine off my MacBook and found that it was the BEST BEST BEST for all the Bioinformatic stuff that is out there. If none of this works I think I just might scrap Windows 8 altogether.. In which case I shall probably be begging for more help :)[/COLOR]

---

### Post by bananabuntu on 2013-04-08
Ok.

I did the first thing. I re-ran the Boot Repair from the Live USB and went to Adv Options> [COLOR=#000000]tick "Backup and rename EFI files" --> Apply

[http://paste.ubuntu.com/5691063](http://paste.ubuntu.com/5691063)
I then shut down Ubuntu
Turned on Computer
!
I then saw a new "Windows Boot UEFI loader" Option.. Clicked on that and Windows booted (none of that odd Blue screen that I was getting before) 
Shut down Windows
Turned on Computer
GRUB!!
Clicked on Ubuntu... 
BAM! 
Looks like it works..

Ok
So now I am going to try and Turn on Secure Boot and do what was suggested and Enable Secure Boot and Re Run Boot Repair
...
[http://paste.ubuntu.com/5691088](http://paste.ubuntu.com/5691088)

Shut down Ubuntu
Turned on Computer
Selected "Windows Boot UEFI loader" Option
/EndEntire
file path: /ACPI(lots of numbers..)!!

Oh no.. !!

So went back to BIOS and disabled Secure Boot. Restart took me back to GRUB
Selected "Windows Boot UEFI loader" Option
...
Windows boots correctly.. 
I turned on 'Fast Start Up Option' (Just to see what happens.. )
Shut Down
Turn On

GRUB comes up..
Ubuntu boots fine..
Shut Down
GRUB
Windows boots correctly..
I turned Intel SRT back on (Just to see what happens..)
Shut Down
Turn On
GRUB
Windows boots correctly..
Shut Down
Turn On
GRUB
Ubuntu boots fine..


OK!
1. Thanks for the help
2. The only thing I can think of that was a problem was either having the "Fast Start Up" Option on while running Boot Repair and that somehow not allowing it to repair correctly
3. That I did not have the latest update of Boot Repair when I was first trying this

So in conclusion.. Boot Repair did resolve the issue. HOWEVER I still cannot use 'Secure Boot' It has to be disabled for Windows to Boot correctly. Why? I have no idea. 

I hope the Boot Repair files can help you guys out. Thanks again for the help :) 


[/COLOR]

---

### Post by oldfred on 2013-04-08
If anything having secure boot off to boot is unusual. Usually it is that secure boot has to be on.

But we are finding every vendor's UEFI and maybe even models within each vendor vary. And then whether UEFI is updated as Vendors are also updating the UEFI/BIOS.

Or is it is a mess to understand and about all we can do is suggest alternatives to try.

---

### Post by bananabuntu on 2013-04-09
SO..

This morning after waking up my computer (I put it to sleep while in Ubuntu by closing it) I went to Shut it down and Start Windows again..

There is no error on the Windows 8 but it stays stuck at a blank screen. 

I re-ran Boot Repair

[http://paste.ubuntu.com/5692656](http://paste.ubuntu.com/5692656)

Hopefully I can get into Windows and my only guess is that the 'Quick Start' may actually have made things funky.

---

### Post by oldfred on 2013-04-09
I have seen several users with the cache and have issues. I do not know if cache is just restoring Windows files or doing other (hidden) changes that we do not really know about.

Several users just had to find the original Windows efi file & copy it back. Not sure if the Ubuntu worked ok or not as some systems only boot with secure boot on or only boot Windows and to get grub to boot you have to rename the original Windows file. (as detailed in post #2)

       Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

    Note that Boot-Repair has already renamed your files, but now we are not sure if Intel cache changed things.
 Users who manually moved efi files around:
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
      
 HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by bananabuntu on 2013-04-09
Ok

I ran Boot Repair again and [COLOR=#000000] "rename files to their original names, you just need to tick the "Restore EFI backups" option "[/COLOR]
[COLOR=#000000]and that seemed to work.. 

I guess if it does it again at least I know how to fix it? I know I won't be using Windows all that often so not a huge problem. 

I left the Intel SRT and Quick Wake options on.

I think you have nailed it on the head when you say that it is all a mess to understand. [/COLOR]

---

