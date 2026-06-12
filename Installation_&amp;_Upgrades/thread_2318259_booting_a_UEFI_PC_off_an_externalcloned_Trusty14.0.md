---
title: "booting a UEFI PC off an external/cloned *Trusty/14.04* install for a BIOS-based PC"
date: 2016-03-24
forum: Installation &amp; Upgrades
---

### Post by rjvbertin on 2016-03-24
Hi,

My wife's venerable HP G62 laptop just died (no more display, not even over the VGA port) at the worst possible time, so we're looking at replacing it ASAP. One potential candidate is the ASUS P2 520LA-XO0456T , and I'd like to know what the odds are that I could boot it into the HP's Linux install. That's a Kubuntu 14.04, fully up to date with a home-built, mainstream 3.14.59 kernel and a few PPAs to get newer Qt and KDE4 versions.

The Asus is UEFI-based as I guess most newer hardware will be, while I only have Linux installations with GRUB bootloaders for BIOS. That includes the HP's internal disk which apparently is fine (and contains the single, btrfs Linux partition).

grub2 : 2.02~beta2-9ubuntu1.7
initramfs-tools-bin : 0.103ubuntu4.2
zfs-initramfs : 0.6.5.4-1~trusty

I know one needs to disable SecureBoot and FastBoot, typically. And then? Do PC UEFIs indeed/still contain a BIOS emulation mode? Or do I need to install addition grub components, copy them to /boot/grub, and rerun grub and/or update-initramfs? Should I do that from a UEFI-based PC (somehow) or can that be done simply from my good ole AO722 netbook which is currently the only physical Linux rig I have available?

Thanks!

---

### Post by oldfred on 2016-03-24
Unless you happened to use gpt partitioning and only had Ubuntu on drive, could you easily convert to UEFI boot.

Most current UEFI have CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Only a few lightweight systems were configured as UEFI Class 3 devices that were UEFI only. Those also were 32 bit UEFI to make it difficult to use Linux as when designed Linux did not have a 32 bit UEFI boot.

You should be able to boot a BIOS/MBR drive with your new system. Often video drivers and/or Wireless drivers are the major issues when changing. Also if very new hardware like Skylake Intel chip, you may need 16.04 to have it work or work well.

But I normally suggest new clean install and restore you data and/or /home from your normal backup.

More info on UEFI in link in my signature.

---

### Post by rjvbertin on 2016-03-24
Ah, of course, there's the GPT issue too. As far as that's concerned, any GPT-partitioned drives I have have been set up such that the BIOS PCs of the house can boot Linux off them. IIUC that means they have a sort of shadow MBR installed, somewhere.

Is the CSM activated automatically or does one have to go into the firmware settings for that? I guess I know the answer - your typical PC user wouldn't accept being unable to reuse his peripherals the way s/he used to, with a new machine ... but one best be sure :)

Anyway, my plan would be as follows, as that's how I got the Linux side onto the wife's laptop:
- create the additional partition entries on the internal disk, using either MS Windows utilities or something like the SystemRescueCD
- boot off an external containing the installation I'm planning to clone
- mount the target partition
- clone
- chroot to the clone, run the grub updater and installer (potentially first to a USB thumbdrive so as not to mess the original boot loader)
- reboot

If I were using a more or less standard install I'd probably spring for a clean install, possibly even of a newer Kubuntu version. But with all the tweaks I've accumulated (none of which ought to introduce hardware restrictions as long as I move to a more capable CPU) I expect to gain time with my method - potentially lots of time. And that's crucial here.

