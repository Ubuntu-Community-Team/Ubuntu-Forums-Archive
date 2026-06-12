---
title: "Dual-boot Ubuntu/Win8"
date: 2013-09-02
forum: Installation &amp; Upgrades
---

### Post by shadesofoctober on 2013-09-02
Hi, I am trying a simple dual-boot setup on my Lenovo Y500. Unfortunately, I am having a ton of issues, and bootloaders are not my strong suit. What's worse, the system is EFI, and I've never had luck with that.

Here's the deal.. I got my laptop with Windows 8 pre-installed. I decided to throw Ubuntu on there not long after, which wasn't too much of an issue. I shrunk the Win8 partition, added 2 partitions for Ubuntu and swap. The only problem was that I had to go into Lenovo's boot menu to select Ubuntu, because it booted straight into Win8 (More than likely since I just threw Grub into Ubuntu's partition)

Now the other day, I decided I wanted to boot straight into Grub, and choose either Windows or Ubuntu instead of having to go into the firmware menu each time.

I reinstalled Ubuntu and set the EFI partition as the target for Grub.. Lo and behold, it boots into Grub, but...
If I select Ubuntu.. a message appears "An error occurred while mounting boot/efi", and the output shows "unknown filesystem 'vfat'", so mount fails.
If I press 'S' to skip mounting, the login appears locked at 1024x768 (The max res is 1920x1080) and the mouse cursor does not respond (Using the mouse or touchpad). Completely useless.
If I select Windows, the usual failed to find 'drivemap', etc, message appears.

Using boot-repair from a live-boot fixes Windows booting from Grub. But Ubuntu still fails to boot.

I tried re-created the EFI partition, both fat16 and fat32. fat16- the screen simply stays purple. fat32- the same "An error occurred while mounting boot/efi" message..

Honestly, I have no idea how to tackle the issue.. Reinstalled Ubuntu several times. Even with Grub back inside Ubuntu's own partition, I can't boot into it anymore without the error occurred message. 
So, sorry about the long post.. but does anyone know how I can get Ubuntu back to booting properly again? I can provide any information. I just would prefer not to wipe my Windows 8 partition, but am comfortable modifying any other partition.


To top it off, the new SSO login gave me a new forum account, even though the preferred email was set to the same one my old forum account used :(

---

### Post by Chaivalla on 2013-09-02
Man, I have a Y500 pre-installed with Win8 too. I posted on this forum before. I haven't tried installing Ubuntu yet out of fear of messing up everything :(

---

### Post by shadesofoctober on 2013-09-02
It's a great computer for sure.. but at this rate, I'm about to try to cut my losses and completely remove Ubuntu.
Even my Macbook Pro, I got the triple-boot going with no issue. I don't understand why it suddenly can't mount a simple fat32 partition!
Also, if you haven't tried yet, Fedora 18 and 19 do not boot, period..

---

### Post by Jorge_Gonzalez on 2013-09-02
I went through exactly that, and to be honest I found no solution. I suggest completely removing Ubuntu and starting over, disable Secureboot, and try working from there. I ended up reinstalling Ubuntu, and deleting Windows 8. It's quite tricky to dual boot the two.

Or you could try install Windows 7, delete Windows 8, and install Ubuntu from Windows 7. I did this on my sister's laptop some time ago and it worked marvelously. (edit: every time you turn on the computer, it lets you choose between WIndows 7 and Ubuntu, whereas Windows 8 will never (in my experience) give you that option)

---

### Post by shadesofoctober on 2013-09-02
I am going to try to keep working with it, but am getting frustrated pretty quickly..
I tried the Gnome edition as well, but with same results, just in case my original Ubuntu image was corrupt or something.

I have had Secure Boot disabled, as well as Fast Startup for a long while now.

I'm considering re-installing Windows using a recovery USB, but I have a large number of files to save. Unfortunately, this is more-or-less my gaming laptop, so I pretty much need Windows on it. I'm not sure about Win7... Perhaps I can try that, hopefully the drivers will work in 7 as they do in 8.

This is the boot-repair output, if that helps at all.. [http://paste.ubuntu.com/6057434/](http://paste.ubuntu.com/6057434/)

---

### Post by oldfred on 2013-09-02
Other Lenovo.

 Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)

According to Microsoft its reserved partition must be before any data partitions. Better to have Linux last on drive.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

 Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 
    
If this is an UltraBook you have UEFI vs. BIOS issues & must run Boot-Repair to get correct dual boot entries for Windows as there is a bug in grub2's os-prober which Boot-Repair fixes. But you probably did not have to use the rename function as that is only for those Windows UEFI that only boot the Windows efi file.

But Ultrabooks then have Intel SRT and dual video issues. Links to installs with screen shots, and more info in link in my signature.

---

### Post by shadesofoctober on 2013-09-02
Well..
After thinking on it, I've realized the issue may be the kernel that ships with 13.04 has an issue with mounting the EFI partition in my scenario.
Someone here had a similar issue, and seeing their terminal output, I think they had a Y500 or similar laptop: 
[http://askubuntu.com/questions/335441/boot-efi-cant-be-mounted-after-kernel-update-ubuntu-13-04](http://askubuntu.com/questions/335441/boot-efi-cant-be-mounted-after-kernel-update-ubuntu-13-04)
Plus, boot-repair had the "buggy kernel detected" message appear at times.

Unfortunately, I could not even get into the virtual terminal and update the kernel or connect to the wifi or anything. The screen is compressed into the very top of the screen, and was unreadable. I could only just read that wlan0 was not a valid device, so couldn't connect to internet anyways (Wifi drivers failed to load).

So I went back into live-usb, and ran boot-repair again. I checked the options for purging and reinstalling Grub AND the same options for the kernel. This time.. Ubuntu actually booted!
I'm in the desktop now, installing all updates, so I'll have to wait until it's done and reboot it a few times to see if that was the actual solution.

---

### Post by oldfred on 2013-09-03
If you need proprietary video drivers be sure to install those before rebooting or you will need nomodeset or other boot parameters again.
If dual video check on bumblebee. More info in link in my signature.

---

### Post by shadesofoctober on 2013-09-03
It runs fine without Nvidia drivers, but I assume that accelerated 3D programs suffer performance (Haven't tried Steam without the proprietary drivers). Non-issue, because I use Windows for almost all my games.
They actually took out bumblebee support in the Y500 :( It's an SLI setup as well, so the graphics situation is a whole 'nother story on here! Luckily, I haven't had too many issues so far.

Anyhow, I've rebooted a couple times, and it goes into Grub, where I can choose between Ubuntu and Win8, which was my final intention.
I'm going to go ahead and say the issue was the kernel causing the failure to mount sda2.. so I'll mark this as solved for now. I appreciate everyone's input!

Edit: Ok, guess I can't edit titles.. memory's bad :)

---

### Post by sharathkumar on 2013-09-11
Hope this post helps:

[http://ubuntuforums.org/showthread.php?t=2170146&p=12781215#post12781215](http://ubuntuforums.org/showthread.php?t=2170146&p=12781215#post12781215)

---

