---
title: "USB Hard disk installation does not boot"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by nbala.iyer on 2010-10-31
Hi ,

I have installed Kubuntu on external WD HDD , it does NOT boot on this laptop but works on couple of other laptops :( , attached is the results txt output of the boot_info...sh. 
I can boot with USB flash drive that has kubuntu live Cd image .. 
when I use the external HDD ,it gives a blinking cursor only .. 

regards,
bala

---

### Post by P4man on 2010-10-31
It looks like grub is configured to boot ubuntu from hd1 and windows from hd0. However if you set your bios to boot from the external USB drive first, then that drive is likely hd0 (and the internal drive becomes hd1).

Im just guessing here that you installed ubuntu by booting from usb using the bios boot menu (usually F11 or F12) and that you now changed bios boot order?

If that is the case, you could try if at least it boot if you set the bios to boot from the internal drive initially but use the same bios boot menu to select the usb drive

---

### Post by nbala.iyer on 2010-10-31
Hi , Thanks for response , I have not changed the BIOS order , in fact this external HDD boots on my DELL 530 and Toshiba , only Vaio (PCG71312) is giving this issue ..  I held the shift while booting on .. it ended up with GRUB Loading. and a blinking cursor below it



Regards,
Bala

---

### Post by oldfred on 2010-10-31
If you get to the grub menu, then it likely is the video chip or video card. You may need to try several alternatives.

From liveCD you can run this to know what video you have:
sudo lspci | grep VGA

On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

The nVidia nForce is not a graphical chip, but a chipset, so using the fix for the nvidia graphics card did not work.
The generic one did.

---

### Post by nbala.iyer on 2010-11-01
Hi , just checked .. It shows 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) ..
also upon first boot the upon pressing shift , it shows 'GRUB Loading.' and blinking cursor only..It does not bring up a GRUB loader menu.

---

### Post by oldfred on 2010-11-01
You have to hold shift key from BIOS boot until menu appears, if grub has only configured one system.

It still may be video, if you can get menu, try e and put i915 setting if older. Some new i5 systems also needed acpi=off or other settings.

Check BIOS for settings and sometimes other parameters:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by nbala.iyer on 2010-11-01
sir , tried by holding shift key for long time. . no menu at all.. only the GRUB loading then blinking cursor.  :(
Surprisingly the Live Cd works excellently.. also the same USB HD when connected to my DELL 530 boots without any problem.. is there any way to check BIOS whether it supports USB HDD for booting..

---

### Post by oldfred on 2010-11-01
The grub flashing is the first part of boot normally, right after the menu. If it boots on other systems it would seem that grub is configured and should work. 

But you should be able to go into BIOS to confirm that you can set the external as a boot device. You should also have a key (mine is f12) to choose one time alternative boot which should show your choices.

Plug in external and run this from liveCD:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by nbala.iyer on 2010-11-01
hi , attached is the results.txt , have removed my laptop internal hard disk so that it does not show up in any installation or trouble shoot.. 
F2 is for boot order sequence , it has only 3 options , OPtical drive , External drive , Internal HD .. 
Vaio is not showing any one time boot option.. but the memory test done from live CD / USB went ok without any errors.. 
rgds, bala:popcorn::)

---

### Post by oldfred on 2010-11-01
It is strange that it shows your flash drive as sda and you other drive as sdb.

Your BIOS description does not sound like it offers USB boot, how is external defined by your system?

I have not used it but this will supposedly let you boot USB devices that otherwise are not bootable. 

