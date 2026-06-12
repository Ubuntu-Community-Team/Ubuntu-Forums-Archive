---
title: "Problem installing Maverick from a usb disk"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by gamx on 2010-10-10
I am trying to install Maverick from a pendrive (my netbook does not have a cdrom and I wanted to do a clean install). I have created, as usual, a bootable usb drive using the "Startup Disk Creator". Everything works well during the creation process. However, when I try to install it on the netbook, the process starts, I get the purple screen saying Ubuntu 10.10 and eventually everything stops with the message:

Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell(ash)
Enter 'help' for a list of built-in commands

(initramfs) Unable to find a medium containing a live file system


Any suggestion about what do to?
Thanks,

Gamx

---

### Post by JackNocturne on 2010-10-10
So it boots normally then it gives error or?

Does it go to the **menu** with the "Try Ubuntu" and "Install Ubuntu" option ??

---

### Post by gamx on 2010-10-10
Not quite. It just starts, I get the splash screen and after a while it gives me that message.

---

### Post by JackNocturne on 2010-10-10
Could be this  [http://ubuntuforums.org/showthread.php?p=9948797](http://ubuntuforums.org/showthread.php?p=9948797)  maybe  

Did you modify the **syslinux.cfg** file after you created your live USB with USb-creator?

---

### Post by gamx on 2010-10-10
I have tried again and now I've got the menu. I have chosen "install ubuntu" but... the same message again...
I do not know if it matters but my netbook is a Sony Vaio P, and I have never had problems with that...

---

### Post by JackNocturne on 2010-10-10
Mmmh , a little bit out of my scope:(

When the menu comes again, click "Try Ubuntu" , then try to install it from inside (as when it logs in Gnome-desktop)

---

### Post by gamx on 2010-10-10
I have tried that but it does not work.... :-(
The option of try ubuntu gets me to the same place. Even checking the disk leads to the same outcome...

---

### Post by JackNocturne on 2010-10-10
Bad luck, the only thing you can do now is /Troubleshooting/   


My tips would be

1)Make sure the iso you downloaded is the correct i.e MD5 hash check
   [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2)Try making the live USB again with Usb-disk creator

3)Try other OS like even Ubuntu 10.04 if it works

Sorry man ,i know how frustrating it can be

---

### Post by gamx on 2010-10-11
Yes. It is very frustrating. I do not think there is a problem with neither the iso image nor the way I have used the startup disk creator...
Thanks a lot for your help.

---

### Post by Cal on 2010-10-11
Same Vaio P problem here...  I'll add a little extra data as well...

I tried both a USB stick and a USB CD/DVDRom; neither worked.  I also tried installing from WUBI, which worked and resulted in a bootable system.  

The problem with that solution is that none of the USB ports worked. Plugging in memory sticks and other usb devices wouldn't even show up in dmesg.  lsusb showed several bus devices but again, dmesg didn't register plugging or unplugging devices.

BIOS can see and boot from the drives, but once the installer tries to load a kernel and boot image we have problem.

My linux-fu is weak, so thats as far as I have gotten.

Any help?  Is this a bug or lack of user knowledge?

---

### Post by bod on 2010-10-11
Exactly the same problem here.

Acer Aspire One. Tried both the Netbook and Desktop images on 2 different USB sticks with the same result every time.

---

### Post by nerilex on 2010-10-12
Hi,
I have a similar Problem with my Vaio P.
I installed the maverik kernel also on 10.04 an could start it and found the following in dmesg:
```

[    0.704486] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.704668] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[    0.704834] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    0.705050] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.705069] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.705418] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.705643] ehci_hcd 0000:00:1d.7: debug port 0 IN USE
[    1.051394] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.051488] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x7f800000
[    1.398090] ehci_hcd 0000:00:1d.7: startup error -110
[    1.398227] ehci_hcd 0000:00:1d.7: USB bus 1 deregistered
[    1.398647] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[    1.398749] ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -110
[    1.398860] ehci_hcd: probe of 0000:00:1d.7 failed with error -110
[    1.399070] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.399265] uhci_hcd: USB Universal Host Controller Interface driver
[    1.399570] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.399705] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.399726] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.400082] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.400310] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00006040
[    1.401840] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.401967] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.401985] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.402332] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    1.402555] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00006020
[    1.403996] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    1.404130] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.404148] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.404491] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    1.404726] uhci_hcd 0000:00:1d.2: irq 23, io base 0x00006000
[    1.716139] usb 2-2: new full speed USB device using uhci_hcd and address 2

```So it seems that the kernel has trouble getting EHCI (USB2.0) to work.
Due to having no USB the boot fails because the system can not load other data from PenDrive or USB-CD.
Hopefully they will fix the Kernel soon.

---

### Post by spazzymoto on 2010-10-12
Can comfirm the same error on sony vaio x laptop.

---

### Post by Cal on 2010-10-12
Is this the point where we can/should file a bug?

---

### Post by scubajeff on 2010-10-12
confirm same problem on sony vaio x. by adding "acpi=off" to grub boot menu, seems to bring the usb back to normal, but this setting conflict with gma600 psb display driver.

---

### Post by bod on 2010-10-12
I've managed to get it working by looking at what's changed since the 10.04 ISO which still works fine.

The default entry in my syslinux.cfg now reads as follows ...

```

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu-netbook.seed boot=casper quiet splash -- 

```

This is for a USB stick created with UNetbootin so I imagine the label will be different for one created using the Startup Disk Creator.

---

### Post by perlwonk on 2010-10-12
I have the same problem here. I'm trying to install ubuntu 10.10 netbook on a Sony Vaio using a USB flash, but keep getting the message "BusyBox ... Unable to find a medium containing a live file system". The same USB flash works just fine on an HP netbook, but not the Sony.:confused:

---

### Post by DShad on 2010-10-12
Did someone find a fix for that problem?

I'm having the same issue with Sony VAIO P series.

Is there any workaround?

Thanks

---

### Post by mörgæs on 2010-10-12
Some reports indicate that creating the USB stick with the latest Unetbootin works best. I have not tried it myself, though.

---

### Post by cblanquer on 2010-10-13
Same issue on a vaio P installing from an USB:
"(initramfs) Unable to find a medium containing a live file system"

I used the same USB to install Ubuntu Netboook 10.10 on an eeePC 710 some hours ago without any problem.

The only difference I see, apart the hardware, is that my Vaio P holds already an Ubuntu installation and a Windows 7 installation. But the message received from the installar does not seem related to that specifically but rather to some bug in the installer.

---

### Post by cblanquer on 2010-10-13
Same issue on my Vaio P, when it worked perfectly on an eeePC 701.

---

### Post by scubajeff on 2010-10-14
ok, guys, i manage to solve the a kernel issue stopping Maverick from recognizing USB. 

machine model: sony vaio x, cpu z530, memory 2GB
problem: maverick can boot and latest GMA500 driver works, but missing usb hotplug, bluetooth, sd, memorystick.

By digging dmesg output, found that ehci_hcd is trying to use io mem 0x7f800000 but fails and stops loading, and psb driver is also complaining it can't use memory range from 0x7f800000. So that is the problem.

Solution: by adding memmap=1K#0x7f800000 to your grub config, update grub and reboot. everything work again!

---

### Post by Cal on 2010-10-14
> **scubajeff said:**
> Solution: by adding memmap=1K#0x7f800000 to your grub config, update grub and reboot. everything work again!

Thanks subajeff,
I'm testing this solution now, it seems to work.

---

### Post by zl1ogx on 2010-10-14
I have been having a similar issue.

I downloaded the 10.10 UNR iso, used Live-USB creator, the same tool I have used to create 10.04 USB installs with.  But when I use it to try to install on my dell mini9 I noticed that it came up with SYSlinux as the boot loader, and it just hangs there.

So created a boot cd from the iso, and created the boot usb from inside UNR.  Went to the dell mini and noticed that a different boot loader was installed, confused :confused:.  Anyway, that started the install process.

Got all the way through the installation re-booted and bugger, a flashing cursor in the top left and nothing else.  

So now I'm trying the live version and installing via that to see what happens.

Not having fun any more :(

Heres hoping..

Ian

---

### Post by mörgæs on 2010-10-14
How long did you wait for the boot process to begin, when there only was a cursor on the screen?

If everything else fails, try Unetbootin. The version which comes by default in 10.04 appears not to work; best is to get the newest from
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Cal on 2010-10-14
EDIT: Just realized that mörgæs was talking to someone else.

---

### Post by zl1ogx on 2010-10-14
Hi Mörgæs

I waited for well over 5 minutes and got really frustrated, so went ahead and started again.

This time, with the USB created from with in the live cd, appears to have worked.  Although I have a screen full of udevd[81] worker refused kill it at boot up.  System comes up and unity runs.  Done some slight configuration and installed Skype, which only appeared after a restart.

The rest looks like it running OK, so off to see if I can keep it running.

Cheers

Ian

---

### Post by DShad on 2010-10-21
> **scubajeff said:**
> 

Solution: by adding memmap=1K#0x7f800000 to your grub config, update grub and reboot. everything work again!

You're the man!  

It works!  Thanks a lot.

---

### Post by loldrup on 2010-10-29
> **DShad said:**
> You're the man!  

It works!  Thanks a lot.

I need a bit more guidance guidance..
So, I insert the Maverick USB image, boot, and then..? Where/how do I type these grub commands?

I thought grub was something that resided in my MBR, and so isn't involved in booting from USB?

---

### Post by mörgæs on 2010-10-30
These pages might help:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by lcbruzer on 2010-10-31
Not much help on Sony Vaio P. Tried both USBs and a USB-powered DVD. Any ideas are appreciated...

---

### Post by lcbruzer on 2010-11-01
missed the page1 post that 10.04 still works; will try that.

---

### Post by emem on 2010-11-05
I second that. Same results on my Sony Vaio P with different USB sticks and all startup disk creators mentioned (Windows and Linux).

I know how to edit grub on a running system. But i don't see a way to edit grub on the usb stick. Will that be done on the target PC while booting or on the PC creating the startup disk?

A 9.04 startup disk created on 9.04 works.

---

### Post by emem on 2010-11-05
This works! But it's less complicated. You don't have to edit grub. Just add memmap=1K#0x7f800000 to the Boot Options on startup. Therefore press ESC as soon as the purple screen appears. Press F6 and write memmap=1K#0x7f800000 after quiet splash.

It boots. Starts X. But now my Sony Vaio P is stuck after Unity could not load.

Edit: Second try and it works. Seems to solve the problem quite simple.

---

### Post by universe-traveller on 2010-12-02
only add "memmap=1K#0x7f800000" didn't work in my case.
press F6 and select all except "free software only", it worked

---

### Post by VirtualRoot on 2010-12-11
I'm having a completely different problem....

Trying to install 10.10 amd64 on a ASUS Sabertooth.  

The USB stick boots fine, I can select the installer, select my keyboard, and it starts scanning CD ROM files.

Then it says "There was a problem reading data from the CDROM.......

failed to copy file from the CDROM..."

Then it offers to retry or not.  Retrying brings me back to the same error.

My MD5SUM of my ISO image matches, and I've tried 2 different USB sticks.

The MEMMAP trick didn't work either.

Thanks!

---

### Post by mörgæs on 2010-12-13
Hi, welcome to the fora.

Have you created the USB stick with Unetbootin as described earlier in the thread?

---

### Post by VirtualRoot on 2010-12-13
> **mörgæs said:**
> Hi, welcome to the fora.

Have you created the USB stick with Unetbootin as described earlier in the thread?

Yes I did, but that got me even less far.  With Unetbootin I was able to boot the stick, get to the menu to select to install 10.10 server, and then it just came up and said  it couldn't find a CDROM and I had to install drivers.

---

### Post by mörgæs on 2010-12-14
In that case I would begin searching a little wider. What about trying the alternate 32 bit 10.04? 

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by RebateFX on 2011-01-14
> **universe-traveller said:**
> only add "memmap=1K#0x7f800000" didn't work in my case.
press F6 and select all except "free software only", it worked

I can confirm that this works for the Sony Vaio X. I got the Desktop to boot from USB and I'm running the installer now! :)

Nice one, thanks!

---

