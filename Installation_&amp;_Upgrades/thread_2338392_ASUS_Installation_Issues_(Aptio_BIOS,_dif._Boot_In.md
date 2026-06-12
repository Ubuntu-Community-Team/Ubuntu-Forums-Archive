---
title: "ASUS Installation Issues (Aptio BIOS, dif. Boot Installer Menu, and constant reboot)"
date: 2016-09-27
forum: Installation &amp; Upgrades
---

### Post by simplearc on 2016-09-27
Hey, I am new to Ubuntu, and I have been trying for the last two days to install it on my ASUS Laptop, and I have come upon endless issues, most of which I found the solutions to on these forums, but now I am stuck, and I am not sure if I am even on the right path.

1. So, I first created a partition of OS C Drive of 17.5 GB, which after hours of disc cleanup and file reorganizing was all the space I could give (due to unmovable system files needing the space).

2. Next I downloaded the ubuntu-16.04.1-desktop-amd64 iso from the ubuntu site (my computer has a 64-bit OS, in case that immediately concerned you, although I will get to my computer specs at the end).

3. Next I plugged in my empty, brand new 16GB Toshiba USB.

4. Then I downloaded and ran the Universal-USB-Installer-1.9.6.7 from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

5. When asked if I wanted to reformat to FAT32 I said yes, and this led to my first inconsistency with the installation guide I was following. I had the same issue as this guy:
     [http://askubuntu.com/questions/142728/how-to-fix-syslinux-error-creating-a-bootable-usb-stick-in-windows](http://askubuntu.com/questions/142728/how-to-fix-syslinux-error-creating-a-bootable-usb-stick-in-windows)
and so I did what they suggested in that thread and instead of getting the Universal USB Installer reformat the USB, I reformatted it myself to NTFS, and ran it again, this time I received no error messages and the installation seemed to go smoothly.

6. Sadly, when I rebooted my computer and held f2, the second inconsistency occurred, my computer, which came with windows 8 installed, uses a legacy BIOS by American Megatrends, Aptio Setup Utility. So my boot menu looked something like this:
 [IMG]http://eai72.free.fr/IMG/bios.jpg[/IMG](picture taken from google images, but is practically identical to mine) 
which basically meant that my boot-able USB was not appearing as a boot option. So I tried following fixes forum, but there weren't many, and they all seemed quite confused, and the not necessary the same as what was going on with mine. eg. [https://ubuntuforums.org/showthread.php?t=2052009](https://ubuntuforums.org/showthread.php?t=2052009)
As in the post I just linked I tried to add new boot option, but couldn't find help on what to do with the path. I proceeded to try and find any similar issues, but all my searches just led to different installation, or different UEFI to Legacy BIOS and vice versa issues.

7. And then I found this (which I recommend you don't watch as he takes a long time): [https://www.youtube.com/watch?v=X3GFZm9at6g](https://www.youtube.com/watch?v=X3GFZm9at6g)
What I did was disable Secure Boot Control in the Security tab of my BIOS, and then enable Launch CSM, which you can see in the Boot tab of aptio in the image above. After restarting, the boot option for my Toshiba USB was there. I moved it to 1 and rebooted.

8. Now I ran into the third inconsistency. Whereas the ubuntu boot installer in both the video above, and in the two guides I was following (one by NT Forever, and the other directed by the Odin Project), looked like this: 
[IMG]http://i.stack.imgur.com/j2HOK.png[/IMG]

Mine, looked like this:

[ATTACH=CONFIG]271378[/ATTACH]

or a closer picture from google images:

[IMG]http://www.davebennett.tv/wp-content/uploads/2016/02/install-ubuntu-1024x576.jpg[/IMG]

From here, although different then in the guides, still had the same options, so I selected Install, and pressed Enter. Then my computer rebooted, right back into the same menu, so I tried again, and again, and then every other option, all of which did not help in the slightest. After each reboot a quick message (far to quick to read even a letter of) would flash in the top left of the screen and then it would go to the same message. So I tried using TAB to 'edit a menu entry', which I didn't have the faintest clue how to do, and led to no resolution. So I turned to the forums and after searching until I was exhausted I decided to write this all out and sleep on it. So please, if I have gone wrong at a certain step please let me know, if I am close but am going the wrong way please redirect me, and if I am completely hopeless, please let me know.

Here are my computer specs:

My laptop is an ASUS ROG G46VW-DS71-CA (this is pretty much it: [https://www.amazon.ca/ASUS-G46VW-DS71-CA-14-1-Inch-Republic-Processor/dp/B00E36LFZQ](https://www.amazon.ca/ASUS-G46VW-DS71-CA-14-1-Inch-Republic-Processor/dp/B00E36LFZQ))
I run Windows 10 Home (64-bit) version 1607, OS Build: 14393.187, although the laptop was originally Windows 8.
Intel i7-3630QM (2.40GHz)
8GB RAM
C Drive with 196 of 261GB FREE
D (DATA) Drive with 389 of 397GB FREE

If there is anything else I should have posted please notify me. If there is already a solution I welcome a snide remark and a posting of the previous thread. Thanks for your help. I'll be back tomorrow.

---

### Post by Geoffrey_Arndt on 2016-09-27
Click on the "Try Ubuntu" and after it (hopefully) boots up into a "Live" version of Ubuntu, click on the dash icon (top left on launcher) and type in "gparted".    Run it and take a screen shot of your partitions so we can see what's what.   It's likely you are on a UEFI system, which requires at least to disable "fast boot" in Windows, and also, in step 2, how did you create the partition and what file system does it have?    That's part of what gparted should show us.   The installer has to "see" a valid place (partition of unallocated space, or a partition with a Linux file system like ext4) to proceed with the install.

---

### Post by simplearc on 2016-09-28
So as I stated in the OP it will not boot into any version of Ubuntu and instead just reboots to the same black background menu. I have disabled fast boot (to my knowledge). I created the partition by right clicking the windows key and selecting disc management. Then right clicking OS C:\ drive and selecting shrink volume, then shrinking by 17.5 GB.
[ATTACH=CONFIG]271382[/ATTACH]

Hope that helps. Cheers

---

### Post by simplearc on 2016-09-30
Still in need of help.

---

### Post by Geoffrey_Arndt on 2016-09-30
Just a quick note here . . . there are usually two places to turn off "fash boot/quick boot" . . . 1 in the uefi/bios, and the other in the Windows OS itself.   I think it's in the power settings.   As I haven't used Windows regularly in 6 years, I can't recall exactly, but I would suggest to look in power settings first.   Be sure also that secure boot is off (temporarily).

Also, since your system is relatively new, it uses UEFI by default versus standard BIOS unless you've changed that default so the system uses Legacy MBR booting/storage.   Ubuntu will load/install either way but it has to be booted up consistent with the mode the usb image has been setup.   So if the usbstick is setup via Legacy, you will choose the Legacy install, versus the UEFI install.

Here are a couple other threads for more info . . the last link especially has much good info to check out:
[URL="http://http://askubuntu.com/questions/820423/cannot-install-ubuntu-16-04-lts-on-asus-rog-laptop"]
http://askubuntu.com/questions/820423/cannot-install-ubuntu-16-04-lts-on-asus-rog-laptop[/URL]
[URL="http://http://askubuntu.com/questions/336506/linux-on-asus-rog-laptop"]
http://askubuntu.com/questions/336506/linux-on-asus-rog-laptop[/URL]

[https://rog.asus.com/forum/showthread.php?54342-Dual-booting-Windows-8-1-amp-Ubuntu-14-04-in-G751JT](https://rog.asus.com/forum/showthread.php?54342-Dual-booting-Windows-8-1-amp-Ubuntu-14-04-in-G751JT)

---

### Post by oldfred on 2016-09-30
Please attach screenshots or photos, not post in line. Not everyone has high speed Internet and it can slow their system. Easy to attach with Forum's advanced editor and paper clip icon.

You cannot use NTFS for the installer, it must be the FAT32, so it can boot in either UEFI or BIOS boot mode. UEFI only boots from FAT32 partitions.

Do not create partitions with Windows, it cannot create any partition usable for the actual Ubuntu install. It does not know about ext4 or swap. It can create a shared NTFS or d: drive in Windows as long as you do not let Windows convert to dynamic partitions.

That screens may look slightly different is related to newer version. But difference between BIOS & UEFI boot is a lot. With UEFI boot you get grub menu.
And in your system's UEFI, you should get two options to boot a flash drive, one UEFI:name and other must name where name is brand or partition label on flash drive. But you may have to turn on a setting that says allow USB boot in UEFI. Secure boot often does not allow USB boot as that is then not secure, so you have to specifically allow it. BIOS boot is not secure boot, anyway.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

More detail and lots of links in link in my signature.

Often issues are similar across many models from one brand. So some of these may be similar.

Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/) 
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by simplearc on 2016-10-04
Yeah I had originally turned off fast boot from both the BIOS and in the OS. I also had secure boot turned off while I was attempting it. Thanks

---

