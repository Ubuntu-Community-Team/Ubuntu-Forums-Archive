---
title: "Ubuntu on  VAIO Duo 11 Ultrabook"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by greenchiliishot on 2012-12-19
Is it possible to install Ubuntu on a VAIO Duo 11 Ultrabook? Is somebody did it with success?

---

### Post by oldfred on 2012-12-21
Is this an system with Intel SRT. That is usually what an Ultrabook is? And is it Windows 8?

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

    
       Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)

---

### Post by mhemeryck on 2012-12-23
Hi all,

I also have a Sony VAIO Duo 11 Ultrabook for which I'd like to install ubuntu alongside the existing windows 8 OS. I already tried some of the instructions on [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), but I can't seem to boot a live ubuntu.

Specifically I tried the following:

[LIST]
[*]got into a boot menu via the *assist* button (separate button to access UEFI / BIOS options I suppose)
[*]accessed BIOS options: set secure boot to legacy, enabled boot from USB. Boot in UEFI mode
[*]boot from live USB
[LIST]
[*]prepared live USB using ubuntu secure remix 12.10 image in unetbootin (on another pc running an older distro of ubuntu). Did not change too much on the USB drive besides removing all files on it first, partioning was default FAT32
[/LIST]
 
[*]from the boot menu via the *assist* button: tried to boot from USB
[/LIST]
From this point on, my PC just froze. I also tried to set the BIOS option to boot in legacy (non-UEFI) mode, but this didn't make a difference.


Could it be that I can't boot from live USB due to the partioning of the USB drive? Or something else?


Thx in advance.

---

### Post by oldfred on 2012-12-23
Usually legacy mode means BIOS not UEFI. You want UEFI mode but not secure boot,  but every UEFI menu is different and what settings are needed vary.

Did you also turn off fast boot?
Did you download 64 bit version of 12.10?

Some have issues with brand of flash drive, some with USB3 ports, try USB2, some with issues on which installer was used to create flash drive. And some do not have a valid download. 
And those that seem to change one or more of these then seem to usually get it to work but we never know what the real issue was.

---

### Post by Open and Sourced on 2012-12-23
You might have to get a burned disc. Since many of the Linux distro's are compact, you might have to be careful what your doing. It could end detrimental.

---

### Post by mhemeryck on 2012-12-24
> **oldfred said:**
> Usually legacy mode means BIOS not UEFI. You want UEFI mode but not secure boot,  but every UEFI menu is different and what settings are needed vary.

Tried UEFI boot first (as this is what I'd probably need to boot alongside an existing windows 8 partition), then I tried to boot using legacy mode, but this didn't work either.

[QUOTE=oldfred]Did you also turn off fast boot?[/QUOTE]Couldn't find such an option in the boot menu, so no.

[QUOTE=oldfred]Did you download 64 bit version of 12.10?[/QUOTE]
Yes, I used the [ubuntu-secured-remix 12.10 64-bit version]("http://sourceforge.net/projects/ubuntu-secured/files/ubuntu-secure-remix-12.10-64bit.iso/download").

[QUOTE=oldfred]
Some have issues with brand of flash drive, some with USB3 ports, try USB2, some with issues on which installer was used to create flash drive. And some do not have a valid download. 
And those that seem to change one or more of these then seem to usually get it to work but we never know what the real issue was.[/QUOTE]

[QUOTE=Open and Sourced]
You might have to get a burned disc. Since many of the Linux distro's  are compact, you might have to be careful what your doing. It could end  detrimental.
[/QUOTE]I previously did all my ubuntu installs using a disk, but I wanted to use a live USB here because my VAIO doesn't have an optical drive. Perhaps I'll try to boot from CD using an external optical drive.

Don't have that external optical drive lying around here atm, so it might take some time before I can post an update.

thx already anyway :)

---

### Post by Josh1 on 2012-12-26
Hi,

Just chiming in here.

I managed to get Ubuntu 12.10 working ALMOST perfectly since the 2012-11-21.

