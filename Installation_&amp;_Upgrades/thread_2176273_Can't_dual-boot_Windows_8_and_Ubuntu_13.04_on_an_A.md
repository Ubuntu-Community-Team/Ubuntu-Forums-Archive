---
title: "Can't dual-boot Windows 8 and Ubuntu 13.04 on an Acer Aspire V5-551G"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by kjellahl on 2013-09-23
I've got a new Acer Aspire V5-551G laptop with Windows 8 pre-installed. I'd  like to also have Ubuntu. It was no problem on my old PC with Windows XP. 

1. When I tried to install Ubuntu, the installation program said "This  computer currently has no detected operating systems." One of the  choices I got was to erase the whole disk, and install Ubuntu. I didn't  want to do that. 
I found a solution at the end of the discussion at  [http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450). 
That way I could install Ubuntu, but I couldn't boot it. Windows 8  started up, without giving me a chance to select anything else. The  description I followed describes problems with a Dell computer, and it says  Ubuntu (not Windows) starts up. It obviously does not completely apply  to my laptop. 

2. Windows is started via Windows Boot Manager. I found this description  of how to dual-boot WIndows 8 and Linux with Windows Boot Manager:  [http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm](http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm). 
After I did as described there, I got the chance to select OS in Windows  Boot Manager, but only the Windows 8 selection worked. When I chose  Ubuntu, the boot manager said some file was missing or corrupted. (I  don't remember the exact wording.) 

3. My latest draw has been to install and use boot-repair from an Ubuntu  live-USB as described at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).  After that I get to Grub when I start up my laptop. There are entries for  Ubuntu and Windows, but only the Ubuntu entry works. Now I can boot into  Ubuntu, but not into WIndows. 

boot-repair gave me the URL [http://paste.ubuntu.com/6142264/](http://paste.ubuntu.com/6142264/) 
boot-repair also asked me to turn off secure boot. That's not  possible in the BIOS/UEFI setup in my laptop. When UEFI mode is selected,  which I suppose it must be in order to use Windows 8, then secure boot  is unconditionally enabled. There is a Secure Boot entry in a setup  menu, but it's not selectable. 

I've got both a Windows 8 recovery disk on a USB stick, and an Ubuntu  live-USB. If necessary, I can re-partition the hard disk, and install  both WIndows 8 and Ubuntu again. 

Did I buy the wrong type of PC, or is there a chance I can  dual-boot on it?
I need both Windows and Linux, preferably Ubuntu. It would be possible but inconvenient to have them in different laptops.

I have sent an email almost identical to this post to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL].

---

### Post by oldfred on 2013-09-23
You are not showing any BIOS boot. And you now have signed kernel so Ubuntu should be booting with secure boot on.

It looks like you used the rename function in Boot-Repair. It moved shim into the Windows boot folder and renames it to be the Windows efi file. Then the Windows file is bkpbootmgfw.efi which you need to boot from your grub menu. If you did not turn hibernation or fast boot off in Windows that may be part of the issue. That is for buggy UEFI implementations that only boot Window's efi file which is not UEFI standard.

This entry should boot Windows.
 menuentry "Windows UEFI bkpbootmgfw.efi"

If nothing else you can undo the rename and then should boot Windows again.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by kjellahl on 2013-09-27
Problem solved, but with considerable trouble.

I ran boot-repair again, ticking *Restore EFI backups*. After that, I could start Windows by moving Windows Boot Manager to the top of the boot priority order in the BIOS/UEFI setup. With the hard disk (HDD) at the top, Grub started, but I could not start Windows from Grub.

This was not satisfactory. I had also added an entry for Ubuntu in Windows Boot Manager. That entry didn't work. I decided to start all over, installing Windows and Ubuntu from scratch.

When I had installed Windows and Ubuntu, the hard disk was not bootable. I could only boot Windows via Windows Boot Manager.
I ran boot-repair once again, now replying **No** to the question *Do you want to activate [Backup and rename Windows EFI files]?*
Now the hard disk became bootable, but when I put it at the top of the boot priority order, BIOS/UEFI said *HDD: has been blocked by the current security policy*. I assumed I should disable secure boot. After a lot of searching on the Internet, I found how to do that, and now I can select Windows or Ubuntu from Grub. At last!


