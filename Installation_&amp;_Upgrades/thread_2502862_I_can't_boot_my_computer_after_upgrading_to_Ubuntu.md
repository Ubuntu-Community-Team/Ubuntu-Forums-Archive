---
title: "I can't boot my computer after upgrading to Ubuntu 24.04."
date: 2024-12-02
forum: Installation &amp; Upgrades
---

### Post by yurad on 2024-12-02
When I upgraded Ubuntu 22.04 to 24.04 two days ago, something went wrong. After rebooting, I got to BIOS, which has no boot options. Maybe GRUB is corrupted.  I attached the image. What should I do?

---

### Post by yancek on 2024-12-03
Did you get any warning/error messages during the upgrade and if so, you need to post them.
How did you do the upgrade?  People commonly use the term 'upgrade' when they reinstall from a DVD/USB so did you do a release upgrade from a terminal, did you use the software updater or did you do a reinstall of the newer version to the same partitions from a USB?

The image you posted is of the BIOS firmware for whatever type computer you have and Grub has not entered the picture at this point.  Was your Ubuntu an EFI install origianlly?  Is it the only OS on the system?  If you start the computer with the power button, what exactly happens?  Does it give you any option to boot or do you just go to the BIOS?  That would seem unlikely.

---

### Post by yurad on 2024-12-03
I have Asus X556UQ with preinstalled Windows 10. I installed Ubuntu. So, I have double boot: Ubuntu - the primary OS (from 2017)  and Windows 10 for specific tasks. On Saturday I started the 24.04 update from Software Updater. After a while I got the usual popup for a non-responsive window with Wait or "force quit" buttons. This time the message was something like: Noble is not responding. (I didn't even understand what Noble was)
Then the upgrade window closed. Maybe I accidentally pressed force quit. Or the process died.
I started researching what to do. Soon Software Updater popped up with a bunch of updates. I assumed it was a continuation of the upgrade and accepted all the updates. At the end of the updates, Updater asked to reboot. After rebooting I got the BIOS WITHOUT ANY BOOT OPTION. After turning the laptop off and on I get the same BIOS WITHOUT ANY BOOT OPTION.
(this evening I plan to create a bootable USB with 24.04 to check the hard drive)

---

### Post by yurad on 2024-12-03
I couldn't boot from USB or CD. Probably a problem with the motherboard. It's strange that this happened right after I tried to update Ubuntu. It's hard to believe that this is a coincidence. But anything is possible.

---

### Post by oldfred on 2024-12-03
If your Ubuntu is from 2017, it probably is obsolete and upgrade then does not work.
What version is it?
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If you have live installer of 24.04 LTS, you can install to existing / without formatting. And if separate /home you install but never format an existing /home partition.  You still need good backups as any system files will be overwritten with defaults. And always best to have good backup of your data, in cast of user error or hardware failure.

Benefits of a release-upgrade (over clean install) by guiverc, but I prefer clean install & restore from backup
[https://ubuntuforums.org/showthread.php?t=2501145](https://ubuntuforums.org/showthread.php?t=2501145)
Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)
[https://ubuntuforums.org/showthread.php?t=2496620](https://ubuntuforums.org/showthread.php?t=2496620)
[https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)

---

### Post by grahammechanical on 2024-12-04
> This time the message was something like: Noble is not responding. (I didn't even understand what Noble was)

We get new versions of Ubuntu every six months. Each version has a code name. The code name for Ubuntu 24.04 is Noble Numbat. The code name for Ubuntu 24.10 is Oracular Oriole. The developers work through the alphabet. Ubuntu is now going through the alphabet for the second time. You mention having Ubuntu as the primary OS since 2017. That would have been Ubuntu 17.04 (Zesty Zapus) or Ubuntu 17.10 (Artful Aardvark).

Regards

---

### Post by yurad on 2024-12-04
@oldfred ,  @grahammechanical

 I am really very very confused with this!
 I have mentioned in the very first post. I upgraded Ubuntu 22.04 to 24.04. (2017 is the year when I started using Ubuntu on this laptop) So it was a correct upgrade.

But right after the upgrade I am unable to boot in any way. Not from my hard-drive, not from any flash drive, not from CD (I have old bootable CDs)

Something happened with the motherboard? Why right after the upgrade?

---

### Post by tea for one on 2024-12-04
Within your UEFI (BIOS) settings, do you have an option to reset to default?

---

### Post by oldfred on 2024-12-04
Did not see you upgraded from 22.04.

May be best to see details of configuration.
Best to use 24.04.1 live installer to run Boot-Repair.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by yurad on 2024-12-04
> **tea for one said:**
> Within your UEFI (BIOS) settings, do you have an option to reset to default?

Yes, I found reset to default. It didn't change anything

---

### Post by yancek on 2024-12-04
It is extremely unlikely that an update of your Ubuntu or any OS for that matter is going to destroy the option in your BIOS firmware.  When you access your BIOS and go to the screen show in your first post and arrow down to add new option or Delete option and highlight either and hit the Enter key, do you see any options, particularly under the Delete option.  Did you see a boot entry previously for Ubuntu in your UEFI settings in the BIOS?

---

### Post by yurad on 2024-12-04
> **oldfred said:**
> Did not see you upgraded from 22.04.

May be best to see details of configuration.
Best to use 24.04.1 live installer to run Boot-Repair.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Unfortunately, I'm completely stuck. I cannot boot my laptop. I inserted my old bootable flashes and they don't appear in the boot menu. I tried my old bootable CD with Ubuntu and Knoppix. They don't. boot. either. When I am trying to manually create new boot options I can see the content of the flash disk. (I attached a few pictures.) I am able to select some efi files and create boot options. This way, I created a boot option for each efi file I found. But, after I restart the laptop I don't see all these boot options anymore. Also sometimes after trying to exit the BIOS I'm still stuck in the BIOS, I'm just moved to the first tab. 
There might be something wrong with the BIOS hardware. I'm not an expert on this. It's just extremely strange that this happened right after an Ubuntu update. It's hard to believe that Ubuntu messed up my BIOS. But it's also hard to believe that it's just a coincidence. It happened on a Saturday. Before that update, I booted into Windows and updated it in case Ubuntu broke after the update. Then I booted back into Ubuntu and did that botched update. Then my laptop lost its existing boot options and won't let me boot from USB sticks. It's all weird. A sophisticated BIOS malware? I never heard they exist.

---

### Post by oldfred on 2024-12-04
Windows update and with some models Ubuntu/fwupdate can update UEFI firmware. 
That resets many UEFI settings to defaults. If you had to change settings, you probably have to redo them.

Some even have added extra security to prevent USB boot as then that would not be secure.
User then has to specifically allow USB boot or full USB support.

---

### Post by tea for one on 2024-12-05
> **yurad said:**
> It's hard to believe that Ubuntu messed up my BIOS. But it's also hard to believe that it's just a coincidence.
Well, yes, both circumstances are hard to believe but there may be an answer from the Asus website........?
> Update BIOS in BIO/replacing Utility (with EZ Flash)
Since some models are not able to update BIOS in Windows, this article will introduce how to update BIOS in BIOS Utility.
Have you considered updating or replacing your firmware?
It looks like Asus have a way to do this?
[https://www.asus.com/uk/support/faq/1008859/](https://www.asus.com/uk/support/faq/1008859/)

---

### Post by yurad on 2024-12-06
this is a duplicated post. The real post is below

---

### Post by yurad on 2024-12-06
Big relief! I finally booted from one of my old USB sticks with Ubuntu 17.04. It's a bit old, but still pretty good for copying everything from my home directory and Windows partition. I still think my BIOS is broken. I've never had trouble booting from USB sticks before. Today I had to manually create a boot option. I think I did it exactly the same way as yesterday. But this time I was able to boot.
Thanks for all the help!
I'll take a short break to check the BIOS status.  I'll also consider updating the BIOS. 
I'd appreciate any advice on how to check the BIOS.
(Once I've sorted out the BIOS issues, I'll try to repair the boot with GRUBE.)

---

### Post by oldfred on 2024-12-06
UEFI/BIOS and SSD:
Compare to vendors support site
sudo dmidecode -s bios-version
udisksctl status
inxi -d

Vendors vary greatly on how to update UEFI/BIOS. If older system, you may still have a newer but not recent update available.
Windows often updates UEFI.
Some brands and newer systems can update UEFI from Ubuntu/grub with fwupdate.
[https://fwupd.org/](https://fwupd.org/)
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Some UEFI can even update directly from UEFI. Some need you to download the update file & from within UEFI read that. Must be saved to FAT32 formatted partition as that is all that UEFI reads.
Older BIOS may need BIOS bootable with FreeDOS or similar to run .exe file that has update file inside it. Usually instructions & files on vendors support site.

---

### Post by yurad on 2024-12-11
I restored the boot settings. The problem was that after the failed upgrade to 24.04 (I mentioned it in the second post) my UEFI BIOS went into an invalid mode. The BIOS lost the boot options and could not restore them. I could not boot from USB drives. Sometimes I did boot from flash, but right after a successful boot I could not repeat itagain.
So my conclusion is that during the faulty upgrade (I'll add more information about this below) one of the processes interacted with my legacy UEFI BIOS and left it in this broken mode. Otherwise I can't explain what happened.

I don't know what exactly fixed the BIOS. I kept turning off and on different settings. I tried to create and save new boot options. Sometimes I was able to boot from a flash drive. But it was unreliable. I tried RESET commands in the BIOS, but it didn't work either. I thought my BIOS had hardware issues, and was going to reinstall the firmware as a last trial. But suddenly, after one my iterations, the laptop booted Windows. I immediately checked the BIOS. All boot options were back. I could boot into GRUB and Windows. (I have two efi files on my hard drive, Windows and GRUB. From GRUB I can also boot Windows). Now I can boot from any of my bootable flash drives, just like before.
What will I do if this happens again? Without fiddling with the BIOS settings, I will try resetting the BIOS on the motherboard or reinstalling the firmware. I also saved screenshots of my BIOS settings.

(Just in case, I'll add some details about my faulty upgrade. Before the start I closed all programs except the terminal with "top" open and started the upgrade. Pretty soon I got a popup saying Noble is not responding. Please wait or force quit. The type of popup I got very often on 22.04. I didn't understand what Noble was and opened Firefox to find information. However, the Upgrader window was gone. Maybe I accidentally pressed force quit. I checked in "top" that the updater was missing and opened the GUI updater again. It gave me a big list of updates. I naively thought that the 24.04 upgrade would continue. The updates took a long time. After the updates, I rebooted and encountered this BIOS problem. When I was able to boot Ubuntu again, I found no changes in the interface compared to 22.04, although Ubuntu said its version was 24.04. The upgrade went wrong. I don't like the reliability of the Ubuntu GUI updater anymore. To fix the upgrade, I used "apt dist-upgrade" in the terminal)

---

