---
title: "Windows 8 inaccessible after boot repair"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by davidwebbo on 2013-03-21
Hi - hope you can help me.

Brand new Asus K55V laptop (Intel i5 CPU, 6 Gb RAM, one 500 Gb HDD ) with Windows 8 pre-installed.

Installed Ubuntu alonside Windows 8 and, initially...
- if BIOS configured to boot first from Windows, then OK but no Grub, therefore no Ubuntu
- if BIOS configured to boot first from Ubuntu, then I get Grub and boot to Ubuntu is OK, but selecting Windows from Grub not OK
- so if I pressed 'Esc' during reboot, I got a choice from BIOS where to boot from
- this would have been a tolerable solution ... except I ran boot repair, hoping to get Windows from Grub working, but ...

Now I've lost access to Windows altogether...
- boots to Grub and if I select Ubuntu then OK
- but if I select Windows it fails
- if I press 'Esc' to select boot from Windows, still fails - appears Windows boot info is corrupted (?)

I've tried numerous boot repairs, which has returned the following URLs (/paste.ubuntu.com/...)
5628075
5628224
5629927
5631329
5635902

I don't feel confident to play around with boot repair's advanced options (nor gparted for that matter).

Can you help? 

I don't have any data in Windows 8 but I also do not have an installation disc. I'd really like to have a dual boot machine.

Let me know if you need any further info. I really hope you can help me.

Thanks - David

PS  New to Ubuntu but have it on my desktop with no problems and love it. But not quite ready yet to completely abandon Windows.

---

### Post by oldfred on 2013-03-22
Does this grub entry work?

Windows UEFI bootmgfw.efi

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

But some systems will not boot Windows unless secure boot is on.
If so you have to use grub's shim file that has the Microsoft key and rename the Windows files. You can tell Boot-Repair that secure boot is off to undo the changes. Still a good idea to back up efi partition as it is not large so easy to copy.


 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.
I disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

---

### Post by davidwebbo on 2013-03-22
Many thanks for your prompt reply. I'm away from my laptop until tomorrow. Will try your suggestion and report back as soon as I can.

---

### Post by davidwebbo on 2013-03-23
OK, I've [COLOR=#000000]run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply[/COLOR] ... here's the URL

[http://paste.ubuntu.com/5639054/](http://paste.ubuntu.com/5639054/)

When I reboot with SecureBoot disabled ...
- I get a Grub menu with about 8 items
- if I select Ubunti, OK - Ubuntu boots
- if I select Windows, fails with error messages - "cannot find command 'drivemap" and "invalid EFI file path"

When I reboot with SecureBoot enabled ... nothing works ... selecting Ubuntu hangs the machine ... 

I then ran Boot Repair again, just selecting Recommended repair ... here's the URL

[http://paste.ubuntu.com/5639072/](http://paste.ubuntu.com/5639072/)    ... which I think is identical to the above URL

So, still no way of booting Windows 8.  Ouch!

Any other suggestions?

---

### Post by oldfred on 2013-03-23
Are you booting this entry, not the os-prober one's as posted above on os-prober bug.

 menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 0849-970A
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}


Or this one which looks more like a grub script creation, maybe the are working on bug?

menuentry "Windows 8 (loader)" {

But not these:
menuentry 'Windows Recovery Environment (loader) (on /dev/sda2)'

menuentry 'Windows 8 (loader) (on /dev/sda4)'

If those do not work, then you need to let Boot-Repair do the rename files and see it that works with secure boot on.
       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

### Post by davidwebbo on 2013-03-23
I'm sorry, I don't understand what you say I should do.

Using the Grub menu, the only option that works is 'Ubuntu'. If I select anything else it fails and takes me back to Grub.

Boot Repair give me the following message ...

[COLOR=#500050][FONT=arial]"Please do not forget to make your BIOS boot on[/FONT][/COLOR][COLOR=#500050] [/COLOR][FONT=arial]sda1/EFI/ubuntu/shimx64.efi file!"

What does this mean and how do I do this?

Please help. I still have no access to Windows 8 on this brand new laptop. [/FONT]

---

### Post by oldfred on 2013-03-23
You probably need to turn secure boot on for Windows to work. But you then use Boot-Repair to rename files. It renames the shim file to the Windows file and when you boot Windows you really boot grub. Then grub loads Windows. See post #5 on how it renames files.
Try with secure boot on and off. Rename files and try with secure boot on and off.

---

### Post by davidwebbo on 2013-03-24
No. If I turn secure boot on, nothing works - no Windows, no Ubuntu.

I have tried everything I can think of but I cannot get it to boot to Windows.

If I need to rename files, please tell me exactly which files, including their directory, need to be renamed to what, including their directory - e.g.

    /a/b/c/d/filename      rename to     /x/y/z/newfilename

Is there any way I can restore my computer back to where it was before I first used Boot Repair? I would be happy now if I could go to the BIOS to choose which operating system to boot.

---

### Post by YannBuntu on 2013-03-24
Hello
To rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by davidwebbo on 2013-03-24
I don't see any "Restore EFI backups" option.

Do you mean "Restore MBR"?

---

### Post by YannBuntu on 2013-03-25
If you see no such option in the Advanced Options tabs, then your files already have their original names.

---

### Post by davidwebbo on 2013-03-25
OK, thanks. But I'm still stuck. Sorry to be a pest but how do I get my laptop back to the state it was before I ran Boot Repair?  

1) Would "Restore MBR" help?

2) Should I try non-UEFI (i.e. legacy/CSM) boot? I believe this requires: [FONT=arial]Grub Location -> untick Separate /boot/efi partition ... and then changing my BIOS to CSM boot ...

3) Or maybe purge and re-install Grub: [/FONT][FONT=arial]GRUB options tab -> Tick the "Purge [/FONT][FONT=arial]GRUB and reinstall it" option[/FONT][FONT=arial]
[/FONT]
I don't want to try these advanced options without checking with you first.

