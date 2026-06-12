---
title: "instalation problem"
date: 2023-10-31
forum: Installation &amp; Upgrades
---

### Post by garik542984 on 2023-10-31
Hello,
I have such a problem:


I'm trying to install Ubuntu on my laptop.
I created an image of Ubuntu 22.04.3 LTS,
but after starting it, I get an error like the one in the picture in attachment.
[IMG]https://drive.google.com/file/d/13uOKZHTk_CxRHWcJyTKbmBX5ZZ_GSMhI/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/13uOKZHTk_CxRHWcJyTKbmBX5ZZ_GSMhI/view?usp=sharing[/IMG]

[IMG]https://drive.google.com/file/d/13uOKZHTk_CxRHWcJyTKbmBX5ZZ_GSMhI/view?usp=sharing[/IMG]

I checked if the installation might be bad, but I installed the system on a PC without any problems.


Later, I tried with Ubuntu 23.10, and after selecting the installation location, I received a "installation failed" message after about 2 minutes.
However, when I try to install it on a PC, it also goes smoothly.


I'll add that I want to install it on a partition where Windows is already installed, or on an additional disk, but the installer doesn't see any partitions on it and wants to format it (it's 50% full).
I really need both systems.


My laptop is a Lenovo Legion 5 PF41B6MH.


What steps should I take?

---

### Post by yancek on 2023-10-31
>  I'll add that I want to install it on a partition where Windows is already installed, 

You can't do that, it won't work.

> or on an additional disk 

That will work, best to just leave unallocated space to select for the install.  No point in creating a partition from windows as you need to format the partition with a Linux filesystem and windows default doesn't do that.

>  but the installer doesn't see any partitions on it and wants to format it (it's 50% full).
I really need both systems.

Is it 50% full with windows data and a windows filesystem?  If that is the case, you most likely left windows in the default state of hibernation and the partition filesystem won't be mounted, accessible or shown during the install.  Turn off hibernation in windows (countless sites online explaining this) and try again.  Have you turned off Secure Boot?  Might try that but should not be necessary.

I don't know what Device Guard is but if you are setting it up, have you set a BIOS password as suggested in the image you posted?

---

### Post by garik542984 on 2023-11-01
Thank you for respond

The installation wizard suggests and installs Ubuntu on the Windows disk. 

When it comes to manual installation, the wizard sees the second disk but does not see any additional partitions or the allocated free space, as shown in the pictures.
 However, it can see everything perfectly when it's allocated on the first disk (with windows). Could this be related to the UEFI disk setting?


Although I clicked through the UEFI settings, I couldn't find any additional options for disk settings.



> [COLOR=#000000]Have you turned off Secure Boot?[/COLOR]
yes, I turned it off

> [COLOR=#000000]you most likely left windows in the default state of hibernation[/COLOR]
nope, I checked it

---

### Post by tea for one on 2023-11-01
Your second disk nvme1n1 (picture 3) does not seem to have any free space.
Close the installer
In a live session, open Gparted
Select nvme1n1
Unmount the partitions (if mounted)
Create some free space (user choice)

---

### Post by MAFoElffen on 2023-11-03
In Windows, suspend bitlocker, turn off fastboot... Did you go to Windows disk management and make room for the install by shrinking a Windows partition? Set the next boot to Safe Mode from the Windows Recovery section...

In your UEFI BIOS, disable SecureBoot, disable Intel Rapid Storage technology, set Boot Mode to EFI, set SATA mode to AHCI...

Tell us if you found any of those options set and had to change them.

---