Everything almost works, however the multitouch errors out.

I might have to create a video tutorial on how to install Ubuntu 12.10 onto the device as it can be a bit of a PITA.

I bought this device for well under retail ($800 off) through a special coupon that the retailer provided.

---

### Post by mwtzzz on 2012-12-26
I'd like to know how to get wireless working on this hardware. Does it work out of the box on Ubuntu? Cuz I installed the latest Puppy Linux and it didn't work.

---

### Post by mwtzzz on 2012-12-26
> **mwtzzz said:**
> I'd like to know how to get wireless working on this hardware. Does it work out of the box on Ubuntu? Cuz I installed the latest Puppy Linux and it didn't work.
 
Answering my own question: yes it does work out of the box on Ubuntu 12.10. I downloaded the 64 bit iso, used the USB installer to make a bootable USB from it and it booted and worked without any problems.

---

### Post by hcdaume3 on 2012-12-28
I can confirm that pretty much everything works out of the box.  Aside from the usual gripe about the stupid "mouse" thing, there are two things that don't work for me, and I'm hoping someone has solved these issues.

The first, as mentioned by another poster, is the touchscreen.  It will work for about 3 seconds and then timeout or something.  It shows up in "xinput list" as "N-trig DuoSense id=10	[slave  pointer  (2)]" and one in a while I can get it to scroll whatever the active window is and "xinput test 10" will sometimes register for a second before it stops.

The second is that what should be the middle mouse button doesn't work.  This is INCREDIBLY infuriating, since that's what I want to use to paste.  If you "xinput test" it, then holding and scrolling up/down with the pointer gives you the correct buttons 5 and 6 (IIRC) but just pressing it on its own gives you NOTHING.  Has anyone been able to fix these?

If I can't fix both these issues, I have to say that it's probably going to get sent back.

---

### Post by mhemeryck on 2013-01-13
> **mwtzzz said:**
> Answering my own question: yes it does work out of the box on Ubuntu 12.10. I downloaded the 64 bit iso, used the USB installer to make a bootable USB from it and it booted and worked without any problems.

Some questions:

[LIST]
[*]what ISO are you using? just the default one from the main ubuntu site?
[*]what USB installer did you use? I tried unetbootin
[*]what special options did you set for the boot mode? UEFI / legacy?
[*]... any other clue why it doesn't work on my VAIO? :)
[/LIST]
Meanwhile, I've managed to boot (an older) ubuntu 10.10 live cd I had still lying around via an external optical drive, in legacy mode. From here on, I guess I'll burn a more up to date version of ubuntu (the secured remix), to finally get to installing.

---

### Post by mhemeryck on 2013-01-13
> **mhemeryck said:**
> Some questions:

[LIST]
[*]what ISO are you using? just the default one from the main ubuntu site?
[*]what USB installer did you use? I tried unetbootin
[*]what special options did you set for the boot mode? UEFI / legacy?
[*]... any other clue why it doesn't work on my VAIO? :)
[/LIST]
Meanwhile, I've managed to boot (an older) ubuntu 10.10 live cd I had still lying around via an external optical drive, in legacy mode. From here on, I guess I'll burn a more up to date version of ubuntu (the secured remix), to finally get to installing.

Update: I did burn the ubuntu secure remix 12.10 and did manage to boot if via external optical drive. Problem is that I had to set booting to legacy mode (I am actually using it right now); booting in UEFI mode showed "no operating system available".

I was just wondering whether to interpret the installation instructions ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) as installing in legacy mode and then repairing the install using the boot repair. I'd just like to be sure this is the way to go before screwing up my boot sector ...

---

### Post by mwtzzz on 2013-01-14
> **mhemeryck said:**
> Some questions:

[LIST]
[*]what ISO are you using? just the default one from the main ubuntu site?
[*]what USB installer did you use? I tried unetbootin
[*]what special options did you set for the boot mode? UEFI / legacy?
[*]... any other clue why it doesn't work on my VAIO? :)
[/LIST]
 ubuntu-12.10-desktop-amd64
