---
title: "Ubuntu 14.04 Cannot Boot from SSD"
date: 2015-09-15
forum: Installation &amp; Upgrades
---

### Post by Stephen_Le on 2015-09-15
I have been trying for about 3 days now with progressive levels of luck. However, I am now stuck on the only thing I wanted to do - the Ubuntu boot/install.


I can run from my LiveUSB fine, but every time I go to boot from the SSD (Sandisk 256GB), it doesn't take, so it boots over to the flash drive.


I've erased/reinstalled several times now. I even tried "making" my own partitions (though, to be honest, I had no idea what I was doing). To be clear, this is a fresh install - Ubuntu is the only thing running on this system.


Does anyone have any insight? My boot-repair log is at **paste.ubuntu.com/12417947**


Please let me know if you need any information about my system.

---

### Post by ubfan1 on 2015-09-15
What happens when you remove the flash drive?  What error messages?  Are you sure the SSD is before the flash drive in the boot order?

---

### Post by Stephen_Le on 2015-09-15
When I remove the flash drive , literally nothing happens. I've waited about 10 minutes before and even the drivers won't load. 

The boot order for my Mobo is drivers, then ports. So my impression is that it may not be detecting the right settings to boot.

---

### Post by oldfred on 2015-09-15
What brand/model system? Some are hard coded to only boot an entry that says "Windows". But we then change ubuntu to Windows description in UEFI , but still boot grub in UEFI.

What video card? It could be booting thru grub, but then video not working?

If you press (maybe several times) escape key after UEFI/BIOS but before grub (hard to tell) you should get grub menu.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Stephen_Le on 2015-09-15
I'm using a system I built. THe Mobo is a GA-H97N-WIFI by Gigabyte. I actually don't have the video card installed and the PC doesn't even enter a BIOS stage anymore.

