---
title: "After Ubuntu installation Win7 is corrupted"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by riccardosl45 on 2014-02-19
Hello guys,

I'm having a lot of troubles after installation of Ubuntu desktop 13.10 64bit on this machine:
[B]HP notebook Haswell + Intel technlogy SDD+HDD Hybrid on Win 7 64bit
[/B]
During Ubuntu installation I had issues to see my disk partitions and I used this command:
**sudo dmraid -Er /dev/sda**
I think this command did something wrong for windows!

Now after reboot Ubuntu is working fine but Win 7 installation is corrupted with this error:
[I]Status: 0xsc000000f
Info The boot selection faile because a required device is inaccessible.
[/I]
I found out that some UEFI or SRT Intel can be the issue on this link:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) 

**but I didn't disabled anything on BIOS!** many topics are talking about similar issues but there are many too many different solutions and I'm confused now.
What do you think is the best way to fix this at this point?

---

### Post by oldfred on 2014-02-19
These users posted what they did to re-instate SRT.

 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

---

### Post by riccardosl45 on 2014-02-19
> **oldfred said:**
> These users posted what they did to re-instate SRT.

 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

Hi I didnt changed any settings in my Bios so these solutions are explaining something different. I only deleted dmraid metadata but don-t know how to restore these metadata

---

### Post by riccardosl45 on 2014-02-19
boot repair output

[http://paste.ubuntu.com/6961883/](http://paste.ubuntu.com/6961883/)

---

### Post by oldfred on 2014-02-19
Was this originally a Windows 8 system? Haswell is so new that Windows 7 was not a standard.

Not sure that Windows 7 has the drivers with Haswell processors which are very new and for Intel SRT.

Microsoft was trying to get vendors to not back port new drivers for Windows 8 back to Windows 7, so users could not use Windows 7 on very  new systems. Have not heard anything lately, but that may be your issue.

But you still have to re-enable Intel SRT thru UEFI. And then maybe in Windows 8?

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by riccardosl45 on 2014-02-19
> **oldfred said:**
> Was this originally a Windows 8 system? Haswell is so new that Windows 7 was not a standard.

Not sure that Windows 7 has the drivers with Haswell processors which are very new and for Intel SRT.

Microsoft was trying to get vendors to not back port new drivers for Windows 8 back to Windows 7, so users could not use Windows 7 on very  new systems. Have not heard anything lately, but that may be your issue.

But you still have to re-enable Intel SRT thru UEFI. And then maybe in Windows 8?

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Hi this HP model Elitebook 840 is sold by vendor with windows 7 64bit professional pre-installed, probably because is a business laptop

I enabled on bios UEFI with CSM, before was Legacy option but windows is still not working, I tried boot-repair but no success

I read also here [http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file/423365#423365](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file/423365#423365) there is a common problem with HP bios but I can-t execute this

             this command $ sudo efibootmgr -v
  give me an error like
  fatal could-t open either sysfs or procfs directories for accessing EFI variables  Try modprobe efivars as root
  I obviously tried modprobe as root but nothing changed, any idea?

---

### Post by oldfred on 2014-02-19
Windows installed in BIOS mode will not boot in UEFI mode.
And Windows installed in UEFI mode will not boot in BIOS mode.

efibootmgr is to direct edit the NVRAM that UEFI uses to store boot order info. But since in BIOS boot mode, I do not think it can do much.
But if Intel SRT, you should have some Intel settings related to SRT somewhere in UEFI/BIOS.

---

### Post by riccardosl45 on 2014-02-19
> **oldfred said:**
> Windows installed in BIOS mode will not boot in UEFI mode.
And Windows installed in UEFI mode will not boot in BIOS mode.

efibootmgr is to direct edit the NVRAM that UEFI uses to store boot order info. But since in BIOS boot mode, I do not think it can do much.
But if Intel SRT, you should have some Intel settings related to SRT somewhere in UEFI/BIOS.

I never modified settings in bios before or after installation of ubuntu

I ONLY removed DMRAID metadata and at boot disk cache RAID0 is shown as Disabled... I this this is related with the issue , see screenshots below
BIOS
[ATTACH=CONFIG]250496[/ATTACH]

RAID ERROR
[ATTACH=CONFIG]250497[/ATTACH]

---

### Post by oldfred on 2014-02-19
Do you have settings to turn on Intel SRT for first drive or is that the control L shown in your screen shot?

---

### Post by masdeal on 2014-02-19
I am prefer not to install ubuntu software together with windows... Because chances of a crash will become bigger.

---

### Post by riccardosl45 on 2014-02-20
> **oldfred said:**
> Do you have settings to turn on Intel SRT for first drive or is that the control L shown in your screen shot?

I don't see a specific option in the bios, but Intel SRT screen shows that Raid0 is disabled, I probably need to re-install [COLOR=#000000]DMRAID metadata but syntax is quite complicated [/COLOR]

---

