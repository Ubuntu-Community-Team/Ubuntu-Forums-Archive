---
title: "Install Ubuntu 12.04 LTS alongside Windows 8.0/8.1 in UEFI mode (Asus R501VB-S3116D)"
date: 2013-12-10
forum: Installation &amp; Upgrades
---

### Post by paul.catinean on 2013-12-10
Good day community,

I am having severe issues with installing ubuntu alongside windows in uefi

When I received the notebook at first I installed windows 8 and then ubuntu in both cases using usb-stick and the option "Install ubuntu alongside windows" appeared.I did that and through the help of the community I managed to use the boot repair (because grub was not starting it was booting straight into windows) but I had two entries in grub for windows which unerved me and formatted once again

This time I have no idea what I've done (maybe it was the windows firmware update, maybe it was switching boot priorities, maybe it was booting in uefi one install and regular the other, maybe it was creating the usb stick with a difference partition).But now whatever I do an no matter how many times I erase and repartition the drive I never get the "Install Ubuntu alongside windows" option

The latest achievement I have managed is to use the esc key on boot to choose the boot option and pick the stick in uefi mode for both installations (that way when you pick "something else", in ubuntu install it sees the partitions otherwise I get only free space)

I have in the end installed manually by creating a swap area of 4 gb and installing ubuntu on the rest of the space but after boot repair I get many options and wierd names to boot windows and all that and furthermore (Don't know if it is related I get some nasty freezez in ubuntu while browsing and I can't do anything except shutdown by pressing the power key)

I am a medium linux user, not extremly technical but pretty good enough to understand and research

Could anyone please provide a step-by-step on how this should be approached from making the usb stick with windows to installing ubuntu properly alongside it so they work in harmony, grub boots safely and I have no nasty by-products

Many thanks for anyone taking time into this, much appreciated!

---

### Post by fantab on 2013-12-10
Do you now have both, windows and Ubuntu booting?
Post the output of the following from either Ubuntu on HDD or use Live USB:
```
sudo parted -l
```

Do you want to re-install both Win and Ubu or just Ubu?
Or
Do you want to remove the unwanted entries from the boot-menu?

You say, "I installed windows 8", do you have a Windows Install Disc? 
Did you yourself created the Windows partitions before installing it, or did you use the existing partitions? Or was it the Windows installer which did the partitioning for you?
Is there a SSD device in the picture? If yes, did you put in yourself or did it come pre-loaded with the laptop?
More info about your notebook will be helpful, like Graphics card, RAM CPU etc.

---

### Post by paul.catinean on 2013-12-10
Hello fantab and thank you very much for helping out, I appreciate it tremendously

1. I can/want to re-install everything from scratch win/ubuntu (I've done so 20 times, 1 more shouldn't be a problem)
2. I have a windows usb stick that I've made myself using Rufus and installed/install windows from that usb stick
3. I ALWAYS used the windows setup to partition to hard-drive this way (50gb for windows C where the setup has created the reserved space and other stuff, 500gb for D, and the rest 16x free space to ubuntu setup to identify and use itself)
4. So far there is no SSD drive in the picture just this only hard-drive though in the near future (1 month max) I would like to use a ssd and a caddy (but this is not the present case) - curious what would change there

