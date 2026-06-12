---
title: "Dual Boot With New HP Desktop (With A Twist)"
date: 2016-05-17
forum: Installation &amp; Upgrades
---

### Post by CoffeeBeanPie on 2016-05-17
Hi,

I have a HP Desktop with the following specs:
```

OS           : Windows 10 Home 64-bit
Manufacturer : HP
Product Name : 750-116
Processor    : AMD A10-8750
RAM          : 12GB (10.9 Usable)
```

I would like to setup a dual boot. The twist is that I would prefer to always boot to windows 10. And only boot to Linux if I interrupt to boot process by hitting [ESC], and then selecting [F9] Boot Device Options.

I apologize for the length of my post.

**Background**
Over the past month I have attempted to install Lubuntu five times and failed. I have used Lubuntu for a few years now on a couple of very old (non-UEFI) computers. 

I didn't do any reading before my initial attempts, so I have probably screwed some things up royally (Didn't know about disabling Fast Startup for example). I now know that HP has [wonky UEFI firmware]("http://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/Changing-Boot-Order-on-Dual-Boot-Windows-8-and-Ubuntu/td-p/2503733") and that may also be contributing to my issues.

I have done a lot of reading over the past few weeks. But the truth is I am drowning in acronyms. And now I find myself doing a lot more skimming than reading which is probably why I am having these issues to this day. I am familiar with the following [link]("http://ubuntuforums.org/showthread.php?t=2147295"). So feel free to bop me over the head if the answer is there in plain site and my dumbass just missed it.

The following [link]("https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-with-uefi") seems to have a working solution, but I don't want to use a msdos scheme (I want to use gpt). [This solution]("https://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook") seems to also work but I don't want to re-install windows.

**Steps I Took During Last Attempt**
[LIST=1]
[*]Disabled Fast Startup in Windows 10 
[*]Using Disk Management in Win10, shrunk windows partition by ~200GB (left un-allocated) 
[*]Already have LiveDVD ready (Lubuntu 16.04 LTS, AMD 64-bit) 
[*]Secure Boot Enabled (I read that modern versions of Ubuntu work with Secure Boot) 
[*]Fast Boot Enabled (I read that LiveDVDs work fine with Fast Boot) 
[*]Booted to LiveDVD ([ESC]->[F9]->Selected UEFI: HP DVDRW) 
[*]Selected "Try Lubuntu" at GRUB Menu 
[/LIST]

At this point I ran efibootmgr. I didn't try it with my previous installs. This is *basically* what I saw:
```

BootCurrent = 7
BootOrder = 0,1,2,7,4,5,6
boot0    Windows Boot Mgr
boot1    USB CD/Floppy
boot2    USB HDD
boot4    UEFI: IPv4 Realtek...
boot5    UEFI: IPv6 Realtek...
boot6    Fake Legacy Option
boot7    UEFI: hp DVDRW
```

Not sure why, but there was no "boot0003" option. Next, I clicked the "Install Lubuntu" desktop icon. The installation went smoothly. I selected the "Install Alongside Windows" option, entered the required data, and waited for the installer to complete. When the installation finished, I did not reboot, I ran efibootmgr again from the liveDVD. The results were exactly the same as earlier.

I rebooted **back into the liveDVD.** Why? I don't know. Again, I used [ESC]->[F9]->UEFI HP DVDRW. I ran "Try Lubuntu" again, and re-ran efibootmgr.
```

BootCurrent = 7
BootOrder = 3,1,2,7,4,5,6
boot1    USB CD/Floppy
boot2    USB HDD
boot3    Ubuntu
boot4    UEFI: IPv4 Realtek...
boot5    UEFI: IPv6 Realtek...
boot6    Fake Legacy Option
boot7    UEFI: hp DVDRW
```

NOTE: there was no "boot0000" option and Windows Boot Mgr was missing. 

I then removed the LiveDVD and rebooted. I saw a GRUB screen, there was an option for Windows but I selected Lubuntu (it may have said Ubuntu). I then ran efibootmgr again.
```

BootCurrent = 3
BootOrder = 3,1,2,4,5,6
boot1    USB CD/Floppy
boot2    USB HDD
boot3    Ubuntu
boot4    UEFI: IPv4 Realtek...
boot5    UEFI: IPv6 Realtek...
boot6    Fake Legacy Option
```

Again, Windows Boot Mgr was missing. At this point I rebooted, and at the GRUB screen I selected windows.

As with my previous attempts at making a dual boot machine, when I booted to windows the current time on the "Welcome Screen" was wrong. Every time I installed Lubuntu on this machine and booted to windows the current time would be off by a few hours. 

I rebooted: The machine booted directly into windows (no GRUB).

I rebooted: [ESC]->[F9] There is no option for Lubuntu.

I rebooted: [ESC]->[F10] There is no option/mention of Lubuntu.

