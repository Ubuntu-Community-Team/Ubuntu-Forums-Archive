---
title: "Boot problems"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by Brother_James on 2013-10-14
Hello all,

I'm in a bind with my new system. (first time Ubuntu installer)

(All brand new)
ASROCK Z87 EXTREME4 1150 SERIES MOTHERBOARD
i7 CORE 3.4GHZ HASWELL 4470 Intel PROCESSOR
2 KINGSTON 4GB DDDR RAM
1 KINGSTON 128GB SSD V300

USB/ubuntu-13.04-desktop-amd64.iso 
DVD/ubuntu-13.04-desktop-amd64.iso

ASROCK Tech Support stated my bios confiq, system boot sequence and sata connection are correct.

I get Black screen with flashing cursor top left corner. USB boot attempt. (2.0 port)
I get "Press any key to continue" message. DVD boot attempt.

ASROCK Bios has a shell option in which I had to download .efi file and rename it shellx64.efi
Finally in EFI SHELL and I can see USB DIR 

fs0: .....ubunto-13.04-desktop-amd64.iso

What do I do to launch this iso file?

If anyone wants to mention GRUB or GRUB2 or any other third party stuff to mount ISO files in efi shells, please list a concise How-To and provide links to software you wish to suggest. 

Otherwise, please note that the ASROCK tech stated that the EFI SHELL is not to install operating systems, but for other functions regarding driver installs, etc., not for iso. 
 I felt that the tech spoke with confidence.

Is it that ubuntu 13.04 is not ready for what I'm throwing at it?
Do I need to wait for the soon release of 13.1 Salamander or whatever its called?

I've done enough research to know that the information provided should help resolve my issue and get me going in the correct direction.

sincerely 
Mind Blown in Michigan

P.S.
Its not a CHECKSUM issue

I went down that rabbit hole and downloaded iso multiple times...same results :(

---

### Post by fantab on 2013-10-15
What graphics card do you have?
How did you burn the .iso to DVD or USB? 
Is booting from DVD and/or USB enabled in BIOS/UEFI?
Is the HDD partitioned and formatted? What partition table does the HDD have, msdos or GPT?

---

### Post by mastablasta on 2013-10-15
since you see an .iso file it's obvious that you did not burn the image correctly to dvd: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
How to put image on USB: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
(can also use Unetbootin or LinuxLiveUSB creator)

you also need to provide info **fantab** is asking about

---

### Post by mörgæs on 2013-10-15
Next time please use a more descriptive (and less dramatic) title.
Changed.

---

### Post by Brother_James on 2013-10-15
> **fantab said:**
> What graphics card do you have?
How did you burn the .iso to DVD or USB? 
Is booting from DVD and/or USB enabled in BIOS/UEFI?
Is the HDD partitioned and formatted? What partition table does the HDD have, msdos or GPT?


FANTAB,

I'm not using any third party graphic cards, just onboard graphix. 

Maybe I should ask you how your burning .iso file unto USB and or DVD because my way isn't working. (please indicate the correct method)

Yes, Like I stated before. ASROCK Tech Support went through the bios setting and boot sequence and all is correct.

I am using an SSD and I am NOT using any other os. I just want to use Ubuntu. 

Why can't I just get Ubuntu to mount into a gui and format and or partition from that point. (like with my mac & windows computers I've build)

---

### Post by oldfred on 2013-10-15
So far everyone with the very new Haswell processors has needed the very new 13.10 that has major updates to kernel & video drivers by Intel to work with those new systems.

You need to decide if booting in the new UEFI boot mode with gpt partitioning or the 30 year old but well known BIOS/MBR boot mode. Very new hardware may work better with UEFI.

You still may need settings on live flash drive installer's grub menu and first boot grub menu for the Intel driver to configure correctly. And if only installing Ubuntu you may not get grub menu by default, but need to use shift key from UEFI/BIOS until menu appears. Some new UEFI systems need escape instead of shift.

How you boot install media is how it installs. This shows both a BIOS purple boot screen and the  grub2 UEFI boot screen. 
       [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also good to review if using UEFI and have Windows 8:
      
 [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Intel typically does not use nomodeset but other boot parameters in grub, use one of these instead of nomodeset, instuctions below on adding boot parameters in nomodeset link below.
      
 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor

      How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

     Older versions
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

---

### Post by Brother_James on 2013-10-15
guys, way too much info about everything. first, my video is fine.

second, its hard to see the purple boot screen when the Ubunto iso will not boot in to the system.

what is "grub"

what is "grub2"

why do I need grub(s)

most importantly, 
is 13.04 going to work with my computer specs or is 13.10 the only option I have.

if anyone is confused with my concern, please review my previous postings on the topic.

P.S.
This is the problem of the century and not just a boot problem.

---

### Post by oldfred on 2013-10-15
Old BIOS based systems boot from BIOS on motherboard, which jumps to MBR or very first sector of hard drive. In MBR is a boot loader. Windows has its own boot loader and Ubuntu uses grub2. Grub legacy is a now old version that would not even work with your system unless you install in in some old crippled mode.
Grub2 has two versions - grub-pc for BIOS systems and grub-efi for UEFI systems. 
Ubuntu has to have grub2 to boot. Although there are some workarounds.

BIOS is 35 years old and has had many changes but just cannot keep up with new hardware. New systems have UEFI, but for use with older hard drives or configurations it has a BIOS mode called:
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

How you boot your install media, DVD or flash drive is how it installs.

Many install with UEFI and if not dual booting with Windows, it only requires you to boot flash drive in boot mode you want to install - BIOS or UEFI. Since very new system I would suggest UEFI. 
Some that are used to BIOS,  have installed in BIOS mode on newer systems, but I am not sure many with very new hardware like yours have.

Most with Haswell have reported 13.10 works.

---

### Post by Brother_James on 2013-10-15
Thanks for the tips sir.

Currently I am working on My Intel mac Disc Utility image burning option that I have not tried yet! 

Thanks for your help, I will keep you posted on what I come up with.

---

### Post by Brother_James on 2013-10-16
Hello Again all,

Great news

It was in front of me this whole time, but everyones help crystalized it.

Finally realized that you can't just drag and drop .ISO files and expect the image to boot.
Using the disc utility installed already on my macbook allowed me to burn the .iso as an Image to DVD disc!

All is well with Ubuntu Except that I don't have any Audio from my HDMI out port.
Video is great just no audio.

In the installation process I did not check the LVT (Some kind of volume enhancement technology) box and I am wondering if that was the error of my way.

Any suggestions welcomed.

---

### Post by fantab on 2013-10-16
Glad you figured it out.

There is no LVT that I am aware of. You might be reffering to LVM and it has nothing to do with Sound Volume.

Have you checked the sound in the top bar? Sound is muted by default. If the problem persists then start a new thread with an appropriate title.

---

### Post by mörgæs on 2013-10-16
- and please mark this one 'solved' using 'thread tools'.

---

