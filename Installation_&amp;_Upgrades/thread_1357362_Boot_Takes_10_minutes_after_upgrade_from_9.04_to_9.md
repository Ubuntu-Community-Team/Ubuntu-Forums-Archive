---
title: "Boot Takes 10 minutes after upgrade from 9.04 to 9.10"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by mlebaron on 2009-12-17
After upgrading from 9.04 to 9.10 booting is extremely slow.

I'm using Ubuntu 64 9.10 on an Acer AM1100 Athon AMD4000+.

Vista is on one SATA drive and boots perfectly, Ubuntu is on another ide or maybe eide drive, third drive is a shared data drive and is SATA.  Dual booting using grub.

When I turn on the machine I get the grub menu.
I select Ubuntu 9.04 and I see a "Starting from drivename" message.  The screen flickers and then the same message reappears and then TEN minutes or so later the white ubuntu logo appears for a few seconds and then finally the Ubuntu login screen appears.

In order to better see what is going on, I tried getting rid of the "quiet" in my Ubuntu grub menu item.  I can make the change but I don't know how to save the modification.  (I use "d" to delete the line with the "quiet" and then I tried hitting Esc but that didn't save the change.  So then I tried hitting "b" for boot but that didn't save the change either.  How do you save the Grub menu item with no "quiet" in it?).

If I could at least see what is happening during the boot maybe you and I could trouble-shoot this thing together.

---

### Post by mlebaron on 2009-12-18
Bump

---

### Post by mlebaron on 2009-12-18
Bump

---

### Post by kansasnoob on 2009-12-18
I assume you have legacy grub. You can see while booted into Ubuntu by running the command:

```
grub-install -v
```

(0.97 is legacy grub, 1.97 is grub2)

Anyway if it's legacy grub you can edit the menu.lst. First back it up:

