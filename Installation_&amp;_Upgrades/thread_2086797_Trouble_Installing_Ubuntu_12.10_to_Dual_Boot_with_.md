---
title: "Trouble Installing Ubuntu 12.10 to Dual Boot with Windows 8"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by jjwyse on 2012-11-21
I just recently purchased a Gateway DX4870-UB318 Desktop.  It has Windows 8 running on it with 1TB hard drive, 8 GB RAM and an i5 and I am trying to install Ubuntu 12.10 as a dual boot option.  

I tried using the Wubi installer but it complained I was missing a file, so I put it onto a USB and installed it that way.  Everything seemed to go OK, however it did not detect that I had Windows 8 installed during installation but instead said that 'No operating systems were detected...'.  I decided to just partition the hard drive myself and after partitioning and installing Ubuntu 12.10 I restarted the computer when prompted.  When everything rebooted it went straight to Windows 8 and I cannot get Ubuntu to boot at all.

I downloaded EasyBCD for Windows 8 and it finds my Ubuntu partition.  When I set that Ubuntu as the 'default' in the 'Edit Boot Menu' and reboot, it prompts me what OS I want to start with but the only option is Windows 8.

I've been trying to get this installed for a couple days now and any help would be much appreciated!

---

### Post by oldfred on 2012-11-21
Have they updated EasyBCD to work with UEFI. A while ago it did not.

Did you install the 64 bit version of Ubuntu? And did you install in the UEFI mode. When you boot your flash drive installer, it should give two choices, one UEFI and the other BIOS/legacy/AHCI or whatever. Only the UEFI option will work if you have Windows in UEFI and Windows 8 will be UEFI with secure boot if pre-installed.

If you did install the 64 bit version  in BIOS mode you can convert to UEFI mode with Boot-Repair. You uninstall grub-pc and install grub-efi and then in UEFI/BIOS choose to boot Ubuntu. Grub also has a bug in creating a boot stanza to chain load to Windows, but again Boot-Repair can also add a correct boot for Windows.

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by jjwyse on 2012-11-21
From my understanding the new EasyBCD 2.2 does indeed have UEFI support, however I should mention I am new to installing my own OS and do not completely understand what UEFI is or what I need to do in order to comply with it?

I did install the 64 bit version of Ubuntu.  I do not know if I installed in UEFI mode, can you help me out with exactly how to do that because I did not see that option when I used by boot installer (Universal-USB-Installer-1.9.16).  Do I need to use a different flash drive installer?

I have seen the Boot-Repair mentioned elsewhere but, this may be a dumb question, but how do I use that utility when I can't get to my Ubuntu installation?  That is just a Linux utility, correct?  Or do I install those utilities while just running Ubuntu from a flash drive?  

I apologize for the dumb questions and really appreciate your help!

---

