---
title: "Dual Boot Installation with Windows 10 - MSI GS70 2QE"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by swatto2 on 2015-09-05
Good Morning,

I am attempting to install Ubuntu 15.04 from a USB drive, it boots in UEFI mode (I get the GRUB menu) and I get to the setup screen but it cannot detect my Windows 10 installation. My machine is: MSI GS70 2QE 

I have tried the following:

Disabled secure boot
Switched from UEFI to Legacy boot
Turned off fast boot

I have two SSD drives in the laptop that are raided for performance reasons that contain my Windows 10 installation (maybe this is the issue?)

Thanks for any help you can provide

---

### Post by swatto2 on 2015-09-05
I have managed to install Ubuntu by manually specifying partitions but I do not get a grub menu and now boot directly into Ubuntu (I can boot into windows by changing my BBS boot priority in the BIOS to Windows boot manager).

Is there a way I can get a dual boot menu please?

---

### Post by oldfred on 2015-09-05
It used to be the only way to install Ubuntu to a desktop was with the text based alternative installer or use server version. But last version with alternative installer was 12.04. When they discontinued Alternative installer they said they would add LVM & RAID installs to gui desktop verions. LVM has been added, and now installer seems to see RAID partitions. But grub does not usually install correctly.

Did you install UBuntu in UEFI boot mode. Grub only boots systems installed in same boot mode, either both UEFI or both BIOS.
If in same boot mode.
sudo update-grub

If not post this to see details, do not run any auto fix until someone has reviewed report:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by swatto2 on 2015-09-05
Thanks for the response - I tried the above and although I see the Grub menu I do not see any entries relating to Windows 10.  Here is my bootinfo summary:

[http://paste.ubuntu.com/12285744/](http://paste.ubuntu.com/12285744/)

---

### Post by Mark Phelps on 2015-09-05
Win10, like it's predecessor Win8, runs with FastStartup enabled by default.  That forces Win10 to go into hibernation when you shut it down, leaving all open partitions STILL mounted and, thus, preventing Linux from mounting or reading those same partititons.

You need to do the following to gain access to Win10:
1) Boot into Win10
2) Go to Control Panel --> Power Options. Select Change what the buttons will do.  Near the top of the window, there is an entry for showing other options, select that.  Scroll down to the bottom of the windows, there is a check box labeled Fast Startup.  Uncheck it.
3) Reboot Win10

NOW, Fast Startup is disabled and Linux should see the Win10 partitions.

---

### Post by oldfred on 2015-09-05
I always add this entry, as I like to add my own entries:
 GRUB_DISABLE_OS_PROBER="true"
But that turns off the os-prober which adds the Windows entry into grub menu.
You can add your own entry, but it often is easier for new users to just let grub add it.

/etc/default/grub
You can change to "false" and re-run
sudo update-grub

---

### Post by swatto2 on 2015-09-05
> **Mark Phelps said:**
> Win10, like it's predecessor Win8, runs with FastStartup enabled by default.  That forces Win10 to go into hibernation when you shut it down, leaving all open partitions STILL mounted and, thus, preventing Linux from mounting or reading those same partititons.

You need to do the following to gain access to Win10:
1) Boot into Win10
2) Go to Control Panel --> Power Options. Select Change what the buttons will do.  Near the top of the window, there is an entry for showing other options, select that.  Scroll down to the bottom of the windows, there is a check box labeled Fast Startup.  Uncheck it.
3) Reboot Win10

NOW, Fast Startup is disabled and Linux should see the Win10 partitions.

Thanks for the response - I have tried that but the GRUB menu still does not see my Windows partition - the only way I can boot into Windows is by changing my BSS HDD Priority in the BIOS to 'Windows Boot Manager' instead of 'ubuntu'.  Is there a way based on the info file I have given to manually add the entry for my Windows installation? (I am using Grub Customizer).

Thanks for any further help you can provide.

---

### Post by oldfred on 2015-09-05
Did you use Customizer to change /etc/default/grub.
You would not normally turn off os-prober with an entry like that unless you did it somehow?

Turn prober back on and the grub update should work.

---

### Post by swatto2 on 2015-09-05
Hi oldfred,

Thanks - I tried that but it did not work, in the end I ran the boot-repair from a live environment and it fixed the issue - I can now see Windows in the entry listing and successfully boot to it.

Thanks for all the help you both have given me.

---

