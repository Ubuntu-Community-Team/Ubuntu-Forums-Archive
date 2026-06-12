---
title: "Can't Start Install"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by ichilton on 2011-09-14
Hi,

I've got an machine that I want to use Ubuntu on but I just can't get the install to start.

Debian installs and works fine.

I've tried Ubuntu 10.10 and 11.04 - same problem.
I've tried 32-bit and 64-bit - same problem.

When I try the normal CD, it boots from the CD, shows a screen with a symbol on the bottom (looks like a keyboard = little man) and then goes to a black screen with a flashing cursor at the top left and stays like that forever.

When I try the alternate CD (which I believe is a text based install?), it boots to a graphical screen to pick the language, I hit enter and it goes to a black screen and sits there forever.

It's an AMD Sempron 3400+ in a Gigabyte GA-MA69VM-S2 motherboard with an onboard ATI X1500 graphics card.

Here is the motherboard spec:
[http://uk.gigabyte.com/products/product-page.aspx?pid=2500#sp](http://uk.gigabyte.com/products/product-page.aspx?pid=2500#sp)

I've also tried a PCI graphics card and that didn't help.

Any ideas?

Thanks,

Ian

---

### Post by mörgæs on 2011-09-14
It sounds like you need boot options. There are links explaining how in this post:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by ichilton on 2011-09-15
Hi,

Thanks for that - I played with the various boot options and setting the "acpi=off" made it boot into the install normally and the install completed successfully.

Any idea why that would be?

However, now it's finished the install and tried to boot, I get a similar problem to the install but I dont really want to use acpi=off all the time as I want it to be as power efficient as possible.

Any ideas?

Thanks,

Ian

---

### Post by Hakunka-Matata on 2011-09-15
> **ichilton said:**
> Hi,

Thanks for that - I played with the various boot options and setting the &quot;acpi=off&quot; made it boot into the install normally and the install completed successfully.

Any idea why that would be?

However, now it's finished the install and tried to boot, I get a similar problem to the install but I dont really want to use acpi=off all the time as I want it to be as power efficient as possible.

Any ideas?

Thanks,

Ian

 Check to see if there are any **Additional drivers or Hardware drivers** waiting to be downloaded.  System > Administration > Additional drivers  and often the icon for additional drivers appears upper right hand corner by the clock if they are available.

---

### Post by ichilton on 2011-09-22
Hi,

I booted with acpi=off but there are no additional drivers to install. I also did a dist-upgrade while I was in there but it still won't boot without acpi=off.

I found this page: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)
So I started going through the list of paramters and the 3rd one down is the one which makes it boot - pci=noacpi.

If I use pci=noacpi then it consistently boots.

Is there a disadvantage to booting with that? - will it affect the power saving/consumption? will it impair the use of PCI cards?

Any ideas how I can get it to boot without it?

I've had a look through the BIOS settings and tried changing a few but it doesn't seem to have an effect.

Thanks,

Ian

---

