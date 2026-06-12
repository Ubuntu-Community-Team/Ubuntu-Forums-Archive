---
title: "Dell Inspiron 3891 won't boot Linux Live DVD or USB"
date: 2021-10-29
forum: Installation &amp; Upgrades
---

### Post by WB0HYQ on 2021-10-29
Just purchased a Dell Inspiron (3891) and am attempting to install Ubuntu 20.04 on it. I've finally managed to get the DVD drive in the F12 boot menu, but when I click on it, the DVD drive fires up, I get the Grub menu, but every time I select "Ubuntu," the DVD drive clatters a bit, then the whole computer powers off, leaving just the power light in the switch on. I have a backlit keyboard, and that goes dead as well so I know the power is gone.

I'm a bit worried the BIOS may be at fault here as when I'm in it, the first paragraph across the top states: "UEFI Only." Right under that is this:

NOTE: Legacy boot mode is not supported on this platform.

Now, when I boot normally into Windows 10, I can view every directory on the DVD. I've also used it on one of my laptops to see if it actually bootable. Linux Live runs just fine there, so it has to be the computer itself blocking the Linux boot.

I've also turned off Secure Boot. I had to do that before the DVD even became available in the boot menu.

Any help out there?

Bill

---

### Post by ActionParsnip on 2021-10-29
Sounds like a bad drive. A Dell Inspiron 3891 seems to be a tower PC with a conventional CD tray drive.
do you have a 1Gb USB stick (or larger) that you can use here?

---

### Post by WB0HYQ on 2021-10-29
Hmm. Could be. But then how am I able to access the drive once I'm back into Windows? I popped a music cd in and it plays just fine as well. I admit the DVD drive is very flimsy and only a skeleton-type drive with the barest of parts.

Bill

---

### Post by WB0HYQ on 2021-10-29
Progress, of sorts. I tried using an 18.04 DVD. It behaves the same way as the 20.04 disk. After booting now, I get a Grub menu. The 18.04 disk had an entry for "check disk for errors." None were found, so I tried the topmost item: "Run Ubuntu (without installing). The drive clanked away for about thirty seconds, and the purple screen with the marching dots appeared. This is a good sign. However, once they stopped, the computer powered down once more as before.

I changed the boot order to try the DVD drive first, and simply let it boot. I got the Grub menu once more. This time, I chose "Install Ubuntu." The machine thought about it for a while, then this popped up:

(initram) Unable to find a medium containing a live file system

Um, what? Windows 10 is on the machine (250G SSD) and there is a 1Tb drive as well. Both are functional in Windows.

So now I am confused as to the error message. It does seem as if this particular Dell model is incapable of working with any external form of booting. There are hints in the Dell forum of this. I suspect it is all due to the "Legacy boot mode" not being supported on this platform (as the BIOS notice says). Pity we can't give a computer a try before we spend the bucks for it.

Bill

---

### Post by ubfan1 on 2021-10-29
Ubuntu's been booting UEFI secure boot since 2012, so lacking legacy mode should not be a problem.  The Windows checks to perform before everything else are: 
1)Filesystem in good shape, run chkdsk to confirm. 
2)Not in RAID mode, need the ahci drivers added to Windows to switch to ahci mode [https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10](https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10)
3)Windows Power Settings have Fast boot off (so shutdown does not hibernate). Need to dig a bit through Advanced options.... to even find the Fast Boot disable.
4)Check that the Windows partitions are not "Dynamic", but are simple.  Ubuntu installer cannot use the proprietary dynamic partitioning.
Turn Bitlocker OFF/disable for the install.  The default these days is to supply the Windows disk with Bitlocker enabled, and until you set up a Microsoft account and backup your keys, you rely on TPM register values to decode -- these values may change with BIOS updates...and who knows what other hardware changes, so if you use Bitlocker, be sure to have your own key backups.
5)Do check with Dell for any firmware updates.  Even new machines can be several releases out of date, since updates may be quite frequent.
6)Look through the UEFI/BIOS settings -- Not much experience with Dell, but just tried booting a year old laptop from USB without problem.
7)Some machines (Acer?) give you more options after you set a supervisor password.  Google to see if Dell ever does this.