Anyway, we'll see soon enough when testing with an external disk. Depending on where we go shopping I might even be able to do that as part of a selection process. Given the budget in which we'll be looking (500&#8364; max) I'm kind of hoping we'll be choosing between machines using older components if not downright down-priced older models (the Asus I mentioned still uses a 1366x768 panel for instance, with an HD4000 GPU).

---

### Post by grahammechanical on 2016-03-24
As I understand it you are intending to take the drive from the broken laptop and connect it to the new laptop and then clone the drive. Interesting. I foresee one problem.

What video driver was that install of Kubuntu using? A proprietary video driver? Will you be purchasing a laptop with the same make of video adapter as the broken laptop? What will you do when you first load this cloned version of Kubuntu and get a broken OS because the video driver is incompatible with the video adapter?

My advice would be to first try and boot from that old drive and at the boot menu select Advance Options and then select recovery mode. At the recovery menu select Resume. If that gets to a working desktop change video drivers to the open source video driver.

In other words, see if you can get Kubuntu running from that old drive before you clone it. Back up the data. Otherwise, that time saving method might prove to be waste of time.

Regards

---

### Post by oldfred on 2016-03-24
You have to turn UEFI secure boot off. Then you should have the choice of UEFI or CSM/BIOS boot. You cannot use Secure boot with CSM.
But cloning to new system is not particularly easy.
You cannot clone from MBR to gpt, only rsync or cp -a all the data.

I use gparted to partition in advance and have high speed Internet. My install took 10 minutes. Updates & reconfiguration took a total of about an hour.
Most of you configurations are in /home, so backup & restore of /home should restore all your settings. And if you extract a list of installed applications, you can easily restore those.
When for backup you may need setting in /etc, but if new system most of those settings change. I do restore my custom 40_custom for my own grub configurations and my NFS settings, but that is about all.

You may need different video drivers, different Internet and/or Wi-FI drivers. You will have to reinstall grub, easier usually with Boot-Repair.
Also are hidden grub settings that specify which drive to reinstall grub into which will when cloned to a different drive will be wrong & need update. You also have to manually edit fstab with new UUIDs. Only if cloned is full drive may UUIDs also be copied.

I find new drive/new system as a great time to reorganize or house clean.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[URL="http://ubuntuforums.org/showthread.php?t=1883834"]http://ubuntuforums.org/showthread.php?t=1883834

[/URL]New install better, but how to migrate old to new 
[http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) [URL="http://ubuntuforums.org/showthread.php?t=1883834"]
[/URL]

---

### Post by sudodus on 2016-03-24
It is different with different UEFI/BIOS systems, some select automatically between UEFI and BIOS depending on what you try to boot, but I think most of them must be set manually in some menu.

Try live before starting to install anything, and let her decide if she wants to keep Windows. It is more complicated to install alongside Windows, but you should be able to do it. It is also worthwhile to ask here and browse the internet for* linux + {the brand name and model}* you intend to buy.

Would it be an option for you to buy a second-hand computer? If available where you live, a revamped enterprise class computer can give you more computer for the money. In my family we have such computers. It is often easier to make them work with linux too: the development of free software has adapted to them.

---

### Post by rjvbertin on 2016-03-25
[OT: does this forum support reopening an "old" link in a restarted browser session, log in as a result of clicking "reply", and then taking me back to this post rather than to the forum list page?!]

Anyway, thanks for your feedback.

- The HP was already used under Linux for more than a year. I don't think my wife ever got to really like it, but it worked and the same couldn't really be said about the Win7 install anymore no matter how much effort I put into cleaning and optimising it. It'll depend on Win10 whether the new rig will be used mainly under that or Linux (if supported).
- indeed, "cloning" to a new disk means using something like rsync (I have a nice little script that does that). I don't use the term in the sense of cloning a full disk.
- video drivers: I've already used (clones of) the same install to boot a netbook, the defunct HP and VMs running under VirtualBox and Parallels Desktop on my Mac. From what I understand that's possible because all those systems each have a single GPU with open-source drivers or at least drivers that don't require an Xorg.conf file.
- of course I'll have to edit certain files (if not only fstab) even if it's possible to transfer the current Linux install onto the replacement laptop, and evidently I'll have to update the grub config. I have a pretty good idea which files to adapt, much less how to recreate all customisations in a single session (and I'm really not fond of things like installing kernels).

About boot-repair : I had a quick look yesterday and couldn't figure out whether it has a mode in which it shows exactly what it'll do before doing it. That's all the more important when you're running after booting from an external that shouldn't be touched and chroot'ing into an "internal" install that is the target. I could check if it's included on the current SystemRescueCD though.

We seem to be homing in on another HP, a W10 15-something model, with an AMD R5 M330 GPU and either with an AMD A8 (7410) CPU or an Intel i5 with an additional embedded HD5500 GPU that's 100&#8364; more and a bit over budget). The A8 model comes with 6Gb of RAM, the i5 with only 4Gb. I'm rather certain that both CPUs are largely up to an task my wife will be throwing at them for the years to come. I guess it's going to boil down to how well (or not) the R5 GPU is supported under Linux, how much extra complications an additional embedded GPU will cause.

Another thought, nothing to do with Linux: we've now had to replace 2 laptops because of failing graphics (internal and via the external monitor link), the HP and my old Mac Powerbook G4 (both with discrete ATI/AMD graphics boards). What are the odds that an additional embedded GPU will function as a fallback in that kind of scenario?

It'll be a good idea though to throw in an extra thumb drive or two when we go shopping tomorrow. It's been a few years since I created a liveUSB drive; is it possible to dedicate only part of such a drive for that purpose (i.e. partition it) or should I just get the smallest model that will hold a typical ISO (2Gb)?

---

### Post by sudodus on 2016-03-25
> **rjvbertin said:**
> ...
We seem to be homing in on another HP, a W10 15-something model, with an AMD R5 M330 GPU and either with an AMD A8 (7410) CPU or an Intel i5 with an additional embedded HD5500 GPU that's 100€ more and a bit over budget). The A8 model comes with 6Gb of RAM, the i5 with only 4Gb. I'm rather certain that both CPUs are largely up to an task my wife will be throwing at them for the years to come. I guess it's going to boil down to how well (or not) the R5 GPU is supported under Linux, how much extra complications an additional embedded GPU will cause.

I know Intel graphics and nvidia graphics better than AMD/ATI/Radeon graphics, but other people can help you.

Generally, graphics chip models that are not brand new, but maybe a year or two old are better supported in linux.
> 
Another thought, nothing to do with Linux: we've now had to replace 2 laptops because of failing graphics (internal and via the external monitor link), the HP and my old Mac Powerbook G4 (both with discrete ATI/AMD graphics boards). What are the odds that an additional embedded GPU will function as a fallback in that kind of scenario?