### Post by dino99 on 2011-09-22
you said "i've got a machine", well its not very usefull :(
look at synaptic to install custom acpi if your "machine" is acer or asus (google around: ubuntu+yourmodel /acpi+yourmodel)

but sadly there is a bunch of acpi issues related to linux. If you dont have such trouble with debian, then look at ubuntu custom settings (blacklist, ...) and watch your logs of course.

maybe add acpi:debug to the boot line, then watch the log. Maybe your bios have several acpi settings to tweak.

---

### Post by ichilton on 2011-09-22
Hi,

When I said a machine, it's a motherboard sat on the table with a power supply and hard disk connected! - so it's not a brand name.

Thanks for the suggestions.

Ian

---

### Post by Linux_junkie on 2011-09-22
You could try and resolve the problem with the help of the forum or as you said you didn't have a problem with Debian why not stick with that.  Debian is a very stable distribution of Linux and works the same way as Ubuntu (Ubuntu is based upon Debian).

---

### Post by leodan on 2011-10-17
> **ichilton said:**
> Hi,

I've got an machine that I want to use Ubuntu on but I just can't get the install to start.

Debian installs and works fine.

I've tried Ubuntu 10.10 and 11.04 - same problem.
I've tried 32-bit and 64-bit - same problem.

When I try the normal CD, it boots from the CD, shows a screen with a symbol on the bottom (looks like a keyboard = little man) and then goes to a black screen with a flashing cursor at the top left and stays like that forever.

When I try the alternate CD (which I believe is a text based install?), it boots to a graphical screen to pick the language, I hit enter and it goes to a black screen and sits there forever.

It's an AMD Sempron 3400+ in a Gigabyte GA-MA69VM-S2 motherboard with an onboard ATI X1500 graphics card.

Here is the motherboard spec:
[http://uk.gigabyte.com/products/product-page.aspx?pid=2500#sp](http://uk.gigabyte.com/products/product-page.aspx?pid=2500#sp)

I've also tried a PCI graphics card and that didn't help.

Any ideas?

Thanks,

Ian

Hi,

 I have exactly the same problems with my PC which has GA GA-MA69VM-S2 F8 mother board. I tested various distributions - only Ubuntu 8.04 works. Can't install any other newer distribution doesn't matter 32 or 64 bits. Same results with Fedora 15. Any ideas?

---

### Post by mörgæs on 2011-10-18
Please give some more hardware information.

Memory?
Chipset?
Screen card?

---

### Post by mastablasta on 2011-10-18
> **leodan said:**
> Hi,
 
I have exactly the same problems with my PC which has GA GA-MA69VM-S2 F8 mother board. I tested various distributions - only Ubuntu 8.04 works. Can't install any other newer distribution doesn't matter 32 or 64 bits. Same results with Fedora 15. Any ideas?
 
 
also have you tried debian (or if you like more stuff preconfigured like in Ubuntu try Chrunchbang)? as OP suggested Debian worked well.
 
It seems newer ubuntu lost the ability to boot on soem a bit older systems. I am also not sure why this happened. I see that my CPU is compatible but the boot just doesn't happen. funny thing is that upon using the PLOP boot manager it all booted normally. (ok this *might* be a different issue).

---

### Post by leodan on 2011-10-28
Hi,

Yepp, It works with Debian 6.0.3  without any problems. Tried Mint 11 - fails. So rule of thumb  would before attempting to install or more importantly to upgrade your Linux machine try live CD or USB first - if fails to run most likely you will have a problem during installation or the upgrade.

---

### Post by Hakunka-Matata on 2011-10-28
> **leodan said:**
> Hi,

Yepp, It works with Debian 6.0.3  without any problems. Tried Mint 11 - fails. So rule of thumb  would before attempting to install or more importantly to upgrade your Linux machine try live CD or USB first - if fails to run most likely you will have a problem during installation or the upgrade.

Your methodology would seem sound at first glance, but the way I understand the problem your 'rule of thumb' is not foolproof because the liveCD/USB graphics drivers/setup is different from an installed Ubuntu system's method of setting up the graphics drivers.  Often times, lately at least, the liveCD/USB graphics might work fine, but when booting for the first time from the HD, new installation, graphics fails as a different set of video parameters are loaded trying to use properly whatever graphics chipset your hardware uses.  So there is to my knowledge, no sure way of knowing in advance whether or not there will be graphics issues after the system is installed to hard disk.
It's not exactly easy or apparent always, that the problem one might experience on first boot after install, is a Grub/bootloader problem or a graphics problem.  Messing around with the boot parameters (if a graphics problem is suspected - like blinking cursor upper left hand corner on a black background (nomodeset, acpi=off, etc.)) or a Grub/bootloader problem, must be sussed first.  If you suspect a graphics problem, change boot line, add parameters, if one suspects a Grub/bootloader problem, run the boot_info_script.sh bash shell program and post the RESULTS**x**.txt file it produces.

**EDIT: **If you're willing to 'play around' a little bit, do me a favor and execute the "justdoit.sh" file:  It's not dangerous, it's nothing more than a really, really, simple script file that:
[LIST]
[*]downloads,
[*]extracts,
[*]and runs the file named "boot_info_script.sh".
[*]It generates the RESULTS.txt file in a directory named ~/Downloads/bootinfoscriptfiles.
[*]It copies the RESULTS.txt file to the Desktop, and then opens it with Gnome's gedit program.
[/LIST]
  Hopefully.

Using whatever **directory** you download the justdoit.sh script file to execute it with following command:```
sudo bash **directory/**justdoit.sh
``` I'm a **real** novice at writing scripts, as you will see if you edit the "justdoit.sh" file.  But if you do run it, and it works for you, once you are in gedit, editing the RESULTS.txt file: then highlight and copy the entire text of the file into a fresh reply, enclosed in code tags,click on the #icon to enclose the entire pasted, highlighted, text with code tags.

---

### Post by MAFoElffen on 2011-10-28
> **ichilton said:**
> Hi,

I booted with acpi=off but there are no additional drivers to install. I also did a dist-upgrade while I was in there but it still won't boot without acpi=off.

I found this page: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)
So I started going through the list of paramters and the 3rd one down is the one which makes it boot - pci=noacpi.

If I use pci=noacpi then it consistently boots.

Is there a disadvantage to booting with that? - will it affect the power saving/consumption? will it impair the use of PCI cards?

Any ideas how I can get it to boot without it?

I've had a look through the BIOS settings and tried changing a few but it doesn't seem to have an effect.

Thanks,

Ian
Yes there "are" disadvantages. 

I'll give you the workaround for this here... Use this sticky, post 1 for reference: 
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

but I'll sumarrize everything tailored for your problem right here.

1. Boot [COLOR=Teal]temporarily[/COLOR] using a "acpi=off" or "nopci" or yours mentioned above... all those "are" the same option.

2. Go to a terminal session.

3. Install hwinfo (small graphics utility)
```

sudo apt-get install hwinfo

```4. Find the modes of your video card:
```

sudo hwinfo --framebuffer

```It should have ouput simlar to this
```

02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.WzmqMIsndrA
  Hardware Class: framebuffer
  Model: "NVIDIA G92 Board - 03920051"
  Vendor: "NVIDIA Corporation"
  Device: "G92 Board - 03920051"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xd5000000-0xd5dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
[COLOR=Red]  Mode 0x0318: 1024x768 (+4096), 24 bits
[/COLOR]  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```Its pretty safe to assume that most monitors in the last 5 years have 1024x798 at 24bit color. So if I look at this line:
```

[COLOR=Red]  Mode 0x0318: [COLOR=Green]1024x768[/COLOR] (+4096), [COLOR=Green]24 bits[/COLOR]
[/COLOR]
```I copy down the hex number "[COLOR=Red]0x0318[/COLOR]"...

5. Open /etc/default/grub for edit with previledges:
```

gksudo gedit /etc/default/grub

```6. First Line you are looking for says:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vt.handoff=7"

```Change it to this
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=[COLOR=Red]0x0318[/COLOR] vt.handoff=7"

```7. Next line you looking for in this file is
```

#GFXMODE=640x480

```Change it to match the resoltuion your picked above
```

#GFXMODE=[COLOR=Teal]1024x798x24[/COLOR]

```8. Save and close the file.

9. Update your grub files.
```

sudo update-grub

```10. reboot and test.

Tell me how it goes for you... or if you need more info.

Note- You can pick any mode both your card, your monitor and you can handle. Remember that text in a 1920x1200 screen is pretty small! Just ensure you are consistant in where you change it in those 2 places of that file.  What this does is preps the card into a mode at Grub, the kernel... passes that mode through KMS to the X-Session.

Edit- I know that driver is supported by the xorg "radeon" driver.  If you edit your sources file (/etc/apt/sources.list) and uncomment the Conical Partners repo (2 lines in there) then an additional driver may show up or not, depending if that card is still supported by ATI.  More work if you have ATI, that repo is not a default setting, so the fglrx packages (ATI Drivers) don't show as a default in 11.10. (argh!)

---

### Post by leodan on 2012-04-15
All right, at last  found a remedy to my problem  :guitar: - I have disabled HPET support in BIOS power settings. I tested Ubuntu 11.10 , 12.04 beta 2  and Fedora 16 all boot and work without any problems :p . Just to remind my motherboard is ga-ma69vm-s2 f10e. Was not able to run most of the linux distros newer than Ubuntu 8.04.

---