Plop
[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by nbala.iyer on 2010-11-02
hi fred, tried to use Plop , it also says there is 'No valid boot device' on USB , upon Ctrl+Alt+Del , it shows as HDB 1 & HDB2 still not booting from it , is there any way to check on the BIOS compatability or BUG .. while loading using Live CD USB of kubuntu the log showed somelines like below :
2010-11-02 18:20:48	ubuntu	kernel	[    4.319907] pci 0000:00:1a.0: EHCI: BIOS handoff failed (BIOS bug?) 01010001
2010-11-02 18:20:48	ubuntu	kernel	[    5.919214] pci 0000:00:1d.0: EHCI: BIOS handoff failed (BIOS bug?) 01010001
2010-11-02 18:20:48	ubuntu	kernel	[    6.013150] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
2010-11-02 18:20:48	ubuntu	kernel	[    6.013239] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
2010-11-02 18:20:48	ubuntu	kernel	[    6.013320] ehci_hcd 0000:00:1a.0: setting latency timer to 64
2010-11-02 18:20:48	ubuntu	kernel	[    6.013325] ehci_hcd 0000:00:1a.0: EHCI Host Controller
2010-11-02 18:20:48	ubuntu	kernel	[    6.013417] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
2010-11-02 18:20:48	ubuntu	kernel	[    6.013546] ehci_hcd 0000:00:1a.0: debug port 2
2010-11-02 18:20:48	ubuntu	kernel	[    6.017492] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
2010-11-02 18:20:48	ubuntu	kernel	[    6.017510] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf6008000
2010-11-02 18:20:48	ubuntu	kernel	[    6.031410] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
2010-11-02 18:20:48	ubuntu	kernel	[    6.031850] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
2010-11-02 18:20:48	ubuntu	kernel	[    6.031928] ehci_hcd 0000:00:1d.0: setting latency timer to 64
2010-11-02 18:20:48	ubuntu	kernel	[    6.031933] ehci_hcd 0000:00:1d.0: EHCI Host Controller
2010-11-02 18:20:48	ubuntu	kernel	[    6.032037] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
2010-11-02 18:20:48	ubuntu	kernel	[    6.032152] ehci_hcd 0000:00:1d.0: debug port 2
2010-11-02 18:20:48	ubuntu	kernel	[    6.036097] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
2010-11-02 18:20:48	ubuntu	kernel	[    6.036112] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf6007000
2010-11-02 18:20:48	ubuntu	kernel	[    6.051401] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
2010-11-02 18:20:48	ubuntu	kernel	[    6.387522] usb 1-1: new high speed USB device using ehci_hcd and address 2
2010-11-02 18:20:48	ubuntu	kernel	[    6.635553] usb 2-1: new high speed USB device using ehci_hcd and address 2
2010-11-02 18:20:48	ubuntu	kernel	[    6.838948] usb 1-1.2: new high speed USB device using ehci_hcd and address 3
2010-11-02 18:20:48	ubuntu	kernel	[    7.039367] usb 2-1.5: new high speed USB device using ehci_hcd and address 3
2010-11-02 18:20:48	ubuntu	kernel	[    7.207318] usb 2-1.6: new high speed USB device using ehci_hcd and address 4

attached is the Results.txt :) , is there anyway to catch hold of manufacturer for Bugs in BIOS.. 

Rgds,
Bala

---

### Post by oldfred on 2010-11-02
Does BIOS see the drive?

My BIOS shows I can boot from a USB device and I tried from a flash drive but it never worked from any of the USB choices. One day much latter I had the flash plugged in and was rebooting and choosing hard drives with f12 (one time boot key) and the USB flash drive was listed as a hard drive.

---

### Post by nbala.iyer on 2010-11-03
Hi Fred , Seems that BIOS sees the HDD but incapable of pulling the boot image from its sectors , I can boot from USB Flash Drive .. unfortunately the USB HDD gives issues , have logged a complaint to Vaio support... Even when I try to use Win2003 USB installation it fails stating No Hard Drive found' .. rgds, bala

---

### Post by nbala.iyer on 2010-11-10
Hi Fred, It now works .. atleast goes to the GRUB prompt from there i am able to boot into the X server without any issues..  :)

---

### Post by oldfred on 2010-11-10
Progress, we love to hear that something is working. :)

If you have new issues that are not related to booting then it will be better to open new threads. If solved you can change the status, see my signature for instructions.

---