[COLOR=#000000]I just generated a new boot-repair file at [/COLOR][B]paste.ubuntu.com/12418800


[/B]It should also be noted that I have tried the "erase/install" process several times.

When I go into "gparted", I notice that my drive in question says it isn't mounted, but that the boot flag is active on the ext4 partition. COmparing to the flash drive, it is mounted at /cdrom and also has a boot flag. Could this help anyone with debugging?

---

### Post by Stephen_Le on 2015-09-15
I just generated a new boot-repair file at [COLOR=#000000] [/COLOR]**paste.ubuntu.com/12418536**

---

### Post by oldfred on 2015-09-15
Please post full link, so clickable.
[http://paste.ubuntu.com/12418536/](http://paste.ubuntu.com/12418536/)
You have UEFI hardware, but install is now BIOS boot from MBR(msdos) partitioned drive.
You should not install grub to PBR - partition boot sector as it cannot be used unless you have another install with grub to chain to it. Only install the MBR.

With BIOS mode you must turn off all UEFI settings in UEFI/BIOS and only boot with CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Grub does not use boot flag. Windows has to have boot flag for BIOS boot.

And UEFI when using gparted uses boot flag to know where the efi boot files are. With UEFI it really is a very long GUID and gparted just uses boot flag as short cut to add GUID. 
Another partition tool gdisk uses a code ef00 to assign the correct GUID for the ESP -  efi system partition.

Gigabyte needs the IOMMU setting and usually the GRUB_CMDLINE_LINUX="iommu=soft"

     Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

 You need to review UEFI settings for your Gigabyte board.
With my Asus motherboard, I had to make many changes in UEFI to get it to correctly boot in UEFI mode. I turned off fast boot from cold boot, set warm boot to 3 sec delay on fast boot so I had time to get into UEFI if needed. I had to set to UEFI only boot on USB ports, no overclock on anything, updated UEFI/BIOS from vendor, and many others.

You can use gpt partitioning and boot in either UEFI or BIOS boot mode. Windows only boots from gpt with UEFI.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Stephen_Le on 2015-09-15
A small problem, though, is that I'm not able to get into the BIOS. When I boot up, there's a long delay, and I just catch the tail end of the LiveUSB menu. I'm currently resetting the CMOS and removing the drives to see if I can get into the BIOS and try at least one of these things, but that has been a consistent condition: every time I've "installed" Ubuntu on here, the BIOS ends up getting skipped (or, it displays much too quickly for me or the monitor to react).

EDIT:
I don't have any IOMMU options on my mobo.

---

### Post by oldfred on 2015-09-15
That is why is it important to turn off fast boot in UEFI, or if you have a setting to put some delay on it.
Some can reset to give some time to press key, if you do a total cold boot and hold power switch down for 10 sec. For those with laptops they must also remove battery.
If that does not work then you may have to jumper reset pins on motherboard and/or remove motherboard coin battery. That may totally reset system, so you will have to go into UEFI and make all the changes you made before.

Both Windows & Ubuntu have ways to get to UEFI from system. Grub often adds this:

```
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}

```

But with one install you will not get grub menu by default and have to press & hold shift key if in BIOS mode. If in UEFI mode press (repeatedly) the escape key.

---

### Post by Stephen_Le on 2015-09-15
So I'm in the BIOS now, but I don't see any IOMMU options, so I can't follow the procedures you posted earlier. To recap this is what I have:

LiveUSB (works to install and run "try Linux")
SSD with Linux (supposedly) installed to it
No graphics card plugged in
No additional devices present

Is there anything I should verify? Am I missing anything?

---

### Post by oldfred on 2015-09-15
What CPU? Some Intel chips also need to have a boot parameter.

But reviewing manual I am confused.
It makes sense that "otherOS" is default.
But then says you must be in "Windows 8 " features for CSM or UEFI selection. It may mean you can only have UEFI boot with Windows 8 setting. Which should work with Ubuntu as Ubuntu uses the same security and signing process.

Since you have installed in Legacy mode have you set boot to legacy only?

(from page 48 of your manual).

---

### Post by Stephen_Le on 2015-09-15
I actually have no idea how I installed in Legacy or UEFI, but I initially had everything set to UEFI and then switched everything over to Legacy when I noticed this, but still to no avail. I just tried switching everything to Legacy (or at least Legacy first) and it still isn't booting into the drive.

I'm confused by your first point - so what settings should I be set to? I would have thought the "OtherOS" and "UEFI and Legacy" would have worked.

On a side note, I've actually done the install process a lot of times - it says that the names I've previously tried using are "still on the network" How can I clear these (unused) names? (Just thought I'd ask; ignore if I can probably find the answer somewhere)

---

### Post by oldfred on 2015-09-15
Buried in the link in my signature.
I think you have to boot in UEFI mode.
              
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

I wanted UEFI boot and with my Asus motherboard, could only get it to boot installer in UEFI mode with UEFI only, not even UEFI first. But every motherboard's implementation of the UEFI "standard" is different.

---

### Post by Stephen_Le on 2015-09-15
Weird problem - I just tried your command (using my LiveUSB), and it says the command was not found for "sudo efibootmgr -v"

edit:

Duh, had to install it. But when I type:
sudo su
modprobe efivars
It still doesn't execute the command you originally gave me.
Looking at other forums around, it seems that the problem could stem from my device (the flash drive) not even being UEFI to begin with. How do I make it bootable in UEFI so I can try this whole process again from the top? I don't recall seeing non-UEFI or Legacy options when downloading and such.

The USB is 8GB and I was using x64 .iso + Universal USB installer to make the drive bootable. Thanks in advance.

---

### Post by oldfred on 2015-09-15
Installer is both UEFI and BIOS, but it is how you boot from from UEFI menu on how it then installs. And with my system I could only boot in UEFI mode with "UEFI only". Others have had to specifically allow or turn on USB ports for booting.

I always partition in advance with gparted. But you have to change to gpt partitioning first. 
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

My partitioning just posted in this thread.

  [http://ubuntuforums.org/showthread.php?t=2294472&p=13356594#post13356594](http://ubuntuforums.org/showthread.php?t=2294472&p=13356594#post13356594)

---

### Post by Stephen_Le on 2015-09-15
Alright Fred, so what I'm going to do is this:

Get new installer, just to be on the safe side.
Go directly into the BIOS of my board and force everything into UEFI
Install using the new drive
Try and boot from SSD

EDIT:
Went back to try the efibootmgr. It's listing only a single boot entry, but the problem is that I have no idea whether it's the flash drive or the SSD (both are by SanDisk).

EDIT2:
Ran again using a different USB stick. efibootmgr is only detecting the flash drive. How do I add the SSD? And I looked at your partitioning,  what do I format to for the ones that are blank?

---

### Post by oldfred on 2015-09-15
Did you use the Something Else install option and choose the partition you planned for root as /? I do not use separate /home, but have /mnt/data where all the normal folders in /home really are. They then are linked back into /home folder in /.

Skip the Winodws parts:
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
      
 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/](http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/)
Something Else install, but prefer larger / of 20 or 25GB. Not showing Windows
[http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/](http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/)

If you still have issues post link to summary report from Boot-Repair.
       
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Stephen_Le on 2015-09-16
I tried a weird combination of the self-partitioning (I went with the partitioning scheme of [http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/](http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/)) amd the other one that told me to boot-repair. Still can't boot.

Boot-repair is at [http://paste.ubuntu.com/12427050](http://paste.ubuntu.com/12427050)

---

### Post by oldfred on 2015-09-16
With only Ubuntu installed you do not see grub menu. With UEFI you have to press escape key often several times after BIOS but before grub. ( can be a bit tricky). Even with my 3 sec delay I often have to try a couple of times. (if BIOS boot it is shift key and you hold it.)

And you need grub menu to add boot parameter(s). 
Is monitor plugged into Intel video from motherboard or nVidia from nVidia 750?
The 750 was the first Maxwell and the entire Maxwell family does not work with the open source driver or does not work well. You need the nVidia driver. The newest from Ubuntu should work, but you may not even newer. Do not install from nVidia directly with the .run file, but use a ppa.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1, including some for Intel
[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710
      [/URL]
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

 Maxwell 750 - kernel 3.15 or newer required
[http://ubuntuforums.org/showthread.php?t=2292419](http://ubuntuforums.org/showthread.php?t=2292419)
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[URL="http://ubuntuforums.org/showthread.php?t=2252908"]http://ubuntuforums.org/showthread.php?t=2252908

[/URL]Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.
[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]
[/URL]

---

### Post by Stephen_Le on 2015-09-16
Wait, so now we're saying that it's a graphics issue? I just tried the NOMODESET from the live USB, I tried to get to the gksudo but it says it's not installed. When I do apt-get install gksu, it finishes but returns the error "E: Unable to locate package gksu".

There is literally only a half-second delay between the splash screen and the liveUSB. I can't hit the grub at all, which I guess leads back to the graphics problem? But then I don't know how to safely use the PPA.

I guess I'm a little overwhelmed. Can you treat me like a 3rd grader? Like, a step-by-step list:

1. DO this (go here)
2. Next, do this (go here)(but don't do this part)
3. Do this(etc)

Just so you know exactly what I am doing is exactly what you're expecting, then it should make this issue easier.


EDIT:
I realized I was always hitting the grub menu....I was confused, I thought it was another menu altogether. Sorry. #-o

But, that doesn't solve the rest of my confusion. What do I enter from here? What do I do from here? Aren't I in the USB, not the SSD?

---

### Post by oldfred on 2015-09-16
I am confused also. I thought you installed.
But with UEFI you add nomodeset or Intel boot parameters to grub menu the same way.
And if you cannot get into UEFI, you must turn off the fast boot setting. It used to be that you could brick some computers, but now either cold boot or removing coin battery on motherboard will let you back in.

So which are we booting? Installer or after install you get black screen?

---

### Post by Stephen_Le on 2015-09-16
So, as I stated before, I have installed using the set partitions according to the site posted before (see my last post). The system is built, but open, so if you think it's a graphic issue, I can remove the video card and plug directly into the mobo port.

**We are trying to boot the SSD, but I am getting shot directly into the Live USB.**

What happens every time is:
1. Boot up into LiveUSB
2. Install (using the auto partition or, in this most recent case, I manually did the partitions, as you see in the boot-repair)
3. Install finishes and tells me to reboot.
4. On reboot, SSD is not seen and boots directly into LiveUSB.
5. Go into Try Ubuntu
6. Connect to Wifi and install/run Boot-Repair
7. Reboot, repeat Step 4.
8. Shut down, remove LiveUSB; PC does not recognize drive and offers BIOS settings.

It bounces immediately from the Gigabyte splash screen to the LiveUSB. Either not getting a black screen at all or it's just skipping it (but Step 8 makes me think I'm not even getting a black screen)

Everything in BIOS is set to UEFI only, so what I installed (from your comments) it should have installed in UEFI. Running the [COLOR=#333333][FONT=monospace][ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" [/FONT][/COLOR]command just now stated that I am on EFI.

It may be worth mentioning that when I do the "Check disk for errors", from the new installer I made using the Universal USB Installer + .iso from the main site, I keep getting 2 errors found. However, when I ran this with the old installer (which, you remember, still didn't really work) I got no errors. I can't recall where I got the "old installer" from, though.

EDIT:

efibootmgr still doesn't see the SSD, though.

---

### Post by ubfan1 on 2015-09-16
Took a look at your latest boot-repair report.  Nothing looks too bad, but I'd check the size of /EFI/Boot/bootx64.efi to confirm it's the same size as grubx64.efi (That's the EFI partition, it may already be mounted at /boot/efi/... ).  If the sizes are the same, you have a fallback bootloader, which is good, but it will only work when secure boot is disabled.  If the sizes are different, check the shimx64.efi size. If they are the same, you are missing the grubx64.efi in that directory.  You can just copy it over from /EFI/ubuntu/grubx64.efi. Then you will have a fallback for both secure boot enabled and disabled.
  I know nothing about Gigabyte boards, but the name "ubuntu" in the 0000 boot position may need to be changed to "Windows Boot Loader".  Check oldfred's links, there may be info on that.  The other non-standard UEFI trick vendors play is to only boot bootloaders named "bootmgfw.efi".  That's what a boot-repair fix will do for you.  And of course, there is no "nomodeset" on the grub linux boot lines, so when you get to the grub menu, edit it in yourself to see if that helps.

---

### Post by Stephen_Le on 2015-09-16
That's both good and upsetting that everything looks good. I am certain that secure boot is turned off, as I pass it every time I go into the BIOS.

I've run the boot-repair, which supposedly did that, but again, no boot.

I'm confused by your last line - how do I do this? And wouldn't it only effect the boot from the LiveUSB, as that's the grub menu that comes up?

---

### Post by oldfred on 2015-09-16
With flash drive removed what happens, just black screen?
Then you need to press escape to get the grub menu.

Or you need to use UEFI to choose to boot ubuntu entry or one time boot key like f12 (my Asus is f8) which is just the boot menu choice similar to UEFI boot tab.

Instead of escape you can try down arrow. If after UEFI, but while grub is loading it remembers keystokes. Down arrow should give you a different boot. I think now you need 2 to get to recovery mode, but have not tried lately.

Then if nothing else works we need to edit the bootx64.efi. But newest installers make it difficult as they now are setting default permissions that do not let you edit anything and you are user 999 when installed system is user 1000.

---

### Post by Stephen_Le on 2015-09-16
With LiveUSB removed, it goes from splash screen to not detecting a bootable drive and asking to change BIOS settings. Though, for some reason ( I believe because I am plugged into the graphics card and not directly into the mobo, now) I can't even detect the splash screen by the time my stupid monitor finishes scanning available inputs. So essentially Push power button >> No bootable device, go into BIOS.

Again, that is my only option with the LiveUSB out. With it in, I have everything else, assuming we don't need to be IN the drive (SSD) to do it.

---

### Post by oldfred on 2015-09-16
When you say splash screen, you mean Gigabyte's UEFI/BIOS start screen?
That is where UEFI has to have settings to allow ubuntu entry to work.
And you need escape key to get to grub menu.
Can you press correct f-key for boot menu?

And then monitor searching for device? That is like it is not outputting anything from video card. You normally should get text screen from grub before it switches video mode & goes to black screen about a couple of sec into actual boot process or that was how my nVidia card did not work.

I might try Boot-Repair. It has an option to add nomodeset.
I might try changing to Intel video from motherboard, but it often requires a different boot parameter, some depending on version of Intel video you have?

---

### Post by Stephen_Le on 2015-09-16
Splash screen=Gigabyte UEFI/BIOS Start screen, so yes. the computer is plugged into a monitor right now, but it's plugged in via the video card. I am sure I turned fast boot off, but even "slow boot" isn't slow enough for the monitor to finish scanning VGA/HDMI/DVI to find my computer. I suspect if I plug it into the motherboard and remove the video card, I can get to the splash screen easier.

So I'm going to try things in that order (Boot-repair with nomodeset, then switching to mobo video) and I'll update this post when I'm through. Once I do get into the grub menu, what do I do?

EDIT:

New Boot Repair: [http://paste.ubuntu.com/12430303](http://paste.ubuntu.com/12430303)

Yet another boot-repair: [http://paste.ubuntu.com/12430452](http://paste.ubuntu.com/12430452)

---

### Post by oldfred on 2015-09-16
If using Intel then you need to change the nomodeset to one of the Intel options. See post #19.

---

### Post by Stephen_Le on 2015-09-16
I posted a couple of the boot repairs in my previous post. How can I narrow down what kernel I should be using from the boot-repair?

---

### Post by oldfred on 2015-09-16
Newest kernel should be fine.

I only keep two normally. One older one just in case. And the newest.

---

### Post by Stephen_Le on 2015-09-16
Oh, I actually meant from the drop down that is present in the boot-repair. There's pretty much every option there that anyone has mentioned.

I ask because I don't think I changed anything internally to allow be to use the gksudo or anything to directly access and save the grub.

---

### Post by oldfred on 2015-09-16
You mean kernel option, not kernel?

If using nVidia try nomodeset.
If using Intel try any of the i915 options. 
What Intel chip do you have, or what video?

But better to use Escape and get into grub menu. Then you can try the various options. Long way around to have Boot-Repair change it.

---

### Post by Stephen_Le on 2015-09-16
Yes, sorry, I meant Kernel option. I tried both the nomodeset and i915=0 options, neither (seemed to make) a difference. How will I know which one works? Or do I just keep rebooting till one does something different?

If I access the grub booted from the LiveUSB, is that still okay? I also have no idea how to properly use grub....

---

### Post by oldfred on 2015-09-16
You need to have live installer unplugged when you reboot.
Have you been able to use UEFI boot menu or one time boot key?

Have you been pressing escape during/after UEFI and does grub menu appear?

I prefer to replace quiet splash (as posted above) as then you see boot process to know it is booting and if it stops it may give a clue on where or why.

Which Intel chip?
Which version of Ubuntu? Newest 14.04.3?
If still 14.04 and very new Intel chip, try 15.04.

---

### Post by Stephen_Le on 2015-09-16
Ubuntu 14.04.3
Intel i5-4690

Yeah Fred, I really can't do anything - it's about half a second between when the splash screen disappears and then I get a blue screen that tells me no recognizable boot device, go to the BIOS setup. Should I try 15.04 then?

---

### Post by oldfred on 2015-09-16
I have that same chip and a much older nVidia card.

I still think you have some setting in UEFI that prevents it from seeing or allowing boot from SSD or ubuntu entry in UEFI.
In UEFI or one time boot menu (your manual says f12) do you see the ubuntu entry?

Post this from live installer:
sudo efibootmgr -v

Boot-Repair already showed them, but those are the entries in your UEFI. 
If you have secure boot on, but installed in non-secure boot mode then UEFI will give that message.  Or it can be whether the Windows or other setting is on.  

I might in UEFI try both Windows and other setting. 
And then use Boot-Repair to install signed grub & kernels for secure boot.
Then try Windows & other setting in UEFI to see if it boots.

It looks like you have to turn on/off either the internal or external video. Is that setting correct.
It looks like IOMMU is now this? I might try with it on and off.
VT-d (Note)
Enables or disables Intel ® Virtualization Technology for Directed I/O. (Default: Enabled)

You do have drives in AHCI? Not RAID nor IDE?

---

### Post by Stephen_Le on 2015-09-17
No other drives in the system other than the SSD.

When I do the sudo efibootmgr -v, only the live installer shows up.

Secure boot is definitely disabled, and Vt-d is also enabled. Should I try disabled?

I don't know what you meant by:
"[COLOR=#000000]I might in UEFI try both Windows and other setting. [/COLOR]
[COLOR=#000000]And then use Boot-Repair to install signed grub & kernels for secure boot.[/COLOR]
[COLOR=#000000]Then try Windows & other setting in UEFI to see if it boots."

EDIT:

Tried VT-d disabled, no change.[/COLOR]

---

### Post by ubfan1 on 2015-09-17
Did you ever confirm that the /EFI/Boot/bootx64.efi is the same size as /EFI/ubuntu/grubx64.efi?    If the sizes are different, you don't have a valid fallback boot.  A valid fallback should be all you need, regardless of what the vendor is doing for requiring specific names on nvram boot entries.  
The other valid fallback configuration is for bootx64.efi to be a copy of shimx64.efi, and grubx64.efi is also present in the same directory.

---

### Post by oldfred on 2015-09-17
Your manual says you have a UEFI/CSM setting for "Windows" or "other". You should try both.

Are you reviewing your motherboard manual and checking that settings are correct? You must document all the ones you change. When you do a UEFI update from Gigabyte it will change back to defaults. And often some setting that does not seem to apply is what then makes it work.

Do you have the latest UEFI version from Gigabyte?

And as ubfan1 suggests copy grubx64.efi into /EFI/Boot and rename to bootx64.efi.

---

### Post by Stephen_Le on 2015-09-17
@ubfan1 - I don't know how to check sizes (talking to a literal newbie), and I wouldn't know how to fix it if that were the problem. Quite strictly would need a "Enter this: then enter this: " sort of description.

@oldfred - I have been doing all this in the "other setting", but I can try flipping to windows and see if anything works.


EDIT:

Just tried all the non-legacy options possible with the "other OS" and "Windows" How do I do what ubfan1 is suggesting?

---

### Post by ubfan1 on 2015-09-17
The EFI partition is usually mounted at /boot/efi, and the command in a terminal (ctrl-alt-t starts one or from the dash, search for term) is
ls -l /boot/efi/EFI/Boot/*
Note the -l is the lower case letter L
The size of the files listed is just before the date, for example, on my system:
$ ls -l /boot/efi/EFI/Boot/*
-rwxr-xr-x 1 root root 1357480 Apr 22  2013 /boot/efi/EFI/Boot/bootx64.efi
-rwxr-xr-x 1 root root  897400 Apr 22  2013 /boot/efi/EFI/Boot/grubx64.efi

Next take a look in the /boot/efi/EFI/ubuntu directory:
$ ls -l /boot/efi/EFI/ubuntu/*
total 3128
-rwxr-xr-x 1 root root  933752 Mar 27  2013 /boot/efi/EFI/ubuntu/gcdx64.efi
-rwxr-xr-x 1 root root    6821 Mar 27  2013 /boot/efi/EFI/ubuntu/grub.cfg
-rwxr-xr-x 1 root root  897400 Mar 25  2013 /boot/efi/EFI/ubuntu/grubx64.efi
-rwxr-xr-x 1 root root 1357480 Mar 27  2013 /boot/efi/EFI/ubuntu/shimx64.efi

Note the size of bootx64.efi is NOT the same as the size of grubx64.efi, but is the same as shimx64.efi.
That works for me.  If the bootx64.efi matches grubx64.efi, that should work for you without secure boot.

The copy command is cp

---

### Post by Stephen_Le on 2015-09-17
Um, so this is really weird, but it says that those directories don't exist. I tried to trace back to /boot but I'm concerned cause it doesn't even show anything even remotely relevant to what we're talking about.

When I do ls -l /boot, all I see is (yes I typed it all out):

-rw-r--r-- 1 root root 1270417 Jul 24 23:19 abi-3.19.0-25-generic
-rw-r--r-- 1 root root 177779 Jul 24 23:19 config-3.19.0-25-generic
drwxr--r-- 1 root root 60 Sep 18 03:06 grub
-rw-r--r-- 1 root root 176500 Mar 12 2014 memtest86+.bin
-rw-r--r-- 1 root root 178176 Mar 12 2014 memtest86+.elf
-rw-r--r-- 1 root root 178680 Mar 12 2014 memtest86+_multiboot.bin
-rw------- 1 root root 3623533 Jul 24 23:19 System.map-3.19.0-25-generic

Any ideas?

---

### Post by ubfan1 on 2015-09-17
Looks like a BIOS boot instead of an UEFI boot.  There should be an efi directory in /boot for UEFI.
You could just mount the EFI partition yourself at any location, like an empty directory in your home.
Ensure you are in your home
cd
Make the empty directory
mkdir x
Mount the EFI partition at x (you can type out your actual home directory starting with /home/xxx if you want)
sudo mount -tvfat /dev/sda1 $HOME/x
Now set your default to the moutned directory and look around
cd x
ls
ls -l Boot
ls -l ubuntu

---

### Post by oldfred on 2015-09-17
Your Summary Report from Boot-Repair in post #28 showed an UEFI install? And it looked pretty normal.
Did you reinstall?

Or are you looking at /boot in the installer, not your install?
You probably have to mount your efi partition in your install if wanting to view it.

/mnt is a existing mount so you do not have to create a mount point if that is all you are using:
 sudo mount -t vfat /dev/sda1 /mnt
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by Stephen_Le on 2015-09-17
Alright, so I THINK I did this right, but when I do 

cd x
ls -l  >> drwxr-xr-x 5 root root 4096 Sep 16 14:21 EFI
ls -l /boot >> same as before
ls -l /home/ubuntu >> Lists folders, plus the one I made, dated Jan 1 1970, labeled root and number 3

Annnnnd a reboot doesn't change anything. When I tried just the mkdir, then tried to mount and it said that I made the folder in the wrong place, so I made it there instead (such as home/ubuntu/x).

@oldfred

I have not re-installed since the last boot-repair I posted. I have been working from the LiveUSB. (In that all the terminal commands are being put into the terminal run off the LiveUSB)

I just tried what you said (I don't know if there should be a space between -t and vfat, but I put one) and I'm still same place.

---

### Post by oldfred on 2015-09-18
If using live installer, you are looking at its files, not your install.

Best just to copy commands, then all spaces are in correct place.

You still need to use escape when booting to get grub menu in your install (with no flash drive installer plugged in).

---

### Post by ubfan1 on 2015-09-18
Oops, forgot the EFI directory in x.  You need to go down into it then do the ls -l Boot
cd x
cd EFI
ls -l Boot ubuntu

---

### Post by Stephen_Le on 2015-09-18
@oldFred - I'm telling you, the boot sequence is inhumanly fast - I just can't catch it. I will try again but what do I do from there?

@ubfan1 - I'll try that and update this post with the information from that.

EDIT:

Boot:
total 120
-rwxr-xr-x 1 root root 119296 Sep 18 03:58 bootx64.efi
-rwxr-xr-x 1 root root 0 Sep 18 03:58 bootx64.efi.grb

ubuntu:
total 2628
-rwxr-xr-x 1 root root 126 Sep 16 21:16 grub.cfg
-rwxr-xr-x 1 root root 119296 Sep 16 21:27 grubx64.efi
-rwxr-xr-x 1 root root 1271672 Sep 16 21:16 MokManager.efi
-rwxr-xr-x 1 root root 1289424 Sep 16 21:16 shimx64.efi

I'm excited, I think we're narrowing it down. As you can see, the bootx64.efi and grubx64.efi are the same size.

---

### Post by oldfred on 2015-09-18
I have installed several different versions of Ubuntu, so my ESP keeps getting overwritten. So far no issues on version difference.

But my bootx64.efi was a copy of an older grubx64.efi, so not exact & this is my grub, but mine is a lot bigger?? Grubx64.efi is probably from wily as that was last install.

```
-rwxr-xr-x 1 root root  956792 Sep 30  2014 bootx64.efi
-rwxr-xr-x 1 root root  955256 Sep 17 18:13 grubx64.efi

```

---

### Post by Stephen_Le on 2015-09-19
Hmm, that is concerning. Do you think I should re-install and go through the process (below) again?

1. Boot to LiveUSB
2. Install Ubuntu 14.04 and reboot
3. Boot to LiveUSB
4. Run Boot-repair

Also, I agree with your comment about me accessing the wrong side (install vs installer), because the changes I made to the home directory weren't saved when I came back in. I'm still trying to open up the grub on the install side, but it seems to just be going straight from the splash to the "No bootable device found" screen.

---

### Post by ubfan1 on 2015-09-19
At this point you have to figure out how to get into the UEFI settings (also know as BIOS).  Power-on holding down buttons, power-on rapidly pressing buttons, --- whatever it takes.  First reset the boot speed to something other than 0 or fast to make it easier next time to get back into the UEFI settings. Then examine your boot devices, from the efibootmgr, it doesn't even look like you have a hard disk listed other than the specific "ubuntu" listing, which may have vendor caused problems because of the name (not Windows Boot Manager), or the executable (not /EFI/Microsoft/Boot/bootmgfw.efi).  Normally, there is a generic hard disk in the list, just like the generic USB.  Add the hard disk to the boot order (after the USB).  Then the default boot loader /EFI/Boot/bootx64.efi should kick in when all else fails.  My understanding is that you do NOT even get a grub prompt when you attempt to boot, and I guess if the device is not included in the boot order, I can understand that.

---

### Post by Stephen_Le on 2015-09-19
efibootmgr only returns the liveUSB, nothing else.

I've gotten into the BIOS and my mobo only has device type-specific (such as SATA, USB, of PXE) boot options, not directly to each of its possible inputs.

So what exactly am I doing then?

---

### Post by oldfred on 2015-09-19
You should be getting a UEFI boot menu with ubuntu as a choice. There are other brands so graphics are different, but UEFI should all show ubuntu as a choice. And you then also should have UEFI: hard drive or something similar as a choice also.

This shows details. entry in UEFI is just "ubuntu"
sudo efibootmgr -v
Boot0000* ubuntu    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\UBUNTU\[COLOR=#ff0000]SHIMX64.EFI[/COLOR])
Boot0013* UEFI OS    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\BOOT\[COLOR=#ff0000]BOOTX64.EFI[/COLOR])..BO
Boot0014* ubuntu    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\UBUNTU\[COLOR=#ff0000]GRUBX64.EFI[/COLOR])..BO

---

### Post by Stephen_Le on 2015-09-21
When I run efibootmgr, I only get one Boot XXXX, and it's the LiveUSB. What does that mean?

---

### Post by oldfred on 2015-09-21
Either you are installing in BIOS boot mode, or grub is not installing the UEFI boot loader correctly.

Boot Boot-Repair in UEFI boot mode and post new Summary Report.

---

### Post by Stephen_Le on 2015-09-21
New Boot repair at [http://paste.ubuntu.com/12515282](http://paste.ubuntu.com/12515282)

---

### Post by oldfred on 2015-09-21
It reinstalled grub and efibootmgr now shows an Ubuntu entry:
```

chroot /mnt/boot-sav/sdb2 efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001,0002
Boot0000* ubuntu	HD(1,800,135800,417bf6a3-82d5-4aba-a07a-aa42bb366bb6)File(EFIubuntushimx64.efi)
Boot0001* UEFI: ADATA USB Flash Drive 1.00	ACPI(a0341d0,0)PCI(14,0)USB(8,0)AMBO
Boot0002* Removable Drive 	BIOS(1,0,00)AMGOAMNO........c.A.D.A.T.A. .U.S.B. .F.l.a.s.h. .D.r.i.v.e. .1...0.0....................A.......................6..Gd-.;.A..MQ..L.2.3.7.1.0.0.9.1.3.2.0.4.0.5.2.2......AMBO

```

From UEFI or one time boot key can you select the ubuntu entry?

It looks like part of issue may be that flash drive is promoted to sda, and hard drive is then sdb.
I had similar issues when sda was in first SATA port, but I must have skipped a port and flash drives would be sdb on reboot, sde when plugged into working system. I had multiple drives and had my own confusion and had to keep track of sdb, sdc, & sdd was they would change drive.

It might avoid confusion if you plug drive into first SATA port? But then the UEFI entries showing hd1 and grub showing hd1 may need updating. UEFI uses GUID and grub uses UUID to avoid port change issues, but not sure with UEFI.

---

### Post by Stephen_Le on 2015-09-21
It's weird, it's still not showing that the SSD is bootable at startup.

---

### Post by oldfred on 2015-09-21
Do you have secure boot on?
 Normally you get two ubuntu entries, both shim & grub. Shim for Secure boot and grub for standard UEFI boot. You only have the one ubuntu using shimx64.efi.

---

### Post by Stephen_Le on 2015-09-21
I am 100% secure boot is disabled.

---

### Post by oldfred on 2015-09-21
I am running out of ideas.

Did you check if SSD is in SATA port 1?
Does UEFI have a setting to turn on hard drive port? Some do.

---

### Post by Stephen_Le on 2015-09-22
No, there are no options other than SATA, USB, and PXE. I didn't think it would matter if the drive was connected to SATA1, but I can try.

EDIT:

I apologize 1000x. I was pigheaded. I just plugged into SATA0 and it booted up perfectly.

---

### Post by oldfred on 2015-09-22
Glad we found a solution, but that was a last straw suggestion. I would have also thought it should have worked  from any port.

---

