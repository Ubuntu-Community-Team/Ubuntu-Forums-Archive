---
title: "Os-uninstaller question?"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by tomsubt on 2014-03-25
Hello Everyone,  I used the OS-Uninstaller and removed windows successfully and it states the ubuntu os is still present, so after I 
restarted the pc instead of starting with Ubuntu, I got a "Operating system not found please insert a disk and press Enter"
So I brought up the OS-Uninstaller again and the Only OS it asked to Uninstall was Ubuntu, so I closed out knowing ubuntu is still on the pc
My question is How to get the pc to start with ubuntu now that windows has been removed? Any Help would be appreciated very much. Thanks

---

### Post by Dave_L on 2014-03-25
Can you boot into Ubuntu from the Live USB or Live CD/DVD you used to install Ubuntu?

If so, I would try re-installing grub (the boot loader):
[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

---

### Post by grahammechanical on 2014-03-25
It is my guess that your system was using the Windows boot loader. So, that when Windows was removed then its boot loader was removed and the machine was left without any information about where to look for a boot image.

If Grub was the boot loader then removing Windows should not have affected the Grub boot loader but you may have needed to load into Ubuntu and run sudo update-grub to get rid of the Windows entry in the boot menu.

If we use OS-Uninstaller as part of a Linux Secure Remix live session then after removing the unwanted OS we can run Boot-Repair to fix any possible boot problems before we accept the advice to reboot.

[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Regards.

---

### Post by tomsubt on 2014-03-25
When I put the command in "sudo update-grub" it stated that the Device not found /(its/dev mounted?)

---

### Post by oldfred on 2014-03-25
A few systems give that error even when grub is in MBR. They look for a primary partition with the boot flag which is the Windows requirement. But grub does not use boot flag.

Best to see all details:
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by tomsubt on 2014-03-25
Ok I already have a boot repair disk, Should I run it again and get the Link to its results and send them here? Is this what you need?

---

### Post by oldfred on 2014-03-25
You can run BootInfo report from its own liveCD or flash drive or just install to your Ubuntu live installer.
It will give you a pastebin link, post that.

---

### Post by tomsubt on 2014-03-25
ok, here is the boot info>>>  [http://paste.ubuntu.com/7152947](http://paste.ubuntu.com/7152947)

---

### Post by oldfred on 2014-03-25
You have a Windows boot loader in the MBR, but no bootable Windows partition. You should have Boot-Repair install grub to MBR.

You do show a partition inconsistency. It looks like sda2 is formatted ext3, but partition table says it is fat32 and has Windows boot flag. That could have been an old XP although most XP installs are in NTFS.

If sda2 was your Windows you may want to see what testdisk says about it.
 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

   repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by tomsubt on 2014-03-25
You said>>>   You should have Boot-Repair install grub to MBR.

How do  I go about doing this, is there a terminal command I have to use? Thanks

---

### Post by mastablasta on 2014-03-26
the boot repair tool when you click repair boot should do that for you.

---

### Post by tomsubt on 2014-03-26
> **mastablasta said:**
> the boot repair tool when you click repair boot should do that for you.

ok I put the boot repair disk in and the first screen to come up said>>>

"pc is in Legacy mode you may want to retry after changing it to efi mode
Alternately you may want to Re Try after Deactivating the [seperate/boot/efi partition:]
DO YOU WANT TO CONTINUE <<<

My question is first do I run the repair first and how do i change to the efi mode/

Also How to Deactivate the serperate boot efi partition?   Thanks

---

### Post by oldfred on 2014-03-26
UEFI and BIOS are not compatible. You cannot change modes except by rebooting. From UEFI menu you should get two boot options, one UEFI and the other Legacy/BIOS/CSM or something that is not UEFI.

If you install in UEFI mode, your fstab also mounts the efi partition. If you install in BIOS mode you do not have that entry. But I think that is more for updates. 

There are two versions of grub, grub-pc(BIOS) and grub-efi(UEFI) which configure system and where grub is installed differently to match how you boot system.

---

### Post by tomsubt on 2014-03-26
> **oldfred said:**
> UEFI and BIOS are not compatible. You cannot change modes except by rebooting. From UEFI menu you should get two boot options, one UEFI and the other Legacy/BIOS/CSM or something that is not UEFI.

If you install in UEFI mode, your fstab also mounts the efi partition. If you install in BIOS mode you do not have that entry. But I think that is more for updates. 

There are two versions of grub, grub-pc(BIOS) and grub-efi(UEFI) which configure system and where grub is installed differently to match how you boot system.


I am not getting any boot options at all, would installing  the grub-pc (bios) or is it the grub-efi (uefi)  help if so how?>>
Thanks

---

### Post by tomsubt on 2014-03-26
I tried installing grub and ran the repair again please see here and perhaps let me know what I can try>>>>>

[http://paste.ubuntu.com/7157210/](http://paste.ubuntu.com/7157210/)

PS, what gets me is it says the boot was repaired but still getting os not found?

---

### Post by oldfred on 2014-03-26
You are not showing anything related to UEFI, just BIOS. UEFI is only on very new computers and all new pre-installed Windows 8 systems.

You show a Windows boot loader but no Windows to boot from.
Windows uses boot flag which must be on the NTFS (maybe FAT32) primary partition with Windows boot files. UEFI also used FAT32 with boot flag on gpt partitioned drives. But your drive is MBR which only boots with BIOS.
You have boot flag on sda6 a logical partition with Linux so that is not a syslinux (Windows type) bootable partition.
Be sure to boot Boot-Repair or Ubuntu live install in BIOS mode and install grub to MBR, not an efi install. You may have to select manual install as it seems to want to try to use UEFI which is not correct. If not just manually reinstall grub to MBR.

A few BIOS will give errors if boot flag is not on a primary partition.

I do not know why Boot-Repair is even mentioning efi???
> Recommended-Repair
This setting would reinstall the grub-efi of sda6, using the following options:        sda2/boot/efi,

Boot-Repair also has the option to totally unstall grub & reinstall. You may need to do that to uninstall grub-efi (UEFI) and install grub-pc(BIOS). Not sure how you could have even gotten grub-efi installed unless you somehow forced that from a BIOS boot?

---

### Post by tomsubt on 2014-03-26
Ok you said>>>  Boot-Repair also has the option to totally unstall grub & reinstall. You may need to do that to uninstall grub-efi (UEFI) and install grub-pc(BIOS). Not sure how you could have even gotten grub-efi installed unless you somehow forced that from a BIOS boot? <<<


I never saw that option come up on the repair disk UNTIL just now and it reinstalled grub and I can now boot into Ubuntu without windows showing up, Thank You Guys Very Much

But I have to ask this one more question,  when I now boot the pc it has 3 different linux options on the screen and I missed what is said but I let it just start up by itself 

I do know the third option was to start with the Previous Version On linux should I have chosen that?

Also how can I get the boot screen to stay open longer so I can view the 3 Options. it must be set for 10 seconds or less right now, please let me know and I will relate the boot options to you guys, Thanks

---

### Post by oldfred on 2014-03-26
Your default on grub menu is 10 sec. But if you only have one system, it will not show menu unless you hold shift key down from BIOS screen until menu appears. It assumes you want to boot default unless you have issues.
 You really should not need more than 10 sec normally. But it can be set to forever, but do not change to 0 as that leads to other issues.

You will get with every new kernel a two new boot lines in grub menu. Boot and boot recovery. There also is a memory test if you seem to have hardware issues.
Best to periodically houseclean kernels. They do not take a lot of room but more than two are not necessarily. I let it grow to 3 or 4 then houseclean down to 2, current and previous just in case current develops issues.

[https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior](https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior)
 sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
      
 sudo update-grub

      
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a

 In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

I prefer synaptic, but that is not now installed by default.

---

### Post by tomsubt on 2014-03-26
Oldfred,  Thanks  I held down the shift key as instructed and got a good look at the boot menu

The first and default says  Its Generic

The Second is the Recovery

The third is the Previous Linux

Should I be using the Previous or is it ok to stay with Generic (BTW, I did alot of upgrades using this default, if that matters or not I dont know?

Also, At start up and Just before the linux boot screen I am still getting a windows screen with the option to recovery etc, but there is no recovery and never was it was deleted by some one who owned the pc before.
I installed Gparted and one of the entries was  Dev/sda2/1.49Gib(ntfs)  is this the old windows splash screen, I can delete it if it is, right? Please let me know am anxious to get rid of all the windows items. Thank You

---

### Post by oldfred on 2014-03-26
Grub's default is always the first entry. And that is what you want to use unless you have issues. Then you try recovery, or older kernel depending on issue.

Do not know what screen you are getting as recovery? Is that something from BIOS. Grub in MBR should not show anything other than grub menu.

Often BIOS has settings to turn off BIOS splash, but sometimes then you have difficulty getting into BIOS to fix settings later. Depends a lot on BIOS. Best to see if there is a manual on line for your system.

---

### Post by tomsubt on 2014-03-26
The recovery is ok its for the ubuntu for linux 3809 recovery
the default has the same numbers (not sure of the 3809 as the exact numbers)

The windows splash screen that comes up and disappears quickly is I believe from the old bios of windows xp that was on the pc before, for some reason this did not get removed but all other parts of the windows were removed.

What could a manual do to help me get rid of this screen, I keep thinking I could remove it from the partition screen or am I wrong?  Thats why I asked if the "dev/sda2/1.49 (unknown) was the windows screen thats keeps flashing on startup?

---

### Post by oldfred on 2014-03-26
Grub will not show any Windows splash screens. That has to be something from BIOS and I do not know if you delete something that BIOS also wants to see if you have major boot issues.

I would at least back it up before deleting to be on the safe side.

Normal boot process is BIOS checks what hardware you have and writes that info, then transfers to MBR where then grub takes over boot process and loads initrd and kernel. Then the boot process reads hardware info to know what drivers to load. There is no Windows in that process unless you had wubi inside the NTFS partition.

---

### Post by tomsubt on 2014-03-26
Well, I dont have Wubi inside! I had windowsxp side by side with ubuntu

Also the quick flash of windows screen always appears just before Grub boot screen?

I dont know how to get at it to remove it, what do you think I might try?

If I cannot do it its no big deal I just dont like it!  Thanks

---

### Post by oldfred on 2014-03-26
Can you use camera and get a decent photo? You need to then shrink to screenshot size and can use advanced editor and paper clip icon to upload screenshot. 

I had to take photos of all my BIOS screens, so when updating BIOS I knew what settings I had changed.

---

### Post by tomsubt on 2014-03-26
I dont have a camera always wanted to get one.  My cell phone takes still pictures but I dont know if it will come out clear will try it in the morning and get back to you.

How can I get into the bios when using ubuntu?

---

### Post by oldfred on 2014-03-27
Getting into BIOS is not related to Ubuntu or Windows at least until you have UEFI with Windows 8.

You have to press a key to get into BIOS, but varies by vendor.

Some examples, if one does not work try another.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by tomsubt on 2014-03-27
Thanks, I got into the windows bios and have it up now can I disable the windows splash screen from coming up
at the start up of the pc from this bios screen?

---

### Post by oldfred on 2014-03-27
BIOS is not Windows.
Some BIOS will let you minimize the BIOS screens, others just show BIOS loading. 
My old BIOS used to take forever loading memory and other hardware devices, but it had a setting to skip showing most of that.

---

### Post by tomsubt on 2014-03-27
So do you think I am stuck forever with the windows splash screen coming up on each startup just before ubuntu?  Theres No way to get rid of it?

---

### Post by oldfred on 2014-03-27
I do not know if you are seeing Windows or just BIOS. 
The only reason I do not think it is Windows as it also loads after BIOS and you now have grub installed to MBR, so there should not be any Windows anywhere.
Without seeing screen I do not know what is going on.

---

### Post by tomsubt on 2014-03-27
I took a picture of it with my cell phone but dont know yet how to transfer picture to my computer to send to you. Have you ever done this?

---

### Post by tomsubt on 2014-03-27
ok, I found a cord that connects the cell phone to the computer and even though it did not find a driver for the cell phone it states it is ready to use.
If I can get the picture up would I be able to send it to you as an attachment?

---

### Post by oldfred on 2014-03-27
Forum has rules on size limits, so you have to shrink it. Then use advanced editor and paperclip icon to attach photo.
I regularly copy photos from iPhone 4s to Ubuntu for backkup, but lately have had some permissions issues. But eventually it works. I did have to add some drivers originally, but have not tried any of the fixes they suggest for the permission issues, yet.

---

### Post by tomsubt on 2014-03-27
Thanks, but I am having problems I am using a tracfone with camera (only still pictures) any way I have good snap shot of the HP invent splash screen that comes on at startup.
It stated the phone was ready to use but could not install the Driver for some reason so I could not get it onto the pc. will have to see where I can get the driver for a LG420 Cell phone
Maybe there website I dont know but will let you know.

---

### Post by tomsubt on 2014-03-27
I was wondering if I took out the cmos battery would that do anything to ubuntu?

---

### Post by oldfred on 2014-03-27
That resets BIOS to defaults. 
And defaults may need to be reset to settings that are correct. That's why I took pictures of my working settings.
But it would not make any difference to Ubuntu or Windows.

If battery is older and run down it can make for issues as it will keep resetting to defaults. But you normally see that when time is not correct.

---

### Post by tomsubt on 2014-03-27
Here is a picture of what I get when I start pc up just before Linux default screen>>

[https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcTt4YToQxgqBJd59HaithiPrO9FkwcIeOsMgOPnDT2UGD4ca_H6lA](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcTt4YToQxgqBJd59HaithiPrO9FkwcIeOsMgOPnDT2UGD4ca_H6lA)

---

### Post by oldfred on 2014-03-27
That looks like a standard BIOS boot screen. I am not familiar with HP but similar to other systems I know.
Some do have BIOS setting to minimize how long you see that screen.

---

### Post by tomsubt on 2014-03-28
> **oldfred said:**
> That looks like a standard BIOS boot screen. I am not familiar with HP but similar to other systems I know.
Some do have BIOS setting to minimize how long you see that screen.

Yes, It is, and I know how to set it to (0) so it wont show anymore but as far as i know it cannot be dont Until you bring up MsConfig then Boot .ini  thats were the setting is, but I cannot get anything up like msconfig on windows anymore since removing it.
I wonder I see in GPart that there is an item or two with just the size (0)in them, could one be a left over windowsxp, Not sure will have to look again but one says sda2?

---

### Post by oldfred on 2014-03-28
With BIOS operating systems did not change BIOS settings, although now with UEFI operating system can change some UEFI settings. You may be thinking of Windows timeout in boot.ini on Windows boot screen which also is after the BIOS screen.

As I posted before be sure to backup anything you delete just in case. It probably will not matter, but the one time you do not back it up is the one time it does matter.

---

### Post by tomsubt on 2014-03-28
Yes Your right so I guess I am stuck with this windows screen flashing first and the only way I can see to get rid of it is to reinstall ubuntu which I really dont want to do? Thank You

---

