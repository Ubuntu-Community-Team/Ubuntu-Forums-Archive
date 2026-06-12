---
title: "Ubuntu 14.04/Windows 8 UEFI dual boot - No Windows option in GRUB"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by peter128 on 2014-08-08
I have installed Ubuntu 14.04 (64bit) in a dual boot setup with Windows 8. My system has two 750GB hard drives and the Ubuntu installation is on 150GB of the second drive which I think may be the cause of my problem. During installation I was prompted to create an EFI partition for Ubuntu as the installer could not locate the Windows 8 EFI partition. I created the EFI partition and the usual Ubuntu partitions and now whenever I start my laptop it boots almost straight into Ubuntu (Ironic as most posted issues are about booting straight into Windows). on booting I get presented with what I assume is the GRUB bootloader but it doesn't fully load, I only get a small purple boarder around my screen for ~30 seconds and then Ubuntu loads, I can bypass this by pressing ESC to enter the GRUB bootloader but then I am only presented with three options: Boot into Ubuntu, See advanced options for Ubuntu, and lastly; to see start up options. This last option is what allows me to reboot reboot my laptop, access UEFI setting and then boot into Windows 8. In addition to this, almost half the time my touchpad is inoperable and Ubuntu cannot see any wi-fi connections, the wi-fi issue is why I can't try to fix this issue from within Ubuntu itself and why I have to keep keep rebooting in Windows. (I only have wifi no ethernet, odd I know).

I have a feeling this is because I have two EFI partitions (one on each hard drive) which is a result of the installer not being able to detect the Windows EFI partition and the advice of several tutorials/articles on the web that said there should be one EFI partion on each hard drive (Unless I misunderstood).

Any help with this would be greatly appreciated as I need this laptop for university.

---

### Post by oldfred on 2014-08-08
It is best for Ubuntu to have its own efi partition on a second drive when you have two drives.
But it is strange that the installer did not see  the efi partition on the Windows drive.

There were some old issues of a strange locked efi partition which with FAT32 cannot happen. The fix was to backup the entire efi partition, delete partition and use gparted to create a new FAT32 partition and add boot flag to make it the efi partition. Then restore backed up files.

Often issue of only booting Ubuntu is where Ubuntu is installed in BIOS Mode and Windows is in UEFI mode. Since UEFI & BIOS are not compatible you then can only dual boot from UEFI/BIOS menu and may have to turn on/off UEFI or BIOS settings. Some auto switch and you can use the one time boot key, often f12 or f10 but varies by vendor.

Best to see details (but oldfred will not be back till late Sunday or Monday)

If installs are UEFI be sure to only boot in UEFI mode.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

With two drives do not run auto fix. Boot-Repair likes to auto install grub to every MBR if in BIOS mode. Not sure if it does the same with UEFI. But best to always use Advanced options if multiple installs on multiplie drives.

---

### Post by peter128 on 2014-08-08
Thanks for the quick reply.

Which EFI partition should be backed up and then restored? The Ubuntu one or the Windows one? I don't have the option to turn off secure boot and both are installed in UEFI mode to the best of my knowledge.

I'll have to look into the Boot Repair in a couple of days due to a limited internet data allowance at the moment. I will still look into the EUFI/BIOS issue though just to make sure.

Thanks again for the advice.

---

### Post by oldfred on 2014-08-10
If you have separate efi partition on each drive then it is not an issue. But UEFI should see both efi partitions and offer to boot installs from either.

But you cannot have two efi partitions on one drive.

Boot-Repair is text based and you can easily install to your current live installer. So it does not use a lot of Internet resources.

---

### Post by peter128 on 2014-08-10
OK, I'm about to install Boot-Repair from inside Ubuntu. Are there any special steps that must be taken or should I just do the default boot repair option?

---

### Post by oldfred on 2014-08-10
Link has the steps to install Boot-Repair into Ubuntu.
It has not been updated for 14.04 so you do have to run the rename, so it really is downloading the last version.

Do not run the auto repair until someone has reviewed report. Usually auto-repair works, but sometimes we can suggest specific fixes.

---

