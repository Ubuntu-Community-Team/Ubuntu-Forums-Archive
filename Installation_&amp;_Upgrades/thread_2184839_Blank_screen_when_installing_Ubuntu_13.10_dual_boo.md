---
title: "Blank screen when installing Ubuntu 13.10 dual boot with UEFI"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by toby.dublin on 2013-10-30
I have been unsuccessfully trying to dual boot Ubuntu 13.10 to a new-ish laptop with Windows 8.1. The laptop has UEFI. I have used both live DVD and live USB, and I have tried with SecureBoot both enabled and disabled. Every time I have the same failure. Just before the GRUB screen appears, the following error message briefly flashes on the screen "error variable root isn't set". The GRUB screen then appears. I have tried both Trying-out the Installation, and Installation, and each time after I select one of these options the screen then goes blank and stays blank. When using a DVD, the DVD continues to whirr for several seconds, before going dead. 

Out of interest I have also tried installing OpenSUSE 12.3 in the same ways (with SecureBoot both enabled and disabled in turn, etc) and the installation stalls at a similar point each time, which leads me to think it's something to do with the way UEFI is set up on this laptop.

The laptop is a Toshiba Satellite P845T about 3 months old, with the HDD replaced by a SSD. It came with Windows 8 pre-installed, and I upgraded to Windows 8.1 last week, shortly before trying to install Ubuntu. Curiously the Windows 8.1 desktop has a watermark in the lower-right corner that says "SecureBoot isn't configured correctly", but that may not be relevant to this query, as googling this suggests that many people have this watermark even though SecureBoot is configured correctly. And enabling/disabling SecureBoot makes no difference to the message.

Any help would be gratefully received, as I'd love to get this dual-booted with Ubuntu. Thanks!

---