With the Windows/hardware stuff out of the way, Hashcheck the downloaded Ubuntu ISO, burn the ISO as slowly as possible, Check media if offered, Try USB.  You should be able to get the live system to run with the "Try" grub option.   Good Luck.

---

### Post by grahammechanical on 2021-10-29
> (initram) Unable to find a medium containing a live file system

That is referring to OS that is on the DVD. The installer is supposed to set up a file system in RAM and load Ubuntu into that for the purpose of trying Ubuntu or using the running Ubuntu in RAM to install to a hard drive.

The comment made by ubfan1 is sensible: "burn the ISO image as slowly as possible." It is a long time since I burned an ISO to DVD and before that it was burning to CD. And yes the advice back then was to burn the ISO as slowly as possible. It might just be the solution.

Regards

---

### Post by WB0HYQ on 2021-10-29
Okay. Lots of information here.

1) Filesystem is fine on both the SSD and the bigger one.

2) Here might be the killer. There are three settings for RAID: OFF, AHCI, and RAID On. When I click the Off or AHCI, I get a huge popup warning me the operating system will definitely not like it, so I Cancel out.

3) Fast Boot is only: Minimal, Normal, and Auto. It cannot be turned off.

4) According to Windows Disk manager, a right-click on either of the drives shows "Convert to Dynamic disk" as a menu item, so I'm assuming they are NOT dynamic already. It appears there is no Bitlocker on my system. When I search for "bitlocker" or "manage bitlocker" it always sends me to a web page telling me how it works. There is no Control panel entry I can find for Bitlocker. I do have a MS account. I've never used Bitlocker on any of my systems.

5) My BIOS is from October, 2021. The "check for update" feature returns "OK"

6) I can boot my laptops easily with the same disk I'm trying on this machine, so I have to assume they are correct.

7) I once locked myself out of BIOS using a password. Even though I wrote it down, and tried it several times, when I really needed it, the BIOS said my password was wrong. I'm a little gunshy on this one.

I'll keep pecking away.

Bill

---

### Post by WB0HYQ on 2021-10-29
> **grahammechanical said:**
> That is referring to OS that is on the DVD. The installer is supposed to set up a file system in RAM and load Ubuntu into that for the purpose of trying Ubuntu or using the running Ubuntu in RAM to install to a hard drive.

The comment made by ubfan1 is sensible: "burn the ISO image as slowly as possible." It is a long time since I burned an ISO to DVD and before that it was burning to CD. And yes the advice back then was to burn the ISO as slowly as possible. It might just be the solution.

Regards

I'm very familiar with the "initiating RAMDisk" as machines boot up, and I've run a lot of Ubuntu Live sessions. This one doesn't do that. I agree that the ISO may have been burned too rapidly. The default is "as fast as humanly possible" and I didn't catch that. I'll reburn it and make sure it is set to a much slower pace. My burning software has a check box for "verify after burn" and I did click that before, however.

Tired now. I'll hit it tomorrow morning.

Bill

---

