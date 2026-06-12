---
title: "Installing Linux on a Toshiba A505-s6033"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by flamesbladeflcl on 2010-02-06
I recently got a new laptop a [Toshiba A505-S6033]("http://laptops.toshiba.com/laptops/satellite/A500/A505-S6033") from best buy after my prior laptop's screen hinge broke. The laptop comes installed with windows 7 64bit. I trying to install ubuntu to a another primary partition in order to dual boot (and after I get that running, I plan to add osx to triple boot). I have a copy of ubuntu on a usb drive made with unetbootin, and I've tested that it works with multiple other computers. When I try to boot it on the a505, it starts to load then fails when it tries to find the root file system. I've tried to load other linux versions such as puppy (both from usb and cd) and Hexxeh's chromium os (usb) to similar results, all failing when they try to find the filesystem. any suggestions?

---

### Post by quixote on 2010-02-07
I don't see your exact model on the [Laptop Testing page]("https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba"), but maybe there will be some useful information for you among the other Satellite models.

---

### Post by flamesbladeflcl on 2010-02-07
can't find anything to help, all the ones I see list problems for things not working after install. but I can't even install.

---

### Post by djchandler on 2010-02-08
> **flamesbladeflcl said:**
> I recently got a new laptop a [Toshiba A505-S6033]("http://laptops.toshiba.com/laptops/satellite/A500/A505-S6033") from best buy after my prior laptop's screen hinge broke. The laptop comes installed with windows 7 64bit. I trying to install ubuntu to a another primary partition in order to dual boot (and after I get that running, I plan to add osx to triple boot). I have a copy of ubuntu on a usb drive made with unetbootin, and I've tested that it works with multiple other computers. When I try to boot it on the a505, it starts to load then fails when it tries to find the root file system. I've tried to load other linux versions such as puppy (both from usb and cd) and Hexxeh's chromium os (usb) to similar results, all failing when they try to find the filesystem. any suggestions?

First of all, congratulations on your purchase of a very nice laptop. Toshiba has a great reputation for reliability. It should serve you well. There's a lot of computer there.

Puppy Linux requires Grub be installed before you can install Puppy to a hard disk. Considering how it works to install to hard disk, that wouldn't be my first choice. It looks as if they are looking to find their niche as a portable OS, not necessarily for long term install on a hard disk. To do that, you need to jump through a couple of hoops. What you tried with Puppy probably doesn't even try to mount your hard drive. [See this link]("http://www.puppylinux.org/main/index.php?file=Frugal%20Install%20to%20Hard%20Disk.txt").

If Puppy is the only one you tried to boot with a CD, that doesn't mean  an Ubuntu CD won't boot. But I don't think the USB boot is the problem. It looks to me like you have out thought the software installer. The Ubuntu installer must assume that the user is probably not as sophisticated as you seem to be.

Did you create the new primary partition in Windows 7 and perhaps create any extended partitions within it? Or if you have a primary also created for OS X, that could be the problem.

My solution would be to go back into Windows and delete the partition you already set aside for Ubuntu. The Ubuntu installer started moving my Windows data around to  make room for itself on the Windows partition when I did that once and wasn't fully paying attention. It was a case of outsmarting the installer, just as you did too. The other primary partitions could flummox the installer, especially if there are already 4 primary partitions and marked as in use.  If the room you set aside is just marked as unused and not partitioned, then you will have the option to install in the largest contiguous empty space on the hard disk.

[Check out this thread]("http://ubuntuforums.org/showthread.php?t=572451"). The original poster in this thread had reached the 4 primary partition limit. It's 3 pages long but marked solved, and that's a good sign.

Most new computers with Windows installed have 3 primary partitions already allocated since Vista. You have a restore partition set up by the OEM, a rescue partition created by the Windows installation plus the partition where Windows itself resides. That leaves just one, and if Ubuntu is already finding 4, that could be the problem and why it won't mount the drive, particularly if you chose install now instead of "Try Ubuntu."

---

### Post by flamesbladeflcl on 2010-02-08
I wasn't trying to install puppy that was more of a test to see if anything would boot right at all after my trying to run ubuntu failed. (I used puppy as I normally keep a puppy flash to run on wyse boxes when the server is down for a quick temp setup) I haven't made the partitions yet, though yes there are 3 by default which I plan to remove. but the more important thing i want to make clear is that it doesn't get far enough to show the option select screen (the try ubuntu, install ubuntu options).

I'll try an ubuntu cd but I don't think it is the solution either...

---

### Post by djchandler on 2010-02-08
> **flamesbladeflcl said:**
> I'll try an ubuntu cd but I don't think it is the solution either...

How about a BIOS/EFI setting getting in your way and stopping it from booting from USB? I assume you had to fiddle with the BIOS or enter a menu to boot the USB device.

---

### Post by flamesbladeflcl on 2010-02-08
> **djchandler said:**
> How about a BIOS/EFI setting getting in your way and stopping it from booting from USB? I assume you had to fiddle with the BIOS or enter a menu to boot the USB device.

It starts to boot it just fails, I've tried reseting it back to default bios settings but it still doesn't work.

---

### Post by djchandler on 2010-02-09
> **flamesbladeflcl said:**
> It starts to boot it just fails, I've tried reseting it back to default bios settings but it still doesn't work.

Do you at least get to the sign-on line that starts "ISOLINUX" before it stops?

Somehow the code being read from the media you are trying to install from is not properly executing--Square One again. How about changing your SATA to AHCI if set to IDE?

Can you run and MD5SUM or SHA1SUM on the CD or .ISO image file from within Windows?

You can find those data strings in the directory at the [bottom of this page]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/karmic/").

---

### Post by djchandler on 2010-02-09
> **flamesbladeflcl said:**
> It starts to boot it just fails, I've tried reseting it back to default bios settings but it still doesn't work.

Do you at least get to the sign-on line that starts "ISOLINUX" before it stops?

Somehow the code being read from the media you are trying to install from is not properly executing--Square One again. How about changing your SATA to AHCI if set to IDE?

Can you run and MD5SUM or SHA1SUM on the CD or .ISO image file from within Windows?

You can find those data strings in the directory at the [bottom of this page]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/karmic/").

---

### Post by flamesbladeflcl on 2010-02-09
> **djchandler said:**
> Do you at least get to the sign-on line that starts "ISOLINUX" before it stops?

Somehow the code being read from the media you are trying to install from is not properly executing--Square One again. How about changing your SATA to AHCI if set to IDE?

Can you run and MD5SUM or SHA1SUM on the CD or .ISO image file from within Windows?

You can find those data strings in the directory at the [bottom of this page]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/karmic/").
it dies at a line like "begin:finding root filesystem" I don't remember the exact phrasing though, so I'll re-run to confirm what it is.

I'll try changing the mode and see the difference.

I don't think it is an improper download as the usb will boot on a different computer. but I'll check that too.

---

### Post by flamesbladeflcl on 2010-02-09
okay it was "Begin:waiting for root file system...."
after that it said something about improper irq?
then "gave up waiting for root device" and it droped to busy box. this is from a fresh download

---

