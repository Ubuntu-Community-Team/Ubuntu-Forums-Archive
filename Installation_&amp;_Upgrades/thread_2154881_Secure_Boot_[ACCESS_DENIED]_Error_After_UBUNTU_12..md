---
title: "Secure Boot [ACCESS DENIED] Error After UBUNTU 12.04 Install"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by JaneNova on 2013-06-16
Hello,

I recently purchased an Acer Aspire V5 Touchscreen Ultrabook.  I decided to wipe my system clean and install Ubuntu.  Unfortunately, I did not realize that I needed to change certain aspects of the Boot menu with Windows 8 before wiping it clean.  After installing Ubuntu, I receive a tiny image that lets me know that "Secure Image Failed to Load *ACCESS DENIED* Click any key [OK]."  After I click a key, a black screen shows up with a simple sentence at the top, "Operating System Not Found."

After examining many forums and doing a "boot repair," experimenting with renaming the EFI file in the USB (which actually caused the live CD not to start, I had to name it back), and reading very complex coding suggestions, I am at a loss as to what to do.  It seems that most people have had this issue while installing dual booting, and I haven't found any forums that address what happens when you install Ubuntu only.

My boot repair link is:  [http://paste.ubuntu.com/5770382](http://paste.ubuntu.com/5770382) 
I also did a second one:  [http://paste.ubuntu.com/5770502](http://paste.ubuntu.com/5770502)

Any help is greatly appreciated!

JN

---

### Post by oldfred on 2013-06-16
You can turn secure boot off in UEFI settings and it should then boot.

Or you can boot a live system with Boot-Repair in secure boot mode and tick secure boot checkbox. It will then update grub and add signed kernels that will boot with secure boot on.

 One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

      
 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

Since you have only one system installed, are you perhaps booting but having video issues? 

If you hold shift key from UEFI/BIOS do you get a grub menu? Grub menu is not normally shown with one system as you do not need to normally choose which system to boot. Only if you need recovery or memtest would you want menu which shift should give you.

---

### Post by JaneNova on 2013-06-16
Thanks for replying @oldfred.  :)

I only have one system installed and it will not boot.  A boot menu does not show up, the image that says Secure Image *ACCESS DENIED* shows up, I press a key (and I tried hitting the F12 key when the ACER screen shows up), then it turns black and says Operating System Not Found.  I called the ACER people since it's still under warranty to see if I could get the system restored back to factory settings (then I can take care of the boot stuff in Windows and try to re-install).  Apparently, that will cost me 100 bucks?!  I really want to try to hack this on my own, but I don't know what to do.  

The only time GRUB shows up is if I use a LiveUSB.  Otherwise, nothing.  Now that Windows has been wiped off the system, I can't retroactively changed its boot settings.  Not sure what I should do...!

---

### Post by oldfred on 2013-06-16
Can you not get into UEFI to turn off secure boot? That is a Microsoft requirement to offer Windows 8 that the user be able to turn secure boot off.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by JaneNova on 2013-06-16
@oldfred, correct.  I did not do this *before* installing Ubuntu, and that caused the installation to result in the error message, "Operating System Not Found."

---

### Post by oldfred on 2013-06-17
Since you have secure boot on, and can boot with Boot-Repair, you should be able to use Boot-Repair and tick the secure boot box. That will then install the shim file that has the Microsoft key, and install the signed kernels to boot with secure boot on.

---

### Post by JaneNova on 2013-06-17
@oldfred, thank you so much for helping me!  I will try re-installing boot repair later this evening and reply ASAP.

---

### Post by JaneNova on 2013-06-24
@oldfred

I've read through all of the links that you provided, did another boot repair, and the system will not boot without a LiveUSB.  I also tried to put in the Windows recovery CD, but it won't boot or respond or anything.  The manufacturer will reset it back to factory settings for 100 bucks.  I don't want to do that, but I'm frustrated that I bought a new computer and have no control over my OS.  Again, I should have done my homework first, but how could I possibly know that BIOS was history?!  Ugh, so so so upset....

I appreciate your help anyway...!  

Would installing a different version of Ubuntu make a difference?  I have 12.04 on that USB, but I could wipe it and re-install the latest version...

Thanks again!

---

### Post by oldfred on 2013-06-24
Both UEFI from Vendor and Operating systems Windows & Linux are getting significant updates as UEFI and particularly Secure Boot are all new.

The latest may be a bit better, but some computers just have issues and it is the vendors fault as Ubuntu & secure boot do work for many.
I am quite surprised they want $100 to fix system. 

Post the link to a new run of the BootInfo report from Boot-Repair. But it also may need some settings in UEFI/BIOS which we cannot see and you may just have to try.
Did your system boot with secure boot off? It should but many do not.
Then many only boot the Windows efi file with secure boot on.

You can restore the Windows efi file and then it should directly boot Windows if you choose in in the UEFI boot menu (not grub).

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

That should work but Windows also keeps a copy of its boot loader file:
      
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
You should be able to copy to the efi partition in the Windows folder. Depending on how you mount it, it will be here, but the /boot/efi is from inside a working Ubuntu. If from liveCD it will be /media/....

 /boot/efi/EFI/Microsoft/Boot/bootmgr.efi

---

### Post by JaneNova on 2013-06-30
@oldfred, thanks for the reply.  I'm sorry but I am a bit intimidated by  the language you use to fix the system.  In particular, my  understanding is inhibited by the fact that Windows no longer exists on  my system, so I don't know how restoring a windows file will then boot  back to Windows.  This is all over my head.  If I rename files, what  should they be renamed to?  I am assuming the system is booting with  secure something because that is precisely what won't let me bypass the  ACCESS DENIED error message.  GRUB menu shows up only when a LiveUSB is  inserted.  Again, I apologize for being below the learning curve of many  Linux users, but if you break it down for me I am willing to learn and  try to fix the error so that other users in my situation don't have to  go through this!  Much appreciation for your speedy responses!

---

### Post by oldfred on 2013-06-30
Sorry post #9 was about repairing Windows but you have erased it. 

The live installer has this menu entry.
menuentry 'System setup'
 {     fwsetup }

And should be able to run the code to get into the UEFI menu. Does that work?

Since you only have Ubuntu, it will not show a grub menu unless you hold shift key down from BIOS/UEFI. Some have reported with UEFI that shift does not work but escape key does work. Do either of these give you a grub menu when booting without flash drive installer?

---

### Post by ubfan1 on 2013-06-30
As long as you can boot your Ubuntu live media, you can fix things.  As a background task, next time you boot or next get into UEFI settings/BIOS, try to see what your machine's firmware version is, and do check the vendor web site for any updates.  Taking a look at OldFred's suggestions, try the efi boot, which you should be able to start with a function key (each machine is different, can't say which one).  The correct function key should list the boot devices for you to choose -- if you just see a hard disk (HDD) choose it, and you should then get to choose ubuntu or windows.  Try Windows, but after running boot-repair, you will probably get the grub menu, just like you should when you select ubuntu.  That's because boot-repair has renamed the windows boot files, and put a copy of shim.efi in their place.  You can rename them back yourself, or run boot-repair and "restore backup files".  The backup files all have bck in their names, so it's easy to tell what they should be (same name without the bck).  So, where are these files you ask?  They are in the EFI boot partition, which MAY be automatically mounted by the live media.  Such automounts  are done in /media, so look for any subdirectories in /media:
```
ls /media
```
Expect a directory with 8 or 9 numbers and letters, look into it:
```
ls /media/????-????
```
Expect to fine a directory named EFI.  Look into it and you should see directories named "Boot", "Microsoft", and "ubuntu", and may others which the vendor may put there.  The Windows files are under Microsoft in another directory named Boot, so 
```
ls /media/????-????/EFI/Microsoft/Boot
```
should list all the (renamed and backed up) windows boot files.
You can look into the ubuntu directory, and see the shimx64.efi and grubx64.efi, and grub.cfg files ubuntu needs to boot.
use the -l switch after the ls above to see the sizes of the files -- since they have been renamed, you can tell what they really are by their size, expect many files to be the same size as the shim.efi file -- they're copies.  Now, your efi boot menu probably points to /EFI/Microsoft/Boot/bootmgfw.efi (or bootmgr.efi I don't know what they do differently). but both are probably copies of shim.  I'd guess the original bootmgfw.efi is now named bckbootmgfw.efi, so just copy it back to it's original name (overriding the shim copy):
```
cd /media/????-????/Microsoft/Boot
sudo cp bckbootmgfw.efi bootmfgw.efi
sudo cp bckbootmgr.efi bootmgr.efi
```
OK, now you can try the efi boot menu again and see if you have windows back.  If you can run boot-repair, all those renames should be done for you by checking the restore backup files, but now you know what's going on under the hood so to speak.
One step at at time, and you'll get there.  Your Windows install probably is fine, just the booting was messed up.

---

### Post by oldfred on 2013-06-30
@ubfan1
If you look at pastebin in first post, JaneNova has totally deleted Windows. Only the boot files in the efi partition are left, but no Windows partitions.

---

### Post by ubfan1 on 2013-07-02
Sorry about prev post, didn't look carefully enough at history.
Missing grub menues may also be caused by the /etc/grub.d/30_os-prober script setting the timeout to 0 when no Windows is found.  You can remove the executable flag on the script and it won't run in the future:
```
sudo chmod -x /etc/grub.d/30_os-prober
```
You can edit the grub.cfg file to remove the unwanted timeout code between the lines:
> ### BEGIN /etc/grub.d/30_os-prober ###
<snip>
### END /etc/grub.d/30_os-prober ###
Rerunning "sudo update-grub" would also fix the grub.cfg file.

---

