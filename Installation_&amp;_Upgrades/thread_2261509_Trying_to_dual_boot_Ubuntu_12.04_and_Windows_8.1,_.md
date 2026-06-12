---
title: "Trying to dual boot Ubuntu 12.04 and Windows 8.1, logging into blank purple screen"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by Pedro_Carvalho on 2015-01-19
I posted originally on [ask ubuntu]("http://askubuntu.com/questions/575179/trying-to-install-ubuntu-12-04-log-to-a-black-screen/575434?noredirect=1#comment794226_575434"). I'm trying to install Ubuntu 12.04 on my laptop that happens to have two graphics cards, and UEFI + graphics problems ensued. After finally managing to install ubuntu, I can't actually boot it, as booting in normal mode (resp. recovery mode) shows me a blank purple (resp. black) screen and doesn't load anything. My boot-recovery pastebin is [here]("http://paste.ubuntu.com/9784753/"). Presumably I'd need to install the proper drivers now, but I'm in this slight catch-22 in which I need to install the drivers to use ubuntu, and need to use it to install the drivers.

What should I do?

-ETA: Using nomodeset doesn't seem to work either.

---

### Post by oldfred on 2015-01-19
You are showing both Intel & nVidia.
Can you control which you boot with in UEFI? Or does it auto switch.
You may be better with 14.04 or even 14.10. Intel is updating its drivers and support software and the newer kernels also have improvements that work better with newer hardware.

If booting with Intel you may need Intel settings, not nomodeset.

 Intel Video
[http://askubuntu.com/questions/496944/after-using-boot-repair-i-cannot-change-screen-resolution/497712#497712](http://askubuntu.com/questions/496944/after-using-boot-repair-i-cannot-change-screen-resolution/497712#497712)
Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024:
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60


 Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

Do you just have both video or is it dual video that you can switch -Optimus.
Some use the new Nvidia Prime or others bumblebee. Not sure which is better.

      
 Dual graphics install nVidia prime and newer nVidia driver
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)
Getting hybrid graphics to work nvidia-prime GT650M - but you want most current nVidia driver available
[http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m](http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-nvidia-prime-gt650m)
[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)
Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)

   Bumblebee may not be required with nVidia Optimus