### Post by peter128 on 2014-08-10
OK, here is the URL: [http://paste.ubuntu.com/8013479/](http://paste.ubuntu.com/8013479/) I hope this helps.

---

### Post by peter128 on 2014-08-10
I had a look at the info in your link but I couldn't quite understand what I had to do. Should I look at one of the links for a dual disk system that was available in the link in your sig?

I also have a consistent problem where the backlight on the keyboard of my laptop keeps flashing every 30 seconds or so. I have an Alienware M17x, is there any way that I can fix this from Ubuntu or so I have to turn the lights off in Windows every time I want to use Ubuntu?

I have also just noticed that whenever I boot into Windows after having booted into Ubuntu that the clock is set to approximately 4 in the morning. I have a feeling that this is related to the boot issues that I am having but I just wanted to make sure.

---

### Post by peter128 on 2014-08-11
Success!! I managed to get Windows 8 to show up in GRUB by following the instructions in the 14th post of: [http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836) Thank you oldfred for your help!

This has fixed my Keyboard issue as well however I now can't use my keyboard or mouse once I have signed into Ubuntu. The mouse cursor moves around the screen but whenever I click or try to summon the terminal with ctr + alt+ t nothing happens. I think that this is related to xfce.

I installed it and then rebooted so the option would show up. I went into an xfce session, decided that I didn't like it and then logged out. I then tried to log back into unity but then once I was in the keyboard and mouse stopped working. I hade to quit using the power button on my laptop and then I could get into the unity and eveything was working fine. I then managed to get Windows 8 to show up in GRUB and now I can't use my mouse or keyboard anymore. Is there a way that I can remove xfce from my system?


I managed to get into Unity and uninstall xfce. So now the problem should hopefully be solved. However my system clock is still screwed up in Ubuntu and is off by approximately 2 hours. I will try to sort this out as soon as possible. Thanks again for the help oldfred.

---

### Post by oldfred on 2014-08-11
Glad you got it working.

I have seen several threads on clock and keyboard issues, but how did you solve yours? So others will know.

---

### Post by peter128 on 2014-08-13
I'm still having issues with the clock and keyboard for some reason. I think that my system clock may have somehow become set to the wrong time and my keyboard lights only work properly half the time. My mouse and keyboard only work after 5 - 10 seconds after having logged in, I have no clue why this is. Ubuntu on Oracle VM boots and works a lot better than my actual install. And now after the latest update to 3.13.33(I think that's it anyway) my computer freezes after 5 - 10 minutes and requires me to use the power button to restart the computer.

Are there any instructions on how to safely remove Ubuntu from my system? Will I have to repair my Windows EFI or anything like that? I am considering removing Ubuntu because I'm having so many issues. I would prefer not to have to remove it but I feel like I might end up having no choice.

On a side note, should I change this thread to unsolved again?

---

### Post by oldfred on 2014-08-13
With UEFI you have to remove the ubuntu folder in the efi partition. Use efibootmgr from live installer to remove entry in UEFI after removing entry in efi folder or else UEFI will re-add it. Then you can repartition.

       # from liveDVD or flash and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

You may need some UEFI settings or kernel boot options in grub menu.
Is UEFI most current version from Vendor?
This says some applies to all Intel systems:

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)


 Enabling USB Legacy Support - If keyboard does not work. 
[http://support.creative.com/kb/ShowArticle.aspx?sid=5754](http://support.creative.com/kb/ShowArticle.aspx?sid=5754)

 update-initramfs with keyboard drivers.
[http://ubuntuforums.org/showthread.php?t=2201983](http://ubuntuforums.org/showthread.php?t=2201983)


 [http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows](http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows)
Clock and some boot settings like fsck, login,   tmp retain time.
/etc/default/rcS
# Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no

---

### Post by peter128 on 2014-08-13
Thanks for the prompt reply, I will look into it as soon as I have the time. Is there a way that I can revert back to the previous kernel version? I.e. From 3.13.33 back to 3.13.30 or whatever it was before? I applied the update through the update manager after it stated that there was an update available and after I did that I started having this freezing issue. Would reverting to the previous version prevent me from getting any security fixes, etc?

---

### Post by oldfred on 2014-08-13
As long as it is that recent it should be in your grub menu, unless you already housecleaned. What does the advanced options sub menu show?

---

### Post by peter128 on 2014-08-15
I am able to get to it through the advanced options sub menu. Is there anyway that I can go about trying to stop the freezing on the latest version so I can use that instead? Or should I just uninstall the latest update? And if so, how do I go about doing that?

---

### Post by oldfred on 2014-08-15
How or where is it freezing? 
And that type of issue can be many things, UEFI settings, grub boot options, video or other drivers, system overheating and unknown issues.

---

### Post by peter128 on 2014-08-17
It just randomly freezes after 5 - 10 minutes. It can be when I'm browsing the internet or when I'm copying files from one place to another or just while I'm on the desktop. As far as I can tell, there is no pattern to it.

It only started happening once I updated/upgraded to 3.13.0-33-generic(I think that's what it is called). I know that 32-generic is fine and I can use that without any problems at all, even now.

---

### Post by oldfred on 2014-08-17
Part of reason we like to keep an older kernel when housecleaning kernels.

Sometimes regressions do occur and then are fixed in later kernels.
More advanced users install ppa (pre-compiled but test) with newer or even compile not yet released beta kernels to test if issue is still there.

---

### Post by peter128 on 2014-09-01
I found out what the issue is but I have no clue how to solve it. The system freezes if I don't have my USB mouse pugged in. I'm not sure how to fix it but I have found several threads saying that it's an issue with a config file of some sort. I can deal with it for now but it is a real inconvenience. 

On a side note, should I start a new thread for this problem or can I just leave it here?

---

