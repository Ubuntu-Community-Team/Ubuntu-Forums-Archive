---
title: "trying to install on new computer"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by 2roombas on 2010-06-07
I recently bought a new desktop, an HP dual-core 64-bit with Win7.   It sure beats my old Dell Dimension 2350, but I obviously want to dual-boot with Ubuntu 10.04.  I'll, keep Win7 for my beloved Bookworm and Bejeweled  games. This install is not going as well as it did on my xp machines. Not sure why either.

First off, I download the 32-bit .iso because the 64-bit said it was not for daily use.  Was that the right thing to do? Yes, I checked the md5sum.

After loading, seeing the purple "keyboard=man" screen, hitting space, English, Try ubuntu without installing, I get a screen full of this below repeated over and over .....

[   0.176001]   [<c0>06b>] ? ftrace_define+_fields_sys_exit+0x3b/0x90

I have to hard shut down, exit. No ubuntu. :(  

What's going on?

---

### Post by Cavsfan on 2010-06-07
> **2roombas said:**
> I recently bought a new desktop, an HP dual-core 64-bit with Win7.   It sure beats my old Dell Dimension 2350, but I obviously want to dual-boot with Ubuntu 10.04.  I'll, keep Win7 for my beloved Bookworm and Bejeweled  games. This install is not going as well as it did on my xp machines. Not sure why either.

First off, I download the 32-bit .iso because the 64-bit said it was not for daily use.  Was that the right thing to do? Yes, I checked the md5sum.

After loading, seeing the purple "keyboard=man" screen, hitting space, English, Try ubuntu without installing, I get a screen full of this below repeated over and over .....

[   0.176001]   [<c0>06b>] ? ftrace_define+_fields_sys_exit+0x3b/0x90

I have to hard shut down, exit. No ubuntu. :(  

What's going on?


I would go with the 64 bit Ubuntu. I have windows 7 and 10.04 both 64 bit.
It works well!

---

### Post by 2roombas on 2010-06-07
> **Cavsfan said:**
> I would go with the 64 bit Ubuntu. I have windows 7 and 10.04 both 64 bit.
It works well!

Thanks! :)

---

### Post by oldfred on 2010-06-07
One of the main issue with Lucid is video cards. What card do you have? The nomodeset works with several of the others as an initial setting. I have been using the 64 bit since Karmic without any 64 bit issues. No one seems to know why they added that daily use comment?? 

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)


After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line


if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

### Post by 2roombas on 2010-06-07
Shoot, it still didn't work  after downloading the 64 bit .iso, so I did it the wubi.exe way and I was super happy to see it  install. However upon reboot, I still only see a screen of code freeze. I cannot type "all" of it, sorry. 

I tried the i915.modeset=1 and the i915.modeset=0 after quiet splash (are u supposed to space after splash??),because yes, I do have an Intel. It's a brand new computer though,just got it a couple days ago, so I cannot imagine it's old?! Those didn't work for me. :(

Any more ideas with an already installed copy that just wont boot?

edit:  I forgot to add that yes, I get the choice menu after turning the computer on. And yes, the win7 is fine, it boots fine into that. But after choosing ubuntu it will go straight to  grub. I ave tried..

1.  enter on generic
2.  enter safemode
3.  clicking e and doing the modeset thing
4.  delete quiet splash and replace with nomodeset

All of these go to a screen full of code... then a blinking curser at the bottom of the age.

---

### Post by oldfred on 2010-06-07
Someone with similar issues. His workaround was to install 9.10 and upgrade. What processor do you have?

[http://ubuntuforums.org/showthread.php?t=1488088](http://ubuntuforums.org/showthread.php?t=1488088)

---

### Post by 2roombas on 2010-06-07
> **oldfred said:**
> Someone with similar issues. His workaround was to install 9.10 and upgrade. What processor do you have?

[http://ubuntuforums.org/showthread.php?t=1488088](http://ubuntuforums.org/showthread.php?t=1488088)

It's Pentium Dual-Core CPU E5300 @ 2.60GHz, 64-bit 3.00 GB memory

If I try to load 9.10, then how can I get rid of the already installed 10.04 and not disturb the win7?

---

### Post by oldfred on 2010-06-07
Just use manual install and choose your existing root & it will find & use the existing swap. If you have anything in your system you need to back it up. If you have a separate /home you also select it as part of the manual install.

---

### Post by 2roombas on 2010-06-07
The wubi.exe ubuntu was easy to uninstsll. I just went to the wiki, it was just a normal uninstall of windows-type programs in thr add/remove.

Anyway, I then tried a fresh install of both 9.10 and 9.04. Both get up to the menu, but as soon as I click "Try without..." up pops a whole screen of code with a blinking curser at the bottom. Drats!:(

---