### Post by flamesbladeflcl on 2010-02-09
oaky I got my computer to boot the iso directly with easybcd 2.0 and I managed to get to the install screen. so while I am now able to install ubuntu, I still want to fix the usb boot issue as I use the boot from usb option often when repairing or testing out a new distro (or running something like chromium os which doesn't work right from a hard drive install).

---

### Post by flamesbladeflcl on 2010-02-09
wait I lied, it actually loaded up the "try ubuntu/install/boot from first hard drive" screen this time but after I hit "try" it failed again. with the message "/init: line 1: can't open /dev/sr0: No medium found"

---

### Post by flamesbladeflcl on 2010-02-11
tried a few more times but still no luck >_< any suggestions?

---

### Post by djchandler on 2010-02-12
> **flamesbladeflcl said:**
> tried a few more times but still no luck >_< any suggestions?

You've exhausted all conceivable solutions AFAIK.

The only think left is a hardware issue. In the back of my mind is the paranoid idea that Toshiba has somehow hamstrung your system, keeping it from installing another OS because they don't want to support it. I have a bit older and less expensive Toshiba laptop that they deliberately left a setting for hardware virtualization out of the BIOS settings even though the underlying hardware is fully capable of supporting it.

Are you trying 32-bit or 64-bit Ubuntu? I would be interested to know if that makes a difference.

So here's a couple of shots in the dark to suggest. Have you tried downloading Virtualbox or some other hypervisor and tried to install Ubuntu in a virtual machine? Have you tried to install Ubuntu using [Wubi]("http://wubi-installer.org/")?

I tried to use MS Virtual PC to run Linux in Windows 7 x64 Ultimate. Older versions did in Windows XP. It seems the only operating systems the newest Virtual PC in Windows 7 supports are Microsoft's. So I have been using Virtualbox 3.1 (Debian, Virtualbox 3.1.4 out now) or VMware Player 3.x (BusyBox notfred appliance for running Folding@Home SMP) to run Linux in a VM. Don't forget to fiddle with the BIOS/EFI yet again to enable hardware virtualization.

Your CPU and system are so new, you are blazing the trail, my friend. I think they call this the "bleeding edge." The only thing else I can think of is go over to [Launchpad]("https://launchpad.net/ubuntu") and see if there are any issues with your architecture posted there.

Found [this link]("http://forums.linuxmint.com/viewtopic.php?f=49&t=40899"). Even once this user got LinuxMint installed, there were still issues and no answers yet.

In reply to [this question]("http://forums.fedoraforum.org/showthread.php?t=237580") I found [another link on the Fedora Forums]("http://fedoraproject.org/wiki/Common_F12_bugs#Systems_fail_to_boot.2C_USB_is_not_functional.2C_network_adapter_fails_to_work_.28or_possibly_other_symptoms.29_due_to_imperfect_handling_of_BIOSes_with_broken_IOMMU_handling") about a BIOS bug on an HP system with the same i7-720QM CPU. If you have been using a 32-bit version, this link suggests that perhaps using 64-bit will fix your issue despite the fact you are not over 4GB of RAM.

Your post above where you quoted
>  "Begin:waiting for root file system...."
after that it said something about improper irq?
then "gave up waiting for root device"
suggests we may be on the right track here as regards the BIOS bug and IOMMU.

:confused:

PS Sorry it took so long to answer again. I've been indisposed the last couple of days.

---

### Post by flamesbladeflcl on 2010-02-14
I first tried 32 bit, then I switched to trying 64 bit Ubuntu, and the puppy I tried was 32 bit...

Haven't tried virtual box but that doesn't really solve my problems. I did try wubi though, that let me install but it failed again after running updates and restarting. different reason though.

Yeah some bios thing seems to be it.... but I can't figure out what.

---

### Post by rigsc on 2010-03-07
I just purchased the same laptop.  I've managed to successfully install Fedora 12 on it using the "basic" video option.  I have to boot with "pci=noacpi" in order to use USB devices, install the Nvidia driver, wifi driver, etc and even then it's a coinflip whether or not it will boot successfully.

Please followup if you've made any progress with it.  It's too nice of a laptop to only run Windows.

---

### Post by Djalmahal on 2010-03-07
Hi, I'm thinking of buying this very laptop, so I'm foloowing this thread. Tomorrow I will go into a shop and try to boot it from an USB Stick, I'll let you know what happened...

Andreas

---

### Post by flamesbladeflcl on 2010-03-08
> **Djalmahal said:**
> Hi, I'm thinking of buying this very laptop, so I'm foloowing this thread. Tomorrow I will go into a shop and try to boot it from an USB Stick, I'll let you know what happened...

Andreas

it is a nice laptop on windows, it seems to be really annoying for linux though

---

### Post by Scienceman123 on 2010-03-08
I had issues with Wubi on this same laptop. Using Ubuntu 64-bit, the graphics start in what appear to be 256 colors. The login window fails to appear, switching to other ttys results in analog-like distortion (text wavers and shimmers). Switching to tty7 and then to a text tty renders all text unreadable.

---

### Post by rigsc on 2010-03-09
Check out this thread:
 
[http://ubuntuforums.org/showthread.php?t=1301101&page=8](http://ubuntuforums.org/showthread.php?t=1301101&page=8)
 
It's for a different laptop that's presumably suffering from the same issue and the steps get my A505 booting without any additional kernel options.

---

### Post by xtamarche on 2010-03-19
bump.

I just got this laptop as well and I tried installing this.  I did a little bit of research on the same problem.  It installs fine, except for the wireless driver working.  I believe that it is using a realtek driver 8192se series.  That wasn't my major concern...

The _major_ problem is with the X server, the restricted proprietary driver from nvidia (185.18.x series I believe is what I was using), and the way IRQ was being handled.  It loops at login and just flashes the login screen.

Upon further research, I read the /etc/X11/xorg.conf and read that the display screen wasn't being detected.  I tried importing the .bin file for the EDID through windows 7.  The file is :

SEC3041.bin  

I added this to my xorg.conf file but still no solution.  I went into safeboot option (I think it's the repair option... I'm having a brain fart right now).

From there, I tried to enter in the startx command manually.  I got my log message with the error:

NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): The NVIDIA kernel module does not appear to be receiving
(EE) NVIDIA(0):     interrupts generated by the NVIDIA graphics device
(EE) NVIDIA(0):     PCI:1:0:0.  Please see Chapter 8: Common Problems in the
(EE) NVIDIA(0):     README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

From there, I changed grub with the boot option pci=noacpi

Didn't solve that either.  Any suggestions anyone?  I can post additional information as well (I can get my xorg.conf file as well later on).  Please advise on what I need to do next, even if it includes posting more info.  Thanks!

---

### Post by xtamarche on 2010-03-19
Update:

I booted with the noapic parameter and it got me to the login screen.  Now it doesn't crash until after you enter in a login.

It will seem like it's booting, then it will hang before it gets into gnome.

---

### Post by xtamarche on 2010-03-19
For anyone who wants to know....

I switched out the nvidia driver and swapped back in the nv driver..

That fixes it for the most part...

Now to fix the wireless and the fact that the USB ports dont work.

---

### Post by rigsc on 2010-03-19
I'm running *mostly* good with a vanilla 2.6.33 kernel patched with this patch:

 [http://bugzilla.kernel.org/attachment.cgi?id=23958](http://bugzilla.kernel.org/attachment.cgi?id=23958) 

I boot with the "nohpet" option to get rid of one of the stack traces while it's booting.

and Nvidia driver version 195.36.08 (the version that's reported to cause overheating on Windows machines...don't think it's a problem on laptops, though).

Wireless works *ok* with the driver from Realtek until I get more than 40 feet from my router then it get's a little flaky.

---

### Post by Simulator on 2010-03-22
I've got this same laptop, and - after a weekend of extensive research, banging my head against the wall, and almost re-installing Windoze on it - I've finally succeeded in getting the following working:

[LIST]
[*]NVIDIA GeForce 310M graphics card.
[*]RealTek RTL8191SE-VA2 wireless network card.
[*]WebCam
[*]USB
[/LIST]

Here's some step-by-step instructions (for Ubuntu 9.10 Karmic Koala).  Note that you need an Internet connection - most likely through a wired connection.

[LIST=1]
[*]Following a clean install, update all of your packages to the most up-to-date versions:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
[*]Make sure you have some required packages installed.  These are needed to build some of the required drivers:

```
sudo apt-get install build-essential ia32-libs
```

[*]Now edit the default GRUB settings.  This is done for two reasons: firstly, so that you can get to a recovery console to fix any boot problems that you may subsequently experience (also needed to install the NVIDIA driver) and secondly to change a Kernel Parameter that, all by itself fixes most of the problems running Linux on this machine.
[LIST=a]
[*]Edit the file (I use nano to edit system files - feel free to use vi or emacs or whatever):
```
sudo nano /etc/default/grub
```
[*]Comment out the line that defines GRUB_HIDDEN_TIMEOUT by placing a '#' at the start of the line.  This tells GRUB to show you a menu at boot time, which allows you to select a recovery console later.
[*]You should also see a line with the following contents:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Edit this line so that it reads:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]acpi=noirq[/COLOR]"
```
All by itself, this fixes most of the problems with the machine.  It appears that the i7 processor does some funky stuff with the IRQ signals, causing problems for many of the hardware devices under Ubuntu.
[*]Save the modified file (Control+"O" + RETURN to save, Control+"X" to exit in nano) and then have grub update its configuration with the command:
```
sudo update-grub
```
[/LIST]
[*]OK.  Now let's get that problematic NVIDIA card working.  Go to the NVIDIA web-site and download the latest driver.  If you have installed the 64-bit (AMD64) variant of Karmic, use the first link - otherwise use the second:
64-bit Ubuntu: [http://www.nvidia.com/object/linux_display_amd64_195.36.15.html]("http://www.nvidia.com/object/linux_display_amd64_195.36.15.html")
32-bit Ubuntu: [http://www.nvidia.com/object/linux_display_ia32_195.36.15.html]("http://www.nvidia.com/object/linux_display_ia32_195.36.15.html")
I'm going to assume that this file is downloaded into the "/home/someuser/Downloads" directory.
[*]Restart your machine.  When the GRUB menu appears, select the recovery mode for the most recent Kernel version installed (second option from the top, typically).  The machine boots and eventually brings up a menu.  Select the top menu option (resume).  This will bring you to a console login - log in.
[*]When you get to a command prompt, issue the following command to install the NVIDIA drivers:
64-bit Ubuntu:
```
sudo /home/someuser/Downloads/NVIDIA-Linux-x86_64-195.36.15-pkg2.run
```
32-bit Ubuntu:
```
sudo /home/someuser/Downloads/NVIDIA-Linux-x86-195.36.15-pkg1.run
```
(Check the version numbers to ensure they match the version you downloaded. Also don't forget to replace "someuser" with your user name. ;))
Follow the instructions in the installer to build the driver, install it and generate your "xorg.conf" file accordingly.
[*]IMPORTANT: You now need to edit the "xorg.conf" file to add a couple of lines:
[LIST=a]
[*]```
sudo nano /etc/X11/xorg.conf
```
[*]Locate the "Device" section and add the lines indicated in red below:
```
Section "Device"
        Identifier      "InternalCard"
        Driver          "nvidia"
        [COLOR="Red"]Option          "ConnectedMonitor" "DFP-0"
        Option          "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"[/COLOR]
EndSection
```
[*]Save the modified version of the file.
[/LIST]
[*]Now reboot your machine to activate the NVIDIA driver.  (Let the GRUB menu time-out so that it boots normally).  If all has gone well, you should see the NVIDIA logo appear before getting to the X login screen.
[*]Login as normal.  Now we're going to get the wireless driver running.  Download the driver from the RealTek web-site:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")
Select the any of the site numbers for the *Linux driver for kernel 2.6.X* option.
[*]Now build and install your wireless driver:
```
cd /home/someuser/Downloads
tar xvzf rtl8192se_linux_2.6.0015.0127.2010.tar.gz
cd rtl8192se_linux_2.6.0015.0127.2010
make
sudo make install
sudo modprobe r8192se_pci
```
And you're all set!
[*]Enjoy your new laptop running Ubuntu!  You should find your USB ports and web-cam are now working too!
[/LIST]

---

### Post by xtamarche on 2010-03-31
To the above, I will try this tomorrow.  Thank you for your reply, and let's pray it works for me too =]  Also you mentioned for people getting a 32-bit version of the Ubuntu, I don't think anyone who got this laptop would go with a 32-bit version... just for clarification purposes, maybe u should edit it to only follow 64-bit?  But otherwise, GREAT guide.

---

### Post by rigsc on 2010-03-31
AFAICT, the guide is enough to get the laptop "operational" but power management will be an issue.
 
A bit more work, but if you would like to have working power management look at this thread:
 
[[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=1301101&page=8[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1301101&page=8")
 
Replace the kernel patch they mention with this one:
 
[https://bugzilla.kernel.org/attachment.cgi?id=25669](https://bugzilla.kernel.org/attachment.cgi?id=25669)
 
And boot the new kernel with the option "acpi=copy_dsdt"

---

### Post by Simulator on 2010-03-31
Thanks for the info.  I'll definitely look into that.

Since my last posting, I have encountered a few problems: occasionally I get an error on start-up stating: **BUG: soft lockup - CPU#0 stuck for 61s!**.  I could only get around this by restarting the machine.

Also, I get errors Hibernating the machine, which is annoying.

I'll try out the kernel patch you refer to - which looks very promising!  Power Management is definitely something that shouldn't be ignored...

---

### Post by xtamarche on 2010-04-01
Simulator- Thank you for the giude, it helped me with getting the nvidia drivers to work.

I switched the noapic flag i was using to the acpi=noirq and it gives me problems with IRQ and the USB ports ONLY in recovery mode... Scary to think about.... but thank you nonetheless, I have not started on my wireless driver nor the power management part on this.  But it definitely is a start!  I will continue on this as well.

---

### Post by xtamarche on 2010-04-01
Problem on install with wireless.  Compiles fine.  On install, I try and get:

  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/xtam/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192'
make: *** [install] Error 2

Any suggestions?

---

### Post by wiltk on 2010-04-01
> **xtamarche said:**
> Problem on install with wireless.  Compiles fine.  On install, I try and get:

  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/xtam/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192'
make: *** [install] Error 2

Any suggestions?

I think I ran into this same problem on my installs on the A505-s6035.  The solution was that I needed to actually be using a root shell (i.e. sudo su), and not just sudo the *make install* command.

---

### Post by wiltk on 2010-04-02
> **rigsc said:**
> AFAICT, the guide is enough to get the laptop "operational" but power management will be an issue.
 
A bit more work, but if you would like to have working power management look at this thread:
 
[[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=1301101&page=8[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1301101&page=8")
 
Replace the kernel patch they mention with this one:
 
[https://bugzilla.kernel.org/attachment.cgi?id=25669](https://bugzilla.kernel.org/attachment.cgi?id=25669)
 
And boot the new kernel with the option "acpi=copy_dsdt"

Thanks for this **rigsc**.  That was the last piece of the puzzle for me to get my A505-S6035 completely up and running.

---

### Post by Scienceman123 on 2010-04-13
I followed his instructions for 9.10, but when compiling:

```
  LD      drivers/acpi/acpica/acpi.o                                                                                
drivers/acpi/acpica/dsmthdat.o: In function `acpi_ds_method_data_init':                                             
/usr/src/linux/drivers/acpi/acpica/dsmthdat.c:92: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/dsopcode.o: In function `acpi_ds_exec_end_control_op':                                          
/usr/src/linux/drivers/acpi/acpica/dsopcode.c:1231: multiple definition of `acpi_gbl_copy_dsdt'                     
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/dswexec.o: In function `acpi_ds_exec_begin_op':                                                 
/usr/src/linux/drivers/acpi/acpica/dswexec.c:215: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/dswscope.o: In function `acpi_ds_scope_stack_pop':                                              
/usr/src/linux/drivers/acpi/acpica/dswscope.c:178: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/dsmethod.o: In function `acpi_ds_create_method_mutex':                                          
/usr/src/linux/drivers/acpi/acpica/dsmethod.c:138: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/dsobject.o: In function `acpi_ds_init_object_from_op':                                          
/usr/src/linux/drivers/acpi/acpica/dsobject.c:604: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/dsutils.o: In function `acpi_ds_resolve_operands':                                              
/usr/src/linux/drivers/acpi/acpica/dsutils.c:386: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/dswload.o: In function `acpi_ds_init_callbacks':                                                
/usr/src/linux/drivers/acpi/acpica/dswload.c:74: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/dswstate.o: In function `acpi_ds_get_current_walk_state':                                       
/usr/src/linux/drivers/acpi/acpica/dswstate.c:447: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/dsinit.o: In function `acpi_ds_initialize_objects':                                             
/usr/src/linux/drivers/acpi/acpica/dsinit.c:157: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evevent.o: In function `acpi_ev_fixed_event_detect':                                            
/usr/src/linux/drivers/acpi/acpica/evevent.c:232: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evregion.o: In function `acpi_ev_execute_reg_methods':                                          
/usr/src/linux/drivers/acpi/acpica/evregion.c:998: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evsci.o: In function `acpi_ev_remove_sci_handler':                                              
/usr/src/linux/drivers/acpi/acpica/evsci.c:179: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evxfevnt.o: In function `acpi_ev_get_gpe_device':                                               
/usr/src/linux/drivers/acpi/acpica/evxfevnt.c:796: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evmisc.o: In function `acpi_ev_is_notify_object':                                               
/usr/src/linux/drivers/acpi/acpica/evmisc.c:623: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evrgnini.o: In function `acpi_ev_io_space_region_setup':                                        
/usr/src/linux/drivers/acpi/acpica/evrgnini.c:138: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evxface.o: In function `acpi_release_global_lock':                                              
/usr/src/linux/drivers/acpi/acpica/evxface.c:811: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evxfregn.o: In function `acpi_remove_address_space_handler':                                    
/usr/src/linux/drivers/acpi/acpica/evxfregn.c:135: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evgpe.o: In function `acpi_ev_update_gpe_enable_masks':                                         
/usr/src/linux/drivers/acpi/acpica/evgpe.c:121: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/evgpeblk.o: In function `acpi_ev_valid_gpe_event':                                              
/usr/src/linux/drivers/acpi/acpica/evgpeblk.c:89: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exconfig.o: In function `acpi_ex_unload_table':                                                 
/usr/src/linux/drivers/acpi/acpica/exconfig.c:554: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exfield.o: In function `acpi_ex_write_data_to_field':                                           
/usr/src/linux/drivers/acpi/acpica/exfield.c:210: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exnames.o: In function `trace_kmalloc':                                                         
/usr/src/linux/include/trace/events/kmem.h:47: multiple definition of `acpi_gbl_copy_dsdt'                          
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exoparg6.o: In function `acpi_ex_do_match':                                                     
/usr/src/linux/drivers/acpi/acpica/exoparg6.c:101: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exresolv.o: In function `acpi_ex_resolve_multiple':                                             
/usr/src/linux/drivers/acpi/acpica/exresolv.c:340: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exstorob.o: In function `trace_kmalloc':                                                        
/usr/src/linux/include/trace/events/kmem.h:47: multiple definition of `acpi_gbl_copy_dsdt'                          
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exconvrt.o: In function `acpi_ex_convert_to_ascii':                                             
/usr/src/linux/drivers/acpi/acpica/exconvrt.c:291: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exfldio.o: In function `trace_kmalloc':                                                         
/usr/src/linux/include/trace/events/kmem.h:47: multiple definition of `acpi_gbl_copy_dsdt'                          
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exoparg1.o: In function `acpi_ex_opcode_1A_0T_1R':                                              
/usr/src/linux/drivers/acpi/acpica/exoparg1.c:586: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exprep.o: In function `acpi_ex_prep_common_field_object':                                       
/usr/src/linux/drivers/acpi/acpica/exprep.c:321: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exresop.o: In function `acpi_ex_check_object_type':                                             
/usr/src/linux/drivers/acpi/acpica/exresop.c:77: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exsystem.o: In function `acpi_ex_system_reset_event':                                           
/usr/src/linux/drivers/acpi/acpica/exsystem.c:285: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/excreate.o: In function `acpi_ex_create_method':                                                
/usr/src/linux/drivers/acpi/acpica/excreate.c:463: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exmisc.o: In function `acpi_ex_do_math_op':                                                     
/usr/src/linux/drivers/acpi/acpica/exmisc.c:414: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exoparg2.o: In function `acpi_ex_opcode_2A_0T_1R':                                              
/usr/src/linux/drivers/acpi/acpica/exoparg2.c:515: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exregion.o: In function `acpi_ex_cmos_space_handler':                                           
/usr/src/linux/drivers/acpi/acpica/exregion.c:415: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exstore.o: In function `acpi_ex_store_object_to_node':                                          
/usr/src/linux/drivers/acpi/acpica/exstore.c:604: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exutils.o: In function `acpi_ex_truncate_for32bit_table':                                       
/usr/src/linux/drivers/acpi/acpica/exutils.c:214: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exdump.o:(.bss+0x0): multiple definition of `acpi_gbl_copy_dsdt'                                
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exmutex.o: In function `acpi_ex_unlink_mutex':                                                  
/usr/src/linux/drivers/acpi/acpica/exmutex.c:72: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exoparg3.o: In function `trace_kmalloc':                                                        
/usr/src/linux/include/trace/events/kmem.h:47: multiple definition of `acpi_gbl_copy_dsdt'                          
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exresnte.o: In function `acpi_ex_resolve_node_to_value':                                        
/usr/src/linux/drivers/acpi/acpica/exresnte.c:82: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/exstoren.o: In function `acpi_ex_store_object_to_object':                                       
/usr/src/linux/drivers/acpi/acpica/exstoren.c:199: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/hwacpi.o: In function `acpi_hw_get_mode':                                                       
/usr/src/linux/drivers/acpi/acpica/hwacpi.c:162: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/hwgpe.o: In function `acpi_hw_enable_all_wakeup_gpes':                                          
/usr/src/linux/drivers/acpi/acpica/hwgpe.c:459: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/hwregs.o: In function `acpi_hw_read_multiple':                                                  
/usr/src/linux/drivers/acpi/acpica/hwregs.c:397: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/hwsleep.o: In function `acpi_set_firmware_waking_vector':                                       
/usr/src/linux/drivers/acpi/acpica/hwsleep.c:80: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/hwxface.o: In function `acpi_read_bit_register':                                                
/usr/src/linux/drivers/acpi/acpica/hwxface.c:268: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/hwvalid.o: In function `acpi_hw_validate_io_request':                                           
/usr/src/linux/drivers/acpi/acpica/hwvalid.c:126: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsaccess.o: In function `acpi_ns_lookup':                                                       
/usr/src/linux/drivers/acpi/acpica/nsaccess.c:287: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsload.o: In function `acpi_ns_load_table':                                                     
/usr/src/linux/drivers/acpi/acpica/nsload.c:76: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nssearch.o: In function `acpi_ns_search_one_scope':                                             
/usr/src/linux/drivers/acpi/acpica/nssearch.c:99: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsxfeval.o: In function `acpi_get_data':                                                        
/usr/src/linux/drivers/acpi/acpica/nsxfeval.c:799: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsalloc.o: In function `acpi_ns_install_node':                                                  
/usr/src/linux/drivers/acpi/acpica/nsalloc.c:177: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nseval.o: In function `acpi_ns_evaluate':                                                       
/usr/src/linux/drivers/acpi/acpica/nseval.c:80: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsnames.o: In function `acpi_ns_get_pathname_length':                                           
/usr/src/linux/drivers/acpi/acpica/nsnames.c:180: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsutils.o: In function `acpi_ns_valid_root_prefix':                                             
/usr/src/linux/drivers/acpi/acpica/nsutils.c:210: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsxfname.o: In function `trace_kmalloc':                                                        
/usr/src/linux/include/trace/events/kmem.h:47: multiple definition of `acpi_gbl_copy_dsdt'                          
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsdump.o:(.bss+0x0): multiple definition of `acpi_gbl_copy_dsdt'                                
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsinit.o: In function `acpi_ns_init_one_device':                                                
/usr/src/linux/drivers/acpi/acpica/nsinit.c:425: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsobject.o: In function `acpi_ns_get_secondary_object':                                         
/usr/src/linux/drivers/acpi/acpica/nsobject.c:300: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nswalk.o: In function `acpi_ns_get_next_node':                                                  
/usr/src/linux/drivers/acpi/acpica/nswalk.c:72: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsxfobj.o: In function `acpi_get_next_object':                                                  
/usr/src/linux/drivers/acpi/acpica/nsxfobj.c:231: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nsparse.o: In function `acpi_ns_one_complete_parse':                                            
/usr/src/linux/drivers/acpi/acpica/nsparse.c:70: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/nspredef.o: In function `acpi_ns_check_for_predefined_name':                                    
/usr/src/linux/drivers/acpi/acpica/nspredef.c:347: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/psargs.o: In function `acpi_ps_get_next_package_end':                                           
/usr/src/linux/drivers/acpi/acpica/psargs.c:128: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/psparse.o: In function `acpi_ps_get_opcode_size':                                               
/usr/src/linux/drivers/acpi/acpica/psparse.c:76: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/psloop.o: In function `acpi_ps_complete_op':                                                    
/usr/src/linux/drivers/acpi/acpica/psloop.c:571: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/pstree.o: In function `acpi_ps_get_arg':                                                        
/usr/src/linux/drivers/acpi/acpica/pstree.c:71: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/pswalk.o: In function `acpi_ps_delete_parse_tree':                                              
/usr/src/linux/drivers/acpi/acpica/pswalk.c:63: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/psopcode.o: In function `acpi_ps_get_opcode_info':                                              
/usr/src/linux/drivers/acpi/acpica/psopcode.c:728: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/psscope.o: In function `acpi_ps_get_parent_scope':                                              
/usr/src/linux/drivers/acpi/acpica/psscope.c:64: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/psutils.o: In function `acpi_ps_init_op':                                                       
/usr/src/linux/drivers/acpi/acpica/psutils.c:90: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/psxface.o: In function `acpi_debug_trace':                                                      
/usr/src/linux/drivers/acpi/acpica/psxface.c:80: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rsaddr.o: In function `acpi_rs_set_address_common':                                             
/usr/src/linux/drivers/acpi/acpica/rsaddr.c:359: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rscreate.o: In function `acpi_rs_create_aml_resources':                                         
/usr/src/linux/drivers/acpi/acpica/rscreate.c:400: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rsinfo.o:(.bss+0x0): multiple definition of `acpi_gbl_copy_dsdt'                                
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rsio.o:(.bss+0x0): multiple definition of `acpi_gbl_copy_dsdt'                                  
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rslist.o: In function `acpi_rs_convert_resources_to_aml':                                       
/usr/src/linux/drivers/acpi/acpica/rslist.c:135: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rsmisc.o: In function `acpi_rs_convert_resource_to_aml':                                        
/usr/src/linux/drivers/acpi/acpica/rsmisc.c:327: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rsxface.o: In function `acpi_walk_resources':                                                   
/usr/src/linux/drivers/acpi/acpica/rsxface.c:504: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rscalc.o: In function `acpi_rs_get_aml_length':                                                 
/usr/src/linux/drivers/acpi/acpica/rscalc.c:189: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rsirq.o:(.bss+0x0): multiple definition of `acpi_gbl_copy_dsdt'                                 
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rsmemory.o:(.bss+0x0): multiple definition of `acpi_gbl_copy_dsdt'                              
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/rsutils.o: In function `acpi_rs_decode_bitmask':                                                
/usr/src/linux/drivers/acpi/acpica/rsutils.c:65: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/tbxface.o: In function `acpi_remove_table_handler':                                             
/usr/src/linux/drivers/acpi/acpica/tbxface.c:712: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/tbinstal.o: In function `acpi_tb_set_table_loaded_flag':                                        
/usr/src/linux/drivers/acpi/acpica/tbinstal.c:616: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/tbutils.o: In function `acpi_tb_tables_loaded':                                                 
/usr/src/linux/drivers/acpi/acpica/tbutils.c:153: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/tbfind.o: In function `acpi_tb_find_table':                                                     
/usr/src/linux/drivers/acpi/acpica/tbfind.c:70: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/tbfadt.o: In function `acpi_tb_create_local_fadt':                                              
/usr/src/linux/drivers/acpi/acpica/tbfadt.c:277: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/tbxfroot.o: In function `acpi_tb_scan_memory_for_rsdp':                                         
/usr/src/linux/drivers/acpi/acpica/tbxfroot.c:236: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utalloc.o: In function `acpi_ut_validate_buffer':                                               
/usr/src/linux/drivers/acpi/acpica/utalloc.c:201: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utdebug.o: In function `acpi_ut_dump_buffer2':                                                  
/usr/src/linux/drivers/acpi/acpica/utdebug.c:524: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/uteval.o: In function `trace_kmalloc':                                                          
/usr/src/linux/include/trace/events/kmem.h:47: multiple definition of `acpi_gbl_copy_dsdt'                          
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utinit.o: In function `acpi_ut_subsystem_shutdown':                                             
/usr/src/linux/drivers/acpi/acpica/utinit.c:112: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utmisc.o: In function `acpi_ut_validate_exception':                                             
/usr/src/linux/drivers/acpi/acpica/utmisc.c:76: multiple definition of `acpi_gbl_copy_dsdt'                         
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utxface.o: In function `acpi_purge_cached_objects':                                             
/usr/src/linux/drivers/acpi/acpica/utxface.c:501: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utcopy.o: In function `trace_kmalloc':                                                          
/usr/src/linux/include/trace/events/kmem.h:47: multiple definition of `acpi_gbl_copy_dsdt'                          
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utdelete.o: In function `acpi_ut_delete_internal_obj':                                          
/usr/src/linux/drivers/acpi/acpica/utdelete.c:73: multiple definition of `acpi_gbl_copy_dsdt'                       
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utglobal.o: In function `acpi_ut_hex_to_ascii_char':                                            
/usr/src/linux/drivers/acpi/acpica/utglobal.c:230: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utmath.o: In function `acpi_ut_divide':                                                         
/usr/src/linux/drivers/acpi/acpica/utmath.c:290: multiple definition of `acpi_gbl_copy_dsdt'                        
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here                  
drivers/acpi/acpica/utobject.o: In function `acpi_ut_valid_internal_object':                                        
/usr/src/linux/drivers/acpi/acpica/utobject.c:306: multiple definition of `acpi_gbl_copy_dsdt'                      
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here
drivers/acpi/acpica/utstate.o: In function `acpi_ut_push_generic_state':
/usr/src/linux/drivers/acpi/acpica/utstate.c:104: multiple definition of `acpi_gbl_copy_dsdt'
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here
drivers/acpi/acpica/utmutex.o: In function `acpi_ut_release_mutex':
/usr/src/linux/drivers/acpi/acpica/utmutex.c:291: multiple definition of `acpi_gbl_copy_dsdt'
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here
drivers/acpi/acpica/utresrc.o: In function `acpi_ut_validate_resource':
/usr/src/linux/drivers/acpi/acpica/utresrc.c:367: multiple definition of `acpi_gbl_copy_dsdt'
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here
drivers/acpi/acpica/utlock.o: In function `acpi_ut_release_write_lock':
/usr/src/linux/drivers/acpi/acpica/utlock.c:172: multiple definition of `acpi_gbl_copy_dsdt'
drivers/acpi/acpica/dsfield.o:/usr/src/linux/drivers/acpi/acpica/dsfield.c:218: first defined here
make[4]: *** [drivers/acpi/acpica/acpi.o] Error 1
make[3]: *** [drivers/acpi/acpica] Error 2
make[2]: *** [drivers/acpi] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.31.12'
make: *** [debian/stamp/build/kernel] Error 2

```

---

### Post by rampage355 on 2010-04-17
I followed you steps to the letter, when at the console and i run your command sudo /home/someuser/Downloads/NVIDIA-Linux-x86_64-195.36.15-pkg2.run
I get "sudo /home/someuser/Downloads/NVIDIA-Linux-x86_64-195.36.15-pkg2.run: command not found". Am i missing something else?

Thanks

---

### Post by rampage355 on 2010-04-17
I did replace someuser with my user name :)

---

### Post by wiltk on 2010-04-17
> **rampage355 said:**
> I followed you steps to the letter, when at the console and i run your command sudo /home/someuser/Downloads/NVIDIA-Linux-x86_64-195.36.15-pkg2.run
I get "sudo /home/someuser/Downloads/NVIDIA-Linux-x86_64-195.36.15-pkg2.run: command not found". Am i missing something else?

Thanks

Try adding a period before the first slash in the command. i.e. sudo ./home/blahblahblah

---

### Post by rampage355 on 2010-04-17
Thanks, forgot to report back. it ended up being the permissions of the file, was not set for executable, having major issues with the wireless drivers it keeps disconnecting, even randomly locking the laptop up completely its a Realtek Semiconductor Co., Ltd. Device 8172, I have verified this by turning off wireless networking and have not had any issues. I did not see anything in the log files to give me a clue as to why. Any help would be appreciated.

---

### Post by DimitriLW on 2010-04-18
> **wiltk said:**
> I think I ran into this same problem on my installs on the A505-s6035.  The solution was that I needed to actually be using a root shell (i.e. sudo su), and not just sudo the *make install* command.

I am having the same issue on my A505-6033.

Here's what I did (and I *did* replace 'someuser' with my directory name):
```

cd /home/someuser/Downloads
sudo su
sudo tar xvzf rtl8192se_linux_2.6.0015.0127.2010.tar.gz
cd rtl8192se_linux_2.6.0015.0127.2010
sudo make
sudo make install
exit

```

Note that I decided to try it where *everything* was as root and sudo'ed, just to be extra crazy.  Nevertheless, I had the same errors as a result, which for continuity I am repasting here:
```

SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/xtam/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192'
make: *** [install] Error 2

```

Does anybody have further guidance on how to fix the error?  I really miss wifi right about now....

---

### Post by rampage355 on 2010-04-18
```
Section "Device"
        Identifier      "InternalCard"
        Driver          "nvidia"
        [COLOR="Red"]Option          "ConnectedMonitor" "DFP-0"
        Option          "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"[/COLOR]
EndSection
```

What does adding this code do? Mine seems to work just fine without adding this.

---

### Post by rampage355 on 2010-04-18
I installed the wireless drivers as root and not sudo and it seems to be doing much better.

Has anyone tested out the HDMI, eSATA port to see if those are working?
Any had any luck getting multi touch pad or the button to turn off the pad to work?

---

### Post by ndstate on 2010-04-20
> **rampage355 said:**
> I installed the wireless drivers as root and not sudo and it seems to be doing much better.

Has anyone tested out the HDMI, eSATA port to see if those are working?
Any had any luck getting multi touch pad or the button to turn off the pad to work?

Rampage355, what steps did you end up taking to get this to work?  I have tried several different ones and cant get wireless running.

---

### Post by rampage355 on 2010-04-20
Simulator reply # 26 of this post page 3 I think, I tried it as root after i already did it as sudo and it still did not work. I am pretty new to command line and did not know how to uninstall the wireless driver. So when I reinstalled I ran the wireless part all as root and have not had any problems. My problem is I want 10.4 and it wants to be stubborn lol

---

### Post by ndstate on 2010-04-21
> **rampage355 said:**
> Simulator reply # 26 of this post page 3 I think, I tried it as root after i already did it as sudo and it still did not work. I am pretty new to command line and did not know how to uninstall the wireless driver. So when I reinstalled I ran the wireless part all as root and have not had any problems. My problem is I want 10.4 and it wants to be stubborn lol

Thanks for the reply.  You did this on 9.10 64bit or 10.04 Beta 2 64 bit? I appreciate your help :)

---

### Post by rampage355 on 2010-04-21
9.10 64 bit and it worked great per the post from Simulator, except for the sudo issue with the wireless. Now I just need my power management for my laptop.

---

### Post by rampage355 on 2010-04-23
Has anyone updated there kernel from 2.6.31-20 to 2.6.31-21 on 9.10 64 bit, if so what issues have you had?

---

### Post by Wanas on 2010-05-03
In my plan is this laptop but when I read this thread I got confused I cant use windows any more, so please tell us what works and what doesnt !!

---

### Post by flamesbladeflcl on 2010-05-21
Okay I've been away for this thread for a while and mostly gave up on it, but last night I tried to go ahead and see if I could get 10.04 to install. I tried using wubi and I think I managed to install it. The Display didn't work during the install process but I just waited long enough and the laptop turned itself of then when I turned it back on the ubuntu option in windows bootloader switched from saying something about an installer to a regular grub menu. The problem is the graphics still don't work. I tried doing the recovery mode option and it worked fine for a while said something about an irq then went to black and stayed that way. I see people have gotten linux to install so it is workable if not perfect but I can't even seem to manage that. any help?

---

### Post by marleyfan68 on 2010-05-22
I am replying to this post from my "mostly fully functioning" Toshiba A505, core i7, 6GB RAM; running Ubuntu 10.04.  Aside from power-management (laptop battery) issues (i.e. I can run off of the battery, but have no way yet to tell how much "power" is left in it - gotta figure that one out!), everything seems to be working fine (wireless [ok], USB [ok], webcam [ok], vmware workstation 7 [ok]).

I booted and installed from the Live CD version (10.04) with the "noapic" and "nomodeset" added to the kernel boot parameters.  After the initial installation and prior to rebooting for the first time, I added the same boot parameters (noapic & nomodeset) to /boot/grub/grub.cfg; reboot went fine and I ended up with a working system (PAE kernel) but only 800x600 resolution.

Next task; installed the proprietary Nvidia graphics driver and rebooted (left the added boot parameters [see above] in /boot/grub/grub.cfg).  Reboot resulted in a working system with 1366x768 resolution [yeah]!

Next task; sudo apt-get update && apt-get upgrade [followed by reboot].  All is working well, just gotta figure out the battery/power management problem (or find out where it is already posted).

So far so good, very happy with things at this point; when I first purchased it Windows 7 & Office 2007 kept crashing on the laptop, so I made the switch to an Ubuntu base and Win XP Pro in a virtual machine for my "windows only apps."

marleyfan68:P

---

### Post by flamesbladeflcl on 2010-05-22
> **marleyfan68 said:**
> ...I booted and installed from the Live CD version (10.04) with the "noapic" and "nomodeset" added to the kernel boot parameters.  After the initial installation and prior to rebooting for the first time, I added the same boot parameters (noapic & nomodeset) to /boot/grub/grub.cfg; reboot went fine and I ended up with a working system (PAE kernel) but only 800x600 resolution.

Next task; installed the proprietary Nvidia graphics driver and rebooted (left the added boot parameters [see above] in /boot/grub/grub.cfg).  Reboot resulted in a working system with 1366x768 resolution [yeah]!...

Mind a few more detail (Ie step by step instructions) on how to do that? I'm new at linux terminal, and am not sure how to add the noapic and nodeset options to the kernel boot peramiters.

---

### Post by marleyfan68 on 2010-05-22
Sure, my apologies!

As the Live CD starts to spin, hit the ESC key once (this worked for me to make sure it didn't get stuck in graphics hell with the initial splash screen!); this will ensure that you can enter the right boot parameters.  You "enter" the right boot parameters from the Live CD by hitting F6 and selecting the "noapic" and "nomodeset" options prior too hitting enter to initiate the full boot process.

Once Ubuntu fully boots and you have a "working system", install as per the normal procedure utilizing the "install" icon that will be on the desktop.  Once the install procedure has completed, DO NOT reboot yet, click the "continue using Ubuntu" option (forget what is called exactly!).

Next - open a terminal window - found under the Applications -> Accessories "menu options"

Next - at the prompt (in the terminal window) enter the following commands; 

1) sudo mkdir /mnt/tmp
2) sudo mount /dev/sda1 /mnt/tmp [note: /dev/sda1 is the hard drive partition where /boot is located on my laptop's hard-drive - > you could make sure that you note during the install on what partition you put /boot (it would be part of the / partition unless you partitioned /boot separately; default partitioning should put /boot on the / partition and so your "/dev/sda1" will likely either be the same, or possible /dev/hda1)
3) sudo vi /mnt/tmp/boot/grub/grub.cfg (when the file opens for editing, find the first line that looks like the one below)

linux   /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=9c4ead3c-5b2a-4d6f-b91e-89da84958237 ro quiet splash

- add - - > noapic nomodeset after the word splash  (insert option in the vi editor is initiated with the "i" key)

when you finish inserting the boot parameters, the line should look something like this:

linux   /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=9c4ead3c-5b2a-4d6f-b91e-89da84958237 ro quiet splash noapic nomodeset

- if it does, then hit the ESC key and then :wq! (this will close the file and retain your edits)

4) sudo reboot (at the terminal command prompt)

voila, should boot to a working system and then you should be able to add the proprietary Nvidia driver and get the resolution the laptop is capable of.

let me know if you need more help!  - marleyfan68

---

### Post by flamesbladeflcl on 2010-05-25
alright it looks like it is working. I don't have a battery meter either

---

### Post by nights815 on 2010-06-02
I will give my experience. i have a toshiba a505-s6025. kubuntu and ubuntu 9.10 32 and 64bit installs fine. 9.4 and under fails during install. and 10.4 isn't compatible with the videocard. i ran 10.4 on my desktop at same time as installing a fresh copy on the laptop and the disk drives operate the same time when i use the menu options.. just no video at all. but installing 9.10 then upgrading to 10.4 works but i must use 800x600 since nvidia drivers crashes. video works fine on 9.10 at 1366x768 but without nvidias drivers. and the realtek wifi dosnt work on any version. but lan works fine. used linux drivers and ndiswrapper installs fine just dosnt allow wifi. much of this i think is related to motherboard chipset issues. the led buttons on top work except for eco button. sound works. hdmi works both audio and video. the mouse on/off button dose not work. webcam works and no battery indicator on any version.

---

### Post by slushpuppisan on 2010-06-18
Hey guys,

Has anybody gotten Lucid to work with the version 1.3 BIOS? I followed MarleyFan's instructions but it still wouldn't boot, so I made the very poor decision (in hindsight) to update the bios since the release notes said something about fixing the USB on Acronis Linux. Now I can't even run Ubuntu from the CD with noapic and nomodeset options. 

I'd really rather not re-downgrade the BIOS unless absolutely necessary. If anyone has any tips it would be much appreciated. The last few lines of text I get before it quits altogether are:

[1.044329] [<c07a32f8>] do_basic_setup+x47/0x57
[1.044467] [<c07a3376>] kernel_init+0x6e/0xbf
[1.044603] [<c07a3308>] ? kernel_init+0x0/0xbf
[1.044731] kernel_thread_helper+0x7/0x10

I'm going to search kernel_thread_helper in the forum and see if I can figure anything out on my own. I'll let ya know back here.

---

### Post by slushpuppisan on 2010-06-18
Actually, nevermind. ACPI was automatically turned off when I first installed Ubuntu from the live CD, when I tried the live CD this time I guess it wasn't for some reason. Adding acpi=off to the boot options let me boot off the hard disk, and USB appears to be working already (just in case that matters to anyone).

---

### Post by jromma on 2010-06-18
So I've spend the past couple days trying to figure out how to install 10.04 (amd64) on my A505-S6035. Like slushpuppian, I also upgrade the BIOS to 1.3 (possibly a huge mistake?). I had to include the following boot options to get it to install:

acpi=off noapic nolapic pci=noacpi irqpoll nomodeset

I had to include the same boot options to run ubuntu after I installed it, and I also had to include the "text" boot option, because it would make it to the login screen, but the login screen would be broken and not allow you to login. fyi, it wouldn't run off of a usb stick, only the cdrom. So, after doing this I followed the instructions in this guide: 
[http://ubuntuforums.org/showthread.php?t=1503491&highlight=toshiba+a505](http://ubuntuforums.org/showthread.php?t=1503491&highlight=toshiba+a505)
only using the command line interface, and by transfering the patched kernels to my hard drive via running ubuntu off the startup disk (which still recognized usb devices) and then compiling them. it was a huge pain, but its finally sort of working now. The login screen issue still persists, so I have to boot with text and then run the command "startx". The catch is, ubuntu doesnt recognize any of my disk drives or usb devices. When I try to access something that requires them (like startup disk creator), I get the error "An error occurred talking to the udisks service". I'm about to try installing the drivers for the wireless card. The only non-standard boot options I have are "text" and "acpi=copy_dsdt". How do you guys think I should go about fixing this problem?

---

### Post by jromma on 2010-06-19
actually, nevermind. it turns out i messed with the permissions too much, and it messed things up. doing a complete reinstall with just the above boot options allows it to install and boot normally, and my usb works now. perfect! installing the new kernel and booting with acpi=copy_dsdt fixes everything now. all i have left is getting wireless to work. when installing the drivers from realtek's website, it exits with errors. any suggestions?

---

### Post by jromma on 2010-06-19
got the wireless drivers on realtek's website to work for my computer, it turns out you have to do:
```

sudo su
make
make clean
make install

```

then reboot. "make clean" wasn't included as a necessary command for installation in the readme. weird. anyways, my a505-s6035 is now fully functional! woooo! so stoked. as someone before me said, its waay too nice of a computer to just run windows on

---

### Post by slushpuppisan on 2010-06-20
Thanks for the link Jromma, using the new ubuntu kernel was a heck of a lot easier than compiling my own, and the biggest upside was that it actually worked. I'm in about the same situation you are now. Has anyone had any luck installing the newest Nvidia drivers? I have a 310m (in an A505-S6033) and installing from Ubuntu hasn't worked (or maybe just needs some configuration?) and neither has following the instructions from earlier in this thread on installing using the driver downloaded from Nvidia. I'm going to try an older one. Right now I'm working in 32-bit but I'm going to get the new kernel on my amd64 install here soon too so let me know if you've had better luck with it. One last question: When I unplugged my computer for the first time the battery meter estimated I only had about a total of 1 hour battery life, what have others been getting? I have the 4400 mWhr battery, or whatever it is.

For anyone new viewing this thread with the same problems we've been having, I highly recommend installing the .35-rc1 kernel as per Jromma's link.

---

### Post by slushpuppisan on 2010-06-20
Okay, this is interesting, I tried installing the NVidia .31 driver by  booting with the text option and running it on the command line. I got  an error saying that the version of gcc I'm compiling with probably  needs to match the version used to compile the kernel. I have gcc-4.4,  apparently the kernel was compiled with gcc-4.2, and 4.2 is not in the  repository. Any ideas?

I just tried the .15 version mentioned earlier and it doesn't work either. I should also note that at the start the "distribution provided" pre-install script fails (with both installers I've tried).

---

### Post by slushpuppisan on 2010-06-20
Installing the Nvidia drivers in 64-bit using the gnome "hardware drivers" utility worked, and installed version 195.36.24. Maybe I just broke the config in 32-bit from all my playing around?

---

### Post by Breeegz on 2010-06-26
I have a Toshiba A505 (dunno the dash number, but I don't think it's a s6033.  PN is PSAT9U-0KQ007)i7-720, Bluray, Nvidia and such..  

I'm gonna try the Live CD tomorrow, see what happens.  Wish me luck.

---

### Post by Breeegz on 2010-06-27
> **Breeegz said:**
> I have a Toshiba A505 (dunno the dash number, but I don't think it's a s6033.  PN is PSAT9U-0KQ007)i7-720, Bluray, Nvidia and such..  

I'm gonna try the Live CD tomorrow, see what happens.  Wish me luck.

The live CD (32 Bit Desktop) didn't really like my laptop, I didn't pay much attention to it, but it never loaded..

---

### Post by Euboon2 on 2010-07-25
I just installed Ubuntu 10.04 on my wife's Toshiba A665-S6065 laptop, which comes with an i7 processor, nvidia GT 330M, and realtek wifi. Most things seems to work. On first boot into gnome, it automatically offered to install propriety drivers for the wifi and nvidia.

Although there is an applet that monitors the cpu usage, I don't really know if everything is really fine. When I tried running "sudo sensors-detect", it says that the hardware is too new. Can someone tell me what application can be used for monitoring the cpu, hard-disk... temperatures? 

Suspend and hilbernate work. Most of the function buttons also work out of the box. USB works. etc etc etc...

When I went through the "system test" (fromgnome menu), I was very impressed that everything works (apart from a few tests that I skipped, e.g. I don't have a DVD movie disk, external microphone etc for testing).

All in all, ubuntu on the laptop seems to function really well, contrary to almost everything I read on the web about installing linux on i7 laptops. So, I wrote this so that others who have an i7 laptops but are hesitating to install linux, may be tempted to do so. My only reservation is whether the cpu might be too hot, so this is part of the reason for this post. (The warm air blowing out of the vent is slightly warmer than my 2.1GHz core 2 duo laptop, also a bit warmer than when running windows 7 on this i7 laptop.)

**Details of the installation:**
-- (Didn't try to install ubuntu-desktop directly from CD, due to my initial concern from reading the difficulties of attempts by others.)
-- (Didn't managed to install propriety nvidia driver manually, i.e. keep getting error. Eventually re-installing all over again as detailed below. Anyway the standard ubuntu-desktop install seems to handle that.)
-- Install a command line system
-- On first boot, dpkg -i 2.6.35rc1 kernel (not exact name of the deb files)
-- On reboot, apt-get  update, apt-get upgrade, apt-get install build-essential, then compile and make install wifi driver from realtek website, and finally apt-get install ubuntu-desktop.

Update: Installed version is amd64, also didn't manually change any boot parameter

---

### Post by soad6 on 2010-08-18
ok im running 9.10 on my i7 satellite a505 s6033... the only issues i have are no wifi, battery displays wrong charge information( i think), and when i plug in my external harddrive to the usb it isnt recognized... im upgrading to 10.04 in hopes that this will fix the issues. also i have a question with booting in noapci what does that do exactly? is that going to make the computer not use all 4 cores or something or is it something minor that i shouldnt worry to much about??
](*,) where's the entrance?

---

### Post by soad6 on 2010-08-18
ok so trying to upgrade from 9.10 to 10.04 totally failed...got stuck with a black screen and a command prompt. so not sure what to do, are there any work arounds to upgrading the system to 10.04 or will i have to wait til 10.10 before i upgrade?? thanks for any advice... i will fix my wifi issue with the drivers i found but as for usb not recongizing my hard drive im still not sure what to do here either... thanks.
](*,) where's the entrance?

---

### Post by soad6 on 2010-08-23
ok so there is no way that you can get 10.04 to work on this from the live cd it just hangs after a few minutes. even with noapic and nomodeset. Sorry but it doesnt work, also 10.10 doesnt fix anything at this moment because it will load to a certain point and then hang. This is really annoying because i really miss linux and VMware doesnt do it justice! this sux someone please help fix the issues!
](*,) where's the entrance?

---

### Post by rigsc on 2010-08-23
There is a fix in kernel 2.6.35.  I don't know when Ubuntu will get there.  In the meantime Toshiba released a BIOS update for this laptop (1.30).  It might help.

---

### Post by Euboon2 on 2010-08-27
soad6,

If you have a spare partition (or shrink your current partition and create a new one with the unpartitioned space), I would suggest that you try installing 10.04 in it just for testing (try what I did if standard installation don't work). And delete or ignore the new partition if the new installation fails.

A665-S6065 has very much the same spec as S505-S6033, perhaps with updated bios (and perhaps updated drivers for the windows 7). So I think what I did might apply to you (but no certainty). See [http://ubuntuforums.org/showthread.php?t=1503491&highlight=toshiba+a505](http://ubuntuforums.org/showthread.php?t=1503491&highlight=toshiba+a505) for more details. The linux wireless driver you need is probably on the manufacturer website.

So far, it runs cool when the laptop is used for normal web surfing. But the air coming out of the vent is quite warm when viewing youtube video.

Append:

Usb works for me (e.g. external camera, usb thumbdrive, and harddisk detected), but so far haven't plugged in the battery.

I also experience freezing while booting up (but very rarely: read on...). The first time that happened, I press ESC after rebooting so that the purple screen switches to the normal black screen (like those boot up screen without splash) and I can see what is going on. I realize that the OS is actually automatically running fsck (file system check). I waited for some time and it eventually continued to the gnome log-in screen. So when freezing happens again, I know it's actually doing a check on one of the partitions, and simply wait for it to finish what is neccesary. The purple ubuntu screen should notify user of this, then I would not have mistaken it for a system hang. Not sure if this applied to you.

---

### Post by soad6 on 2010-09-16
sorry for not replying to my thread soon enough... i got the problem fixed, turns out that its supported as of 10.10, there is no way to get 10.04 to run because of something with the nvidia card handling the irq wrong, so the only thing i can suggest is that if you run a i7 satellite a505 s6033 then wait til october unless you wanna deal with all the muckyness of multiple hanging after loading, or hanging while trying to reboot. It can be loaded, but you have to turn off acpi and nomodeset and apci, then press F6 and you should be able to get it to load but you will still possible have it lock up while loading the partition system. Just better luck with waiting, or install the beta as its out right now, and thats what im using.
Take it from me its so much easier to just run the beta and do a few upgrades to fix stuff.

[-X If someone says it can't be done, then they haven't tried Linux yet!

---

### Post by soad6 on 2010-09-16
oh and also, another thing, if you did manage to install a previous version on your system but still having heating issues or problems with the acpi support, then upgrade the kernel to 2.6.35-22 or whatever the current new kernel is since as of 2.6.35-19 we have full acpi support including battery, thermal, and other. However if you still have an issue with your wifi card the RTL8191sevB I am sorry to report that it still is buggy even in ubuntu 10.10. Not sure what the reasoning behind this is, but hopefully it will get fixed soon. 

[-X If someone says it can't be done, then they haven't tried Linux yet!

---

### Post by Scienceman123 on 2010-11-02
I tried the newest kernel, but it hangs on the "Kubuntu" screen with the progress dots under it.

---

