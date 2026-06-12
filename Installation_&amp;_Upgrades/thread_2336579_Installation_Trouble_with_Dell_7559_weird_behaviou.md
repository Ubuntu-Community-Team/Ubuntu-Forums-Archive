---
title: "Installation Trouble with Dell 7559: weird behaviour?"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by blue_fox on 2016-09-09
Hi all!

I would like to have some help. I’ve a Dell 7559, the i7 6700HQ CPU model with a 500GB Samsung EVO M.2 SSD and a Nvidia GTX 960m GPU. I would like to have a dual boot system with Ubuntu 16.04 and Windows 10.
Windows 10 was ‘transferred’ to the SSD with the Samsung Data Migration tool, which worked fine (but it didn’t copy the Windows recovery partition). I’ve already made a recovery ISO image with the Windows utility (from the original HDD), so if anything goes wrong it won’t be the end of the world.

[Edit: I haven't yet installed Ubuntu, but I'm trying to let it boot from a USB drive properly first.]
But now the weird thing is: sometimes (around one in 20 times) Ubuntu just boots … but in most cases it stops booting.
I've made two videos, one of a failed boot and one of a successful boot:
failed: [https://www.youtube.com/watch?v=0etv-i0Euk8](https://www.youtube.com/watch?v=0etv-i0Euk8).
successful: [https://www.youtube.com/watch?v=YogZc_f70Vc](https://www.youtube.com/watch?v=YogZc_f70Vc).
You can set the video speed to 0.25 if necessary.

The USB drive was prepared with the Rufus USB installer.
**I didn’t disable ‘secure boot’** and as it seems to be difficult to re-enable it I wouldn’t like to turn it off.

[Update: Here's the output from BootInfo: [http://paste2.org/6O4DgxMU](http://paste2.org/6O4DgxMU)]

Could someone explain this weird behaviour, and if possible, give a solution in order to solve it? I suppose it won't be gone after installing Ubuntu?

Also, regarding the install and the UEFI stuff, I like to set the partitions by myself but are there any other settings (grub, ...) I should take care of?

---

### Post by oldfred on 2016-09-09
Videos are private, but I usually do not watch videos anyway.

Secure boot should just be a setting on or off (often Windows or "other"). But fast boot in UEFI can make it more difficult to get back into UEFI. 

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Have you installed nVidia drivers from repository?

---

### Post by blue_fox on 2016-09-09
*Videos are private, but I usually do not watch videos anyway.*

Video issue should be fixed now! I added the videos because I think they show the problem best (with all the info and text shown during start-up).

[I]Secure boot should just be a setting on or off (often Windows or "other"). But fast boot in UEFI can make it more difficult to get back into UEFI. 
[/I]
My Dell 7559 doesn't seem to have fast boot options.

       [I]May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

[/I]I've added a link to the bootinfo file in the original post.

[I]Have you installed nVidia drivers from repository?
[/I]
I should have been clearer in my first post (did an edit now), but I haven't yet installed Ubuntu on this PC. I'm only trying to boot it from a USB drive. So I haven't yet installed any drivers.
I suppose that if I can't get Ubuntu booting reliably from the USB drive, it also won't be reliable after installation?

---

### Post by oldfred on 2016-09-09
You already have a swap partition? But no Linux partition(s).

Usually with nVidia, a boot parameter is required - nomodeset.
Some older nVidia may work with just the open source driver. My 620GT works well with just open source driver.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

Only use Windows to shrink your Windows NTFS data partition to make space for Ubuntu. I prefer to manually partition in advance, otherwise auto installs set sizes at what I consider less than optimal, if there is such a thing.

See link below and quick steps for install and then lots of details if desired.

My Dell SFF wanted a Dell backup and a Windows backup. Then I made a full image backup. And all that was Windows 8 and then I updated to Windows 10 and all those backups are not worth much. Only did one backup of Windows 10. Only using Windows as Comcast lets that watch DVR recordings, Linux does not work due to DRM.

---

### Post by blue_fox on 2016-09-10
Thanks for the *nomodeset* tip, oldfred.

Two commands seem to make my 7559 boot reliably: replace <*quiet splash*> with <*nomodeset*> OR add behind <*splash*> <  *acpi_osi=*>.
In both cases the screen brightness setting didn't work anymore. With *nomodeset* the screen resolution was limited to 800x600 (hèhè, I could just as well reboot my 486!).

As Ubuntu wasn't yet installed I didn't install any drivers or updates, so hopefully this issue will go away after installation, updates and editing the graphics settings.

<acpi_osi="Linux"> didn't seem to work.

I'm going to try to install Ubuntu now...

---

### Post by blue_fox on 2016-09-10
So... Ubuntu's up and running! (And Windows 10 is also still working).

After install compiz didn't work. I enabled the nvidia drivers and Intel microcode drivers, updated and upgraded all the stuff and now it's working properly.
Screen brightness works now.

---

