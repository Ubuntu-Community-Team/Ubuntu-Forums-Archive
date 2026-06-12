---
title: "Clean Install of 24.04 on a New 512 Gb M.2 Sata ssd"
date: 2024-07-25
forum: Installation &amp; Upgrades
---

### Post by vbchevy on 2024-07-25
Good Morniing from Vairginia Beach, VA,

I have 3 computers (2 laptops 1 desktop) that do not qualify for Windows 11. Guess they now qualify as Legacy Hardware. They all work fine. Looks like Microsoft is trying to force you to purchase new hardware a little over a  year from now after Win 10 support ends. Heck with that. My stuff is working good and has been.

I have a 9 year old HP laptop that I would like to install Ubuntu 24.04 on to try it out. After using it for a time I can decide if it is worth installing on my other computers. Both OS's are Windows 10.

My question is:

1.) I installed a New 512 GB M.2 Sata 2280 drive in the HP Laptop. Do I need to Initiate, format and partition it through the command line or will the Ubuntu installler do all that. I have heard the stories about Ubuntu installs corrupting drives. Your expert input is appreciated as I am new to Linux.

Thanks in Advance,

Joe

---

### Post by tea for one on 2024-07-25
> **vbchevy said:**
> I have a 9 year old HP laptop that I would like to install Ubuntu 24.04 on to try it out. 
For a 9 year old PC, I would try Xubuntu 24.04 or Lubuntu 24.04 first.
How much RAM on your HP?
Try a live session first - are you familiar with this?
> **vbchevy said:**
> I have heard the stories about Ubuntu installs corrupting drives.
Highly unlikely, unless there's a power cut or insane user error.

---

### Post by vbchevy on 2024-07-25
Thanks Tea for One for the Advice on Xubuntu. It is spot on. The laptop is 64 bit with 8Gb of memory. I will download the latest Xubuntu ISO and flash it with Balenaetcher. I will install it on the laptop as I never used it previously. It was my wife's. The Ubuntu experiment begins.

Thanks again for your advice.

Joe

---

### Post by oldfred on 2024-07-25
HP historically is one of the least friendly to Linux installs.
It can be done, but may require some extra settings.

Make sure HP's UEFI firmware, even if now older is the latest version available.
If new SSD, then make sure it has latest firmware, even new drives may have newer firmware released.
Compare to vendor's support site
sudo dmidecode -s bios-version
udisksctl status

HP typically likes to boot an UEFI entry that says "Windows Boot Manager"
If single booting or erasing Windows you may need to create a UEFI boot entry that says Windows but boots grub2's shimx64.efi.
And/or HP does not recognize UEFI boot order changes with efibootmgr which grub2 used to set Ubuntu as first or default boot. It may boot once, then HP resets it back to the Windows UEFI boot entry. HP users have all reported they had to go into HP's settings, not boot menu and change boot order there.

HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI boot menu, <kbd>F10</kbd> for UEFI/bios settings

While issues are often common across many models, what model is your system?
Some also have issues with Optane card which is usually a small SSD used only by Windows for its hibernation file to speed boot, since Windows is so slow booting.

---

### Post by vbchevy on 2024-07-25
The model is HP Spectre x360 13-4102dx

---

### Post by oldfred on 2024-07-25
There seems to be many x360 models, not all the same over the years.

Not sure if any of the now older threads I saved on solutions to various issues still apply.
HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume) & 
[https://askubuntu.com/questions/1345338/common-failed-to-install-grub](https://askubuntu.com/questions/1345338/common-failed-to-install-grub)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086) & 
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)
HP Spectre x360 15t  Optane issue
[https://ubuntuforums.org/showthread.php?t=2474790](https://ubuntuforums.org/showthread.php?t=2474790) & 
[https://chanon.info/install-ubuntu-22.04-on-hp-envy-x360/](https://chanon.info/install-ubuntu-22.04-on-hp-envy-x360/)

---

### Post by vbchevy on 2024-07-26
I decided to go with the newest version of Ubuntu OS 24.04 LTS. It flashed and installed without an issue. It will take me a bit to get used to the GUI. I used the command line to install Chrome. I would expect there will be some U tube videos on basic how to use it.

Again, I want to use Ubuntu to make sure Linux is the way to go in the future after Windows 10 support ends next year. All my machines are working perfectly. 

Thanks for you input

---

### Post by yancek on 2024-07-26
The link below is to the official Ubuntu Desktop Guide and might be worth bookmarking for a new user.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by vbchevy on 2024-07-27
Thanks Yancek. I will definitely check it out.

When the time comes, how difficult would it be to migrate my Windows files into Ubuntu ? I use Acronis for my local and cloud backup. I have not looked into their Linux support yet.

---

