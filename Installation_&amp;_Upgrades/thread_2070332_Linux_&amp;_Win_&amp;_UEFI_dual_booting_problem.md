---
title: "Linux &amp; Win &amp; UEFI dual booting problem"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by zacharysonicfast on 2012-10-12
I just tried to dual boot Mint 13, an Ubuntu Derivative. I unplugged my hard drive and wanted to install linux to a flash drive. That worked perfectly with one hardware exception  - will post in another topic area.

The problem is when I plugged my hard drive that has Win7 on it, windows forced me to reformat and re install without the flash drive present.

Ok, how do I dual boot any linux with win7 uefi and not screw up win7??

I want to select the boot OS manually through boot up screen not a boot manager.

PLEASE be specific and step by step if at all possible. I don't want win7 or linux messing with the others' boot stuff.

Note: I would prfer copying win7 to a *much* smaller SSD drive and dual boot with any linux on that hard drive the traditional way, but I can find any way to copy win7 without screwing with my existing hard drive and it's partitions.

I figure if I copied win7 to an ssd drive, removed and saved the normal hard drive, installed the ssd drive with win7 on it then tried installing linux the typical way to the ssd drive I could do it that way.

Can this be done without being forced to buy expensive Acronis True Image Plus???

I can take zero chances messing up the win7. The notbook is still under warranty and I might have to put the regular hard drive back in for any warranty claims. It is an ASUS K55a and about a month old.

And I certainly will not use Geek Squad for anything...

---

### Post by zacharysonicfast on 2012-10-12
Had to reply just to turn in the instant notification setting....

---

### Post by oldfred on 2012-10-12
How did you install to flash drive. As UEFI boot or BIOS boot? Generally best if both are same. Do not understand why Windows would want a reinstall unless you converted from BIOS to UEFI or vice-versa. 

[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT]("https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT")
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Bootable UEFI USB Key 
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

My flash drive is just seen as another hard drive. But I only have BIOS. But my flash drive full install is gpt.
UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by zacharysonicfast on 2012-10-12
I unplugged the hard drive, plugged in the flash drive, started the computer, installed Mint 13 kde 64 bit, restarted, tested linux, shut down, plugged hard drive back in. That is when linux quit working and win7 started working.

I would rather go with linux but seems there isn't any detection for the usb dongle i use nor any drivers.

So, i plan on using linux for wifi and win7 for the usb dongle.

Note the computer does not come with any restore disks so installing win7 in a vm is not possible.

---

### Post by oldfred on 2012-10-12
I am not sure where you are at, but you can post BootInfo which will both document system and tell us all the details of how you are booting.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by zacharysonicfast on 2012-10-13
> **oldfred said:**
> I am not sure where you are at, but you can post BootInfo which will both document system and tell us all the details of how you are booting.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Win7 with uefi on a regular laptop hard drive.

I can run a live version of linux but that takes far too long to do every time and it ties up my burner if i want to use it. 

I have an XP desktop computer that I dual boot with linux. I select which hard drive i want to boot from at computer start up and away i go.

I am very hesitant to screw with the uefi stuff since i don't know how to repair the computer should it break. And paying geek squad is out of the question.

Things would be much easier if any version of linux would work with a usb internet dongle, prepaid only type.

I could just pull the HD out and swap it with an ssd then install linux only. I only have to keep the HD with win7 intact that came with it for any warranty claims.

I am using a prepaid dongle because I do not want to give out my SS number or ID number to any company. I have no idea what they do with it behind my back. :=$

---

### Post by oldfred on 2012-10-13
I always suggest a liveCD or USB or repair disk for Windows for the current version of every system you have installed. Otherwise when you have problems you have no way to repair it. And a way to reinstall. With Windows that is often a image backup as Windows does not make it easy to reinstall like Ubuntu does.

Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by zacharysonicfast on 2012-10-13
Thanks for the links and info. This will take me a bit of time to go through.

Is there any risk of destroying my ability to use win7?

Personally I would want to remove the existing hard drive and install an ssd drive, then dual boot win7 and linux off the ssd drive. I wanted to try the flash drive because it is faster than the DVD.

I am still having trouble understanding UEFI and how it works. BIOS was so easy....

I have this tab pinned so it is there all the time. Once I discover how to gt this issue taken care of I surely will mark it as solved.