### Post by ubfan1 on 2021-10-30
Here's a link for disabling bitlocker:  [https://windowsreport.com/disable-bitlocker-windows-8/](https://windowsreport.com/disable-bitlocker-windows-8/)
Bitlocker was on by default, and the only initial keys are in TPM registers which are subject to change, so I think finding out your bitlocker situation would be first.
The "Fast Boot" or "Fast Startup" that needs to be off is not a  BIOS/UEFI settings option, it is a Windows/Settings/..Power  option.(found on the power options page after you click a few things like "show hidden options" and Advanced options.  
Seems like you are in RAID mode, so getting the AHCI drivers installed has to be done.  See earlier post's link.

---

### Post by WB0HYQ on 2021-10-30
BitLocker is definitely not on my machine. As I am running Windows10 Home, I don't have access to the GP editor, however, when I go to advanced power options and click the link for BitLocker Settings, I get taken to the Microsoft Store which will let me install it. Also, no mention of BitLocker is made whenever I look at disk drive information.

I called Dell support, waited a while, then talked to a rep. He advised I shouldn't change the RAID mode as this particular computer is set up to run in that mode. Of course, he was probably doing this as a CYA thing, but just the same there are many complaints in the Dell forum that describe the pure despair of those who have changed it and bricked their computers. BSODs abounded.

My quest to install Linux on this machine isn't quite that urgent. I did burn an ISO of 21.10 (at 1x speed) and the boot results were exactly the same as before. I get the GRUB, then choose Ubuntu and the computer shuts down. If this level of system protection continues, I wouldn't be surprised that the only way one can get a "foreign" OS on one's computer is to build it yourself, OR replace the primary drive with a new one and start again. That is, of course, if the BIOS will let you boot from something other than a primary drive.

In 2022, I will have been working with computers for 60 years. Maybe it's time to just roll with the punches and become a simple user.

Bill

---

### Post by ubfan1 on 2021-10-30
Virtualbox runs on Windows I think, and These days, Windows Subsystem for Linux is developing, (but maybe not GUI yet for Win10?).  Waiting a bit and checking for experiences others have had is a good strategy too if there's no hurry.  Since your USERI Settings does have AHCI, I'd think it should work, but if others have tried and failed, wait until you see some success.

---

### Post by WB0HYQ on 2021-10-30
My gaming machine runs Windows 10 because the games aren't crossdecked to Linux (darn it). I've already installed the little app allowing the Ubuntu (18.04) Terminal to run. It works fine, but has limited capability. For grins, I created a special directory, made it system-protected, and put a text file in it. The Ubuntu Terminal couldn't change or edit it, even using SUDO. Windows seems to have encapsulated it neatly.

Perhaps the Linux powers-that-be might begin investigating a method of installing Linux on a machine while the current OS is running, setting everything in motion for a reboot, which would then give the GRUB and we're off and running. Or better yet, a Windows app that scans your computer and tells you what you need to do to install Linux on it. Those would be pretty cool in my estimation.

Bill

---

### Post by ubfan1 on 2021-10-30
Try making a USB3 install media.  I just saw a note on Dell not supporting USB2 on Intel Skylake and later.  Can't say how the DVD is attached or if it would be affected. [https://www.dell.com/support/kbdoc/en-us/000132108/how-to-install-ubuntu-and-windows-vista-or-7-as-a-dual-boot-on-your-dell-pc](https://www.dell.com/support/kbdoc/en-us/000132108/how-to-install-ubuntu-and-windows-vista-or-7-as-a-dual-boot-on-your-dell-pc)

---

### Post by WB0HYQ on 2021-10-30
I went out yesterday and bought an 8G thumb drive (supposedly for USB3) and burned the ISO to it. The USB port is there, and I can use it, but there doesn't seem to be any way to get the BIOS to give me that option on the F12 boot menu. Looks like Microsoft has finally locked their systems from being replaced. I'm not used to giving up, but this one has me whipped.

Bill

---

### Post by sudodus on 2021-10-30
Strange that Dell has abandoned Linux :-( I have some older Dell systems, that are very willing to boot via F12 and the temporary menu both in UEFI mode and BIOS mode (legacy mode).

Maybe you can try some other things before giving up. Can you change the boot order (give USB higher priority than the internal drive) in a menu of the UEFI/BIOS system?

How did you make the USB pendrive bootable (method/tool)? Does it boot in UEFI mode in some other computer?

Edit: A brand new computer may need the newest possible Linux kernel with newest possible hardware support. So you should try with Ubuntu 21.10, that was released this month (October 2021).

---

### Post by WB0HYQ on 2021-10-30
I mentioned I'd burned 21.10 in Post #10. I did it to both a DVD and to the USB thumb drive. There is a problem with arranging the boot priority order. I can move DVD to the top, followed by UEFI Hard drive, then Windows Boot, but there is no option for USB boot. It just isn't there in the boot order list and to add it, there is an "Add" button, but when I click it, I'm given a "go-find-a-file" dialogue and no instructions as to where I might find it, or what to look for when I get there.

The USB drive does boot in all three of my laptops.

Bill

---

### Post by oldfred on 2021-10-30
You definitely need AHCI.
And you should first install the AHCI drivers into Windows or Windows will not boot.

Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

---

### Post by tea for one on 2021-10-30
> **WB0HYQ said:**
> I went out yesterday and bought an 8G thumb drive (supposedly for USB3) and burned the ISO to it. The USB port is there, and I can use it, but there doesn't seem to be any way to get the BIOS to give me that option on the F12 boot menu. Looks like Microsoft has finally locked their systems from being replaced. I'm not used to giving up, but this one has me whipped.

Isolate, de-activate or physically remove the Windows drive and try to boot into a live Ubuntu session using your USB/DVD.

Any joy?

---

### Post by WB0HYQ on 2021-10-30
> **tea for one said:**
> Isolate, de-activate or physically remove the Windows drive and try to boot into a live Ubuntu session using your USB/DVD.

Any joy?

The Windows drive is an SSD. Not willing to remove it as it is fastened to the MOBO.

Bill

---

### Post by WB0HYQ on 2021-10-30
> **oldfred said:**
> You definitely need AHCI.
And you should first install the AHCI drivers into Windows or Windows will not boot.

Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

I am rapidly coming to this conclusion. The BIOS on this machine is something to behold. It is, by far, the most confusing thing I've ever come across. After each and every change I make, I cringe when I click the Save and Exit button.

Thanks so much for the reading material. I'll get on it and see if I can make any headway at all. It isn't mission critical I get Ubuntu on this machine, but now it's messing with my mind and I can't let it go.I have a hard time believing that a manufacturer would lock in a given OS so thoroughly the machine cannot be booted into another OS by external means.

Bill

---

### Post by oldfred on 2021-10-30
Another alternative is an external SSD.
I find my old M.2 SSD drive converted to external with M.2 to USB adapter to be almost as fast as internal SSD. I wanted larger drive and M.2 on my system also supported NVMe, so updated to that for internal drive. 
While booting & loading large application is a bit faster with NVMe, I find the person between keyboard & chair to be getting even slower.

---

### Post by WB0HYQ on 2021-10-30
@OldFred: The third link you gave me may have the solution. According to the Canonical certification list, my Dell Inspiron is NOT listed. Two of the 3891s are, but not mine. Here's the identification string from Windows "About": 11th Gen Intel(R) Core(TM) i5-11400 @ 2.60GHz   2.59 GHz.

The two listed are Core-i7 and Core-i9.

The problem is getting a USB drive of ANY type to be recognized and allowed to boot. Heck, I even tried my drive from a working Ubuntu 21.10 computer by taking it out and plugging it into the only spare SATA slot on the MOBO. Still wouldn't boot.

Bill

---

### Post by oldfred on 2021-10-30
I would be surprised if specs on same model systems with different processors would be enough different to prevent Ubuntu install.

With very new hardware like yours, you have to use the very newest Ubuntu and even then may need newer kernel & drivers.
Dell is usually pretty good about releasing changes required for their systems so they can be included in new kernels & drivers. But time to get into kernel & then time for newest kernel to be in a distribution that is only released every 6 months may be a problem.

And UEFI systems often require various settings in UEFI and in Windows to work with Ubuntu.
And often both UEFI & SSD firmware have to be updated to latest version, even with new systems, some have updates.

---

### Post by tea for one on 2021-10-30
> **WB0HYQ said:**
> The Windows drive is an SSD. Not willing to remove it as it is fastened to the MOBO.

How is it attached?
On Desktop PCs, it is generally fairly easy to replace and upgrade SSD drives without too much effort? 

Alternatively, is there a UEFI setting to de-activate the SSD?

---

### Post by WB0HYQ on 2021-10-30
Looks to be attached on top of a small heat sink. There are two hex-headed screws holding it down. It's only about 1.5 inches square. At first, I thought it was the wireless or Bluetooth module, but that's sitting aside from the MOBO. There is a way in the BIOS to turn off the SSD, but once again I'm faced with a big warning it isn't advisable to do so.

There is a law of diminishing returns here. I'm expending way too much effort for something that I can live without as I have three laptops and two more desktops running either full Ubuntu or dual-boot with Win 7. Perhaps something will come along that fixes this, but I don't think it will be soon. The whole way this computer is set up is very odd indeed. Next time, I build my own.

Bill

---

### Post by WB0HYQ on 2021-10-30
I found this in the "[SIZE=2][FONT=sans-serif]Intel® Rapid Storage Technology [/FONT][FONT=sans-serif](Intel® RST) Release with Intel® [/FONT][FONT=sans-serif]Optane&#8482; Memory[/FONT][/SIZE]" PDF manual:

- - - - - - - - - -
[FONT=sans-serif]5.1.2.1[/FONT][FONT=sans-serif]SATA Controller Mode Switching to AHCI Mode [/FONT]
[FONT=sans-serif]Once the system is setup with Intel® Optane&#8482; Memory enabled, the user cannot [/FONT][FONT=sans-serif]switch the PCH SATA controller mode from one of the Intel® RST modes to the AHCI [/FONT][FONT=sans-serif]mode.  If the mode is switched and the user attempts to boot the system, the Intel® [/FONT][FONT=sans-serif]RST configuration metadata can be corrupted making the system unbootable when [/FONT][FONT=sans-serif]PCH SATA mode is switched backed to the available Intel® RST mode.

To avoid this [/FONT][FONT=sans-serif]error condition the following precautions should be taken: 
[/FONT]
[FONT=sans-serif]&#8226;[/FONT][FONT=sans-serif]All users: If you require switching the PCH SATA controller mode to AHCI for some [/FONT][FONT=sans-serif]reason, then before switching, disable Intel® Optane&#8482; Memory prior to switching [/FONT][FONT=sans-serif]the mode.  You can re-enable Intel® Optane&#8482; Memory once the controller is [/FONT][FONT=sans-serif]switched back to the supported Intel® Optane&#8482; mode.

- - - - - - - - - - - - -

The computer has 16G of RAM, but only 12G shows up in the About display, so this Optane thing must be enabled.

Bill

[/FONT]

---

### Post by WB0HYQ on 2021-10-31
I was once again on the phone to Dell this morning for an hour. It seems that my particular computer "fell between the cracks" as far as modifications go. This model was put together with year-end components and marketed as a simple "user" box. When I asked about AHCI again, I was told it cannot be changed on this computer as the Optane is "locked in" and the method of removal (setuprst.exe and setupoptanememory.exe - both from Dell) will NOT run on this computer as the chipset won't support it. When I specifically asked about installing Linux as even a dual-boot, he told me it wasn't possible as the linux applicaiton initramfs tries to find memory and cannot as Optane has locked it up. And, since I can't remove Optane, I'm neatly boxed in. Looks as if the $400 i spent on this went circling down the drain as far as Ubuntu is concerned. This could be a high grade of bologna, but it sure sounded true enough.

Nuts. At least I can continue using it for writing more novels.

Bill

---

### Post by sudodus on 2021-10-31
Next time you'll spend $400 on a refurbished enterprise class computer, and your chances to succeed with Ubuntu will be much better.

---

### Post by WB0HYQ on 2021-10-31
Yeah. To think that all this started because of a simple blown capacitor on my old MOBO in the old machine. When it went, it let all the smoke escape from the chips and they quit working. :rolleyes:

Bill

---

### Post by MAFoElffen on 2021-10-31
> **sudodus said:**
> Next time you'll spend $400 on a refurbished enterprise class computer, and your chances to succeed with Ubuntu will be much better.

Wait and back up a bit... I do Warranty Service Repair (Dell NDS) calls on these (I do Dell/Lenovo/HP)... No name calling.

One  option of this Desktop "came preinstalled" with Ubuntu 20.04 LTS... So  Dell has in no way abandoned Ubuntu, and has a long continued  relationship with...

On the BIOS defaults, when I have to change the system boards on these... 

[LIST]
[*]The BIOS is confirmed as UEFI only. 
[*]The  Secure Boot option default is off on these boards. But it also has  another BIOS option for "Secure Boot Mode", additional to the normal,  just enable/disable, which deals with how that is enforced, if  it is enabled... 
[*]The Boot order does not say DVD (Not a CD, but rather DVD drive) as an option. It says 'removable drive'. 
[*]The  peculiarity of the USB settings in this BIOS is that they can be  enabled/disabled as a group (front/back) and individually for each port... Make sure  they are 'all' enabled. This was a commercial/enterprize security option. 
[*]The Storage settings have 3 options (RAID/AHCI/None). Set to AHCI. If you only have one drive, I can guaranty it does not have RAID. (You don't know how many times I show up to a can't read HDD service call, and this is the only problem!) 
[*]The Storage Interface settings: Check all the boxes to enable them. If they are not really present, it won't matter. 
[/LIST]

On Diagnostics with my ePSA Technician Diagnostics USB Keys, I boot and press F12... On this BIOS, the USB key shows up in the boot menu automatically. That is how I would try to install Ubuntu. If it had come with Ubuntu pre-installed, that is the form of the OS Restore Media Dell would have provided.

What you didn't mention was the CPU and GPU this came with... If it "had" come pre-installed with Ubuntu, the OEM version of the install media would have the 3rd party drivers there for what was installed and connected in it's HW inventory by the Service Tag... Please provide the Service Tag Number, or tell us what those options are.

You are either 10th or 11th Gen Intel for CPU. Some options were x-xxxxF, which didn't have an APU Graphics in the CPU, and had other GPU options in the PCIe x16 slot... You can tell these easily, if it came with a black sticker over the I/O board's HDMI port when it cam new. (and if the owner didn't remove it. LOL) We are in the dark to recommend anything on booting options until we know the details on those.

Does yours have Intel Optane? I'm curious as this option, if you got this for at some kind of ridiculous price, that option was very very spendy all by itself... So if it does, you got a steal. You can boot Linux from Intel Optane persistant memory... Intel has many instructions for that... So people saying that is "a problem"... Well, they need to understand how that really works. It doesn't prevent Linux from installing or running. It is a challenge on how it reports the RAM memory's non-persistent and persistent total. It initially boots from the non-persistent RAM, then transfers to... once it finds it. There is still enough non-persistent RAM in RAM channel 0, slot 0 to boot, even so. Even at the lowest configuration option of that machine. Example: [https://itpeernetwork.intel.com/tuning-performance-intel-optane-ssds-linux-operating-systems/#gs.ejbeu1](https://itpeernetwork.intel.com/tuning-performance-intel-optane-ssds-linux-operating-systems/#gs.ejbeu1)

But yes... If you have Intel Optane, you cannot "dual-boot" easily because the cache would have persistence caching of the other OS within it... And then it gets confused. So it is a known limitation at this time. I'm thinking that what would have to be done is to turn off the persistent cache before switching to the other OS... And when switched off, use a not-connected to Optane partition to install to... Or like oldfred suggested, install another drive, internal or to external USB, that is not connect to or associated with Optane.

Going on, when you get to the Grub menu of 20.04, you should look for the HWE install option to install with the Hardware Enablement Stack, because of the newer hardware technologies.

---

### Post by WB0HYQ on 2021-10-31
@MAFoElffen: Was all this meant for me? if so, a lot of your questions have already been answered in this thread.

Bill

---

### Post by MAFoElffen on 2021-10-31
I read through it again...

11th Gen i5, Internal APU, Not just SSD, but rather NVMe. Optane limitations to it. Dang... LOL

Dual-boot (through not having to do many careful changes of enable/disable and not being convenient at all) would be limited to an External USB drive, like oldfred suggested.

-OR-

Do you have Windows Pro Edition?

---

### Post by WB0HYQ on 2021-10-31
Nope. Windows 10 Home. It lacks a bunch of very useful things my other machine (Windows 10 Pro) has.

EDIT: have to leave for a couple of hours. Be back then.

Bill

---

### Post by MAFoElffen on 2021-10-31
Dang.

If Home Edition, then open to you still is also installing/running VirtualBox or VMware Player, and installing as a VM Guest...

If it was Pro, then you would have had options to Hyper-V or WSL2 and extending that with hacks to 'extend' that to display an Ubuntu Desktop from within Windows.

Personally, an external USB drive is inexpensive and would be better performance than running as a VM.

The big precaution would be to make sure when you do install, is to make sure the pointer to install grub is to the external drive... Then just use the F12 key to get to the Boot Menu, to choose to boot that...

---

### Post by WB0HYQ on 2021-10-31
Ah, but there's the rub! There is NO F12 boot menu item for a USB drive. None at all no matter what I do in BIOS. If I plug one in, bootable that is, even then it is not recognized as a boot device. I can plug one in later, after the OS has loaded and it works just fine. Simply cannot boot from one. As I said earlier, I even took a working SATA drive out of another desktop and installed it in the only empty SATA slot. BIOS didn't even see it, yet the once-booted OS did. I couldn't do anything with it however because the entire disk was an Ubuntu-formatted disk. Disk manager could see it, but do nothing with it other than offer to format it.

Bill

---

### Post by WB0HYQ on 2021-10-31
I've installed VMWare on the computer and it is churning away creating a VHD on an external USB drive. I'm wondering why it will take a stated 3 hours to create a 200G drive though. That seems a bit excessive. I may end up installing a spare 1TB disk drive I have on the shelf and re-installing using it as it connects internally to the SATA port. Even though the external USB drive is USB3, three hours does seem quite long.


EDIT: I stopped that disk creation and installed a 2TB internal SATA drive. Now, to create a 400G VHD it only takes 23 minutes. Much better.


Bill

---

### Post by MAFoElffen on 2021-10-31
Deleted. Double post strangeness..

---

### Post by MAFoElffen on 2021-10-31
> **WB0HYQ said:**
> Ah, but there's the rub! There is NO F12 boot menu item for a USB drive. None at all no matter what I do in BIOS. If I plug one in, bootable that is, even then it is not recognized as a boot device. I can plug one in later, after the OS has loaded and it works just fine. Simply cannot boot from one. As I said earlier, I even took a working SATA drive out of another desktop and installed it in the only empty SATA slot. BIOS didn't even see it, yet the once-booted OS did. I couldn't do anything with it however because the entire disk was an Ubuntu-formatted disk. Disk manager could see it, but do nothing with it other than offer to format it.

Bill
Dang... Strange... Quote from the Dell Inspiron 3891 DSM:
> 
**Inspiron 3891    Service Manual**    

                                        [Inspiron 3891    Service Manual >]("https://www.dell.com/support/manuals/en-us/inspiron-3891-desktop/inspiron-3891-service-manual/inspiron-3891-service-manual?guid=guid-5b8de7b7-879f-45a4-88e0-732155904029&lang=en-us") [System setup]("https://www.dell.com/support/manuals/en-us/inspiron-3891-desktop/inspiron-3891-service-manual/system-setup?guid=guid-e4ecaec1-c84b-4228-b42a-b0494dd7a52d&lang=en-us") >[Updating the BIOS]("https://www.dell.com/support/manuals/en-us/inspiron-3891-desktop/inspiron-3891-service-manual/updating-the-bios?guid=guid-02b5a40c-5646-47ac-83a3-1ac8fb44d774&lang=en-us") > Updating the BIOS using the USB drive in Windows
                
                                                           **Updating the BIOS using the USB drive in Windows**

           **Steps**

[LIST=1]
[*]            Follow the procedure from step 1 to step 6 in               [Updating the BIOS in Windows]("https://www.dell.com/support/manuals/en-us/inspiron-3891-desktop/inspiron-3891-service-manual/updating-the-bios-in-windows?guid=guid-f5899359-c2e1-41c0-9663-4c79969506eb&lang=en-us") to download the latest BIOS setup program file. 
[*]            Create a bootable USB drive. For more information, see the knowledge base article               [000145519]("https://www.dell.com/support/kbdoc/000145519/") at               [www.dell.com/support]("https://www.dell.com/support"). 
[*]            Copy the BIOS setup program file to the bootable USB drive. 
[*]            Connect the bootable USB drive to the computer that needs the BIOS update. 
[*]            Restart the computer and press               **F12               **. 
[*]            Select the USB drive from the               **One Time Boot Menu**. 
[*]            Type the BIOS setup program filename and press               **Enter**.                        The               **BIOS Update Utility** appears. 
[*]            Follow the on-screen instructions to complete the BIOS update. 
[/LIST]

Hmmm. No matter now...

Glad that you found an acceptable way for you...

---

### Post by WB0HYQ on 2021-10-31
Well, after having my poor DVD drive clattering away for over two hours solid, I've finally managed to get Ubuntu 21.10 into the VMBox. It is running nicely in it's own little virtual window in it's own Win10 desktop number 5. I've used VMWare before, but quite some time ago. I'll have to get used to the screen commands. Too bad it won't allow a given USB drive to be attached to both the host and the VM at the same time. If I attach it to the VM, it can't be seen/used by the host. Bummer.

My deep thanks to everyone who helped in this thread. The old adage is true: when you buy a lemon, make lemonade from it. I wondered why Costco was deep-discounting them. Now I know.

Bill

---

### Post by MAFoElffen on 2021-11-03
Just an FYI post on Inspiron's to give you an additional idea on what might be faster option than what you have now.

... I had an upgrade service call yesterday morning on an Inspriron All-in-One, for memory and storage... where I upgraded the system from SATA+Optane to NVMe... The Customer was not aware that they needed to backup their data previous to the call... The old SATA was going to be left in as a storage drive.

During the process, because there was only 1 NVMe connector on the Inspiron model I did, the Optane gets removed, and the NVMe drive gets installed in it's place... And because the OS (Win10) was originally installed with the Optane present, then the BIOS Options changing to adapt for it's removal- the SATA mode changed from RAID mode to ACHI, the two Intel Security options for Optane disabled, ...and the SATA drive left in to be used for storage...

During the process, the Original OS install should have failed (become unreadable), and Windows would have to be reinstalled. Strange oddity, was that Windows 10 booted on the old drive. Not saying it should have at all. It should have failed, by all rights.

I had to re-partition that drive to get it to stop being used as the primary (making it unbootable) and to be used as a storage drive/secondary. Setting the NVMe drive as primary, with the old SATA being used as a secondary drive, made the system about 10-15 times faster... Since that system did not have a second NVMe slot, the Optane could not be used with the NVMe storage drive... (If it had, it could have been made even faster.)

Like I said, just an FYI post.

---

### Post by WB0HYQ on 2021-11-03
Now, that's interesting. The procedure sounds like a good solution, but far more than I would want to do for what is really a minor thing. The primary reason I wanted Ubuntu on this machine was for it to be more compatible with my three laptops I take with me on book signings and other trips. Running as it is on top of Win10 works quite well and serves the purpose nicely. The only drawback, if you can call it that, is the virtual machine can't "see" the host's video card (Nvidia gt710 - an old card, but with 4Gb of RAM), thus, I'm left with an emulated video with only 16M of RAM assigned. Still, you don't need much for writing apps.

Bill

---