Notebook info:
Link where I bought it from with all the specs:
1. [http://www.oktal.ro/laptop/asus-r501vb-s3116d+ivy+bridge+i7-3630qm+4gb+750gb+nvidia+geforce+gt+740m+2gb+freedos-o112490.html](http://www.oktal.ro/laptop/asus-r501vb-s3116d+ivy+bridge+i7-3630qm+4gb+750gb+nvidia+geforce+gt+740m+2gb+freedos-o112490.html)
2. HDD : Toshiba MQ01ABDO75
3. CD-ROM: MATSHITA DVD-RAM UJ8E1
4. BIOS info:
- BIOS Vendor: American Megatrends
- Version: 202
- VBIOS Version: 2124.I14N560.005
- EC Version 203E120001
- Does not include options like (Enable/Disable UEFI/Secure boot/ Intel smth (same as secure boot)) but I do have options to boot devices (hdd, cd-rom, stick in UEFI mode or standard using priorities and boot menu)
- When ubuntu stick boots it says "Safe Boot not enabled" and a few tests done through windows console determined the same thing

I can help with any further information by running shell commands or other software just say the word

Many thanks once more fantab!

---

### Post by fantab on 2013-12-10
Then re-install Windows8. Make it a 'Clean Install', meaning you will delete all partitions and start over with 'unallocated space'.
If you need help: [http://pcsupport.about.com/od/windows-8/ss/windows-8-clean-install-part-1.htm](http://pcsupport.about.com/od/windows-8/ss/windows-8-clean-install-part-1.htm)
Make Windows C: partition about 70Gb... windows does get bloated when start installing other software. It is an excellent idea to have atleat 30% of free space at any given time on C: partition.

Ubuntu 13.10 supports newer hardware better than 12.04 IMO. So you can opt to download and burn 13.10 Ubuntu to the USB...

1. Boot your Ubuntu-usb in **UEFI mode only**: [https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode)
2. "Try Ubuntu Without installing"
If you load to a black screen after selecting the above option then use '[**nomodeset**]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option to boot in a 'failsafe grafix' mode. This is a temporary fix, and after installing we have to install proper graphics drivers.
3. Open Gparted. We'll partition for Ubuntu manually.

I suggest the following partition scheme:
20Gb ext4 Ubuntu '/' (mountpoint='/', is where the installer will install ubuntu filesystem... its like Win C: 
20Gb ext4 Free (in case later you want to try another distro or another Ubuntu flavor or version. I have 4 operating systems on my desktop... you can have more 'Free ext4 partitons if you like)
4Gb SWAP
???Gb ext4 Linux only Data partition, either simple or /home. (to keep data separated from system '/' partition. If you plan on using more distros then don't use '/home')

ubuntu can read/write to NTFS partition. So your D: partition can be used as a shared partition between Windows and Ubuntu. Whichever OS you use more allocate more space to its data partition.

Apply changes in Gparted and close it.

4. Establish connection to internet.

5. Install ubuntu from desktop.

6. At the 'Installation Type' dialog, choose "Something Else".
At the next dialog select the first 20Gb partition and click "Change". Setup the partition with "*Use As* = Ext4 journaling system", "*mountpoint* = /", and check to '*format*'.
If you have opted to have '/home' then select the data partiton and set it up with "*Use as* = Ext4", "*mountpoint* = /home" and check to '*format*'.
Swap partition will be recognized by installer. No need to do anything more about it.
Thats it.

7. Continue with installation.

If you run into any issue with booting either Windows or Ubuntu then use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). '*Recommended Repair*' should suffice.

There is tool, called '[efibootmgr]("http://manpages.ubuntu.com/manpages/gutsy/man8/efibootmgr.8.html")' which can clean up EFI partition of obsolete/unwanted boot entries. 
How to use 'efibootmgr': [http://alllinuxstuff.blogspot.in/2013/06/how-to-remove-linux-mint-or-ubuntu-from.html](http://alllinuxstuff.blogspot.in/2013/06/how-to-remove-linux-mint-or-ubuntu-from.html)
Sometimes there will be two entries for Windows in boot-menu and they both seem to boot the OS, this is because Windows appears to keep its boot file in two different partitions.
Both entries will boot Windows, but one will boot slower than the other... just make a note of the faster option and use it... No need to remove the other entry.

More Info:
[Some OEM's add SSD as a 'cacheing' device, and in doing so use 'hybrid RAID', which cause issues when installing Linux OS].
UEFI is relatively new, and different OEM's are implementing it differently, inspite of there being a standard. That is causing some issues. 

Good Luck...

---

### Post by paul.catinean on 2013-12-10
I will get to it as soon as possible. Isn't the option of disabling UEFI (if possible) easier and would remove all these problems?

---

### Post by fantab on 2013-12-10
No. UEFI is the present and future. And it is better when communicating with the newer hardware. [More Reading]("http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement").
Don't disable UEFI....

---

### Post by oldfred on 2013-12-10
How you boot install media for both Ubuntu & Windows is how it installs. So you want to boot in UEFI mode.
Also with Windows 8 you need to turn off the always on hibernation or fast boot.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot-Repair may offer to rename files for "buggy" UEFI. Do not run that unless you cannot boot the ubuntu entry from UEFI menu. And it sometimes takes several trys before you know for sure. Older versions of Ubuntu/grub2's os-prober do not create correct UEFI boot entries for Windows, so Boot-Repair adds those. Very newest Ubuntu has the version of grub2 with the fix for that bug and then Boot-Repairs entries are not really required unless you have to run the rename function.

---

### Post by paul.catinean on 2013-12-10
Again, I can't thank you guys enough for the help you provide

Some feedback:

@oldfred

I have install both windows and ubuntu in uefi mode (figured it out myself 4-5 formats ago) by using UEFI: device in the boot manager (also windows creates some restore partitions in UEFI mode only

I have forgot only this time to turn of the fast boot in windows, but now I did (though it was on when I was installing ubuntu if that has any relevance)

@fantab

When I boot the USB stick in UEFI mode just before I have the panel to choose between "Try Ubuntu / Install / System settings" there is a VERY short message that I can barely read, something like "Cannot read...uefi / efi smth...".

I assume this is the reason why ubuntu fails to see the windows OS installed if not I would really like to know the reason because the same notebook just yesterday trying to install from usb sticks HAD the install ubuntu alongside windows option but now it doesn't appear anymore, I have no idea what I have changed...

Then I ran the live-cd (usb stick) and used gparted (hopefully) as you instructed me:
[http://s29.postimg.org/okadezth2/Ubuntu_gparted.jpg](http://s29.postimg.org/okadezth2/Ubuntu_gparted.jpg)
[http://s21.postimg.org/4zfmvx6gm/ubuntu_install.jpg](http://s21.postimg.org/4zfmvx6gm/ubuntu_install.jpg)

After the install has finished I restarted and grub presents nicely for the first time without any additional work (could be a byproduct of using ubuntu 13 instead of 12.04) having options:
- Ubuntu
- Advanced options for Ubuntu
- Windows Boot Manager (UEFI on /dev/sda2)
- System setup

Everything works nice except going into ubuntu just freezez at the dark purple screen
And going into Advanced options for Ubuntu and picking a (recovery mode) version shows:
Loading Linux 3.11.0-14 generic ...
Loading initial ramdisk ...

And it freezes as well

What would be the next step?

Ran boot-repair:
[http://paste.ubuntu.com/6552319](http://paste.ubuntu.com/6552319)

Picked the first option...same behaviour

---

### Post by oldfred on 2013-12-10
It looks like a good install. Do not run Boot-Repairs auto fix or "buggy" UEFI if you can boot to grub menu from UEFI menu, which it sounds like you can.

The recovery mode uses nomodeset by default, which usually works.
You show the Intel video is your driver. Line 904
       Kernel driver in use: i915
    There is only the one open source driver for Intel and it usually works, but new ones seem to need boot parameters.

I have in my notes one other boot parameter for a different Asus. Not sure if just this or in addition to Intel parameters or just Intel. Or you have to experiment for your system.
 Some Asus need this boot parameter:
 pci=nomsi

I have seen all of these alternative boot parameters for Intel but only a few say any work. One user tried all of them at once and that of course did not work.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Instead of nomodeset try each of these. Also remove the quiet splash settings and see if it reports any errors. It often stops at a battery setting but it is the posted entries before that that should have an error.
At grub menu, use e for edit, scroll to linux line and replace quiet splash with each of these to see if any work.

      Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

---

### Post by paul.catinean on 2013-12-10
I have ran boot repair and I assume there is no easy way to "revert" to the state just before I installed Ubuntu and ran the bootloader is there? So I could just delete the Ubuntu partitions and start fresh?

I have to reinstall everything don't I?

---

### Post by paul.catinean on 2013-12-10
I have ran boot repair and I assume there is no easy way to "revert" to the state just before I installed Ubuntu and ran the bootloader is there? So I could just delete the Ubuntu partitions and start fresh?

 I have to reinstall everything don't I?

[UPDATE]

Also I have managed to make a snapshot of the message when booting stick in UEFI it's:

"Could not open "\EFI\BOOT\fallback.efi": 14

Also, when making the usb stick with win in rufus what should I pick: 
1. MBR partition scheme for BIOS / UEFI computers
2. MBR partition scheme for UEFI computers
3. GPT partition scheme for UEFI computers

Also the link [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) says that when installing Ubuntu in uefi mode alongside windows (that was installed in uefi):

"nothing special is required if you use the automatic installer of Ubuntu ("Install Ubuntu alongside others"
why doesn't it get detected here?

---

### Post by paul.catinean on 2013-12-10
I have marked this question as resolved because I formatted once more as fantab suggested only this time when botting into safe mode after a bit of patience it fully went in.Did an update and now it boots every time.I would like to thank you all for the tremendous support you gave and getting me here. (Hope nothing bad happens soon)

A few questions remain:
1. Why did the ubuntu installer never detected windows operating system that was installed before it (both in uefi and non-uefi)
2. Why did it work the very first time I formatted the notebook (indicating that it is possible for the ubuntu installer to see windows in some configuration)
3. Why did 12.04 not work and/or required boot repair to get it going and in the end having some duplicate entries and other stuff not the clean grub I got with 13.10
4. What happens if something breaks now and I have to format ubuntu once more? I need to delete windows as well?

This and a few others still remain a mistery, a lot of material to read and explanations are greatly appreciated!

Thanks again guys!

---

### Post by fantab on 2013-12-10
> **paul.catinean said:**
> I have marked this question as resolved because I formatted once more as fantab suggested only this time when botting into safe mode after a bit of patience it fully went in.Did an update and now it boots every time.I would like to thank you all for the tremendous support you gave and getting me here. (Hope nothing bad happens soon)

A few questions remain:
1. Why did the ubuntu installer never detected windows operating system that was installed before it (both in uefi and non-uefi)[COLOR=#006400][/COLOR]
2. Why did it work the very first time I formatted the notebook (indicating that it is possible for the ubuntu installer to see windows in some configuration)
3. Why did 12.04 not work and/or required boot repair to get it going and in the end having some duplicate entries and other stuff not the clean grub I got with 13.10
4. What happens if something breaks now and I have to format ubuntu once more? I need to delete windows as well?

This and a few others still remain a mistery, a lot of material to read and explanations are greatly appreciated!


I am glad that you have a working install. 

To answer your questions: I am not really sure why Ubuntu installer does not detect the Windows OS. This generally happens when Windows is 'hibernating' and not really 'Shutdown'. If using Win8 then 'FastStarup' needs to be disabled. 
Or if there are any filesystem errors on the NTFS partition or the HDD itself. 
Since OEM's are NOT implementing the 'Standard' UEFI, like they are supposed to, Ubuntu's installer has to learn and adapt to every new UEFI configuration. Hopefully this improves in future, both at OEM side and the installer's side.

12.04 is nearly two years old now. When it was released we coud not install Ubuntu along with Windows8 if the 'Secureboot' feature was enabled in Win8. We had to disable it. Only the later upgrades to 12.04 added the support for 'Secureboot' and newer Hardware.
13.10, on the other hand, being latest, offers better support for UEFI environment and newer hardware. 
'Boot-Repair' too needs some improvement... 

Make a 'System Repair Disc' for Windows. If something breaks, try to fix it. Ubuntu 14.04LTS will hopefully release in April 2014, until then try to run the same 13.10 without reinstalling, as long as possible. Then you can later install 14.04.
You will learn a lot. Once you come to know your computer then things will be lot easier for you. 

I don't think your install will break, but if it does then this forum is good place to find fixes and solutions.

Good Luck...

---

### Post by paul.catinean on 2013-12-11
I still can't believe I have a dual boot with no issues...clean grub, two stable os's and everything running smoothly. Thank you very much! I will keep reading!

---

### Post by oldfred on 2013-12-11
Glad you got it working. :)

We are seeing Windows updates reset Windows to boot first. But it is not like BIOS with MBR where the boot loader is overwritten. With UEFI all boot loaders exist in efi partition, so all you then have to do is go back into UEFI and set Ubuntu as first entry again.

As always good backups and a current version of every operating sytem's repair CD or flash drive are good to have. Your Ubuntu live install then can be the repair flash drive for Ubuntu if ever needed.

---