If you don't hear back from me at least weekly then you know my computer won't work and something got screwed up.

Will your solutions work with other linux OS's?

I had a bad experience with Xandros. It dual booted with windows, but when I wanted to remove xandros windows refused to boot. Had to R/R the whole hard drive.

Will both Win7 Home Premium and some version of Linux both fit on a 64gb ssd drive?

Or would I be stuck having to buy a bigger one?

How can I clone just my win7 partition to an ssd so I can work with that leaving me peace of mind?
I don't want to fool with my existing partitions at all (resize, etc)

I have a desktop that I can use to plug in the drives. But that desktop doesn't have uefi on it.

Things would be so much easier if any linux would recognize my internet dongle and actually work.
I wouldn't need to use windows at all.

History - about 3 years ago i got fed up with XP and all the expense. I tried several versions of linux and settled on pclos because it has a similar feel to that of xp. But that was on my desktop. And no more expense in antivirus programs, firewalls, etc. I was in HEAVEN! LOL 

Ubuntu was OK but absolutely HATED the gnome desktop. I want KDE.
I tried different desktops and still want KDE.
Ubuntu back then was great with all the available software. But ownership problems between pclos and ubuntu were abound. Had to stick with pclos.
I still have ownership problems with accessing data on some of the drives on my desktop computer. I need 100% total access to stored fies from any computer any operating system. So, on my data drives i was forced to format in ntfs to get the job done.


Now, due to my situation i had to buy a toy computer (aka netbook/laptop). I miss linux, but it is too much hassle to run from cd/dvd every time and that too makes is slow.

I don't do command line. Hate typing and having to remember syntax.

If I am forced to get a bigger SSD drive then which is the best one for Linux? How big?

I read that some mfr's are going to build in automatic trim support (no OS needed to do the job).

---

### Post by zacharysonicfast on 2012-10-13
It appears that none of the links you provided are suitable for my needs.
They all require typing and manually editing things

I was looking for some sort of automatic process with a nice GUI for me to choose the options I want.

Why is it so difficult to dual boot when stuck with uefi??

The old BIOS system was great. Install each to a separate drive so neither know that the other one exists. Select from boot up screen at computer boot up and horray! I can choose without a problem.

I don't like boot loaders for the simple fact that they mess things up badly, especially when you want to try different configurations.

I tried manually adjusting grub to allow for an XP boot option but it didn't work.

I am a computer user and don't want to fool with making manual changes. Point and click works best for me.

Perhaps this is why many windows users won't switch to linux? Too much hassle to get things done?

I dunno.

I just want to dual boot where neither knows the other exists and select it from the computer boot up screen with Linux as the default boot option.

What happens if I am using windows and a virus screws up the boot loader and neither will boot the next start?
Or I decide to get rid of some flavor of Linux in favor of a different one then windows won't boot and grub won't work?

While ubuntu is the biggest Linux distro, is there another one more suitable to my needs?

I don't care for Mint but it at least has the KDE desktop that I like.

I do like Linux puppy though. Fast and does what I need. But then there is that dreaded uefi issue to circumvent.

Flash drives are ok, but the real speed comes with an SSD hard drive.

Now I don't know what to do or even how to mark this thread as no plausible solution exists to do what I want when dealing with dual booting and uefi.

downloading a win7 trial formatting flash drives twice, making special partitions and such is a lot of unnecessary work in my opinion.

Maybe just install linux to a flash drive and plug it in when needed? Slower but won't force me to reformat and reinstall windows.

And using windows 'fixit' disks in the past is the most useless thing they ever come up with. You have to be MSCE certified to do anything other than formatting a drive maybe.

I have a sandisk cruzer fit drive, 32gb that I keep installed all the time. I run readyboost on 1/2 of it. I was hoping to run some flavor of linux on the other 1/2. But it seems uefi won't allow it.

I don't want to plug and unplug any flash drive as it will wear out the usb connector, which can't be replaced because of this being a toy computer (laptop).

I am stuck with windows for now until i can find a way to boot the way i want without spending weeks trying to get the thing working.


Will the linux community get this issue fixed anytime soon?

I would rather they fix the mobile broadband dongle issue myself, then I wouldn't need windows.

Any other suggestions that do not involve excessive work on my part? Or risk losing win7?