Try it live (run the computer without the graphics card and connect the monitor to the built-in graphics).
> 
It'll be a good idea though to throw in an extra thumb drive or two when we go shopping tomorrow. It's been a few years since I created a liveUSB drive; is it possible to dedicate only part of such a drive for that purpose (i.e. partition it) or should I just get the smallest model that will hold a typical ISO (2Gb)?

Yes, it is a good idea. See the following links and links from them:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You can create a persistent live drive with mkusb (and part of the pendrive can be used to store or transfer files).

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Otherwise any [2GB or larger] pendrive will be fine for a live-only system. You can use mkusb to wipe the pendrive afterwards and restore it into a storage device.

---

### Post by oldfred on 2016-03-25
I keep both a Windows repair flash drive and my Ubuntu installer flash drive.
With my older BIOS install I had both on one flash drive, but not exactly easy to configure.

You can partition flash drive. Do get USB3 flash drives. New system will have USB3 ports and run reasonably fast with USB3.
If you only want UEFI boot, not BIOS from flash drive.
       UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
The FAT32 partition can be any size large enough to be installer or 2GB, but Windows only sees first partition on USB flash drives. Not sure if still true with Windows 10.
I also have full installs and boot ISO from flash drives.

HP, along with many others now, has not been friendly with Linux. It violates UEFI spec and uses description as part of UEFI boot and of course only valid description is "Windows Boot Manager". But we have many work arounds for these type of systems.

---

### Post by rjvbertin on 2016-04-02
Curious I never saw an alert for that latest reply.

Either way, the trigger was pulled on a bigger beast. Still an HP, a Pavillon W10 17" with a 6th gen i3 @2.3Ghz, 6Gb of RAM, and an AMD R7 GPU in addition to the i3's HD520. Despite being an i3 it's about as fast as the 2.7Ghz i7 from 2011 in my MacBook Pro. And in a nice deviation from HP's reputation (and our experience with the defunct G62) it remains perfectly cool to the touch (I saw 27 deg C. after streaming some flash video on the CPU under Linux).

Anyway, it took me a while to figure out how to get into the BIOS (they still call it that way), and activate the legacy mode (only possible when deactivating Secure Boot, which suits me fine). I haven't yet figured out exactly what the new entries in the boot order menus mean (2, one for legacy and "sexy" mode) so I'm using the Esc-F9 path to bring up the boot device selector for now. I did push down the internal HD's priority in the legacy boot order menu.

With that, the disk from the dead laptop (now in an USB3 enclosure) boots the PC into Linux just fine. Booting Win7 off that disk appears to be a no-go, unsurprisingly, but who cares.

I had to install the linux-*-lts-xenial packages to obtain the required drivers, as well as the bcmwl-kernel-source package for the BCM43142 board (used the generic kernel, did all that running in a VM under Win10). That means I can no longer use Paragon's free ufsd driver for native access to ntfs but that's not an issue for the time being; the (new?) ntfs driver in the 4.4 kernel appears to do well enough.

The only remaining issue is with graphics. The system goes for the R7 by default, which would make sense if it were supported more fully. For simple desktop work everything's OK, but there is no hardware acceleration at all so even scrolling doesn't work as well as it should. I haven't yet figured out exactly which driver is being used; I only identified the amdgpu kext.
I tried to putting "blacklist amdgpu" in a dedicated file under /etc/modprobe.d . That doesn't stop it from being loaded somehow, but at least lspci -v shows more information about the R7 device. Still, I'd like to test the HD520 adapter, which I presume is behind the "Sky Lake Graphics" device for which a "something915" driver (can't remember the exact name).
How would I achieve this if I don't know what to block for the Radeon GPU or how? I'd prefer not to use an Xorg.conf file so that I can keep booting other (virtual) machines off the same drive.

---

### Post by oldfred on 2016-04-02
Better to start a new thread on video issue of Intel & AMD.
I do not know AMD, but with Skylake video boot parameter may be required.
Can you turn on/off video in UEFI settings?

       Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)
Xubuntu 14.04 - GRUB2 nomodeset brings wrong screen resolution - Acer TravelMate 4740 with Intel HD Graphics
[URL="http://ubuntuforums.org/showthread.php?t=2240620"]http://ubuntuforums.org/showthread.php?t=2240620

[/URL]You add skylake or other boot parameters like adding nomodeset which is often required for nVidia or AMD until proprietary drivers are installed. But some AMD can only use open source driver.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710) 

Laptops sometimes need added boot parameters also. My new Skylake SFF desktop with 16.04 just works with Intel video.

UEFI from a vendor is often very similar across models:
      
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681) 
     HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[       ]("http://ubuntuforums.org/showthread.php?t=2240620") 16.04
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu 
    [ ]("http://ubuntuforums.org/showthread.php?t=2240620")

---

### Post by rjvbertin on 2016-04-02
[FONT=system]Wow, lots of links and info - I'll process all that in due time (for some silly reason I don't have access to this, my wife's, laptop when she's home ;)).
Good suggestion to create a new thread, too.[/FONT]

---