I inserted the LiveDVD, rebooted and selected "Try Lubuntu". I installed boot-repair and ran it. The program told me to re-run it after I disabled secure boot. Here are the results with secure boot ENABLED: 
[http://paste2.org/B3nKdDBZ](http://paste2.org/B3nKdDBZ)

Here are the results with secure boot DISABLED:
[URL="http://paste2.org/1aAw3kZP"]http://paste2.org/1aAw3kZP
[/URL]
At this point, I rebooted. The GRUB menu had *several* entries, some pointing to efi files. Using GRUB I booted into windows. Rebooted and GRUB was gone. This is where I quit for a couple of days.

After a couple of days I booted into the LiveDVD and I re-ran efibootmgr:
```

BootCurrent = 7
BootOrder = 0,1,2,7,4,5,6
boot0    Windows Boot Mgr
boot1    USB CD/Floppy
boot2    USB HDD
boot3
boot4    UEFI: IPv4 Realtek...
boot5    UEFI: IPv6 Realtek...
boot6    Fake Legacy Option
boot7    UEFI: HP DVDRW
```

Note: 'boot0003' was in the list but had a blank entry.

I attempted to add a lubuntu entry with the following command:
```

sudo efibootmgr \ 
--create \
--loader \\EFI\\ubuntu\\shimx64.efi \
--label "ubuntu" \
--part 1 \
--disk /dev/sda

```

The above added "ubuntu" to the beginning of the BootOrder list given by efibootmgr:
```

BootCurrent = 7
BootOrder = 3,0,1,2,7,4,5,6
boot0    Windows Boot Mgr
boot1    USB CD/Floppy
boot2    USB HDD
boot3    Ubuntu
boot4    UEFI: IPv4 Realtek...
boot5    UEFI: IPv6 Realtek...
boot6    Fake Legacy Option
boot7    UEFI: HP DVDRW
```

Finally, I used efibootmgr to switch the order so that the HP firmware didn't stomp on what I had done:
```

sudo efibootmgr \
--bootorder 0,1,2,3,7,4,5,6

```

I rebooted: There was no GRUB and the machine went straight into windows.

I rebooted: [ESC]->[F9]: Ubuntu did not appear in the list.

This is where I gave up (again). If you made it this far then thank you for reading. I would like to have windows 10 always boot. The exception would be if I hit [ESC]->[F9] at boot time and select Lubuntu. Any suggestions would be appreciated.

---

### Post by oldfred on 2016-05-17
HP is not dual boot friendly.
Just about all versions will not boot the ubuntu entry, not sure even with Secure boot on if that is another complication.

You can leave Windows boot as default and use its one time boot keys to choose to boot Ubuntu, but with HP you have to change the hard drive or fallback boot entry to really be /EFI/Boot/shimx64.efi. Then you should be able to choose the hard drive or fallback entry to boot Ubuntu when desired.

Some also edit Windows BCD with an Ubuntu entry. I believe that does a reboot and UEFI also has an internal one time boot entry that is then used.

       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

      
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
    [URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL]

---

### Post by CoffeeBeanPie on 2016-05-19
Thank you for the reply.

Unfortunately, I don't have any options to set a custom efi file (that would have been great).

The link using bcdedit worked. Pointing directly to the shimx64.efi caused the system to boot directly to GRUB. However, this solution won't work for my situation. I need the system to always boot to Windows 10 unless I do something special (like [ESC],[F9]).

It is so odd how seemingly every post I have read on this topic has the opposite problem. They can see ubuntu in their list of boot sources but they cannot get GRUB to work. I can't get Lubuntu to show up in my list of sources, but I can force GRUB to appear during the boot process. It is also odd how after I installed Lubunutu the entry "boot0000 Windows Boot Mgr" vanished from the efibootmgr list.

Right now I am in the process of setting up Windows again. I ran a system recovery (the one that keeps your files). My hope was that it would re-install (reset) the EFI partition. But the ubuntu directory is still there. I want to try and install Lubuntu one last time. But this time I will add "boot0000 Windows Boot Mgr" manually to the list in efibootmgr. I can't use Linux on this computer unless both Windows and Lubuntu appear in the boot sources list.

Thanks again for your help and all of your posts on this subject.

---

### Post by oldfred on 2016-05-19
If you copy shimx64.efi to /EFI/Boot/bootx64.efi, then set in UEFI Windows as default, you should have what you want.
You then can use the one time boot key in UEFI Escape-f9 and choose to boot hard drive entry. 
If you do not have a hard entry we can add one with whatever description your like just using /EFI/Boot/bootx64.efi as boot file.

Shows boot entries and files used (without slash or backslash) from Ubuntu terminal.
sudo efibootmgr -v

---

### Post by CoffeeBeanPie on 2016-05-24
Update: I managed to get a working solution. 

Again, my goal was to install and use Lubuntu without changing the normal behavior of windows. Windows should ideally boot and run as though I had never installed Lubuntu. My hope was to select Lubuntu at boot time by pressing [ESC] and selecting the distro from a boot sources list. Unfortunately, the firmware on the computer I am using prevents this from happening.

And again, my specs:
[http://support.hp.com/us-en/document/c04803066](http://support.hp.com/us-en/document/c04803066)
HP 750-116
Windows 10
BIOS Version --> AMI A0.08, 1/14/2016


In UEFI mode, I am limited to 3 or 4 boot sources. I cannot add anymore by installing another OS. I cannot add a customized boot source or file in the UEFI/Bios firmware settings. My boot device options are always:
1) Windows Boot Manager*
2) UEFI: IPv4 Realtek PCIe GBE Family Controller
3) UEFI: IPv6 Realtek PCIe GBE Family Controller

*If I install Lubuntu, "Ubuntu" replaces Windows Boot Manager until I boot into Windows.

If there is a DVD in the computer at boot time then there is a 4th option in the UEFI Boot Sources menu:
4) UEFI: HP DVDRW

**Solution**: [Burn a DVD with rEFInd.]("http://www.rodsbooks.com/refind/getting.html") Use that disk every time I want to use Lubunutu. The bootable image file does not support secure boot. So I had to disable it.

Having to disable secure boot is a negative. But I'm ready to move on.

If you are looking to use a real dual-boot system (not the hack I'm doing), then you may find this page useful: 

[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