I must keep win7 no matter what for the time being.

---

### Post by oldfred on 2012-10-13
The minimum size I have seen suggested for Windows 7 is 30GB, I install Ubuntu in 25GB, so you can fit both into your 64GB SSD, but will not have a lot of room. 

I keep all data including some if the hidden folders in /home on my rotating drive and just use SSD as system drive. Not sure with Windows as with XP I could move most data to my NTFS data partition but many programs and some data would only go into the c: drive, so that tends to grow quickly.

I so not suggest trying to copy Ubuntu to SSD and you cannot copy gpt partitions using any low level tools as the gpt has unique data in it.

Lots of detail info on SSDs:
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

If system is UEFI, you should just use it to install to new drive. Do not know if the macrim backup will work with UEFI but it should. You can probably just copy the efi partition over. But UEFI Windows also has another partition MSR or Microsoft reserved partition.

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.

With UEFI you do have to have everything configured for UEFI. Actually in the "old" days everything was configured for BIOS, but that was the only choice, now there are two UEFI or BIOS and it is more confusing.

---

### Post by zacharysonicfast on 2012-10-13
So I am stuck with each OS knowing the other is there?

What happens if I unplug the flash drive that I plan on having linux on for the interim? Or the flash drive fails?

Does that mean Windows won't boot?

This is so confusing to say the least.

If only linux would recognize and support mobile broadband dongles I would have a much easier time with this. No win7 needed . . .

The risk of having each OS knowing the other exists can open things up for loads of problems, especially since windows is easy to infest with malware that can prevent either from working.

I will certainly check into the links you provided. thanks.

Note: I have two laptops to fix this problem. I don't want my wife to use windows even though she loves the cutzie features.

If only I could pull my hard drive out, install linux to a flash drive, plug my hard drive back in then choose which to boot from when I turn on the computer.

I tried that but windows forced a reformat and reinstall. Then linux wouldn't work.

This problem doesn't exist when using a live version of linux.
But that is too much hassle and too slow.

---

### Post by oldfred on 2012-10-13
I am afraid dual booting is a bit more advanced. And UEFI is new so there may be cases where you have to use commands to do things. 

But we usually post terminal commands as Linux has many gui's and each is different on how to do things, where the terminal command is the same. Most cases you should just have to copy & paste which does not require really learning the commands any more than clicking on menus. 

I still do not understand what you did that Windows had to reinstall. Just plugging drive back in should not have caused that. 

My suggestions have always been to have Windows on one drive and fully bootable without any other drive. But you can chainload from grub's menu to boot Windows. That also works with UEFI. And on my system a flash drive is seen as another hard drive to boot, so there is no real difference.

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by zacharysonicfast on 2012-10-13
This still doesn't tell me how to dual boot and it requires a windows full install cd/dvd to do it.