### Post by jjwyse on 2012-11-22
I ran the Boot-Repair from Ubuntu and the results are here (this is after I deleted the partition I attempted to install on): [http://paste.ubuntu.com/1376493/](http://paste.ubuntu.com/1376493/)

Here is an update from Boot-Repair after after I attempted to install Ubuntu 12.10 again: [http://paste.ubuntu.com/1376518](http://paste.ubuntu.com/1376518)

---

### Post by jjwyse on 2012-11-22
After running Boot-Repair I now can't boot from anything on the hard drive but only from my flash drive.  When I go to click install in Ubuntu it detects the other Ubuntu 12.10 installer but it now appears I've screwed something up with Windows 8.

Ran Boot-Repair again and back to kind of back to where I began.  It prompts me on startup for the OS I want to boot to and the only options is Windows 8.

---

### Post by darkod on 2012-11-22
Since your computer already had win8 in UEFI, you need to install ubuntu in UEFI too.

That means:
1. It has to be the 64bit version since the 32bit doesn't support UEFI.
2. When you boot the cd or usb to install, you have to boot the UEFI device.

On UEFI systems you will have two devices for the dvd-rom and for bootable usb sticks: one for the older legacy mode, and the other for UEFI mode.

You have to boot the UEFI device for ubuntu to install in UEFI mode. Be careful to make the correct selection when booting, and it should be fine after that.

---

### Post by jjwyse on 2012-11-22
Thanks for the help.  I re-installed and ran boot-repair and it seems like the Grub location is accurately pointing to the right location however it still won't boot up Ubuntu and I'm back to not being able to boot to Windows 8 either.  Sorry for the hassle but I must be missing something here?

Here's the most recent boot-repair information: [http://paste.ubuntu.com/1377347](http://paste.ubuntu.com/1377347)

---

### Post by darkod on 2012-11-22
Why did you comment out /boot/efi fstab? I think it needs to use it for UEFI.

Also, since UEFI boots with its own boot manager, not with windows bootloader or grub, sometimes you need to enter bios/uefi setup and add the ubuntu entry yourself. You should be able to find a procedure in the computer manual or online.

PS. I noticed you added the /boot/efi at the end. I only saw the disabled entry at first glance. See if you need to add it to the uefi menu yourself.

---

### Post by oldfred on 2012-11-22
It looks like the /boot/efi is commented out and then added again, so it is ok.

You have to go into UEFI/BIOS (check manual for which key) and choose to boot Ubuntu. UEFI remembers last booted, so it will keep booting Windows until you change it. And when booting Ubuntu, grub menu will also have an option to chain back to Windows, so from grub you can boot either.

---

### Post by jjwyse on 2012-11-22
Thanks again for both of your help.  I cannot seem to find how to get into the UEFI/BIOS menu to modify it?  I've been searching the web and looking in the manual for it but the only thing I can find is the 'Del' button to get to the BIOS.

Since I couldn't get to Windows I was getting worried so using GParted I just deleted the Linux partitions and reformatted the C:/ (Windows) partition back to how it came out of the box.  This allowed me to boot back into Windows.  I am going to try (the fifth time) to install Ubuntu 12.10 by partitioning the drive myself.  Before I do this again is there any directions specifically I should change?  Below is how I've been manually partitioning things:

10 GB   - Linux swap
1 GB     - /boot
500 GB - /

I then have just been running Boot-Repair to allow it to do the dirty work because truthfully, I'm pretty new to this and don't understand exactly what I need to do still.  Sorry for needing my hand held through all of this but I really appreciate your help and any further direction would be appreciated.

---

### Post by darkod on 2012-11-22
You don't really need the separate /boot, and note what we said about booting the uefi device.

If all goes well, you shouldn't need to run boot-repair at all, it should work. Additional step might be needed to add ubuntu to the uefi loader, but if that is the case I think boot-repair can't help anyway since it can't add that. The only choice is to enter bios with Del and look for that uefi boot menu/manager or what ever it might be called.

---

### Post by oldfred on 2012-11-22
We have seem some systems have issues with very large / (root) partitions. Boot-Repair then does suggest the separate /boot. 

I prefer a smaller / (root) partition of about 25GB and then the rest of the space you want to allocate for Ubuntu as either /home or just data partition(s).

One user posted this and said you could change  the name of what you boot. But each vendor's implementation of UEFI is different.

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

    

---

### Post by hgroover on 2012-11-22
I am still working through this with the Ubuntu 12.10 SecureBoot remix on my ASUS laptop with 750gb hard drive and Windows 8 preinstalled.

One thing I should add is that the ASUS aptio (AMI) bios is VERY confusing and seems to be not that well thought out. It DOES detect the EFI/ubuntu/grubx64.efi secure boot loader on the sda1 fat32 partition (after I ran boot repair the first time). To boot back into Windows 8 I have to hit F2 quickly when I power on or restart. Changing the boot loader order doesn't work and I end  up falling through to the network BOOTP fallback.

The only way I can choose boot is by setting the Windows 8 boot loader and ubuntu loader in the boot order screen, THEN go to the "Save changes" page and use the boot override to select one of the specific boot loaders. 

I suspect their management of boot loader override is broken since they probably didn't bother to test it on a multi-OS setup with large hard disks.

In any case I can get to the Ubuntu loader but it doesn't seem to be able to load the initial kernel and ramdisk initrd. I suspect there's a problem with the gpt partition table and the way I have it partitioned:

sda1 fat32 300mb
sda2 ntfs 600mb (Windows 8 recovery)
sda3 unknown 128mb (???)
sda4 ntfs 258gb (Windows 8)
sda5 ntfs 20gb (Windows 8 restore)
sda6 unknown (bios_grub?) 1mb
sda7 ext4 413gb (Ubuntu 12.10)
sda8 linux-swap 6gb

I wanted to share this because after several frustrating hours of trying to get this to work I'm beginning to realize that part of the problem may be that the AMI aptio UEFI loader may be making this much harder than it should be.

I can boot to my Ubuntu 12.10 Secure remix install DVD and to a boot repair CD and I can manually boot to Grub2 or WIndows 8, but it's not at all obvious.

Just bought this laptop yesterday (and was expecting some trouble with Windows 8 dual booting, but this has been a major headache). I suspect that getting Ubuntu dual-booting on some Windows 8 machines is going to be a moving target for a little while yet...

---

### Post by jjwyse on 2012-11-22
Thanks again for everyones' responses.  I am continuing to work through it myself and have not yet solved this problem.

I installed Ubuntu 12.10 again by partitioning:

/                 - 500 GB
swap space - 10GB

to no avail.  I think a smaller /boot partition may be necessary but I haven't got either working so I can't really say.

I found the 'Advanced Startup' options in Windows 8 which gives me some more options and I saw an 'ubuntu' option showing up in the list of 'Use another operating system' but when I tried to boot to that, I just get a black screen on startup 'Windows Boot Manager', which only allows me to select Windows 8 from the list of available OS's?

If anyone has any more insight into this issue(s) I would really appreciate it.  Thanks for your time.

PS - Also in the 'Choose an operating system' settings in 'Advanced startup options' I have selected 'UEFI:ST1000DM003-9YN162' which seems to load the Windows Boot Manager each time.  I just need to get 'Ubuntu' into this list to boot

---

### Post by oldfred on 2012-11-22
I still suggest the 25GB / (root) and separate /home. If that does not work then a separate /boot near the beginning of the drive may be required. 

Does UEFI have a fast/quick boot setting, many BIOS do and that has caused issues. Some other seemingly unrelated settings can also cause issues.

 @hgroover
Windows in UEFI has a system reserved partition and you installed Ubuntu in BIOS mode so it added a bios_grub partition. Both are unformatted spaces for boot code, so partition tools show them as unknown since there is no format.
The bios_grub is not required with UEFI.

---

### Post by jjwyse on 2012-11-23
@oldfred I re-installed as you suggested:

/[root] -   25 GB
/home - 630 GB
swap   -   10 GB

and booting directly to the UEFI it only allows me to choose Windows 8.  I'm going to reboot to the Ubuntu on the flash drive and run boot-repair to see if this works now.

After running boot-repair, here is the report that I see now: [http://paste.ubuntu.com/1378766/](http://paste.ubuntu.com/1378766/)

Still unable to get an option to boot to ubuntu and it just goes to the 2nd boot option which is the USB drive.  Only way around this to fix to get me able to boot to the hard drive has been to remove the Ubuntu 12.10 partitions, run boot-repair and then restart.  

If you see anything obvious that needs changed please let me know.  I'm going to head to bed for the night but have time tomorrow to continue to try to get this setup.

---

### Post by oldfred on 2012-11-23
With multiple efi entries the UEFI should then give multiple choices. hgroover said he did see the ubuntu choice. 

And then you can use boot repair to add the correct Windows boot entry to the grub menu which it looks like you have done.

---

### Post by hgroover on 2012-11-23
OK, there are some further developments here.
After my previous posting I went through boot repair a second time after reinstalling from the 12.10 secure remix.

My gpt0 is a fat16 partition with EFI/ubuntu/grubx64.efi and the aptio bios on my ASUS Q500 laptop does in fact now find this and allow me to select it in the boot order entry.

So I can power on and have grub2 come up by default. One small victory.

I can select the Windows UEFI loader from grub2 and it loads Windows 8. Also good.

I still have the problem where I can't seem to load the kernel. I'm still working through grub2 command line options but basically I end up with a blank screen and no disk activity trying to load the kernel and initrd.

I've also gone through the grub2 docs trying various options which may help me get better debug message visibility early in the boot process.

It could certainly have something to do with the disk size but I've shrunk Win8 down as far as I can / want to (258gb) and perhaps I'll need to do a custom install of ubuntu onto another partition split where I have a smaller boot / root partition which doesn't end after 500gb or wherever the boundary that is causing the failure lies.

I think that splitting my 450gb ubuntu partition may be the next step... I'd still like to better understand why that should be needed, it seems that grub should be able to handle it but at this point I just want to get it working...

---

### Post by oldfred on 2012-11-23
It could be a grub/UEFI/BIOS issue, but if you get grub menu and screen is blank that may just be video issue. What video card/chip do you have?

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by hgroover on 2012-11-24
Thanks for all the suggestions and help!

I have Intel HD Graphics 4000
nomodeset has no effect
I tried various vesa modes via vga= (824, 792, etc) but they have no effect
The live CD correctly sets the video mode to 1366x768

I've tried modifying the boot options in the grub menu and also dropping to the grub command prompt (via c) and setting options by hand. I always get the same result: the last thing I have on my screen are the grub boot options I typed in, ending with linux ... then initrd ... then boot, and the system is hung.

Setting debug=all in grub doesn't give me much and seems to trigger some odd behavior.

I also have the "Advanced option" grub entries which boot with nomodeset, and both of them (normal and recovery) show

Loading Linux 3.5.0-17-generic ...
Loading initial ramdisk ...

and nothing else. The system is still responsive to Ctrl-Alt-Del but nothing else and no disk activity. I've also tried waiting for 10 minutes or more. Interestingly I get short disk activity hitting ENTER twice, then again hitting ENTER twice - after that ctrl-alt-del doesn't work and I have to use the power button.

The 12.10 secure remix live CD works as does the regular x64 live CD.

When I use the grub command line I can view my 20gb boot filesystem including /var/log, but there is nothing interesting there.

> **oldfred said:**
> It could be a grub/UEFI/BIOS issue, but if you get grub menu and screen is blank that may just be video issue. What video card/chip do you have?

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by oldfred on 2012-11-24
@       jjwyse
If UEFI will not show Ubuntu I do not know what else to try. There are some defective UEFIs.
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

@       hgroover
Intel 4000 just works for most, but some need other settings. Intel only has one driver for all versions.

I do not know if this applies to the new one like yours.

 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

This also was for an older Intel
       if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
           
Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

---

### Post by hgroover on 2012-11-26
Unfortunately, none of these options worked. The "Ubuntu advanced options" / recovery mode kernel should already boot without switching to graphics mode right away, but it looks like I'm hanging somewhere right away.

I suspect there's a problem either in the very early kernel initialization or with the grub bootloading process. I'll probably need to build a kernel and initrd to debug this further and figure out what's going on, and may not get to do that for a while.

Thanks again for your helpful suggestions!

> **oldfred said:**
> ...
@       hgroover
Intel 4000 just works for most, but some need other settings. Intel only has one driver for all versions.

I do not know if this applies to the new one like yours.

 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

This also was for an older Intel
       if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
           
Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

---

### Post by YannBuntu on 2012-11-26
Hello

**@jjwyse:** i updated Boot-Repair's PPA today. Please update Boot-Repair (boot-repair and boot-sav packages) then run the Recommended Repair and indicate the new URL that will appear. Reboot and tell me if you see the GRUB menu?

**@hgroover:** in order to avoid confusion, please could you create your own thread [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=333"), and tell us its link so that we can follow-up.

---

### Post by hgroover on 2012-12-01
Thanks, posted here: [http://ubuntuforums.org/showthread.php?p=12382839](http://ubuntuforums.org/showthread.php?p=12382839)

> **YannBuntu said:**
> Hello

**@hgroover:** in order to avoid confusion, please could you create your own thread [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=333"), and tell us its link so that we can follow-up.

---

### Post by magcig on 2013-01-11
Detailed Guide to Install Ubuntu 12.10 on Pc with Win8 Pre-Installed:
[http://install-climber.blogspot.it/2013/01/howtoinstall-linuxubuntu-pcwindows8preinstalled.html](http://install-climber.blogspot.it/2013/01/howtoinstall-linuxubuntu-pcwindows8preinstalled.html)

---

### Post by oldfred on 2013-01-11
@magcig
Your link is to a total overwrite of Windows with Ubuntu. While that may work for some systems, it definitely is not dual booting.

And on some systems it may totally brick system, if user has not turned off secure boot and turned off fast boot.
       UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

---

