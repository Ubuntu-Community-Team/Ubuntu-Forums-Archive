---
title: "Windows not installing (setup fails) after setting up Ubuntu"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by lifeperfecti0n on 2010-01-05
Hi everyone,

I recent faced a problem with my Windows 7 installation which made my computer really slow after startup (it took 1 minute to just load up 'My Computer' or other folders in explorer). Guessing that this was because of a virus, and not having the Windows 7 setup disk on me during my vacation, I decided to setup Ubuntu on my tablet PC. It has been successfully setup, but after arriving home I have realized I cannot install Windows at all. 

I need the OS for some applications which don't run on Linux so it is necessary for me to set it up. After Windows setup loads all the files from the boot able CD, it shows a blue screen at the step that says 'Setup is starting Windows'. I am stuck now and cannot install Windows at all, the same error is occurring with XP, Vista, and 7, so it is probably a hardware issue.

I have performed memory tests and a hard drive self test using the laptop's provided utility in BIOS, but all tests are successful. Are there any suggestions on what I should do next? I know this is more of a Windows issue, but if any one out there can think of something which might be causing this please let me know.

Thanks,

Kazim Naqvi

---

### Post by phillw on 2010-01-05
Hi,

is there an ntfs partition for win to install to ? If you just wiped the Win installation, your hard drive will be 100% linux filesystem, which Win cannot use.

Boot off the LiveCD and use Gparted to mount and slice your hard disk so that there is an area for Win (format it as ntfs ), whilst retaining you ubuntu area. Realistically, ubuntu needs about 10GB (including swap) for a standard installation, with not too many videos stored on it, you can give the remainder to Win.

Bear in mind that when you install Win, your ubuntu area will not appear as a boot option. This is quite normal, as the Win installation will over-write Grub, but not harm your ubuntu installation.

To get back to dual boot after putting Win back on, you need to pop over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Regards,

Phill.

---

### Post by lifeperfecti0n on 2010-01-06
Thanks for the suggestion, yes I do have two ntfs partitions.
The good news is that I was able to setup Windows Vista (its setup for some reason gave no problems). The sad part is that this is probably the worst release of Windows yet, so I am not sure I will be keeping it.
Meanwhile, Ubuntu is working perfectly for me - so I might not be going back to Windows at all!:)

---

