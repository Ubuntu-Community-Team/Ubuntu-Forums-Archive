---
title: "New PC, cannot install Ubuntu (pci 0000:00:01.0: MSI quirk detected)"
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by prohacx on 2014-01-28
Hi experts,

I am having quite some trouble getting Ubuntu / Xubuntu installed on this new PC I bought.

I basically tried several options: both 32 and 64 bit versions of both Ubuntu and Xubuntu 12.04 LTS and now also tried Ubuntu 13.10 64 bit. 

I made my bootable USB using LiLi. I can get the installer to run, but when I let it do its thing it throws some text at the screen and then gets stuck at

pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled

I then tried hitting a key when the ubuntu icon shows up in the installer so I can get in the extra options. I tried using nomodeset, all sorts of combinations of acpi on and off (whatever that may mean) and also tried adding a few -- vga 791 boot options.

Nothing works. With the -- vga 791 setting it basically turns the screen black and then sits there.

This is a newly bought PC with a biostar A960D+ motherboard, 1TB SATA HDD, 4gb RAM, AMD processor.

Any advise is highly appreciated.

Thanks in advance!

---

### Post by oldfred on 2014-01-28
Do not know about your motherboard.

But all new motherboards are both UEFI with BIOS called CSM.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

The 32 bit install will only install in BIOS mode as it does not have any UEFI.

The 64 bit will install in either BIOS or UEFI mode based on how you boot it.
In UEFI menu you should have two entries for flash drive, one UEFI and the other not UEFI, but not always clear that it is BIOS boot.

vga= options have been obsolete for a while.

 vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
replace "set gfxmode=auto" by "set gfxmode=1366x768"

Most boot with nomodeset, but what video card/chip do you have?
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by prohacx on 2014-01-28
First of all thanks a lot for taking the effort to reply to my thread.

I must admit I am a little lost in all the info you (and other websites) provide.

If Ubuntu can boot in both UEFI and without, why would I need to worry about it then? What I can say reading through one of the threads you provided is that it looks from the screenshot that my installation is booting using non UEFI. I guess that is fine.
I have a completely new PC, nothing on my hard drive, so wouldn't know where/how to update /etc/default/grub. I am assuming you mean this is a file on my USB installation media, but I can't find it.

The onboard graphics card is ATI Radeon&#8482; HD3000 Graphics, On Board Graphic Max. Memory Share Up to 1024 MB

