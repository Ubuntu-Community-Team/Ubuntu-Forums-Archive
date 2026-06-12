---
title: "ZTE modems on 9.10 pre-release versions"
date: 2009-07-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GeorgeVita on 2009-07-02
[size=3]**[bug#408555]("https://bugs.launchpad.net/bugs/408555")**[/size]


Hi to all **ZTE 3G/HSPA modem users**,

after trying a lot to find out how to use my ZTE MF636 modem on various versions of Ubuntu and as it seems that developers are very close to make it, I desided to create this thread with the test results trying the ZTE modem with the 9.10 pre-release versions.

**Every post from a ZTE modem user containing technical info is helpful!**

A typical test procedure could be:

1. fully **update** system (Karmic Koala pre-released version)
2. boot **without** the modem, delete ALL Mobile Broadband connections (N.M.)
3. attach the modem, wait some seconds, test **lsusb**
4. **eject** any drive appeared
5. wait and retry **lsusb**
6. try **dmesg** and see last lines regarding **ttyUSBx** creation
7. follow Mobile Broadband wizard info (if started)
8. if some ttyUSBx found and the wizard did not started, try a **manual setup**
9. try **connect**ing (if 'provider' appears to Network Manager Applet)
10. finally check **uname -a**

Post all above results in a 'technical look' (brief but data inclusive!)

Regards,
George

---

### Post by GeorgeVita on 2009-07-02
**MF636** on Alpha 2, updated: **02-July**, **2.6.31-1**-generic #13-Ubuntu[INDENT]aprox. same results as below[/INDENT]

**MF636** on Alpha 2, updated: **01-July**, **2.6.30-10**-generic #12-Ubuntu #12-Ubuntu[INDENT]Booted without modem, Plugged in, lsusb shows 19d2:2000, eject ZeroCD, lsusb shows 19d2:0031, from dmesg found the following **Oops** and the system **frozen** at all! Note the **wrong numbering** on ttyUSBs[/INDENT]
```

[  242.768726] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  242.768844] option 1-2:1.0: device disconnected
[  242.769752] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  242.769857] option 1-2:1.1: device disconnected
[  242.770004] option: option_instat_callback: error -108
[  242.770985] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  242.771094] option 1-2:1.3: device disconnected
[  242.880144] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  243.015049] option 1-2:1.3: GSM modem (1-port) converter detected
[  243.015398] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  243.015520] option 1-2:1.1: GSM modem (1-port) converter detected
[  243.015733] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  243.015844] option 1-2:1.0: GSM modem (1-port) converter detected
[  243.016157] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  248.985672] BUG: unable to handle kernel NULL pointer dereference at 0000002b
[  248.985699] IP: [<c03da6d3>] usb_kill_urb+0x13/0xa0
[  248.985728] *pde = 7e5c7067 
[  248.985740] Oops: 0000 [#2] SMP 
[  248.985753] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/ASUS010:00/rfkill/rfkill0/state
```


**MF636** on Alpha 2, updated: **30-June**, **2.6.30-10**-generic (#??)[indent]After plugged in, lsusb shows 19d2:2000
ZeroCD icon appeared, pop up window anounces Software...
I Eject it (from desktop environment)
the lsusb changed to 19d2:0031
two (2) providers found via network manager icon
I got connected from the 2nd one and ... **Everything seems OK!**[/indent]

---

### Post by GeorgeVita on 2009-07-02
The reference list below describes the behaviour of ZTE modems on previous versions of Ubuntu.

Great thread with info regarding ZTE modems and network Manager:
[http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)

Specific ideas targeted on "where could be the problem":
[http://ubuntuforums.org/showthread.php?p=7537029](http://ubuntuforums.org/showthread.php?p=7537029)
[http://ubuntuforums.org/showthread.php?p=7539275](http://ubuntuforums.org/showthread.php?p=7539275)

Behaviour of ZTE MF636 on previous Ubuntu versions:
[http://www.acomelectronics.com/GeorgeVita/ZTEonUBUNTU.html](http://www.acomelectronics.com/GeorgeVita/ZTEonUBUNTU.html)

A big step done after "Remove ZTE Modem ZeroCD from unusual_devs.h":
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/373821](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/373821)

A "working solution" with wvdial on 8.10:
[http://ubuntuforums.org/showpost.php?p=6511814&postcount=2](http://ubuntuforums.org/showpost.php?p=6511814&postcount=2)


>>> If you have other links with useful data post them.

---

### Post by GeorgeVita on 2009-07-23
**ZTE MF636** (original state 0x19d2:0x2000) on **EeePC 1000H** with a clean installation of Ubuntu **9.10 Alpha3** (2.6.31-3-generic #19-Ubuntu) **crashes the system**: totally frozen after step 6 of my first post.

Alpha3 and a previous daily image (12-JUNE-09) both downloaded successfully using the same hardware configuration, running Karmic Alpha2 with **network-manager 'purged'** and connected via **wvdial**. The download time was almost 11 hours all the time connected!

I also tried PPA version of network-manager (on Alpha2+updates) with the same results. Many other users of similar but not the same type of modem have better results! There is always a possibility something not working well with my h/w setup (1000H & MF636).

**It would be helpful if anybody could test the MF636 on any other h/w running Alpha3** and post here the results. The proposed test is that on my 1st post of this thread.

**UPDATE_1:** same results with MF636 attached before boot (on Alpha3+updates)

**UPDATE_2:** I followed instructions from [https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa) and I installed version **0.7.1.git.4.364ab2f86-0ubuntu1~nm1** (on Alpha3+updates with kernel=2.6.31-3-generic #19-Ubuntu)
The crash happens again with the modem attached before or after boot. The  ZeroCD re-appears into dmesg (sr0 or sr1) before the freeze of the system.

**UPDATE_3:** approx. same results with linux-image-2.6.31-020631rc4-generic_2.6.31-020631rc4_i386

... now formatting to install 9.10 Alpha3 from .iso (23-July)

Thanks in advance,
George

---

### Post by Sergiu Bivol on 2009-07-24
Hmmm... you are getting the freezes that I used to experience in Jaunty and Karmic < alpha 2. Since Karmic switched to kernel 2.6.31, it is more stable (but it does freeze occasionally). 

Could you try the udev rule that I posted [here]("http://ubuntuforums.org/showpost.php?p=7624549&postcount=61")? It should behave the same as manually ejecting the CD-ROM, so it's worth trying. 

As far as I'm concerned, MF637 works pretty well on latest Karmic kernel with Rick's [nm-modem-probe]("http://ubuntuforums.org/showpost.php?p=7636176&postcount=67").

Have you reported bugs on Launchpad regarding the freezes? We could try to report a bug upstream regarding the "option" driver (I'm almost sure it is causing all this mess).

---

### Post by GeorgeVita on 2009-07-26
Hi **Sergiu Bivol**,
I tried your udev rule to auto exect with the 9.10 alpha3 and it was looping as the drive reappears some seconds after the eject.

I think that there is the problem. After ejecting, the system must not 'reset/scan' it again when it reappears.

But this is a minor problem now as ... an update of the system messed up some things in my EeePC and I cannot connect neither with the Huawei E169 with the new kernel 2.6.31-4 (!), I faced an Oops:
```
[  168.323201] tty_port_close_start: count = -1
[  168.323498] BUG: unable to handle kernel NULL pointer dereference at 00000014
[  168.327102] IP: [<f816e2e3>] serial_tiocmset+0x23/0xa0 [usbserial]
[  168.327102] *pde = 7dce1067 
[  168.327102] Oops: 0000 [#1] SMP 
[  168.327102] last sysfs file: /sys/devices/virtual/sound/timer/uevent
[  168.327102] Modules linked in: option usbserial usb_storage binfmt_misc ppdev bridge stp bnep lp parport snd_hda_codec_realtek snd_hda_intel snd_hda_codec joydev snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device uvcvideo snd btusb videodev rt2860sta(C) soundcore pcspkr v4l1_compat psmouse serio_raw snd_page_alloc eeepc_laptop atl1e fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp agpgart
[  168.327102] 
[  168.327102] Pid: 3117, comm: pppd Tainted: G         C (2.6.31-4-generic #22-Ubuntu) 1000H
[  168.327102] EIP: 0060:[<f816e2e3>] EFLAGS: 00010246 CPU: 0
[  168.327102] EIP is at serial_tiocmset+0x23/0xa0 [usbserial]
[  168.327102] EAX: f67a0000 EBX: f67a0000 ECX: 00000000 EDX: 00000000
[  168.327102] ESI: 00000000 EDI: f5771880 EBP: f57b1f1c ESP: f57b1efc
[  168.327102]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[  168.327102] Process pppd (pid: 3117, ti=f57b0000 task=f574d7f0 task.ti=f57b0000)
[  168.327102] Stack:
[  168.327102]  000000bc 00000002 f44f53b8 f57b1f78 c01e1739 f8171fe0 f67a0000 f5771880
[  168.327102] <0> f57b1f50 c0377798 00000002 091369a8 f67a0000 bff4aeb4 00005417 00000000
[  168.327102] <0> 00000003 00000000 c0377480 c05984e0 bff4aeb4 f57b1f70 c01ee1cc f579b000
[  168.327102] Call Trace:
[  168.327102]  [<c01e1739>] ? do_readv_writev+0x149/0x1c0
[  168.327102]  [<c0377798>] ? tty_ioctl+0x318/0x620
[  168.327102]  [<c0377480>] ? tty_ioctl+0x0/0x620
[  168.327102]  [<c01ee1cc>] ? vfs_ioctl+0x1c/0x90
[  168.327102]  [<c01e9766>] ? putname+0x26/0x40
[  168.327102]  [<c01ee4f1>] ? do_vfs_ioctl+0x71/0x310
[  168.327102]  [<c01e17f5>] ? vfs_writev+0x45/0x60
[  168.327102]  [<c01ee7ef>] ? sys_ioctl+0x5f/0x80
[  168.327102]  [<c010334c>] ? syscall_call+0x7/0xb
[  168.327102] Code: 00 8d bc 27 00 00 00 00 55 89 e5 83 ec 20 89 7d fc 89 d7 8b 15 24 68 17 f8 89 5d f4 89 c3 89 75 f8 8b b0 3c 01 00 00 85 d2 75 34 <8b> 46 14 85 c0 74 59 8b 06 8b 40 04 8b b0 a8 00 00 00 b8 ea ff 
[  168.327102] EIP: [<f816e2e3>] serial_tiocmset+0x23/0xa0 [usbserial] SS:ESP 0068:f57b1efc
[  168.327102] CR2: 0000000000000014
[  168.543266] ---[ end trace 747168e11c2900da ]---
[  224.721086] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
``` 
... some more stucks etc.

I decided to leave it for some days to stabilize again (I am updating/testing every day). Till then I am using 9.04 on SDHC and Puppy 4.2.1 on SD (Puppy has wvdial v1.53 and usbserial driver so _I can connect with all my 3G USB modems!_)

As you know there is no need to post a new Oops to Launchpad (yours are waiting there).

Thanks and regards,
George

---

### Post by Sergiu Bivol on 2009-07-27
> **GeorgeVita said:**
> I tried your udev rule to auto exect with the 9.10 alpha3 and it was looping as the drive reappears some seconds after the eject.


Hmmm, it should reappear as a modem AND mass storage device after ejecting, NOT as a CD-ROM. Can you confirm that it reconnects as a CD-ROM after ejecting?

> 
I think that there is the problem. After ejecting, the system must not 'reset/scan' it again when it reappears.


That udev rule checks for 19d2:2000, so it has no effect after ejecting the CD-ROM, because the device reconnects as 19d2:0031.

> 
But this is a minor problem now as ... an update of the system messed up some things in my EeePC and I cannot connect neither with the Huawei E169 with the new kernel 2.6.31-4 (!), I faced an Oops:
[CODE][  168.323201] tty_port_close_start: count = -1
[  168.323498] BUG: unable to handle kernel NULL pointer dereference at 00000014
...


Damn, I upgraded to kernel 2.6.31-4 and now I get the same errors, freezes, panics, and so on. It doesn't connect, no matter what.

> 
As you know there is no need to post a new Oops to Launchpad (yours are waiting there).


Yeah, I have ~100 more kernel panics to report, but nobody cares, so there's no point reporting them.

---

### Post by GeorgeVita on 2009-07-27
> **Sergiu Bivol said:**
> Hmmm, it should reappear as a modem AND mass storage device after ejecting, NOT as a CD-ROM. Can you confirm that it reconnects as a CD-ROM after ejecting?


This is the part of System > Administration > Log File Viewer > **syslog**

Modem: **ZTE MF636** (in original state 19d2:2000)
Ubuntu: **2.6.31-3-generic #19**
Actions: Boot without the modem, wait for the system to load, attach modem, sr0 created, **sudo eject sr0**, wait and the system stucks after re-creation of sr0 (icon shown on desktop)

```
Jul 27 23:20:13 KKa3 wpa_supplicant[2258]: CTRL-EVENT-SCAN-RESULTS 
Jul 27 23:20:38 KKa3 kernel: [   25.801319]  domain 0: span 0-1 level SIBLING
Jul 27 23:20:38 KKa3 kernel: [   25.801325]   groups: 1 0
Jul 27 23:20:38 KKa3 kernel: [   25.820149] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
Jul 27 23:20:38 KKa3 kernel: [   30.972053] ra0: no IPv6 routers present
Jul 27 23:20:38 KKa3 kernel: [   36.750121] integrated sync not supported
Jul 27 23:20:38 KKa3 kernel: [   36.891102] integrated sync not supported
Jul 27 23:20:38 KKa3 kernel: [   37.030180] integrated sync not supported
Jul 27 23:20:38 KKa3 kernel: [   39.038279] integrated sync not supported
Jul 27 23:20:38 KKa3 kernel: [   45.719773] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
Jul 27 23:20:38 KKa3 kernel: [   71.272084] usb 1-2: new high speed USB device using ehci_hcd and address 4
Jul 27 23:20:38 KKa3 kernel: [   71.417504] usb 1-2: configuration #1 chosen from 1 choice
Jul 27 23:20:38 KKa3 kernel: [   71.629121] Initializing USB Mass Storage driver...
Jul 27 23:20:38 KKa3 kernel: [   71.630086] scsi2 : SCSI emulation for USB Mass Storage devices
Jul 27 23:20:38 KKa3 kernel: [   71.630468] usbcore: registered new interface driver usb-storage
Jul 27 23:20:38 KKa3 kernel: [   71.630481] USB Mass Storage support registered.
Jul 27 23:20:38 KKa3 kernel: [   71.630757] usb-storage: device found at 4
Jul 27 23:20:38 KKa3 kernel: [   71.630764] usb-storage: waiting for device to settle before scanning
Jul 27 23:20:43 KKa3 wpa_supplicant[2258]: CTRL-EVENT-SCAN-RESULTS 
Jul 27 23:20:43 KKa3 kernel: [   71.676832] USB Serial support registered for GSM modem (1-port)
Jul 27 23:20:43 KKa3 kernel: [   71.677560] usbcore: registered new interface driver option
Jul 27 23:20:43 KKa3 kernel: [   71.677570] option: v0.7.2:USB Driver for GSM modems
Jul 27 23:20:43 KKa3 kernel: [   75.717485] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
Jul 27 23:20:43 KKa3 kernel: [   76.630501] usb-storage: device scan complete
Jul 27 23:20:43 KKa3 kernel: [   76.632391] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Jul 27 23:20:43 KKa3 kernel: [   76.663863] sr0: scsi-1 drive
Jul 27 23:20:43 KKa3 kernel: [   76.663873] Uniform CD-ROM driver Revision: 3.20
Jul 27 23:20:43 KKa3 kernel: [   76.665498] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jul 27 23:21:09 KKa3 kernel: [   76.668715] sr 2:0:0:0: Attached scsi generic sg1 type 5
Jul 27 23:21:09 KKa3 kernel: [   90.181272] ISO 9660 Extensions: Microsoft Joliet Level 1
Jul 27 23:21:09 KKa3 kernel: [   90.201906] ISOFS: changing to secondary root
Jul 27 23:21:09 KKa3 kernel: [   97.063899] usb 1-2: USB disconnect, address 4
Jul 27 23:21:09 KKa3 kernel: [  102.272085] usb 1-2: new high speed USB device using ehci_hcd and address 5
Jul 27 23:21:09 KKa3 kernel: [  102.403529] usb 1-2: configuration #1 chosen from 1 choice
Jul 27 23:21:09 KKa3 kernel: [  102.405956] option 1-2:1.0: GSM modem (1-port) converter detected
Jul 27 23:21:14 KKa3 kernel: [  102.406214] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 27 23:21:14 KKa3 kernel: [  102.406512] option 1-2:1.1: GSM modem (1-port) converter detected
Jul 27 23:21:14 KKa3 kernel: [  102.406717] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Jul 27 23:21:14 KKa3 kernel: [  102.408409] scsi3 : SCSI emulation for USB Mass Storage devices
Jul 27 23:21:14 KKa3 kernel: [  102.411082] usb-storage: device found at 5
Jul 27 23:21:14 KKa3 kernel: [  102.411097] usb-storage: waiting for device to settle before scanning
Jul 27 23:21:14 KKa3 kernel: [  102.411435] option 1-2:1.3: GSM modem (1-port) converter detected
Jul 27 23:21:14 KKa3 kernel: [  102.411765] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Jul 27 23:21:17 KKa3 kernel: [  107.551963] usb-storage: device scan complete
Jul 27 23:21:17 KKa3 kernel: [  107.555455] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Jul 27 23:21:17 KKa3 kernel: [  107.556352] scsi 3:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Jul 27 23:21:17 KKa3 kernel: [  107.559686] sd 3:0:0:0: Attached scsi generic sg1 type 0
Jul 27 23:21:17 KKa3 kernel: [  110.569629] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jul 27 23:21:17 KKa3 kernel: [  110.569711] option 1-2:1.0: device disconnected
Jul 27 23:21:18 KKa3 kernel: [  110.570116] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jul 27 23:21:18 KKa3 kernel: [  110.570173] option 1-2:1.1: device disconnected
Jul 27 23:21:18 KKa3 kernel: [  110.570295] option: option_instat_callback: error -108
Jul 27 23:21:18 KKa3 kernel: [  110.570791] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jul 27 23:21:18 KKa3 kernel: [  110.570846] option 1-2:1.3: device disconnected
Jul 27 23:21:18 KKa3 kernel: [  110.688084] usb 1-2: reset high speed USB device using ehci_hcd and address 5
Jul 27 23:21:18 KKa3 kernel: [  110.823919] option 1-2:1.3: GSM modem (1-port) converter detected
Jul 27 23:21:18 KKa3 kernel: [  110.824311] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 27 23:21:18 KKa3 kernel: [  110.824446] option 1-2:1.1: GSM modem (1-port) converter detected
Jul 27 23:21:18 KKa3 kernel: [  110.824654] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Jul 27 23:21:18 KKa3 kernel: [  110.824778] option 1-2:1.0: GSM modem (1-port) converter detected
Jul 27 23:21:18 KKa3 kernel: [  110.824974] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Jul 27 23:21:18 KKa3 kernel: [  110.837544] sr0: scsi-1 drive
Jul 27 23:21:18 KKa3 kernel: [  110.838126] sr 3:0:0:1: Attached scsi CD-ROM sr0
Jul 27 23:21:18 KKa3 kernel: [  110.838504] sr 3:0:0:1: Attached scsi generic sg2 type 5

```

I am going to test again the udev rule and make a new post...
G

---

### Post by GeorgeVita on 2009-07-27
New test after **sudo gedit /etc/udev/rules.d/zte_eject.rules** with:
```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```

Part of syslog with **kernel 2.6.31-3.19**
```
Jul 27 23:50:09 KKa3 wpa_supplicant[2272]: CTRL-EVENT-SCAN-RESULTS 
Jul 27 23:50:09 KKa3 kernel: [   25.829084] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
Jul 27 23:50:09 KKa3 kernel: [   31.192065] ra0: no IPv6 routers present
Jul 27 23:50:09 KKa3 kernel: [   36.882175] integrated sync not supported
Jul 27 23:50:09 KKa3 kernel: [   37.022079] integrated sync not supported
Jul 27 23:50:09 KKa3 kernel: [   37.162076] integrated sync not supported
Jul 27 23:50:09 KKa3 kernel: [   39.190229] integrated sync not supported
Jul 27 23:50:09 KKa3 kernel: [   45.724115] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
Jul 27 23:50:09 KKa3 kernel: [   75.721649] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
Jul 27 23:50:11 KKa3 kernel: [  115.720528] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
Jul 27 23:50:11 KKa3 kernel: [  118.040098] usb 1-2: new high speed USB device using ehci_hcd and address 4
Jul 27 23:50:11 KKa3 kernel: [  118.185600] usb 1-2: configuration #1 chosen from 1 choice
Jul 27 23:50:11 KKa3 kernel: [  118.306338] Initializing USB Mass Storage driver...
Jul 27 23:50:11 KKa3 kernel: [  118.307662] scsi2 : SCSI emulation for USB Mass Storage devices
Jul 27 23:50:11 KKa3 kernel: [  118.308097] usb-storage: device found at 4
Jul 27 23:50:11 KKa3 kernel: [  118.308104] usb-storage: waiting for device to settle before scanning
Jul 27 23:50:11 KKa3 kernel: [  118.308137] usbcore: registered new interface driver usb-storage
Jul 27 23:50:16 KKa3 kernel: [  118.308244] USB Mass Storage support registered.
Jul 27 23:50:16 KKa3 kernel: [  118.346554] USB Serial support registered for GSM modem (1-port)
Jul 27 23:50:16 KKa3 kernel: [  118.347099] usbcore: registered new interface driver option
Jul 27 23:50:16 KKa3 kernel: [  118.347114] option: v0.7.2:USB Driver for GSM modems
Jul 27 23:50:16 KKa3 kernel: [  123.309575] usb-storage: device scan complete
Jul 27 23:50:16 KKa3 kernel: [  123.311552] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Jul 27 23:50:16 KKa3 kernel: [  123.350734] sr0: scsi-1 drive
Jul 27 23:50:16 KKa3 kernel: [  123.350746] Uniform CD-ROM driver Revision: 3.20
Jul 27 23:50:22 KKa3 kernel: [  123.352913] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jul 27 23:50:22 KKa3 kernel: [  123.355305] sr 2:0:0:0: Attached scsi generic sg1 type 5
Jul 27 23:50:22 KKa3 kernel: [  123.641267] usb 1-2: USB disconnect, address 4
Jul 27 23:50:22 KKa3 kernel: [  123.644871] scsi 2:0:0:0: rejecting I/O to dead device
Jul 27 23:50:22 KKa3 kernel: [  123.644930] scsi 2:0:0:0: rejecting I/O to dead device
Jul 27 23:50:22 KKa3 kernel: [  123.644963] scsi 2:0:0:0: rejecting I/O to dead device
Jul 27 23:50:22 KKa3 kernel: [  128.572105] usb 1-2: new high speed USB device using ehci_hcd and address 5
Jul 27 23:50:22 KKa3 kernel: [  128.707345] usb 1-2: configuration #1 chosen from 1 choice
Jul 27 23:50:22 KKa3 kernel: [  128.709800] option 1-2:1.0: GSM modem (1-port) converter detected
Jul 27 23:50:22 KKa3 kernel: [  128.710163] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 27 23:50:22 KKa3 kernel: [  128.710629] option 1-2:1.1: GSM modem (1-port) converter detected
Jul 27 23:50:22 KKa3 kernel: [  128.710931] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Jul 27 23:50:22 KKa3 kernel: [  128.712735] scsi3 : SCSI emulation for USB Mass Storage devices
Jul 27 23:50:22 KKa3 kernel: [  128.720145] usb-storage: device found at 5
Jul 27 23:50:22 KKa3 kernel: [  128.720160] usb-storage: waiting for device to settle before scanning
Jul 27 23:50:30 KKa3 kernel: [  128.720514] option 1-2:1.3: GSM modem (1-port) converter detected
Jul 27 23:50:30 KKa3 kernel: [  128.720843] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Jul 27 23:50:30 KKa3 kernel: [  133.865001] usb-storage: device scan complete
Jul 27 23:50:30 KKa3 kernel: [  133.866025] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Jul 27 23:50:30 KKa3 kernel: [  133.866759] scsi 3:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Jul 27 23:50:30 KKa3 kernel: [  133.879496] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Jul 27 23:50:30 KKa3 kernel: [  133.898719] sd 3:0:0:0: Attached scsi generic sg1 type 0
Jul 27 23:50:30 KKa3 pulseaudio[2763]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if3_serial_usb_2
Jul 27 23:50:30 KKa3 kernel: [  136.907083] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jul 27 23:50:30 KKa3 kernel: [  136.907164] option 1-2:1.0: device disconnected
Jul 27 23:50:30 KKa3 kernel: [  136.907573] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jul 27 23:50:30 KKa3 kernel: [  136.907629] option 1-2:1.1: device disconnected
Jul 27 23:50:30 KKa3 kernel: [  136.907750] option: option_instat_callback: error -108
Jul 27 23:50:30 KKa3 kernel: [  136.908213] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jul 27 23:50:30 KKa3 kernel: [  136.908294] option 1-2:1.3: device disconnected
Jul 27 23:50:30 KKa3 kernel: [  137.018643] usb 1-2: reset high speed USB device using ehci_hcd and address 5
Jul 27 23:50:30 KKa3 kernel: [  137.154214] option 1-2:1.3: GSM modem (1-port) converter detected
Jul 27 23:50:30 KKa3 kernel: [  137.154609] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 27 23:50:30 KKa3 kernel: [  137.154799] option 1-2:1.1: GSM modem (1-port) converter detected
Jul 27 23:50:30 KKa3 kernel: [  137.155113] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Jul 27 23:50:30 KKa3 kernel: [  137.155293] option 1-2:1.0: GSM modem (1-port) converter detected
Jul 27 23:50:30 KKa3 kernel: [  137.155587] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Jul 27 23:50:36 KKa3 pulseaudio[2763]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if0_serial_usb_0
Jul 27 23:50:40 KKa3 udevd-work[2985]: chown(/dev/.tmp-char-188:0, 0, 0) failed: No such file or directory
Jul 27 23:50:40 KKa3 kernel: [  137.159619] sr0: scsi-1 drive
Jul 27 23:50:40 KKa3 kernel: [  137.160188] sr 3:0:0:1: Attached scsi CD-ROM sr0
Jul 27 23:50:40 KKa3 kernel: [  137.160533] sr 3:0:0:1: Attached scsi generic sg2 type 5
Jul 27 23:50:40 KKa3 udevd-work[2985]: chmod(/dev/.tmp-char-188:0, 0000) failed: No such file or directory
Jul 27 23:50:40 KKa3 kernel: [  142.282573] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jul 27 23:50:40 KKa3 kernel: [  142.282789] option 1-2:1.0: device disconnected
Jul 27 23:50:40 KKa3 kernel: [  142.282959] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jul 27 23:50:40 KKa3 kernel: [  142.283021] option 1-2:1.1: device disconnected
Jul 27 23:50:40 KKa3 kernel: [  142.283139] option: option_instat_callback: error -108
Jul 27 23:50:40 KKa3 pulseaudio[2763]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if1_serial_usb_1
Jul 27 23:50:40 KKa3 usb_id[3031]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.1/ttyUSB1/tty/ttyUSB1'
Jul 27 23:50:40 KKa3 pulseaudio[2763]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if3_serial_usb_0
Jul 27 23:50:40 KKa3 usb_id[3032]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.1/ttyUSB1/tty/ttyUSB1'
Jul 27 23:50:40 KKa3 pulseaudio[2763]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if1_serial_usb_1
Jul 27 23:50:40 KKa3 kernel: [  147.284486] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jul 27 23:50:40 KKa3 kernel: [  147.284566] option 1-2:1.3: device disconnected
Jul 27 23:50:40 KKa3 kernel: [  147.396105] usb 1-2: reset high speed USB device using ehci_hcd and address 5
Jul 27 23:50:40 KKa3 kernel: [  147.530578] option 1-2:1.3: GSM modem (1-port) converter detected
Jul 27 23:50:40 KKa3 kernel: [  147.530917] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 27 23:50:40 KKa3 kernel: [  147.531051] option 1-2:1.1: GSM modem (1-port) converter detected
Jul 27 23:50:40 KKa3 kernel: [  147.531254] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1

```


Part of syslog with **kernel 2.6.31-4.22**
```
Jul 27 23:53:16 KKa3 kernel: [   77.723569] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
Jul 27 23:53:16 KKa3 kernel: [   98.508096] usb 1-2: new high speed USB device using ehci_hcd and address 4
Jul 27 23:53:16 KKa3 kernel: [   98.653618] usb 1-2: configuration #1 chosen from 1 choice
Jul 27 23:53:16 KKa3 kernel: [   98.767047] Initializing USB Mass Storage driver...
Jul 27 23:53:16 KKa3 kernel: [   98.769089] scsi2 : SCSI emulation for USB Mass Storage devices
Jul 27 23:53:16 KKa3 kernel: [   98.769581] usb-storage: device found at 4
Jul 27 23:53:16 KKa3 kernel: [   98.769589] usb-storage: waiting for device to settle before scanning
Jul 27 23:53:16 KKa3 kernel: [   98.769621] usbcore: registered new interface driver usb-storage
Jul 27 23:53:16 KKa3 kernel: [   98.769725] USB Mass Storage support registered.
Jul 27 23:53:16 KKa3 kernel: [   98.794506] usbcore: registered new interface driver usbserial
Jul 27 23:53:16 KKa3 kernel: [   98.795348] USB Serial support registered for generic
Jul 27 23:53:16 KKa3 kernel: [   98.795576] usbcore: registered new interface driver usbserial_generic
Jul 27 23:53:16 KKa3 kernel: [   98.795587] usbserial: USB Serial Driver core
Jul 27 23:53:16 KKa3 kernel: [   98.812388] USB Serial support registered for GSM modem (1-port)
Jul 27 23:53:16 KKa3 kernel: [   98.813411] usbcore: registered new interface driver option
Jul 27 23:53:26 KKa3 kernel: [   98.813421] option: v0.7.2:USB Driver for GSM modems
Jul 27 23:53:26 KKa3 kernel: [  103.770567] usb-storage: device scan complete
Jul 27 23:53:26 KKa3 kernel: [  103.772522] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Jul 27 23:53:26 KKa3 kernel: [  103.807979] sr0: scsi-1 drive
Jul 27 23:53:26 KKa3 kernel: [  103.807990] Uniform CD-ROM driver Revision: 3.20
Jul 27 23:53:26 KKa3 kernel: [  103.808301] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jul 27 23:53:26 KKa3 kernel: [  103.808487] sr 2:0:0:0: Attached scsi generic sg1 type 5
Jul 27 23:53:26 KKa3 kernel: [  103.923987] usb 1-2: USB disconnect, address 4
Jul 27 23:53:26 KKa3 kernel: [  109.520111] usb 1-2: new high speed USB device using ehci_hcd and address 5
Jul 27 23:53:26 KKa3 kernel: [  109.655603] usb 1-2: configuration #1 chosen from 1 choice
Jul 27 23:53:26 KKa3 kernel: [  109.658060] option 1-2:1.0: GSM modem (1-port) converter detected
Jul 27 23:53:26 KKa3 kernel: [  109.658432] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 27 23:53:26 KKa3 kernel: [  109.658896] option 1-2:1.1: GSM modem (1-port) converter detected
Jul 27 23:53:26 KKa3 kernel: [  109.659216] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Jul 27 23:53:26 KKa3 kernel: [  109.687734] scsi3 : SCSI emulation for USB Mass Storage devices
Jul 27 23:53:26 KKa3 kernel: [  109.688571] option 1-2:1.3: GSM modem (1-port) converter detected
Jul 27 23:53:32 KKa3 kernel: [  109.688840] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Jul 27 23:53:32 KKa3 kernel: [  109.689027] usb-storage: device found at 5
Jul 27 23:53:32 KKa3 kernel: [  109.689034] usb-storage: waiting for device to settle before scanning
Jul 27 23:53:32 KKa3 kernel: [  114.804970] usb-storage: device scan complete
Jul 27 23:53:32 KKa3 kernel: [  114.806153] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Jul 27 23:53:32 KKa3 kernel: [  114.807133] scsi 3:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Jul 27 23:53:32 KKa3 kernel: [  114.814347] sd 3:0:0:0: Attached scsi generic sg1 type 0
Jul 27 23:53:35 KKa3 wpa_supplicant[2269]: CTRL-EVENT-SCAN-RESULTS 
Jul 27 23:53:37 KKa3 kernel: [  114.817771] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Jul 27 23:53:37 KKa3 kernel: [  117.724005] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
Jul 27 23:53:37 KKa3 kernel: [  117.833704] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jul 27 23:53:37 KKa3 kernel: [  117.833786] option 1-2:1.0: device disconnected
Jul 27 23:53:37 KKa3 kernel: [  117.834178] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jul 27 23:53:37 KKa3 kernel: [  117.834235] option 1-2:1.1: device disconnected
Jul 27 23:53:37 KKa3 kernel: [  117.834355] option: option_instat_callback: error -108
Jul 27 23:53:37 KKa3 pulseaudio[2760]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if3_serial_usb_2
Jul 27 23:53:37 KKa3 kernel: [  119.808474] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jul 27 23:53:37 KKa3 kernel: [  119.808537] option 1-2:1.3: device disconnected
Jul 27 23:53:37 KKa3 kernel: [  119.920082] usb 1-2: reset high speed USB device using ehci_hcd and address 5
Jul 27 23:53:37 KKa3 kernel: [  120.052324] option 1-2:1.3: GSM modem (1-port) converter detected
Jul 27 23:53:37 KKa3 kernel: [  120.052664] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 27 23:53:37 KKa3 kernel: [  120.052794] option 1-2:1.1: GSM modem (1-port) converter detected
Jul 27 23:53:37 KKa3 kernel: [  120.052992] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Jul 27 23:53:42 KKa3 kernel: [  120.053157] option 1-2:1.0: GSM modem (1-port) converter detected
Jul 27 23:53:42 KKa3 kernel: [  120.053376] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Jul 27 23:53:42 KKa3 kernel: [  120.061117] sr0: scsi-1 drive
Jul 27 23:53:42 KKa3 kernel: [  120.061677] sr 3:0:0:1: Attached scsi CD-ROM sr0
Jul 27 23:53:42 KKa3 kernel: [  120.062025] sr 3:0:0:1: Attached scsi generic sg2 type 5
Jul 27 23:53:42 KKa3 kernel: [  125.125576] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jul 27 23:53:42 KKa3 kernel: [  125.125686] option 1-2:1.0: device disconnected
Jul 27 23:53:43 KKa3 pulseaudio[2760]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if0_serial_usb_0
Jul 27 23:53:47 KKa3 udevd-work[2981]: chown(/dev/.tmp-char-188:0, 0, 0) failed: No such file or directory
Jul 27 23:53:47 KKa3 udevd-work[2981]: chmod(/dev/.tmp-char-188:0, 0000) failed: No such file or directory
Jul 27 23:53:47 KKa3 usb_id[3031]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.1/ttyUSB1/tty/ttyUSB1'
Jul 27 23:53:47 KKa3 usb_id[3032]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.1/ttyUSB1/tty/ttyUSB1'
Jul 27 23:53:47 KKa3 pulseaudio[2760]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if1_serial_usb_1
Jul 27 23:53:47 KKa3 pulseaudio[2760]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if3_serial_usb_0
Jul 27 23:53:47 KKa3 pulseaudio[2760]: module-hal-detect.c: D-Bus error while parsing HAL data: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_19d2_31_1234567890ABCDEF_if1_serial_usb_1
Jul 27 23:53:47 KKa3 kernel: [  125.125859] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jul 27 23:53:47 KKa3 kernel: [  125.125921] option 1-2:1.1: device disconnected
Jul 27 23:53:47 KKa3 kernel: [  125.126040] option: option_instat_callback: error -108
Jul 27 23:53:47 KKa3 kernel: [  130.136403] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jul 27 23:53:47 KKa3 kernel: [  130.136517] option 1-2:1.3: device disconnected
Jul 27 23:53:47 KKa3 kernel: [  130.245151] usb 1-2: reset high speed USB device using ehci_hcd and address 5
Jul 27 23:53:47 KKa3 kernel: [  130.379572] option 1-2:1.3: GSM modem (1-port) converter detected
Jul 27 23:53:52 KKa3 kernel: [  130.379911] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
Jul 27 23:53:52 KKa3 kernel: [  130.380093] option 1-2:1.1: GSM modem (1-port) converter detected
Jul 27 23:53:52 KKa3 kernel: [  130.380294] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
Jul 27 23:53:52 KKa3 kernel: [  130.380417] option 1-2:1.0: GSM modem (1-port) converter detected
Jul 27 23:53:52 KKa3 kernel: [  130.380615] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
Jul 27 23:53:52 KKa3 kernel: [  133.469427] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jul 27 23:53:52 KKa3 kernel: [  133.469499] option 1-2:1.0: device d

```

OK, looking at the above some new ideas ... like changing the .fdi file but as we know all these are 'floating'.

Thanks,
George

---

### Post by Sergiu Bivol on 2009-07-28
> **GeorgeVita said:**
> 
Part of syslog with **kernel 2.6.31-4.22**
```

...
Jul 27 **23:53:32** KKa3 kernel: [  114.806153] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Jul 27 **23:53:32** KKa3 kernel: [  114.807133] scsi 3:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
...

```


Nope, this is not possible. The device is either a Modem+MMC, or CD-ROM.
Once switched to modem mode, it does NOT switch back to CD-ROM mode, unless unplugged.
Yours looks like both of them at the same time. Something else is breaking your modem. Please purge usb-modeswitch, .fdi files and any other stuff that could touch the modem. That udev rule that you created is enough for mode-switching (I never had issues with it).

> 
OK, looking at the above some new ideas ... like changing the .fdi file but as we know all these are 'floating'.


There is no need to touch .fdi files - hal is deprecated (replaced by udev + DeviceKit). Anyway, you don't need HAL.

I installed the vanilla kernel from 23 July, and it is the most broken kernel I have ever seen. Even pppd was freezing it.

On the other hand, the kernel that appeared today [1] works great as far as I can tell (no freezes, no Oops). Could you please give it a go and post you results?

[1] [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2009-07-28/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2009-07-28/)

---

### Post by Hairy_Palms on 2009-07-28
my ZTE MF627 works fine, but mine came with native linux software so dont know if it works with NM or not, havent tried.

---

### Post by GeorgeVita on 2009-07-28
Hi **Hairy_Palms**,
> **Hairy_Palms said:**
> my ZTE MF627 works fine, but mine came with native linux software so dont know if it works with NM or not, havent tried.Hope this would be the 'standard way' in the future and just download some info/settings from the manufacturer's site. In your case this is probably an offer from your provider.

Hi **Sergiu Bivol**, I deleted the 10-modem.fdi file, dnld & install kernel linux-image-2.6.31-999-generic_2.6.31-999.1248771614_i386 (only kernel and not headers) and your 'eject' rule remains.

After reboot, system loaded, 2 crash reports detected (usplash, nautilus), modem attached, green led got ON-OFF-ON (eject done), blue led light but provider never appeared to NM selection for connection. After some minutes I disconnected. The system NOT FROZEN!

Below is the dmesg from the attachment till the removal:
```
[  367.580205] usb 1-2: new high speed USB device using ehci_hcd and address 4
[  367.725749] usb 1-2: configuration #1 chosen from 1 choice
[  368.153855] Initializing USB Mass Storage driver...
[  368.156769] scsi2 : SCSI emulation for USB Mass Storage devices
[  368.157606] usbcore: registered new interface driver usb-storage
[  368.158678] USB Mass Storage support registered.
[  368.159426] usb-storage: device found at 4
[  368.159441] usb-storage: waiting for device to settle before scanning
[  368.196916] usbcore: registered new interface driver usbserial
[  368.199589] USB Serial support registered for generic
[  368.200831] usbcore: registered new interface driver usbserial_generic
[  368.200842] usbserial: USB Serial Driver core
[  368.216225] USB Serial support registered for GSM modem (1-port)
[  368.218521] usbcore: registered new interface driver option
[  368.218535] option: v0.7.2:USB Driver for GSM modems
[  373.157595] usb-storage: device scan complete
[  373.159528] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  373.186933] sr0: scsi-1 drive
[  373.186943] Uniform CD-ROM driver Revision: 3.20
[  373.188051] sr 2:0:0:0: Attached scsi CD-ROM sr0
[  373.189959] sr 2:0:0:0: Attached scsi generic sg1 type 5
[  373.294331] usb 1-2: USB disconnect, address 4
[  378.124138] usb 1-2: new high speed USB device using ehci_hcd and address 5
[  378.259630] usb 1-2: configuration #1 chosen from 1 choice
[  378.261915] option 1-2:1.0: GSM modem (1-port) converter detected
[  378.262163] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  378.262466] option 1-2:1.1: GSM modem (1-port) converter detected
[  378.262668] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  378.266640] scsi3 : SCSI emulation for USB Mass Storage devices
[  378.270675] usb-storage: device found at 5
[  378.270688] usb-storage: waiting for device to settle before scanning
[  378.271087] option 1-2:1.3: GSM modem (1-port) converter detected
[  378.271536] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  383.393160] usb-storage: device scan complete
[  383.394067] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[  383.394934] scsi 3:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  383.406715] sd 3:0:0:0: Attached scsi generic sg1 type 0
[  383.407518] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  386.408875] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  386.408946] option 1-2:1.0: device disconnected
[  386.409391] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  386.409445] option 1-2:1.1: device disconnected
[  386.409583] option: option_instat_callback: error -108
[  386.409963] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  386.410015] option 1-2:1.3: device disconnected
[  386.520147] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  386.655088] option 1-2:1.3: GSM modem (1-port) converter detected
[  386.655440] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  386.655570] option 1-2:1.1: GSM modem (1-port) converter detected
[  386.655782] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  386.655906] option 1-2:1.0: GSM modem (1-port) converter detected
[  386.656195] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  386.661047] sr0: scsi-1 drive
[  386.661718] sr 3:0:0:1: Attached scsi CD-ROM sr0
[  386.662057] sr 3:0:0:1: Attached scsi generic sg2 type 5
[  391.741790] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[  391.741883] option 1-2:1.0: device disconnected
[  391.748774] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  391.748857] option 1-2:1.1: device disconnected
[  391.749023] option: option_instat_callback: error -108
[  391.749465] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  391.749521] option 1-2:1.3: device disconnected
[  391.860146] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  391.995086] option 1-2:1.3: GSM modem (1-port) converter detected
[  391.995451] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB6
[  391.995580] option 1-2:1.1: GSM modem (1-port) converter detected
[  391.995789] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB7
[  391.995913] option 1-2:1.0: GSM modem (1-port) converter detected
[  391.996210] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB8
[  397.057876] option1 ttyUSB8: GSM modem (1-port) converter now disconnected from ttyUSB8
[  397.057937] option 1-2:1.0: device disconnected
[  397.100776] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[  397.100871] option 1-2:1.1: device disconnected
[  397.101015] option: option_instat_callback: error -108
[  397.101651] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[  397.101707] option 1-2:1.3: device disconnected
[  397.216137] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  397.350838] option 1-2:1.3: GSM modem (1-port) converter detected
[  397.351184] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  397.351314] option 1-2:1.1: GSM modem (1-port) converter detected
[  397.351518] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  397.351642] option 1-2:1.0: GSM modem (1-port) converter detected
[  397.351855] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  402.432694] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  402.432754] option 1-2:1.0: device disconnected
[  402.440702] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  402.440765] option 1-2:1.1: device disconnected
[  402.440906] option: option_instat_callback: error -108
[  402.441552] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  402.441634] option 1-2:1.3: device disconnected
[  402.553224] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  402.687965] option 1-2:1.3: GSM modem (1-port) converter detected
[  402.688492] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  402.688682] option 1-2:1.1: GSM modem (1-port) converter detected
[  402.689016] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  402.689200] option 1-2:1.0: GSM modem (1-port) converter detected
[  402.689524] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  407.780772] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[  407.780861] option 1-2:1.0: device disconnected
[  407.792800] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  407.792881] option 1-2:1.1: device disconnected
[  407.793047] option: option_instat_callback: error -108
[  407.793493] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  407.793548] option 1-2:1.3: device disconnected
[  407.908158] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  408.041840] option 1-2:1.3: GSM modem (1-port) converter detected
[  408.042193] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  408.042325] option 1-2:1.1: GSM modem (1-port) converter detected
[  408.042531] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB6
[  408.042655] option 1-2:1.0: GSM modem (1-port) converter detected
[  408.042859] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB7
[  408.080713] ISO 9660 Extensions: Microsoft Joliet Level 1
[  408.118673] ISOFS: changing to secondary root
[  416.116892] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[  416.116964] option 1-2:1.0: device disconnected
[  416.117645] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[  416.117702] option 1-2:1.1: device disconnected
[  416.117838] option: option_instat_callback: error -108
[  416.118321] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  416.118376] option 1-2:1.3: device disconnected
[  416.232134] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  416.367096] option 1-2:1.3: GSM modem (1-port) converter detected
[  416.367498] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  416.367653] option 1-2:1.1: GSM modem (1-port) converter detected
[  416.367942] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  416.368176] option 1-2:1.0: GSM modem (1-port) converter detected
[  416.368428] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  424.424879] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  424.424971] option 1-2:1.0: device disconnected
[  424.425444] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  424.425523] option 1-2:1.1: device disconnected
[  424.425692] option: option_instat_callback: error -108
[  424.426125] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  424.426204] option 1-2:1.3: device disconnected
[  424.536195] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  424.671343] option 1-2:1.3: GSM modem (1-port) converter detected
[  424.671698] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  424.671829] option 1-2:1.1: GSM modem (1-port) converter detected
[  424.672110] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  424.672238] option 1-2:1.0: GSM modem (1-port) converter detected
[  424.672444] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  429.740690] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[  429.740741] option 1-2:1.0: device disconnected
[  429.741073] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  429.741108] option 1-2:1.1: device disconnected
[  429.741213] option: option_instat_callback: error -108
[  429.741528] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  429.741561] option 1-2:1.3: device disconnected
[  429.852215] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  429.987218] option 1-2:1.3: GSM modem (1-port) converter detected
[  429.987577] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB6
[  429.987708] option 1-2:1.1: GSM modem (1-port) converter detected
[  429.987921] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB7
[  429.988124] option 1-2:1.0: GSM modem (1-port) converter detected
[  429.988334] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB8
[  438.060898] option1 ttyUSB8: GSM modem (1-port) converter now disconnected from ttyUSB8
[  438.060969] option 1-2:1.0: device disconnected
[  438.061659] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[  438.061716] option 1-2:1.1: device disconnected
[  438.061850] option: option_instat_callback: error -108
[  438.062326] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[  438.062380] option 1-2:1.3: device disconnected
[  438.176133] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  438.311221] option 1-2:1.3: GSM modem (1-port) converter detected
[  438.311622] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  438.311778] option 1-2:1.1: GSM modem (1-port) converter detected
[  438.312151] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  438.312293] option 1-2:1.0: GSM modem (1-port) converter detected
[  438.312513] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  446.380914] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  446.381004] option 1-2:1.0: device disconnected
[  446.381443] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  446.381499] option 1-2:1.1: device disconnected
[  446.381632] option: option_instat_callback: error -108
[  446.382112] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  446.382166] option 1-2:1.3: device disconnected
[  446.492144] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  446.627265] option 1-2:1.3: GSM modem (1-port) converter detected
[  446.627742] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  446.627931] option 1-2:1.1: GSM modem (1-port) converter detected
[  446.628360] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  446.628543] option 1-2:1.0: GSM modem (1-port) converter detected
[  446.628875] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  451.676720] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[  451.676783] option 1-2:1.0: device disconnected
[  451.681760] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  451.681885] option 1-2:1.1: device disconnected
[  451.682083] option: option_instat_callback: error -108
[  451.682599] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  451.682658] option 1-2:1.3: device disconnected
[  451.793151] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  451.927095] option 1-2:1.3: GSM modem (1-port) converter detected
[  451.927456] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB6
[  451.927588] option 1-2:1.1: GSM modem (1-port) converter detected
[  451.927804] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB7
[  451.927927] option 1-2:1.0: GSM modem (1-port) converter detected
[  451.928275] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB8
[  459.988906] option1 ttyUSB8: GSM modem (1-port) converter now disconnected from ttyUSB8
[  459.988996] option 1-2:1.0: device disconnected
[  459.989459] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[  459.989516] option 1-2:1.1: device disconnected
[  459.989650] option: option_instat_callback: error -108
[  459.990124] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[  459.990178] option 1-2:1.3: device disconnected
[  460.100142] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  460.235096] option 1-2:1.3: GSM modem (1-port) converter detected
[  460.235444] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  460.235574] option 1-2:1.1: GSM modem (1-port) converter detected
[  460.235778] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  460.235901] option 1-2:1.0: GSM modem (1-port) converter detected
[  460.236194] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  468.295542] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  468.295661] option 1-2:1.0: device disconnected
[  468.296297] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  468.296378] option 1-2:1.1: device disconnected
[  468.296546] option: option_instat_callback: error -108
[  468.297552] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  468.297641] option 1-2:1.3: device disconnected
[  468.412128] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  468.547100] option 1-2:1.3: GSM modem (1-port) converter detected
[  468.547500] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  468.547658] option 1-2:1.1: GSM modem (1-port) converter detected
[  468.547951] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  468.548176] option 1-2:1.0: GSM modem (1-port) converter detected
[  468.548422] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  476.620905] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[  476.620976] option 1-2:1.0: device disconnected
[  476.621651] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  476.621707] option 1-2:1.1: device disconnected
[  476.621842] option: option_instat_callback: error -108
[  476.622318] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  476.622372] option 1-2:1.3: device disconnected
[  476.732144] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  476.867098] option 1-2:1.3: GSM modem (1-port) converter detected
[  476.867448] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  476.867578] option 1-2:1.1: GSM modem (1-port) converter detected
[  476.867784] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  476.867907] option 1-2:1.0: GSM modem (1-port) converter detected
[  476.868198] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  481.916893] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  481.916961] option 1-2:1.0: device disconnected
[  481.933669] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  481.933784] option 1-2:1.1: device disconnected
[  481.933929] option: option_instat_callback: error -108
[  481.934517] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  481.934571] option 1-2:1.3: device disconnected
[  482.044144] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  482.179100] option 1-2:1.3: GSM modem (1-port) converter detected
[  482.179456] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  482.179586] option 1-2:1.1: GSM modem (1-port) converter detected
[  482.179796] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB6
[  482.179919] option 1-2:1.0: GSM modem (1-port) converter detected
[  482.180216] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB7
[  490.255908] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[  490.256111] option 1-2:1.0: device disconnected
[  490.256556] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[  490.256611] option 1-2:1.1: device disconnected
[  490.256745] option: option_instat_callback: error -108
[  490.257295] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  490.257352] option 1-2:1.3: device disconnected
[  490.369213] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  490.504483] option 1-2:1.3: GSM modem (1-port) converter detected
[  490.504882] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  490.505062] option 1-2:1.1: GSM modem (1-port) converter detected
[  490.505348] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  490.505478] option 1-2:1.0: GSM modem (1-port) converter detected
[  490.505689] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  498.572690] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  498.572786] option 1-2:1.0: device disconnected
[  498.573258] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  498.573315] option 1-2:1.1: device disconnected
[  498.573449] option: option_instat_callback: error -108
[  498.573936] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  498.573990] option 1-2:1.3: device disconnected
[  498.688160] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  498.823093] option 1-2:1.3: GSM modem (1-port) converter detected
[  498.823460] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  498.823604] option 1-2:1.1: GSM modem (1-port) converter detected
[  498.823839] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  498.823971] option 1-2:1.0: GSM modem (1-port) converter detected
[  498.824269] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  503.877695] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[  503.877755] option 1-2:1.0: device disconnected
[  503.893833] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  503.893897] option 1-2:1.1: device disconnected
[  503.894038] option: option_instat_callback: error -108
[  503.894663] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  503.894719] option 1-2:1.3: device disconnected
[  504.008133] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  504.147404] option 1-2:1.3: GSM modem (1-port) converter detected
[  504.147876] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB6
[  504.148151] option 1-2:1.1: GSM modem (1-port) converter detected
[  504.148495] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB7
[  504.148680] option 1-2:1.0: GSM modem (1-port) converter detected
[  504.149003] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB8
[  512.216709] option1 ttyUSB8: GSM modem (1-port) converter now disconnected from ttyUSB8
[  512.216773] option 1-2:1.0: device disconnected
[  512.217460] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[  512.217516] option 1-2:1.1: device disconnected
[  512.217651] option: option_instat_callback: error -108
[  512.218134] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[  512.218190] option 1-2:1.3: device disconnected
[  512.328168] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  512.463353] option 1-2:1.3: GSM modem (1-port) converter detected
[  512.463705] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  512.463837] option 1-2:1.1: GSM modem (1-port) converter detected
[  512.464122] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  512.464249] option 1-2:1.0: GSM modem (1-port) converter detected
[  512.464453] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  520.540919] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  520.541021] option 1-2:1.0: device disconnected
[  520.541460] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  520.541517] option 1-2:1.1: device disconnected
[  520.541652] option: option_instat_callback: error -108
[  520.542136] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  520.542191] option 1-2:1.3: device disconnected
[  520.652167] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  520.787354] option 1-2:1.3: GSM modem (1-port) converter detected
[  520.787705] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  520.787835] option 1-2:1.1: GSM modem (1-port) converter detected
[  520.788126] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  520.788253] option 1-2:1.0: GSM modem (1-port) converter detected
[  520.788467] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  525.841788] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[  525.841873] option 1-2:1.0: device disconnected
[  525.854635] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  525.854719] option 1-2:1.1: device disconnected
[  525.854886] option: option_instat_callback: error -108
[  525.855292] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  525.855370] option 1-2:1.3: device disconnected
[  525.965167] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  526.103106] option 1-2:1.3: GSM modem (1-port) converter detected
[  526.103463] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB6
[  526.103593] option 1-2:1.1: GSM modem (1-port) converter detected
[  526.103807] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB7
[  526.103931] option 1-2:1.0: GSM modem (1-port) converter detected
[  526.104202] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB8
[  534.172618] option1 ttyUSB8: GSM modem (1-port) converter now disconnected from ttyUSB8
[  534.172705] option 1-2:1.0: device disconnected
[  534.173218] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[  534.173274] option 1-2:1.1: device disconnected
[  534.173408] option: option_instat_callback: error -108
[  534.173906] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[  534.173960] option 1-2:1.3: device disconnected
[  534.288133] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  534.423106] option 1-2:1.3: GSM modem (1-port) converter detected
[  534.423461] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  534.423591] option 1-2:1.1: GSM modem (1-port) converter detected
[  534.423796] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  534.423918] option 1-2:1.0: GSM modem (1-port) converter detected
[  534.424197] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  542.496437] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  542.496468] option 1-2:1.0: device disconnected
[  542.496801] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  542.496830] option 1-2:1.1: device disconnected
[  542.496927] option: option_instat_callback: error -108
[  542.497304] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  542.497346] option 1-2:1.3: device disconnected
[  542.497830] BUG: unable to handle kernel NULL pointer dereference at 00000084
[  542.497847] IP: [<f8c0991a>] serial_do_down+0x3a/0x60 [usbserial]
[  542.497873] *pde = 00000000 
[  542.497881] Oops: 0000 [#1] SMP 
[  542.497890] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.7/usb1/idVendor
[  542.497899] Modules linked in: nls_utf8 isofs option usbserial usb_storage binfmt_misc ppdev bridge stp bnep lp parport snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss joydev snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc eeepc_laptop pcspkr psmouse btusb serio_raw rt2860sta(C) atl1e fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp agpgart
[  542.498003] 
[  542.498014] Pid: 9, comm: events/0 Tainted: G         C (2.6.31-999-generic #1248771614) 1000H
[  542.498024] EIP: 0060:[<f8c0991a>] EFLAGS: 00010286 CPU: 0
[  542.498040] EIP is at serial_do_down+0x3a/0x60 [usbserial]
[  542.498049] EAX: f7076000 EBX: f5606600 ECX: 00000216 EDX: f8c09940
[  542.498058] ESI: 00000004 EDI: f560665c EBP: f7077f28 ESP: f7077f1c
[  542.498066]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  542.498076] Process events/0 (pid: 9, ti=f7076000 task=f7056ff0 task.ti=f7076000)
[  542.498082] Stack:
[  542.498087]  f5606600 ffffffff f693a000 f7077f34 f8c09951 00000216 f7077f5c c03608cd
[  542.498107] <0> f693a040 00000000 00000000 00000001 f6a14aa0 f693a128 c2001600 00000000
[  542.498127] <0> f7077f8c c01511e8 c2001020 00000000 31b84bef 0000007e c2001604 c03607f0
[  542.498148] Call Trace:
[  542.498168]  [<f8c09951>] ? serial_hangup+0x11/0x20 [usbserial]
[  542.498183]  [<c03608cd>] ? do_tty_hangup+0xdd/0x300
[  542.498198]  [<c01511e8>] ? run_workqueue+0x68/0x120
[  542.498209]  [<c03607f0>] ? do_tty_hangup+0x0/0x300
[  542.498220]  [<c0152458>] ? worker_thread+0x88/0xe0
[  542.498232]  [<c0155a20>] ? autoremove_wake_function+0x0/0x40
[  542.498244]  [<c01523d0>] ? worker_thread+0x0/0xe0
[  542.498255]  [<c01557a5>] ? kthread+0x75/0x80
[  542.498265]  [<c0155730>] ? kthread+0x0/0x80
[  542.498277]  [<c0103977>] ? kernel_thread_helper+0x7/0x10
[  542.498284] Code: 89 7c 24 08 8b 00 80 bb da 00 00 00 00 8b 70 04 74 0f 8b 1c 24 8b 74 24 04 8b 7c 24 08 89 ec 5d c3 8d 7b 5c 89 f8 e8 16 46 93 c7 <8b> 96 80 00 00 00 85 d2 74 04 89 d8 ff d2 89 f8 e8 b1 45 93 c7 
[  542.498391] EIP: [<f8c0991a>] serial_do_down+0x3a/0x60 [usbserial] SS:ESP 0068:f7077f1c
[  542.498415] CR2: 0000000000000084
[  542.498423] ---[ end trace a92ba52a87d70f8b ]---
[  542.608093] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  542.742905] option 1-2:1.3: GSM modem (1-port) converter detected
[  542.743175] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  542.743281] option 1-2:1.1: GSM modem (1-port) converter detected
[  542.743449] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  542.743546] option 1-2:1.0: GSM modem (1-port) converter detected
[  542.743712] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  547.797735] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  547.797803] option 1-2:1.0: device disconnected
[  547.798445] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  547.798503] option 1-2:1.1: device disconnected
[  547.798633] option: option_instat_callback: error -108
[  547.798781] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  547.798844] option 1-2:1.3: device disconnected
[  547.908226] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  548.043089] option 1-2:1.3: GSM modem (1-port) converter detected
[  548.043462] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  548.043607] option 1-2:1.1: GSM modem (1-port) converter detected
[  548.043847] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB5
[  548.043982] option 1-2:1.0: GSM modem (1-port) converter detected
[  548.044313] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB6
[  556.104566] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[  556.104633] option 1-2:1.0: device disconnected
[  556.105326] option1 ttyUSB5: GSM modem (1-port) converter now disconnected from ttyUSB5
[  556.105385] option 1-2:1.1: device disconnected
[  556.105517] option: option_instat_callback: error -108
[  556.105666] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  556.105729] option 1-2:1.3: device disconnected
[  556.220133] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  556.354217] option 1-2:1.3: GSM modem (1-port) converter detected
[  556.354571] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  556.354703] option 1-2:1.1: GSM modem (1-port) converter detected
[  556.354913] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  556.355038] option 1-2:1.0: GSM modem (1-port) converter detected
[  556.355246] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  564.617550] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  564.617624] option 1-2:1.0: device disconnected
[  564.617786] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  564.617845] option 1-2:1.1: device disconnected
[  564.617972] option: option_instat_callback: error -108
[  564.618116] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  564.618178] option 1-2:1.3: device disconnected
[  564.732123] usb 1-2: reset high speed USB device using ehci_hcd and address 5
[  564.867106] option 1-2:1.3: GSM modem (1-port) converter detected
[  564.867460] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  564.867591] option 1-2:1.1: GSM modem (1-port) converter detected
[  564.867796] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  564.867920] option 1-2:1.0: GSM modem (1-port) converter detected
[  564.868194] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  603.024645] usb 1-2: USB disconnect, address 5
[  603.024776] option: option_instat_callback: error -108
[  603.025174] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  603.025244] option 1-2:1.0: device disconnected
[  603.025585] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  603.025644] option 1-2:1.1: device disconnected
[  603.028324] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  603.028424] option 1-2:1.3: device disconnected

```

Do I have to check PPA network manager also?

Regards,
George
the system  mouse

---

### Post by Sergiu Bivol on 2009-07-29
> **GeorgeVita said:**
> 
Do I have to check PPA network manager also?


You could try (please try it :) ). For me, the PPA NetworkManager has never worked.

---

### Post by GeorgeVita on 2009-07-29
With all PPAs (NM+kernel) the results are similar to above. Not frozen, ttyUSBx looping (0-1-2, disconnected 0, new 3-4-5, disconnected x, new 6-7-8...).

Good news: my Huawei now works with daily (999) kernel (with standard or PPA NM).
[http://ubuntuforums.org/showthread.php?t=1224361](http://ubuntuforums.org/showthread.php?t=1224361) (solved)

I am downloading a daily Karmic iso to start from todays image.

Regards,
George

---

### Post by GeorgeVita on 2009-07-29
[COLOR="Gray"]Finally the daily-live of 29-July made the connection with NO CHANGES to any file. After attaching the modem the ZeroCD appeared, I eject it, 2 providers shown at N.M. icon, connected from the second one _successfully_!

Now posting from ZTE MF636.

[/COLOR]_First try_:
```
g@KK729:~$ uname -a
Linux KK729 2.6.31-3-generic #19-Ubuntu SMP Tue Jul 14 16:04:41 UTC 2009 i686 GNU/Linux
g@KK729:~$ 
```

manual eject
network-manager 0.7.1-0ubuntu1
no updates to system or N.M.
no changes to .fdi file
no usb_modeswitch or other program
but dmesg shows some more ttyUSBs 

Hope it will connect in a next reboot (or after update).

**NO! AFTER NEXT BOOT PROBLEM EXISTS!** slight deferent but get frozen again.

**_Update1_**: Problem exists on clean install (9.10 daily build 29-july) to an older P4 desktop PC.

**_Update2_**: Problem exists after updating (P4 desktop PC) to 9.10 daily build 29-july to newer kernel (2.6.31-4) AND after using all Pre-Released updates AND using last daily build of kernel (dated 29-July).

Regards,
George

---

### Post by GeorgeVita on 2009-08-03
Tests with the last daily build of the rc5 kernel:

**Linux KK729 2.6.31-999-generic #200908031000 SMP Mon Aug 3 09:44:18 UTC 2009 i686 GNU/Linux**

have approximately the same results.

I created a 'bug' report: [https://bugs.launchpad.net/ubuntu/+bug/408555](https://bugs.launchpad.net/ubuntu/+bug/408555)

Regards,
George

---

### Post by anttu on 2009-08-04
I do not know if this is of any help at all, but I could get MF636 to work quite nicely with 9.04 with the setup described in the link. It is in Finnish, but you can see the actual code parts.
[http://forum.ubuntu-fi.org/index.php?topic=26797.msg216544#msg216544](http://forum.ubuntu-fi.org/index.php?topic=26797.msg216544#msg216544)

There is also a proven init string for MF636 to prevent going to sleep while idle in this thread for Asus WL-500 with Koppel firmware and ZTE MF636:
[http://www.siptune.net/siptune.net/forum/viewtopic.php?f=3&t=93&p=425#p425](http://www.siptune.net/siptune.net/forum/viewtopic.php?f=3&t=93&p=425#p425)

---

### Post by GeorgeVita on 2009-08-04
Hi **anttu**, thanks for replying to this thread.

The idea is to test if MF636 can be used with no modifications to the system and with the modem to its original state (19d2:2000 at lsusb).

If you can test your modem with  a daily-live version of Karmic Koala it would be great.

I am now downloading the recent one from: [http://cdimage.ubuntu.com/daily-live/20090804/](http://cdimage.ubuntu.com/daily-live/20090804/) (for my system: karmic-desktop-i386.iso)

After running the liveCD (or after installation) you must attach the modem, wait till the ZeroCD appear, eject it and check dmesg some times to see behavior of ttyUSBx creation/disconnection.

Thanks,
George

---

### Post by anttu on 2009-08-05
I copied the newest daily (to to a mini DVD-RW as it is oversized for CD) and it booted OK.

1. After plugging in the ZTE MF636+ ("+" stands for a connector for an external antenna, sold at least in Finland) the modem content icon appears. Lsusb shows the info 19d2:2000. 

2. After ejecting the zerocd icon lsusb shows the product id changing from 2000 to 0031 and NWM / Create new connection window opens. Dmesg shows the ports attached to (option?) GSM modem converter:
```
[  600.408047] usb 2-5: new high speed USB device using ehci_hcd and address 8
[  600.543202] usb 2-5: configuration #1 chosen from 1 choice
[  600.545653] scsi6 : SCSI emulation for USB Mass Storage devices
[  600.546061] usb-storage: device found at 8
[  600.546067] usb-storage: waiting for device to settle before scanning
[  602.339751] USB Serial support registered for GSM modem (1-port)
[  602.340374] option 2-5:1.0: GSM modem (1-port) converter detected
[  602.340551] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB1
[  602.340597] option 2-5:1.1: GSM modem (1-port) converter detected
[  602.340699] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB2
[  602.340747] option 2-5:1.3: GSM modem (1-port) converter detected
[  602.340903] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB3
[  602.340938] usbcore: registered new interface driver option
[  602.340943] option: v0.7.2:USB Driver for GSM modems

```3. I can put up the connection and actually also this message is sent thru the ZTE.

There is something rotten still. (Might be the modem itself too.) In my first attempt the modem stalled after a couple of minutes, and there was nothing I could do but reboot. Rebooting with the modem readily plugged in did not show the zerocd icon at all, and the modem stayed as 19d2:2000, not showing as ttyUSB's. After another reboot and only afterwards plugging in the modem everything has worked like a charm for some 30 minutes now.

---

### Post by GeorgeVita on 2009-08-05
Hi **anttu**, thanks for your test!

This makes it more complicate as you can use it (MF636+), I cannot (MF636) and our h/w samples are only two!

From your part of dmesg the **ttyUSB0** is missed. Possibly it is used by another peripheral...
Also as I remember some times (rarely) I had a connection once ...

Please post in the future any other thought/result about this.

Thanks again,
George

---

### Post by anttu on 2009-08-05
Yes, during the test USB0 was attached to the USB-RS232 converter.

Just let me know if you need any further experiments/outputs.

---

### Post by Axel Thimm on 2009-08-05
Hi,

I'm not an Ubuntu user, but I still want to share some findings, which may benefit 636 users:

I'm using Fedora 11 and the default kernel oopses when trying to eject 19d2:2000 to 19d2:0031 (or using usb_modeswitch or modem-modeswitch). I filed a bug for Fedora at

[https://bugzilla.redhat.com/show_bug.cgi?id=514918](https://bugzilla.redhat.com/show_bug.cgi?id=514918)

The very first time I used the card it happily started to connect to the ISP (which is BTW Cosmote/Internet On The Go, just like GeorgeVita, that's how I found this article) and asked for a PIN. After storing the PIN on the card it would always oops when nm-modem-probe probed the three ttyUSB* devices. I also have the CD-ROM & MMC together issue like GeorgeVita.

Long story short, I had to disable the option module (by blacklisting it) and go with usbserial instead. Unfortunately usbserial would not recognize the modem as such, as udev support in usbserial is not as good as in option and thus I had to do the manual hacking in the hal fdi files, even though hal is deprecated. Also otherwise looking identical systems that may work or fail may differ in whether they need/have a PIN on the SIM.

HTH

---

### Post by Sergiu Bivol on 2009-08-05
> **Axel Thimm said:**
> 
I'm using Fedora 11 and the default kernel oopses when trying to eject 19d2:2000 to 19d2:0031 (or using usb_modeswitch or modem-modeswitch). I filed a bug for Fedora at

[https://bugzilla.redhat.com/show_bug.cgi?id=514918](https://bugzilla.redhat.com/show_bug.cgi?id=514918)


It doesn't Oops, it just says "Welcome to the great world of Linux, where nothing ever breaks" :D

Indeed, it Oopses on any operation with the modem. The bad news is you can't do anything about it - the kernel is fscked up.

The good news: other kernels were even worse :) Today Karmic updated the kernel to version 2.6.31-5.24, and it **seems** to work – I have successfully connected ~10 times with wvdial and NetworkManager. No Oops, no BUG.

PS:
> "After a stern criticism from Linus, the long-time kernel hacker Alan Cox has decided to walk away as the maintainer of the TTY subsystem of the Linux Kernel".

We should not hope for fantastic improvements in the near future.

---

### Post by GeorgeVita on 2009-08-05
Hi **Axel Thimm**, thanks for your info! Note also that now I am using Wind as my provider, resulting to:

The problem exists to the same type of modem (Greece, MF636 from Cosmote) with possibly the same ZTE firmware, with different providers, different PC hardware, slight different operating system (possibly same kernel and/or drivers and/or network-manager) and hopefully there are more people that 'want to help'!

Regards,
George

---

### Post by GeorgeVita on 2009-08-08
**Aug 8th** update:

A recent update to network manager **0.8** broke also my Huawei E169 connection! As there are many Huawei users, I suppose this will be solved soon. Trying to investigate this problem I removed (purge or via Synaptic) the package **modemmanager**, resulting to:

**a VERY STABLE assignment of ttyUSBx ports for the ZTE MF636 modem!**

Below is the part of **dmesg** showing the attachment of the modem (19d2:2000), the eject of sr0, the creation of ttyUSB0-1-2 (the last is the data port), re-appearance of the ZeroCD and the card reader and finally the PPP connection via **wvdial** (to write this post).

>>> I CAN USE BOTH ZeroCD and CARD READER on the modem!
>>> Tested and found fully functioning: HSPA connected, read ZeroCD, read/write to a 4GB micro SD card attached to the modem,

```
[   70.045077] usb 1-2: new high speed USB device using ehci_hcd and address 4
[   70.190580] usb 1-2: configuration #1 chosen from 1 choice
[   70.281167] Initializing USB Mass Storage driver...
[   70.284022] scsi2 : SCSI emulation for USB Mass Storage devices
[   70.284483] usbcore: registered new interface driver usb-storage
[   70.284922] USB Mass Storage support registered.
[   70.286756] usb-storage: device found at 4
[   70.286765] usb-storage: waiting for device to settle before scanning
[   74.740168] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[   75.286451] usb-storage: device scan complete
[   75.288555] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[   75.322976] sr0: scsi-1 drive
[   75.322990] Uniform CD-ROM driver Revision: 3.20
[   75.323636] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   75.324955] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   89.325908] ISO 9660 Extensions: Microsoft Joliet Level 1
[   89.336306] ISOFS: changing to secondary root
[  114.745170] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  114.808281] usb 1-2: USB disconnect, address 4
[  120.044207] usb 1-2: new high speed USB device using ehci_hcd and address 5
[  120.179623] usb 1-2: configuration #1 chosen from 1 choice
[  120.194882] scsi3 : SCSI emulation for USB Mass Storage devices
[  120.199682] usb-storage: device found at 5
[  120.199698] usb-storage: waiting for device to settle before scanning
[  120.273015] usbcore: registered new interface driver usbserial
[  120.273698] USB Serial support registered for generic
[  120.274386] usbcore: registered new interface driver usbserial_generic
[  120.274394] usbserial: USB Serial Driver core
[  120.285544] USB Serial support registered for GSM modem (1-port)
[  120.285727] option 1-2:1.0: GSM modem (1-port) converter detected
[  120.285937] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  120.286006] option 1-2:1.1: GSM modem (1-port) converter detected
[  120.286183] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  120.286257] option 1-2:1.3: GSM modem (1-port) converter detected
[  120.286490] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  120.286537] usbcore: registered new interface driver option
[  120.286545] option: v0.7.2:USB Driver for GSM modems
[  125.200348] usb-storage: device scan complete
[  125.201430] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[  125.202409] scsi 3:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  125.208281] sd 3:0:0:0: Attached scsi generic sg1 type 0
[  125.226394] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  125.228532] sr0: scsi-1 drive
[  125.228845] sr 3:0:0:1: Attached scsi CD-ROM sr0
[  125.229039] sr 3:0:0:1: Attached scsi generic sg2 type 5
[  138.008411] ISO 9660 Extensions: Microsoft Joliet Level 1
[  138.009912] ISOFS: changing to secondary root
[  164.743175] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  191.736604] sd 3:0:0:0: [sdb] 7811072 512-byte logical blocks: (3.99 GB/3.72 GiB)
[  191.742491] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  191.747868] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  191.747891]  sdb: sdb1
[  224.742281] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  245.720348] PPP BSD Compression module registered
[  245.752355] PPP Deflate Compression module registered
[  284.743529] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  344.743156] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  404.743200] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  464.743414] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  524.740206] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  584.741127] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  644.742895] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  704.743717] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  764.744391] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  824.742740] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  884.743187] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92
[  944.743162] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 92

```

Regards,
George

---

### Post by GeorgeVita on 2009-08-14
Below is my 'Best way to connect using ZTE MF636 on Karmic Alpha 4'
(most is copy from comment #3 of [https://bugs.launchpad.net/bugs/408555](https://bugs.launchpad.net/bugs/408555))
> Many tests done and the system behavior is very bad when network manager and modem manager running, after ejecting the created CDROM. Partially freeze on terminal, cannot open a new terminal or complete freeze of the system. I can understand 'no connection' but 'loosing' the system is a real 'bug'.

After a clean install of **Ubuntu 9.10 Alpha 4** my best way to connect with **ZTE MF636** modem:

0- boot without the modem, wait for the system to load
1- stop network manager
2- check that wvdial is not running (no process)
3- find process number of modem-manager
4- kill modem-manager
5- attach modem
6- check lsusb: 19d2:2000 (CDROM)
7- wait and eject CDROM created (sr0)
8- check again lsusb: 19d2:0031 (modem)
9- check creation of /dev/ttyUSB0-1-2
a- connect using wvdial and port /dev/ttyUSB2
b- checked that the connection done: valid IP, DNS
```
g@KKa4:~$ sudo /etc/init.d/NetworkManager stop
[sudo] password for g:
 * Stopping network connection manager NetworkManager [ OK ]
g@KKa4:~$ ps -A | grep wvdial
g@KKa4:~$ ps -A | grep modem
 1494 ? 00:00:00 modem-manager
g@KKa4:~$ sudo kill 1494
g@KKa4:~$ ps -A | grep modem
g@KKa4:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 19d2:2000 ONDA Communication S.p.A.
Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
g@KKa4:~$ sudo eject sr0
g@KKa4:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 19d2:0031 ONDA Communication S.p.A.
Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
g@KKa4:~$ dmesg | grep ttyUSB
[ 224.005998] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 224.008440] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 224.009049] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
g@KKa4:~$ sudo wvdial 2
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F
AT&F
OK
--> Sending: AT+CGDCONT=1,"IP","gint.b-online.gr"
AT+CGDCONT=1,"IP","gint.b-online.gr"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Fri Aug 14 14:58:32 2009
--> Pid of pppd: 2420
--> Using interface ppp0
--> local IP address 212.152.101.199
--> remote IP address 10.64.64.64
--> primary DNS address 212.152.70.6
--> secondary DNS address 212.152.70.7
```
Trying to get debug log from modem manager all system got frozen (totally).
I am still in progress to find a way to get this log.

My **/etc/wvdial.conf** is:```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Phone = *99***1#
Username = web
Password = web
Init2 = AT&F
Init3 = AT+CGDCONT=1,"IP","gint.b-online.gr"
Stupid Mode = yes
Dial Attempts = 1

[Dialer 1]
Modem = /dev/ttyUSB1

[Dialer 2]
Modem = /dev/ttyUSB2
```

With the above method I downloaded the Alpha 4 .iso (1h30m), install, update, upgrade, etc.

Regards,
George

---

### Post by GeorgeVita on 2009-08-23
After new tests with Ubuntu 9.10 alpha4 +upgrades +kernel 2.6.31-020631rc7
using 'typical (a4)' and 'trunk' versions of network-manager and modem-manager, below is another 'way' to use my ZTE MF636:

0. boot without modem, wait for the system to fully load
1. STOP network manager
2. KILL modem manager
3. modem attached
4. ZeroCD ejected
5. check: 'real modem state' (lsusb), ttyUSBx creation (dmesg)
6. connected via pppd command (chat included)
7. posted this message

```
g@KKa4:~$ sudo /etc/init.d/NetworkManager stop
[sudo] password for g: 
 * Stopping network connection manager NetworkManager                    [ OK ] 
g@KKa4:~$ ps -A | grep modem
 2508 ?        00:00:00 modem-manager
g@KKa4:~$ sudo kill 2508
g@KKa4:~$ ps -A | grep modem
g@KKa4:~$ # ------> MODEM ATTACHED NOW, WAIT 20sec
g@KKa4:~$ dmesg | grep CD-ROM
[  150.920937] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  150.948117] Uniform CD-ROM driver Revision: 3.20
[  150.949905] sr 2:0:0:0: Attached scsi CD-ROM sr0
g@KKa4:~$ sudo eject sr0
g@KKa4:~$ # -------> WAIT 10sec
g@KKa4:~$ lsusb | grep 19d2
Bus 001 Device 004: ID 19d2:0031 ONDA Communication S.p.A. 
g@KKa4:~$ dmesg | grep ttyU
[  183.957799] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  183.958218] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  183.958681] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
g@KKa4:~$ pppd ttyUSB2 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" OK "atdt*99***1#" CONNECT' user web password web
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
CHAP authentication succeeded
CHAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 212.152.103.76
remote IP address 10.64.64.64
primary   DNS address 212.152.70.6
secondary DNS address 212.152.70.7

```

More info at: [https://bugs.launchpad.net/bugs/408555](https://bugs.launchpad.net/bugs/408555)

Regards,
George

P.S. finally I hope only 'Greek' version of MF636 to be problematic!

---

### Post by alechiko on 2009-09-17
GeorgeVita, I arrived at this post through several other threads you have been involved in regarding the ZTE modems. Admittedly, i followed most of the advice from them first, before realising it was for Ubuntu 8.10

Im using the Karmic and I have a ZTE M636 in Israel using the Cellcom network

After following the instructions quoted below. My system loads and fails to reach the GDM login screen. After 10 minutes or more, i realised it probably wouldnt change and rebooted. I have reverted to the settings before updating the files as described below.

Could you suggest anything else to me? I'm using the EEEPC 901

Thank you.

> **GeorgeVita said:**
> After new tests with Ubuntu 9.10 alpha4 +upgrades +kernel 2.6.31-020631rc7
using 'typical (a4)' and 'trunk' versions of network-manager and modem-manager, below is another 'way' to use my ZTE MF636:

0. boot without modem, wait for the system to fully load
1. STOP network manager
2. KILL modem manager
3. modem attached
4. ZeroCD ejected
5. check: 'real modem state' (lsusb), ttyUSBx creation (dmesg)
6. connected via pppd command (chat included)
7. posted this message

```
g@KKa4:~$ sudo /etc/init.d/NetworkManager stop
[sudo] password for g: 
 * Stopping network connection manager NetworkManager                    [ OK ] 
g@KKa4:~$ ps -A | grep modem
 2508 ?        00:00:00 modem-manager
g@KKa4:~$ sudo kill 2508
g@KKa4:~$ ps -A | grep modem
g@KKa4:~$ # ------> MODEM ATTACHED NOW, WAIT 20sec
g@KKa4:~$ dmesg | grep CD-ROM
[  150.920937] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  150.948117] Uniform CD-ROM driver Revision: 3.20
[  150.949905] sr 2:0:0:0: Attached scsi CD-ROM sr0
g@KKa4:~$ sudo eject sr0
g@KKa4:~$ # -------> WAIT 10sec
g@KKa4:~$ lsusb | grep 19d2
Bus 001 Device 004: ID 19d2:0031 ONDA Communication S.p.A. 
g@KKa4:~$ dmesg | grep ttyU
[  183.957799] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  183.958218] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  183.958681] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
g@KKa4:~$ pppd ttyUSB2 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" OK "atdt*99***1#" CONNECT' user web password web
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
CHAP authentication succeeded
CHAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 212.152.103.76
remote IP address 10.64.64.64
primary   DNS address 212.152.70.6
secondary DNS address 212.152.70.7

```More info at: [https://bugs.launchpad.net/bugs/408555](https://bugs.launchpad.net/bugs/408555)

Regards,
George

P.S. finally I hope only 'Greek' version of MF636 to be problematic!

---

### Post by GeorgeVita on 2009-09-18
Hi **alechiko**, your actions made are not 'hurting' anything. If you make a real reboot you must have your system back. Try from terminal: ```
sudo reboot
```

For connecting the ZTE MF636 modem, I think you must read/try:

[http://ubuntuforums.org/showthread.php?p=6511814](http://ubuntuforums.org/showthread.php?p=6511814)
[http://ubuntuforums.org/showthread.php?p=6894586](http://ubuntuforums.org/showthread.php?p=6894586)

and post there your progress (I am attending both threads), OR better **open a new thread** with a descriptive title into [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") forum so more readers may help. After creation post here or send me a private message with your link.

Regards,
George

**EDIT 'in topic'**: after Alpha 6 tests still my modem 'crashes' the system when modem-manager and/or network-manager are running!

---

### Post by alechiko on 2009-09-18
> **GeorgeVita said:**
> Hi **alechiko**, your actions made are not 'hurting' anything. If you make a real reboot you must have your system back. Try from terminal: ```
sudo reboot
```For connecting the ZTE MF636 modem, I think you must read/try:

[http://ubuntuforums.org/showthread.php?p=6511814](http://ubuntuforums.org/showthread.php?p=6511814)
[http://ubuntuforums.org/showthread.php?p=6894586](http://ubuntuforums.org/showthread.php?p=6894586)

and post there your progress (I am attending both threads), OR better **open a new thread** with a descriptive title into [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") forum so more readers may help. After creation post here or send me a private message with your link.

Regards,
George

**EDIT 'in topic'**: after Alpha 6 tests still my modem 'crashes' the system when modem-manager and/or network-manager are running!

Forgive me. I posted at a late hour. What i have written in my previous post is not accurate. I followed the information at 

[http://ubuntuforums.org/showthread.php?p=6511814](http://ubuntuforums.org/showthread.php?p=6511814)
[http://ubuntuforums.org/showthread.php?p=6894586](http://ubuntuforums.org/showthread.php?p=6894586)

and that was what caused the system to freeze - perhaps because those instructions are designed for 8.10 and im using 9.10?

The instructions that you gave in here:
```

g@KKa4:~$ sudo /etc/init.d/NetworkManager stop
[sudo] password for g: 
 * Stopping network connection manager NetworkManager                    [ OK ] 
g@KKa4:~$ ps -A | grep modem
 2508 ?        00:00:00 modem-manager
g@KKa4:~$ sudo kill 2508
g@KKa4:~$ ps -A | grep modem
g@KKa4:~$ # ------> MODEM ATTACHED NOW, WAIT 20sec
g@KKa4:~$ dmesg | grep CD-ROM
[  150.920937] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[  150.948117] Uniform CD-ROM driver Revision: 3.20
[  150.949905] sr 2:0:0:0: Attached scsi CD-ROM sr0
g@KKa4:~$ sudo eject sr0
g@KKa4:~$ # -------> WAIT 10sec
g@KKa4:~$ lsusb | grep 19d2
Bus 001 Device 004: ID 19d2:0031 ONDA Communication S.p.A. 
g@KKa4:~$ dmesg | grep ttyU
[  183.957799] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  183.958218] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  183.958681] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
g@KKa4:~$ pppd ttyUSB2 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" OK "atdt*99***1#" CONNECT' user web password web
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
CHAP authentication succeeded
CHAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 212.152.103.76
remote IP address 10.64.64.64
primary   DNS address 212.152.70.6
```you are completely correct in saying, caused no damage to the system, it just wouldn't dial out, and after waiting a few minutes and checking the modem log with no error, i gave up and went to sleep. 
But just to clarify, the system hung because of the changes to the following files

[B]/usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
[/B][B]/etc/udev/rules.d/90-zte.rules

[/B]i doubled checked to see that they were edited correctly and i couldnt find any errors, but when the system wouldnt load up anymore, i used the livecd to load up and restore the files to their original states

In light of this new information, is there anything else you can suggest or do you still think i should open a new threat? (I know moderators dont like cloned threads)

---

### Post by GeorgeVita on 2009-09-18
Hi **alechiko**, below is the summary of your case (as shown from your posts):

pc: EEEPC 901
os: Karmic (9.10)
modem: ZTE MF636
3G provider: Cellcom/Israel

If above are correct, **this** is our thread and the most possible reason for your computer 'freeze' is [https://bugs.launchpad.net/bugs/408555](https://bugs.launchpad.net/bugs/408555)

Please confirm above data adding more info:
1. kernel version (from terminal: **uname -a**)
2. do you have any other way to update?

My idea is to have the same configuration as yours and test in parallel.

Regards,
George

---

### Post by alechiko on 2009-09-19
You understood correctly.

```
Linux eeepc 2.6.31-10-generic #34-Ubuntu SMP Wed Sept 16 00:23:19 UTC 2009 i686 GNU/Linux
```

I have full internet access through wifi and optical device usage. Updating is not a problem. As i said, i used the livecd to startup the system and manually revert the files to their original states.

Im curious, why does the 3G provider matter? In any event surely you cannot mirror that?

Thank you in advance :)

---

### Post by GeorgeVita on 2009-09-19
> **alechiko said:**
> ...Im curious, why does the 3G provider matter?

Just in case you need to 'kill' GUIs and use all parameters to a terminal alternative. You have to use APN, user/pass as connecting parameters.

So we are in the same position (same kernel, modem, my pc=EeePC 1000H).

I can use MF636 only with network-manager stopped, modem-manager killed, connecting via **[wvdial]("http://ubuntuforums.org/showpost.php?p=7784945&postcount=26")** or **[pppd]("http://ubuntuforums.org/showpost.php?p=7832437&postcount=27")** commaaaaand as described in previous posts. My 'bug report' has all the history and if affects you [click it there]("https://bugs.launchpad.net/bugs/408555").

G

---

### Post by alechiko on 2009-09-19
> **GeorgeVita said:**
> Just in case you need to 'kill' GUIs and use all parameters to a terminal alternative. You have to use APN, user/pass as connecting parameters.

So we are in the same position (same kernel, modem, my pc=EeePC 1000H).

I can use MF636 only with network-manager stopped, modem-manager killed, connecting via wvdial or pppd commaaaaand as described in previous posts. My 'bug report' has all the history and if affects you [click it there]("https://bugs.launchpad.net/bugs/408555").

G

Yes i see you are seriously investigating the matter. I've been following your posts. What i dont understand though is that user/pass are not required for my service provider. Presumably i would leave those fields blank "" "" ?

---

### Post by GeorgeVita on 2009-09-19
> **alechiko said:**
> What i dont understand though is that user/pass are not required for my service provider. Presumably i would leave those fields blank "" "" ?
Yes, if the connecting method accepts a blank (null) or space user/pass. For example wvdial.conf needs at least one character. Usually a provider who does not use usernames and passwords will accept anything so a 'dummy' character is not a problem.

G

---

### Post by UserDatagram on 2009-09-28
i have enabled zte mf636 with Network Manager.

im using it right now...
if u want to know how just ask..

---

### Post by anttu on 2009-09-28
Yes, please! Tell how. 

Thanks.

---

### Post by GeorgeVita on 2009-09-28
> **UserDatagram said:**
> i have enabled zte mf636 with Network Manager.
im using it right now...
if u want to know how just ask..
**I am asking!**[SIZE="1"]
(Please also provide 'technical' info as **lsusb** output)[/SIZE]

**EDIT:** just checked my ZTE MF636 with fully updated karmic and the symptoms are the same!
kernel 2.6.31-11-generic #36
modemmanager 0.2.git.20090923t083842.f2a3825-0ubuntu1
network-manager 0.8~a~git.20090923t064445.b20cef2-0ubuntu1


Regards,
George

---

### Post by GeorgeVita on 2009-10-07
Today's updates broke my Huawei E169 connection, so return back to test my ZTE MF636. With last kernel **2.6.31-12-generic #40** all system updated NOW system hungs (as usual) when network-manager and modem-manager running.

Good and stable connection after:
```
g@KKsep22:/$ sudo stop network-manager
network-manager stop/waiting
g@KKsep22:/$ sudo killall modem-manager 
g@KKsep22:/$ ps -A | grep -i manag
g@KKsep22:/$ sudo pppd ttyUSB2 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" OK "atdt*99***1#" CONNECT' user web password web
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
CHAP authentication succeeded
CHAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 1...
```
Above actions: Stop KillAll CHEck COnnect (**SKACHECO**)

Note: pppd used for connection (wvdial is an alternative)
Regards,
George

---

### Post by UserDatagram on 2009-10-08
hi guys, sorry for the waiting time.

well, first of all , u need to enable the modem. the only thing u need is usb_modeswitch.

install it.
after u intall it run gedit /etc/usb_modeswitch.conf

search for the zte mf636 section it should look like this :
```

########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
# ZTE MF626
# ZTE MF633
# ZTE MF636 (aka "Telstra / BigPond 7.2 Mobile Card")
#
# Contributor: Joakim Wennergren

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

# only for reference and 0.x versions
MessageEndpoint=0x01

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

# if that command doesn't work, try the other ("eject")
;MessageContent="5553424312345678000000000000061b000000030000000000000000000000"

```when u done with this, make sure with lsusb that ur modem address changed from 0x2000 to 0x0031. if it does - were good.

open Network Manager -> Edit Connections -> Mobile Broadband -> Add

now, a wizard will open and ask u for ur country and provider, fill it up.
now it will be added to ur list , mark and edit it.
in the edit section there is IPv4 tab, go in there and change the method to Automatic (PPP)

that should do it.
now try it, probably u will have problems, so we are here to help troubleshoot.
have fun.

---

### Post by GeorgeVita on 2009-10-08
Hi **UserDatagram**,

What **Ubuntu version** are you running?

```
uname -a
```

Regards,
George

---

### Post by UserDatagram on 2009-10-08
hi.
```
$ uname -a
Linux a-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
```

---

### Post by GeorgeVita on 2009-10-08
**2.6.28-15**-generic #52 is the 'history' and this thread refers to the 'future'!

Your version is **9.04** and at this forum category: > Karmic Koala Testing and Discussion
Ubuntu Karmic Koala is in development, use only for testing purposes!!! we are trying on Ubuntu 9.10 with kernel (now) **2.6.31-12 +**

Thanks anyway!

---

### Post by UserDatagram on 2009-10-08
auhh sorry, just tried to help u guys..

---

### Post by francsal on 2009-10-09
Hi all! Even though I've been reading this forum for a bit of time, this is my first time posting here. Hope I can find some light to the problem I'm facing now...

Ok, here's the thing Today I upgraded my 9.04 to 9.10 via a wired connection. In 9.04 I used to connect via wvdial, no hassles at all. After the update, everything seemed to be fine, so I decided to give my modem a try, thinking I needed to do the usbmodeswitch and wvdial again (just for the record, I'm totally new to Linux, so please, bare with my limitations!). To my surprise, after pluggin the modem, and being detected as a ZTE CDROM (I have a MF626 wich, I think, is essentially the same as the 636), it changed to modem all by itself (I was still connected to the wired LAN, and it downloaded an update for the network manager). It even showed the cute phone icon on the taskbar (I'm using Kubuntu if it matters at all). Growing ambitious, I created a connection on the "broadband" section, and tried to connect, but no joy, so fired up konsole, typed "sudo wvdial" and voila! it connected! Unplugged the wired LAN, and it worked flawesly!

After that, I shutdown the computer, and headed back home. Coming here, I turned the PC on, plugged the modem and NOTHING happened, not even the "ZTE CDROM" was detected.... tried turning it on with and without the modem plugged and still it was not detected, tried pluggin it in the other usb ports, and nothing. Growing desperate, I decided to launch WinXP to post the problem here. While I was at it, I remembered that when I first installed kubuntu, and was trying to make the modem work (before realizing about usbmodeswitch and wvdial), once I restarted the PC from WinXP to Kubuntu WITHOUT ending the connection, and it was recognized at startup, so I decided to give it a try... and voila! I'm connected again! Better yet, it connected from Network Manager!!!!

However, I fear that after shutting it down it would not be recognized again. As I told you, when it was not working it wasnt even detected as a CDROM, so no chance to use usbmodeswitch and wvdial. And even though I'm ecstasic (is that a word?? :-D ) about having it work now from network manager, without any command line input, having to launch winxp just to make that happen seems like "a little" too much to do. I have no problem using usbmodeswitch and wvdial as long as it works, but I really fear that after shutting it down again it wont work.... And so, here comes the question: Any ideas what might be happening? Or what should I do to prevent it from happening? As I stated before, I'm really new to linux, so any ideas, no matter how basic they are, will be most welcome!

Thanks a lot for taking the time to read this, and I'm even more thankful for any help that you might provide.

If it helps, I'm using Kubuntu 9.10 Beta version, downloaded today, on a MSI Wind U120. I'm in Guatemala, Central America, and my 3G service provider is Claro.

Cheers!

Frank.

Edit:

Ok, restarted with the modem unplugged. After start, plugged back in. Detected as CDROM. Automatically started to detect it as modem and then the system froze. turned it off by pressing the power button. Started it back again, this time with the modem plugged in. Detected as CDROM, but it did not automatically got set as modem. Used isbmodeswitch, and it got detected as modem, no freeze this time. Tried to connect with the network manager, and it connected, but no response from any site. Disconnected from the network manager, and then connected via wvdial, and it worked ok. Disconnected from wvdial, and connected back with network manager and it worked ok, again (writing this now.) Will try to disconnect again, restart without the modem, try it again.... hmmm... I should be sleeping :-D

Cheers!

---

### Post by GeorgeVita on 2009-10-09
Hi Frank, welcome to this forum and **thanks** for sharing your efforts.

From 9.10 the 'switching to modem state' is done with '**eject**ing once' the CDROM. This action sends a USB control command to the modem resulting to 'appearance' of the modem. From this point the **lsusb** respond must be **19d2:00xx** (0031 for MF636, possibly 0015 for MF626).

Normal and 'good' behavior is to connect using network-manager.
Guatemala/Claro exists as a selection and **must** work (check it with right click on network manager icon, edit connections, mobile broadband).
As I have gnome desktop, I am not sure if network manager (and modem manager) are the same versions on KDE.

Keep in touch posting us any new progress.

Regards,
George

---

### Post by francsal on 2009-10-09
Hi George! Thanks for the welcome words and for replying so fast.

I don´t know why, but right now it serems to be working just fine. As you said, all I have to do is press the eject icon on the "recently plugged devices" and that does it. It gets recognized as a modem. I tried it again this morning and it seems to be working ok, detecting it as soon as I plug it. And my ZTE is identified as :0031 too, in lsusb.

Now, the only problem stiff happening is that, if I try to connect directly from network manager first, it doesnt recognizes any DNS servers. I have to first connect via wvdial, close that connection, and then I can connect via network manager with it recognizing the DNS servers. I think it might have something to do with my creating the connection profile in the "mobile broadband" tab of the connection settings, but, unfortunately, fo some reason, I have no pre-defined list of service providers there, so no chance of picking Claro Guatemala out of the box.

I have searched where to make that configuration (defining the DNS Servers), but I guess that after so many years of being "adoctrinated" by windows  :P I´m absolutely unable to find the place to do so. Any ideas as to how to configure a pre-defined DNS server for that particular connection? If only I could fix that, I guess I) could definitely say that my MF626 works "right out of the box" with Kubuntu Karmic.

One thing that I find odd is that after 4 or 5 tries, the thing seems to be working ok now. I´m ignorant enough of Linux as to post the following foolish question: Is there an auto adapt or a self-learning process in Linux/Kubuntu? Because that´s precisely the way it feels to me, with this thing working ok after a few tries, and with nothing whatsoever done from my part, besides plugging and unplugging the modem...

Finally, I think (correct me if I´m wrong, please) that what might have helped it to work are the usbmodeswitch.conf and wvdial.conf files I had in Jaunty? I saw a line, during the install process that said something like "reading wvdial.conf file" and then "trying to detect modem".  I have the feeling that it might have helped Karmic to detect it....

Anyway, will keep on testing it, and post anything else that might happen. And, if you have any idea on how to manually configure the DNS server, I would be more than thankful!

Cheers!


Frank

---

### Post by GeorgeVita on 2009-10-09
Hi Frank!
Let's start checking network manager data (mine shows):
Guatemala, Claro, Phone=*99#, APN=internet.ideasclaro, user/pass=empty
PPP settings: Allowed methods all ticked, Compression BSD, Deflate & TCP ticked, IPv4 method=Automatic(PPP)
I do not know if above are valid for your provider, but are the same for mine (except user/pass=web).

For DNS setting, try: IPv4 method=Automatic(PPP) **addresses only** and then edit DNS servers to your choice.

>>> The idea is to simply: boot, attach the modem, eject it (manually for now) and then just click on provider to connect. Probably wait for the led on the modem to become steady blue before trying to connect.

All other methods MUST be kept in mind because in any problem you can connect using them (ex. wvdial).

Rregards,
George

---

### Post by francsal on 2009-10-09
Hi George!

Yep, that precisely how I configured my manual connection on broadband mobile, copying the parameters I used on Windows... Now the thing is

> **GeorgeVita said:**
> 

For DNS setting, try: IPv4 method=Automatic(PPP) addresses only and then edit DNS servers to your choice.



Where is that? that´s precisely what I´ve been trying to find, but seem unable to do so. In the network manager settings I have been unable to find where to set those parameters... It´s definitely not on the broadband settings....

Will keep on trying to find it....

PS. Now, it seems it doesn´t like to boot with the modem connected.... hmmm.... I can live with that, too. :-D


EDIT: Ok, this is freaky.. :-D now it´s working without needing me to connect via wvdial..... I know I should be happy about it just working now... but it puzzles me why... any ideas? I mean, I´m definitely not complaining, but I would love to understand what happened, what did I / it did to work, both to understand it, as well as maybe helping others...

anyway... I think I can now confidently say that the MF626 works "out of the box" (sort of... ;-) ) with Karmic.

will keep on trying it and posting about it.

thanks George, for the input!

cheers!

---

### Post by GeorgeVita on 2009-10-09
IPv4 setting is a tab under mobile broadband on my gnome-network manager.

> **francsal said:**
> ...Ok, this is freaky.. :-D now it´s working without needing me to connect via wvdial..... I know I should be happy about it just working now... but it puzzles me why... any ideas? I mean, I´m definitely not complaining, but I would love to understand what happened, what did I / it did to work, both to understand it, as well as maybe helping others...

anyway... I think I can now confidently say that the MF626 works "out of the box" (sort of... ;-) ) with Karmic...

Also note that 'fun' just began ... as we must wait 20 days more for the final release! For now just: > Karmic Koala Testing and Discussion
Ubuntu Karmic Koala is in development, use only for testing purposes!!!

Thanks for sharing (and trying)!
George

---

### Post by francsal on 2009-10-09
Yep, imagine the final version! I must say that this "Beta" is much more stable than ano7her  ;-) beta I tried a couple of months ago... :-D



Regarding the IP Settings, in KDE they´re not there. Still trying to figure out where the heck are they hidden.. :-D

Still working ok. 

Cheers!

---

### Post by stinger30au on 2009-10-17
g'day,
frank put me on to this thread and im trying to get one of the telstra model MF626 3g modems working with 9.10

9.10 beta has all its updates and when plugged in it shows the icon for the install data on the desktop

i hit eject and installed the modem and setup adsl

the first time i tried this it said my signal was full strength but would not transfer data

i shutdown the pc and tried the usb modem in a laptop running windows xp and it runs fine

fireup up ubuntu 9.10 again deleted the adsl settings and plugged in modem and setup modem again

this time it said there was no signal at all.

this time i shut down 9.10 again and i brought the laptop to where the modem was and plugged it in to the laptop and tried again just incase the modem was in a bad signal area

the laptop again worked fine so the modem is ok and the location of the modme in the house makes no difference

something amiss as to why 9.10 is not working with it correctly

firedup 9.10 on my desktop pc again and now it does not even recognise the modem 

i had the *EXACT* same drams with 9.04

*sigh*

so frustrating

---

### Post by GeorgeVita on 2009-10-17
Hi **stinger30au**, this is not the best time to try!

At first a note: signal strength does NOT work on 3G connections! It shows 'connected' (like full signal) and 'not connected' (like no or minimum signal).

Although your modem (MF626) seems identical to mine (MF636) using **lsusb** command (19d2:0031), we are not sure for the same behavior using network-manager. Also a recent kernel bug 'broke' 3G connections with other type of modems (possibly adds more problems to ZTEs).

My opinion is that we must wait one week more for the 9.10 **RC**  and try it with the final kernel.

Note that: I can connect with **ZTE MF636** on Ubuntu 9.10 using kernel **2.6.31-11-generic #38** after **stop**ping network-manager and **kill**ing modem-manager using **wvdial** (must be downloaded) or **pppd** (difficult).

^^^^ is above a 'compatible' solution?

With Ubuntu 9.04 the situation is different. I think it is better to try **udev-extras** as described at [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)

In any progress post any new data to follow up.

Regads,
George

---

### Post by francsal on 2009-10-17
Hi Stinger.

It´s really confusing to see you having this kind of problems. As George said, it´s probably not the best time to try. The funny thing is that I have exactly the same modem as you do, using 9.10, and it works really good, whenever it gets detected...(There seem to be some kind of bug with the USB detection in my computer, because it doesn´t get detected all the time. And it´s not a modem problem, because when it doesnt get detected, it doesnt detect my usb memory stick, either, and it only works after "rebooting" -in quotes, because I also have some problems with the reboot/shutdown process- several times....)

Back on topic. I think that something that might have helped me is that, when I had 9.04 installed, I connected with the usbmodeswitch tip, and used wvdial to establish the connection. I´ve got the feeling that when I updated to 9.10 beta, it detected the configuration I had, and that helped make it work as good as it does.

If you did a fresh update, maybe that´s the problem. I´d suggest you to do the usbmodeswitch tip, and then try to connect with wvdial, and see if that works. If so, I´d guess that you would also be able to connect via networkmanager. Just so you know (and to prove that every experience is different, mainly in a beta release), as opposed to George experience, I do not have to kill any application, or connect via a command line. So, if the usage is not really VITAL, you can keep on trying different tips to see what can make it work. At least, in my case, besides making it work, it has been a wonderful and priceless learning experience.

So, why don´t you give usbmodeswitch and wvdial a try? Let us know how it works, ok?

Cheers.


Frank.

---

### Post by stinger30au on 2009-10-17
thanks guys for the feedback

i will have a go at your suggestions and report back

---

### Post by gdp77 on 2009-10-18
Hi to everyone!

I have just subscribed to a mobile broadband service (cosmote / greece) and my usb dongle is the ZTE MF662.

lsusb output :

```
Bus 001 Device 002: ID 19d2:0017 ONDA Communication S.p.A.
```

Unfortunately the dongle is being recognized only when I have previously booted windows XP and initialized the dongle. Then I can boot ubuntu - I am using 9.10 beta - and connect from network manager with one click!

The problem is that when the pc is turned off and I boot into ubuntu (red led on the dongle) then the dongle is not being recognized and therefore i can't connect. 

To make things worse the last update caused a lot of problems at my network manager icon (it is disappeared when the OS boots) and I have to manually make it appear again with ```
nm-applet & 
```

So, I guess I have to wait until RC or final version and then see how dongle behaves. In the meantime (this thread is huge) is there any bug report from you guys, so we can all contribute? Please give link.

---

### Post by GeorgeVita on 2009-10-18
Hi **gdp77**,
glad to see another 'Greek ZTE tester'!

The bug# for ZTE MF636 is: [https://bugs.launchpad.net/bugs/408555](https://bugs.launchpad.net/bugs/408555)

Also at this time another bug 'broke' 3G connections:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)
which fixed but not yet at repositories.

Main idea is that the modem MUST work attached or not during boot and of course without using another O.S. before! ZTE modems are a minority (as Ubuntu at this time) and cannot be fully tested from developers.

The problem may exist on how modem-manager handles the 'real' modem and ejects the virtual CDROM. You can check it using a 'terminal' test procedure:

- boot Ubuntu 9.10 **without** the modem (use **2.6.31-11** if possible)
- open a terminal window, **stop** network manager & **kill**all modem-manager:
```
sudo stop network-manager
sudo killall modem-manager
```
- attach modem, wait for the CDROM icon to appear, if so right click on icon and 'eject' it
- from terminal try the following pppd commaaaaand (**edited for cosmote**):
```
sudo pppd ttyUSB2 nodetach defaultroute noipdefault noauth lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','internet'" OK "atdt*99***1#" CONNECT' user u password p
```
If you get a stable connection the problem may exist between network and modem managers.

Regards,
George

---

### Post by gdp77 on 2009-10-18
Ok. I'll try to do what you say when I have the time. In the meantime it would be a good idea to "spam" our providers and ZTE manufacturer in order to give to their customers better linux support. Let them know that THERE ARE people who use others OS than windows.

---

### Post by Dropbear on 2009-10-23
I find I can use the mf636 through network manager on a clean install of karmic rc 64bit. There is still a long delay (30 seconds approx) from plugging in till network manager finds it. 

Only real problem I had was it would have a lot of trouble getting a dns. It seems ok if uncheck all authentication methods except CHAP.

Previously I could only connect with wvdial. A clean install seems to have resolved this issue for me at least.

I'm using Telstra NextG

---

### Post by momo971 on 2009-10-23
My **ZTE MF 626** is working **without** the need for usb-modeswitch in Kubuntu Karmic 32 & 64 bits.
That's nice.
I have to eject sr1 each time I plug-in the USB modem, or it will not be recognized as a USB broadband mobile modem. 

That's a bit annoying.

```
sudo eject sr1
```

Troughput is terrible compared to Windows, but it works.

---

### Post by thisisbetter on 2009-10-24
Hello

I hope you can help. I'm new to Ubuntu currently with version 9.04 running on an Acer laptop with no other operating system (I took the plunge!).

I've bought a ZTE MF627 usb modem, I'm in the UK and the mobile broadband is with the 3 network.

I'm wondering if I wait until version 9.10 is released in 5 days time ... will my modem work without any complicated problems? 

Many thanks

:)

---

### Post by GeorgeVita on 2009-10-24
Hi **thisisbetter**,
**MF627** with **9.04** most possible solution (if you are not using it already) is to try **udev-extras** as described at:
[http://ubuntuforums.org/showthread.php?t=1017987](http://ubuntuforums.org/showthread.php?t=1017987)
or [http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way)

If your connection with this modem is 'the only one' it is better to try the final 9.10 LiveCD before updating or installing.

----------

Hi **Dropbear**, I tried a new installation of 9.10 rc (32 bit) with worst results for my ZTE MF636! Also I could not work with Huawei E169 (another active [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146")), so I used Puppy again to download a patched [kernel]("http://people.canonical.com/~apw/lp446146-karmic/"). With the **rc** kernel ( .14-48 ) I could not use neither straight pppd command (disconnected after 1-2 minutes).

----------

Hi **momo971**, this is the way it should work for our modems also. If you want you can make a udev rule to 'auto eject' it:
[http://ubuntuforums.org/showpost.php?p=8034194&postcount=63](http://ubuntuforums.org/showpost.php?p=8034194&postcount=63)

Regards,
George

---

### Post by Dropbear on 2009-10-25
> **GeorgeVita said:**
> Hi **thisisbetter**,
**MF627** with **9.04** most possible solution (if you are not using it already) is to try **udev-extras** as described at:
[http://ubuntuforums.org/showthread.php?t=1017987](http://ubuntuforums.org/showthread.php?t=1017987)
or [http://www.greenhughes.com/content/zte-mf627-easy-way](http://www.greenhughes.com/content/zte-mf627-easy-way)

If your connection with this modem is 'the only one' it is better to try the final 9.10 LiveCD before updating or installing.

----------

Hi **Dropbear**, I tried a new installation of 9.10 rc (32 bit) with worst results for my ZTE MF636! Also I could not work with Huawei E169 (another active [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146")), so I used Puppy again to download a patched [kernel]("http://people.canonical.com/~apw/lp446146-karmic/"). With the **rc** kernel ( .14-48 ) I could not use neither straight pppd command (disconnected after 1-2 minutes).

----------

Hi **momo971**, this is the way it should work for our modems also. If you want you can make a udev rule to 'auto eject' it:
[http://ubuntuforums.org/showpost.php?p=8034194&postcount=63](http://ubuntuforums.org/showpost.php?p=8034194&postcount=63)

Regards,
George

What actually happens when you plug in your modem? I often find I have to unplug and replug for the modem to show up in dmesg. Not sure if it's a problem with my laptop (Compaq Presario F503AU) or a software problem as it happens with a few usb devices. I have the cdrom mode on the mf636  disabled using so it is not necessary to eject.

---

### Post by piankhi on 2009-10-26
Hi...

I hope this is the right thread to ask my question. I have a ZTE AC8710 usb 3G modem that i've been using with Kubuntu 9.10 for the last couple of weeks. The modem wasn't recognized by network manager when i first plugged it in, but that wasn't a big deal (for me) since i prefer using KPPP. After "apt-get removing" network manager (because of another issue) i did the following:


 Doing a lsusb showed that the product id for my AC8710 modem was 0xFFFF, So i did:

```

modprobe usbserial vendor=0x19d2 product=0xFFFF

```The modem worked at this point but my connection was capped at 63kbps, which was weird. So i did some digging around and found that i should be using the "option.ko" driver instead (is that correct?). So i loaded option.ko after unloading usbserial by doing:

```

rmmod usbserial 
modprobe option

```Checked dmesg after that. "Option.ko" was loaded but it didn't recognize my modem. So i looked into the "option.c" source file and turns out it has AC8710 hard-coded with 0xFFF1 instead of 0xFFFF as the product id. I simply recompiled the "option.c" source file after editing 0xFFF1 to 0xFFFF, copied the compiled option.ko file to **/lib/modules/2.6.31-14-generic/kernel/drivers/usb/serial**, did a "depmod -a" and finally "modprobe option". Now my modem is recognized and working as soon as i plug it in.

Since I'm relatively new to the linux world (returning after being in a long windows coma :D), i have no idea how to contact the devs so this can get sorted out pre-release. How would i go about reporting this issue?

Edit: Forgot to include that im runnnig with the latest updates as of 19:16 UTC, 10/26/2009, as well as :

**uname -a:**

```
 
2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

```[B]
dmesg:[/B]

```

[31547.704035] usb 2-3: new full speed USB device using ohci_hcd and address 7
[31547.916579] usb 2-3: configuration #1 chosen from 1 choice
[31547.927365] option 2-3:1.0: GSM modem (1-port) converter detected
[31547.927534] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB0
[31547.929571] option 2-3:1.1: GSM modem (1-port) converter detected
[31547.929715] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB1
[31547.932760] option 2-3:1.2: GSM modem (1-port) converter detected
[31547.932920] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB2
[31547.937012] option 2-3:1.3: GSM modem (1-port) converter detected
[31547.937154] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB3

```**lsusb:**

```

Bus 002 Device 007: ID 19d2:ffff ONDA Communication S.p.A.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0200 Chicony Electronics Co., Ltd
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by GeorgeVita on 2009-10-26
Hi **piankhi**,
from your post it is clear that 'you know enough to help!' so firstly you need a launchpad account. Read more at [https://launchpad.net/](https://launchpad.net/)

Your modem was not working 'directly' when attached to the system, so assume this behavior a 'bug'. Usually we create a new thread at [Networking and Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") forum to discuss/confirm the problem with other users and then report it to Launchpad.

When you have a fix/patch you post it to your launchpad bug report, a developer will 'pick it' and find the way to establish it in a next update or next Ubuntu version. Till then some users may try and work with your patch reading your thread at ubuntuforums.org

--------------

Hi **Dropbear**, the behavior of my MF636 is the same when ejecting or removed permanently the virtual CD-ROM. Creation/disconnection of ttyUSBx is looping resulting (most times) to a terminal freeze. Within this thread another user reported that his modem worked fine but was MF636**+** (+ had an antenna connector) which maybe using another firmware.


Regards,
George

---

### Post by Abdullahnz on 2009-10-26
Would a possible solution be to simply reconfigure the modem to connect directly as a 'real modem' instead of using the CD autorun?

I did this with my ZTE MF626. It was an easy process and now it is plug n play every time.

I wrote a brief guide explainiing the process here:
[http://ubuntuforums.org/showthread.php?t=1302235](http://ubuntuforums.org/showthread.php?t=1302235)

I presume the same is possible with an MF627, though the AT commands might differ.

---

### Post by GeorgeVita on 2009-10-27
Hi **Abdullahnz**, thanks for sharing your HowTo which can 'switch off the autorun function of ZTE MF6xx devices'.

Similar posts:
8.10 & wvdial: [http://ubuntuforums.org/showthread.php?p=6511814](http://ubuntuforums.org/showthread.php?p=6511814)
8.10 & network manager: [http://ubuntuforums.org/showthread.php?p=6894586](http://ubuntuforums.org/showthread.php?p=6894586)

Some users do not want to use above method (although simpler and stable) just to have the option for 'auto-installation' to other win computers.

Some modems cannot 'be connected' simply after this 'real-modem switching' because they have a different productID (lsusb output: 19d2:00xx).

Regards,
George

---