**[SIZE=3][SIZE=3]H[/SIZE]ow to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G.[/SIZE]**

It's probably done similarly on some other Acer models.

**Backup your Windows 8 system**.
(My experience says that there is a high risk that you will have to, or want to, start all over by installing Windows on a cleared disk.)
From the control panel in Windows, create a bootable recovery device on a USB stick.
If you have personal files you want to keep, back them up.

**Turn off Fast Startup in Windows.**
Described here: [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

**Download and prepare Ubuntu live-USB.**
Download as described here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Create a bootable live-USB as described here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

**Shrink the C:\ drive to free some space for Ubuntu.**
See [http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450), the post entitled *SOLUTION*, section *SHRINK C:/ DRIVE TO FREE SPACE FOR UBUNTU*.

**BIOS/UEFI setup.**
Reboot or power on the computer. When the Acer start screen shows up, press F2, to get into the BIOS/UEFI setup.
Go to the Boot tab, move USB HDD to the top of the list of devices to boot from.
(Always keep the setting Boot Mode: [UEFI]. If you change it to [Legacy BIOS] it may be easier to boot Ubuntu, but you will not be able to boot Windows 8.)
Save changes and exit, entering Windows, if you have not inserted the Ubuntu live-USB.
Turn off the computer.

**Install Ubuntu.**
Insert the Ubuntu live-USB.
Turn on the computer.
Now follow [http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450), the post entitled *SOLUTION*, section *INSTALL UBUNTU*, from step 5, beginning *The system will reboot and you will see the grub textual menu.*
Once the installation is complete, if you remove the live-USB, the computer will boot straight into Windows 8, not giving the option to select Ubuntu.

**Repair the bootloader.**
Use boot-repair, as described here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can use it from the live-USB, selecting "Try Ubuntu" in the Grub menu.
Run boot-repair, select *Recommended Repair*.
If you get the question *Do you want to activate [Backup and rename Windows EFI files]?*, answer **No**, even if it's not the preselected alternative.

**Change the boot order.**
Reboot, or power up, press F2 to get into the BIOS/UEFI setup.
Go to the Boot tab, put the hard disk (HDD) before Windows Boot Manager.
If you don't plan to boot from USB any more, you can move USB HDD down in the list. But you can also wait with this until you see that everything is working.
Save the changes and exit.
You may now get the message *HDD: has been blocked by the current security policy*.
If so, you must disable secure boot.

**Disable Secure Boot in the BIOS/UEFI setup (if necessary).**
In the Boot tab there is the setting Secure Boot: [Enabled]. It's grayed out, and can't be changed. The trick to unlock it is mentioned in a line here: [http://community.acer.com/t5/Notebooks-Netbooks/How-do-I-disable-secure-boot-on-an-Aspire-V5-171/td-p/44003](http://community.acer.com/t5/Notebooks-Netbooks/How-do-I-disable-secure-boot-on-an-Aspire-V5-171/td-p/44003)
(Be sure you **remember the supervisor password you se**t, or else you will have great trouble ever getting into the BIOS/UEFI setup again.)
Create a supervisor password. Described here: [http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
Then several locked settings are unlocked.
Change Secure Boot to [Disabled].
Optional: Remove the supervisor password. Described here: [http://acer.custhelp.com/app/answers/detail/a_id/29353/](http://acer.custhelp.com/app/answers/detail/a_id/29353/)
When you reboot, the Grub screen is shown. From there you can start either Windows or Ubuntu.

**Clean up the BIOS/UEFI settings (optional).**
When you have confirmed that everything is working, you may want to clean up the BIOS/UEFI settings, if you haven't done so before.
Remove the supervisor password.
Change the boot priority order. HDD must remain before Windows Boot Manager, but you may want to move USB HDD after those two.

---

### Post by oldfred on 2013-09-27
Glad you got it working. :)

Thanks for update. Others will find this thread and it will help.

---

### Post by martinr on 2013-11-09
A new install worked more quickly for me.

Just make sure that you don't boot the installation CD with a UEFI boot sequence if your HD structures is MSDOS with MBR or vice versa.
(See: [this thread]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957"))

---