I am basically trying to understand where things are going wrong so I can find a proper solution. What are the next steps I can take to get the installation going? I did complete a few Ubuntu and Xubuntu installations before, however, those were straightforward: put in the media and go. Now I am lost :(

Your help is again appreciated.

UPDATE: I used -- video=1280x1024-24@60 as boot parameters and now get back to the text screen that stops at pci 0000:00.01.0: MSI quirk detected
Before (with --vga=791 it stopped at a black screen).
FYI - running live mode does not work either, I hadn't mentioned that before.

---

### Post by oldfred on 2014-01-28
This was just an example, is it your monitor's standard as that is what you need.
1280x1024-24@60

You have an older AMD card. You then can only use the open source drivers as AMD only supports newer cards. Or install the legacy driver. Do not install current or you may get conflicts.
 This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for several versions of Ubuntu.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

To get you into system try Radeon or Generic setting.

[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1 
[*]nVidia: nomodeset 
[*]Generic: xforcevesa or nouveau.modeset=0 
[*]Radeon: radeon.modeset=0 
[/LIST]
     
And you may still need other boot options. But that may try experimentation or find someone with similar motherboard and what they used.
 Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by prohacx on 2014-01-28
i gave your ideas a go, sadly no luck so far...

I tried xforcevesa, nouveau.modeset=0 and radeon.modeset=0 both with and without acpi=off, the only difference being that with acpi=off I get the one more line on my terminal before it hangs:
0000:00:12.0: PCI -> APIC IRQ transform: INT A -> IRQ 16

Are we even sure this is a display driver issue and not something else?

Thanks again for your help so far!

---

### Post by oldfred on 2014-01-28
It may be both or like you think just something else, but some boot parameter may make it work. 
I just do not know with your configuration what else to suggest.

Some UEFI/BIOS may also need changes to defaults in UEFI. Not sure what it may be with your system.

---

### Post by prohacx on 2014-01-31
So i read in some other posts on the internet that this MSI quirck can be worked around by seeting the USB Legacy support to disabled in the BIOS.

I did that, but now I get Checking NVRAM.. when I boot the PC and it hangs there even before getting into the Ubuntu install.

Never thought that installing an OS can be so hard... any more ideas from anyone?

Thanks in advance as always!

---

### Post by oldfred on 2014-01-31
NVRAM is where UEFI stores variables and what to boot. Not seen that error from UEFI/BIOS??

Did you turn secure boot on, and without any secure boot systems it hangs?
Do you also have Intel graphics or just the AMD? Some then boot with Intel for low power but use the video card for heavy duty applications. If booting with Intel then other settings would be required. May also be a setting in UEFI/BIOS.

---

### Post by prohacx on 2014-02-01
Oldfred, I want to thank you for your tireless effort to help me with resolving this issue. I am very grateful that people like you are available to the community to support noobs like myself :D

I am posting this from my new Xubuntu install, so it seems we finally managed to get things working!!!

Here is a recap from the steps I took that (I think) lead to the resolution:
- (Obviously) go through the posts provided by Oldfred, tried out several options
- I found some info pointing towards USB legacy support and MSI quirk
- Disabled legacy support in my BIOS
- Got that Checking NVRAM error
- Reset my CMOS (through the jumper setting described in my motherboard manual)
- Disabled legacy support again, checked some other BIOS settings to make sure they are what they were before resetting the CMOS
- Set my CD/DVD up as primary boot device (in BIOS)
- Used a (X)Ubuntu installation CD instead of a USB (as legacy support is now disabled)
- Up till this point I still had that Checking NVRAM error at POST. 
- Almost went out to buy a new motherboard, gave it one more try by unplugging my USB keyboard and mouse, booting with Xubuntu installation CD (12.04.3 LTS)
- BINGO! Installation starts!!!
- During installation, plug back in my USB keyboard and mouse
- Let it complete
- Restart is needed in order to complete installation
- Had some more issues after that with keyboard not working in GRUB menu
- Somehow magically ended up in my BIOS again (by using the DEL key during boot)
- Enabled USB legacy support
- Reboot
- Finally able to have Xubuntu boot again, login, install latest updates, working instllation!

I am hoping that I described all this in enough detail so that it can help others with similar issues.

In the end it seems that when you get that MSI quirk error, disabling USB legacy support in your BIOS goes a long way. That Checking NVRAM error is (or looks to be) because you still have USB devices plugged in when USB legacy support is disabled.

So resetting the CMOS may not have been necessary after all. I did not have a PS/2 keyboard/mouse available, but probably disabling legacy USB support in the BIOS and using PS/2 keyboard+mouse would have worked directly.

I do not know if the Ubuntu developers want/can do anything about this conflict, but it did take quite a while for me to get an OS installed, so I can only hope people with this same issue are helped by this thread.

Thanks again to this great community!!!

---

### Post by prohacx on 2014-02-03
One small addition: you may not get to the MSI quirk error and stay atuck at a blinking cursor screen. My ubuntu installation media was somehow running without the quiet option so that's why I got that MSI quirk error visaully on my screen. When you get stuck during installation at the blinking cursor screen then this may be another potential solution for your problem (disable legacy USB support and retry the installation from a CD/DVD instead of a USB stick). To check if you are in this situation, go into the ubuntu installation (by pressing any key when the icon on the bottom shows) and remove the quiet from the boot parameters (press F6 then escape then in the boot parameters remove quiet if you have it there)

---

