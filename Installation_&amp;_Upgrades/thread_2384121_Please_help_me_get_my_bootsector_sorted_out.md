---
title: "Please help me get my bootsector sorted out"
date: 2018-02-02
forum: Installation &amp; Upgrades
---

### Post by kekstastisch on 2018-02-02
Hey guys!
I wanted to install ubuntu on a usb drive
I know about live versions but those reset everything you do on them

So i got 2 usb sticks
One with the ubuntu image
And an empty 32 gig on witch i installed ubunu on


I plugged both into my windows laptop and started the installation and chose the 32 gig usb stick
The installation was done and told me to reboot

But i removed both drives to look if windows was still working

Then this showed up [https://m.imgur.com/FARLa7E](https://m.imgur.com/FARLa7E)

Even if i put the drives back it does the same

Please help

---

### Post by oldos2er on 2018-02-02
Is your system UEFI or MBR? Please tell us your hardware specs.

---

### Post by ubfan1 on 2018-02-02
That's bug 1173457.  You should be able to boot Windows with the 32G USB present.  If the grub menu with Windows does not boot Windows, maybe secure boot needs to be disabled.

---

### Post by kekstastisch on 2018-02-02
@ubfan I am really sorry i am a noob in linux so please explain stel by step

Its an uefi

Asus gl502vs
Really expensive
Nvidia 1070 16gb
Intel 7800hq
A nvme ssd and a 1t hdd

I dont even see a menue thats the problem

Omg did i mess my laptop up i am panicing

---

### Post by ubfan1 on 2018-02-02
Don't panic, only the bootloader is in the wrong place (the hard disk, not your fault).  I have to go out a bit, but will check in later if more help needed.  Try putting the USB you installed to (not the install media USB) and see if you get the grub menu.

---

### Post by kekstastisch on 2018-02-02
Still the same
Thanks for help
I need it fast

---

### Post by yancek on 2018-02-02
You may have mixed MBR and EFI installs.  If you can boot the Ubuntu install usb, do that and run the following command and post the output.

> sudo parted -l

Lower case letter L in the command.  This will be useful to see if you have an EFI partition.  If you do you can boot Ubuntu from the grub prompt you now see on boot.

---

### Post by kansasnoob on 2018-02-02
I assume that you can still boot the live USB - the one you used to install Ubuntu, not the one you installed Ubuntu on. In order for us to figure out what went wrong we really need to see the boot info script as produced using Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That can be run using the live USB. **DO NOT run the recommended repair!** Only use it to create a boot info summary and then post the link here so we can actually see what's wrong. Just trying stuff haphazardly without troubleshooting can make things worse!

We would get the most complete picture of what's wrong if you're able to boot the live USB with all drives connected but the most important thing is to see what we've mucked up in Windows. It's possible that Ubuntu installed in non-UEFI mode which then resulted in the installer planting an MBR on the GPT drive.

---

### Post by kekstastisch on 2018-02-02
error: can't find command 'sudo'.

---

### Post by kekstastisch on 2018-02-02
Nothing works 
Not windows and not ubuntu and not the boot media

---

### Post by TheFu on 2018-02-02
Until you help us by providing the requested information, we cannot help you.
"nothing works" isn't useful, sorry.  Follow the boot-repair link above and do what kansasnoob suggests.

---

### Post by kekstastisch on 2018-02-02
I cant do that because i cant enter ubuntu

---

### Post by QIII on 2018-02-02
What DOES happen?  

Does your machine boot?  Does it pass POST?  Do you see the BIOS flash screen?  Can you enter the BIOS menu?  Does the GRUB menu appear?  Do you see anything when you select something from GRUB?  Can you enter recovery mode? Does the Ubuntu splash screen appear?  Are you greeted with the login screen? 

Do you still see only the GRUB Rescue screen?

Paint us a word picture.

Again: "Nothing works" is of no value in diagnosing thhe issue.

---

### Post by genericvii143 on 2018-02-02
Okay, let me show you the way bud here is the deal since you already have booth-able  USB with your Linux  then you  need to go the BIOS  of the computer and switch the UEFI  to the Legacy then  go to the boot options and put External media  aka USB  1st and then everything else come in 2th 3th Etc. After that save and exit then make sure that the USB is plug in the PC and press okay and the PC automatically will reboot and it will run the setup process please Let me know  if you need any further instructions.

Best regards,
JInx

---

### Post by TheFu on 2018-02-02
An Ubuntu ISO on a flash disk doesn't need legacy boot from the BIOS.  Changing to legacy from UEFI will cause issues later.

The OP should use the already created flash drive and "Try Ubuntu", then gather the information requested.

---

### Post by ubfan1 on 2018-02-02
Windows is installed in UEFI mode, so you want to install Ubuntu in UEFI mode.  Unlike legacy, the bootloaders do not overwrite each other, one is set as the default, but you may select which one to run via the EFI menu (invoked with some function key like F12 at power-up).  Selecting Windows should run the Windows bootloader, and ignore grub.  Now the grub problems may be addressed without worrying about Windows.  You have a number of confusing issues, which don't seem to be related (missing sudo???). 
The UEFI grub install went to the EFI partition on the hard disk, directory /EFI/ubuntu. It should run from there just fine, but  does require the presence of the USB on which you installed Ubuntu.  A better way is to copy everything in the hard disk's EFI partition to the USB's EFI partition (check that it does have an EFI partition).
Then the USB device, when selected for booting (either via the device bootorder or the EFI menu) should boot Ubuntu.  To "Fix" the hard disk's boot, all that needs to be
done is to change the EFI bootorder from Ubuntu first to Windows first.  From Ubuntu, the efibootmgr program can change the EFI order.

When you get grub displaying a menu, that menu should contain a Windows entry.  Some machines cannot boot Windows from grub when secure boot is enabled, so disable it (or make Windows first in the bootorder, and use the EFI menu to boot grub).  You have Nvidia hardware, so will probably need to add the "nomodeset" word to the grub line starting with "linux" (at the "quiet splash" words).  That should get you to the desktop, where you can run Software Updater, update your package index, and
install the proprietary Nvidia drivers (under Alternate DRivers tab).  The Nvidia detail instructions are well covered here and in askubuntu.com -- do a search to take a look at them.

---

### Post by genericvii143 on 2018-02-02
I bet everything that what i said early will work but is up to the him to listen to.

---

### Post by QIII on 2018-02-02
Perhaps it would.  But if Windows is installed UEFI, which is a more modern system with many advantages, why would you ask the user to change the Windows arrangement -- which apparently worked -- when installing Ubuntu as UEFI is just as easy and produces a cleaner result?  Why risk further breakage?

Furthermore, since the user's machine is in an as-yet unknown state, blindly reinstalling might cause even more damage.

Your advice was simply not the most efficient nor was it recommended.

---

### Post by kansasnoob on 2018-02-02
> **genericvii143 said:**
> I bet everything that what i said early will work but is up to the him to listen to.

Clearly NOT. The OP indicated in post [#10]("https://ubuntuforums.org/showthread.php?t=2384121&p=13736391#post13736391") that he can't even get the Live USB to boot :(

---

### Post by kansasnoob on 2018-02-02
> **kekstastisch said:**
> Nothing works 
Not windows and not ubuntu and not the boot media

Then the process of installing Ubuntu probably planted grub on the live USB .................. maybe ???????????????

All I can do is guess and that's not a sufficient method of fixing anything.

One thing we could try that shouldn't create additional problems is looking at the UEFI boot menu during system boot.

Is this the right laptop:

[http://dlcdnet.asus.com/pub/ASUS/nb/GL502VS/0409_E11526_GL502VT_VY_V2_A.pdf?_ga=2.72148307.1304198542.1517617788-225858261.1517617788](http://dlcdnet.asus.com/pub/ASUS/nb/GL502VS/0409_E11526_GL502VT_VY_V2_A.pdf?_ga=2.72148307.1304198542.1517617788-225858261.1517617788)

If so it says you can access the BIOS/UEFI settings at boot by pressing F2. If you have Fast Boot set it really is FAST! So pretty much as soon as you press the power button you have to start pressing F2. In my own experience just pressing and holding doesn't often work, so 'tap-tap-tap'. I would turn off Fast Boot at this point if it's turned on. I would NOT get too carried away making any other changes at this point.

They weren't nice enough to say which key to push at boot-up to display the boot menu but I'd try either Esc or F8 when the laptop first boots - before that grub screen appears - to see if the UEFI boot menu appears. Unless the EFI boot partition (ESP) is damaged you should see more than one option and hopefully at least Windows will boot using that method. Then maybe we need to create a new Live USB so we can properly diagnose things.

---

### Post by genericvii143 on 2018-02-02
How about if he switch UEFI  to Legacy?

---

### Post by QIII on 2018-02-02
@genericvii143:

Please read through the thread again and desist.

---

### Post by kansasnoob on 2018-02-02
> **rbmorse said:**
> Jinx, that is the worst possible thing he could do at this moment.  Please read the other messages in the thread.

+1! Clearly the OP wants to get his Windows boot back. Drastically changing settings could, and in this case likely would, make his Windows install that much more difficult to recover.

If he can get the UEFI boot menu to appear and get Windows to boot from that, or maybe change the boot settings in BIOS to boot Windows first, then we need to get a bootable Live USB working and do the diagnostics to see what exactly happened.

---

### Post by kekstastisch on 2018-02-03
Ok guys, i have great news!
after finding out that i can enter a boot selector by pressing escape ( not F12 or F2 or Del, wth are manufacturers thinking) i can boot into windows and the life usb and here is the boot repair pastebin [http://paste.ubuntu.com/26511314/](http://paste.ubuntu.com/26511314/) as you told me i selected the create boot info summary option

i tried to get into the installed ubuntu but its stuck at that purple background and there are no loading dots or a ubunto logo
just the empty background


i think i need to define my goal new.
someone edited the title from "Please help me" to "please help me install ubuntu"

ubuntu on that 32gig stick is not a factor anymore, ill format it after this is all done
the goal is to get that messed up ubuntu bootloader off my system so when i hit the powerbutton it takes me straight to windows like it should

this experience is pretty stressfull so i wont ever try ubuntu again on my main pc but i got an old amd tower from early win7 days that is open for experimentation like this.

i dont know if this is important to say but my primary partition is on an m.2 ssd so i cant just plug it in to another computer to mess with it

---

### Post by oldfred on 2018-02-03
You have UEFI system.
And at some point you had Ubuntu installed in UEFI boot mode as you show left over Ubuntu/grub boot files in ESP - efi system partition.
But with nVidia you need nomodeset boot parameter to boot until you install the nVidia proprietary driver from Ubuntu repository.
You also are showing Windows fast start up on which is hibernation. And Ubuntu NTFS driver will not use hibernated NTFS partition(s) to prevent damage. But then you cannot see them to install.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

From link in my signature below. Do not skip any steps. If a step in not understood, there a further links to more info & instructions. Lots of info, but you can follow it.  
Summary UEFI install instructions
Back up Windows, your data, and make a Windows repair/recovery flash drive.
Download and create Ubuntu 64 bit  installer, flash drive or DVD.
Only use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
Turn off Windows fast startup in Windows.
In UEFI turn off fast boot (different than fast start up) and often  better but not required to turn off Secure boot (may be called "other"  vs. "Windows"), some may need CSM mode on (Dell), but still select UEFI
Some UEFI may need you to turn on or allow USB/DVD boot, especially if Secure boot is on.
Boot Ubuntu installing in UEFI live mode, and verify your system works ok.
Install Ubuntu.
Create backup procedure for your data and configuration files.
If Issue with install, more info needed, or terms not understood, see info & links below:

Since you have nVidia:
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

