---
title: "New to UEFI, need help please"
date: 2017-08-17
forum: Installation &amp; Upgrades
---

### Post by robert_frittmann2 on 2017-08-17
Pastebin: [https://paste.ubuntu.com/25335731/](https://paste.ubuntu.com/25335731/)

Hi all, I've been volunteering locally to install Lubuntu Linux on some old laptop computers, which until now has gone perfectly, without any problems. The machine I'm currently working on has given me no end of grief though, as it is a newer machine which had Windows 7 on it. The owner wanted me to blow away the Microsoft OS entirely and replace it with Lubuntu 17.04. At first I couldn't even get the USB to boot, regardless of the Boot Options in the BIOS. Eventually I switched to UEFI mode and it booted from the Live USB at that point. The first installation failed spectacularly, with all manner of UEFI errors. My second attempt seems to have worked, and I now have a Lubuntu installation on the hard disk, but there is no bootloader. I can boot the new OS, but each time I have to manually select the appropriate *.efi file from /boot/efi which is a real nuisance, and not fit for purpose, to return to the user.

To try to fix this myself I have read through [Rod Smith's page]("http://www.rodsbooks.com/linux-uefi/") and some of the links therein. I have been through the [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") process, but the pastebin procedure failed, so I have uploaded the report manually, [here]("https://paste.ubuntu.com/25335731/"). I have very little experience with UEFI, and would really appreciate some help. I have backed up the laptop owners' original OS using dd, backing up both partitions separately, but I can't even seem to restore that to just return the laptop in its original condition, abandoning the idea of installing Lubuntu. Basically, I'm stuck between a rock and a hard place, and I'd really appreciate some help.

---

### Post by oldfred on 2017-08-17
What brand/ model system?
Many need various work arounds.
Have you tried with UEFI Secure Boot off. 
It should work with Secure boot on, unless you also need proprietary drivers for video or Internet.

Have you updated UEFI from vendor?

First list of boot options did not even show ubuntu. After Boot-Repair now it shows Ubuntu entry.
Same UEFI boot list as report:
sudo efibootmgr -v

Offically with UEFI you should be able to just set Ubuntu as first in boot order, which it became after Boot-Repair's update and that becomes default boot.
But many vendors violate UEFI standard that says NOT to use description as part of boot.

Since only Ubuntu, if one of the brands that only boots a Windows entry you can do this and set this as default boot. Alternative d1 from link in my signature.
       
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1. And then set "Windows" entry to first in boot order, if not reset automatically.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Check again:
sudo efibootmgr -v

More info 
man efibootmgr

---

### Post by robert_frittmann2 on 2017-08-18
Wow, thanks **oldfred**, that is a huge amount of  information, and a lot there for me to digest. As I mentioned, this UEFI  stuff is all quite new to me. I've been installing various different  operating systems on computers since about the MS-DOS v5.0 days, and  have encountered all manner of scenarios, but this one just seems  unnecessarily complex. Is there some way for me to just disable the UEFI  stuff and go back to legacy mode? I don't see the advantage or  necessity for UEFI at all, and I just want to get this laptop to boot up  to Lubuntu without the end user having to select boot options each time  and locate the required *.efi file. The last laptop I changed from  Windows to Linux took me about 2 days, including migrating the apps and data,  and customising the desktop for the user. I've now had this particular  laptop on my desk for almost a week, and I still can't get it to even boot  up by itself without intervention each time. Is there some quick and easy way to force it to legacy mode? It just won't boot at all from USB in legacy mode, no matter the boot order.

The laptop is an HP ProBook 6540b. When it came to me it had Windows 7 Pro OA installed, and the UEFI was disabled. I have not updated the UEFI firmware at all. Since my last message here, **[COLOR=#0000ff]*the laptop is now not booting up at all*[/COLOR]**, nothing is showing on the screen, although the CPU fan spins up and the status LEDs light up. This is getting worse! I understand from Rod Smith's tome that this can be a known issue when dealing with UEFI, and he mentions going into a text editor to fix it.
> [CENTER]*A problem that many people had through much of 2013 (but with decreasing  frequency since then) was blank displays when booted in EFI mode.  Sometimes this problem can be fixed by adding [SIZE=1][FONT=system]nomodeset[/FONT][/SIZE] to the kernel's command line. You can do this by typing [SIZE=1][FONT=system]**e**[/FONT][/SIZE]  to open a simple text editor in GRUB. In many cases, though, you'll  need to research this problem in more detail, because it often has more  hardware-specific causes.*
[/CENTER]
[SIZE=1]
[Linux on UEFI: A Quick Installation Guide]("http://www.rodsbooks.com/linux-uefi") &#8680; [Installing Linux]("http://www.rodsbooks.com/linux-uefi/#installing") &#8680; Fixing blank displays[/SIZE]


But that's kind of difficult to achieve without a working display. I'm at my wit's end with this machine, and it really is putting me off doing these volunteer installs of Linux in future. I'm going to end up as "the bad guy" here, failing to deliver, and worse, returning an unusable device to its owner. I really need some help, in simple terms, of how to get this working again. I have some technical ability, and could rip the hard drive out if need be, or locate the CMOS battery and reset everything like that, if it would help. However, I don't want to stumble ahead blindly any more. Thanks for the help so far.

---

### Post by oldfred on 2017-08-18
I still recommend using UEFI installs, if UEFI hardware.
But some early implementations by vendors (and by Linux/grub) did not work as well as it should. So best to always update UEFI from vendor.
And it looks like your HP is a first gen Intel i-series chip which would be first gen UEFI.

HP is one of several vendors that violates UEFI spec, and causes further issues.
Since only Ubuntu the simple work around of booting Ubuntu/grub/shim file using "Windows Boot Manager" description works and is easy to do.

UEFI also has another UEFI setting, fast boot. Fast boot assumes that system hardware & software configuration has not changed and immediately jumps to booting. Info from UEFI for operating system to use on hard drive is normally refreshed with every reboot. This speeds booting, but can be so fast you have no time to press a key to get into UEFI/BIOS to change boot order or other settings.
Best to have fast boot off when reconfiguring system.
Last menu item in grub 'System setup' is also another way to get into UEFI.
Most systems will do a "normal" or full reboot with a cold boot or full power down. Laptops may require removing battery, also. And with power disconnected hold power switch to fully drain all power. A few system need the jumpers on motherboard, or battery on motherboard removed to totally reset.

You can convert UEFI to BIOS just by reinstalling grub2. UEFI uses grub-efi-amd64 where BIOS uses grub-pc. 
But since gpt partitioning you will need a 1 or 2MB unformatted partition with the bios_grub flag which can be anywhere on drive which you must have for grub to install. Use gparted to shrink one partition slightly and add the bios_grub flagged partition. Or use Rod Smith's gdisk to add a partition with code ef02. With gpt actual code is a very long GUID, but parted uses bios_grub and gdisk ef02 to assign actual internal code.
Then often easier to use Boot-Repair to reinstall grub using advanced mode. How you boot install/repair media, UEFI or BIOS is how it normally installs or repairs.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/
[/URL]
 Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html) 

For newer computers:
      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694(Rod Smith):
I converted to only using gpt on Linux only drives using BIOS boot with bios_grub partition. Back then my XP was on a separate MBR drive. Windows only boots with UEFI from gpt partitioned drives.
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help) 
    
Do not know about AMD/ATI video. Often nomodeset required with proprietary video.
And AMD has multiple drivers, some that only work with certain versions of Linux kernel and some that only work with certain AMD/ATI cards/chips. What works best can be an issue.
       Radeon: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

---

### Post by robert_frittmann2 on 2017-08-18
Again, thanks for your help, **oldfred**. Currently I have removed the laptop's primary battery and AC adaptor, and will leave it powered down for 24 hours in the hope of getting the display working again. I have not, as yet, resorted to resetting the CMOS, so hopefully that won't be necessary, but is the next logical step if I still have no display. The rest of your suggestions I can't really follow at present, until the display comes back on, haha. :p I had tried using the external VGA port, but that didn't initialize either.

It really seems to me that UEFI is more trouble than it is worth, but it looks like I'm going to have to learn more about it than I really wanted to. I'll keep you posted on how this laptop progresses. I've given the laptop's owners a link to this discussion, so that they can see what's going on here too.

---

### Post by robert_frittmann2 on 2017-08-19
I have put the main battery back into the laptop again now and tried booting up. Still the laptop screen and external VGA port do not initialize, and the status LEDs are still blinking a power-on self test (POST) error. Specifically, it is the numlock and capslock status LEDs, and they blink in groups of 3. According to [this post on the HP site]("https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/Scroll-Num-Lock-and-Caps-Lock-LED-s-blinking-and-battery-not/m-p/879685#M53288"), that error code probably means that there is a RAM memory problem. Of course, that was for a different model of HP laptop, so I'm not totally convinced, but at least I know that the flashing POST status LEDs mean ... something. I have downloaded both the User Guide and the Maintenance and Service Guide manuals for this HP ProBook 6540b, but neither of them give the POST status LED error codes. Thanks HP. I'll keep looking for a solution to the POST problem, before I can even begin to solve the UEFI problem.

UPDATE: I've followed the procedure in the Maintenance and Service Guide manual for removing and re-seating the RAM, but I'm still getting a POST error showing the 3 flashes of a RAM problem. Running out of options here. While I had the laptop open, I also removed the CMOS battery for a while, but that didn't seem to help either. I'll try leaving the CMOS battery, main battery, AC power, and RAM out for 24 hours next. [Here]("https://support.hp.com/us-en/document/c01732674") is a document on the HP website showing the POST error codes for this laptop. Select the option for "BIOS flashing light error codes for computers released between 2011 and January 2015". [Here]("https://support.hp.com/us-en/document/c01732674#ReseatMemory") are the instructions for re-seating the RAM memory modules. This particular laptop doesn't have anything in the externally-accessible expansion RAM slot, so I had to follow the procedure on p.118 of the Maintenance and Service Guide manual to remove the internal RAM from the slot under the keyboard.

---

### Post by robert_frittmann2 on 2017-08-21
As it turns out, I have been unable to proceed further with this UEFI  problem, as another problem has emerged which prevents me from following  any of **oldfred**'s advice. There is definitely a RAM  memory problem during the power-on self test (POST) which is preventing  the screen (both internal and external) from initializing. This whole  process of changing the OS from Windows to Linux was a Hail Mary  exercise anyway, to try to breathe new life into an old laptop. Now, it  seems, this old laptop has breathed its last. It is not economically  viable to replace the RAM in it. I was doing the Linux install for free  anyway. Fortunately, I had backed up the entire hard drive first during  the procedure, while the laptop was still working, so I have the laptop  owners' data all safe and secure without needing to remove the hard  drive. I am now just awaiting on the owner to let me know what they want  done with the dead body, whether it should be returned to them or given  a decent burial.

Thanks anyway, **oldfred**, for  all your help and advice. It looks like I am going to have to force  myself to learn more about UEFI in the future anyway, if I am to  continue doing this type of upgrade from Windows to Linux on old  computers. I guess my definition of an "old computer" is getting rather  outdated, haha. Even the old ones these days have newer technology on  them than I'm used to.

---

### Post by QIII on 2017-08-21
Hello!

Please don't mark a thread as solved if it is not.  This might be confusing to others searching for a solution and finding none.

Thanks!

---

### Post by robert_frittmann2 on 2017-08-21
Ah, okay, sorry about that. I didn't want anyone wasting their time trying to help me further to resolve the original UEFI issue when the laptop is dead and this is not going any further, from my perspective. I see your point, though. Thanks.

---