[http://i.technet.microsoft.com/dynimg/IC514412.png](http://i.technet.microsoft.com/dynimg/IC514412.png)

Is there a linux pic that shows how linux uses uefi?

Or are we all still at the mercy of microsoft just to use a computer?
I am scared to try messing with 'wipe the disk' instructions on that page. If I mess up i won't have a computer, warranty, or internet.

Is there a program i can get that does all this stuff for me??

---

### Post by oldfred on 2012-10-13
If you have Windows install in UEFI mode on a gpt drive and have additional space, all you have to do is boot the 64bit version of Ubuntu in UEFI mode. Then you an install it just like any other install. Grub goes into the efi partition not the MBR. You can use defaults of / (root) and swap or create additional /home or other partitions depending on how you install.

Many of these users had some issues and that is why they had a thread, but worked thru them. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
UEFI installs in BIOS, Boot-Repair to fix
[http://ubuntuforums.org/showthread.php?t=2048457](http://ubuntuforums.org/showthread.php?t=2048457)
[http://ubuntuforums.org/showthread.php?t=2058453](http://ubuntuforums.org/showthread.php?t=2058453)

GUIDE: (U)EFI installation Also full install post #52 superfreak on pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Dual Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)

---

### Post by zacharysonicfast on 2012-10-13
I was trying to have manual control over which OS I waned to boot from, not use grub or win bootloader or uefi bootloader to do it.

If one thing happens then neither might not be bootable. And since uefi is new I have no clue as to how to fix the problem other then if i am lucky use windows restore partition and lose everything.

Also, I would have rather had a choice in Linux OS's and not be stuck with ubuntu or any other one specifically.

The way I did it before I could just unplug one drive R/R the other one ad switch at a whim.

If I had ubuntu on a flash drive and win7 on a hard drive then removed the flash drive what happens then?
Will windows force me to R/R the hard drive because of a configuration change?

I must preserve windows at all costs while the computer is under warranty. Or they will charge me to re install windows to put it back to factory specs.

Note: I tried Knoppix once - it caught my power supply on fire immediately.

Is there a way to fix uefi so as to ignore any other hard drive or OS on a different boot medium? Or write protect uefi so that no changes could be made and thus preserve the windows drive?

I know it ignores live cd's/dvd's.

Also, just a thought - what happens if I want to save a file to the windows hard drive when running a live Linux OS?

Just by accessing the drive could cause problems, right?

I looked in my BIOS.here is a setting to turn disable UEFI.

If I do, what happens then? Could I dual boot the way I want without windows screaming for a R/R?

It is beginning to look like I get a choice of one or the other and I am not comfortable with Microsoft choosing that for me.

Again, if Linux would even recognize my internet usb dongle there would be a chance that I could get it to work.

I am not  windows hater or a linux lover. I want something that works with the lest amount of problems. So that means Linux is the winner.

The boot repair stuff might seem easy but I should never have to resort to such things just to dual boot.

And what happens if things get screwed up and I can't get to the site to get the program or technical support??

Remember, when I am using windows, a hacker or virus could damage the uefi partition and on the subsequent boot, neither would load.

---

### Post by zacharysonicfast on 2012-10-13
> **oldfred said:**
> I am afraid dual booting is a bit more advanced. And UEFI is new so there may be cases where you have to use commands to do things. 

But we usually post terminal commands as Linux has many gui's and each is different on how to do things, where the terminal command is the same. Most cases you should just have to copy & paste which does not require really learning the commands any more than clicking on menus. 

I still do not understand what you did that Windows had to reinstall. Just plugging drive back in should not have caused that. 

My suggestions have always been to have Windows on one drive and fully bootable without any other drive. But you can chainload from grub's menu to boot Windows. That also works with UEFI. And on my system a flash drive is seen as another hard drive to boot, so there is no real difference.

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

Uh-Oh, i just realized something. What if my laptop has uefi active, I put in a totally new hard drive ten install linux to that drive. Will linux know to make extra partitions?
When manually partitioning a drive will linux be smart enough to force me to make the extra uefi partition?

And what size does it need to be? 200mb? 300mb?
50mb? And more importantly why any particular size?? Why the first partition? Why not the last partition?
The uefi partition would only be used once per boot. Why put it on the fastest part of a normal hard drive what the speed would be precious to the user?

Maybe when we are all forced to go to cloud computing I won't have to worry about it.

---

### Post by oldfred on 2012-10-13
You have to have a boot loader. 

The UEFI specification says it should be first, but some have made it second or third. I think the FAT32 driver in UEFI cannot read over a certain size so it is easier just to specify it should be first than try to explain exactly what the limits are. 

If a separate drive and you boot the install in UEFI it will just install without any issue.

Grub does not create a correct chain load entry with UEFI, but you can use Boot-Repair to add a correct entry.

---

### Post by wnelson on 2012-10-14
Add the following to /etc/grub.d/40_custom

menuentry "Windows 7 " --class windows --class os {
    insmod part_gpt
    insmod part_msdos
    set root='(hd0,gptX)' <-- Your gpt partition number, ie. gpt2
    search --no-floppy --fs-uuid --set=root XXXX-XXXX ---> Your uuid for ms-dos partition, ie. 763A-3456
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi  <-- copy bootmgfw.efi from your Windows installation.

For some help. [https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)


Thanks walt

---

### Post by zacharysonicfast on 2012-10-15
I have contacted ASUS about the issue to see if I can turn off UEFI and use BIOS only since I only have a 500gb hard drive and UEFI isn't needed. Still waiting for a reply.

If I can then I shouldn't have any more problems.

I don't want a boot loader controlling anything. Had a few bad experiences with those, especially GRUB.

---