Universal-USB-installer-1.9.2.1 
Installed to a USB stick and it boots in UEFI mode
 
If you figure out how to make the VAIO a dual-boot system, please let me know. I am unable to shrink the C: drive (partition) using Minitool in order to be able to put linux on it

---

### Post by oldfred on 2013-01-14
Have you tried using Windows own MMC to shrink the Windows partition. Do not create partitions with Windows as it may convert to dynamic and reboot so it can run chkdsk and make whatever repairs it needs on a resize.

---

### Post by mwtzzz on 2013-01-15
> **oldfred said:**
> Have you tried using Windows own MMC to shrink the Windows partition. 
 
Thanks for the tip. I went ahead and did this with the Windows disk management tool and it worked. I didn't know Windows had a partitioning tool that actually worked, so that's good to know.
 
Anyway, I shrunk the partition, made my Linux partitions, and installed Ubuntu, but the only way I can boot it is by replacing the Microsft efi (/[FONT=Courier New]EFI/Microsoft/Boot/bootmgfw.efi) with the "grub.efi" that ubuntu created (located in /EFI/ubuntu/). With this I can boot Ubuntu, however I am unable boot Windows from the Grub menu (complains about invalid path to efi file).[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]It would be nice to have a single menu giving me the choice of booting either OS ... Anyone know how to "add" the Microsoft EFI to the grub goot, or vice-versa?[/FONT]

---

### Post by oldfred on 2013-01-15
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'


You can use Boot-Repair or manually add entries which are in the bug report workarounds. 
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mhemeryck on 2013-01-16
> **mwtzzz said:**
> 
[/LIST]
 ubuntu-12.10-desktop-amd64
Universal-USB-installer-1.9.2.1 
Installed to a USB stick and it boots in UEFI mode
 
If you figure out how to make the VAIO a dual-boot system, please let me know. I am unable to shrink the C: drive (partition) using Minitool in order to be able to put linux on it

Thx for the info; I've tried this, but I couldn't manage to boot from USB. Did you change anything in the BIOS USB settings? (or any other BIOS setting?). Any special USB port? I just think it's strange that your (supposedly) identical VAIO would be able to boot from USB, while mine won't :)

Anyway, I'll probably need to install from external optical drive in legacy mode and then convert to EFI later. I'm just not so eager to start fiddling with the boot partitions ... Probably will take some time before I get to that, but I'll keep you posted.

---

### Post by mwtzzz on 2013-01-17
> **mhemeryck said:**
> Thx for the info; I've tried this, but I couldn't manage to boot from USB. Did you change anything in the BIOS USB settings? (or any other BIOS setting?). Any special USB port? I just think it's strange that your (supposedly) identical VAIO would be able to boot from USB, while mine won't :)
 

 
The only thing I did in BIOS was put the external device at the top of the boot order. 
 
It worked pretty much out of the box using the tools I mentioned for creating the boot stick.
 
> 
Anyway, I'll probably need to install from external optical drive in legacy mode and then convert to EFI later. I'm just not so eager to start fiddling with the boot partitions ... Probably will take some time before I get to that, but I'll keep you posted.
 
Yeah the EFI stuff is new to me. I see Ubuntu posted a reply above regarding how to fix their bootloader.
 
Although Ubuntu works - wireless and everything else - it does freeze pretty frequently on me. I think Linux still has some catching up to do with this hardware.

---

### Post by mwtzzz on 2013-01-21
> **oldfred said:**
> grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
 
 
You can use Boot-Repair or manually add entries which are in the bug report workarounds. 
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
 
I fixed it by booting Ubuntu Secure Remix (live CD), and running the Boot Repair program.

---

### Post by mhemeryck on 2013-01-22
> **mwtzzz said:**
> I fixed it by booting Ubuntu Secure Remix (live CD), and running the Boot Repair program.