### Post by skhandige on 2013-10-31
Try setting "nomodeset". Refer [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by fantab on 2013-10-31
Have you disabled 'Fast Startup'?
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Have you disabled 'Fast Boot'?
[http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm](http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm)

Also check in the BIOS/UEFI for 'Intel SRT', usually this is to found when SSD and HDD are provided by the manufacturer on Intel-based machines. If you find it then Disable it.
[http://superuser.com/questions/476777/properly-disabling-intel-srt](http://superuser.com/questions/476777/properly-disabling-intel-srt)

---

### Post by toby.dublin on 2013-11-01
Thanks, skhandige and fantab.
I have tried nomodeset, I have disabled Fast Startup, and I have disabled Fast Boot. Still no luck.
I am unable to see an option to disable Intel SRT in the BIOS options. I had a look through the info in the link you provided, fantab, and I am a little confused about how to disable SRT if there is no opton to do this given in the BIOS menu.
How can I tell if I have SRT enabled if there is no option in the BIOS menu?
Thanks!

---

### Post by fantab on 2013-11-01
> **toby.dublin said:**
> ...
I am unable to see an option to disable Intel SRT in the BIOS options. I had a look through the info in the link you provided, fantab, and I am a little confused about how to disable SRT if there is no opton to do this given in the BIOS menu.
How can I tell if I have SRT enabled if there is no option in the BIOS menu?

It it probable that you don't have it. Like I said, it is usually found on computers that come pre-installed with both SSD and HDD, where the SSD is used as a 'cacheing' device.

So you don't have a HDD on the laptop but only SSD, right? Or do you have both?
How did you "Burn" the DVD? It is possible that there could be an issue with your DVD drive.
Have you tried to "Burn' the .iso to USB pendrive? You can use [Unetbootin]("http://unetbootin.sourceforge.net/") to burn .iso to USB drive.

Also we need to know exactly what ERROR you see.

---

### Post by oldfred on 2013-11-01
It looks like it is part of grub2's startup.

[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)> GRUB's normal start-up procedure involves setting the &#8216;prefix&#8217; environment variable to a value set in the core image by grub-install, [COLOR=#b22222]setting the &#8216;root&#8217; variable to match[/COLOR], loading the &#8216;normal&#8217; module from the prefix, and running the &#8216;normal&#8217; command (see [normal]("http://www.gnu.org/software/grub/manual/grub.html#normal")).  This command is responsible for reading /boot/grub/grub.cfg, running the menu, and doing all the useful things GRUB is supposed to do.     



But I have no idea how to fix, as if it then works it must not really be wrong? Other than a full reinstall of grub2 which may reset it to correct value??

---

### Post by toby.dublin on 2013-11-02
Hi, many thanks for the assistance. I have tried again, now using USB drive, but still the same error: "error: variable 'root' isn't set".

I have tried reading the notes sent by oldfred, and as far as I understand (I'm new to all this) the next step is for me to try using the Boot Repair tool. However, I'm unsure how to use it - I read the instructions, but they seem to assume you have already installed Ubuntu. How do I access and run the Boot Repair tool if I am at the grub menu but have not yet installed Ubuntu?

---

### Post by fantab on 2013-11-02
Here is boot repair CD: 
[https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair)

See the 1st option.

---

### Post by toby.dublin on 2013-11-02
So, I just tried installing Boot-Repair on a Live USB using UnetBootin. I then rebooted. The GRUB menu came up, and gave me the option Boot Repair Disk Session. I pressed enter, and the screen went blank and stayed blank, just as it has done whenever I've tried to install Ubuntu. So I seem unable to use the Boot Repair Disk. Is there some other way?
(I have been wondering whether this is all just me being incompetent, so I've tested by trying to install Ubuntu on an old PC (pre-UEFI) using the same USB drive I've been unsuccessfully using on this new laptop. On the old PC I successfully managed to install and dual-boot Ubuntu and Windows. So I think it's not user error!)

---

### Post by fantab on 2013-11-02
I suspect some hardware or Windows8 issue, though I can't think of anything more. I'd suggest you look carefully through your UEFI menu and see if there is anything that you suspect that is perhaps preventing other OS to load or boot. Usually this is done by 'Secure boot', but since you've tried both with 'secure boot' and without it... I can't think of anything more.

I have found some links from Toshiba Forums and it seems you are not the only one.
[http://forums.toshiba.com/t5/Computer-Troubleshooting/cannot-dual-boot-on-P845t-S4310/td-p/388433](http://forums.toshiba.com/t5/Computer-Troubleshooting/cannot-dual-boot-on-P845t-S4310/td-p/388433)
[http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=283448&tstart=0](http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=283448&tstart=0)

The following thread is from these forums, but no solution:
[http://ubuntuforums.org/showthread.php?t=2109707&page=2](http://ubuntuforums.org/showthread.php?t=2109707&page=2)

I think the best option for you, if you want to dual boot will be to disable UEFI boot and switch to Legacy/BIOS/CSM boot. [Backup all your important data, as the switch will force you to change the partition table from 'GPT' to 'msdos'. And the Partition table switch will erase all the data on the Hard disk]. Then re-install Windows 8 and Ubuntu. Also contact Toshiba service and see if they can offer any help.

Good Luck...

---

### Post by toby.dublin on 2013-11-03
Many thanks. I shall look at that option, but I think I am now out of my depth! I'm afraid that I shall have to give up. It's a shame as I had really been hoping to get Ubuntu installed on this laptop. Hopefully somebody will come up with some solution to the Toshiba problem!

---

### Post by oldfred on 2013-11-03
Some more threads and what those users did with other Toshibas.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
Toshiba laptop C850 Windows 7 with upgrade to 8 version -  sudodus
[http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025](http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025)
 [SOLVED] Can't install Windows 8 & Ubuntu in Toshiba Portege Z930 with explanation how by OP feb 2013
[http://ubuntuforums.org/showthread.php?t=2114290](http://ubuntuforums.org/showthread.php?t=2114290)

---

### Post by ubfan1 on 2013-12-11
If you are getting to the black grub menu screen, it's not a secure boot issue.  Try the below video and ssd options on the linux line -- edit the grub commands by typing "e" (instructions at bottom of screen).
For UEFI machines (with a black screen grub (grub-efi)  without any
function key options, like the older grub-pc, edit the grub menu and add
the below options on the "linux" line, then boot with F10 or ctrl-X.

Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic
i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

To slow SSDs to allow them to boot:
libata.force=noncq

---

### Post by antonioalonzi85 on 2013-12-12
Hi,

Is the screen blank just because of the luminosity to 0?
For me this happens (I have a HP-650).

Try either to increase the luminosity either to press enter and wait for a couple of times.

EDIT: sorry I think I replied seeing only the first message of this thread.

---

### Post by travel.test on 2013-12-23
Hi, I'm having the same problem have you had any luck with this?

---

### Post by The-Master on 2013-12-28
Hi. I'm having the same problem. I have an NVIDIA geforce card. I've tried nomodeset and all of the other settings at grub and it isn't working. It's very frustrating. I've tried ctrl+alt+f1 once the screen goes blank to get to the command line and from there I've tried updating the system and installing the nvidia drivers but I can't startx. I'd love to get this sorted because I can't deal with windows 8 even after stripping it down.

Anyone have any other things to try?

---

### Post by oldfred on 2013-12-28
For nVidia nomodeset should work.

If Intel i915 see this note, not just Dell but many i915.
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

> Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux. 



---

### Post by bangbangtanggates on 2014-01-03
> **travel.test said:**
> Hi, I'm having the same problem have you had any luck with this?

I had the same problem.Now i solved it and reply this message for u in ubuntu 13.10. 

I just diabled Intel Processor Graphics in bios.And it worked.

Try it. If it doesn't work you can contact me ,my email is {removed}

It takes me almost 24 hours to make it work.

---

### Post by oldfred on 2014-01-04
Forums are regularly searched by bots. Removed email as then you may get spam or worse. Please use PM if you want separate conversation, but purpose of forum is to post questions and solutions so others can also use them.

---

### Post by manthony121 on 2014-01-14
I have a Toshiba Satellite C55D-A5381 laptop, that would not boot in UEFI mode.  It is set to dual boot with Win8.  Trying to boot Ubuntu 12.04.3 LTS 64 bit would lead to an eternal purple screen.  Adding "acpi_backlight=vendor" to the boot command line fixed it.  Thanks!

---

### Post by wbatten1 on 2014-03-04
I had the same problem trying to install on my HP ENVY17.  I ignored the root warning message and everything still installed fine.  As far as the black screen, I thought my screen was off.  Turns out it wasn't... For some reason, Ubuntu installer was setting my screen brightness to 0.  All I had to do was hit the +brightness button on my keyboard and voila!  Problem fixed.  I know, it sounds too simple to be the problem, but it's likely your issue.

---

