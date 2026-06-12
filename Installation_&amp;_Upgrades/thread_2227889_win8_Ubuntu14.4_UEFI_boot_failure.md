---
title: "win8 Ubuntu14.4 UEFI boot failure"
date: 2014-06-04
forum: Installation &amp; Upgrades
---

### Post by jeffhill913 on 2014-06-04
Having great difficulty with dual boot Win8 and Ubuntu.
    Tried to reinstall Ubuntu to go from 13.10 to 14.4.
    Ended up restoring the HP-G7 laptop Win8 to factory state, then     install 14.4, which looked like a clean install.  Laptop boots     directly to Win8.  Booted ubuntu dvd, installed and ran boot-repair,     still boots directly to Win8.
    
    Here is the diag info from boot-repair.
    
    
    
    Please write on a paper the following URL:
    [http://paste.ubuntu.com/7584715/](http://paste.ubuntu.com/7584715/)
    
    In case you still experience boot problem, indicate this URL to:
    [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or     to your favorite support forum.
    
    No change has been performed on your computer.
    
    Any help would be appreciated.
    
    
    
    Thanks.....     Jeff

---

### Post by LastDino on 2014-06-04
Have you turned off the secure boot in W8? Did you tinker with UEFI and legacy BIOS option? Both windows and Ubuntu need to be installed in same mode.

-waits for oldfred to push the boat-

---

### Post by jeffhill913 on 2014-06-04
prior to 14.4 install, did disable secure boot in win8, uefi was still enabled (not in legacy mode). used Ubuntu 14.4 dvd with internet connected, install had no errors, boots to win8 no indication of grub.

---

### Post by jeffhill913 on 2014-06-04
I looked at the sda3 defined in the paste from boot-repair, it looks like this is an invalid or undefined format.  I looked at the partition (sda3) with gparted and gparted shows a red flag and unknown as to format.  Is this the problem? Where is the grub supposed to be located?  Sorry I am not more knowledgeable.

---

### Post by squakie on 2014-06-04
Don't worry about SDA3 at this point.  What does boot-repair say it would do *IF* you ok'd it (but don't ok it!)?

Also, have you read the many threads on Win 8 uefi in dual boot with ubuntu?   Many, many, MANY of these.  Check threads from oldfred - they are an expert on this have links to several posts to help.

I seem to remember that besides turning off secure boot, you also have to turn off fast boot.

I'm suspecting you just need to let boot-repair do its thing at this point.  If you have just completely reloaded your system as you say you really don't have much to lose.

---

### Post by oldfred on 2014-06-04
Every HP I have seen so far has had issues.
They seem to have modified UEFI to only boot Windows, even if ubuntu entry is in UEFI when viewed directly.

Your sda3 is Windows system reserved and required by Windows. It is like unformatted scratch space for it to hide serial numbers, DRM info, etc. In MBR it used the sectors after the MBR but before first partition.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
      
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Many with HP used a manual rename. You can use Boot-REpairs rename or 'buggy' UEFI fix but that can cause issues on Windows updates later.
      
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

I have seen all these used:

 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
A: Manually rename files either bootmfg.efi and/or bootx64.efi : 
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   B:Boot_Repair rename Windows bootmfg.efi. But cannot boot Windows from UEFI only grub 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   C: Edit Windows BCD, one Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   D: If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

   E: Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by jeffhill913 on 2014-06-04
I saw your long set of suggestions before I posted to this forum.  I wish I knew enough to try one or more of your suggestions, but I do not.My efi partition looks like this:
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate32.efi 
                       /EFI/HP/SystemDiags/CryptRSA.efi 
                       /EFI/HP/SystemDiags/CryptRSA32.efi 
                       /EFI/HP/SystemDiags/SystemDiags.efi 
                       /EFI/HP/SystemDiags/SystemDiags32.efi 
                       /EFI/HP/boot/bootmgfw.efi /EFI/HP/boot/bootmgr.efi 
                       /EFI/HP/boot/memtest.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/HP/EFI/Boot/bootx64.efi

Booting with escape and pf9 shows two ubuntu items, but when selected it looks like a grub output, and choosing ubuntu gives error of /boot/vmlinuz... not found??
unaligned pointer 0x848d9cc8    Aborted.  press any key to exit.
I never see grub on a normal boot, only from pf9.
You indicate to do a rename, how would I do that, and what should I rename?

Thanks for your help

---

### Post by oldfred on 2014-06-04
I think some with HP have said your boot method works, its only when you want to be able to set it as a default in UEFI menu.

It is this file/folder
 /EFI/Boot/bootx64.efi

And you copy grub or shim into the above folder and rename grub or shim to be bootx64.efi. Of course rename bootx64.efi first. Probably best to back up entire efi partition first also.
Copy from here:

 /EFI/ubuntu/grubx64.efi 
/EFI/ubuntu/shimx64.efi 
Not sure which or if either works. I would expect you need shim if secure boot on. 
Then you should be able to set hard drive as default boot and it should work.

But issue from one time boot key, may be something else?
You could run the full uninstall and reinstall of grub that Boot-Repair suggests. May sure Internet is working as it has to have Internet to download a new copy of grub.

Some systems require boot parameters.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
And a few really require the newest kernel, support software and video drivers that will be in the next Ubuntu in 14.10. There are ppa's to more easily install all that, similar to how you installed Boot-Repair.

---

### Post by jeffhill913 on 2014-06-05
I did a reinstall of ubuntu, pointing boot loader to sda2 (the fat32 part with efi files)
 Still boots directly to win8
   ran boot-repair with defaults
      get an error in boot repair
        using pf9 at boot time I can select ubuntu and get a grub load, but only ubuntu and the win8 restore      	are in the list
 

           if I select EFI then win8 boots
 

 next  rename /boot/efi/EFI/bootx64.efi to bootx64.efi.bkup
          copy /boot/efi/EFI/ubuntu/shimx64.efi to /boot/efi/EFI as bootx64.efi
    still boots directly to win8
 

 next
   copy /boot/efi/EFI/ubuntu/grubx64.efi to /boot/efi/EFI as bootx64.efi
   still boots directly to win8
 

 next run boot-repair using all the default selection and add check to “use the standard EFI file”
   boot repair gets to removing grub, then says grub still there????
 

 I notice that boot-repair installs something from 13.10, I an running 14.4, is that part of the problem?
 

 I found shimx64.efi in boot/efi/EFI so made a bkup and removed  
  still boots directly to win8  
   pf9 and select EFI  boots to win8  
   pf9 and select ubuntu boots grub with ubuntu and win8 for restore only, no regular win8  
       select ubuntu and ubuntu boots  
 

 looks to me that the boot process does not look at the files we have been renaming.
 

 Run boot-repair again using default selections
   error  unable to locate package grubx64.efi.bkup    ??
     then it quits    
    I will remove the grubx64.efi.bkup  from there and try again.
   error  unable to locate package grubx64.efi.bkup  even tho I removed it!!
   will reboot and try again.
 

 Boot-repair says efi detected, check options, so I checked use efi
 An error occurred during the repair.  Not same as above.
            
 [http://paste.ubuntu.com/7595345/](http://paste.ubuntu.com/7595345/) 
 

 still boots directly to win8

---

### Post by oldfred on 2014-06-05
You do have to go into UEFI and set hard drive as first in Boot order. Not sure with HP but most have said they could not set ubuntu entry to be first, but can set hard drive as first in boot order and that work. Otherwise you only can use one time boot key or try the other solutions I posted.

You have this:
>  BootOrder: 3001,3000,3002,2001,2002,2003
Boot0001* Windows Boot Manager
Boot0002* Ubuntu
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk



But there are 4 versions starting at line 9008. Not sure why. I assume one is BIOS, one is secure boot and one is UEFI. Perhaps one is last boot? Not sure and have not seen anything that details that inside UEFI.

 sudo efibootmgr -v
      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

 Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by jeffhill913 on 2014-06-07
Tried to change the boot order
 

 sudo efibootmgr -v     to display
 

 sudo efibootmgr -v  -o 3000,3001,3002,2001,2002     to change order
 

 sudo efibootmgr -v  -o 3002,3001,3000,2001,2002     to change order
 

 sudo efibootmgr -v  -o 0000,3000,3001,3002,2001,2002     to change order
 

 tried reboot after each change, and directly boots to win8
 

 did a display after each set and new boot order shows,  did a display after each pf9 reboot to Ubuntu and the original boot order shows!!

---

### Post by oldfred on 2014-06-07
Either HP or Windows or both somehow reset the boot order to be only Windows.

That is why HPs seem to need all the work arounds or you use f9 one time boot key all the time.

---

### Post by ronb19495 on 2014-06-07
go into bios click open boot tab you should have 2 entries in there windows boot manager and ubuntu if so make ubuntu your first boot option save and reboot ubuntu boot screen should have windows in the boot options.
when I installed 14.04 after windows I had to change boot order in bios to make ubuntu first boot then had to sudo update-grub all was good then

---

### Post by jeffhill913 on 2014-06-08
Tried to change the boot order
 

 sudo efibootmgr -v     to display
 

 original order  3001,3000,3002,2001,2002
 

  sudo efibootmgr -v  -o 3001,3002,3000,2001,2002     to change order
 

 sudo efibootmgr -v  -o 3000,3001,3002,2001,2002     to change order
 

 sudo efibootmgr -v  -o 3002,3001,3000,2001,2002     to change order
 

 sudo efibootmgr -v  -o 0000,3000,3001,3002,2001,2002     to change order
 

 tried reboot after each change, and directly boots to win8
 

 did a display after each set and new boot order shows,  did a display after each pf9 reboot to Ubuntu and the original boot order shows!!
 

 looks like boot order change has no effect.
 

 

 Is this problem only with HP computers?   
 

 This is my first HP laptop, perhaps that was a big mistake on my part.

---

### Post by jeffhill913 on 2014-06-08
Sorry about my last post.  I looked at the forum and did not see my post from 20 hrs ago, so reposted today.  Must be something I did wrong.

---

### Post by jeffhill913 on 2014-06-08
reply to ronb19495, I looked at the BIOS for  boot tab, and this HP G7 laptop does not have that, only a boot order under uefi.  
anyway, thanks for the suggestion.

---

### Post by oldfred on 2014-06-08
HP & Sony seem to hard code the UEFI to only boot Windows. That is not per UEFI standard.

Most with HP do a rename and it does then let you set a drive as first. Or just live with using the key combinations to get to Ubuntu.

And Windows also resets boot order on any maintenance with all systems. Windows thinks it is the only operating system and wants to make sure it works to boot Windows.

---

### Post by jeffhill913 on 2014-06-08
I will continue to use the pf9 route to boot Ubuntu.
I thank the moderator for all of his suggestions and efforts to get this HP G7 laptop of mine to boot grub, instead  of Win8.
It is interesting that I was able to dual boot 13.10 on this computer for a year, but trying to do a fresh install of 14.4 left me unable to dual boot.

---

### Post by ronb19495 on 2014-06-08
> **jeffhill913 said:**
> I will continue to use the pf9 route to boot Ubuntu.
I thank the moderator for all of his suggestions and efforts to get this HP G7 laptop of mine to boot grub, instead  of Win8.
It is interesting that I was able to dual boot 13.10 on this computer for a year, but trying to do a fresh install of 14.4 left me unable to dual boot.this is what intrigues me you say 13.10 did dual boot did it have the grub menu with windows and ubuntu? I have been triple booting windows,  ubuntu,linux mint 17 no problem,but when I installed 14.04 I had the same problem as you,thats when I realized I had to go into bios and change boot sequence to ubuntu.once I had made ubuntu first boot all I did was in a terminal sudo update-grub and it fixed my problem I think something has changed from 13.10 to 14.04 in the way it sets up uefi.When you installed 14.04 did you manually partition with gparted
can you write down the boot order and post on here please I would like to take a look at it thanks

---

### Post by ronb19495 on 2014-06-09
I just tried an experiment ,I uninstalled ubuntu and installed fedora 20 in uefi mode fedora booted ok but from boot screen linux mint or windows didnt boot so I had previously install reFind so I went into bios and made refind first boot priority windows,fedora and linux mint 17 all boot up ok from refind
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by jeffhill913 on 2014-06-09
Reply for rob19495
 

 I think my first uefi install on this HP G7 was 13.4, later upgrade to 13.10, because I bought this laptop may 2013, with win8 already installed.
   
 With 13.10 install next to win8, my default boot would show grub with ubuntu first in line, along with win8.  I could continue with either at that point, and ubuntu was first.  I reviewed my notes on the earlier (june 2013) efi  install and it looks like I ran boot-repair and all was well.   
 

 I noticed this install with 14.4 when I run boot-repair, there is a warning notice that parts of 13.10 will be installed during boot-repair, could this be the problem, something in boot-repair?  I sent a copy of my boot-repair failure to boot-repair but they sent a note that they could not respond to me.
 

 Re boot order... my bios under uefi is internal cd/dvd, then hard drive, no option available to select which partition on hard drive to start.  See my earlier post on trying to change boot order with efibootmgr command.
 

 At this point since I can use pf9 to boot into ubuntu, I will leave grub alone, although I dislike that ubuntu is not booting first, as that is my primary os.  If I did not need win8 for two windows only programs, I would make this laptop ubuntu only.

---

### Post by oldfred on 2014-06-09
Boot-Repair does not have a trusty version.
You have to edit ppa to be saucy as the new install instructions do.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I do not see Boot-Repair creating 25_custom any more with Windows boot entries. With 14.04 grub has been fixed so you do not have to run Boot-Repair to get a working Windows chain load entry with UEFI.

But with the 'buggy' UEFI Boot-Repair would rename the Windows efi file bootmgfw.efi to bkpbootmgfw.efi and make the original file grub's efi file. Then those systems that only boot Windows would think they are booting Windows but really boot grub. But then you could only boot Windows from the new entry by Boot-Repair to chain to the renamed file. That was probably how you booted before?

---

### Post by felix14 on 2014-07-27
FINALLY this works on my Envy M6. 
Changing the boot order!!!!

$ sudo **efibootmgr**[COLOR=#333333][FONT=inherit] [/FONT][/COLOR]**-o**[COLOR=#333333][FONT=inherit] 2[/FONT][/COLOR]**,1**

---