Exactly what I did :)

To summarize for those interested, what worked for me:

[LIST=1]
[*]downloaded ubuntu secure remix, i.e.atm  ubuntu 12.10 + boot repair ([https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)) and burned to CD
[*]opened bios settings (check for the pink 'assist' button underneath the keyboard) and changed booting to legacy, disabled secure boot.
[*]restart and boot via external optical drive (connected via USB)
[*]prepare partitions as described in UEFI booting ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) using gparted from live cd. here's what I did:
[LIST=1]
[*]shrunk windows data partition to about 50 gigs
[*]created root partition (ext4) of about 10 gigs
[*]created home partition (ext4) of about 42 gigs
[*]foresee 512 MiB for swap (actually, that one isn't used atm, any idea why?)
[*]for the boot loader: re-use the first partition
[/LIST]
 
[*]run the installer: assign the partitions as foreseen
[*]reboot
[*]reload from live cd again
[*]run the boot recovery from disk
[*]access bios options again, set boot to UEFI (did not re-enable secure boot)
[*]... that's pretty much it
[/LIST]
Some remaining issues atm:

[LIST=1]
[*]touch screen did work flawlessly from live cd, but it does crash for the installed version
[*]after booting in windows again and putting it in stand-by mode, it seemed all wlan radio was turned off and I couldn't turn it on again. Since there doesn't seem to be a hardware button, I didn't find any way to fix this in windows. Fortunately, I could fix it for ubuntu using rfkill
[*]checking gparted again, the swap partition doesn't seem in use. What can be the reason / do I really need one (given that it's an SSD drive ...)
[/LIST]
Anyhow, it's great to have ubuntu on it again, so I can finally do some work :). thx all for your support!

---

### Post by mwtzzz on 2013-01-23
> **mhemeryck said:**
> Exactly what I did :)
 
foresee 512 MiB for swap (actually, that one isn't used atm, any idea why?)

 
Swap won't be used unless your computer has very little total RAM, or you load a larged, bloated program with memory leaks into memory.
 
> 


touch screen did work flawlessly from live cd, but it does crash for the installed version

 
same here
 
> 
[LIST=1]
[*]checking gparted again, the swap partition doesn't seem in use. What can be the reason / do I really need one (given that it's an SSD drive ...)
[/LIST]
 
If you're going to be running big programs, then you should have swap space. 
 
from command line type "swapon -s" to make sure it's using the swap partition

---

### Post by ktogias on 2013-02-11
I have submitted a bug report about multitouch support on a Sony Vaio
Duo 11 ultrabook/windows tablet hybrid I purchased recently. The bu
report and attached info/log files is at
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1121379](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1121379)
. 

Any guidance in order to further investigate or test fixes will be
appreciated. 

If you have Sony Vaio Duo 11 and would like to run ubuntu on it, please go at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1121379](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1121379) and press the "affects me too" button. This will rise bug's "heat" and thus increase the possibilitty to be noticed by ubuntu developers and other technical community members.

---

### Post by Redallover on 2013-03-08
I recently installed Ubuntu 12.10 (Secure remix) to my Duo 11, the touchscreen is semi buggy, it will work the first time you touch the screen then stop working, but if you touch the screen with some pressure with two fingers it will semi work again then stop. I also get an issue if i try to use the touch screen then i try to use Nautilus to view files/directories I can double click to open a folder, the fix for me is to reset the laptop. After a reset if I dont use the touch screen I can doube click in Nautilus to open folders and it will work.

---

### Post by Naguissa on 2013-05-06
ACCOMPLISED!!!


Windows 8 and Linux permanent Dual boot, even after starting Windows!!!

[Sony  VAIO with Insyde H2O EFI bios Windows 8 / Linux GRUB2 Dual boot - Blog -  Naguissa.com - Recursos y discusiones sobre desarrollo web]("http://www.naguissa.com/blog.php?verpost&comentario=962#ENG")

---