```
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Then open with gedit to edit:

```
sudo gedit /boot/grub/menu.lst
```

Look for this section:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

If you change the line **# defoptions=quiet splash** to: **# defoptions=splash** and then click on Save, then File > Quit and run the command:

```
sudo update-grub
```

You'll still have a splash screen but it will give information about the startup process.

If you change it to: **# defoptions=** that will also remove the splash screen. Note: you still must "sudo update-grub" after any change!

I'm a bit curious to see the output of:

```
ls /boot/grub
```

BTW that's a lower case L.

---

### Post by oldfred on 2009-12-18
Did you review log files in System, Administration, log file viewer? It should have info on the kernel loading and show errors or a long time between a process step.

---

### Post by mlebaron on 2009-12-19
Thank you for your response.  It is definitely legacy grub.  I made the change to get rid of the "quiet".  I haven't yet rebooted.  I'll try it and post results after I reboot.  But here is the "ls" output you asked for:

mark@kitchen-desktop-ubuntu64:~$ ls /boot/grub
default        fat_stage1_5       jfs_stage1_5  menu.lst_backup    stage1
device.map     grubenv            menu.lst      minix_stage1_5     stage2
e2fs_stage1_5  installed-version  menu.lst~     reiserfs_stage1_5  xfs_stage1_5

---

### Post by mlebaron on 2009-12-19
Thank you for your response.  I did look in the log file viewer but I wasn't sure which of the many logs to examine.  The "Boot" log was empty.  So I just checked the "kern.log" from the 17th and there is what appears to be a recurring problem in that log.  Do you suppose this is what is causing a ten minute boot time?  I *swear* that this machine was booting in less than a minute under 9.04 and the only thing that has changed is that I made the mistake of upgrading to 9.10.

Here is the text of what appears to be a recurring problem in the kern.log:

Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    1.332527] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    1.342530] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    1.500030] usb 1-3: new high speed USB device using ehci_hcd and address 4
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    1.653438] usb 1-3: configuration #1 chosen from 1 choice
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    1.732526] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    2.070017] usb 2-2: new low speed USB device using ohci_hcd and address 2
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    2.254303] usb 2-2: configuration #1 chosen from 1 choice
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    2.550016] usb 4-1: new full speed USB device using ohci_hcd and address 2
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    2.733091] usb 4-1: configuration #1 chosen from 1 choice
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    6.330022] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    6.330032] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    6.342515] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    6.342524] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    6.730017] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    6.730026] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    6.860030] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    6.872525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [    7.260027] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   16.860019] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   16.860028] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   16.860032] ata2: limiting SATA link speed to 1.5 Gbps
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   16.872513] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   16.872522] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   16.872526] ata3: limiting SATA link speed to 1.5 Gbps
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   17.260016] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   17.260025] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   17.260028] ata1: limiting SATA link speed to 1.5 Gbps
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   17.390029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   17.402525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   17.790027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.390015] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.390024] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.402513] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.402522] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.790015] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.790024] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.920028] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.932525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.942524] ata2: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t4
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.942527] ata2: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.942531] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.952522] ata3: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t4
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.952525] ata3: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   47.952528] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   48.322525] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   48.340024] ata1: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t4
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   48.340027] ata1: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   48.340030] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   48.470029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   48.482525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   48.870027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   53.470015] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   53.470024] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   53.470027] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   53.482513] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   53.482522] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   53.482525] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   53.870015] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   53.870024] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   53.870027] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   54.000034] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   54.012529] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   54.400027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.000017] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.000027] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.000031] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.012514] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.012523] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.012527] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.400015] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.400025] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.400029] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.530028] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.542525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   64.930027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   94.530019] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   94.530028] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   94.530031] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   94.542513] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   94.542522] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   94.542525] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   94.930015] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   94.930024] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   94.930027] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.060029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.060043] ata2: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t3
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.060046] ata2: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.060049] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.072526] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.072539] ata3: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t3
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.072542] ata3: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.072545] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.460028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.460041] ata1: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t3
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.460044] ata1: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.460047] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.590029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.602525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [   95.990027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  100.590019] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  100.590029] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  100.590032] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  100.602513] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  100.602522] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  100.602525] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  100.990016] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  100.990025] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  100.990028] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  101.120029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  101.132525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  101.520028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.120016] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.120025] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.120029] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.132513] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.132522] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.132526] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.520016] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.520025] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.520029] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.650029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  111.662525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  112.050031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  141.650017] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  141.650027] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  141.650030] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  141.662514] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  141.662523] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  141.662525] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.050018] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.050027] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.050030] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.180029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.180043] ata2: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t2
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.180046] ata2: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.180049] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.192526] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.192539] ata3: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t2
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.192542] ata3: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.192545] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.580028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.580041] ata1: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t2
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.580044] ata1: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.580047] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.710029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  142.722525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  143.110031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  147.710017] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  147.710026] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  147.710029] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  147.722514] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  147.722523] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  147.722525] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  148.110017] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  148.110027] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  148.110029] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  148.240029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  148.252525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  148.640028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.240018] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.240027] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.240032] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.252514] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.252523] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.252526] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.640016] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.640025] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.640028] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.770029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  158.782525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  159.170029] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  188.770018] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  188.770027] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  188.770030] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  188.782513] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  188.782522] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  188.782525] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.170017] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.170026] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.170029] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.300029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.300042] ata2: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t1
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.300045] ata2: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.300048] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.312525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.312539] ata3: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t1
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.312542] ata3: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.312544] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.700028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.700042] ata1: exception Emask 0x40 SAct 0x0 SErr 0x400800 action 0x7 t1
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.700045] ata1: SError: { HostInt Handshk }
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.700048] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.830029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  189.842525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  190.230027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  194.830019] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  194.830028] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  194.830031] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  194.842514] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  194.842523] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  194.842525] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  195.230016] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  195.230025] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  195.230028] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  195.360029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  195.372525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  195.760027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.360016] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.360025] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.360029] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.372513] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.372522] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.372526] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.760016] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.760025] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.760028] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.890028] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  205.902525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  206.290028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  235.890016] ata2.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  235.890026] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  235.890029] ata2: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  235.902514] ata3.00: qc timeout (cmd 0xa1)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  235.902522] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  235.902525] ata3: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.290015] ata1.00: qc timeout (cmd 0xec)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.290024] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.290027] ata1: hard resetting link
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.420029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.420035] ata2: EH pending after 5 tries, giving up
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.420037] ata2: EH complete
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.432525] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.432530] ata3: EH pending after 5 tries, giving up
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.432533] ata3: EH complete
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.820028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.820033] ata1: EH pending after 5 tries, giving up
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.820035] ata1: EH complete
Dec 17 01:21:52 kitchen-desktop-ubuntu64 kernel: [  236.820161] scsi 4:0:0:0: Direct-Access     ATA      WDC WD800BB-00CA 17.0 PQ: 0 ANSI: 5

---

### Post by mlebaron on 2009-12-19
I rebooted now that the "quiet" has been removed from the grub entry.  It is definitely taking a long time to get through all that "ata / SATA" stuff that I listed in my last post.  Everything else seems to move by pretty fast.

Incidentally, I just realized that my DVD player no longer auto-mounts discs and the data drive that used to show up on my desktop under 9.04 no longer is mounted.  Ubuntu is on an old ide or maybe eide drive.  The Vista and the data drive are both SATA.  I'm betting these are both attributable to the same root cause as the slow boot time.

So, why did this problem start happening with an upgrade to 9.10; and more importantly, how do I fix it?

---

### Post by oldfred on 2009-12-19
I have seen recommendations to in BIOS change the setting to IDE from Sata for mixed systems like yours. The sata should work under the ide setting but may not take advantage of the newer sata features but your ide drive prevents that anyway.

---

### Post by mlebaron on 2009-12-21
I appreciate your response.  This is really a perplexing problem.

Under 9.04 this mixed setup worked fine with no changes to the BIOS settings.  Also, if I boot to Vista, I can see the SATA drives just fine.  So, the problem is with the upgrade to 9.10.

Wouldn't you agree?

---

### Post by mlebaron on 2009-12-29
Bump

---

### Post by oldfred on 2009-12-29
I recently saw another user who was having issues with his SATA and system. He found moving the SATA connections from slave to master made a difference. 

I know on my machine I see the slave/master settings but until the other user said he had to physically move the connection to make a difference. I have also seen issue with the slave master settings in mixed SATA and PATA/IDE drives and some BIOS do not support the mixed configurations well.

My BIOS has several settings for SATA including AHCI and Native mode.  I think one of these settings on your system may be why it is having issues. It seems to be trying to use the high speed SATA setting but then if the drive does not support it, then it has to drop back to a slower speed.

---

### Post by mlebaron on 2010-01-16
Oldfred, I really appreciate your efforts.  However, you are saying that 9.04 supported mixed SATA and PATA/IDE drives but that 9.10 does not?  I find that hard to believe.  Remember that my 9.04 was working perfectly on the same machine and my Vista still works perfectly on the same machine.  So why am I suddenly having these problems with 9.10?

Verdict: Karmic Koala is a total flop.  I can deal with a few upgrade problems as long as there are actually real solutions.  But look how long this thread has been open with no solution.  I'm just going to back up my data and reinstall 9.04 and I'll be advising everyone I know NOT to upgrade to 9.10.

Sorry to pick on you; I know you are only trying to help.  I'm just really frustrated that this is what it has come down to.

Thanks for trying.

---

### Post by oldfred on 2010-01-16
We have seen several cases where windows and older versions of grub/ubuntu may have worked, but now do not. It seems that the older versions just ignored BIOS settings. The new versions of grub do not ignore the BIOS settings but use them and have then created problems.

I think the official reponse will be that this was what you wanted since that is what you had in BIOS. But most people do not even know about BIOS much less what settings they have.

---

### Post by mlebaron on 2010-03-25
OK this is just weird.  So, I let my 9.10 sit for a couple of months and occasionally the family would accidentally let the system re-boot into Ubuntu rather than Vista.  Sometimes when Vista would reboot in the middle of the night, it would reboot to Ubuntu.  I guess there were times when Ubuntu just sat running with nobody doing anything with it.

So, tonight I accidentally walked away from the machine after rebooting and it booted to Ubuntu rather than into Vista.  And guess what?!?!  It only took a few seconds to get to the login screen!!!  So I logged in and it only took a few seconds to get logged in.  AND.... Now I can suddenly see my 500 Gig SATA drive that had disappeared!!!

I figure somebody at Ubuntu fixed something and I must have auto-downloaded it and installed it in the middle of the night or something.

Just plain weird.  But it appears to be fixed, so I'll take it!

---