Bumblebee - allows both nVidia & Intel to be used, nVidia Prime was just nVidia, but now updated:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04](http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by Pedro_Carvalho on 2015-01-19
It's typically auto-switch, and it typically only switches to nVidia when high-performance software (i.e. 3d modelling, games, etc) is used, but it's possible to manually switch it on Windows. I don't know whether it's possible and how to do it during boot, though.

I need to get 12.04. I'm installing this because I need to connect to a robot for a class, and apparently it's impossible to do so for 14.04 because the robot's software doesn't support any ubuntu later than 12.04.

It's *probably* booting with Intel, since it only uses the nVidia when it really needs to, normally. I'm gonna go test this option and get back to you on it.

[INDENT]Some other Intel boot options Each line is one that may workacpi_osi=Linux acpi_backlight=vendor
i915.i915_enable_rc6=1[/INDENT]

Where should I add these lines?

[INDENT]Do you just have both video or is it dual video that you can switch -Optimus.
Some use the new Nvidia Prime or others bumblebee. Not sure which is better.[/INDENT]

I don't understand this. My graphics cards switch depending on the software I'm using, normally. And what's Optimus/Prime/Bumblebee?

---

### Post by oldfred on 2015-01-19
If it auto switches that is nVidia Optimus.  And then nVidia Prime or Bumblebee is the software. But I think Prime only works with the newest kernels or newer versions of Ubuntu.

But if booting with nVidia then you add one or more boot options just like nomodeset.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by Pedro_Carvalho on 2015-01-20
Like I said earlier, using nomodeset doesn't work. I've tried replacing quiet splash with video=1600x900-24@60 (1600x900 is the resolution I run on Windows) or video=VGA-1:1600x900-24@60, or adding acpi_osi=Linux acpi_backlight=vendor or i915.i915_enable_rc6=1 at the end of the parameters in the grub menu also did not work. I'm still stuck with the purple screen.

(Possibly relevant: I noticed that before I'm presented with the purple screen to choose which OS to use, the message "efidisk read error" appears a few times.)

(Also possibly relevant: on my UEFI boot priority list, it identifies ubuntu three times and Windows only once. On installation, I made a swap partition, a bootloader partition, and an ubuntu partition, this might be it, but I don't know.)

---

### Post by oldfred on 2015-01-20
If you installed in BIOS mode, it has to go back and switch from UEFI for Windows boot to BIOS. That may be part of efi read error. Or many systems now modify UEFI to only boot by description that reads "Windows". Did you implement one of the work arounds to make it work for those that boot only Windows?

But if none of all those settings work, then you are into a much more complex issue. 
First why does does not your other software work with newer version of Ubuntu? That might be easier to fix.
Otherwise you in effect upgrade Ubuntu kernel, support software & nVidia drivers with ppa, so you are running all the current versions that should then work with your hardware, but are still 12.04. Those upgrades may again break whatever is the issue with your software.

       xorg-edgers PPA
Oibaf PPA discusion  [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)

---

### Post by Pedro_Carvalho on 2015-01-20
I'm not sure what you mean. Like I mentioned originally in the askubuntu link, I had to turn UEFI off in order to install ubuntu at all. When I did, it could not install the bootloader for some reason, and I had to use a boot recovery disk to install the boot loader. If I keep UEFI off, it recognises neither Windows nor ubuntu; if I turn it on, it recognises both, but it just shows me the purple screen, like I said before. I'm not sure what workarounds you mean.

I don't know why it doesn't work with a newer version of ubuntu, my professor just said it didn't, and observably it doesn't.

How do I upgrade ubuntu kernel and download drivers if I can't even open ubuntu in the first place?

---

### Post by oldfred on 2015-01-20
You do have to have a partially working install or boot at least to command line.

If installing in BIOS boot mode, you have to have a 1 or 2MB unformatted partition anywhere on drive with the bios_grub flag with gparted or ef02 setting if using gdisk. That is so grub can correctly install in BIOS boot mode. 
In BIOS boot mode, you also in UEFI have to turn off secure boot and all UEFI settings, or turn on CSM/ BIOS boot mode. You can then only boot Windows by turning on UEFI. Some will auto switch and let you dual boot from one time boot key often f10 or f12.

But generally better to have UEFI on, secure boot off to boot both Ubuntu and Windows from either UEFI boot menu or grub menu.

Lets just see if configured correctly for booting. If you do get to grub menu, then this may not tell much. And what brand/model computer is this?
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Pedro_Carvalho on 2015-01-20
I select ubuntu from a grub menu, I have access to *that*, it's after that that nothing works.

No matter what I did, I couldn't use that partition to install the boot loader. I had a 512MB unformatted partition with the bios_grub flag and the ubuntu installer *still* couldn't create the boot loader there.

Like I said before, I used a boot recovery disk in order to make ubuntu visible at all.

It's a Medion laptop, I think the information is in the pastebin I provided at the top.

I'm going to try to create a bootinfo and I'll get back to you on this.

---

### Post by Pedro_Carvalho on 2015-01-26
Sorry for taking so long, I've had a pretty hellish week.
My bootinfo is [here]("http://paste.ubuntu.com/9878703/"). It doesn't look much different from the pastebin I pasted on my original post, so I dunno what new information you'll be able to get from it that you couldn't from that one.

-ETA: I have tried using boot-repair once again and instead of installing /boot/efi on a separate unit I installed it on sda. That causes Ubuntu to no longer recognise Windows, but it starts booting, and stops right after "Starting CUPS printing spooler/server" (only works with UEFI deactivated).

---

### Post by oldfred on 2015-01-26
You only show Ubuntu installed in UEFI boot mode.

You do show several ubuntu entries:

```
BootCurrent: 0014
Timeout: 2 seconds
BootOrder: 0014,0000,0007,0012,0013,0010,0011
Boot0000* ubuntu	[COLOR=#ff0000]HD(2[/COLOR],fa000,32000,1b7803ef-dedf-4406-bbfc-e017c55c457f)File(EFIubuntushimx64.efi)
Boot0007* Windows Boot Manager	HD(2,fa000,32000,1b7803ef-dedf-4406-bbfc-e017c55c457f)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0010* UEFI: Network IPv4 Device 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(8c89a50d4e05,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0011* UEFI: Network IPv6 Device 	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(8c89a50d4e05,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0012* ubuntu	[COLOR=#ff0000]HD(2[/COLOR],fa000,32000,1b7803ef-dedf-4406-bbfc-e017c55c457f)File(EFIUbuntugrubx64.efi)
Boot0013* ubuntu	[COLOR=#ff0000]HD(4[/COLOR],16c000,200000,eaae954f-437a-4616-8513-79a48f4c9c0e)File(EFIUbuntugrubx64.efi)
Boot0014* UEFI:  USB Flash Memory1.00	ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(1,0)HD(1,800,3baf9f,b0f673be-684f-4b37-989d-cf3428b8ddba)..BO
```

You do need to use the entry that is hd2 as that is the same drive as Windows. And it looks like you have a duplicate of hd2.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

    
The error in booting may not be last entry, so it can be hard to tell what is issue.

---

### Post by Pedro_Carvalho on 2015-01-26
The error in booting may not be last entry, so it can be hard to tell what is issue."You do show several ubuntu entries:"
I know, but I dunno what they're doing there.

"You do need to use the entry that is hd2 as that is the same drive as Windows. And it looks like you have a duplicate of hd2."
I have no idea what this means or how to do that.

"# from liveDVD or flash booted in UEFI mode and use efibootmgr"
I also have no idea what this means. How do I use efibootmgr, what is that?

"The error in booting may not be last entry, so it can be hard to tell what is issue."
What do you mean, may not be last entry?

---

### Post by oldfred on 2015-01-26
In post #11, I show the UEFI boot entries that came from your Summary report.
Highlighted in red the ubuntu entries. One is really grub, one is shim for secure boot, and one is for hd4 whatever drive that is.

efibootmgr is software to edit UEFI entries. But you have to boot live installer (or a working install) in UEFI mode to be able to use it.
See also links on description of efibootmgr and the other commands & options it has.

I assume you had errors on booting and it showed the boot process. That often stops booting, but the error is almost always several commands before last one on screen.

---

### Post by Pedro_Carvalho on 2015-02-01
I managed to solve it, with a friend's help (who was having the exact same problem). I posted the answer on the [askubuntu website]("https://askubuntu.com/questions/575179/trying-to-install-ubuntu-12-04-log-to-a-black-screen/580572#580572").

---