Like I said before, I'd be happy now if I could choose my O/S through the BIOS (i.e. forget about Grub altogether) ... like I used to be able to before I tried Boot Repair.  FYI I think I lost Windows after the 2nd time I ran Boot Repair. It was OK after the first time - i.e. default boot to Windows, press 'Esc' during boot to select Ubuntu, which would be good enough if I can get this back.

Thanks for your help, sorry to be such a nuisance.

---

### Post by oldfred on 2013-03-25
In legacy mode, you will not be able to boot Windows. Windows only boots from gpt partitioned drives with UEFI.

In UEFI mode MBR is not used. It only exists on gpt partitioned drives to let legacy partition tools know drive is fully used by gpt and not to try to partition it.
But some computers (Samsungs, maybe others) have major issues with UEFI and secure boot. For those you can install Ubuntu in BIOS/legacy mode and boot from MBR. But to boot Windows you have to go into UEFI change to UEFI mode and boot Windows. Then to boot Ubuntu you have to go into UEFI/BIOS and change to BIOS/CSM mode to boot Ubuntu. Not an easy way to dual boot. If installed in BIOS mode, Boot-Repair can convert Ubuntu to UEFI boot.

The entire UEFI boot is not consistent by vendor. Some will dual boot Windows & Ubuntu with secure boot on or off. Which is how it should be. But most do not.
Some require secure boot to be on, and with Ubuntu using the Microsoft key will boot both Windows & Ubuntu with secure boot on.
But some have modified UEFI to only boot Windows efi file. Then you have to use the rename function to get UEFI to think it is booting Windows when it really is booting the shim file from grub that still has Microsoft key. Then grub chain loads back to Windows efi file to boot Windows.

Or there are multiple combinations of secure boot on/off. Windows files renamed or not. And even UEFI or BIOS settings in UEFI. And many users do not know all the settings within the UEFI menu to even turn secure boot on or off and BIOS mode on or off.
And we do not know details for each brand computer and even that may vary by model of computer.

---

### Post by YannBuntu on 2013-03-25
1) Would "Restore MBR" help?

No. (MBR is not used by UEFI)

2) Should I try non-UEFI (i.e. legacy/CSM) boot? I believe this requires: [FONT=arial]Grub Location -> untick Separate /boot/efi partition ... and then changing my BIOS to CSM boot ...

No. Unless you reinstall Windows then Ubuntu after switching BIOS to Legacy.

3) Or maybe purge and re-install Grub: [/FONT][FONT=arial]GRUB options tab -> Tick the "Purge [/FONT][FONT=arial]GRUB and reinstall it" option[/FONT][FONT=arial]
[/FONT]

No, it won't help.


I haven't read all the story, but all your Boot-Info URLs show that you were able to boot into Ubuntu (either with and without SecureBoot) and run Boot-Repair from the installed session.
So it looks like you problem is only to access Windows. You should be able to access it via the Windows entry in your BIOS.

---

### Post by davidwebbo on 2013-03-26
My thanks to both of you, oldfred and YannBantu, for persisting with my problem. 

Yes, YannBuntu, my problem is only to access Windows. And yes, I "should" be able to access it via the Windows entry in the BIOS ... except I can't, it doesn't work. If I press 'Esc' during reboot and set the BIOS boot priority to Windows, it fails and goes to the second priority - Ubuntu (Grub). And from Grub I can boot into Ubuntu but none of the other options on the Grub menu work.

So I now just want to restore my computer to how it was before I ran Boot Repair (for the second time, that is).

Once more I ask, please help.

Thanks - David

---

### Post by oldfred on 2013-03-26
Since I am not sure which file is which.
I am sure Boot-Repair has made backups, but you can just copy the Windows file back to the correct location in the efi partition.
 
Windows UEFI install should  have backup of bootmgfw.efi here, so copy from here, from Ubuntu or liveCD it may mount at a slightly different location.
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

Copy to here:
From Linux the efi partition is here and the Windows boot file is in the /EFI/Microsoft/Boot folder as it is mounted at /boot/efi

 /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

Then with secure boot on, from UEFI menu you should be able to boot. 

Yann may have better ways with Boot-Repair. But he is in Europe and probably will not be on line till later.

---

### Post by davidwebbo on 2013-03-26
Yay and Hooray! Thank you, oldfred, I could kiss you. I moved the file as you said and now Windows is back. It even appears that I can choose either Windows or Ubuntu from the Grub menu. Phew ... And thanks to Yann too. Now to figure out how to mark this thread as [SOLVED] ... :-)

---

### Post by oldfred on 2013-03-26
Glad that worked. :)

Not sure what was wrong before though? 
But even with BIOS we have had to just restore Windows files and that sometimes fixes things.

---

