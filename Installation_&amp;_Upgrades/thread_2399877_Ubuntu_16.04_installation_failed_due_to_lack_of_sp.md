---
title: "Ubuntu 16.04 installation failed due to lack of space"
date: 2018-08-30
forum: Installation &amp; Upgrades
---

### Post by prajay on 2018-08-30
Sorry for the long post, but I'm trying to include all details regarding my issue. 
I'm trying to install Ubuntu 16.04 on my Asus vivobook Max (core i3 7100u + 8gb Ram + intel hd620) 

I previously had only Windows 10 on the laptop, but decided to shift over to Ubuntu.
Initially I tried with Ubuntu 18.04, however once it installed, I couldn't get past my Login Screen as it would be stuck on the purple load screen with no cursor after entering the password and clicking login. My senior from college figured that my display manager wasn't loading up and asked me to switch to lightdm. He asked me to do that via the tty from the login screen (alt + ctrl + f2) 

However, after this, instead of the try, i get a black screen with a stream on error messages "pci bus error severity corrected" 
So to recitify this, with help from the net, i entered "pci=noaer" by pressing e at the grub screen. This fixed the issue and i was able to enter into the tty. 
But since i couldn't connect to my WiFi (i do not know how to since most net tutorials suggested ifconfig and that didn't come pre-installed),i couldn't lightdm so i was stuck. 

So i decided to install Ubuntu 16.04. However, this would cause the error while installation that "installation failed due to disk filled up", even though I'm installing onto a completely new 1tb hardisk, using a 8gb pen drive. 

I'm really stuck here and would love some help. 
Thank you.

---

### Post by oldfred on 2018-08-30
Are you installing in UEFI or BIOS boot mode?
What install option? Default or Something Else.

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    

Some other Asus. May need UEFI update and if SSD, SSD firmware update.
 Asus X541UV [SOLVED] How to partition my ssd in order to install ubuntu 17.10 / 16.04.4
[https://ubuntuforums.org/showthread.php?t=2392861](https://ubuntuforums.org/showthread.php?t=2392861)
Asus Vivobook S15
[https://ubuntuforums.org/showthread.php?t=2375408](https://ubuntuforums.org/showthread.php?t=2375408)
ASUS VivoMini UN45 UEFI update required to see NVMe drive
[https://ubuntuforums.org/showthread.php?t=2355295](https://ubuntuforums.org/showthread.php?t=2355295)
Asus/Samsung problem with every NVME SSD and G752! 
[https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551](https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551)
[http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04) 

General UEFI install instructions in link in my signature. Only 9 "easy" steps. :)

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by prajay on 2018-08-30
Booting in UEFI MODE. 
Tried all options, clean install, dual boot with windows and all manually setting partions. None worked.

Tired the partition options you provided the link. Didn't work :/

---

### Post by oldfred on 2018-08-30
Have you updated UEFI? And SSD firmware?

       Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

